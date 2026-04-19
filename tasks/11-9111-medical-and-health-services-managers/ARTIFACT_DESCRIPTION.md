# CMS Hospital-Acquired Conditions Reduction Plan — St. Brenna Memorial, FY2027

## Occupation
- **SOC:** 11-9111
- **Title:** Medical and Health Services Managers

## Scenario
St. Brenna Memorial Hospital, a 412-bed community hospital in central Oregon, has landed in the worst-performing quartile of the CMS Hospital-Acquired Conditions (HAC) Reduction Program for FY2026, triggering a 1% Medicare payment penalty (~$2.3M annualized). Director of Quality & Clinical Operations Harriet Nakamura, RN, MHA, must deliver a 12-month HAC reduction plan to the CMO, Dr. Wendell Burroughs, and the Quality & Safety Committee by May 22, 2026. The plan needs to drive out of the worst quartile by the FY2028 measurement window (July 2026-June 2027 performance data) and will be shared with Joint Commission during the triennial survey cycle in October 2026.

## Inputs
The model starts with:

- **Current HAC measure performance (rolling 12mo, Mar 2025-Feb 2026):**
  - CLABSI (Central Line-Associated Bloodstream Infection) SIR: 1.34 (national benchmark 1.0, 75th percentile 0.87)
  - CAUTI (Catheter-Associated UTI) SIR: 1.18 (benchmark 1.0, 75th percentile 0.78)
  - SSI (colon + hysterectomy combined) SIR: 0.94 (meeting benchmark)
  - MRSA bacteremia SIR: 1.62 (benchmark 1.0, 75th percentile 0.71)
  - C. difficile SIR: 1.09 (benchmark 1.0, 75th percentile 0.75)
  - CMS Patient Safety Indicator (PSI-90) composite: 1.21 (benchmark 1.0)
- **Internal metric drivers:**
  - Central line utilization rate: 0.48 line-days/patient-day (ICU); national median 0.41.
  - Urinary catheter utilization: 0.31; national median 0.22.
  - Hand-hygiene compliance (direct observation): 74% (goal 90%).
  - Chlorhexidine bathing compliance (ICU): 68% of line-days.
  - Antibiotic stewardship DOT (days of therapy per 1,000 pt-days): 812 (benchmark ~700).
- **Staffing / operations context:**
  - Nursing vacancy rate: 14.3%; travel/agency RN fill: 22% of ICU hours.
  - Infection Prevention department: 2.0 FTE IPs for 412 beds (IDSA/SHEA recommend 1 per 69-100 beds; we're at 1 per 206).
  - EHR: Epic; CLABSI/CAUTI surveillance currently done manually by IP staff.
- **Prior improvement efforts:**
  - CLABSI bundle rollout 2023; compliance audits stopped 2024.
  - Last tracer survey by Joint Commission (2023) cited inconsistent line-necessity documentation.
- **Budget envelope:** Up to $480K capital/opex for quality initiatives; must net-out vs. $2.3M penalty.

## Artifact specification
A formal hospital-quality improvement plan with the following structure:
1. **Executive summary** — current state, penalty exposure, target state at FY2028 measurement window, the three highest-impact interventions, cost-benefit summary.
2. **Measure-level performance analysis** — a table for each of the 6 HAC measures: SIR, benchmark, gap to 75th percentile, clinical and operational drivers.
3. **Root-cause / driver analysis for the worst three measures** (MRSA bacteremia, CLABSI, PSI-90 composite). Use a fishbone or 5-Whys framework; ground each cause in a specific internal metric (e.g., "MRSA bacteremia SIR 1.62 driven by: (a) central-line utilization 0.48 vs. median 0.41, (b) CHG bathing compliance 68%...").
4. **Intervention portfolio** — 8-12 interventions prioritized into 3 waves (Q1 quick wins, Q2-Q3 systemic, Q4 sustainment). Each intervention: evidence base (named guideline or study), expected SIR improvement, cost, owner (Nursing / IP / Medical Staff / Supply Chain), implementation leads, measurement plan.
5. **Governance structure** — committee cadence, accountable executive, clinician-champion model, frontline huddle structure.
6. **Measurement & transparency plan** — unit-level dashboards, which measures are posted publicly on units, audit cadence.
7. **Joint Commission readiness crosswalk** — map interventions to relevant TJC IC and NPSG standards anticipated in the October 2026 survey.
8. **Financial analysis** — $480K investment vs. $2.3M penalty, patient-days impact of reduced LOS from prevented HAIs, 3-year ROI.
9. **Risk register** — 5-6 risks to plan execution (staffing, survey fatigue, etc.) with mitigation.

Tone: clinically rigorous, evidence-cited, respectful of frontline staff. Must pass review by a CMO, a CNO, and an IP director simultaneously.

## Output format
Markdown document with embedded tables, 8-12 pages, designed to become the canonical committee artifact. Tables for measure performance, intervention portfolio, and TJC crosswalk. Will also feed a 20-slide committee deck (not required in v1).

## Iteration targets
1. **Ground every intervention in a specific driver metric** — v1 tends to list generic bundles ("implement CLABSI bundle"). Iterate to: "Increase CHG bathing compliance from 68% to 90% in ICU via EHR-enforced line-day documentation; expected CLABSI SIR reduction 0.3-0.5 based on [named study]."
2. **Quantify the IP staffing gap** — v1 may mention it generically. Iterate to: request 1.5 additional IP FTE, cite IDSA benchmark, show that manual surveillance is a rate-limiter on interventions.
3. **Prioritize interventions by leverage** — v1 lists interventions at equal weight. A better version ranks by (SIR impact × measure weight in HAC score × implementability) and shows the top 3.
4. **Connect staffing/agency-RN churn to HAC outcomes** — v1 may treat RN vacancy as an external constraint. Iterate to show the mechanism (CLABSI bundle compliance drops with agency RN proportion > 20%) and propose a countermeasure (unit-based IP preceptor model).
5. **Strengthen the Joint Commission crosswalk** — v1 may list standards generically. Iterate to map specific interventions to NPSG.07.01.01, NPSG.07.04.01, IC.02.01.01, etc., with evidence of compliance.
6. **Make the financial analysis honest about timing** — v1 may claim Q1 penalty savings. Iterate to show the 18-24 month lag in CMS measurement windows and when penalty relief actually accrues.

## Success criteria
(For evaluator use only.)
1. Each intervention cites a specific guideline (CDC, IDSA/SHEA, APIC, TJC NPSG) and names a measurable compliance KPI.
2. MRSA bacteremia (SIR 1.62, highest) is treated as the top priority with at least 3 targeted interventions.
3. IP staffing request is quantified specifically (e.g., "+1.5 FTE to reach 1 per 117 beds") with IDSA citation.
4. Financial analysis reflects the CMS measurement window lag — does not claim penalty relief in FY27.
5. At least one intervention addresses the causal chain: nursing vacancy → agency RN → bundle compliance → HAC rate.
6. Joint Commission crosswalk references specific standards (e.g., NPSG.07.05.01) not just "Joint Commission IC standards."

## Scope target
A v1 at ~15 minutes should contain: executive summary with penalty and target state, measure performance table for all 6 measures, root-cause analysis for the top 2 measures, 5-6 prioritized interventions with owner and cost, a draft governance structure, and a simple penalty-vs-investment ROI. TJC crosswalk and 3-wave intervention sequencing are iteration targets.
