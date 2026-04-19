# Rate-Limited Webhook Dispatcher Service for Plaidstone Financial

## Occupation
- **SOC:** 15-1252
- **Title:** Software Developers

## Scenario
Plaidstone Financial, a B2B payments processor in Denver, needs a webhook dispatcher service to notify merchant partners when transactions settle. Lead engineer Priya Ramaswamy (priya.r@plaidstone.io) filed ticket PLD-2147 after three merchants complained that settlement notifications arrived in duplicate batches following the March 3, 2026 outage. The service must go live before the April 30 quarterly close; missing it pushes reconciliation to manual-ops and costs roughly $18K/quarter in contractor hours.

## Inputs
The repo skeleton and existing helpers:

```python
# events/models.py (existing)
from dataclasses import dataclass
from datetime import datetime

@dataclass
class SettlementEvent:
    event_id: str          # UUIDv4
    merchant_id: str       # e.g. "merch_8f2a"
    amount_cents: int
    currency: str          # ISO-4217, e.g. "USD"
    settled_at: datetime   # UTC
    idempotency_key: str

# Merchant registry (Postgres table `merchant_webhooks`):
#   merchant_id TEXT PK, url TEXT, secret TEXT,
#   max_rps INT DEFAULT 10, active BOOLEAN
```

Sample row: `("merch_8f2a", "https://hooks.acme-retail.com/plaidstone", "whsec_7QxL...", 5, true)`.

Dispatcher reads events from Redis stream `settlements:v2` with consumer group `dispatcher-g1`. Each stream entry uses:

```json
{
  "event_id": "550e8400-e29b-41d4-a716-446655440000",
  "merchant_id": "merch_8f2a",
  "amount_cents": 1250,
  "currency": "USD",
  "settled_at": "2026-03-03T19:14:22Z",
  "idempotency_key": "settlement:550e8400-e29b-41d4-a716-446655440000"
}
```

Lookup behavior is strict: if `merchant_id` is missing from Postgres, or the row exists with `active = false`, the dispatcher must skip the HTTP call, ack the stream entry, and emit a structured warning. If the merchant exists and is active, the dispatcher posts the event to `url`.

Downstream endpoints expect a Stripe-style HMAC-SHA256 signature in `X-Plaidstone-Signature` and a timestamp in `X-Plaidstone-Timestamp`. The string to sign is `"<timestamp>.<raw_request_body>"`, where `timestamp` is the Unix second integer in the header and `raw_request_body` is the exact JSON bytes sent over the wire. Retries use exponential backoff with jitter, starting at 2s, capping at 60s, and stopping after 5 total attempts. On success the dispatcher ACKs the Redis stream entry; on repeated failure it leaves the entry pending until a later retry and only dead-letters after the last attempt.

Explicit happy path: one valid Redis entry for an active merchant is loaded, the merchant is found in Postgres, the dispatcher sends one signed HTTP `POST` to the configured webhook URL, receives a `2xx`, and ACKs the stream entry exactly once.

## Artifact specification
Build a Python 3.11 async dispatcher package with:
- `dispatcher/client.py` — the `WebhookDispatcher` class with `run()` loop, Redis stream reads, merchant lookup, ACK handling, and signed HTTP `POST`s via `httpx.AsyncClient`.
- `dispatcher/retry.py` — retry policy with jittered exponential backoff and dead-letter push to `settlements:dlq`.
- `dispatcher/signing.py` — HMAC signing + timestamp verification helpers.
- `tests/test_dispatcher.py` — pytest suite using `respx` to mock HTTP, covering the happy path, missing/inactive merchant handling, retries, and duplicate suppression.
- `README.md` — setup, env vars (`REDIS_URL`, `DB_URL`, `CONCURRENCY`), and a sample docker-compose invocation.

Structural requirements: type hints throughout, `structlog` JSON logs, graceful shutdown on SIGTERM, at-least-once delivery with idempotency-key dedup in a Redis SET with 7-day TTL, and async Redis/Postgres/HTTP calls in the hot path.

## Output format
Multi-file Python package. Main source ~250 lines across modules; tests ~120 lines; README ~60 lines.

## Iteration targets
1. V1: a tiny dispatcher loop in one file that reads one Redis stream entry, looks up the merchant, sends one unsigned `POST` on the happy path, and ACKs on `2xx`. This should be doable in about 15 minutes.
2. V2: add idempotency-key deduplication in Redis and skip duplicate stream entries without sending the webhook again.
3. V3: add Stripe-style signing with the exact string-to-sign above, plus timestamp freshness checks and constant-time comparison.
4. V4: add bounded retries with jittered exponential backoff, DLQ handoff after the final attempt, and explicit ACK-on-success / leave-pending-on-transient-failure semantics.
5. V5: add per-merchant fixed-window throttling using Redis `INCR` + `EXPIRE`, and tests that cover concurrent dispatch at the configured limit.
6. V6: add Prometheus metrics and stronger pytest fixtures, including `fakeredis`, so the suite runs without Docker.

## Success criteria
- V1 passes a single happy-path test: one active merchant, one Redis entry, one outbound HTTP call, one ACK.
- V2 includes a duplicate-suppression test that proves the same `idempotency_key` is not delivered twice.
- V3 includes signature tests for both valid and expired timestamps, and rejects tampered payloads.
- V4 includes a retry test that exercises at least one transient 5xx and verifies DLQ behavior after the last attempt.
- V5 includes a concurrent throttling test against a merchant with a low `max_rps` and verifies the fixed-window behavior matches the configured limit.
- V6 passes `pytest -q`, uses only async I/O in the dispatcher path, and the README shows a runnable `docker-compose up` command.

## Scope target
V1 at ~15 min: single-file `dispatcher/client.py` with a basic async loop, one Redis stream read, merchant lookup, unsigned HTTP `POST`, ACK on success, one happy-path pytest, and a short README. Later iterations add dedup, signing, retries, throttling, metrics, and stronger tests cumulatively.
