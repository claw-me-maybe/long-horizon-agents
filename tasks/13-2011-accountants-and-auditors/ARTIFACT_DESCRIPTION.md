# Q2 2026 Revenue Recognition Audit Workpaper — Helmwright SaaS Inc.

## Occupation
- **SOC:** 13-2011
- **Title:** Accountants and Auditors

## Scenario
You are the senior auditor at Castlewood & Pemberton LLP assigned to the Q2 2026 interim review of Helmwright SaaS Inc., a mid-market B2B analytics vendor preparing for its IPO in Q1 2027. The engagement partner, Reena Kothari, has flagged revenue recognition (ASC 606) as a significant risk after Helmwright's new CFO restructured several multi-element arrangements in May. You must produce the revenue testing workpaper that will support the auditor's sign-off on the 10-Q and feed into the year-end substantive plan.

## Inputs

**Engagement metadata**
- Client: Helmwright SaaS Inc. (Delaware C-corp, fiscal year = calendar year)
- Period under review: April 1 – June 30, 2026
- Materiality: $180,000 (overall); $9,000 (clearly trivial threshold)
- Prior-year qualified opinion? No
- Workpaper index: R-300.02

**Revenue trial balance excerpt (Q2 2026, USD)**
| GL Account | Description              | Amount      |
|-----------:|--------------------------|------------:|
| 4010       | Subscription — Annual    | 12,840,300  |
| 4020       | Subscription — Monthly   | 2,105,750   |
| 4030       | Implementation fees      | 1,680,000   |
| 4040       | Premium support          | 420,000     |
| 4050       | Professional services    | 965,400     |
| 4099       | Deferred revenue release | 3,012,800   |

**Sample selection (15 contracts, stratified)**
Representative excerpt (full population is 847 contracts, $18.0M):
| Contract ID | Customer               | TCV       | Signed   | Term    | Modules                        |
|-------------|------------------------|-----------|----------|---------|--------------------------------|
| HEL-2026-204 | Brinkerhoff Foods     | $480,000  | 5/14/26  | 36 mo   | Core + Forecast + Impl + PS    |
| HEL-2026-211 | North Anchor Credit U | $125,000  | 6/02/26  | 12 mo   | Core + Premium Support         |
| HEL-2026-218 | Quellstream Biotech   | $1,200,000| 4/22/26  | 24 mo   | Enterprise + Impl + Training   |

**Known items from fieldwork**
- New May 2026 standard contract added a "24-month price lock" clause whose impact on distinct performance obligations was not reviewed by management's technical accounting memo.
- Three contracts (HEL-2026-204, HEL-2026-218, HEL-2026-231) include implementation fees >$150K where the SSP allocation was performed by the CFO's spreadsheet, not the billing system.
- Deferred revenue rollforward does not tie to subledger by $41,200 (debit difference).

## Artifact specification
Standard Big-4-style audit workpaper. Required sections:
1. **Header block** (client, period, W/P reference, preparer, reviewer, dates)
2. **Objective** (specific assertions tested: existence, cutoff, accuracy, valuation)
3. **Source of data** and IPE (Information Produced by Entity) considerations
4. **Procedures performed** (numbered, tied to assertions)
5. **Sample methodology** (selection method, sample size justification, stratification)
6. **Detailed testing table** with tickmarks, SSP recalculation, and exceptions
7. **Exceptions summary** with proposed adjustments (PAJE)
8. **Conclusion** on assertion-by-assertion basis
9. **Cross-references** to related workpapers (revenue walk, deferred revenue rollforward, management memo)

Tone: terse, evidentiary, citing ASC 606-10-25-19 through -22 for distinct performance obligations and ASC 606-10-32-31 for SSP allocation where relevant. Use tickmark legend.

## Output format
Markdown file rendering a formal workpaper. Target: 1,400–1,800 words plus tables and tickmark legend.

## Iteration targets
1. v1 likely over-describes procedures but under-documents *why* the sample size of 15 meets the expected-error-based sizing in the firm's methodology — add that justification in the sampling section.
2. The SSP recalculation for HEL-2026-204 needs an explicit side table showing management's allocation vs. auditor's recalc rather than a narrative paragraph.
3. Exception 2 (the $41,200 deferred revenue tie-out difference) is not clearly classified as known-vs-likely misstatement; fix.
4. Tie the "price lock" clause conclusion to a specific ASC 606 paragraph rather than citing "the standard."
5. Conclusion section conflates existence and accuracy; split.
6. Add a tickmark legend table rather than defining tickmarks inline.

## Success criteria
- Procedures map 1:1 to specific financial statement assertions and would survive a peer review.
- Sample selection has documented statistical basis, not just a judgmental handwave.
- Every exception either has a PAJE, a rationale for passing, or a clear path to resolution.
- SSP allocation analysis shows both management's approach and the auditor's independent recalculation, with variances quantified.
- Cross-references to supporting workpapers are specific (e.g., "R-310.01, §3") not generic.
- Conclusion could stand up to PCAOB inspection — no conclusions unsupported by documented procedures.

## Scope target
v1 at ~15 minutes should contain: filled header, objective with 4 assertions named, procedures section (5–7 numbered procedures), a detailed testing table with at least the 3 highlighted contracts populated with tickmarks, the two known exceptions written up with proposed PAJE amounts, and a draft conclusion per assertion. Approximately 900–1,100 words on the first pass, with tickmark legend and SSP recalculation deferred to iteration.
