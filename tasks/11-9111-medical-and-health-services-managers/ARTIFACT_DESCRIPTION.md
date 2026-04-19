# CMS Hospital-Acquired Conditions Reduction Plan — St. Brenna Memorial, FY2027

## Occupation
- **SOC:** 11-9111
- **Title:** Medical and Health Services Managers

## Scenario
St. Brenna Memorial Hospital, a 412-bed community hospital in central Oregon (system: Cascadia
Health), has landed in the worst-performing quartile of the CMS Hospital-Acquired Conditions
(HAC) Reduction Program for FY2026, triggering a 1% Medicare payment penalty (~$2.3M
annualized on $230M Medicare revenue). Director of Quality & Clinical Operations Harriet
Nakamura, RN, MHA, must deliver a 12-month HAC reduction plan to the CMO, Dr. Wendell
Burroughs, and the Quality & Safety Committee by May 22, 2026. The plan needs to drive the
hospital out of the worst quartile by the FY2028 measurement window (July 2026-June 2027
performance data) and will be shared with Joint Commission during the triennial survey cycle
in October 2026. The plan will also be reviewed by Cascadia's system quality committee and
by the hospital's Medical Executive Committee.

## Inputs
The model starts with:

### Current HAC measure performance (rolling 12mo, Mar 2025-Feb 2026)

