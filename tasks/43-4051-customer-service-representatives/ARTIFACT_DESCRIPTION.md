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

## Example of v1 failure modes
- Stopping the 5 Whys at "email bounced" — which leads only to "retry bounced emails more aggressively." A full analysis reaches "our notification architecture assumes email is the sole reliable channel and has no fallback when the only channel fails."
- Listing recommendations as aspirations: "improve communication with customers about price changes." An iteration-worthy version is specific: "Implement SMS fallback for any pricing notification that bounces; estimated volume 1,847 bounces/90 days, estimated cost $16.62/qtr at $0.009/SMS."
- Blaming Bao L. for the missed callback instead of diagnosing the CRM config gap (no callback task was created, so the callback was never on anyone's queue).
- Leaking Mr. Park's full name, email, and the bounced-mailbox detail in the Product Ops-distributed RCA, violating PII minimum-necessary.
- Calculating the refund incorrectly: Mr. Park paid $237.55, final rate $199.00, refund must be $38.55 — not $237.55 minus the goodwill offered or some intermediate number.
- Claiming the supervisor escalation was "standard practice" when in fact Tier 2 was capped at $50 goodwill and the $199 grandfathering exceeded that authority.
- Treating this as a won retention without quantifying the estimated LTV preserved ($2,387 est.) against the cost of resolution ($38.55 direct + ~30 min Sup time + Tier 2 time).

## Common pitfalls to avoid
- Do not quote Mr. Park's bounced-mailbox reason in any audience-broader-than-Keisha artifact; it's sensitive context, not a blame point.
- Do not propose customer-side action items ("Mr. Park should update his email") in the root-cause analysis; the RCA is about our systems.
- Do not claim the issue is "resolved to the customer's satisfaction" without noting the follow-up survey that is not yet returned.
- Do not conflate grandfathering (rate retention for this customer, this year) with a blanket policy change.
- Do not produce a system recommendation that exceeds CSR authority (e.g., committing to a new SMS fallback without Product Ops and Compliance approval); recommend, don't mandate.

## Evaluator notes (context for scoring, not for the model)
- This is the strongest iteration artifact for 43-4051 because "case notes" alone are transactional, but a multi-touch case with RCA and systemic recommendation is where CSR craft shows: depth of root-cause thinking, PII discipline, escalation-path literacy, and quantification of resolution cost and LTV preservation.
- BrightNest Home Security, Mr. Park, and all named CSRs and supervisors are fictional. The 1,847-bounce systemic signal and the grandfathering-by-tenure resolution are realistic.
- A strong v2 reaches a system-architecture-level root cause (single-channel notification with inadequate fallback), proposes a costed fix, and preserves PII appropriately across the internal, team-training, and Product Ops audiences.

## Audience segmentation (use for PII and tone discipline)
- Customer-facing summary: Mr. P. or "you"; positive, forward-looking; references the final resolution; omits internal process details.
- Internal timeline (Rafael and QA only): full name; all details; no redaction.
- Product Ops distributed RCA: anonymized to "a 6-year tenure customer"; systemic focus; no individual case narrative detail.
- Team training lessons: fully anonymized; pattern-focused ("when a callback is promised, confirm a task is created").

## Suggested 5 Whys structure (reference — the model should think through it itself)
1. Why did Mr. Park receive an unexpected price increase? Because he did not see the 2026-01-10 notification email.
2. Why did he not see it? Because his mailbox was briefly full, and the email bounced.
3. Why did the bounce lead to no notification reaching him? Because our bounce-handling logic attempts a single retry after 24 hours, then silently stops.
4. Why is there no fallback to another channel? Because the notification architecture assumes email is the sole reliable channel.
5. Why is that architecture unexamined? Because no dashboard or alert surfaces "pricing notification delivery rate" to Product Ops; the 1,847-bounce quarterly pattern has been invisible.

An even sharper v2 might add a 6th "why" at the policy level: because notification-delivery-rate is not a tracked SLA and has no owner.

## Quantification cues for the systemic recommendation
- Cost of SMS fallback: ~$0.009/message × 1,847 bounces/quarter = ~$16.62/quarter.
- Customer-retention value protected: case-level LTV $2,387 × retention rate × bounce-rate-exposed customers — rough order of magnitude even a small percentage translates to thousands in preserved ARR.
- Implementation effort: single integration work item (CRM-to-SMS-gateway); estimate 2-4 eng sprints.
- Not a recommendation: replacing email as primary. Email remains primary; SMS is fallback when email bounces.

## Post-incident follow-up plan (required in the artifact)
- NPS/CSAT survey scheduled 04/23 (7 days post-close) — separate from the writeup, but cited.
- 30-day check-in call from Keisha on 05/16 — calendared as soft-touch retention.
- Account annotation: "rate grandfathered at $199 for 2026; standard increases resume 2027."
- Flag on account for future escalations: prior dispute history in good resolution; prefer phone contact; daughter-in-neighborhood (note: only if patient-like relevance applies; in this case no care partner, so drop).

## What distinguishes this from a simple ticket close-out
- Multi-touch timeline with behavioral detail, not just resolution status.
- Root cause reaches system architecture, not customer behavior.
- Audience-segmented output with explicit PII discipline.
- Quantified systemic recommendation, not generic "improve processes."
- Team-training lesson extraction, making the case useful as a teaching artifact.

## Final sanity checks before submitting to Rafael
- Refund math: $237.55 − $199.00 = $38.55. Confirmation REF-7712804 noted.
- Every touch logged with CSR, channel, duration, and key exchange.
- RCA reaches a system-level conclusion, not a customer-level or CSR-level one.
- PII scoped appropriately per audience; no leakage into Product Ops-distributed sections.
- Systemic recommendations costed and actionable.
- Team-training lessons are pattern-level, not case-level or person-level.
- Touch-1 missed callback is acknowledged as a CRM tasking gap, not as Bao's personal failure.
