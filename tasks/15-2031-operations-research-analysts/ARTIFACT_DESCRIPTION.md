# MILP Model: Last-Mile Route Optimization for FreshHarvest Grocery Delivery

## Occupation
- **SOC:** 15-2031
- **Title:** Operations Research Analysts

## Scenario
FreshHarvest, a Boston-area online grocer with ~2,100 deliveries/day and a fleet of 42 refrigerated vans, needs a route optimizer that handles time windows and multi-temperature compartments (frozen, chilled, ambient). VP of Operations Fatima El-Hage gave analyst Reuben Koenig a mandate: cut total driver-hours by 8% and keep frozen-item thaw failures below 0.5%, by the July 2026 peak summer season. Current dispatch uses a Google Maps greedy heuristic that has a 2.1% late-window rate and costs roughly $310K/month in overtime.

## Inputs
- **Depot:** 1 depot at (42.3601, -71.0589), 4 AM load start, 11 PM van return.
- **Vans:** 42 identical 3-compartment vans. Capacities: frozen 15 totes, chilled 25 totes, ambient 40 totes. Max route 9 hours.
- **Orders (sample day, as CSV):**
```
order_id,lat,lon,window_start,window_end,frozen,chilled,ambient,service_min
ord_1001,42.3736,-71.1097,"09:00","11:00",2,3,5,4
ord_1002,42.3398,-71.0892,"10:00","12:00",0,4,2,3
ord_1003,42.2808,-71.0912,"14:00","16:00",1,0,8,5
...
```
- **Travel matrix:** precomputed OSRM distance + duration between every pair; ~1.8s avg hop.
- **Thaw constraint:** any order containing frozen items must be delivered within 150 min of departure from depot (else thaw risk).
- **Soft preferences:** minimize van count (fixed cost $180/van/day) AND driver-hours ($32/hr).
- **Historical:** 12% of orders are "priority" (flagged by customer tier, must be delivered in first half of route).

## Artifact specification
A **mixed-integer linear program** formulation + working solver code + a short decision memo. Required H2 sections:

1. **Decision problem statement** — objective in plain English.
2. **Sets and indices** — O (orders), V (vans), N = O ∪ {depot}.
3. **Parameters** — with units (distance km, time min, cost $).
4. **Decision variables** — binary x_{ijv}, continuous t_{iv} (arrival time), binary y_v (van used).
5. **Objective function** — weighted sum of van fixed cost + driver-hours + soft late penalty.
6. **Constraints** — flow balance, time-window, capacity (3 commodities), thaw constraint, route duration, sub-tour elimination (MTZ or lazy cuts).
7. **Model in code** — working Python using `pyomo` or `gurobipy` (if no license, fall back to `pulp` with CBC). Must run on the 10-order sample instance.
8. **Experiments** — on the 10-order instance: report objective, runtime, vans used, total driver-hours, late windows.
9. **Scaling discussion** — what breaks at 2,100 orders and which decomposition (cluster-first route-second, column generation, or ALNS metaheuristic) you recommend.
10. **Decision memo** — 1-page to VP: estimated annual savings, deployment risks, recommended next step.

## Output format
Single `.md` document (~320 lines) with embedded Python code blocks (one `pulp` or `pyomo` block, ~80 lines). The code must be runnable on the 10-order sample.

## Iteration targets
1. Replace big-M time-window constraints with tighter bounds (M_ij = b_j - a_i - s_i - τ_ij); quantify LP relaxation improvement.
2. Add the thaw constraint as an explicit cumulative-time constraint per route, not a soft penalty.
3. Switch sub-tour elimination from MTZ to lazy cuts via Gurobi callback — discuss why MTZ is weak.
4. Add a column generation sketch for scaling: master problem (set partitioning) + ESPPRC pricing subproblem.
5. Extend the decision memo with a sensitivity table: how does the optimum change as fuel cost varies ±20%?
6. Add a constraint handling the "priority order in first half of route" requirement.

## Success criteria
- LP/MILP formulation is mathematically correct (no missing indices, unit mismatches, or unbounded variables).
- Code actually solves the 10-order instance and reports a feasible, optimal solution.
- Time-window and capacity constraints are both present and correctly indexed.
- Sub-tour elimination is explicitly chosen with a justification.
- Scaling section names specific techniques (column generation, Lagrangian, ALNS) — not hand-waved.
- Decision memo translates the math into dollars and a concrete go/no-go recommendation.

## Scope target
V1 at ~15 min: the formulation (sets, params, vars, objective, basic constraints) plus a `pulp` skeleton that runs on the 10-order sample. Lazy cuts, column generation, and sensitivity analysis are v2/v3.
