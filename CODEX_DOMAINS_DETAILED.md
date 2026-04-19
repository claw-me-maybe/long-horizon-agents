# Codex Domains Detailed

A market-weighted, occupation-level synthesis of [`CLAUDE_DOMAINS.md`](./CLAUDE_DOMAINS.md) and [`CODEX_DOMAINS.md`](./CODEX_DOMAINS.md).

## Purpose

`CLAUDE_DOMAINS.md` is good at telling you which broad domains matter for artifact-iteration evals. `CODEX_DOMAINS.md` is good at naming concrete jobs. This document combines them so you can answer both questions at once:

1. Which parts of the economy should matter most in an eval?
2. Within those parts, which specific occupations are concrete enough to benchmark?

The result is a hierarchical weighting:

- `CLAUDE_DOMAINS.md` supplies the parent-domain weights.
- BLS detailed occupations supply the concrete job leaves.
- A role-level fit score filters for jobs that actually produce iterable artifacts.

## Key Decision

Use a `hierarchical` model, not a direct AEI-to-detailed-occupation mapping.

I tested direct detailed mapping from Anthropic Economic Index tasks to detailed SOC occupations. It is too noisy for a stable occupation-level weighting:

- Many O*NET tasks map to multiple detailed occupations, so equal-splitting causes spillover.
- Some O*NET detailed codes do not align cleanly with current BLS detailed codes.
- In practice, this surfaces unstable or misleading leaves, including outdated code buckets and odd task spillovers.

Domain-level AEI is still useful and robust. Detailed occupation splits are much more defensible when they are derived from BLS wage-bill shares inside those parent domains.

## Method

### Step 1: Keep Claude's parent-domain weights

For the artifact-heavy portion of the economy, keep the parent-domain eval weights from `CLAUDE_DOMAINS.md`.

### Step 2: Split each domain into detailed occupations

Within each parent domain, use BLS detailed occupation wage-bill share as the economic signal.

### Step 3: Apply an occupation-level fit score

Each detailed occupation gets a manual `occupation_fit` score that combines:

- Artifact intensity: how much of the job is iterative work on docs, code, analyses, plans, designs, or similar artifacts
- Specificity: penalty for vague or catch-all titles

This is why titles like `Managers, All Other` and other `All Other` buckets are excluded.

### Step 4: Temper concentration within each domain

If you use raw within-domain wage share directly, the largest occupation in a domain can dominate too hard. To preserve variety while keeping market grounding, use a softened split:

```text
within_domain_share = occupation_bls_share / parent_domain_bls_share

leaf_raw = within_domain_share^0.7 * occupation_fit

leaf_mix_within_domain = normalize(leaf_raw within parent domain)

global_leaf_weight = parent_domain_weight * leaf_mix_within_domain
```

The `0.7` exponent is deliberate. It still rewards large occupations, but it does not let one occupation eat an entire domain.

## What The Weights Mean

- `Parent domain weight` is the Claude-style market-and-adoption weight.
- `Within-domain mix` is how to split that parent domain into specific occupations.
- `Global weight` is the final recommended leaf weight for eval sampling.

These are `eval weights`, not literal shares of total U.S. employment.

## Parent Domains Used

These detailed domains cover `92.9%` of the parent-domain eval weight from `CLAUDE_DOMAINS.md`.

| Domain | Parent Weight |
| --- | ---: |
| Computer and Mathematical | 27.9% |
| Office and Administrative Support | 13.9% |
| Business and Financial Operations | 11.0% |
| Management | 9.7% |
| Educational Instruction and Library | 8.1% |
| Arts, Design, Entertainment, Sports, and Media | 6.7% |
| Life, Physical, and Social Science | 5.2% |
| Architecture and Engineering | 4.6% |
| Sales and Related | 3.8% |
| Legal | 2.0% |

## Global Top Occupation Leaves

These are the strongest detailed leaves under the hybrid model.

