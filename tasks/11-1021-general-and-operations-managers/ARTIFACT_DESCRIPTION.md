# Q3 2026 Operational Review: Riverton Distribution Center Consolidation

## Occupation
- **SOC:** 11-1021
- **Title:** General and Operations Managers

## Scenario
Meridian Parcel Logistics, a $340M regional parcel carrier serving the Great Lakes and Ohio
Valley, is six weeks into consolidating its Riverton, OH distribution center (DC-07) into the
larger Columbus hub (DC-03) to remove $4.2M of annual cost. GM Daniela Okafor must present a Q3
operational review to the COO, Priya Venkataraman, on October 14, 2026, covering throughput,
service-level impact, attrition, and the go/no-go decision on closing DC-07's remaining sort
line by December 1. The review will inform whether the company proceeds with the planned $1.8M
severance and lease-exit spend in Q4, and will be shared with the three-person Consolidation
Steering Committee (CFO Terrence Yoo, CHRO Miranda Ellis-Trent, VP Customer Ops Derek Alcott).

## Inputs
The model starts with this dataset and context:

### DC-07 (Riverton) — pre-consolidation baseline, Jan-Jun 2026
- Avg daily outbound packages: 42,800
- On-time delivery (OTD) %: 96.4%
- Labor cost per package: $1.87
- Headcount: 214 FTE
- Peak-day throughput: 58,000 (Black Friday test pull 2025)
- Average dock-to-stock: 27 min

### DC-03 (Columbus) — post-consolidation, Jul-Sep 2026
- Avg daily outbound packages: 71,200 (was 33,500 pre-consolidation)
- OTD %: 92.1% (vs. internal target of 95.0%, contractual floor 93.0% for enterprise)
- Labor cost per package: $1.72
- Headcount: 368 FTE (added 154 from DC-07 + 89 net new; 65 DC-07 employees declined transfer)
- Voluntary attrition Jul-Sep: 14.3% annualized (vs. 8.1% trailing 12mo)
- Sort-line capacity utilization: 94% peak, 78% avg
- First-week-post-transfer productivity of DC-07 hires: 68% of tenured-rep rate
- Supervisor span of control: 1:28 avg (vs. company standard 1:18)

### Customer impact
Two enterprise accounts (NorthStar Retail, $11M ARR; Evergreen Grocers, $6.4M ARR) issued
service-credit claims totaling $287K in August. NorthStar's contract is up for renewal Feb
2027. Three other top-25 accounts (Carolina Outfitters, BlueSky Fitness, Prairie Hardware)
have raised concerns but not filed credits. Net Promoter score from the Sep 2026 enterprise
survey dropped from 42 to 31.

### DC-07 wind-down costs still to incur
- Severance: $1.1M (covers 65 non-transferring employees + 12 redundant supervisors)
- Lease exit: $520K (early-termination clause; current lease runs through Aug 2027)
- Equipment relocation: $180K (two sort lines and one sorter being moved to DC-03 or disposed)
- Total: $1.8M

### Open operational issues
- DC-03 dock congestion 4-7 AM (trailers waiting 42 min avg vs. 18 min target)
- Inbound linehaul from Cincinnati misrouted on 6% of loads in August (was 1.2% pre-consolidation)
- WMS pick-path routing not re-tuned after layout changes; avg picker travel +19%
- Two on-the-job injuries in August (strain + near-miss forklift), vs. zero in all of H1

### Budgetary/financial guardrails
- The $4.2M annualized savings was predicated on DC-07 fully closed by Dec 1 and labor cost/pkg at DC-03 holding at $1.68 or better.
- Enterprise service-credit exposure was budgeted at $400K/year; YTD Aug trending to $1.1M annualized.
- The Q4 forecast currently shows $0.9M of the $4.2M annualized savings realized; remainder flows in Q1-Q2 2027 if closure proceeds Dec 1.

## Artifact specification
An executive operational review document structured for a 45-minute meeting with the COO and
three VPs (Operations, HR, Customer Ops). Required sections in this order:

1. **Executive summary** (half page): current state snapshot, recommendation, specific
   decision requested from the COO, and the single most important risk being flagged.
2. **Consolidation scorecard** — a table comparing pre-consolidation baseline vs. current
   state on throughput, OTD, cost/package, attrition, safety incidents, customer impact.
   Traffic-light status (Green / Yellow / Red) per metric with numeric delta.
3. **Root-cause analysis** of the OTD gap (92.1% vs. 95.0% target): what's driving it, with
   quantified contributors summing to the 2.9 pp gap. Each contributor tied to a specific
   operational metric and proposed countermeasure.
4. **Customer risk assessment**: NorthStar and Evergreen specifically — renewal/retention
   risk, mitigation actions, accountable owner, escalation path. Include a "watchlist" of
   three secondary accounts.
