# Cell Layout Optimization & Line Balancing Study — Nordica Appliances Dishwasher Final-Assembly Line L3 (Cedar Falls Plant)

## Occupation
- **SOC:** 17-2112
- **Title:** Industrial Engineers

## Scenario
Nordica Appliances' Cedar Falls, IA plant is targeting a 22 % throughput lift on dishwasher
final-assembly line L3 (model DW-680 series) to support a national account win with a
big-box retailer. Shift volume must rise from 1,240 to 1,520 units/shift beginning
2026-07-06. IE lead Jordan Patel has three weeks to deliver a cell layout optimization and
line balancing study to plant manager Elise Hruska and ops VP Ken Onyemachi. The current
line is a 14-station straight-line configuration. The target state must achieve takt
without capital expenditure exceeding $85,000 and should retain the existing conveyor
system where feasible. The study will also be used by the corporate continuous-improvement
council to decide whether to replicate the approach at the Greenville, SC sister plant.

## Inputs

### Current-state measurements
- Observation basis: three shifts × 420 cycles per shift of stopwatch time study, with
  video cross-check; element times built up from MTM-UAS data cards.
- Gross shift: 480 min.
- Breaks (two 10-min): 20 min.
- Startup / cleanup: 10 min.
- Net available time per shift: **450 min**.
- Current output: 1,240 units/shift.
- Current takt time: 450 · 60 / 1,240 = **21.8 sec/unit**.
- Current cycle time at bottleneck (station S4): **29.4 sec**.
- Current line efficiency = Σtᵢ / (n · CTₘₐₓ) = 278.6 / (14 · 29.4) = **67.7 %**.

### Station mean times (observed, PF&D-adjusted, sec)
| Stn | Description                          | Obs Mean | σ   | Std Time |
|-----|--------------------------------------|---------:|----:|---------:|
| S1  | Tub stage & orient                   | 18.2     | 1.2 | 20.9     |
| S2  | Sump + motor assy mount              | 22.5     | 1.5 | 25.9     |
| S3  | Pump & hose install                  | 25.1     | 1.8 | 28.9     |
| S4  | Heating element & wiring             | 29.4     | 2.1 | 33.8     |
| S5  | Racks & rail sub-assy (parallel)     | 17.8     | 1.1 | 20.5     |
| S6  | Door hinge & gasket                  | 24.2     | 1.6 | 27.8     |
| S7  | Control board & harness route        | 19.6     | 1.3 | 22.5     |
| S8  | Kick panel & leveling feet           | 26.3     | 1.9 | 30.2     |
| S9  | Water inlet valve & drain hose       | 21.0     | 1.4 | 24.2     |
| S10 | Leak test (fixture-constrained)      | 28.7     | 1.0 | 33.0     |
| S11 | Cosmetic label & serial              | 15.4     | 0.8 | 17.7     |
| S12 | Function test (short cycle)          | 23.8     | 1.7 | 27.4     |
| S13 | Rework / touch-up buffer             | 19.1     | 2.4 | 22.0     |
| S14 | Pack & palletize                     | 27.5     | 1.8 | 31.6     |

### Target state
- New output: 1,520 units/shift.
- New takt: 450 · 60 / 1,520 = **17.8 sec/unit**.

### Precedence constraints
- S1 → S2 → S3 → S4.
- S5 (sub-assembly) is parallel after S2 and feeds S6.
- S6 → S7 → S8.
- S9 → S10 (leak test is fixture-constrained and cannot be split without capex).
- S11 → S12 → S13 → S14 (packaging ladder).

### Operational constraints
- Capex ceiling: **$85,000**.
- Conveyor pitch: 1.2 m, reconfigurable ±15 %.
- Operator headcount: 14 on-line, 3 off-line (sub-assy/relief).
- Skill matrix M-2024-11: only 8 of 14 operators certified on leak-test fixtures.
- Contribution margin per unit: $42 (finance confirmation 2026-02-11).
- Shifts per year: 240.
- Ergonomic ceiling: NIOSH Revised Lifting Equation RWL; no station may exceed
  13.6 kg lift without fixture aid.

### References
- Niebel's Methods, Standards, and Work Design, 14th ed. (PF&D allowance 15 % used).
- MTM-UAS and MOST data cards (2018 harmonization).
- NIOSH Publication 94-110 (Revised Lifting Equation).
- ANSI Z10.0-2019 (Occupational Health and Safety Management Systems).
- ISO 22400-2:2014 (KPIs for Manufacturing Operations Management).

### Known constraints and non-negotiables (from plant manager's 2026-02-04 email)
- No floor re-pour in production area; new equipment must reuse existing anchor grid.
- Union agreement (IUE-CWA Local 801) requires 40 hours of cross-training pay for any
  operator newly certified on leak test; budget for 12 hours per operator trained.
