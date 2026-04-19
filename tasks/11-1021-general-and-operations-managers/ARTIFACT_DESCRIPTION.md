# Q3 2026 Operational Review: Riverton Distribution Center Consolidation

## Occupation
- **SOC:** 11-1021
- **Title:** General and Operations Managers

## Scenario
Meridian Parcel Logistics, a $340M regional parcel carrier, is six weeks into consolidating its Riverton, OH distribution center (DC-07) into the larger Columbus hub (DC-03) to remove $4.2M of annual cost. GM Daniela Okafor must present a Q3 operational review to the COO, Priya Venkataraman, on October 14, 2026, covering throughput, service-level impact, attrition, and the go/no-go decision on closing DC-07's remaining sort line by December 1. The review will inform whether the company proceeds with the planned $1.8M severance and lease-exit spend in Q4.

## Inputs
The model starts with this dataset and context:

- **DC-07 (Riverton) — pre-consolidation baseline, Jan-Jun 2026:**
  - Avg daily outbound packages: 42,800
  - On-time delivery (OTD) %: 96.4%
  - Labor cost per package: $1.87
  - Headcount: 214 FTE
- **DC-03 (Columbus) — post-consolidation, Jul-Sep 2026:**
  - Avg daily outbound packages: 71,200 (was 33,500 pre-consolidation)
  - OTD %: 92.1% (vs. internal target of 95.0%)
  - Labor cost per package: $1.72
  - Headcount: 368 FTE (added 154 from DC-07 + 89 net new; 65 DC-07 employees declined transfer)
  - Voluntary attrition Jul-Sep: 14.3% annualized (vs. 8.1% trailing 12mo)
  - Sort-line capacity utilization: 94% peak, 78% avg
- **Customer impact:** Two enterprise accounts (NorthStar Retail, $11M ARR; Evergreen Grocers, $6.4M ARR) issued service-credit claims totaling $287K in August. NorthStar's contract is up for renewal Feb 2027.
- **DC-07 wind-down costs still to incur:** $1.8M (severance $1.1M, lease exit $520K, equipment relocation $180K).
- **Open issues:** DC-03 dock congestion 4-7 AM (trailers waiting 42 min avg vs. 18 min target); inbound linehaul from Cincinnati misrouted on 6% of loads in August.

## Artifact specification
An executive operational review document structured for a 45-minute meeting with the COO and three VPs. Required sections:
1. **Executive summary** (half page): current state, recommendation, decision requested.
2. **Consolidation scorecard** — a table comparing baseline vs. current on throughput, OTD, cost/package, attrition, customer impact. Traffic-light status per metric.
3. **Root-cause analysis** of the OTD gap (92.1% vs. 95.0% target): what's driving it, with quantified contributors summing to the gap.
4. **Customer risk assessment:** NorthStar and Evergreen specifically — retention risk, mitigation actions, accountable owner.
5. **Decision memo** on December 1 DC-07 sort-line closure: options (proceed / delay 60 days / delay 120 days) with cost, risk, and trigger conditions.
6. **Q4 operational plan:** 5-8 specific workstreams with owner, due date, success metric.
7. **Appendix:** assumptions, data sources, and questions for the COO.

Tone: direct, numerate, decision-oriented. No hedging prose; bullet-dense.

## Output format
A single Markdown document, ~6-9 pages when rendered (roughly 1,200-1,800 words plus tables). Must include at least two structured tables and one quantified root-cause breakdown. No charts required, but reserve labeled placeholders where charts would go in the final deck.

## Iteration targets
1. **Sharpen the OTD root-cause decomposition** — v1 will likely attribute the gap vaguely ("training gaps," "volume surge"). A better version quantifies each cause (e.g., "dock congestion = 1.4 pp, linehaul misrouting = 0.9 pp, new-hire productivity curve = 0.6 pp") and ties to the observable operational data.
2. **Strengthen the NorthStar retention plan** — v1 may offer boilerplate ("proactive communication"). Iterate to a specific action sequence with owner, date, and measurable trip-wire (e.g., "If Oct OTD for NorthStar lanes <94%, escalate to enterprise sales for contract concession conversation before Nov 15").
3. **Make the Dec 1 decision framework crisper** — v1 tends to list pros/cons. Push toward an expected-value framing or a defined set of trip-wires that would flip the recommendation.
4. **Tighten the operational workstream list** — v1 often has 12+ vague items. Cut to 5-8 high-leverage, accountable items; each should be verifiable in 30 days.
5. **Surface the attrition-to-OTD causal link** — 14.3% attrition is likely driving OTD; v1 may treat them as separate bullets. A stronger version shows the mechanism and whether proposed actions address cause or symptom.
6. **Add sensitivity on the recommendation** — what would change the GO to a NO-GO? Name the two or three scenarios.

## Success criteria
(For evaluator use only.)
1. The OTD gap is decomposed into components that sum to ~2.9 pp, with each component grounded in a specific data point from the inputs.
2. The Dec 1 decision is stated unambiguously (proceed / delay) with a named trigger condition that, if met, would flip the recommendation.
3. NorthStar and Evergreen are named individually with distinct risk profiles and actions — not lumped together.
4. The Q4 workstream list has 5-8 items, each with a named owner role, due date within Q4, and a numeric success metric.
5. At least one table directly compares baseline to current state across all five tracked metrics with correct arithmetic.
6. The executive summary is readable in 60 seconds and states the ask clearly.

## Scope target
A v1 at ~15 minutes should contain: executive summary with stated recommendation, the scorecard table, an initial root-cause hypothesis for OTD (even if unquantified), a draft decision framing for Dec 1, and 4-5 workstream items. Customer risk section may be thin but must name both accounts. Appendix can be minimal.
