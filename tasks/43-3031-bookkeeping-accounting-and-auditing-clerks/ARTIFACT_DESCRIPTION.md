# Month-End Bank Reconciliation and Variance Memo — Pinebrook Dental Group, March 2026

## Occupation
- **SOC:** 43-3031
- **Title:** Bookkeeping, Accounting, and Auditing Clerks

## Scenario
Pinebrook Dental Group (3-location practice in Raleigh-Durham, NC; ~$6.8M annual revenue) closes its books monthly. You are Elena Moretti, the bookkeeper, reporting to CFO/Practice Administrator Kwame Asante. March 2026 books must close by April 20. During the bank reconciliation for the operating account at First Carolina Bank (acct ending 4821), you've uncovered a $3,412.87 unexplained variance between the bank statement balance and the QuickBooks Online balance. Kwame needs a reconciliation package with a variance memo before the April 23 ownership meeting, so he can either sign off or request further investigation.

## Inputs

**Bank statement (First Carolina Bank, operating acct ...4821):**
- Beginning balance 03/01/2026: $184,220.14
- Total deposits: $612,844.09
- Total withdrawals: $589,112.51
- Service charges: $48.00
- Ending balance 03/31/2026: $207,903.72

**QuickBooks Online register, same account:**
- Beginning balance 03/01/2026: $184,220.14
- Total deposits: $616,113.96
- Total withdrawals: $589,161.51
- Ending balance 03/31/2026: $211,172.59

**Variance:** QBO $211,172.59 − Bank $207,903.72 = $3,268.87 book over bank; plus $144.00 in reconciling items not yet matched = investigation total $3,412.87.

**Items identified during reconciliation:**

*Outstanding checks as of 03/31:*
| Ck # | Date | Payee | Amount |
|---|---|---|---|
| 10412 | 03/28 | Henry Schein (supplies) | $1,847.22 |
| 10415 | 03/30 | Piedmont Dental Lab | $928.40 |
| 10416 | 03/31 | Duke Energy | $612.08 |
| 10417 | 03/31 | Payroll — K. Martinez (manual) | $1,204.50 |

*Deposits in transit:*
- 03/31 deposit slip #0331A: $4,218.00 (credit card batch settled 04/02)

*Bank-side items not yet in QBO:*
- 03/31 service charge: $48.00
- 03/15 NSF return: patient payment D. Chen, check #1044, $310.00 (originally recorded as deposit 03/10)
- 03/22 ACH debit: $187.50, memo "WOLFPKAUTH" — unknown vendor
- 03/26 wire transfer in: $2,500.00, memo "INSCLAIM BCBSNC" — matches no AR entry in QBO
- 03/30 interest credit: $4.12

*QBO entries not yet cleared by bank (beyond outstanding checks above):*
- 03/29 deposit recorded: $1,842.19 — credit card batch, matches bank 04/01 deposit of $1,842.19 (will clear next month)
- 03/31 deposit recorded: $2,100.00 — "cash deposit" per staff entry, but no corresponding bank activity on 03/31 or 04/01. Night drop bag never made it to bank? Or duplicate entry?

*Miscellaneous:*
- QBO shows check #10414 cleared for $582.00 on 03/24; bank shows #10414 cleared for $528.00 on 03/24. Likely transposition error.
- A journal entry on 03/18 debits Office Supplies $250.00 and credits Cash $250.00, but no corresponding bank transaction; entered by new front-desk hire Taylor R., memo "petty cash restock — will get receipt."

## Artifact specification
Produce a reconciliation package with:

1. **Cover memo to Kwame Asante** — 1 page:
   - Date, From, To, Re
   - Summary: variance amount, count of reconciling items, recommended action
   - Items requiring Kwame's decision vs. items you can resolve

