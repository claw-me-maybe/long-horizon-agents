# Warehouse Slotting & Aisle Redesign Proposal — Pallas Lighting, Memphis DC

## Occupation
- **SOC:** 11-3071
- **Title:** Transportation, Storage, and Distribution Managers

## Scenario
Pallas Lighting, a $220M commercial and architectural lighting wholesaler, operates a 380,000 sq-ft distribution center in Memphis, TN serving 2,800 B2B customers across 28 states. DC Manager Rafael Mendoza must present a slotting + aisle redesign proposal to the VP of Supply Chain, Ines Verhoeven, by October 30, 2026, for a January 12-16, 2027 implementation window (over the MLK weekend shutdown). The business goals: reduce pick travel per line by 18%, cut mis-picks from 0.28% to <0.15%, and free space to absorb the 2027 SKU assortment expansion (+1,450 SKUs from the newly acquired Coral Park Exterior line) without adding square footage.

## Inputs
The model starts with:

- **Facility:**
  - 380,000 sq-ft, clear height 32 ft, 18 aisles currently at 9-ft aisle width, selective pallet racking 4 beams high for reserve, pick modules for case pick.
  - Monthly outbound: 41,000 orders, avg 14 lines/order, avg pick travel 0.44 miles/order (Locus WMS data).
  - Picker headcount: 52 associates across 2 shifts; avg picks/hour 98.
- **SKU profile:**
  - Total active SKUs: 9,820
  - Velocity distribution: A items (top 20%): 1,964 SKUs = 78% of line volume; B items (next 30%): 2,946 SKUs = 17%; C items: 4,910 SKUs = 5%.
  - Current slotting: legacy alphabetical by mfg + SKU number. A items are distributed across all 18 aisles.
  - Slot occupancy: 86% of forward-pick slots; 22% over-sized slots (oversized for current velocity).
- **Incoming assortment (Coral Park Exterior, acquired June 2026):**
  - 1,450 SKUs; ~68% outdoor fixtures (larger cube, heavier per line).
  - Projected to be ~11% of line volume in Year 1, 18% in Year 2.
  - Current temp storage in Aisles 17-18 (non-optimal; 0.52 mi avg travel).
- **Current pain points:**
  - Congestion in Aisles 3-5 (current A items) peak 10AM-1PM.
  - Aisles 17-18 (slow movers + Coral Park temp) have pickers idling during wave flushes.
  - Mis-pick rate 0.28% with 62% of mis-picks attributed to look-alike SKU pairs (similar PN, different voltage or finish) stored adjacent.
  - 8 lift-truck near-misses YTD in aisle 9-ft width with heavy Coral Park traffic.
- **Technology & constraints:**
  - Locus WMS (pick-path optimization available but not tuned to slot velocity).
  - Capex envelope: $420K (racking mods, signage, conveyor adjustments). No new square footage.
  - Implementation must complete in 72 hours (Fri evening Jan 12 - Mon evening Jan 15).
- **Measured data on alternatives (from simulation vendor Solvexia, done August 2026):**
  - Velocity-based slotting (ABC pure): -22% travel, +$380K capex.
  - Family-grouped slotting (ABC within product family): -14% travel, +$260K capex.
  - Hybrid (golden zone for A items, family grouping for B/C): -19% travel, +$340K capex.

