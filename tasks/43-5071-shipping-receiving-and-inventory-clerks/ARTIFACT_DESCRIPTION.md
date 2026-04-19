# Cycle Count Variance Investigation and Reconciliation Report — Foothill Industrial Supply, Zone D, Week of 04/13/2026

## Occupation
- **SOC:** 43-5071
- **Title:** Shipping, Receiving, and Inventory Clerks

## Scenario
Foothill Industrial Supply (an MRO distributor serving manufacturing in the Inland Empire, CA; 62,000 SKUs, one 110,000-sqft warehouse in Ontario, CA) performs weekly cycle counts. You are Rogelio Mendez, senior inventory clerk, 7 years with Foothill, reporting to Warehouse Manager Anita Broussard. Cycle count for Zone D (fasteners, fluids, abrasives; approximately 4,200 SKUs) completed April 16, 2026, revealed an unusually high absolute variance of 3.8% against the WMS (target: <1.0%). Anita needs a variance investigation and reconciliation report by Monday April 20, 2026, in advance of the operations review meeting that afternoon.

## Inputs

**Zone D cycle count summary (04/13-04/16):**
- Locations counted: 512 bin locations
- SKUs counted: 1,387 (sampled across Zone D; next batch 04/20-04/23)
- Absolute variance: 3.8% of unit count; 2.4% of $ value
- Total $ variance: $14,827 net short against WMS
- Prior week Zone D variance: 0.6% units / 0.3% $

**Top 12 variance lines:**

| SKU | Description | WMS qty | Counted | Variance | $ impact | Location | Notes from counters |
|---|---|---|---|---|---|---|---|
| FS-3845 | 3/8-16 x 1" hex cap grade 8 (100-pk) | 420 | 280 | -140 | -$1,120 | D-14-03 | Box crushed; found partial box opened |
| FS-3847 | 3/8-16 x 1.25" hex cap grade 8 (100-pk) | 180 | 320 | +140 | +$1,120 | D-14-04 | Adjacent bin to FS-3845 |
| LB-0221 | WD-40 12oz case/12 | 88 | 72 | -16 | -$512 | D-22-01 | — |
| LB-0231 | 3-in-1 oil 12oz case/12 | 22 | 22 | 0 | $0 | D-22-03 | — |
| AB-7700 | 3M Cubitron 4.5" grinding wheel (25-pk) | 45 | 44 | -1 | -$62 | D-31-05 | Damaged one on floor; logged |
| AB-7712 | 3M Cubitron 5" grinding wheel (25-pk) | 30 | 30 | 0 | $0 | D-31-05 | — |
| FS-6120 | 1/4-20 x 3/4" SHCS grade 8 (100-pk) | 600 | 420 | -180 | -$900 | D-10-02 | No visible shrink; shelf looks right |
| LB-0450 | Mobil DTE 25 hydraulic oil 5-gal | 24 | 24 | 0 | $0 | D-23-07 | — |
| FS-3999 | Assorted grade 8 fastener kit (each) | 50 | 34 | -16 | -$480 | D-15-11 | Kits opened; loose fasteners in same bin |
| AB-8800 | Norton flap disc 4.5" (10-pk) | 80 | 62 | -18 | -$540 | D-32-08 | — |
| LB-0800 | Loctite 242 blue threadlocker 50ml (case/10) | 36 | 36 | 0 | $0 | D-24-02 | — |
| FS-7050 | M10-1.5 x 30mm hex flange bolt (50-pk) | 140 | 140 | 0 | $0 | D-11-04 | — |

**Shipping/receiving activity since last Zone D count (04/06):**
- 47 inbound receipts posted (all confirmed via PO match)
- 112 outbound shipments picked from Zone D
- 4 customer returns received (all re-put-away)
- 2 internal transfers to satellite branch (Rancho Cucamonga)
- 1 known WMS outage 04/11 8:15-10:02 AM — 18 picks entered manually via paper batch; later keyed in. Re-key accuracy not yet audited.

**Other context:**
- New pick-path optimization went live 04/01. Pickers report occasional confusion between adjacent SKUs with similar IDs.
- Floor supervisor Alana noted on 04/14 that "FS-3845 and FS-3847 bins look mislabeled — labels are faded."
- No damaged-goods report filed for LB-0221 (-16 variance).
- No security incident reports for Zone D in past 90 days.
- Zone D is not a controlled-access area.

