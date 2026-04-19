# Claude Domains — Detailed

Per-occupation weighting for evals of **model ability to iterate on domain-specific artifacts**. Extension of `CLAUDE_DOMAINS.md` — same methodology, applied at SOC detailed-occupation granularity (6-digit codes) instead of SOC major groups (2-digit).

## Purpose

`CLAUDE_DOMAINS.md` is market-weighted but abstract (22 broad buckets). `CODEX_DOMAINS.md` is specific-occupation but has no economic or AI-adoption weighting. This file gives you the **specific-profession granularity of CODEX** with the **market + adoption weighting of CLAUDE**, so each line is a concrete job you could build an eval for, ranked by how much it should matter.

## Method

Same three signals as `CLAUDE_DOMAINS.md`, computed at the SOC **detailed** level:

- **`bls_share`** — occupation's share of US wage bill (employment × mean wage), from BLS OEWS May 2024.

- **`api_pct`** — share of Anthropic 1P-API usage attributed to this occupation, from the AEI Feb 2026 release. O*NET tasks are split across their owning SOC codes **weighted by employment** (fixes a dilution bug where small occupations would show inflated adoption shares when they shared tasks with large ones).

- **`artifact_fit`** — qualitative 0-1 score for whether the occupation naturally produces iterable artifacts. Inherited from SOC major group with overrides for notable exceptions (e.g. Cashiers down, Pharmacists up, Producers/Directors up).


**Blend**: `eval_weight ∝ (bls_share)^0.5 × (api_share)^0.3 × artifact_fit^1.0`. Compared to the major-group version, the BLS exponent is higher (0.5 vs 0.4) and API exponent lower (0.3 vs 0.4) — at detailed granularity the AEI signal is noisier because individual tasks can dominate small occupations, so we lean more on economic weight to stabilize rankings.


**Cutoff**: top 80 occupations (~46% of total eval weight, ~44% of total US wage bill). Weights below are renormalized to sum to 100% within this selected set.


**"All Other" catchall buckets** (`, All Other` in title) are excluded — they're BLS garbage-collection categories, not real jobs.

## Top 80 occupations by eval weight

