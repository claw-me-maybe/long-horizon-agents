# 90+ Day Collections Letter Series and Aging Report — Ridgeway Orthodontic Supply

## Occupation
- **SOC:** 43-3021
- **Title:** Billing and Posting Clerks

## Scenario
Ridgeway Orthodontic Supply (a B2B distributor of dental/ortho consumables serving ~1,200 practices across the Mid-Atlantic, HQ Richmond, VA) has seen accounts receivable stretch as clinics slow payments. You are Corinne Lavigne, billing clerk with 6 years at Ridgeway, reporting to Controller Nadia Petrenko. On April 16, 2026, Nadia asks you to produce by April 21: (a) an updated aging report, (b) a tiered collections letter series for 90+ day accounts, and (c) a shortlist of accounts for legal referral. Ridgeway's policy is internal collections through 120 days, then a decision: payment plan, placement with Altus Collections (third-party), or legal.

## Inputs

**Aging snapshot 04/16/2026 (top 15 delinquent accounts, >60 days):**

| Cust # | Practice | Contact | Total AR | Current | 1-30 | 31-60 | 61-90 | 91-120 | 121+ | Last pmt | Notes |
|---|---|---|---|---|---|---|---|---|---|---|---|
| 40211 | Chesapeake Smiles Ortho | Dr. Raya Oduya | $14,820.42 | 0 | 0 | 0 | 4,100 | 6,220 | 4,500 | 2026-01-18 | Called 3x, no return. Front desk says "check with doctor." |
| 41144 | Tidewater Pediatric Dental | Marisol Reyes (office mgr) | $8,330.10 | 2,200 | 3,100 | 0 | 0 | 3,030 | 0 | 2026-03-22 | Paying current but ignoring 91-120 invoice #22-14821. |
| 42007 | Bluefield Orthodontics | Dr. Neil Chun | $22,440.75 | 0 | 0 | 0 | 0 | 0 | 22,440.75 | 2025-11-04 | Practice sold to MSO Nov 2025; new owner disputes. |
| 43019 | Riverbend Family Dental | Alison K. (bookkeeper) | $4,915.88 | 0 | 0 | 1,200 | 2,100 | 1,615.88 | 0 | 2026-02-11 | Responsive; claims waiting on insurance reimbursements. |
| 43502 | Coastal Ortho Partners | Dr. Evan Park | $31,120.00 | 18,000 | 0 | 0 | 0 | 13,120.00 | 0 | 2026-04-02 | Largest customer. Paid most recent invoice current. 91-120 is disputed on shipping charges. |
| 44100 | Shenandoah Dental Group | Ted Okafor | $2,040.11 | 0 | 0 | 0 | 0 | 0 | 2,040.11 | 2025-09-30 | No response to any contact since Jan. Phone disconnected. |
| 44812 | Smile Valley Pediatric | Dr. Padma R. | $6,770.55 | 0 | 0 | 0 | 3,200 | 3,570.55 | 0 | 2026-02-19 | Was on payment plan Oct 2025 - Feb 2026; missed last 2 |
| 45033 | Mountain Ridge Orthodontics | Ginny L. | $1,110.00 | 0 | 0 | 0 | 1,110 | 0 | 0 | 2026-02-01 | New account, first late. |
| 45701 | Arlington Dental Associates | Mr. S. Lin | $9,860.20 | 3,300 | 0 | 0 | 2,420 | 4,140.20 | 0 | 2026-03-14 | Mixed: current + aging. Responsive but slow. |
| 46120 | Northern Virginia Ortho | Dr. Aline B. | $18,200.80 | 0 | 0 | 0 | 0 | 10,200 | 8,000.80 | 2025-12-08 | Attorney on retainer reportedly; careful. |
| 46900 | Piedmont Smiles | Dr. J. Whitehorse | $3,250.00 | 0 | 0 | 0 | 0 | 3,250 | 0 | 2026-02-03 | Paid plans historically. New hire bookkeeper. |
| 47011 | Shore Oral Surgery | Practice mgr Gina T. | $12,400.00 | 0 | 0 | 6,200 | 6,200 | 0 | 0 | 2026-03-28 | Growing steadily. No dispute. |
| 47250 | Charlottesville Ortho Center | Dr. Wade M. | $5,100.40 | 0 | 0 | 0 | 0 | 2,500 | 2,600.40 | 2025-10-17 | Retiring practice; sale pending. |
| 48003 | Richmond Kids Dental | Hector A. | $1,905.00 | 0 | 0 | 0 | 1,905 | 0 | 0 | 2026-02-22 | Good history. One disputed invoice (wrong SKU shipped). |
| 48500 | Capital Orthodontics | Dr. Eunice M. | $7,470.25 | 0 | 0 | 0 | 0 | 7,470.25 | 0 | 2026-01-05 | Dr on maternity leave; office manager temp. |