## Artifact specification
A warehouse redesign proposal with the following structure:
1. **Executive summary** — current state (travel, mis-pick, throughput, congestion), proposed state, recommendation, capex, implementation window.
2. **Current state assessment** — data-driven: aisle heat map (described or tabular), velocity profile, slot occupancy, mis-pick root-cause breakdown.
3. **Design options comparison** — 3 options (velocity-pure, family-grouped, hybrid) with travel reduction, capex, mis-pick impact, space liberation, disruption risk, and scalability to Coral Park volume growth.
4. **Recommendation & rationale** — pick one option, explain trade-offs.
5. **New layout specification** — zone by zone: which aisles hold A / B / C; golden-zone definition (height band); where Coral Park lives; how oversized slots are re-profiled to fit small-velocity SKUs.
6. **Slotting rules & governance** — criteria for a SKU to enter the A zone, re-slotting cadence (quarterly? monthly?), exceptions process, look-alike-SKU separation policy.
7. **Implementation plan** — 72-hour Gantt with hour-by-hour sequencing Fri-Mon. Crew structure. Contingency if running behind at each checkpoint.
8. **Financial case** — $420K capex vs. travel-reduction labor savings (calculate labor $ saved per year), mis-pick cost avoidance, throughput capacity for Coral Park, ROI / payback.
9. **Risk register** — 5-7 risks (pick-error spike post-cutover, training, Coral Park forecast miss, congestion if A zone too concentrated) with mitigation.
10. **KPI dashboard** — the 4-6 metrics tracked daily for the first 30 days post-implementation.

Tone: operations-rigorous, quantitative. Should be directly usable to brief the DC associates, the VP, and the CFO.

## Output format
Markdown document with embedded tables, 6-9 pages. Include a schematic layout description (ASCII or tabular representation of aisle zones) — no image required but the zoning must be specified in enough detail that a slotting planner can implement.

## Iteration targets
1. **Lock the recommendation to the data** — v1 often picks the hybrid option without showing the arithmetic. Iterate to a quantitative trade-off: hybrid gives 19% vs. pure's 22% travel reduction but at $40K lower capex AND reduces mis-pick by more due to family grouping.
2. **Improve the 72-hour implementation plan** — v1 tends to list phases. Iterate to hour-by-hour: "Fri 7pm - aisle freeze, Sat 2am - start Aisle 5 re-profile, Sat 8am - first re-slot wave of top 200 A SKUs..." with named crews and go/no-go checkpoints.
3. **Quantify labor savings honestly** — v1 claims big $ but handwaves the calculation. Iterate to: (# orders × lines × travel reduction × $ per labor hour / pick rate) = explicit labor savings.
4. **Address the mis-pick driver specifically** — v1 may say "re-slot to reduce mis-picks." Iterate to: of 62% of mis-picks from look-alike pairs, the new layout separates X named pairs by at least Y aisles; expected mis-pick reduction 0.09 pp based on this mechanism alone.
5. **Plan for Coral Park growth Year 2** — v1 sizes for Year 1. Iterate to explicit slot reservation/expansion strategy that absorbs Year 2 volume without another redesign.
6. **Golden-zone definition must be actionable** — v1 says "ergonomic height." Iterate to: "slots between 18"-60" height on aisles 3-8, beam level B, with 12-18" pick-face width." Planner should be able to execute without further decisions.

## Success criteria
(For evaluator use only.)
1. Recommendation is stated explicitly (one of the three options), with trade-offs vs. the other two options named in 2-3 sentences each.
2. Labor savings calculation reconciles: (travel reduction % × current labor cost) with stated labor rate and hours baseline.
3. Implementation plan has hour-by-hour or quarter-day granularity for the 72-hour window, not just phase-level.
4. Slotting rules include a specific mis-pick/look-alike-SKU separation policy (e.g., no two SKUs differing only by voltage within same aisle).
5. Coral Park slot reservation plan explicitly handles Year 1 (11%) and Year 2 (18%) volume differentially.
6. At least one KPI in the post-cutover dashboard measures short-term pick-error regression (likely spike) with a defined threshold that would trigger rollback.

## Scope target
A v1 at ~15 minutes should contain: executive summary with the recommendation, options-comparison table with the three options and their three key metrics, a zone-level layout outline (A in aisles X-Y, B in aisles Z-W, Coral Park in aisle P), a preliminary implementation sequence at phase level, capex table summing to $420K, and the financial case with rough payback. Hour-by-hour implementation and detailed golden-zone spec are iteration targets.