**Policy reference (Foothill Inventory Control Procedure, 2024-03):**
- Variance <1%: clerk-authorized WMS adjustment with supervisor sign-off.
- Variance 1-3%: mandatory recount within 48 hours before adjustment.
- Variance >3%: investigation report, recount, and manager + controller sign-off before adjustment.
- Any "swap" variances (equal-and-opposite adjacent SKUs) require root cause determination before either leg is adjusted.

## Artifact specification
Produce a variance investigation and reconciliation report with:

1. **Header** — zone, count dates, lead counter, report author, report date, distribution (Anita, Controller, Operations Review).

2. **Executive summary** — 3-5 sentences: variance magnitude, categorized causes, proposed adjustments, outstanding investigation.

3. **Variance breakdown by category**
   - "Swap" variances (FS-3845 ↔ FS-3847) — likely label/pick confusion
   - True shortage with explanation (FS-6120 no visible cause; AB-7700 damaged; FS-3999 kit opening)
   - True shortage without explanation yet
   - Within-tolerance zero-variance lines (for context)

4. **Root-cause analysis per variance cluster**
   - Cluster A: FS-3845/FS-3847 swap — evidence (adjacent bins, faded labels, pick-path change 04/01), proposed RCA, proposed action.
   - Cluster B: Bulk fastener shortages (FS-6120, FS-3999) — evidence, alternatives to consider (mis-picks during WMS outage 04/11 re-keying? theft? receiving error?).
   - Cluster C: Lubricants/abrasives shortages (LB-0221, AB-8800) — damage? shrinkage? unrecorded?
   - Cluster D: Damaged-known (AB-7700) — already accounted for.

5. **Reconciliation proposals**
   - Adjustments to post now (swap pair, documented damage)
   - Adjustments pending recount (FS-6120, FS-3999)
   - Adjustments pending further investigation (LB-0221, AB-8800)
   - Note which require manager + controller sign-off per policy (this whole report does, since zone variance >3%).

6. **Recount plan** — which SKUs/locations, by whom, by when, observed-by for integrity.

7. **Preventive actions**
   - Label replacement at D-14-03 / D-14-04 (and audit other faded labels)
   - Audit the 18 re-keyed picks from 04/11 outage
   - Coordinate with pick-path team on adjacent-SKU confusion
   - Shrinkage monitoring for LB-0221

8. **Data tables** — variance lines detail; $ impact summary; inbound/outbound activity summary for context.

Tone: factual, non-blaming, policy-referenced. Do not accuse; describe. Do not propose adjustments where policy requires recount first.

## Output format
Single Markdown file with tables, ~3 pages rendered (200-320 lines source).

## Iteration targets
1. **Correctly classify the swap** — v1 may treat FS-3845 -140 and FS-3847 +140 as independent; v2 sees the adjacent-bin, faded-label, pick-path-change pattern and handles them as one swap event with a single RCA.
2. **Respect the policy gates** — v1 may propose direct adjustments; v2 correctly blocks adjustments on the 1-3% and >3% variance categories until recount and sign-off are obtained.
3. **Connect the WMS outage to the bulk-fastener variance** — v1 may not notice; v2 proposes an audit of the 18 re-keyed picks before concluding shrinkage.
4. **Don't over-conclude on LB-0221 / AB-8800** — v1 may guess "shrinkage"; v2 leaves these in the "pending investigation" bucket with a defined investigation scope.
5. **Quantify the $ impact carefully** — swap pair nets to ~$0; true net shortage is substantially less than the headline $14,827; break out swap vs true net in the summary.
6. **Tie preventive actions to evidence** — each preventive action cites the specific finding that motivates it, not a generic "improve process."

## Success criteria
- Swap pair (FS-3845/FS-3847) is correctly classified and its net-zero $ impact surfaced.
- No adjustments are proposed without the policy-required recount/sign-off for lines that require it.
- WMS outage 04/11 is connected to the investigation plan for bulk-fastener shortages.
- Preventive actions are specific and traceable to findings.
- Report clearly distinguishes what Rogelio can post now vs. what needs Anita + Controller.
- Net vs. gross $ variance is accurately stated.

## Scope target
A v1 at ~15 minutes should contain: header, exec summary, variance breakdown with clusters A-D identified, RCA for at least clusters A and B, a reconciliation proposal distinguishing post-now vs. pending, a recount plan, and at least 3 preventive actions. Tightening policy-gate language, refining the net-vs-gross framing, and adding the 04/11 re-key audit in detail belong to iteration.

