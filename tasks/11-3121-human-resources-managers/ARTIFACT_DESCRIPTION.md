# Engineering Job Architecture & Leveling Framework — Aerostream Robotics

## Occupation
- **SOC:** 11-3121
- **Title:** Human Resources Managers

## Scenario
Aerostream Robotics, a Series C warehouse-automation startup with 310 employees (180 in Engineering), is implementing its first formal job architecture for the Engineering org in preparation for a Series D raise targeted for Q2 2027 and to resolve a growing pattern of internal compensation inequities and title inflation. HR Business Partner Lead Priya Rao must deliver the Engineering Job Architecture + Leveling Framework to the Chief People Officer, Marcus Henley, and the VP of Engineering, Jin-Soo Park, by December 4, 2026, for rollout in the January 2027 performance + compensation cycle. The architecture must land without triggering voluntary attrition above the current 11% annualized.

## Inputs
The model starts with:

- **Current Engineering org (180 FTE):**
  - 5 Director / Head-of titles
  - 18 "Senior Manager" or "Engineering Manager" titles
  - 62 "Senior Software Engineer" / "Senior Robotics Engineer" (title-creep concentration)
  - 44 "Software Engineer" / "Robotics Engineer"
  - 21 "Staff Engineer" (mix of 4-year vets and 12-year vets)
  - 11 "Principal Engineer" (some reporting to VP; some reporting to Directors)
  - 19 Engineers untitled/inconsistent (acquired employees from Helix Motion acquisition March 2026)