| # | SOC | Occupation | Emp | Mean wage | BLS% | API% | fit | **Weight** | Artifact examples |
|---|---|---|---|---|---|---|---|---|---|
| 1 | 13-2011 | Accountants and Auditors | 1.45M | $94K | 1.29% | 0.18% | 0.95 | **3.15%** | financial statements, audit workpapers, tax returns, reconciliations |
| 2 | 11-1021 | General and Operations Managers | 3.58M | $133K | 4.56% | 0.04% | 0.70 | **3.05%** | org plans, OKRs, exec briefings, operational reviews |
| 3 | 13-1161 | Market Research Analysts and Marketing Specialists | 861K | $86K | 0.71% | 0.46% | 0.95 | **3.03%** | market studies, segmentation reports, competitor analyses, personas |
| 4 | 43-6014 | Secretaries and Administrative Assistants, Except Legal, Medical, a… | 1.74M | $48K | 0.79% | 1.35% | 0.65 | **3.00%** | meeting notes, correspondence, travel plans, expense reports |
| 5 | 43-9061 | Office Clerks, General | 2.51M | $45K | 1.09% | 0.50% | 0.65 | **2.62%** | general correspondence, filing systems, basic reports |
| 6 | 13-1071 | Human Resources Specialists | 917K | $80K | 0.70% | 0.24% | 0.95 | **2.50%** | job descriptions, hiring plans, performance templates, HRIS configs |
| 7 | 11-3031 | Financial Managers | 819K | $180K | 1.41% | 0.19% | 0.70 | **2.43%** | financial plans, budgets, variance analyses, board reports |
| 8 | 41-3031 | Securities, Commodities, and Financial Services Sales Agents | 472K | $110K | 0.50% | 0.93% | 0.70 | **2.31%** | research reports, pitchbooks, client proposals |
| 9 | 15-1252 | Software Developers | 1.65M | $145K | 2.29% | 0.00% | 1.00 | **2.19%** | code, tests, design docs, PRs, architecture specs |
| 10 | 13-1111 | Management Analysts | 894K | $115K | 0.98% | 0.03% | 0.95 | **1.85%** | process analyses, org studies, recommendation decks |
| 11 | 23-1011 | Lawyers | 748K | $183K | 1.31% | 0.01% | 0.95 | **1.84%** | briefs, contracts, memos, motions, filings |
| 12 | 13-2052 | Personal Financial Advisors | 270K | $160K | 0.41% | 0.19% | 0.95 | **1.82%** | financial plans, portfolio reviews, client memos |
| 13 | 13-2051 | Financial and Investment Analysts | 341K | $116K | 0.38% | 0.20% | 0.95 | **1.77%** | financial models, equity research, valuation memos |
| 14 | 29-1141 | Registered Nurses | 3.28M | $98K | 3.09% | 0.17% | 0.35 | **1.73%** | care plans, patient notes, discharge summaries |
| 15 | 25-2031 | Secondary School Teachers, Except Special and Career/Technical Educ… | 1.07M | $74K | 0.76% | 0.05% | 0.90 | **1.68%** | lesson plans, assignments, rubrics, feedback |
| 16 | 43-1011 | First-Line Supervisors of Office and Administrative Support Workers | 1.50M | $72K | 1.02% | 0.09% | 0.65 | **1.61%** | operational procedures, schedules, reports, memos |
| 17 | 25-2021 | Elementary School Teachers, Except Special Education | 1.39M | $70K | 0.93% | 0.02% | 0.90 | **1.60%** | lesson plans, rubrics, student feedback, curriculum maps |
| 18 | 11-3021 | Computer and Information Systems Managers | 646K | $188K | 1.16% | 0.05% | 0.70 | **1.58%** | IT strategy, roadmaps, incident reviews, vendor evaluations |
| 19 | 43-3031 | Bookkeeping, Accounting, and Auditing Clerks | 1.46M | $52K | 0.72% | 0.13% | 0.65 | **1.49%** | journal entries, reconciliations, ledger reports |
| 20 | 11-2022 | Sales Managers | 604K | $161K | 0.93% | 0.06% | 0.70 | **1.48%** | sales plans, territory maps, compensation structures, forecasts |
| 21 | 13-1041 | Compliance Officers | 398K | $85K | 0.32% | 0.13% | 0.95 | **1.48%** | compliance memos, policy docs, audit reports, risk assessments |
| 22 | 11-1011 | Chief Executives | 212K | $263K | 0.53% | 0.17% | 0.70 | **1.47%** | strategy memos, board decks, shareholder letters |
| 23 | 13-1082 | Project Management Specialists | 1.01M | $108K | 1.04% | 0.00% | 0.95 | **1.41%** | project plans, status reports, RAID logs, stakeholder docs |
| 24 | 25-9031 | Instructional Coordinators | 211K | $78K | 0.16% | 0.41% | 0.90 | **1.36%** | curriculum standards, teacher development materials, assessments |
| 25 | 43-4051 | Customer Service Representatives | 2.73M | $45K | 1.18% | 0.62% | 0.30 | **1.34%** | case notes, ticket resolutions, FAQ entries |
| 26 | 17-2061 | Computer Hardware Engineers | 76K | $157K | 0.11% | 0.69% | 0.85 | **1.31%** | chip/system designs, validation plans, technical specs |
| 27 | 27-3031 | Public Relations Specialists | 281K | $80K | 0.22% | 0.14% | 1.00 | **1.30%** | press releases, messaging docs, media kits, crisis plans |
| 28 | 27-3041 | Editors | 95K | $86K | 0.08% | 0.61% | 1.00 | **1.27%** | edited copy, editorial guidelines, style sheets |
| 29 | 25-1071 | Health Specialties Teachers, Postsecondary | 230K | $138K | 0.30% | 0.09% | 0.90 | **1.24%** | syllabi, clinical teaching materials, case studies |
| 30 | 15-2041 | Statisticians | 30K | $112K | 0.03% | 1.26% | 1.00 | **1.14%** | statistical analyses, experiment designs, reports |
| 31 | 25-2022 | Middle School Teachers, Except Special and Career/Technical Education | 620K | $70K | 0.42% | 0.03% | 0.90 | **1.14%** | lesson plans, assessments, differentiated materials |
| 32 | 11-9111 | Medical and Health Services Managers | 566K | $138K | 0.74% | 0.02% | 0.70 | **1.12%** | quality reports, regulatory filings, clinical operations plans |
| 33 | 27-1024 | Graphic Designers | 214K | $69K | 0.14% | 0.14% | 1.00 | **1.08%** | layouts, brand guides, mockups, design specs |
| 34 | 11-2021 | Marketing Managers | 385K | $172K | 0.63% | 0.03% | 0.70 | **1.08%** | campaign briefs, positioning docs, go-to-market plans |
| 35 | 15-1211 | Computer Systems Analysts | 498K | $112K | 0.53% | 0.00% | 1.00 | **1.07%** | system designs, requirements docs, integration specs |
| 36 | 13-1081 | Logisticians | 236K | $88K | 0.20% | 0.09% | 0.95 | **1.07%** | supply chain plans, routing models, inventory analyses |
| 37 | 17-2141 | Mechanical Engineers | 287K | $110K | 0.30% | 0.06% | 0.85 | **1.07%** | mechanical designs, CAD drawings, engineering calculations |
| 38 | 13-1031 | Claims Adjusters, Examiners, and Investigators | 305K | $79K | 0.23% | 0.07% | 0.95 | **1.06%** | claim investigations, coverage analyses, settlement memos |
| 39 | 27-3043 | Writers and Authors | 48K | $86K | 0.04% | 0.73% | 1.00 | **1.04%** | articles, scripts, books, long-form content |
| 40 | 15-2031 | Operations Research Analysts | 108K | $99K | 0.10% | 0.19% | 1.00 | **1.02%** | optimization models, decision analyses, quantitative reports |
| 41 | 27-3042 | Technical Writers | 56K | $92K | 0.05% | 0.48% | 1.00 | **1.00%** | manuals, API docs, user guides, release notes |
| 42 | 43-6011 | Executive Secretaries and Executive Administrative Assistants | 473K | $77K | 0.35% | 0.11% | 0.65 | **0.99%** | executive briefings, meeting notes, correspondence |
| 43 | 43-4171 | Receptionists and Information Clerks | 965K | $38K | 0.35% | 0.10% | 0.65 | **0.99%** | call logs, appointment schedules, greeting scripts |
| 44 | 15-1232 | Computer User Support Specialists | 697K | $65K | 0.43% | 0.00% | 1.00 | **0.97%** | support runbooks, troubleshooting docs, user guides |
| 45 | 11-9032 | Education Administrators, Kindergarten through Secondary | 320K | $113K | 0.35% | 0.07% | 0.70 | **0.97%** | school improvement plans, curricula frameworks, staff reviews |
| 46 | 41-4012 | Sales Representatives, Wholesale and Manufacturing, Except Technica… | 1.27M | $81K | 0.99% | 0.15% | 0.35 | **0.96%** | proposals, sales collateral, account plans |
| 47 | 11-3071 | Transportation, Storage, and Distribution Managers | 213K | $116K | 0.24% | 0.13% | 0.70 | **0.93%** | logistics plans, routing optimizations, warehouse layouts |
| 48 | 13-1151 | Training and Development Specialists | 437K | $74K | 0.31% | 0.01% | 0.95 | **0.93%** | training curricula, learning content, assessments |
| 49 | 17-2051 | Civil Engineers | 355K | $107K | 0.36% | 0.02% | 0.85 | **0.92%** | civil designs, engineering reports, calculations |
| 50 | 13-1141 | Compensation, Benefits, and Job Analysis Specialists | 102K | $83K | 0.08% | 0.22% | 0.95 | **0.91%** | compensation studies, benefits plans, job evaluations |
| 51 | 43-3021 | Billing and Posting Clerks | 418K | $49K | 0.20% | 0.21% | 0.65 | **0.91%** | billing statements, invoices, collection letters |
| 52 | 25-9045 | Teaching Assistants, Except Postsecondary | 1.38M | $36K | 0.47% | 0.00% | 0.90 | **0.91%** | lesson support materials, accommodations, progress notes |
| 53 | 17-2112 | Industrial Engineers | 350K | $108K | 0.36% | 0.02% | 0.85 | **0.90%** | process maps, operations studies, efficiency analyses |
| 54 | 43-9111 | Statistical Assistants | 6K | $55K | 0.00% | 9.25% | 0.65 | **0.90%** | data tables, statistical outputs, formatted reports |
| 55 | 11-9121 | Natural Sciences Managers | 101K | $174K | 0.17% | 0.20% | 0.70 | **0.89%** | research proposals, grant applications, lab strategy docs |
| 56 | 41-4011 | Sales Representatives, Wholesale and Manufacturing, Technical and S… | 294K | $115K | 0.32% | 0.77% | 0.35 | **0.89%** | technical proposals, RFP responses, scope documents |
| 57 | 13-1020 | Buyers and Purchasing Agents | 487K | $82K | 0.38% | 0.00% | 0.95 | **0.87%** | RFPs, sourcing analyses, contract terms, category strategies |
| 58 | 17-2071 | Electrical Engineers | 189K | $121K | 0.22% | 0.04% | 0.85 | **0.85%** | circuit designs, schematics, technical specs |
| 59 | 25-3021 | Self-Enrichment Teachers | 309K | $53K | 0.16% | 0.07% | 0.90 | **0.84%** | lesson plans, workshop materials, handouts |
| 60 | 15-1244 | Network and Computer Systems Administrators | 319K | $101K | 0.31% | 0.00% | 1.00 | **0.83%** | configs, runbooks, capacity plans, infrastructure-as-code |
| 61 | 11-9021 | Construction Managers | 348K | $120K | 0.40% | 0.02% | 0.70 | **0.81%** | project schedules, bid packages, punch lists, change orders |
| 62 | 41-9031 | Sales Engineers | 57K | $130K | 0.07% | 0.50% | 0.70 | **0.81%** | technical proposals, demo scripts, solution designs |
| 63 | 27-2012 | Producers and Directors | 145K | $114K | 0.16% | 0.26% | 0.60 | **0.80%** | scripts, shooting schedules, show bibles, production plans |
| 64 | 19-2031 | Chemists | 83K | $96K | 0.08% | 0.18% | 0.90 | **0.80%** | research protocols, lab reports, publications |
| 65 | 11-3121 | Human Resources Managers | 216K | $160K | 0.33% | 0.03% | 0.70 | **0.80%** | HR policies, job architectures, org design docs |
| 66 | 43-5071 | Shipping, Receiving, and Inventory Clerks | 858K | $45K | 0.37% | 0.04% | 0.65 | **0.79%** | shipping logs, inventory records, receiving reports |
| 67 | 15-2051 | Data Scientists | 233K | $125K | 0.28% | 0.00% | 1.00 | **0.79%** | analyses, notebooks, model docs, dashboards |
| 68 | 23-2011 | Paralegals and Legal Assistants | 367K | $67K | 0.23% | 0.01% | 0.95 | **0.77%** | legal research memos, document drafts, discovery indexes |
| 69 | 43-6013 | Medical Secretaries and Administrative Assistants | 831K | $46K | 0.36% | 0.03% | 0.65 | **0.75%** | medical correspondence, patient records, scheduling docs |
| 70 | 25-1194 | Career/Technical Education Teachers, Postsecondary | 111K | $69K | 0.07% | 0.13% | 0.90 | **0.72%** | lesson plans, vocational curricula, skills assessments |
| 71 | 15-1241 | Computer Network Architects | 177K | $136K | 0.23% | 0.00% | 1.00 | **0.72%** | network designs, topologies, configuration standards |
| 72 | 43-4111 | Interviewers, Except Eligibility and Loan | 157K | $45K | 0.07% | 0.46% | 0.65 | **0.72%** | interview transcripts, case summaries, screening notes |
| 73 | 11-9041 | Architectural and Engineering Managers | 210K | $176K | 0.35% | 0.01% | 0.70 | **0.72%** | technical project plans, engineering specs, design reviews |
| 74 | 15-1212 | Information Security Analysts | 179K | $128K | 0.22% | 0.00% | 1.00 | **0.70%** | threat models, security policies, incident reports |
| 75 | 29-1051 | Pharmacists | 329K | $137K | 0.43% | 0.05% | 0.50 | **0.70%** | clinical reviews, drug information, patient education materials |
| 76 | 27-1014 | Special Effects Artists and Animators | 21K | $110K | 0.02% | 0.33% | 1.00 | **0.70%** | storyboards, shot lists, animation rigs, effect specs |
| 77 | 21-1012 | Educational, Guidance, and Career Counselors and Advisors | 342K | $72K | 0.23% | 0.11% | 0.55 | **0.69%** | counseling notes, academic plans, career assessments |
| 78 | 15-1253 | Software Quality Assurance Analysts and Testers | 200K | $110K | 0.21% | 0.00% | 1.00 | **0.69%** | test plans, bug reports, QA automation scripts |
| 79 | 19-3022 | Survey Researchers | 8K | $73K | 0.01% | 1.09% | 0.90 | **0.69%** | survey instruments, methodology docs, results reports |
| 80 | 17-2072 | Electronics Engineers, Except Computer | 94K | $132K | 0.12% | 0.05% | 0.85 | **0.67%** | electronic designs, test plans, datasheets |