## Example of v1 failure modes
- Summing the absolute $ variance (adding the swap pair at $1,120 + $1,120 = $2,240) and reporting it as net shortage, inflating the loss.
- Proposing immediate WMS adjustments to the swap pair without the label replacement and bin-label audit, which will let the same variance recur next cycle.
- Treating AB-7700 (damaged, 1 unit, already logged) as unresolved; it has a known cause and a damage log entry.
- Missing the temporal connection between the 04/11 WMS outage and the bulk-fastener variance (FS-6120, FS-3999); these were receive/pick-heavy SKUs during the outage window.
- Recommending a shrinkage investigation on LB-0221 without first ruling out a receiving error or a breakage-not-logged event.
- Using "theft" as an RCA conclusion without any supporting evidence (no security incident, camera access, or pattern data); this is defamatory and premature.
- Proposing adjustments before supervisor sign-off when policy requires manager + controller for >3% variance.
- Failing to name the counter team (lead, counter, observer) in a report that may be audited.

## Common pitfalls to avoid
- Do not adjust the WMS for any cluster until its recount and required sign-offs are on file; write the proposal with adjustment dates conditional on policy-compliant approval.
- Do not propose "add cameras to Zone D" as a preventive action; it's outside inventory-clerk scope and will be declined without facility-level justification.
- Do not combine the swap-pair and the bulk-fastener clusters into a single RCA; their evidence and likely causes are distinct.
- Do not quote rough counts for the kit SKU (FS-3999) without attempting a careful count of loose fasteners in the bin (kit-opening implies loose inventory that should be counted against the kit's component SKUs, not against FS-3999 itself).
- Do not overlook the 4 customer returns re-put-away — one of those could be the source of the LB-0221 shortage if a return was put to a wrong bin.

## Evaluator notes (context for scoring, not for the model)
- The 43-5071 role is strongly iteration-worthy here because the core failure mode — conflating a swap with two independent shortages, or adjusting WMS before required sign-off — is both common and consequential. A strong v2 disentangles the clusters, gates adjustments behind the correct policy thresholds, and connects the bulk-fastener variance to the 04/11 re-key audit.
- Foothill Industrial Supply, the specific SKUs, and all named individuals are fictional. The variance categories (swap, damage, shortage-with-cause, shortage-unexplained) are standard in cycle-count practice. The 1%/1-3%/>3% policy tier structure is typical.
- Iteration feedback should focus on: (a) correctly netting the swap ($0 impact) from the gross variance; (b) respecting the policy gates; (c) connecting WMS outage to investigation; (d) distinguishing evidence-based vs. speculative RCA.

## Arithmetic checks the model should perform
- Swap pair: FS-3845 (-140 × $8.00 = -$1,120) + FS-3847 (+140 × $8.00 = +$1,120) = $0 net. Unit price assumed equal across the pair (same grade, adjacent sizes); verify if needed.
- Net $ variance after swap: $14,827 − net effect of the swap pair = $14,827 (since swap is $0 net).
- True unexplained: $14,827 minus cluster C damage, minus known cluster D damage, leaves the FS-6120 and FS-3999 bulk fastener cluster and LB-0221/AB-8800 as the investigation target.
- Recount scope: the 1,387 SKUs counted this week + re-count of the specific variance lines; Zone D batch 2 (next 1,400 SKUs) is scheduled 04/20-04/23.

## What distinguishes this from a simple cycle count report
- Presence of a swap pattern that requires cross-SKU reasoning.
- Intersection with a WMS outage and re-keyed data that requires source-data audit.
- Mix of damaged/known-cause, damaged/unknown-cause, swap, and clean shortages in a single cycle.
- Policy tiers that gate adjustments behind manager + controller approval at this variance magnitude.
- Preventive action space that includes labels, pick-path configuration, scanner audit, and shrinkage monitoring — multiple independent mechanisms.

## Final sanity checks before submitting to Anita
- Swap pair net-$0 impact surfaced in the exec summary and the reconciliation.
- No WMS adjustments proposed without policy-compliant sign-off path.
- WMS outage 04/11 re-key audit included in the investigation plan.
- Preventive actions tied to specific findings, not generic process improvements.
- Counter team (lead, counter, observer) named in the report.
