# Warehouse Slotting & Aisle Redesign Proposal — Pallas Lighting, Memphis DC

## Occupation
- **SOC:** 11-3071
- **Title:** Transportation, Storage, and Distribution Managers

## Scenario
Pallas Lighting, a $220M commercial and architectural lighting wholesaler, operates a
380,000 sq-ft distribution center in Memphis, TN serving 2,800 B2B customers (specifiers,
distributors, electrical wholesalers) across 28 states. DC Manager Rafael Mendoza must
present a slotting + aisle redesign proposal to the VP of Supply Chain, Ines Verhoeven,
by October 30, 2026, for a January 12-16, 2027 implementation window (over the MLK
weekend shutdown). The business goals: reduce pick travel per line by 18%, cut mis-picks
from 0.28% to below 0.15%, and free space to absorb the 2027 SKU assortment expansion
(+1,450 SKUs from the newly acquired Coral Park Exterior line) without adding square
footage. The proposal will be reviewed by VP SC Verhoeven, the CFO (Diego Menendez), and
the VP of Operations (Karla Stobridge).

## Inputs
The model starts with:

### Facility
- 380,000 sq-ft; clear height 32 ft; selective pallet racking 4 beams high for reserve;
  pick modules for case pick
- 18 aisles currently at 9-ft aisle width
- Monthly outbound: 41,000 orders, average 14 lines/order = 574,000 lines/month
- Average pick travel 0.44 miles/order (Locus WMS data, trailing 90 days)
- Picker headcount: 52 associates across 2 shifts; average picks/hour 98; labor rate
  $24.50/hr fully loaded
- Annual direct labor cost in pick operation: ~$2.65M

### SKU profile (pre-Coral Park)
- Total active SKUs: 9,820
- Velocity distribution:
  - A items (top 20%): 1,964 SKUs = 78% of line volume
  - B items (next 30%): 2,946 SKUs = 17% of line volume
  - C items (remaining 50%): 4,910 SKUs = 5% of line volume
- Current slotting: legacy alphabetical by manufacturer then SKU number
- A items are distributed across all 18 aisles (not concentrated)
- Slot occupancy: 86% of forward-pick slots occupied
- Slot mis-sizing: 22% of forward-pick slots are oversized for current velocity

### Incoming assortment (Coral Park Exterior, acquired June 2026)
- 1,450 SKUs
- ~68% outdoor fixtures (larger cube, heavier per line — avg 2.3 lbs vs. 0.8 lbs for
  typical indoor)
- Projected to be ~11% of line volume in Year 1, ~18% in Year 2
- Current temp storage in Aisles 17-18 (non-optimal; 0.52 mi avg travel from dock)

### Current pain points
- Congestion in Aisles 3-5 (current A items due to alphabetical positioning of top
  manufacturers) peak 10AM-1PM
- Aisles 17-18 (slow movers + Coral Park temp) have pickers idling during wave flushes
- Mis-pick rate 0.28% with 62% of mis-picks attributed to look-alike SKU pairs (similar
  PN, different voltage or finish) stored adjacent
- 8 lift-truck near-misses YTD 2026 in the 9-ft aisles, particularly near Coral Park
  heavy traffic
- Reverse logistics (returns) processing delayed by DC congestion

### Technology & constraints
- Locus WMS (pick-path optimization available but not tuned to new slot velocity since
  acquisition)
- Capex envelope: $420K (racking mods, signage, conveyor adjustments, label printing)
- No new square footage available — DC is landlocked between a DHL facility and a rail
  spur
- Implementation must complete in 72 hours (Fri evening Jan 12 - Mon evening Jan 15)
- Operations resume Jan 16 Tuesday morning

### Measured data on alternatives (from simulation vendor Solvexia, August 2026)
- **Option A: Velocity-based slotting (ABC pure).** -22% travel per line; +$380K capex;
  mis-pick estimated 0.19% (adjacency of high-velocity pairs persists); space freed: 12%.