## Summary by SOC major group

How the top-80 weight redistributes when rolled back up. Useful if you want to allocate eval tasks by archetype rather than individual occupation.

| SOC major | Archetype | # occupations in top-80 | BLS wage% (in top-80) | **Eval weight%** |
|---|---|---|---|---|
| 13-0000 | Business & Financial Ops | 13 | 7.0% | **21.9%** |
| 11-0000 | Management | 13 | 11.8% | **17.3%** |
| 43-0000 | Office & Admin Support | 12 | 6.5% | **16.1%** |
| 15-0000 | Computer & Mathematical | 10 | 4.6% | **10.1%** |
| 25-0000 | Education | 8 | 3.3% | **9.5%** |
| 27-0000 | Arts/Design/Media | 7 | 0.7% | **7.2%** |
| 17-0000 | Architecture & Engineering | 6 | 1.5% | **5.7%** |
| 41-0000 | Sales | 4 | 1.9% | **5.0%** |
| 23-0000 | Legal | 2 | 1.5% | **2.6%** |
| 29-0000 | Healthcare Practitioners | 2 | 3.5% | **2.4%** |
| 19-0000 | Life/Physical/Social Science | 2 | 0.1% | **1.5%** |
| 21-0000 | Community & Social Service | 1 | 0.2% | **0.7%** |