| Measure                  | SIR  | Benchmark | 75th %ile | Trend (6mo) |
|--------------------------|------|-----------|-----------|-------------|
| CLABSI                   | 1.34 | 1.0       | 0.87      | Worsening   |
| CAUTI                    | 1.18 | 1.0       | 0.78      | Flat        |
| SSI (colon + hysterectomy| 0.94 | 1.0       | 0.80      | Improving   |
| MRSA bacteremia          | 1.62 | 1.0       | 0.71      | Worsening   |
| C. difficile             | 1.09 | 1.0       | 0.75      | Flat        |
| PSI-90 composite         | 1.21 | 1.0       | 0.86      | Worsening   |

### Internal metric drivers
- Central line utilization rate (ICU): 0.48 line-days/patient-day; national median 0.41
- Urinary catheter utilization: 0.31; national median 0.22
- Hand-hygiene compliance (direct observation): 74%; goal 90%
- Chlorhexidine (CHG) bathing compliance (ICU): 68% of line-days documented
- Antibiotic stewardship DOT (days of therapy per 1,000 pt-days): 812; benchmark ~700
- Post-op ambulation-by-4-hours compliance: 61%; goal 85%
- Sepsis bundle compliance (SEP-1): 58%; CMS penalty threshold

### Staffing / operations context
- Nursing vacancy rate: 14.3%; travel/agency RN fill: 22% of ICU hours (peaks at 31% on
  weekends)
- Infection Prevention department: 2.0 FTE IPs for 412 beds (IDSA/SHEA recommend 1 IP per
  69-100 beds; St. Brenna is at 1 per 206 — approximately half the recommended staffing)
- Antimicrobial Stewardship: 0.5 FTE pharmacist, 0.2 FTE physician champion
- EHR: Epic; CLABSI/CAUTI surveillance currently done manually by IP staff (no
  NHSN-connected automated module)

### Prior improvement efforts and their outcomes
- CLABSI bundle rollout 2023: trained 100% of ICU RNs; compliance audits stopped 2024 due
  to IP staffing reduction.
- Tracer survey by Joint Commission (2023) cited inconsistent line-necessity documentation.
- 2024 CAUTI reduction sprint: 12-week effort; SIR moved from 1.31 to 1.18 and held.
- 2025 hand-hygiene campaign: two "HH week" events; compliance moved from 69% to 74%,
  plateaued.
- Never-implemented: daily line-necessity rounds (proposed 2023; stalled on EHR build).

### Budget envelope
Up to $480K capital/opex for quality initiatives in FY2027. Must net-out favorably against
$2.3M penalty. System CFO is open to an additional $200K if the plan shows defensible ROI.

### Regulatory and accreditation context
- Joint Commission triennial survey: October 2026. Prior survey (2023) cited three Category
  C findings in Infection Control: IC.02.01.01 (infection prevention plan), NPSG.07.04.01
  (CLABSI prevention), and NPSG.07.05.01 (SSI prevention).
- Oregon Patient Safety Commission reportable HAIs: any cluster of 3+ within 30 days
  triggers state-level inquiry.
- CMS Quality Reporting: HAI data feeds into VBP, HACRP, Star Ratings.

### Clinical leadership and governance structure
- CMO: Dr. Wendell Burroughs (5 years tenure)
- CNO: Dr. Cassandra Liu
- Medical Staff President: Dr. Lalit Venkat
- Infection Prevention Medical Director: Dr. Sonia Aldrich (0.2 FTE)
- Quality Director: Harriet Nakamura (plan author)
- Physician champions for HAI reduction: one ICU intensivist currently; need more

## Artifact specification
A formal hospital-quality improvement plan with the following structure:

1. **Executive summary** — current state, penalty exposure, target state at FY2028
   measurement window, the three highest-impact interventions, cost-benefit summary.
2. **Measure-level performance analysis** — a table for each of the 6 HAC measures: SIR,
   benchmark, gap to 75th percentile, trend, and clinical and operational drivers.
3. **Root-cause / driver analysis for the worst three measures** (MRSA bacteremia,
   CLABSI, PSI-90 composite). Use a fishbone or 5-Whys framework; ground each cause in a
   specific internal metric (e.g., "MRSA bacteremia SIR 1.62 driven by: (a) central-line
   utilization 0.48 vs. median 0.41, (b) CHG bathing compliance 68%, (c) hand hygiene 74%,
   (d) 22% agency RN mix in ICU with lower bundle familiarity").
4. **Intervention portfolio** — 8-12 interventions prioritized into 3 waves (Q1 quick wins,
   Q2-Q3 systemic, Q4 sustainment). Each intervention: evidence base (named guideline or
   study), expected SIR improvement magnitude, cost, owner (Nursing / IP / Medical Staff /
   Supply Chain), implementation leads, measurement plan, and fidelity audit cadence.
5. **Governance structure** — committee cadence (Quality Council weekly? HAC Task Force
   monthly?), accountable executive (CMO? CNO?), clinician-champion model, frontline
   huddle structure, escalation path when a unit misses target.
6. **Measurement & transparency plan** — unit-level dashboards, which measures are posted
   publicly on units, audit cadence, data validation process.
7. **Joint Commission readiness crosswalk** — map interventions to relevant TJC IC and
   NPSG standards anticipated in the October 2026 survey (NPSG.07.01.01, NPSG.07.03.01,
   NPSG.07.04.01, NPSG.07.05.01, IC.02.01.01).
8. **Financial analysis** — $480K investment vs. $2.3M penalty, patient-days impact of
   reduced LOS from prevented HAIs (CLABSI adds ~11 days LOS, MRSA bacteremia ~14 days),
   3-year ROI. Honest treatment of the measurement-window lag (penalty relief accrues
   FY2028 at earliest).
9. **Staffing recommendation** — specifically, the IP FTE ask (1.5 additional FTE to reach
   1:117 beds, still below IDSA target of 1:100 but closer), with IDSA/SHEA citation,
   cost, and expected impact.
10. **Risk register** — 5-6 risks to plan execution (agency RN turnover, survey fatigue,
    sustained leadership attention, EHR build dependencies, stewardship pharmacist
    capacity) with mitigation.

Tone: clinically rigorous, evidence-cited, respectful of frontline staff. Must pass review
by a CMO, a CNO, and an IP director simultaneously. Avoid deficit-framing of nursing or
medical staff ("staff need to do better"); frame interventions as system-level supports.

## Output format
Markdown document with embedded tables, 8-12 pages, designed to become the canonical
committee artifact. Tables for measure performance, intervention portfolio, and TJC
crosswalk. Will also feed a 20-slide committee deck (not required in v1).

## Iteration targets
1. **Ground every intervention in a specific driver metric** — v1 tends to list generic
   bundles ("implement CLABSI bundle"). Iterate to: "Increase CHG bathing compliance from
   68% to 90% in ICU via EHR-enforced line-day documentation; expected CLABSI SIR
   reduction 0.3-0.5 based on [named study: Climo et al. NEJM 2013 or equivalent]."
2. **Quantify the IP staffing gap** — v1 may mention it generically. Iterate to: request
   +1.5 IP FTE ($195K fully loaded), cite IDSA benchmark of 1 IP per 100 beds, show that
   manual surveillance is a rate-limiter on real-time intervention and audit cadence.
3. **Prioritize interventions by leverage** — v1 lists interventions at equal weight. A
   better version ranks by (SIR impact × measure weight in HAC score × implementability)
   and shows the top 3. The HAC score weights measures roughly equally, but MRSA bacteremia
   at SIR 1.62 has the biggest gap to close.
4. **Connect staffing/agency-RN churn to HAC outcomes** — v1 may treat RN vacancy as an
   external constraint. Iterate to show the mechanism (CLABSI bundle compliance drops when
   agency RN proportion exceeds 20%) and propose a countermeasure (unit-based IP
   preceptor model, agency RN credentialing to CLABSI bundle before first ICU shift).
5. **Strengthen the Joint Commission crosswalk** — v1 may list standards generically.
   Iterate to map specific interventions to NPSG.07.01.01 (hand hygiene), NPSG.07.04.01
   (CLABSI), NPSG.07.05.01 (SSI), IC.02.01.01 (infection prevention plan) with evidence
   of compliance that will be produced by Oct 2026.
6. **Make the financial analysis honest about timing** — v1 may claim Q1 penalty savings.
   Iterate to show the 18-24 month lag in CMS measurement windows and when penalty relief
   actually accrues (FY2028 for FY2028 penalty based on Jul 2026-Jun 2027 data).
7. **Address the out-of-budget case** — v1 may stay within $480K. Iterate to show the
   case for the additional $200K if the CFO asks: where it goes (likely IP FTE plus
   automated surveillance module), expected incremental impact, and a clean ROI argument.

## Success criteria
(For evaluator use only.)
1. Each intervention cites a specific guideline (CDC, IDSA/SHEA, APIC, TJC NPSG) and names
   a measurable compliance KPI with a baseline and target.
2. MRSA bacteremia (SIR 1.62, highest) is treated as the top priority with at least 3
   targeted interventions; CLABSI (SIR 1.34) next.
3. IP staffing request is quantified specifically (e.g., "+1.5 FTE to reach 1 per 117
   beds, $195K cost") with IDSA/SHEA citation.
4. Financial analysis reflects the CMS measurement window lag — does not claim penalty
   relief in FY2027.
5. At least one intervention addresses the causal chain: nursing vacancy → agency RN →
   bundle compliance → HAC rate.
6. Joint Commission crosswalk references specific standards by number (e.g.,
   NPSG.07.05.01), not just "Joint Commission IC standards."
7. At least one early-win intervention (Wave 1, Q1) has a clearly defined Go-Live within
   8 weeks with a named owner.
8. Daily line-necessity rounds (historically stalled) appears in the plan with a specific
   owner and unblocking plan.

## Scope target
A v1 at ~15 minutes should contain: executive summary with penalty and target state,
measure performance table for all 6 measures, root-cause analysis for the top 2 measures
(MRSA bacteremia, CLABSI) at minimum, 5-6 prioritized interventions with owner and cost,
a draft governance structure, and a simple penalty-vs-investment ROI. TJC crosswalk and
3-wave intervention sequencing can be outlined. By v2/v3: full 8-12 interventions with
cited evidence, TJC crosswalk mapped to specific standards, and detailed measurement and
fidelity-audit plan per intervention.