**Policy reference (Ridgeway Credit Policy v3, 2024-06):**
- 60 days: soft reminder (statement + note).
- 90 days: first formal letter; hold new shipments unless approved by Nadia.
- 120 days: second formal letter; referral decision to Nadia (payment plan / Altus / legal).
- Interest: 1.5%/month after 60 days per T&Cs (if collected at all).
- Disputes must be routed to Nadia; do not dun disputed invoices until resolved.

**Constraints:**
- Legal referral threshold: Nadia has said anything <$3,000 is not worth legal; Altus takes 25%.
- Tone: firm but collaborative; Ridgeway values long-term customer relationships.
- FDCPA does not apply to Ridgeway directly (first-party, commercial), but Nadia wants tone consistent with its spirit.
- Nadia has not yet decided on account 42007 (Bluefield — sold practice, new owner disputes).

## Artifact specification
Produce a three-part package:

1. **Aging report (reformatted and analyzed)**
   - Summary header: total AR, amount 90+, % of AR that is 90+, count of accounts 90+
   - Table: accounts 60+ with clean columns, last-pmt, contact
   - Short commentary (3-5 bullets): trend notes; concentration (Coastal is largest); disputed vs. ignored vs. paying-current-but-not-old

2. **Collections letter series (three template letters)**
   - **Letter A — 90-day first formal notice.** Collaborative tone; invites dispute; offers payment plan; notes hold on new shipments.
   - **Letter B — 120-day second formal notice.** Firmer; names the specific invoice(s); names the next step deadline (e.g., "by May 5 or account referred to third party collections"); still offers payment plan.
   - **Letter C — Pre-referral final notice.** Clear, firm, not threatening; names date of referral (Altus or legal) if no response.

   Each letter: Ridgeway letterhead placeholder, date, customer block, subject line, body with invoice table (itemized), payment instructions (online + mail), signature block, disclosures (interest accrued to date, per T&Cs).

3. **Referral shortlist memo to Nadia**
   - Per account: recommended action (continue internal / payment plan / Altus / legal / write-off), reason, dollar value, risk factors.
   - Special handling items:
     - 42007 Bluefield — hold pending Nadia's decision on new-owner dispute.
     - 43502 Coastal — disputed shipping; do NOT send Letter A/B; route dispute.
     - 48003 Richmond Kids — wrong-SKU dispute; route to correction, not collections.
     - 44100 Shenandoah — disconnected phone, no contact possible; discuss skip-trace or write-off.
     - 45033 Mountain Ridge — first-time late, small balance; reminder only, not formal letter.

Tone: respectful, factual, businesslike. No threats. Do not demand payment on disputed amounts.

## Output format
Single Markdown file with tables and three letter templates, ~4 pages rendered (260-380 lines source).