- The existing Rockwell Logix 5380 PLC controlling conveyor MCC is at 68 % memory use;
  any new I/O must not exceed an additional 8 % headroom.
- Corporate finance rule: payback must be under 18 months to avoid capex committee
  review.
- The function-test station (S12) cannot be split; the test script runs a 22-second
  sealed-circuit verification that is patented by Nordica (US 10,567,890).

### Baseline KPI snapshot (Q1 2026, from OEE dashboard)
- Availability: 91.3 % (downtime mostly unplanned changeovers on racks).
- Performance: 78.4 % (constrained by S4 and S10 bottlenecks).
- Quality (first-pass yield at EOL): 96.1 %.
- Overall OEE: 68.7 %.
- Target OEE after rebalancing: ≥ 78 %.

## Artifact specification
A process-improvement / line-balancing study memo with the following numbered sections:

1. **Executive summary** — before / after throughput, takt, line efficiency, capex, payback
   in months.
2. **Current-state analysis**
   - ASCII bar chart of station times (one bar per station scaled to CTₘₐₓ).
   - Spaghetti / material flow ASCII sketch of existing layout.
   - Time-study summary table: mean, σ, standard time per station.
   - Bottleneck identification with a Pareto of idle time by station.
3. **Future-state design**
   - Target takt calculation with formula.
   - Theoretical minimum stations: n_min = ⌈Σtᵢ / takt⌉.
   - Rebalanced assignments using a named heuristic (Ranked Positional Weights,
     Kilbridge-Wester, or COMSOAL) — show the ranked list and how tasks were assigned.
   - Proposed layout ASCII sketch (U-cell, parallel, or straight) with conveyor pitch
     and operator positions.
4. **Leak-test capacity decision** — S10 at 28.7 s > 17.8 s takt. Show arithmetic for
   parallel-station solution (2× leak-test fixtures) and the implied fixture cost
   from vendor quote (est. $32k for duplicate fixture plus controls).
5. **Capex bill** — line items with vendor references where possible (e.g., Dorner conveyor
   reconfig kit, Daifuku fixture, training hours at fully-burdened $78/hr).
   Total vs $85k ceiling with margin quoted.
6. **Payback** — incremental units per shift × margin × shifts/year, divided by capex,
   expressed in months.
7. **Risk & change management** — cross-training gap closure plan, ergonomic check via
   NIOSH RWL for S8 (kick-panel lift), ramp schedule (week 1 30 %, week 2 60 %, week 3
   100 %).
8. **Recommendation & sign-off block.**

## Output format
Single Markdown (.md) file, approximately 280–380 lines. ASCII bar charts and layout
sketches inside fenced code blocks. Markdown pipe-syntax tables for the time study,
balance, and capex bill. Formulas inline
(e.g., takt = T_available / D, `SI = sqrt(Σ(CTmax − tᵢ)²)`).

## Iteration targets
1. First pass often balances "on paper" without handling the fixed 28.7 s leak test —
   require an explicit parallel-station or process-redesign decision with the arithmetic
   shown.
2. Tighten the time study: add standard-time conversion = observed · rating · (1 + PF&D).
   Push for an explicit rating factor (e.g., Westinghouse or performance-rating) rather
   than only "mean observed."
3. Require line-efficiency calc before AND after, and compute the smoothness index
   SI = √Σ(CTₘₐₓ − tᵢ)².
4. Enforce a named balancing heuristic (RPW, Kilbridge-Wester, or COMSOAL) rather than
   ad-hoc reassignment.
5. Add a physical-constraint check: conveyor pitch × operator count × takt must match
   the available line-length envelope.
6. Push the ergonomic check into the memo — at least one NIOSH RWL or Snook/Ciriello
   callout for any station where a lift exceeds 13.6 kg.

## Success criteria
- Cites a recognized work-measurement system (MTM-UAS or MOST) and a PF&D convention.
- Takt, theoretical minimum stations, and balance efficiency are all computed with
  formulas visible.
- Bottleneck handling (leak test) is explicit and numeric, not hand-waved.
- Capex is itemized and compared to the $85,000 ceiling with margin quoted.
- Payback uses a named margin assumption and annualized savings with the arithmetic
  shown.
- ASCII bar chart correctly identifies the bottleneck station visually (bar longest at
  S4 or S10).

## Scope target
For a 15-minute v1: executive summary with before/after numbers, station-time ASCII bar
chart, takt and n_min calcs, a first-cut rebalance table using RPW, the leak-test
parallel-station decision, capex rough-out, and payback in months. A detailed MTM-UAS
element breakdown, a full NIOSH RWL assessment, and the ramp plan may be recorded as
TODOs.
