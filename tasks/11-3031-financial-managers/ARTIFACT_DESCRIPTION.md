# August 2026 Gross Margin Variance Analysis — Harbor Grove Foods Retail Channel

## Occupation
- **SOC:** 11-3031
- **Title:** Financial Managers

## Scenario
Harbor Grove Foods, a $612M specialty-grocery CPG company (flagship lines: Coastal Reserve
premium dairy, Harbor Basics value tier), closed August 2026 with retail-channel gross margin
at 38.2%, which is 340 basis points below plan (41.6%) and 210 bps below August 2025. Finance
Manager Aaron Kessler must deliver a concise variance memo to the VP of Finance by September 9,
2026, explain the August miss, and give one Q4 reforecast recommendation. Keep this at a
finance-manager level: actionable, numerically grounded, and suitable for a first-pass review,
not a board deck, controller package, or investor-relations note.

## Inputs
The model starts with this data:

### Retail channel P&L, August 2026 (actuals vs. plan)
- Net revenue: $47.8M actual vs. $49.2M plan (-2.8%)
- COGS: $29.5M actual vs. $28.7M plan (+2.8%)
- Gross margin %: 38.2% vs. 41.6% plan (-340 bps)
- Gross profit $: $18.3M actual vs. $20.5M plan (-$2.2M)

### Volume / price / mix
- Units sold: 6.82M vs. 6.95M plan (-1.9%)
- Avg selling price: $7.01/unit vs. $7.08/unit plan (-1.0%)
- Mix shift: Premium SKUs (Coastal Reserve line) 22% of units vs. 27% plan; Value SKUs
  (Harbor Basics) 41% vs. 36% plan; mid-tier (Harbor Select) held at 37%
- Coastal Reserve GM%: 52.4% (actual), 53.1% (plan)
- Harbor Select GM%: 41.8% (actual), 42.3% (plan)
- Harbor Basics GM%: 27.2% (actual), 28.5% (plan)

### Input costs, $/unit vs. plan
- Dairy ingredients: $1.48 vs. $1.31 plan (+13.0%)
- Packaging (glass + labels): $0.47 vs. $0.44 plan (+6.8%)
- Freight to DC: $0.21 vs. $0.23 plan (-8.7%)
- Direct labor: $0.58 vs. $0.57 plan (+1.8%)
- Total input cost per unit: $2.74 vs. $2.55 plan (+7.5%)

### Trade spend
- Actual: $4.1M vs. $3.2M plan — driven by unplanned Wegmans and H-E-B co-op ads in response
  to a competitor (Seabright Organics) launch. Breakdown: Wegmans $1.3M (plan $0.9M), H-E-B
  $0.8M (plan $0.4M), everyday low price allowances $1.2M (plan $1.1M), slotting $0.8M
  (plan $0.8M).
- Trade spend as % of gross sales: 7.9% vs. 6.1% plan.

### Shrink / damage
- 2.4% of revenue vs. 1.6% plan — elevated at three East Coast DCs (Allentown, Richmond,
  Savannah) after July heat events damaged glass-packaged product in transit.
- Shrink $: $1.15M actual vs. $0.79M plan.

### Year-to-date (Jan-Aug) context
- GM% YTD: 40.1% vs. 41.4% plan (130 bps below)
- Revenue YTD: $392M vs. $402M plan
- Q4 plan assumes 42.0% GM (seasonal premium mix)
- Full-year guidance to the Board: 41.3% GM, $620M revenue

### Known upcoming events
- Coastal Reserve holiday pack ships in October.
- Dairy futures for Nov-Dec have moved +9% since plan lock.
- Seabright Organics planned Q4 distribution expansion at Kroger (public, per trade press).
- Internal cost-out initiative (packaging redesign Phase 2) is scheduled to begin in November.

## Artifact specification
A structured variance analysis deliverable with these components in order:

1. **One-page memo** — summarize the August miss, identify the top drivers, and state a
   single Q4 recommendation. Keep the memo tight enough for a 15-minute first pass.
2. **Bridge table** — show the reconciliation from plan GM% (41.6%) to actual GM% (38.2%)
   with named drivers and a clear arithmetic trail.
3. **Compact Q4 reforecast box** — one quarterly reforecast, not month-by-month detail.
   Use the known Q4 events and bounded assumptions to produce one working case the reviewer
   can check.
4. **Action list** — 3-4 specific actions with owner function and expected bps recovery.
   Keep the actions operational and realistic for a finance manager to coordinate.
5. **Short notes on risks / open questions** — only the items needed to pressure-test the
   recommendation; defer deep customer analysis to later iterations.

Accounting boundary:
- Treat trade spend as a contra-revenue item below gross sales, not as a COGS line.
- In the bridge, trade spend may be shown with both dollars and bps because it changes GM%.
- Volume is dollar-only in the bridge. Do not assign a bps effect to volume; it changes
  the revenue base, not the margin rate bridge.
- Keep the bridge order consistent with that rule: volume in the revenue/dollar section,
  then price, mix, input cost, trade spend, and shrink in the GM% bridge.

Tone: precise, number-dense, no padding. Use accountant conventions (parentheses for
unfavorable, "bps" not "basis points" in tables, $K for thousands in supporting tables).

## Output format
A Markdown document with embedded tables, designed to be exported to a 2-3 page PDF handout
plus one spreadsheet tab. Target ~800-1,200 words plus tables. The bridge table is the
centerpiece; the memo and Q4 reforecast box are secondary anchors.

## Iteration targets
1. **v1: one-page memo + bridge only** — prove the August bridge and give one Q4
   recommendation. No customer appendix, no month-by-month schedule, no long narrative.
2. **v2: add the compact Q4 box and actions** — include a single-quarter reforecast with
   bounded inputs, plus 3-4 actions that a finance manager can actually track.
3. **v3: add sensitivity and deeper diagnosis** — if needed, expand to customer-level
   trade-spend analysis, alternative Q4 cases, and a fuller risk discussion.
4. **Across all versions: keep the bridge rules consistent** — trade spend stays a
   contra-revenue driver, volume stays dollar-only, and every rate driver shown in the bridge
   must tie back to the same accounting boundary.

## Success criteria
(For evaluator use only.)
1. The bridge from 41.6% plan to 38.2% actual reconciles exactly to 340 bps, or includes
   a small, explicit rounding note that explains any residual.
2. Trade spend is treated consistently as contra-revenue, and the bridge reflects that rule
   without mixing it into COGS.
3. Volume is shown as dollar-only, while the rate bridge uses only drivers that affect GM%.
4. The memo states one concrete Q4 recommendation and one checkable Q4 GM% case tied to
   explicit assumptions from the input set.
5. The action list includes at least one structural lever, not just a temporary spend cut
   or a weather-related cleanup item.
6. The answer does not reveal a specific mix conclusion or hard-code example assumptions
   that are not present in the input set.
7. The deliverable stays compact enough for a first-pass finance-manager review and does not
   expand into month-by-month forecasting or deep customer-by-customer annexes.

## Scope target
A v1 at ~15 minutes should contain: the one-page memo, the bridge table with at least five
named drivers summing to approximately 340 bps, and a single Q4 recommendation with bounded
assumptions. By v2, add the compact Q4 box and actions. By v3, expand only if needed into
alternative cases, deeper customer analysis, or more detailed persistence commentary.