## Iteration targets
1. **Don't dun disputed amounts** — v1 may uniformly apply the letter series; v2 correctly excludes 43502 and 48003 from dunning and routes them via the memo.
2. **Tier letters correctly to account state** — Letter A for 91-120 only; Letter B for 121+ with prior Letter A on file; Letter C for pre-referral. Small first-time late accounts (45033) get a friendly reminder, not Letter A.
3. **Recommend the right next step per account** — legal threshold ($3,000) applied; 44100 Shenandoah ($2,040) is below threshold and points to write-off or Altus, not legal; 42007 and 46120 are the legal candidates if they don't respond.
4. **Include correct per-invoice detail** — letters should reference specific invoice numbers and amounts, not a vague total.
5. **Preserve the relationship where the account is responsive** — Tidewater (41144), Riverbend (43019), and Arlington (45701) are communicating; letter B-level firmness is inappropriate; offer payment plans.
6. **Calculate 1.5%/month interest disclosure correctly** — show interest-to-date on letters where applicable; acknowledge Ridgeway's discretion on whether to collect.

## Success criteria
- No disputed invoice is dunned in any letter.
- Legal-referral shortlist applies the $3,000 threshold correctly.
- Letters A/B/C escalate in tone appropriately without becoming threatening.
- Every account in the top 15 has a recommended action in the memo.
- Letters contain real invoice numbers, amounts, and dates — not placeholders.
- Aging commentary names concentration risk (Coastal Ortho is ~14% of delinquent AR if we count all aging).

## Scope target
A v1 at ~15 minutes should contain: reformatted aging report with commentary, complete drafts of Letters A and B (Letter C can be shorter), and a first-pass referral shortlist covering all 15 accounts. Refining per-account recommendations, calculating per-account interest, and fully handling the disputed-vs-dunning distinction belong to iteration.

## Example of v1 failure modes
- Sending Letter B to 43502 (Coastal) despite their disputed shipping charges being unresolved.
- Sending Letter A to 45033 (Mountain Ridge, first-time late, small balance, 61-90 days) — this is disproportionate and damages the relationship.
- Sending any letter to 48003 (Richmond Kids) without first routing the wrong-SKU dispute.
- Treating 42007 (Bluefield) as a standard delinquent account instead of a practice-sale dispute requiring Nadia's decision.
- Recommending legal referral for 44100 (Shenandoah, $2,040) despite the $3,000 threshold.
- Recommending legal referral for 47250 (Charlottesville, retiring) without pausing to consider pending practice sale as a recovery path.
- Forgetting to apply the "hold new shipments" note in Letter A to customers who are otherwise paying current (e.g., 41144 Tidewater — holding their new orders while they have ignored one old invoice may be disproportionate; propose a partial hold or none).
- Computing interest on the aggregate AR balance rather than on the specific delinquent invoices.

## Common pitfalls to avoid
- Do not threaten legal action in Letter A or B; only Letter C mentions referral, and it must be factual (date, third party name) not threatening (consequences, damage to credit).
- Do not use the phrase "final notice" on Letter B; save for Letter C.
- Do not draft letters that imply the customer's dispute is invalid; where disputes exist, the letters are not sent and the memo handles the dispute separately.
- Do not bundle multiple invoices into a single amount due without itemization; each invoice must be line-itemed with its date and amount so the customer can reconcile.
- Do not apply interest unilaterally without noting Nadia's discretion; the policy permits but does not require.
- Do not forget Ridgeway's IPA-level customer relationships; some of these practices are also referral sources for Ridgeway's sales team, and collections tone should not torpedo those relationships.

## Evaluator notes (context for scoring, not for the model)
- The 43-3021 role has an unusually rich iteration surface in collections because tone, sequencing, and account-state awareness all matter, and a one-size letter series is the default junior output. Iteration feedback tightens this to an account-state-aware program with tailored tone and correct disputed-vs-dunning discrimination.
- Ridgeway Orthodontic Supply, all practices, and named individuals are fictional. The 91-120/121+/legal-threshold/third-party structure is typical of B2B collections; the 1.5%/month late fee, Altus's 25% commission, and the $3,000 legal threshold are illustrative.
- A strong v2: correctly excludes disputed accounts from dunning; applies Letter B/C to true non-responders; offers payment plans to communicating customers; applies the $3,000 threshold to legal-referral recommendations; and keeps tone collaborative for long-term-relationship preservation.