- **Option B: Family-grouped slotting (ABC within product family).** -14% travel; +$260K
  capex; mis-pick estimated 0.14% (family grouping reduces look-alike adjacency); space
  freed: 8%.
- **Option C: Hybrid (golden zone for A items, family grouping for B/C).** -19% travel;
  +$340K capex; mis-pick estimated 0.13%; space freed: 11%.

### Labor economics
- Current pick-travel cost: $2.65M × [travel time as % of pick time, ~28%] = ~$742K/yr
- 18% travel reduction = ~$134K annual savings baseline
- 19% travel reduction (hybrid) = ~$141K annual savings
- Throughput capacity gain: 18-22% more picks per labor hour → absorbs Coral Park volume

## Artifact specification
A warehouse redesign proposal with the following structure:

1. **Executive summary** — current state (travel, mis-pick, throughput, congestion),
   proposed state, recommendation, capex, implementation window, financial case summary.
2. **Current state assessment** — data-driven: aisle heat map (described or tabular),
   velocity profile, slot occupancy, mis-pick root-cause breakdown, safety near-miss
   summary.
3. **Design options comparison** — 3 options (velocity-pure, family-grouped, hybrid) with
   travel reduction, capex, mis-pick impact, space liberation, disruption risk, and
   scalability to Coral Park volume growth. Tabular comparison.
4. **Recommendation & rationale** — pick one option; explain trade-offs including what's
   given up relative to each of the other two.
5. **New layout specification** — zone by zone: which aisles hold A / B / C; golden-zone
   definition (height band in inches); where Coral Park lives (consolidated aisles or
   distributed); how oversized slots are re-profiled to fit small-velocity SKUs.
6. **Slotting rules & governance** — criteria for a SKU to enter the A zone, re-slotting
   cadence (quarterly re-slot based on trailing 90-day velocity? monthly for Coral Park
   during ramp?), exceptions process, look-alike-SKU separation policy.
7. **Implementation plan** — 72-hour Gantt with hour-by-hour sequencing Fri-Mon. Crew
   structure (e.g., Crew 1: aisles 1-6; Crew 2: aisles 7-12; Crew 3: aisles 13-18).
   Contingency if running behind at each checkpoint. Named Go/No-Go gates at 24, 48, 60
   hours.
8. **Financial case** — $420K capex vs. travel-reduction labor savings (calculate labor
   $ saved per year), mis-pick cost avoidance (60% of cost of mis-pick is labor + customer
   return = ~$28 per mis-pick; at 41,000 orders/mo with 0.13 pp mis-pick reduction =
   meaningful number), throughput capacity for Coral Park, ROI / payback period.
9. **Risk register** — 5-7 risks (pick-error spike post-cutover during associate
   re-orientation, training rollout, Coral Park forecast miss, congestion if A zone too
   concentrated, ergonomic issues if golden zone overweighted) with mitigation.
10. **KPI dashboard (post-cutover 30 days)** — the 4-6 metrics tracked daily for the first
    30 days post-implementation, with rollback triggers.

Tone: operations-rigorous, quantitative. Should be directly usable to brief the DC
associates (simplified), the VP (this version), and the CFO (with financial appendix).

## Output format
Markdown document with embedded tables, 6-9 pages. Include a schematic layout description
(ASCII or tabular representation of aisle zones) — no image required but the zoning must
be specified in enough detail that a slotting planner can implement.

## Iteration targets
1. **Lock the recommendation to the data** — v1 often picks the hybrid option without
   showing the arithmetic. Iterate to a quantitative trade-off table: hybrid gives 19%
   vs. pure's 22% travel reduction, but at $40K lower capex AND reduces mis-pick more
   effectively due to family grouping separating look-alike SKUs. The expected-value
   framing should explicitly show hybrid is within ~$7K/yr of pure's labor savings but
   $40K cheaper upfront and safer on mis-picks.