2. **Bank reconciliation worksheet** — standard format:
   - Bank balance per statement
   - + Deposits in transit
   - − Outstanding checks
   - = Adjusted bank balance
   - Book balance per QBO
   - ± Adjustments (NSF, service charges, interest, unrecorded credits/debits, errors)
   - = Adjusted book balance
   - **Difference** (should be $0.00 after all adjustments)

3. **Reconciling items detail table** — every item with: date, description, amount, action (adjust book / adjust bank / investigate), status

4. **Journal entries to be posted** — formal debit/credit entries for items that will adjust the books (NSF, service charge, interest, the $528 vs $582 check correction, etc.), with account codes

5. **Open investigation items** — things you cannot resolve alone:
   - WOLFPKAUTH $187.50 ACH — origin?
   - BCBSNC $2,500 wire — which claim/patient?
   - $2,100 night-drop — missing or duplicate?
   - Taylor's petty cash JE without receipt

6. **Internal control observations** — brief, non-accusatory notes on process gaps (front desk making JEs without documentation; night drop not reconciled same-day)

Tone: precise, neutral, professional. Do not guess amounts. Keep accounting language correct (debit/credit; outstanding vs. in-transit).

## Output format
Single Markdown file with tables, ~2-3 pages rendered (170-270 lines source).

## Iteration targets
1. **Solve the reconciliation to zero** — v1 may just list items; v2 arithmetically demonstrates that after all adjustments, the difference is $0.00 OR clearly identifies the remaining unexplained residual (likely the $2,100 night drop) as the sole investigation item.
2. **Post correct journal entries** — ensure debits equal credits on every entry; use realistic account names (e.g., 1010 Cash-Operating, 6100 Bank Charges, 1200 AR, 1150 Undeposited Funds).
3. **Classify each item by who resolves it** — self-resolvable (service charge, interest, check transposition) vs. requires-Kwame-or-others (mystery ACH, unidentified wire, missing deposit, undocumented JE).
4. **Handle the check transposition correctly** — it's a $54.00 error ($582 − $528); determine direction and the JE to correct QBO.
5. **Flag the control issues without blaming Taylor** — frame as process fix (require receipt + supervisor approval for any non-AR cash JE), not personal.
6. **Distinguish timing differences from true adjustments** — outstanding checks and deposits in transit are timing; NSF/charge/interest/errors are adjustments; do not conflate.

## Success criteria
- Reconciliation arithmetic is correct and shown step-by-step.
- Journal entries balance (sum of debits = sum of credits for each entry).
- The $2,100 night-drop issue is appropriately flagged as investigation-required, not resolved by assumption.
- Open items are distinguished from resolved items.
- No item is listed twice (e.g., the $250 petty-cash JE appears in the control observations, not as a reconciling item, because it did not flow through the bank).
- Tone is appropriate for a memo to a CFO: concise, confident, no over-apologizing.

## Scope target
A v1 in ~15 minutes should contain: cover memo, the reconciliation worksheet structure with most items plugged in, a reconciling-items detail table, and at least 3 correct journal entries. Polishing the reconciliation-to-zero arithmetic, refining control observations, and clean separation of timing vs. adjustment items belong to iteration.

