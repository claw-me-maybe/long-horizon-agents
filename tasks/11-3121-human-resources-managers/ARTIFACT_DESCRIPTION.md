# Engineering Job Architecture & Leveling Framework — Aerostream Robotics

## Occupation
- **SOC:** 11-3121
- **Title:** Human Resources Managers

## Scenario
Aerostream Robotics, a Series C warehouse-automation startup with 310 employees (180 in
Engineering), is implementing its first formal job architecture for the Engineering org
in preparation for a Series D raise targeted for Q2 2027 and to resolve a growing pattern
of internal compensation inequities and title inflation. HR Business Partner Lead Priya
Rao must deliver the Engineering Job Architecture + Leveling Framework to the Chief People
Officer, Marcus Henley, and the VP of Engineering, Jin-Soo Park, by December 4, 2026, for
rollout in the January 2027 performance + compensation cycle. The architecture must land
without triggering voluntary attrition above the current 11% annualized baseline, and
must survive due-diligence scrutiny during the Series D process (investors will ask about
comp equity, leveling discipline, and org-design maturity).

## Inputs
The model starts with:

### Current Engineering org (180 FTE)
- 5 Director / Head-of titles
- 18 "Senior Manager" or "Engineering Manager" titles
- 62 "Senior Software Engineer" / "Senior Robotics Engineer" (title-creep concentration —
  this is the problem cluster)
- 44 "Software Engineer" / "Robotics Engineer"
- 21 "Staff Engineer" (mix of 4-year vets and 12-year vets — massive scope variance)
- 11 "Principal Engineer" (some reporting to VP, some reporting to Directors — inconsistent
  scope)
- 19 Engineers untitled or inconsistently titled (acquired employees from Helix Motion
  acquisition March 2026)

### Disciplines and current distribution
- Software (web, services, ML): 74 engineers
- Robotics (motion planning, perception, controls): 42 engineers
- Firmware/Embedded: 21 engineers
- Hardware (EE, ME): 18 engineers
- Systems/Reliability (SRE, platform): 15 engineers
- Technical Program Management (TPM): 10 engineers