2. **Improve the 72-hour implementation plan** — v1 tends to list phases. Iterate to
   hour-by-hour: "Fri 7pm - aisle freeze; Sat 2am - start Aisle 5 re-profile (Crew 1);
   Sat 8am - first re-slot wave of top 200 A SKUs to new positions; Sat 4pm - checkpoint
   #1, Go/No-Go on schedule; Sun 12am - Coral Park consolidation..." with named crews
   and go/no-go checkpoints.
3. **Quantify labor savings honestly** — v1 claims big $ but handwaves the calculation.
   Iterate to: (41,000 orders/mo × 14 lines/order × 12 months = 6.88M lines/yr) ×
   (0.44 mi/order → 0.356 mi/order reduction of ~0.084 mi × $24.50/hr × pick-travel
   minutes per mile) = explicit labor savings of ~$140K/yr.
4. **Address the mis-pick driver specifically** — v1 may say "re-slot to reduce
   mis-picks." Iterate to: 62% of mis-picks are look-alike pairs; the new family-grouped
   layout separates named pairs (e.g., 120V vs. 277V variants of the same fixture) by at
   least 2 aisles; expected mis-pick reduction of 0.09 pp attributable to this mechanism
   alone, remaining 0.06 pp from reduced travel-stress and better slot labeling.
5. **Plan for Coral Park growth Year 2** — v1 sizes for Year 1 (11% of volume). Iterate
   to explicit slot reservation/expansion strategy: reserve 40 additional A-zone slot
   positions in 2027 for Coral Park SKUs that climb into A-velocity by Q4, and plan a
   mid-year re-slot (Jun 2027) to capture Year 2 18% mix.
6. **Golden-zone definition must be actionable** — v1 says "ergonomic height." Iterate
   to: "slots between 18 inches and 60 inches vertical height on aisles 3-8, beam level
   B, with 12-18 inch pick-face width." A slotting planner should be able to execute
   without further interpretation.
7. **Rollback trigger definition** — v1 may omit. Iterate to: "If mis-pick rate on Day 3
   post-cutover exceeds 0.50% (2x baseline), invoke rollback protocol: re-route to backup
   pick paths, flag top 20 problem SKUs for manual re-slot before Day 7."

## Success criteria
(For evaluator use only.)
1. Recommendation is stated explicitly (one of the three options), with trade-offs vs.
   the other two options named in 2-3 sentences each.
2. Labor savings calculation reconciles: (travel reduction % × current labor cost) with
   stated labor rate and hours baseline.
3. Implementation plan has hour-by-hour or quarter-day granularity for the 72-hour
   window, not just phase-level, with at least 2 Go/No-Go checkpoints.
4. Slotting rules include a specific mis-pick/look-alike-SKU separation policy (e.g.,
   no two SKUs differing only by voltage within same aisle).
5. Coral Park slot reservation plan explicitly handles Year 1 (11%) and Year 2 (18%)
   volume differentially; includes a mid-year re-slot.
6. At least one KPI in the post-cutover dashboard measures short-term pick-error
   regression (likely spike) with a defined threshold that would trigger rollback.
7. Capex reconciles to the $420K envelope (within $20K) with line items called out.

## Scope target
A v1 at ~15 minutes should contain: executive summary with the recommendation,
options-comparison table with the three options and 4-5 key metrics each, a zone-level
layout outline (A in aisles X-Y, B in aisles Z-W, Coral Park in aisle P), a preliminary
implementation sequence at phase level (even if not hour-by-hour), capex table summing
to $420K, and the financial case with rough payback. Hour-by-hour implementation, detailed
golden-zone spec, and rollback trigger definitions are iteration targets for v2/v3. By
v3, the labor savings math should reconcile, the Coral Park plan should have a named
mid-year re-slot, and the KPI dashboard should include rollback-trigger thresholds.
