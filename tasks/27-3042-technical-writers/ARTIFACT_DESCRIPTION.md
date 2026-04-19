# API Reference Page: Stripe-Style Docs for Meridian Payouts API

## Occupation
- **SOC:** 27-3042
- **Title:** Technical Writers

## Scenario
You are the lead technical writer at Meridian, a B2B payments infrastructure company launching a new **Payouts API v3** to GA on May 12, 2026. The v3 release consolidates three prior endpoints (`/transfers`, `/instant_payouts`, `/batch_disbursements`) behind a unified `/v3/payouts` resource. You own the reference documentation and need a first-pass reference page for the core `POST /v3/payouts` endpoint by April 24, 2026 — this will be reviewed by the API team lead (Divya Raghunathan), the product manager (Kofi Mensah), and Meridian's DX council next Monday. The docs need to match the clarity standard of Stripe and the taxonomy of OpenAPI-driven docs. Customers will land here via search, via SDK error messages, and via linked cross-references from tutorials.

## Inputs
What you're working from:
- OpenAPI 3.1 spec (partial; request body schema stable, response schema under minor revision).
- Engineering design doc for v3 (internal Notion): explains rationale for consolidation, new idempotency key behavior, new async state machine.
- Three prior reference pages (v2) in your current docs repo — they use a consistent but dated template (no request/response tabs, no language-tabbed examples, poor error documentation).
- Style guide excerpt (Meridian Docs Style): active voice, second person ("you"), present tense, "payout" singular unless referring to the collection, HTTP verbs in monospace, all JSON keys in monospace, no unnecessary capitalization.
- SDK coverage: official SDKs in Node, Python, Ruby, Go, Java. Examples must reflect all five.
- New in v3: idempotency key is required (not optional); `destination` parameter accepts polymorphic inputs (bank account ID, card ID, wallet ID); a `settlement_speed` field replaces the v2 "instant" boolean; async state machine introduces a `processing` state with webhook callbacks.
- Rate limit: 100 requests/minute per account, 429 response with `Retry-After` header.
- 11 documented error codes specific to payouts (insufficient_funds, destination_blocked, settlement_window_closed, etc.).

## Artifact specification
Produce a **full API reference page** for `POST /v3/payouts`. Structure:
1. **Endpoint overview** — one-sentence purpose, two-to-three-sentence framing, idempotency note, versioning note, when to use vs. adjacent endpoints.
2. **Request** — HTTP method + path in a code block, auth note, content-type.
3. **Request parameters** table — columns: Name, Type, Required, Description. Nested parameters use indentation or sub-tables. Polymorphic fields (`destination`) documented with discriminator.
4. **Request example** — language-tabbed (Node shown, others noted). Shows realistic values, idempotency key use, minimal and full examples.
5. **Response** — 201 Created response. Full JSON response body, annotated.
6. **Response fields** table — same columns.
7. **Errors** — table of the 11 documented error codes with `code`, HTTP status, `type`, `message` template, and "how to recover" column.
8. **State machine diagram** — ASCII state diagram showing `created -> processing -> succeeded | failed | returned`, with events/webhooks labeled.
9. **Idempotency** — short section on the new required behavior, example of safe retry, caveats.
10. **Rate limits** — quota, 429 behavior, `Retry-After` handling, exponential backoff recommendation.
11. **Related** — links to adjacent pages (webhooks reference, destination creation, migration guide from v2).

Voice: crisp, no marketing, no apologies. Never "simply" or "just." Second person. Present tense. Prefer the imperative for instructions ("Include an `Idempotency-Key` header"). Code blocks are runnable, not snippet-fragments. When documenting a behavior, document the failure mode too.

## Output format
Single markdown file. JSON in fenced code blocks with `json` tag. Curl in fenced code block with `bash` tag. Tables in GFM format. State machine in a fenced code block (ASCII boxes and arrows, no external image). Rough length: 300-500 lines.

## Iteration targets
1. Tighten the overview — the first sentence must say exactly what the endpoint does, with no preamble.
2. Ensure every required parameter is explicitly marked required, and every optional one has a stated default or "—".
3. The polymorphic `destination` parameter must be documented so a reader can construct any of the three shapes without leaving the page.
4. Error recovery column must be actionable — replace "contact support" entries with concrete developer steps whenever possible.
5. Migration note from v2 must be visible but not dominant — one linked callout, not a whole section (this is a reference, not a migration guide).
6. Make the request example realistic, not boilerplate — amount 4720 (not 1000), currency "USD," destination ID resembling a real Meridian ID prefix (`ba_`).

## Success criteria
- A developer who has never used Meridian Payouts can make a successful request from this page in under 10 minutes, given a test API key.
- Every JSON field shown in the response example is documented in the response-fields table (no orphan fields).
- Idempotency-Key requirement is impossible to miss — it appears in the overview, the parameters table (marked required), the example, and the Idempotency section.
- All 11 error codes are present with non-generic recovery guidance.
- State machine diagram is legible and consistent with the webhook/async copy elsewhere on the page.
- No marketing language ("robust," "seamless," "powerful"). No screenshots (this is a text reference). Zero broken internal links (all "Related" links explicit).

## Scope target
A 15-minute v1 should include: overview, request path/auth, parameters table (may be incomplete on the `destination` polymorphism), a request example in curl form, a response example and partial response table, and a stub errors table with 4-5 of the 11 codes. Missing: full polymorphism docs, all 11 error codes, state machine ASCII diagram, idempotency section polish, and language-tabbed examples beyond curl.
