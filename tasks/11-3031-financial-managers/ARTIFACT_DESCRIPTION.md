# August 2026 Gross Margin Variance Analysis — Harbor Grove Foods Retail Channel

## Occupation
- **SOC:** 11-3031
- **Title:** Financial Managers

## Scenario
Harbor Grove Foods, a $612M specialty-grocery CPG company (flagship lines: Coastal Reserve
premium dairy, Harbor Basics value tier), closed August 2026 with retail-channel gross margin
at 38.2%, which is 340 basis points below plan (41.6%) and 210 bps below August 2025. Finance
Manager Aaron Kessler must deliver a variance analysis to CFO Winnie Larsson by September 9,
2026, decomposing the miss into price, volume, mix, input-cost, trade-spend, and shrink
components, with a recommendation on the Q4 reforecast. The analysis will feed the September
14 Audit & Finance Committee meeting and, depending on magnitude, a possible pre-announcement
call with sell-side analysts.

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
- Coastal Reserve holiday pack ships in October (plan: 18% of Q4 retail units at 48% GM)
- Dairy futures for Nov-Dec have moved +9% since plan lock
- Seabright Organics planned Q4 distribution expansion at Kroger (public, per trade press)
- Internal cost-out initiative (packaging redesign Phase 2) scheduled to deliver $0.03/unit
  savings starting Nov 1 — currently 50% confidence per Operations

## Artifact specification
A structured variance analysis deliverable with these components in order:

1. **One-page CFO summary** — GM% bridge from plan (41.6%) to actual (38.2%) broken into
   named drivers in basis points, summing exactly to 340 bps (with any residual called
   out). Clear statement of the Q4 reforecast recommendation and full-year implication.
2. **Waterfall bridge table** with at least six named drivers: price, volume, mix,
   input-cost subcomponents (dairy separately from other inputs), trade-spend overage,
   shrink/damage. Each line with $ impact, bps impact, and a one-word structural-vs-transitory
   classification.
3. **Driver narratives** (2-4 sentences each) — what happened, why, whether it's one-time
   or structural, and the Q4 forward view.
4. **Mix analysis sub-table** — show the Coastal Reserve / Harbor Basics shift with margin
   per line and quantified GM% impact of the mix change alone (holding volume and cost
   constant). Distinguish "planned mix" from "actual mix" arithmetically.
5. **Trade spend deep-dive** — a table of trade spend by customer vs. plan, with the
   competitive-reaction overspend called out, and the Q4 ask for incremental authorization
   or reduction.
6. **Q4 reforecast recommendation** — updated GM% for Sep, Oct, Nov, Dec with explicit
   assumptions on dairy ($/unit), trade spend, shrink, and mix. State the new full-year
   GM% vs. plan vs. guidance.
7. **Actions table** — 4-6 specific actions. Each with owner function (RGM, Supply Chain,
   Sales Ops, Ops), due date, and expected bps recovery. Total bps recovery in actions
   should reconcile to the gap between reforecast and plan for Q4.
8. **Risks and questions for the CFO** — 3-5 items the committee is likely to ask (e.g.,
   "Are we considering a price increase in Q1?" "Should we pull the Coastal Reserve holiday
   pack forward?")
9. **Appendix**: methodology notes on the bridge decomposition order (volume before mix,
   mix before rate), and reconciliation of the P&L totals.

Tone: precise, number-dense, no padding. Use accountant conventions (parentheses for
unfavorable, "bps" not "basis points" in tables, $K for thousands in supporting tables).

## Output format
A Markdown document with embedded tables, designed to be exported to a 4-5 page PDF handout
plus one spreadsheet tab. Target ~1,500-2,200 words plus tables. The bridge table is the
centerpiece; the reforecast summary and trade-spend sub-table are secondary anchors.

## Iteration targets
1. **Make the bridge reconcile exactly to 340 bps** — v1 often has drivers that sum to
   roughly the right number but with unexplained residual. Iterate to zero residual (or
   <5 bps residual with explicit rounding note) with a rigorous decomposition methodology
   noted in a footnote. Document the sequencing choice (volume-price-mix-rate).
2. **Separate rate vs. volume effects cleanly** — v1 may confuse dollar impacts with
   margin-rate impacts. A better version explicitly shows how a $ miss from lower volume
   does NOT by itself move GM%, while a $ miss from higher input cost does. The bridge
   should show "Volume" as dollar-only, not a bps line.
3. **Isolate the mix effect** — compute the pure mix impact (what GM% would have been if
   the mix held plan) and call out that this is ~120 bps of the miss on its own. The
   numbers support this: Premium fell from 27% to 22% (5 pp); Value rose from 36% to 41%
   (5 pp). With Coastal Reserve at ~52% GM and Harbor Basics at ~27% GM, that 5 pp shift
   alone costs ~(52-27)*5 = 125 bps on a weighted basis. A strong version does this math.
4. **Strengthen the structural-vs-transitory classification** — v1 tends to label
   everything "transitory." A stronger version is honest about which drivers (e.g., dairy
   cost, Seabright competitive pressure, consumer-mix shift down) will persist into Q4.
5. **Make the reforecast defensible** — v1 often just extrapolates August. Iterate to
   named assumption values (e.g., "dairy $/unit at $1.44 Sep-Dec, reflecting futures
   +9%, partially offset by packaging redesign of $0.03 starting Nov 1") that a
   controller could plug into the model without additional interpretation.
6. **Tighten the actions table** — v1 lists broad items ("manage trade spend"). Iterate
   to measurable, scoped actions ("reduce Wegmans co-op spend $350K in Q4 by exiting two
   featured-endcap slots; risk = lower promotional lift estimated at $600K revenue").

## Success criteria
(For evaluator use only.)
1. The bridge from 41.6% plan to 38.2% actual reconciles to exactly 340 bps (or within
   5 bps with explicit rounding note and methodology statement).
2. Mix effect is isolated numerically and shown to be roughly 100-140 bps — the single
   largest driver. The calculation is demonstrable from the given unit mix and GM% by line.
3. Each driver narrative states "one-time vs. structural" with a defensible rationale, and
   the list correctly classifies at least dairy cost and shrink/heat events (the shrink
   was weather-driven and likely non-recurring, but dairy cost will persist).
4. Q4 reforecast GM% is stated as a specific number (e.g., "40.8%") and ties to explicit
   per-unit cost and mix assumptions. Full-year GM% is re-stated against the 41.3%
   guidance number.
5. At least one action addresses a structural driver (not just trade spend or shrink).
   Typical strong actions: SKU rationalization in Value tier, price increase ask on
   Coastal Reserve, cost-pass-through negotiation with one dairy supplier.
6. Dairy futures movement (+9%) and Seabright competitive dynamic are both reflected in
   the Q4 view — not just noted in passing.
7. Trade spend deep-dive distinguishes reactive-to-competitor spend from baseline, and
   states a concrete Q4 trade-spend number.

## Scope target
A v1 at ~15 minutes should contain: the CFO summary paragraph, the bridge table with at
least five named drivers summing to approximately 340 bps, the mix sub-table with a
quantified mix effect, a draft Q4 GM% reforecast number with stated assumptions, and 3-4
draft actions. Driver narratives can be one-sentence placeholders; the appendix and the
CFO-question section may be light. By v2, the mix computation should be shown explicitly;
by v3, the actions table should reconcile the reforecast back to a defensible Q4 number
and the structural-vs-transitory classification should reflect honest assessment of
persistence.
