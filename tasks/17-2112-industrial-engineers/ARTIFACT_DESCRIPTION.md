# Cell Layout Optimization & Line Balancing Study — Nordica Appliances Dishwasher Final-Assembly Line L3 (Cedar Falls Plant)

## Occupation
- **SOC:** 17-2112
- **Title:** Industrial Engineers

## Scenario
Nordica Appliances' Cedar Falls, IA plant is targeting a 22% throughput lift on dishwasher line L3 (model DW-680 series) to support a national account win with a big-box retailer; volume goes from 1,240 to 1,520 units/shift beginning 2026-07-06. IE lead Jordan Patel has been given 3 weeks to produce a cell layout optimization and line balancing study for plant manager Elise Hruska and ops VP Ken Onyemachi. Current line is a 14-station straight-line configuration; the target state must hit takt without capex over $85k and retain the existing conveyor system if feasible.

## Inputs
- **Current state (observed over 3 shifts, 420 cycles each, stopwatch time study per MTM-UAS cross-checked with video):**
  - Available time/shift: 450 min (480 min gross − 20 min breaks − 10 min startup/cleanup).
  - Current output: 1,240 units/shift → current takt = 21.8 sec/unit. Current cycle time (CT) at bottleneck station 4 = 29.4 sec.
  - Line efficiency = Σti / (n · CTmax) = 278.6 s / (14 · 29.4 s) = 67.7%.
- **Station times (observed mean, sec):** S1 18.2 | S2 22.5 | S3 25.1 | S4 29.4 | S5 17.8 | S6 24.2 | S7 19.6 | S8 26.3 | S9 21.0 | S10 28.7 | S11 15.4 | S12 23.8 | S13 19.1 | S14 27.5.
- **Target state:** Output 1,520 units/shift → target takt = 450·60 / 1,520 = 17.8 sec/unit.
- **Precedence constraints:** S1→S2→S3→S4; S5 parallel after S2 (sub-assembly); S6→S7→S8; S9→S10 (leak test, fixed 28.7 s, cannot split); S11→S12→S13→S14 (packaging).
- **Constraints:** Conveyor pitch reconfigurable ±15% from current 1.2 m; $85k capex ceiling; operators cross-trained per skill matrix M-2024-11 (8 of 14 qualified for leak test).
- **Standards:** Use MTM-UAS or MOST for rebalanced element times; cite Niebel's Methods, Standards, and Work Design (14th ed.) for PF&D allowances (15% standard).

## Artifact specification
Process improvement / line balancing study memo with:
1. **Executive summary** — before/after throughput, takt, efficiency, capex, payback.
2. **Current-state analysis**
   - Station-time bar chart in ASCII (one bar per station scaled to max CT).
   - Spaghetti/material flow ASCII sketch of existing layout.
   - Time study summary table with mean, σ, and PF&D-adjusted standard time per station.
   - Bottleneck identification with Pareto of idle time by station.
3. **Future-state design**
   - Target takt calc with formula.
   - Theoretical minimum stations: n_min = ⌈Σti / takt⌉.
   - Proposed rebalanced assignments (RPW or similar heuristic cited) table: station → elements → new time.
   - Proposed layout ASCII sketch (U-cell, parallel, or straight) with conveyor pitch and operator positions.
4. **Capacity/constraint check** — leak test S10 fixed at 28.7 s > target takt; show parallel-station decision (2× leak-test stations) and required fixture cost.
5. **Capex bill** — line items (fixture, conveyor mod, operator training, jigs) with vendor references where possible; total vs $85k ceiling.
6. **Payback** — contribution margin per unit ($42 assumed), incremental units/shift × shifts/yr (240) = annualized savings; payback in months.
7. **Risk & change management** — cross-training gap closure, ergonomics (NIOSH lift eq. check for S8 reach), ramp schedule.
8. **Recommendation & sign-off block.**

## Output format
Single Markdown (.md) file, ~280–380 lines. ASCII bar charts and layout sketches in fenced code blocks. Markdown tables for time study, balance, capex.

## Iteration targets
1. First pass often balances "on paper" without handling the fixed 28.7 s leak test — require a parallel-station or process-redesign decision with explicit math.
2. Tighten time study: add standard-time conversion = observed × rating × (1 + PF&D). Push for a rating factor (e.g., Westinghouse or NIOSH) not just mean observed.
3. Require line-efficiency calc before AND after, and smoothness index (SI = √Σ(CTmax − ti)²).
4. Enforce a named balancing heuristic (Ranked Positional Weights, Kilbridge-Wester, or COMSOAL) rather than ad-hoc reassignment.
5. Add a constraint check: conveyor pitch × operator count × takt must equal line length envelope (verify fits footprint).
6. Push ergonomic check into the memo — at least one NIOSH RWL or Snook/Ciriello call-out for any station exceeding 13.6 kg lifts.

## Success criteria
- Cites a recognized work measurement system (MTM-UAS, MOST) and PF&D convention.
- Takt, theoretical min stations, and balance efficiency all computed with formulas visible.
- Bottleneck handling (leak test) is explicit and numeric, not hand-waved.
- Capex is itemized and compared to the $85k ceiling with margin shown.
- Payback includes a named margin assumption and annualized savings.
- ASCII bar chart correctly identifies the bottleneck station visually.

## Scope target
For a 15-minute v1: exec summary with before/after numbers, station-time ASCII bar chart, takt & n_min calcs, a first-cut rebalance table using RPW, the leak-test parallel-station decision, capex rough-out, and payback in months. Detailed MTM-UAS element breakdown, full ergonomic assessment, and ramp plan can be TODOs.
