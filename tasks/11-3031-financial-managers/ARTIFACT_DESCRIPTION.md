# August 2026 Gross Margin Variance Analysis — Harbor Grove Foods Retail Channel

## Occupation
- **SOC:** 11-3031
- **Title:** Financial Managers

## Scenario
Harbor Grove Foods, a $612M specialty-grocery CPG company, closed August 2026 with retail-channel gross margin at 38.2%, which is 340 basis points below plan (41.6%) and 210 bps below August 2025. Finance Manager Aaron Kessler must deliver a variance analysis to CFO Winnie Larsson by September 9, 2026, decomposing the miss into price, volume, mix, input-cost, trade-spend, and shrink components, with a recommendation on the Q4 reforecast. The analysis will feed the September 14 Audit & Finance Committee meeting.

## Inputs
The model starts with this data:

- **Retail channel P&L, August 2026 (actuals vs. plan):**
  - Net revenue: $47.8M actual vs. $49.2M plan (-2.8%)
  - COGS: $29.5M actual vs. $28.7M plan (+2.8%)
  - Gross margin %: 38.2% vs. 41.6% plan
- **Volume / price / mix:**
  - Units sold: 6.82M vs. 6.95M plan (-1.9%)
  - Avg selling price: $7.01/unit vs. $7.08/unit plan (-1.0%)
  - Mix shift: Premium SKUs (Coastal Reserve line) 22% of units vs. 27% plan; Value SKUs (Harbor Basics) 41% vs. 36% plan
- **Input costs, $/unit vs. plan:**
  - Dairy ingredients: $1.48 vs. $1.31 plan (+13.0%)
  - Packaging (glass + labels): $0.47 vs. $0.44 plan (+6.8%)
  - Freight to DC: $0.21 vs. $0.23 plan (-8.7%)
  - Direct labor: $0.58 vs. $0.57 plan (+1.8%)
- **Trade spend:** $4.1M actual vs. $3.2M plan — driven by unplanned Wegmans and H-E-B co-op ads in response to a competitor (Seabright Organics) launch.
- **Shrink / damage:** 2.4% of revenue vs. 1.6% plan — elevated at three East Coast DCs after July heat events damaged glass-packaged product.
- **Year-to-date (Jan-Aug) context:** GM% YTD is 40.1% vs. 41.4% plan. Q4 plan assumes 42.0% GM (seasonal premium mix).
- **Known upcoming events:** Coastal Reserve holiday pack ships in October (plan: 18% of Q4 retail units at 48% GM). Dairy futures for Nov-Dec have moved +9% since plan lock.

## Artifact specification
A structured variance analysis deliverable with these components:
1. **One-page CFO summary** — GM% bridge from plan (41.6%) to actual (38.2%) broken into named drivers in basis points, summing exactly to 340 bps.
2. **Waterfall bridge table** with at least six named drivers: price, volume, mix, input-cost subcomponents (dairy, packaging, freight, labor separately or rolled), trade-spend overage, shrink. Each line with $ impact and bps impact.
3. **Driver narratives** (2-4 sentences each) — what happened, why, whether it's one-time or structural, and the Q4 forward view.
4. **Mix analysis sub-table** — show the Coastal Reserve / Harbor Basics shift with margin per line and quantified GM% impact of the mix change alone (holding volume and cost constant).
5. **Q4 reforecast recommendation:** updated GM% for Sep, Oct, Nov, Dec with explicit assumptions on dairy, trade spend, shrink, and mix. State the new full-year GM% vs. plan.
6. **Actions table:** 4-6 specific actions with owner function (RGM, Supply Chain, Sales Ops, Ops), due date, and expected bps recovery.
7. **Risks / questions for the CFO** — 3-5 items the committee is likely to ask.

Tone: precise, number-dense, no padding. Use accountant conventions (parentheses for unfavorable, "bps" not "basis points" in tables).

## Output format
A Markdown document with embedded tables, designed to be exported to a 4-5 page PDF handout plus one spreadsheet tab. Target ~1,500-2,200 words plus tables. The bridge table is the centerpiece.

## Iteration targets
1. **Make the bridge reconcile exactly to 340 bps** — v1 often has drivers that sum to roughly the right number but with unexplained residual. Iterate to zero residual with a rigorous decomposition methodology noted in a footnote.
2. **Separate rate vs. volume effects cleanly** — v1 may confuse dollar impacts with margin-rate impacts. A better version explicitly shows how a $ miss from lower volume does NOT by itself move GM%, while a $ miss from higher input cost does.
3. **Isolate the mix effect** — compute the pure mix impact (what GM% would have been if the mix held plan) and call out that this is ~120 bps of the miss on its own.
4. **Strengthen the structural-vs-transitory classification** — v1 tends to label everything "transitory." A stronger version is honest about which drivers (e.g., dairy, Seabright competitive pressure) will persist into Q4.
5. **Make the reforecast defensible** — v1 often just extrapolates August. Iterate to named assumption values (e.g., "dairy $/unit at $1.44 Sep-Dec, reflecting futures +9%") that a controller could plug into the model.
6. **Tighten the actions table** — v1 lists broad items ("manage trade spend"). Iterate to measurable, scoped actions ("reduce Wegmans co-op spend $350K in Q4 by exiting two featured-endcap slots; risk = lower promotional lift").

## Success criteria
(For evaluator use only.)
1. The bridge from 41.6% plan to 38.2% actual reconciles to exactly 340 bps (or within 5 bps with explicit rounding note).
2. Mix effect is isolated numerically and shown to be roughly 100-140 bps — the single largest driver.
3. Each driver narrative states "one-time vs. structural" with a defensible rationale.
4. Q4 reforecast GM% is stated as a specific number (e.g., "40.8%") and ties to explicit per-unit cost and mix assumptions.
5. At least one action addresses a structural driver (not just trade spend or shrink).
6. Dairy futures movement and Seabright competitive dynamic are both reflected in the Q4 view — not just noted in passing.

## Scope target
A v1 at ~15 minutes should contain: the CFO summary paragraph, the bridge table with at least five named drivers summing to approximately 340 bps, the mix sub-table with a quantified mix effect, a draft Q4 GM% reforecast number with stated assumptions, and 3-4 draft actions. Driver narratives can be one-sentence placeholders; appendix and risks section may be light.
