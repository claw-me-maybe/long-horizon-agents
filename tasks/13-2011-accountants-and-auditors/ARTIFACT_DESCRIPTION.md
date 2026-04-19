# Q2 2026 Revenue Recognition Interim Review Workpaper — Helmwright SaaS Inc.

## Occupation
- **SOC:** 13-2011
- **Title:** Accountants and Auditors

## Scenario
You are the senior auditor at Castlewood & Pemberton LLP assigned to the Q2 2026 interim review of Helmwright SaaS Inc., a mid-market B2B analytics vendor preparing for its IPO in Q1 2027. The engagement partner, Reena Kothari, has flagged revenue recognition (ASC 606) as a significant risk after Helmwright's new CFO restructured several customer arrangements in May. You must produce the interim revenue review workpaper that will support the 10-Q review conclusion and feed into the year-end audit plan. This is a limited-scope interim review, so the conclusion language should be review-oriented and evidentiary, not full-audit opinion language.

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

**Sample selection (15 contracts, stratified and deterministic)**
Representative excerpt (full population is 847 contracts, $18.0M):
| Contract ID | Customer               | TCV       | Signed   | Term    | Modules                        |
|-------------|------------------------|-----------|----------|---------|--------------------------------|
| HEL-2026-204 | Brinkerhoff Foods     | $480,000  | 5/14/26  | 36 mo   | Core + Forecast + Impl + PS    |
| HEL-2026-211 | North Anchor Credit U | $125,000  | 6/02/26  | 12 mo   | Core + Premium Support         |
| HEL-2026-218 | Quellstream Biotech   | $1,200,000| 4/22/26  | 24 mo   | Enterprise + Impl + Training   |

Sample strata and selection logic:
| Stratum | Definition | Selection rule | Items |
|---------|------------|----------------|------:|
| A | All new or amended contracts with a May 2026 price lock clause, implementation fee > $150K, or management allocation memo variance | Select all items | 3 |
| B | Remaining multi-element contracts with TCV >= $250K | Select the next 7 items ranked by descending TCV, then signed date, then contract ID | 7 |
| C | Residual low-risk subscription and monthly contracts | Select 5 systematic items using a fixed start on the alphabetized contract register (seed = 260630, start = 3, interval = 9) | 5 |

Why 15 items is sufficient:
- It fully covers the identified high-risk stratum and therefore captures the population most likely to contain a revenue misstatement.
- The residual population is homogeneous single-element or low-complexity subscription revenue, so a small systematic sample is adequate for the interim review objective.
- The sample is reproducible from the written rule set, which allows a reviewer to reperform the selection without judgmental substitution.

**Known items from fieldwork**
- New May 2026 standard contract added a "24-month price lock" clause. Treat this as a transaction price / contract modification / allocation question under ASC 606, not as a generic distinct-performance-obligation issue; the workpaper should conclude whether the lock changes the transaction price, creates a modification, or simply confirms fixed pricing.
- Three contracts (HEL-2026-204, HEL-2026-218, HEL-2026-231) include implementation fees >$150K where the SSP allocation was performed by the CFO's spreadsheet, not the billing system.
- Deferred revenue rollforward does not tie to subledger by $41,200 (debit difference). The exception write-up must classify the difference as either a misstatement or a reconciling item, state whether a PAJE is required, and explain the effect on the conclusion.

## Artifact specification
Standard Big-4-style interim review workpaper. Required sections:
1. **Header block** (client, period, W/P reference, preparer, reviewer, dates)
2. **Objective** (specific review assertions tested: existence/occurrence, cutoff, accuracy/allocation, completeness)
3. **Source of data** and IPE (Information Produced by Entity) considerations
4. **Procedures performed** (numbered, tied to assertions and the limited interim review scope)
5. **Sample methodology** (selection method, sample size justification, stratification, reproducible selection rule)
6. **Detailed testing table** with tickmarks, transaction price / allocation checks, and exceptions
7. **Exceptions summary** with explicit classification, PAJE status, and conclusion impact
8. **Conclusion** on assertion-by-assertion basis using review-style language
9. **Cross-references** to related workpapers (revenue walk, deferred revenue rollforward, management memo)

Tone: terse, evidentiary, citing ASC 606-10 guidance on contract modifications, transaction price, and allocation where relevant. Use tickmark legend. Do not drift into full-audit opinion wording or broad distinct-performance-obligation discussion unless the facts actually require it.

## Output format
Markdown file rendering a formal workpaper. Target: 1,400–1,800 words plus tables and tickmark legend.

## Iteration targets
1. v1 should be a credible ~15 minute pass: header, objective, 5 procedures, sample methodology, 3 highlighted contracts in the testing table, the two known exceptions, and a draft conclusion. Keep it to roughly 700-900 words so it reads like a first-pass workpaper rather than a finished memo.
2. The sample methodology needs to be fully deterministic: state the strata, the ranking or randomization rule, and the specific reason 15 items is enough under the firm's expected-error and coverage logic.
3. The HEL-2026-204 allocation analysis needs an explicit side table showing management's allocation versus the auditor's recalculation, with the revenue impact quantified.
4. Each exception row must include a forced disposition field: misstatement or reconciling item, PAJE yes/no, and effect on the conclusion.
5. The "price lock" clause analysis should be framed as transaction price / modification / allocation under ASC 606, not as a distinct-performance-obligation discussion.
6. Add a tickmark legend table rather than defining tickmarks inline.

## Success criteria
- Procedures map 1:1 to specific review assertions and the limited interim review scope.
- Sample selection is reproducible from the written strata and selection rules.
- Every exception is classified consistently, with PAJE status and conclusion effect stated explicitly.
- Allocation analysis shows both management's approach and the auditor's independent recalculation, with variances quantified.
- Cross-references to supporting workpapers are specific (e.g., "R-310.01, §3") not generic.
- Conclusion is review-style, internally consistent, and supported by the documented procedures and exception dispositions.

## Scope target
v1 at ~15 minutes should contain: filled header, objective with 4 assertions named, 5 numbered procedures, a deterministic sample methodology paragraph plus strata table, a detailed testing table with at least the 3 highlighted contracts populated with tickmarks, the two known exceptions written up with disposition fields, and a draft conclusion per assertion. Approximately 700–900 words on the first pass, with the full tickmark legend and expanded allocation side table added in later iteration(s).