| Occupation | Parent Domain | Global Weight | Artifact Examples |
| --- | --- | ---: | --- |
| Software Developers | Computer and Mathematical | 13.23% | code, tests, repos, specs |
| Computer Systems Analysts | Computer and Mathematical | 4.53% | requirements, process maps, systems docs |
| First-Line Supervisors of Office and Administrative Support Workers | Office and Administrative Support | 3.36% | SOPs, reports, staffing plans |
| Data Scientists | Computer and Mathematical | 3.03% | notebooks, models, analyses, dashboards |
| Bookkeeping, Accounting, and Auditing Clerks | Office and Administrative Support | 2.84% | spreadsheets, reconciliations, records |
| Elementary School Teachers, Except Special Education | Educational Instruction and Library | 2.77% | lesson plans, assignments, parent comms |
| Customer Service Representatives | Office and Administrative Support | 2.58% | case notes, response drafts, ticket workflows |
| Information Security Analysts | Computer and Mathematical | 2.43% | policies, detections, incident writeups |
| Secondary School Teachers, Except Special and Career/Technical Education | Educational Instruction and Library | 2.40% | lesson plans, rubrics, feedback |
| Software Quality Assurance Analysts and Testers | Computer and Mathematical | 2.37% | test plans, cases, bug reports |
| Network and Computer Systems Administrators | Computer and Mathematical | 2.28% | runbooks, configs, change docs |
| Accountants and Auditors | Business and Financial Operations | 2.27% | workpapers, reconciliations, memos |
| Executive Secretaries and Executive Administrative Assistants | Office and Administrative Support | 2.07% | emails, meeting briefs, calendars, summaries |
| Financial Managers | Management | 1.94% | budgets, board packs, financial plans |
| Management Analysts | Business and Financial Operations | 1.87% | analyses, recommendations, process docs |
| Project Management Specialists | Business and Financial Operations | 1.85% | project plans, status reports, RAID logs |
| Medical Scientists, Except Epidemiologists | Life, Physical, and Social Science | 1.75% | protocols, study drafts, literature reviews |
| Medical Secretaries and Administrative Assistants | Office and Administrative Support | 1.75% | forms, scheduling, referral paperwork |
| Computer and Information Systems Managers | Management | 1.69% | roadmaps, architecture reviews, operating plans |
| Public Relations Specialists | Arts, Design, Entertainment, Sports, and Media | 1.64% | press releases, talking points, comms plans |

## Detailed Occupation Menus

These tables are the main payload of the document. In practice, an eval builder should sample a parent domain first, then sample an occupation from the within-domain mix.

## Computer and Mathematical (27.9%)

| Occupation | Within-Domain Mix | Global Weight | Artifact Examples |
| --- | ---: | ---: | --- |
| Software Developers | 47.5% | 13.23% | code, tests, repos, specs |
| Computer Systems Analysts | 16.3% | 4.53% | requirements, process maps, systems docs |
| Data Scientists | 10.9% | 3.03% | notebooks, models, analyses, dashboards |
| Information Security Analysts | 8.7% | 2.43% | policies, detections, incident writeups |
| Software Quality Assurance Analysts and Testers | 8.5% | 2.37% | test plans, cases, bug reports |
| Network and Computer Systems Administrators | 8.2% | 2.28% | runbooks, configs, change docs |

## Office and Administrative Support (13.9%)

| Occupation | Within-Domain Mix | Global Weight | Artifact Examples |
| --- | ---: | ---: | --- |
| First-Line Supervisors of Office and Administrative Support Workers | 24.3% | 3.36% | SOPs, reports, staffing plans |
| Bookkeeping, Accounting, and Auditing Clerks | 20.5% | 2.84% | spreadsheets, reconciliations, records |
| Customer Service Representatives | 18.6% | 2.58% | case notes, response drafts, ticket workflows |
| Executive Secretaries and Executive Administrative Assistants | 14.9% | 2.07% | emails, meeting briefs, calendars, summaries |
| Medical Secretaries and Administrative Assistants | 12.6% | 1.75% | forms, scheduling, referral paperwork |
| Production, Planning, and Expediting Clerks | 9.0% | 1.24% | schedules, trackers, inventory docs |

## Business and Financial Operations (11.0%)

