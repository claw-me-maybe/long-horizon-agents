# Escalated Case Resolution Writeup with Root-Cause Analysis — BrightNest Home Security, Case #CR-2026-04188

## Occupation
- **SOC:** 43-4051
- **Title:** Customer Service Representatives

## Scenario
BrightNest Home Security (a DIY smart-home alarm provider, HQ in Austin, TX, ~180,000 active subscribers) requires CSRs to produce a case resolution document for any case that exceeds 3 touches OR involves a billing dispute over $100 OR results in an escalation to Tier 2 / Retention. You are Keisha Adeyemi, a Tier 2 CSR with a specialization in billing. Case #CR-2026-04188 involves customer Mr. Desmond Park (subscriber since 2019-08-14), a $237.55 disputed charge, 6 touches across 11 days, and a supervisor involvement. The case closed April 16, 2026. Your writeup will be reviewed by your team lead Rafael Chen for quality assurance and by the Product Ops team to identify any systemic issues.

## Inputs

**Case metadata:**
- Case ID: CR-2026-04188
- Customer: Desmond Park, Plan "SecurePlus Annual" (autorenewed 2026-02-14)
- Tenure: 6 years, 8 months
- Lifetime value: $2,387 (est.)
- NPS from last survey (Nov 2025): 9/10
- Dispute amount: $237.55
- Channel mix: 3 phone, 2 chat, 1 email
- Opened: 2026-04-05; Closed: 2026-04-16

**Touch-by-touch log (condensed):**

*Touch 1 — 04/05, 9:42 AM, phone, 14 min, CSR: Bao L. (Tier 1)*
Mr. Park: "I was charged $237.55 for renewal but your website said the annual plan was $199 when I signed up. I want it refunded."
Bao offered a $25 goodwill credit; Mr. Park declined. Case opened, notes: "Cust upset, wants full price-match refund. Will review records." Promised callback by 04/07.

*Touch 2 — 04/08, 10:15 AM, customer-initiated chat, 22 min, CSR: Marco V. (Tier 1)*
Mr. Park had not received callback. Marco found no callback task in system. Marco reviewed pricing history: annual plan was indeed $199/yr when Mr. Park subscribed in 2019; underwent 3 price increases (2021: $209, 2023: $219, 2026: $237.55). Marco told Mr. Park the price had increased and offered a $30 credit. Declined. Escalation flag set, Tier 2 queue.

*Touch 3 — 04/10, 2:08 PM, phone outbound, 19 min, CSR: You (Keisha, Tier 2)*
You reviewed the account. You found:
- Original 2019 T&Cs: price guarantee for 24 months, then "may change with 30 days notice."
- System-generated price-change emails sent 2021-01-04, 2023-01-06, 2026-01-10 to park.d@gmail.com.
- 2026-01-10 email bounced (mailbox full). No retry or alternative-channel attempt by system.
- No SMS or in-app notification on file; customer never opted in, never prompted.
You acknowledged the bounced email to Mr. Park; he confirmed his inbox was briefly full in early January after a trip. He stated: "If I had known, I would have shopped around. I feel trapped." You offered: (a) full refund of $237.55 + cancellation, OR (b) keep service at the grandfathered 2023 rate of $219 + one-time $18.55 credit. Mr. Park asked for time.

*Touch 4 — 04/12, 4:30 PM, email inbound.*
Mr. Park: "I'll consider option (b) if you can also give me the lower 2021 rate for this year ($209). Otherwise I want the full refund and to cancel."

*Touch 5 — 04/14, 11:22 AM, phone outbound, 12 min, CSR: You.*
Consulted with Retention Supervisor Raul Obregon. Approved: keep at 2019 rate of $199 for current year only, standard price increases resume 2027. Offered to Mr. Park. Accepted verbally.

*Touch 6 — 04/16, 9:05 AM, phone outbound, 7 min, CSR: You.*
Confirmed refund of $38.55 processed to original payment method (completes move from $237.55 paid down to $199.00 for the year). Provided confirmation # REF-7712804. Sent summary email. Mr. Park: "Thank you for making it right." Case closed.

**Product Ops context (for your RCA):**
- Bounce-handling logic: single-retry after 24 hrs, then no further attempt. No fallback to SMS/in-app/postal.
- Last 90 days: 1,847 pricing-notification emails bounced systemwide; no known fallback triggered.
- Grandfathering authority: Retention Sup+ only. Tier 2 CSRs capped at $50 goodwill.

## Artifact specification
Produce a case resolution writeup with:
1. **Case header** — ID, customer (first name + last initial only in shareable sections), tenure, product, dates, touch count, resolution value ($38.55 refund + rate retention)
2. **Customer-facing summary** (short, suitable for email-back and for QA review)
3. **Internal detailed timeline** — per touch: date/time, channel, CSR, key exchange, outcome
4. **Root-cause analysis** — 5 Whys or fishbone style; distinguish *incident cause* (this customer), *process cause* (bounce-handling gap), *policy cause* (notification channels)
5. **Resolution and terms** — what was offered, what was accepted, authority used, confirmation numbers
6. **Systemic recommendations to Product Ops** — concrete proposals tied to the 1,847-bounce finding
7. **Metrics impact** — touches, handle time, CSAT not-yet-measured, cost of resolution ($38.55 direct + Sup time + est. retention of $2,387 LTV customer)
8. **Lessons for team training** — 2-3 bullets Rafael can reuse
9. **Attachments referenced** — confirmation REF-7712804, outbound email 04/16, audit of bounce logs

Tone: professional, customer-respectful, process-critical (about the gap) but not blame-oriented toward Bao or Marco. Avoid PII overexposure in the shareable summary.

## Output format
Single Markdown file, ~3 pages rendered (200-300 lines source).

## Iteration targets
1. **Separate incident cause from systemic cause** — v1 may say "customer didn't know about price increase"; v2 traces it to a single-retry bounce-handling logic with no fallback, and ties the fix to the 1,847-bounce systemic signal.
2. **Get the 5 Whys right** — at least five levels of "why" that lead to actionable system change, not stopping at "email bounced."
3. **Call out the Touch-1 callback miss** — Bao's promised callback was not tasked; this is a CRM configuration or training issue, not a Bao personal failure.
4. **Apply PII discipline** — in the customer-facing summary and the Product Ops-distributed sections, use "Mr. P." or first name + last initial; full name only in the internal timeline.
5. **Quantify systemic recommendations** — e.g., "add SMS fallback for pricing notifications; estimated cost $0.009/msg × 1,847/qtr = ~$16.62/qtr"; not "improve communication."
6. **Distinguish what required Retention Sup authority from what Tier 2 could have done alone** — Tier 2 was capped at $50 goodwill; the $199 grandfathering required escalation. Make this traceable.

## Success criteria
- Root-cause analysis reaches a system-level issue, not a customer-level or CSR-level one.
- Every touch appears in the timeline, including the missed callback.
- Systemic recommendations are actionable and quantified.
- PII is appropriately scoped by audience.
- Resolution math is correct: paid $237.55, target $199.00, refund $38.55, plus future grandfathering noted.
- Tone respects Bao and Marco while still naming the callback-tasking gap.

## Scope target
A v1 at ~15 minutes should contain: case header, customer-facing summary, full internal timeline with all 6 touches, a draft root-cause analysis (at least 3 levels deep), resolution terms, and at least 2 systemic recommendations. Tightening the 5 Whys to 5 full levels, quantifying the systemic recs, and polishing the PII discipline belong to iteration.
