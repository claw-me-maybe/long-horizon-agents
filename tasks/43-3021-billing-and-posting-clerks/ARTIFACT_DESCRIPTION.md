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
