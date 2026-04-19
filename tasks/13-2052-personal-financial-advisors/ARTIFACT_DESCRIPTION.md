# Retirement-Readiness Plan — The Okonkwo-Steinberg Household, Age 58 / 55

## Occupation
- **SOC:** 13-2052
- **Title:** Personal Financial Advisors

## Scenario
You are a CFP® at Glenfinnan Wealth Partners in Minneapolis. A long-time client couple, Adanna Okonkwo (58, dentist, solo practice) and Jonah Steinberg (55, tenured community-college faculty), have asked for a retirement-readiness plan ahead of their April 30, 2026 review meeting. Adanna wants to sell her practice in mid-2029; Jonah plans to retire at 62 with a pension. They have one dependent daughter, Ngozi (19, sophomore at UMN, 529-funded). They have expressed two goals that are in tension: retire together in 2029 while keeping their lake cabin, and leave a seven-figure legacy to Ngozi.

## Inputs

**Household balance sheet (3/31/26)**
| Asset / Liability             | Value (USD)   | Notes                                        |
|-------------------------------|---------------|----------------------------------------------|
| Taxable brokerage (Glenfinnan)| 1,240,000     | 67/28/5 stock/bond/cash                      |
| Adanna Solo 401(k)            | 980,000       | Pre-tax; Vanguard TDF 2030                   |
| Jonah 403(b) (TIAA)           | 640,000       | 70/30                                        |
| Roth IRAs (joint total)       | 210,000       | Fully funded annually                        |
| HSA (Adanna)                  | 118,000       | Invested; no distributions taken             |
| 529 (Ngozi)                   | 142,000       | Tuition covered through senior year          |
| Primary residence (Edina)     | 1,050,000     | Mortgage $218,000, 2.875%, 9 yrs remaining   |
| Lake cabin (Brainerd)         | 480,000       | Paid off; $6,400/yr prop tax; rental income 0|
| Dental practice (est. value)  | 1,350,000     | 2025 EBITDA $410K; goodwill heavy            |
| Auto loans                    | (34,000)      |                                              |
| Net worth                     | ~5,978,000    |                                              |

**Cash flow (2025 actuals)**
- Gross income: $612,000 (Adanna $440K K-1, Jonah $172K W-2)
- Pre-tax savings: $74,000 (401(k) + 403(b) + HSA)
- Spending (ex-tax, ex-savings): $218,000
- Federal+state effective rate: 29.4%

**Pension**
- Jonah's MSRS pension at 62: $4,620/mo single-life; $4,010/mo 100% J&S
- COLA: 1.0% annual, capped

**Stated goals and constraints (4/3/26 client meeting notes)**
- Both retire simultaneously July 2029
- Maintain inflation-adjusted spending of $225K/yr net in retirement
- Keep the cabin; refuse to sell
- Leave ≥$1.5M (today's dollars) to Ngozi
- Adanna has family history of early-onset dementia; wants robust LTC plan
- Jonah wants retiree health coverage bridge (retires 7 yrs before Medicare)
- Risk tolerance: moderate; both rattled by 2022 drawdown

**Practice sale assumptions (provided by broker Dominic Haire, CBI)**
- Expected closing: Q2 2029
- Est. sale price $1.2M–$1.5M, structured as 70% cash / 30% 3-yr note at 6.5%
- Capital gains treatment on goodwill; ordinary on receivables

## Artifact specification
A client-facing retirement-readiness plan. Required sections:
1. **Executive summary** — one page: where they stand, the two central trade-offs, the recommended path
2. **Goals and assumptions** — explicitly state inflation, return assumptions, longevity (95 / 97), tax trajectory
3. **Current position** — net-worth statement, allocation vs. target, concentration/liquidity flags
4. **Retirement cash-flow projection** — year-by-year through 2055 in a stylized table; identify the "danger zone" years (gap between retirement 2029 and SS/pension)
5. **Monte Carlo / probability of success** — show success probability for two scenarios (keep cabin vs. sell cabin); explain methodology in plain English
6. **Social Security claiming strategy** — filing ages, rationale, sensitivity to Jonah's pension J&S election
7. **Tax strategy** — Roth conversion runway 2029–2032, QCD eligibility, HSA optimization, practice-sale tax structuring coordination
8. **Risk management** — LTC strategy for Adanna, disability bridge for Jonah, umbrella liability, estate basics
9. **Legacy plan** — path to $1.5M bequest; beneficiary designations audit; 529 endgame
10. **Recommended actions** — prioritized 90-day / 1-year / pre-retirement list, each with owner and deadline

Tone: warm but precise; avoid jargon without explanation; do not be patronizing. Numbers must tie across sections.

## Output format
Markdown document structured for client delivery. Target 2,600–3,400 words plus tables.

## Iteration targets
1. v1 likely presents one base-case cash-flow projection without the cabin-sensitivity comparison; add the side-by-side so the trade-off is visible.
2. The Roth conversion strategy tends to be presented as a single number ("$350K/yr") rather than bracket-fill logic; show the marginal-rate math year by year.
3. LTC recommendation is often a single product pitch — broaden to a decision framework (self-insure vs. hybrid life/LTC vs. traditional LTCi) with cost ranges.
4. Legacy plan often double-counts assets; reconcile to avoid showing the same dollar funding both retirement and bequest.
5. Social Security rationale often ignores the pension's J&S implications on survivor income; integrate.
6. 90-day action list should have owners (client vs. advisor vs. CPA) and specific deadlines, not ambient "soon."

## Success criteria
- The plan honestly addresses the tension between keeping the cabin and the $1.5M bequest, rather than implying they can have both without cost.
- Tax strategy shows a multi-year Roth conversion plan with dollar figures tied to bracket thresholds.
- Monte Carlo results are not just a probability — they include a plain-English interpretation and what levers move the odds.
- Recommendations are prioritized and actionable; not a menu dump.
- Practice-sale transition is coordinated with the cash-flow plan (timing, tax, liquidity).
- Assumptions (return, inflation, longevity) are visible and editable — the client can see what would change the conclusions.

## Scope target
v1 at ~15 minutes should contain: executive summary with the core trade-off named, goals and assumptions table, current-position snapshot, a first-cut cash-flow projection table through 2040, one Monte Carlo scenario described (methodology only), initial Roth conversion thesis, and a draft 90-day action list. Roughly 1,500–1,900 words; LTC product analysis, second Monte Carlo scenario, and full estate reconciliation are iteration work.