5. **Decision memo** on December 1 DC-07 sort-line closure: three options (proceed on Dec 1
   / delay 60 days to Feb 1 / delay 120 days to Apr 1). For each option: annualized savings
   impact, incremental cost, customer-risk implication, and the trigger condition that would
   make that option the right choice.
6. **Q4 operational plan**: 5-8 specific workstreams. Each with owner role, due date within
   Q4, specific quantitative success metric, and dependency notes.
7. **Staffing & attrition plan**: how to bring attrition from 14.3% back toward 8%; includes
   a supervisor-ratio correction, a retention bonus proposal, and the re-training plan for
   the 154 DC-07 transfers.
8. **Appendix**: assumptions, data sources, and a list of open questions for the COO.

Tone: direct, numerate, decision-oriented. No hedging prose; bullet-dense. Avoid the words
"robust," "leverage," "synergies," "unprecedented." Active voice throughout.

## Output format
A single Markdown document, ~6-9 pages when rendered (roughly 1,200-1,800 words plus tables).
Must include at least two structured tables (scorecard, decision matrix) and one quantified
root-cause breakdown. No charts required, but reserve labeled placeholders where charts would
go in the final deck (e.g., "[FIG 1: Daily OTD July-Sep, DC-03 vs. 95% target]").

## Iteration targets
1. **Sharpen the OTD root-cause decomposition** — v1 will likely attribute the gap vaguely
   ("training gaps," "volume surge"). A better version quantifies each contributing cause
   (e.g., "dock congestion = 1.4 pp, linehaul misrouting = 0.9 pp, new-hire productivity
   curve = 0.6 pp") tied to observable operational data, and each contributor should sum
   to ~2.9 pp with stated residual.
2. **Strengthen the NorthStar retention plan** — v1 may offer boilerplate ("proactive
   communication"). Iterate to a specific action sequence with owner, date, and measurable
   trip-wire (e.g., "If Oct OTD for NorthStar-dedicated lanes <94%, escalate to enterprise
   sales for contract concession conversation before Nov 15"). Include a "save" concession
   envelope pre-authorized with the CFO.
3. **Make the Dec 1 decision framework crisper** — v1 tends to list pros/cons. Push toward
   an expected-value framing or a defined set of trip-wires that would flip the
   recommendation. The three options must have clear and distinct trigger conditions, not
   overlapping generalities.
4. **Tighten the operational workstream list** — v1 often has 12+ vague items. Cut to 5-8
   high-leverage, accountable items; each should be verifiable in 30 days, have a named
   owner (not "Operations"), and a numeric success metric (not "improve dock times").
5. **Surface the attrition-to-OTD causal link** — 14.3% attrition is likely driving OTD; v1
   may treat them as separate bullets. A stronger version shows the mechanism (attrition →
   new-hire mix → productivity → processing time → OTD) and whether proposed actions
   address cause or symptom.
6. **Add sensitivity on the recommendation** — what would change the GO to a NO-GO? Name two
   or three scenarios (e.g., "If NorthStar explicitly states contract is at risk in their
   Oct 28 QBR, delay closure by 60 days").

## Success criteria
(For evaluator use only.)
1. The OTD gap is decomposed into components that sum to ~2.9 pp (±0.3 pp, with stated
   residual), with each component grounded in a specific data point from the inputs.
2. The Dec 1 decision is stated unambiguously (proceed / delay 60 / delay 120) with at
   least one named trigger condition that, if met, would flip the recommendation.
3. NorthStar and Evergreen are named individually with distinct risk profiles and actions
   — not lumped together. NorthStar's Feb 2027 renewal is explicitly addressed.
4. The Q4 workstream list has 5-8 items, each with a named owner role, a due date within
   Q4, and a numeric success metric.
5. At least one table directly compares baseline to current state across all tracked
   metrics with correct arithmetic (sums, deltas, percentage calculations).
6. The executive summary is readable in 60 seconds and states the ask clearly — a COO
   should be able to prepare in one minute.
7. The attrition plan has at least one action that addresses the cause (e.g., supervisor
   ratio, compensation, shift stability), not just retention-bonus bandaid.

## Scope target
A v1 at ~15 minutes should contain: executive summary with stated recommendation, the
scorecard table covering at least 5 metrics, an initial root-cause hypothesis for OTD (even
if unquantified), a draft decision framing for Dec 1 with at least two options and rough
trade-offs, and 4-5 workstream items. Customer risk section may be thin but must name both
accounts (NorthStar and Evergreen) with at least one action each. Staffing/attrition section
and appendix can be minimal at v1. By v2/v3 the OTD decomposition should reconcile
numerically, the decision options should have explicit trigger conditions, and the workstream
list should have named owners and metrics.