## Caveats & adjustment guidance

### Occupations worth reviewing

- **Statistical Assistants (43-9111)** — 6K workers but mapped to several heavily-used O*NET tasks, inflating its API share. Ranking is probably too high relative to real-world eval value.

- **Customer Service Representatives (43-4051)** and **Receptionists (43-4171)** — high employment and some artifact fit for scripts/notes, but the "artifact iteration" framing is a stretch. Consider demoting for pure artifact-refinement evals.

- **Registered Nurses (29-1141)** — large wage bill (3.09%) and we inherit Healthcare-Practitioners' 0.35 fit, but most RN work is direct care. If your eval is clinical documentation specifically, keep; if it's general artifact iteration, deweight.

- **Teachers (25-xxxx)** — cluster heavily in the top-80. If your eval has multiple teaching rows testing the same artifact types (lesson plans), consider merging into a single "K-12 teacher" or "postsecondary instructor" bucket.

### Missing important jobs (below top-80 cutoff)

A few high-value knowledge-work jobs fall below our rank-80 line because they're small or niche:

- Actuaries (15-2011), Economists (19-3011), Epidemiologists (19-1041), Urban Planners (19-3051), many postsecondary teaching specialties.

- If your eval targets any of these explicitly, pull them from the full list in `/tmp/bls/detailed_top.csv` (all 826 detailed occupations are ranked there).

### Dials

Edit `/tmp/bls/detailed_cross.py` to:

- Change the cutoff (`target_pct = 60`) to include more or fewer occupations.

- Edit `OVERRIDES` dict to adjust `artifact_fit` for specific occupations you care about.

- Change the blend exponents (`econ ** 0.5`, `adopt ** 0.3`, `fit ** 1.0`) to rebalance signals.

## Sources

- [BLS OEWS May 2024 national cross-industry data](https://www.bls.gov/oes/special-requests/oesm24nat.zip) — 826 SOC detailed occupations with employment and mean wages.

- [Anthropic Economic Index release_2026_03_24](https://huggingface.co/datasets/Anthropic/EconomicIndex/tree/main/release_2026_03_24) — Feb 5-12, 2026 usage window, O*NET task granularity.

- [O*NET task statements (AEI 2025-02-10 release)](https://huggingface.co/datasets/Anthropic/EconomicIndex/tree/main/release_2025_02_10) — maps task descriptions to SOC codes.
