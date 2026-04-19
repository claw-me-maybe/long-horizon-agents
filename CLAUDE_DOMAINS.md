# Claude Domains — weighted list for artifact-iteration evals

A weighted list of occupational domains suitable for evaluating **model ability to iterate on domain-specific artifacts**. Built by cross-referencing US Bureau of Labor Statistics wage data with the Anthropic Economic Index (AEI).

## Purpose

When building an eval of iterative artifact refinement (code, docs, analyses, designs, etc.), domain weights should reflect:

1. **Economic importance** — where knowledge work actually happens
2. **AI adoption signal** — which domains people already use AI for, professionally
3. **Artifact fit** — whether the domain naturally produces iterable artifacts at all (excludes e.g. direct patient care, truck driving, food prep)

This doc blends all three signals into a single recommended weighting.

## Data sources

| Source | What it gives | Date |
|---|---|---|
| [BLS OEWS National](https://www.bls.gov/oes/current/oes_nat.htm) | Employment × mean wage per SOC occupation | May 2024 (released 2025) |
| [Anthropic Economic Index](https://huggingface.co/datasets/Anthropic/EconomicIndex) `release_2026_03_24` | Usage share per O*NET task, Claude.ai + 1P API | Feb 5–12, 2026 window |
| [O*NET task statements](https://huggingface.co/datasets/Anthropic/EconomicIndex/tree/main/release_2025_02_10) | Task description → SOC code | O*NET 28.0 |

Cross-check vs. [AEI Jan 2026 report](https://www.anthropic.com/research/anthropic-economic-index-january-2026-report): this aggregation reports Claude.ai top-4 as 32/13/10/9%, blog reports 34/15/11/8%. Small differences from raw-task aggregation vs. report-level rounding.

## Methodology

### Signals

- **`bls_share_pct`** — each SOC major group's share of the US total wage bill (`employment × mean annual wage`). Labor compensation is ~60% of GDP, so this is a proxy for "economic weight," not a direct GDP split. OEWS excludes self-employed, most farm workers, and military.
- **`cai_pct`** — share of Claude.ai (consumer) conversations mapped to each SOC major group.
- **`api_pct`** — share of first-party API traffic mapped to each SOC major group. This is the closest proxy for "professional iterative artifact work," since API usage skews toward built products and enterprise workflows.
- **`artifact_fit`** — qualitative 0-1 score for how well the domain produces iterable artifacts. Judgment call, not data-driven. **Adjust these for your eval.**

### Blend

```
eval_weight ∝ (bls_share + 0.1)^0.4  ×  (api_share + 0.1)^0.4  ×  artifact_fit^1.0
```

Geometric blend so no single signal dominates. The +0.1 prevents zeros from collapsing the product. `artifact_fit` has exponent 1.0 because it's the strictest filter — a domain with zero artifact fit gets zero weight regardless of economic size.

### Pipeline

1. Download BLS OEWS national cross-industry file. Compute wage bill per SOC code.
2. Download AEI raw Claude.ai + API CSVs. Filter to `facet=onet_task`, `variable=onet_task_pct`, `geography=global`.
3. Join each O*NET task description to its SOC code via `onet_task_statements.csv`; take first 2 digits of SOC code as the major group.
4. Sum `onet_task_pct` per SOC major group per surface. Renormalize to 100% among matched tasks (~93% Claude.ai, ~90% API match).
5. Merge BLS + AEI on SOC major group. Apply blend formula.

## Full cross-reference

Ranked by final eval weight. `API/BLS` > 1 means AI is over-adopted in that domain relative to its economic size.

| # | Domain | BLS wage% | Claude.ai% | API% | API/BLS | artifact fit | EVAL% | cum |
|---|---|---|---|---|---|---|---|---|
| 1 | Computer and Mathematical | 5.8 | 32.2 | 51.6 | 8.91× | 1.00 | 27.9 | 27.9 |
| 2 | Office and Administrative Support | 8.7 | 9.4 | 17.6 | 2.01× | 0.65 | 13.9 | 41.7 |
| 3 | Business and Financial Operations | 9.3 | 4.8 | 3.5 | 0.38× | 0.95 | 11.0 | 52.7 |
| 4 | Management | 14.8 | 4.3 | 3.4 | 0.23× | 0.70 | 9.7 | 62.4 |
| 5 | Educational Instruction and Library | 5.6 | 13.5 | 3.1 | 0.55× | 0.90 | 8.1 | 70.5 |
| 6 | Arts, Design, Entertainment, Sports, Media | 1.5 | 10.4 | 5.2 | 3.39× | 1.00 | 6.7 | 77.3 |
| 7 | Life, Physical, and Social Science | 1.2 | 6.3 | 4.4 | 3.56× | 0.90 | 5.2 | 82.5 |
| 8 | Architecture and Engineering | 2.5 | 2.1 | 1.8 | 0.72× | 0.85 | 4.6 | 87.1 |
| 9 | Sales and Related | 6.9 | 4.9 | 4.1 | 0.60× | 0.35 | 3.8 | 91.0 |
| 10 | Healthcare Practitioners and Technical | 9.6 | 3.0 | 1.0 | 0.10× | 0.35 | 2.6 | 93.5 |
| 11 | Legal | 1.7 | 0.6 | 0.2 | 0.11× | 0.95 | 2.0 | 95.5 |
| 12 | Community and Social Service | 1.5 | 3.2 | 0.5 | 0.32× | 0.55 | 1.5 | 97.1 |
| 13 | Protective Service | 2.1 | 0.4 | 0.5 | 0.25× | 0.20 | 0.7 | 97.7 |
| 14 | Production | 4.2 | 0.7 | 1.2 | 0.29× | 0.10 | 0.6 | 98.3 |
| 15 | Installation, Maintenance, and Repair | 3.6 | 0.7 | 0.4 | 0.11× | 0.10 | 0.4 | 98.7 |
| 16 | Construction and Extraction | 3.9 | 0.2 | 0.3 | 0.08× | 0.10 | 0.3 | 99.0 |
| 17 | Healthcare Support | 2.8 | 0.3 | 0.2 | 0.05× | 0.10 | 0.3 | 99.3 |
| 18 | Personal Care and Service | 1.2 | 1.2 | 0.4 | 0.31× | 0.10 | 0.2 | 99.5 |
| 19 | Transportation and Material Moving | 6.4 | 0.2 | 0.2 | 0.03× | 0.05 | 0.2 | 99.7 |
| 20 | Food Preparation and Serving Related | 4.7 | 0.7 | 0.1 | 0.02× | 0.05 | 0.1 | 99.8 |
| 21 | Building and Grounds Cleaning and Maintenance | 1.7 | 0.2 | 0.1 | 0.06× | 0.05 | 0.1 | 99.9 |
| 22 | Farming, Fishing, and Forestry | 0.2 | 0.5 | 0.1 | 0.69× | 0.10 | 0.1 | 100.0 |

## Recommended eval weighting — top 9 domains covering 91%

Renormalized so the selected domains sum to 100%.

| Domain | Artifact examples | Weight |
|---|---|---|
| Computer and Mathematical | code, tests, configs, schemas, runbooks | **30.6%** |
| Office and Administrative Support | emails, forms, spreadsheets, calendars, SOPs | **15.2%** |
| Business and Financial Operations | financial models, market analyses, BRDs, board docs | **12.1%** |
| Management | strategy docs, OKRs, plans, decks | **10.6%** |
| Educational Instruction and Library | lesson plans, curricula, student feedback, syllabi | **9.0%** |
| Arts, Design, Entertainment, Media | prose, scripts, copy, storyboards, designs | **7.4%** |
| Life, Physical, and Social Science | research drafts, protocols, literature reviews | **5.7%** |
| Architecture and Engineering | specs, drawings, calculations, technical docs | **5.1%** |
| Sales and Related | proposals, sequences, pitch decks | **4.2%** |

## Caveats & knobs to adjust

### Sub-splits worth considering

- **Healthcare Practitioners (9.6% BLS)** — clinical practice isn't artifact iteration, but clinical *documentation*, *coding*, and *literature review* absolutely are. Consider splitting 29-xxxx into care vs. documentation sub-buckets if clinical writing is in-scope.
- **Legal (1.7% BLS, 0.2% API)** — massively under-adopted despite being artifact-heavy. If your eval targets aspirational professional knowledge work, up-weight legal manually; current API share reflects adoption lag, not fit.
- **Management vs. Office/Admin** — overlap in practice. A manager drafting a memo is doing "management" work but producing an "office/admin" artifact. Decide whether your taxonomy is by *role* or by *artifact type*.

### Signal weights

The blend exponents (0.4, 0.4, 1.0) are tunable:

- **Increase API exponent** to chase current enterprise adoption patterns.
- **Increase BLS exponent** to chase long-run economic reality (less AI-hype-biased).
- **Increase artifact_fit exponent** to be stricter about excluding manual/relational work.
- **Swap API for Claude.ai share** if your eval targets consumer/personal use cases (this pushes Education and Arts up significantly).

### AEI matching

~7% of Claude.ai usage and ~10% of API usage didn't map to a SOC major group (tasks not found in O*NET, or "Other" clusters). Results are normalized among matched tasks; if the unmatched portion is systematically biased toward one domain this could skew shares slightly.

### Freshness

AEI usage patterns shift quarter-over-quarter. Computer/Math API share grew from 44% → 46% → 51.6% over Aug 2025 → Nov 2025 → Feb 2026 windows. Expect these weights to drift; re-run annually.

## Files produced during analysis

- `/tmp/bls/cross_ref.csv` — full joined table
- `/tmp/bls/aei/cai_by_major.csv`, `/tmp/bls/aei/api_by_major.csv` — AEI aggregated to SOC major groups
- `/tmp/bls/major_sorted.csv`, `/tmp/bls/detailed_sorted.csv` — BLS wage bill by SOC major / detailed
- `/tmp/bls/cross_ref.py`, `/tmp/bls/aei_map.py`, `/tmp/bls/analyze.py` — computation scripts