### Compensation data (current state)
- Pay bands do not exist formally; comp is set by hiring managers with loose guidance
- **23% of "Senior Engineers" have base <$145K; 18% >$210K** — a 45% spread at the same title
- Helix Motion acquisition employees averaged **17% below Aerostream-native peers at
  equivalent scope** (acquisition comp wasn't normalized at close)
- 6 internal comp-equity complaints filed in Q3 2026 (up from 0 in Q3 2025)
- Gender pay analysis (People Analytics, Q3 2026):
  - Women engineers at "Senior" title: 7.4% median base below men at same title
  - Black/Hispanic engineers: sample sizes small but trending below median

### Performance calibration issues
- Director ratings distribution: 52% "Exceeds" or "Greatly Exceeds" vs. target 25-30%
- No clear promotion-to-Staff criteria; 3 of 21 Staff Engineers were promoted without a
  panel review
- Skip-level compensation decisions inconsistent across Directors

### Benchmark data
- Radford Global Technology Survey, Q3 2026 — targeting 75th percentile for critical
  engineering roles, board-approved
- Radford data available for all 6 disciplines including Hardware and TPM (important for
  discipline-specific banding)

### Budget
- $1.8M comp-adjustment budget for 2027 to close gaps identified by new architecture
- Roughly 1.2% of total engineering comp spend
- Insufficient to close all equity gaps at once; must prioritize

### Political constraints
- VP Engineering Jin-Soo Park has stated: "no one gets demoted in title" but is open to
  leveling at the same title with documented expectations. This is a non-negotiable line.
- CEO Elena Torres wants the framework to support planned scale from 180 to 275 engineers
  by end of 2028.
- Helix Motion leadership (acquired leadership now reporting into Aerostream) has pushed
  back on "assimilation" framing; any crosswalk must be respectful and acknowledge their
  prior company's leveling conventions.
- Board wants the framework to be Series D-ready: defensible, documented, and with a
  comp-equity analysis.

### Prior attempt
A draft framework was circulated internally in Q2 2026 and rejected by Eng leadership as
"too rigid" and "not tailored to robotics." That version was purely copied from a Software-
only framework. The current attempt must treat robotics, hardware, firmware, and TPM as
first-class families.

## Artifact specification
A Job Architecture + Leveling deliverable with the following components:

1. **Framework philosophy** — 1 page. Principles (e.g., dual-track IC/Mgmt; observable
   criteria; calibration is mandatory; comp bands follow levels not titles; title-creep
   is deliberately contained). State what this framework will and will not do.
2. **Level scaffold** — unified level ladder covering both IC and Manager tracks with
   numeric levels (L3 through L9 or similar: L3 Entry, L4 Engineer, L5 Senior, L6 Staff,
   L7 Senior Staff, L8 Principal, L9 Distinguished; Manager track M5 EM, M6 Sr EM, M7
   Director, M8 Sr Director, M9 VP). For each level: role archetype, scope of impact,
   autonomy, influence, technical complexity, years-of-experience proxy (with explicit
   caveat that YoE is not the criterion).
3. **Discipline-specific job families** — for each of 6 disciplines: level-by-level job
   descriptions (1-paragraph archetype + 4-6 proficiency indicators). Must handle TPM
   and Hardware as first-class families, not footnotes.
4. **Leveling rubric / matrix** — observable proficiency indicators on dimensions
   (technical depth, scope, autonomy, leadership, cross-functional influence, mentoring,
   delivery). Used by calibration committees.
5. **Promotion criteria & process** — what's required to advance each level, the panel
   structure (peer + skip-level + external-to-org reviewer), cadence (annual plus mid-year
   Staff+ promotion windows), and the evidence packet expected (examples of scoped work,
   performance data, peer feedback).
6. **Title + comp band mapping** — current titles → new level ladder crosswalk (the
   politically sensitive step). Include comp band table: Level / 25th / 50th / 75th / Max.
   Tied to Radford Q3 2026 benchmark, with geo differentials (SF, NYC, Remote-US).
7. **Helix Motion crosswalk** — specific handling of 19 acquired employees: level-assignment
   methodology (role scope-based, not company-of-origin), comp-equity remediation plan
   (approximate $ per employee, funded from the $1.8M), communication approach (1:1
   before announcement, not a mass email).
8. **Implementation plan** — timeline from Dec 2026 communication (CPO → Directors →
   Managers → Individuals) through Jan 2027 manager training through Feb 2027 employee
   conversations through March 2027 comp adjustments. Change-management touchpoints and
   communication cadence.
9. **Equity impact analysis** — projected changes by demographic group (gender,
   race/ethnicity, Helix vs. native, tenure) to detect and mitigate disparate impact
   before rollout. Must be run by People Analytics in collaboration with Legal (Deborah
   Marin, General Counsel).
10. **Risk register & communication plan** — top 6-8 risks (attrition, title grief, legal
    exposure from equity remediation, VP Eng political capital, Series D timing) with
    mitigation and pre-drafted key messages for common concerns.

Tone: HR-professional but unafraid of the political specifics. Both legally defensible and
operationally actionable. Acknowledges human impact while holding to framework principles.

## Output format
Markdown document with embedded tables, 10-14 pages. Centerpiece tables: level scaffold,
leveling rubric, title crosswalk, comp bands. Must be usable by a calibration committee
without requiring a separate operator manual.

## Iteration targets
1. **Make the level scaffold specific** — v1 often writes generic "Senior Engineer: owns
   a feature." Iterate to observable indicators: "At L5 Senior Engineer, typically owns
   delivery of a 3-6 month feature area, operates autonomously within a team, provides
   technical review on peer PRs, begins to influence cross-team design, expected to
   mentor 1-2 L3/L4 engineers. Does NOT yet drive architectural decisions across the
   team/org (that's L6)."
2. **Fix the Helix Motion crosswalk tone and substance** — v1 risks sounding like
   "assimilation." Iterate to a methodology that assesses role-scope rather than
   company-of-origin, proposes a comp-equity look-back with named budget ($260K allocated
   from the $1.8M, ~$13.7K average adjustment), and offers a 1:1 communication protocol
   (Director → Individual, pre-announcement) that acknowledges Helix's prior conventions
   and explicitly validates their contributions.
3. **Strengthen the leveling rubric with differentiation between adjacent levels** — v1
   often blurs L5 and L6. Iterate to behavior indicators where the difference is
   operationally clear (e.g., L5 "reviews design docs produced by own team"; L6 "authors
   design docs that cross 2+ teams and are reviewed by Staff+ engineers"; L7 "authors
   design docs at the org level, shapes multi-quarter technical direction").
4. **Tighten the Staff/Principal distinction** — the current org has role ambiguity here.
   v1 may paper over it. Iterate to crisp separation: Staff (L6) = technical leader
   within a domain / org of ~30 engineers; Senior Staff (L7) = technical leader across
   2-3 teams or ~60 engineers; Principal (L8) = technical leader across the Engineering
   org, directly shapes multi-year technical direction; Distinguished (L9) = company-wide
   technical authority, reserved (likely 0-2 in current org size).
5. **Make the equity impact analysis real** — v1 may handwave. Iterate to a named
   methodology (e.g., OFCCP-style adverse-impact analysis at each level-transition
   boundary, plus pre-read with Legal before comp adjustment letters ship, and a run by
   People Analytics with two sensitivity analyses: with and without Helix cohort).
6. **Convert political constraints into framework language** — v1 may ignore the VP's
   "no demotions" edict. Iterate to a principled statement: "Level calibration at first
   rollout holds current title for all employees; expectations are re-stated against the
   new framework; promotion/demotion decisions follow the standard promotion process
   beginning Q2 2027. No employee's comp is reduced as part of initial calibration." This
   satisfies both the political need and framework integrity.
7. **Address the Series D due-diligence use case** — v1 may not. Iterate to include a
   one-paragraph statement of how the framework materials will be provided to DD
   including comp-equity analysis, calibration process evidence, and leveling-by-discipline
   documentation.

## Success criteria
(For evaluator use only.)
1. Level scaffold covers at least 6 levels (IC L3-L8+) and 4 levels (Manager M5-M8+) with
   distinct, observable criteria per level.
2. Title crosswalk maps current titles to new levels with a principle that respects VP
   Eng's "no demotions" edict (e.g., all current titles hold; expectations are realigned
   with formal re-calibration timing for future promotions).
3. Comp band table ties to named benchmark (Radford 75th percentile) with bands for each
   level that expand reasonably at higher levels (e.g., L3 band ~$30K spread; L8 band
   ~$120K spread).
4. Helix Motion crosswalk includes a specific comp-equity remediation budget number
   (sub-amount of the $1.8M) and a communication methodology.
5. Promotion process names panel composition (at minimum: manager, skip-level, external-
   to-org reviewer), cadence, and evidence-packet requirements.
6. Equity impact analysis methodology is named (not "we'll review for equity") with a
   specific reviewer (People Analytics + Legal) and a pre-launch gate (e.g., "Comp
   adjustment letters do not ship until equity analysis is signed off by CPO + Legal").
7. At least two disciplines beyond Software (e.g., Hardware, TPM) are treated with equal
   rubric depth — not copied from Software with minor edits. This addresses the Q2 2026
   failed-draft critique.

## Scope target
A v1 at ~15 minutes should contain: framework principles; level scaffold with 5-7 levels
and archetype descriptions; one fully fleshed-out discipline family (Software) with
L3-L8 criteria; a draft leveling rubric with 4-6 dimensions; title crosswalk at the
summary level; comp band table tied to benchmark percentile; and a rollout timeline
skeleton. Full Hardware/TPM/Firmware discipline detail, Helix Motion crosswalk specifics,
and equity-impact analysis methodology are iteration targets for v2/v3. By v3, the
Hardware and TPM families should have comparable depth to Software, and the equity
analysis should include specific demographic cuts and a gated launch process.