## Letter tone gradients (examples — not templates)
- Letter A opening: "Our records show a balance of $[X] on invoice #[Y] dated [date] that is now past due. We understand things come up — please reach out if there is a billing issue, or if you'd like to discuss payment options."
- Letter B opening: "Following our notice dated [date], invoice #[Y] for $[X] remains unpaid and is now [days] days past due. To keep your account in good standing and shipments uninterrupted, please remit payment or contact us to arrange a payment plan by [date]."
- Letter C opening: "Invoice #[Y] dated [date] in the amount of $[X] has been unpaid for [days] days and has not received a response to our prior notices of [date] and [date]. Unless we hear from you by [date], this account will be referred to [third party] for further collection."

The gradient escalates in firmness but never in threat; every letter offers contact and a path to resolution.

## Per-account expected recommendations (reference for evaluator, not a solution the model should copy verbatim)
| Cust # | Expected recommendation | Reasoning |
|---|---|---|
| 40211 Chesapeake Smiles | Letter B (91-120 past Letter A); pre-referral posture | Ignored 3 prior calls |
| 41144 Tidewater | Letter A (selective: only invoice #22-14821); offer payment plan | Paying current; responsive; relationship risk |
| 42007 Bluefield | HOLD — route to Nadia | Practice sold; new owner disputes; not a standard collections case |
| 43019 Riverbend | Offer payment plan; do not send Letter B yet | Responsive; cashflow-pending; relationship valued |
| 43502 Coastal | DO NOT DUN; route dispute on shipping charges | Largest customer; dispute must be resolved first |
| 44100 Shenandoah | Altus or write-off; not legal | Below $3,000; phone disconnected; no recovery path in-house |
| 44812 Smile Valley | Letter B; restructure payment plan proposal | Missed plan payments 2x; trust broken but amounts moderate |
| 45033 Mountain Ridge | Friendly reminder only; NOT Letter A | First-time late; relationship-building account |
| 45701 Arlington | Payment plan offer; Letter A for the oldest invoice if plan not accepted within 10 days | Mixed aging; responsive |
| 46120 Northern Virginia | Letter C posture; coordinate with counsel before legal referral | Attorney-on-retainer context; proceed carefully |
| 46900 Piedmont | Letter A; offer payment plan given new-hire bookkeeper context | Small balance; historical payer; likely process issue |
| 47011 Shore | No letter needed; no dispute or ignored contact | Normal aging; growing customer |
| 47250 Charlottesville | Hold pending practice sale; flag to Nadia | Practice sale pending could pay off AR |
| 48003 Richmond Kids | DO NOT DUN; route correction for wrong-SKU dispute | Good customer; fix the dispute |
| 48500 Capital | Extended grace; offer flexible plan due to maternity-leave temp coverage | Responsive prior history; temp ops |

## What distinguishes this from a basic dunning letter template set
- Account-state awareness: the letter series is not applied uniformly; each account is mapped to a specific gate and letter.
- Dispute discipline: disputed invoices are never dunned; the memo routes them separately.
- Legal threshold honored: $3,000 minimum means 44100 and a few others are not legal candidates regardless of age.
- Relationship preservation: long-term customers, first-time late, or small-balance accounts receive proportionate tone.
- Interest disclosure handled explicitly: policy permits; each letter decides whether to invoke.

## Final sanity checks before handing to Nadia
- No disputed invoice appears in any letter.
- No letter contains legal-consequence language.
- Every letter's invoice table matches the aging report line for that account.
- Memo recommendations sum to a coherent treatment of all 15 top accounts.
- Referral shortlist respects the $3,000 floor for legal.
