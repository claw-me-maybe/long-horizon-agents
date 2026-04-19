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

Downstream endpoints expect HMAC-SHA256 signature in `X-Plaidstone-Signature` header over the raw JSON body, with timestamp in `X-Plaidstone-Timestamp`. Retries must use exponential backoff (base 2s, max 5 attempts, cap 60s). Dispatcher reads events from a Redis stream `settlements:v2` (consumer group `dispatcher-g1`).

## Artifact specification
Build a Python 3.11 async dispatcher package with:
- `dispatcher/client.py` — the `WebhookDispatcher` class with `run()` loop, per-merchant token-bucket rate limiter, and signed HTTP POSTs via `httpx.AsyncClient`.
- `dispatcher/retry.py` — retry policy with jittered exponential backoff and dead-letter push to `settlements:dlq`.
- `dispatcher/signing.py` — HMAC signing + timestamp verification helpers.
- `tests/test_dispatcher.py` — pytest suite using `respx` to mock HTTP, including duplicate-suppression and rate-limit tests.
- `README.md` — setup, env vars (`REDIS_URL`, `DB_URL`, `CONCURRENCY`), and a sample docker-compose invocation.

Structural requirements: type hints throughout, `structlog` JSON logs, graceful shutdown on SIGTERM, at-least-once delivery with idempotency-key dedup in a Redis SET with 7-day TTL.

## Output format
Multi-file Python package. Main source ~250 lines across modules; tests ~120 lines; README ~60 lines.

## Iteration targets
1. Replace naive `asyncio.sleep` rate limiting with a proper token-bucket that survives restarts (use Redis `INCR` + `EXPIRE`).
2. Add circuit breaker per-merchant: open circuit after 5 consecutive 5xx, half-open after 30s.
3. Add Prometheus metrics: `webhooks_sent_total`, `webhook_latency_seconds`, `webhook_retries_total` (by outcome).
4. Harden HMAC verification against timing attacks (`hmac.compare_digest`) and reject events older than 5 min.
5. Add a pytest fixture that spins up `fakeredis` so the suite runs without Docker.

## Success criteria
- `pytest -q` passes; includes at least one test that proves duplicate events are dropped.
- Rate limiter is provably correct under concurrent dispatch (test with 50 concurrent tasks against 10 rps merchant).
- No blocking I/O in the hot path; all DB/Redis calls are async.
- HMAC signature matches the Stripe-style scheme (`t=<ts>,v1=<hex>`).
- Circuit breaker prevents thundering-herd on persistent merchant outage.
- README contains a runnable `docker-compose up` command.

## Scope target
V1 at ~15 min: single-file `dispatcher/client.py` with basic async loop, unsigned POST, naive per-merchant `asyncio.Semaphore`, one happy-path pytest, and a 10-line README. Rate limiting, signing, retries, and metrics arrive in later iterations.