## Example of v1 failure modes
- Subtracting the $54 check transposition on the wrong side (QBO $582 vs bank $528 — QBO is overstated by $54, so cash in books must decrease by $54).
- Posting the $250 petty-cash JE as a reconciling item (it never flowed through the bank; it's an internal books entry and belongs only in the control observations).
- Treating the $2,100 night-drop discrepancy as "investigate later" without any proposed investigation method (review CCTV at the night-drop, call First Carolina on the 04/01 deposit log, interview staff who prepared the 03/31 deposit).
- Assuming the $2,500 BCBSNC wire is a simple missed AR posting without verifying which member or claim it corresponds to.
- Claiming "WOLFPKAUTH $187.50 is a subscription" without any evidence — the memo is genuinely opaque and requires vendor-master lookup.
- Producing journal entries where debits do not equal credits.
- Listing outstanding checks under "adjustments" rather than "timing differences," conflating the two reconciliation concepts.
- Writing a tone that implies judgment on Taylor R. ("Taylor should not be making JEs") rather than process ("process gap: any non-AR cash JE should require a receipt and controller review").

## Common pitfalls to avoid
- Do not round the reconciliation; it needs to resolve to the cent or leave an explicit residual identified.
- Do not propose a JE to "correct" an amount that is actually within the bank's control (service charges, interest).
- Do not skip the NSF entry — the 03/10 deposit of $310 was reversed and must be reflected in books.
- Do not recommend back-dating entries to 03/31; post them effective the date of discovery with a clear notation.
- Do not attempt to "clean up" the vendor-master question by writing off the WOLFPKAUTH charge; it requires Kwame's authorization and vendor identification first.

## Evaluator notes (context for scoring, not for the model)
- The 43-3031 role is strongly iteration-worthy because reconciliation accuracy is binary (the math either closes or doesn't), but the craft layer — distinguishing timing from adjustment, routing open items to the right party, raising control issues without blame — is where a seasoned bookkeeper is visibly better than a junior one.
- Pinebrook Dental, First Carolina Bank, and all named individuals are fictional. The account structure and the reconciliation pattern are realistic for a small multi-location healthcare practice.
- The scenario deliberately includes items that fall into every reconciliation category: timing (outstanding checks, deposit in transit), adjustments (NSF, service charge, interest), errors (check transposition), unknowns (WOLFPKAUTH, missing deposit), and non-reconciling items (the petty-cash JE that never hit the bank). A competent v2 will correctly sort each item.
- The internal controls observation about front-desk JEs is the most subtle element; it should be present, constructive, and process-framed.

## Account codes (use these in journal entries)
- 1010 Cash — First Carolina Operating
- 1020 Cash — Undeposited Funds
- 1200 Accounts Receivable — Patient
- 1210 Accounts Receivable — Insurance
- 5100 Office Supplies Expense
- 6100 Bank Service Charges
- 7100 Interest Income
- 8100 Bad Debt Expense (NSF write-off; normally first cycle back through AR)

## Expected journal entries (for evaluator reference)
- NSF reversal: Dr 1200 AR — Patient (Chen) $310; Cr 1010 Cash $310. Memo: NSF on ck #1044 dated 03/10.
- Bank service charge: Dr 6100 Bank Service Charges $48; Cr 1010 Cash $48. Memo: March service charge.
- Interest income: Dr 1010 Cash $4.12; Cr 7100 Interest Income $4.12.
- Check #10414 transposition: Dr 5XXX Expense (category of original check) $54; Cr 1010 Cash $54. Memo: correct QBO understatement of withdrawal (bank $528 vs QBO $582).
- Note: the petty-cash JE by Taylor R. ($250) does NOT appear here — it did not flow through the bank and is not a reconciling item. It belongs in the control observations.
- The mystery items (WOLFPKAUTH, BCBSNC wire, $2,100 night-drop) generate no JEs until resolved.

## Reconciliation worksheet (expected structure)
```
Bank balance 03/31:                        $207,903.72
Add: Deposits in transit                    +4,218.00
Less: Outstanding checks                    -4,592.20
                                            ----------
Adjusted bank balance:                     $207,529.52

Book balance QBO 03/31:                    $211,172.59
Less: NSF reversal                             -310.00
Less: Bank service charge                       -48.00
Add:  Interest income                            +4.12
Less: Check #10414 correction                   -54.00
Less: Unrecorded wire in (BCBSNC)*              (pending)
Less: Mystery ACH (WOLFPKAUTH)*                 (pending)
Less: $2,100 night-drop phantom*                (pending)
                                            ----------
Adjusted book balance:                     (to resolve)
```
*Items flagged as pending investigation. Worksheet should resolve to $0 once investigation items are adjudicated.
