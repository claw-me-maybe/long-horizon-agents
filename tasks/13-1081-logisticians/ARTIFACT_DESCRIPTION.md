# Regional DC Network Redesign Proposal — Parcelforge West (CA/AZ/NV), FY2027

## Occupation
- **SOC:** 13-1081
- **Title:** Logisticians

## Scenario
Parcelforge Logistics, a 3PL for direct-to-consumer apparel and beauty brands, has seen its West Region (CA/AZ/NV) next-day coverage drop from 94% to 81% as merchant demand consolidated in Los Angeles and San Francisco while its 2019-era footprint remains anchored in Reno and Fresno. The VP of Network Design, Theron Ugochukwu-Brand, needs a redesign proposal for the Q3 2026 capital committee on June 25, 2026 that will determine a two-year, $48M capex commitment. You will produce a distribution-network redesign that recommends where to add, keep, close, or resize facilities to restore 95%+ next-day at ≤4% cost-to-serve increase.

## Inputs

**Current network (4 facilities)**
| DC     | City       | Sqft    | Lease expiry | Throughput (pkg/day) | Auto? |
|--------|------------|---------|--------------|-----------------------|-------|
| PFW-01 | Reno, NV   | 220,000 | 2028-12-31   | 62,000                | Partial |
| PFW-02 | Fresno, CA | 310,000 | 2027-06-30   | 94,000                | Yes     |
| PFW-03 | Riverside, CA | 180,000 | 2029-03-31 | 41,000                | No      |
| PFW-04 | Phoenix, AZ | 260,000 | 2028-08-31  | 78,000                | Yes     |

**Demand (FY2025 actuals, FY2027F)**
- Total West pkg/day FY25: 275,000; FY27F: 378,000 (+37%)
- ZIP-3 demand mix shifted: LA metro +54%, SF Bay +28%, Phoenix +12%, Central Valley -3%, Reno -18%

**Representative ZIP-3 demand excerpt (fy27_forecast_zip3.csv)**
```
zip3, state, fy27_daily_pkg, fy25_daily_pkg, yoy
900, CA, 18200, 11800, +54%
902, CA, 14100, 9100, +55%
941, CA, 9800, 7100, +38%
950, CA, 5400, 3900, +38%
857, AZ, 7200, 6400, +13%
895, NV, 2300, 2800, -18%
```

**Carrier and transit inputs**
- UPS, FedEx, USPS, and regional (LSO, OnTrac) parcel injection zones by 3-digit ZIP
- OnTrac next-day ZIP list (California-focused); ground-service cutoffs by carrier
- Current average CPP (cost per package): $2.38; benchmark best-in-class West 3PL: $2.05

**Candidate sites screened by real-estate team**
- Ontario, CA (Inland Empire spec building, 410,000 sqft, ready 2027-Q1, $1.35/sqft/mo + TI)
- Stockton, CA (220,000 sqft existing, 2026-Q4 ready, $0.98/sqft/mo)
- North Las Vegas, NV (160,000 sqft build-to-suit, 2027-Q2)
- Tracy, CA (180,000 sqft existing, immediately available)

**Constraints**
- SLA: 95% next-day for LA, SF, San Diego, Phoenix metros
- Capex ceiling $48M (2026–2027); opex increase ≤4%
- Must honor union CBA in Fresno (Teamsters 856); headcount floor 420 there through 2028
- Environmental: Company commitment to 30% lower fleet-mile scope-1 emissions by 2028 vs 2024 baseline

## Artifact specification
Network-design decision document with supporting model. Required sections:
1. **Executive summary** — recommendation and headline numbers (nodes, capex, SLA, CPP)
2. **Situation** — demand shift, SLA gap, commercial risk
3. **Approach and methodology** — optimization framing (MIP/center-of-gravity/scenario modeling), data used, horizon
4. **Current network performance** — baseline service, cost, and utilization; named failure modes
5. **Demand projection** — growth by ZIP-3, concentration index, seasonality
6. **Candidate scenarios** — minimum three: (a) stay + automate, (b) add 1 node, (c) redesign with closure
7. **Scenario comparison** — service (% next-day), total landed cost, capex, risk, emissions, CBA impact
8. **Recommendation** — specific: open/close/resize/automate; phasing
9. **Implementation plan** — phases, critical path, decisions to be made now vs. later
10. **Risks and sensitivities** — demand-variation, labor, carrier-rate, real-estate, environmental
11. **Appendix** — data sources, assumptions table, model output summaries

Tone: quantitative, operator-ready, specific to US parcel logistics. Use logistics-standard metrics (CPP, click-to-door, linehaul, stem miles).

## Output format
Markdown document with embedded tables and a supporting methodology section that references a conceptual optimization model (no runnable code required). Target 2,400–3,200 words plus tables.

## Iteration targets
1. Scenario comparison often uses different dimensions per scenario; normalize to a single comparison matrix with identical columns.
2. v1 typically names a "recommended" scenario without stating which constraint is binding at the recommended answer — call out which constraint (capex, SLA, CBA, or emissions) would flip the decision if relaxed.
3. Demand projection often omits seasonal peak; add a peak-week (Cyber Week) stress case and state how the network handles it.
4. Emissions impact is often qualitative; convert to estimated ton-CO2e change with the calculation shown.
5. Automation decision for PFW-03 Riverside is often skipped; if closing, say when; if keeping, say why given LA-metro shift.
6. CBA/Fresno constraint is frequently absorbed implicitly; state explicitly how the recommendation maintains the 420-headcount floor.

## Success criteria
- The recommendation is supported by both quantitative scenario results and the binding-constraint analysis.
- Service, cost, capex, emissions, and CBA impact are all visible in a single comparison matrix.
- Real estate candidates are matched to the recommended scenario with timing and cost.
- The plan has a credible phasing that respects lease expiries and avoids simultaneous cutovers.
- Recommendation explicitly explains the LA-metro demand concentration and how it is addressed (Inland Empire vs. LA-basin consolidation).
- Sensitivity section identifies the 2–3 inputs whose realistic swing most changes the recommendation.

## Scope target
v1 at ~15 minutes should contain: exec summary with a preliminary recommendation, methodology section naming the modeling approach, baseline current-network performance table, demand-projection highlights including ZIP-3 shifts, three named scenarios with first-cut numbers, comparison matrix skeleton, recommendation with phasing outline. Roughly 1,400–1,800 words; detailed emissions math, Cyber Week stress case, and full sensitivity analysis are iteration work.