- **Disciplines:** Software (web, services, ML), Robotics (motion planning, perception, controls), Firmware/Embedded, Hardware (EE, ME), Systems/Reliability, Technical Program Management.
- **Compensation data (current state):**
  - Pay bands do not exist formally; comp is set by hiring managers.
  - 23% of "Senior Engineers" have base < $145K; 18% > $210K — a 45% spread at same title.
  - Helix Motion acquisition employees averaged 17% below Aerostream-native peers at equivalent scope (acquisition comp wasn't normalized).
  - 6 internal comp-equity complaints filed Q3 2026.
- **Performance calibration issues:**
  - Director ratings distribution: 52% "Exceeds" vs. target 25-30%.
  - No clear promotion-to-Staff criteria; 3 of 21 Staff Engineers were promoted without a panel review.
- **Benchmark data purchased:** Radford Global Technology Survey, Q3 2026 — 75th percentile targeting approved by Board for critical roles.
- **Budget:** $1.8M comp-adjustment budget for 2027 to close gaps identified by new architecture (roughly 1.2% of total eng comp).
- **Political constraints:**
  - VP Eng Jin-Soo has said "no one gets demoted in title" but is open to leveling at the same title with documented expectations.
  - CEO (Elena Torres) wants the framework to support planned scale from 180 to 275 engineers by end of 2028.
  - Helix Motion leadership has pushed back on "assimilation" framing; any cross-walk must be respectful.

## Artifact specification
A Job Architecture + Leveling deliverable with the following components:
1. **Framework philosophy** — 1 page. Principles (e.g., dual-track IC/Mgmt; clear criteria; calibration mandatory; comp bands follow levels). State what this framework will and will not do.
2. **Level scaffold** — unified level ladder covering both IC and Manager tracks with numeric levels (L3 through L9 or similar). For each level: role archetype, scope of impact, autonomy, influence, technical complexity, and years-of-experience proxy (with caveat).
3. **Discipline-specific job families** — for each of 6 disciplines: level-by-level job descriptions (1-paragraph archetype + 4-6 proficiency indicators). Must handle TPM and Hardware as first-class families, not footnotes.
4. **Leveling rubric / matrix** — observable proficiency indicators on dimensions (technical depth, scope, autonomy, leadership, cross-functional influence, mentoring). Used by calibration committees.
5. **Promotion criteria & process** — what's required to advance each level, the panel/calibration structure, cadence (annual? twice yearly?), and the evidence packet expected.
6. **Title + comp band mapping** — current titles → new level ladder crosswalk (the politically sensitive step). Include comp band table: Level / 25th / 50th / 75th / Max. Tied to Radford benchmark.
7. **Helix Motion crosswalk** — specific handling of 19 acquired employees: level-assignment methodology, comp-equity remediation plan, communication approach.
8. **Implementation plan** — timeline from Dec 2026 communication through Jan 2027 manager training through Feb 2027 employee conversations through March 2027 comp adjustments. Change-management touchpoints.
9. **Equity impact analysis** — projected changes by demographic group (gender, race/ethnicity, Helix vs. native, tenure) to detect and mitigate disparate impact before rollout.
10. **Risk register & communication plan** — top 6-8 risks (attrition, title grief, legal exposure from equity remediation, VP Eng political capital) with mitigation and pre-drafted key messages.

Tone: HR-professional but unafraid of the political specifics. Both legally defensible and operationally actionable. Acknowledges human impact while holding to framework principles.

## Output format
Markdown document with embedded tables, 10-14 pages. Centerpiece tables: level scaffold, leveling rubric, title crosswalk, comp bands. Must be usable by a calibration committee without requiring a separate operator manual.

## Iteration targets
1. **Make the level scaffold specific** — v1 often writes generic "Senior Engineer: owns a feature." Iterate to observable indicators: "At L5 Senior Engineer, typically owns delivery of a 3-6 month feature area, operates autonomously within a team, provides technical review on peer PRs, begins to influence cross-team design."
2. **Fix the Helix Motion crosswalk tone and substance** — v1 risks sounding like "assimilation." Iterate to a methodology that assesses role-scope not company-of-origin, proposes a comp-equity look-back with named budget ($ per employee avg), and offers a 1:1 communication protocol.
3. **Strengthen the leveling rubric with differentiation between adjacent levels** — v1 often blurs L5 and L6. Iterate to behavior indicators where the difference is operationally clear (e.g., L5 "reviews design docs in own team"; L6 "authors design docs that cross 2+ teams").
4. **Tighten the Staff/Principal distinction** — the current org has role ambiguity here. v1 may paper over it. Iterate to crisp separation: Staff = technical leader within a domain / org of ~30 engineers; Principal = technical leader across the Engineering org, directly shapes multi-year technical direction.
5. **Make the equity impact analysis real** — v1 may handwave. Iterate to a named methodology (e.g., OFCCP-style adverse-impact analysis at each level transition, plus pre-read with Legal before comp adjustment letters ship).
6. **Convert political constraints into framework language** — v1 may ignore the VP's "no demotions" edict. Iterate to a principled "level calibration at first rollout holds title; expectations realigned; future-state level changes follow standard promotion/demotion process" — satisfying both the political need and framework integrity.

## Success criteria
(For evaluator use only.)
1. Level scaffold covers at least 6 levels (IC) and 4 levels (Manager) with distinct, observable criteria per level.
2. Title crosswalk maps current titles to new levels with a principle that respects VP Eng's "no demotions" edict (e.g., all current titles hold, expectations realigned).
3. Comp band table ties to named benchmark (Radford 75th percentile or similar) with bands for each level that expand reasonably at higher levels.
4. Helix Motion crosswalk includes a specific comp-equity remediation budget number and a communication methodology.
5. Promotion process names panel composition, cadence, and evidence packet requirements.
6. Equity impact analysis methodology is named (not "we'll review for equity") with a specific reviewer (Legal + People Analytics) and a pre-launch gate.
7. At least two disciplines beyond Software (e.g., Hardware, TPM) are treated with equal rubric depth — not copied from Software.

## Scope target
A v1 at ~15 minutes should contain: framework principles, level scaffold with 5-7 levels and archetype descriptions, one fully fleshed-out discipline family (Software) with L3-L8 criteria, a draft leveling rubric with 4-6 dimensions, title crosswalk at the summary level, comp band table tied to benchmark percentile, and a rollout timeline skeleton. Full Hardware/TPM/Firmware discipline detail, Helix Motion crosswalk specifics, and equity-impact analysis methodology are iteration targets.