| Occupation | Within-Domain Mix | Global Weight | Artifact Examples |
| --- | ---: | ---: | --- |
| Accountants and Auditors | 20.7% | 2.27% | workpapers, reconciliations, memos |
| Management Analysts | 17.0% | 1.87% | analyses, recommendations, process docs |
| Project Management Specialists | 16.8% | 1.85% | project plans, status reports, RAID logs |
| Market Research Analysts and Marketing Specialists | 12.9% | 1.42% | research decks, campaign briefs, analyses |
| Human Resources Specialists | 10.6% | 1.17% | job descriptions, interview packets, policy drafts |
| Financial and Investment Analysts | 8.7% | 0.96% | models, investment memos, forecasts |
| Compliance Officers | 7.0% | 0.77% | controls docs, audit responses, checklists |
| Training and Development Specialists | 6.4% | 0.70% | training plans, curricula, job aids |

## Management (9.7%)

| Occupation | Within-Domain Mix | Global Weight | Artifact Examples |
| --- | ---: | ---: | --- |
| Financial Managers | 20.0% | 1.94% | budgets, board packs, financial plans |
| Computer and Information Systems Managers | 17.5% | 1.69% | roadmaps, architecture reviews, operating plans |
| Medical and Health Services Managers | 12.0% | 1.16% | operations plans, compliance docs, staffing plans |
| Marketing Managers | 11.4% | 1.10% | campaign plans, briefs, reporting decks |
| Sales Managers | 11.2% | 1.08% | forecasts, territory plans, sales reviews |
| Architectural and Engineering Managers | 7.6% | 0.74% | portfolio plans, design reviews, technical strategy |
| Education Administrators, Kindergarten through Secondary | 7.0% | 0.68% | school plans, communications, policy docs |
| Human Resources Managers | 6.8% | 0.66% | org plans, policies, workforce planning docs |
| Administrative Services Managers | 6.4% | 0.62% | policies, facilities plans, operating procedures |

## Educational Instruction and Library (8.1%)

| Occupation | Within-Domain Mix | Global Weight | Artifact Examples |
| --- | ---: | ---: | --- |
| Elementary School Teachers, Except Special Education | 34.0% | 2.77% | lesson plans, assignments, parent comms |
| Secondary School Teachers, Except Special and Career/Technical Education | 29.4% | 2.40% | lesson plans, rubrics, feedback |
| Health Specialties Teachers, Postsecondary | 16.6% | 1.35% | syllabi, lectures, course materials |
| Instructional Coordinators | 12.6% | 1.02% | curricula, lesson plans, assessment materials |
| Special Education Teachers, Secondary School | 7.4% | 0.60% | IEP drafts, progress reports, lesson plans |

## Arts, Design, Entertainment, Sports, and Media (6.7%)

| Occupation | Within-Domain Mix | Global Weight | Artifact Examples |
| --- | ---: | ---: | --- |
| Public Relations Specialists | 24.4% | 1.64% | press releases, talking points, comms plans |
| Graphic Designers | 19.1% | 1.29% | design comps, asset systems, briefs |
| Producers and Directors | 16.4% | 1.11% | shot lists, scripts, production plans |
| Editors | 12.7% | 0.85% | edits, copy passes, style guides |
| Technical Writers | 9.6% | 0.65% | docs, tutorials, release notes |
| Art Directors | 9.6% | 0.65% | creative direction, comps, brand systems |
| Writers and Authors | 8.2% | 0.55% | drafts, scripts, long-form content |

## Life, Physical, and Social Science (5.2%)

| Occupation | Within-Domain Mix | Global Weight | Artifact Examples |
| --- | ---: | ---: | --- |
| Medical Scientists, Except Epidemiologists | 33.5% | 1.75% | protocols, study drafts, literature reviews |
| Occupational Health and Safety Specialists | 22.0% | 1.15% | incident reports, compliance plans, checklists |
| Chemists | 17.1% | 0.90% | lab reports, methods, technical analyses |
| Environmental Scientists and Specialists, Including Health | 16.4% | 0.86% | assessments, reports, permit docs |
| Urban and Regional Planners | 10.9% | 0.57% | plans, public memos, zoning analyses |

