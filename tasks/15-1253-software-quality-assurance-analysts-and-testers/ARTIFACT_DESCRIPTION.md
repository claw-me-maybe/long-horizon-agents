# Release QA Packet: Payment Method Change Flow for Larkspur Subscription Billing

## Occupation
- **SOC:** 15-1253
- **Title:** Software Quality Assurance Analysts and Testers

## Scenario
Larkspur Subscription Billing runs a self-service customer portal for 84,000 active accounts. A release scheduled for May 6, 2026 adds a new payment-method change flow so customers can replace an expired card without opening a support ticket. QA lead Serena Ibarra needs a compact release-quality artifact pack before sign-off because the prior release introduced a silent failure where 3% of card updates never reached the processor and customers were double-billed on the next invoice. The business wants a practical QA package that can be handed to an engineer or tester in one sitting: a test plan, a small set of actionable bug reports, and a starter automation suite.

## Inputs
- **System under test:** customer portal and billing API.

```text
POST /api/v1/payment-methods/verify
POST /api/v1/payment-methods/update
GET  /api/v1/payment-methods/status
GET  /api/v1/invoices/next
```

- **Business rules:**
  - Card updates must be verified with a 6-digit OTP sent by email before the update can be submitted.
  - OTPs expire after 10 minutes and are single-use.
  - A customer may retry verification 5 times before a 15-minute lockout.
  - An update is rejected if the billing address country differs from the account country.
  - A successful update must refresh the next invoice preview within 30 seconds.
  - Saved payment methods are masked in the UI; only last 4 digits are shown.
- **Known risks from the last release:**
  - Duplicate processor submissions when the browser double-clicked Submit.
  - Stale invoice preview after a successful payment-method update.
  - OTP resend button stayed enabled during lockout.
- **Environments:**
  - `dev.larkspurbill.com` is unstable and used only for smoke checks.
  - `qa.larkspurbill.com` is the primary validation environment.
  - `stage.larkspurbill.com` mirrors production data shape but uses sandbox processor credentials.
- **Test data:**
  - Seed customer `qa.customer+update@larkspurbill.com`
  - Seed accounts for US, CA, and UK billing-country coverage.
  - Sandbox card tokens and OTP inbox access are available in Vault path `secret/qa/larkspur/payment-method-change`.

## Artifact specification
A **QA release packet** with three deliverables in one `.md` file:

### Part A: Test plan
Use these H2 sections in order:
1. **Test plan summary** — release name, owner, target date, and what is being validated.
2. **Scope** — in-scope screens/endpoints and explicit exclusions.
3. **Quality risks** — a short ranked list of the top release risks, each with severity and likelihood.
4. **Test approach** — unit vs API vs UI vs end-to-end checks, plus when each is used.
5. **Test cases** — numbered `TC-###` entries in a table, at least 20 cases covering happy path, OTP invalid/expired/reused, double-submit, lockout, country mismatch, invoice refresh, masked display, cancel flow, network failure, and concurrent updates.
6. **Test data & environment** — accounts, inbox access, feature flags, and cleanup/reset expectations.
7. **Entry and exit criteria** — what must be true before QA starts and before release can ship.
8. **Traceability matrix** — map each business rule to one or more test cases.

### Part B: Bug reports
Include a **bug report template** plus 3 example bugs based on the known risks. Each bug report should have:
- title
- environment
- steps to reproduce
- expected result
- actual result
- severity
- priority
- suspected root cause
- attachments/evidence

At least one example bug must describe the duplicate-submit issue and one must describe stale invoice preview.

### Part C: Automation starter
Include one Python `pytest` file that uses `httpx` for API-level checks and one Playwright Python spec for the UI flow. The starter suite should:
- verify OTP success
- reject an expired OTP
- ensure a second Submit click does not create a duplicate update
- assert the masked payment-method display
- check that the invoice preview refreshes after update

Structural requirements: clear type hints where code is shown, deterministic test data, no arbitrary sleeps, and concise comments only where a step is non-obvious. The artifact should read like something a QA engineer could pick up and extend without reworking the structure.

## Output format
Single `.md` file with prose plus code fenced blocks, roughly 320-380 lines total. The document should be directly usable as a release QA packet, not a vague checklist.

## Iteration targets
1. Expand the test cases into a boundary-value table for OTP timing at 9, 10, and 11 minutes, plus retry counts at 4, 5, and 6 attempts.
2. Add a negative test set for malformed request payloads, including empty card token, oversized billing address, and invalid country codes.
3. Convert the traceability matrix into a stronger coverage map that shows which requirements are covered by API, UI, or end-to-end tests.
4. Add a bug triage section that prioritizes defects by customer impact and release blocker status.
5. Harden the automation starter with a flaky-network retry helper and an assertion for idempotency on the update endpoint.
6. Add accessibility checks for the payment-method form labels and error messages.

## Success criteria
- The test plan has at least 20 numbered test cases with preconditions and expected results.
- The bug report examples are specific enough that an engineer could act on them without asking follow-up questions.
- The automation starter contains one API test file and one UI spec with deterministic assertions.
- Every critical business rule is mapped to at least one test case in the traceability matrix.
- Duplicate-submit, expired OTP, and invoice-refresh behavior are all covered explicitly.
- The file stays implementation-oriented and avoids turning into a generic QA essay.

## Scope target
V1 at ~15 min: a short test plan summary, 8-10 test cases, one bug report template with a single example bug, and a skeletal pytest or Playwright starter. Boundary-value analysis, the full traceability matrix, and multiple defect examples come in later iterations.