## Architecture and Engineering (4.6%)

| Occupation | Within-Domain Mix | Global Weight | Artifact Examples |
| --- | ---: | ---: | --- |
| Civil Engineers | 23.0% | 1.06% | specs, calculations, design docs |
| Industrial Engineers | 22.9% | 1.06% | process maps, optimization analyses, SOPs |
| Mechanical Engineers | 19.0% | 0.88% | drawings, analyses, test reports |
| Electrical Engineers | 15.1% | 0.70% | design docs, schematics, calculations |
| Architects, Except Landscape and Naval | 10.5% | 0.49% | plans, drawings, design packages |
| Computer Hardware Engineers | 9.6% | 0.44% | hardware specs, test reports, designs |

## Sales and Related (3.8%)

| Occupation | Within-Domain Mix | Global Weight | Artifact Examples |
| --- | ---: | ---: | --- |
| Sales Representatives of Services | 32.3% | 1.24% | proposals, account notes, outreach sequences |
| Financial Services Sales Agents | 24.8% | 0.95% | pitch books, account notes, recommendations |
| Technical Sales Representatives | 18.2% | 0.70% | RFP responses, solution briefs, account plans |
| Insurance Sales Agents | 16.9% | 0.65% | coverage comparisons, outreach, proposals |
| Sales Engineers | 7.8% | 0.30% | technical proposals, solution docs, demos |

## Legal (2.0%)

| Occupation | Within-Domain Mix | Global Weight | Artifact Examples |
| --- | ---: | ---: | --- |
| Lawyers | 75.2% | 1.53% | briefs, contracts, memos |
| Paralegals and Legal Assistants | 22.5% | 0.46% | drafts, cite-checks, discovery docs |
| Judicial Law Clerks | 2.3% | 0.05% | bench memos, research, draft opinions |

## Broader Job-Automation Appendix

The core model above is still anchored to `CLAUDE_DOMAINS.md`, so it prioritizes artifact-heavy work. That means some occupations that matter a lot in `CODEX_DOMAINS.md` still show up as underweighted or omitted here.

If the goal is `broader job automation`, not just `artifact iteration`, I would add separate tracks for the following:

### Healthcare Practitioners And Technical

This domain is only `2.6%` in `CLAUDE_DOMAINS.md`, but it is `9.6%` of BLS wage bill. That gap reflects direct-care work being hard to model as artifact iteration, not lack of economic importance.

Recommended detailed occupations for a broader healthcare track:

- `Registered Nurses`
- `Nurse Practitioners`
- `Physician Assistants`
- `Speech-Language Pathologists`
- `Medical Records Specialists`
- `Dental Hygienists`

For healthcare, the right split is usually:

- `documentation / coding / chart-review` tasks
- `direct patient care` tasks

Those should not be benchmarked the same way.

### Field-Work Domains That Matter In `CODEX_DOMAINS.md`

These rank low in the artifact model but are still important if the eval target is end-to-end job automation:

- `Electricians`
- `HVAC technicians`
- `Wind turbine service technicians`
- `Solar photovoltaic installers`
- `Logisticians`

These jobs are better treated as separate benchmark tracks with planning, estimation, scheduling, troubleshooting, and compliance subtasks, not pure document-iteration tasks.

## Recommended Usage

For an eval suite, the cleanest procedure is:

1. Sample a parent domain using the parent weights in this document.
2. Sample a specific occupation using the within-domain mix for that domain.
3. Build artifact families around the example artifacts listed for that occupation.
4. If your benchmark expands beyond artifact work, add dedicated healthcare and field-work tracks instead of forcing them into the same weighting.

## Sources

- `CLAUDE_DOMAINS.md`
- `CODEX_DOMAINS.md`
- BLS OEWS National cross-industry wage data, May 2024 release
- Anthropic Economic Index `release_2026_03_24`
- `/tmp/bls/cross_ref.csv`
- `/tmp/bls/detailed_sorted.csv`
