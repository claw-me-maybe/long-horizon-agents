# Stormwater Detention Pond Sizing Calculation Package — Maple Ridge Commons Redevelopment (Permit Submittal to City of Asheville)

## Occupation
- **SOC:** 17-2051
- **Title:** Civil Engineers

## Scenario
Ridgeline Civil Group is the engineer of record for Maple Ridge Commons, a 12.4-acre infill mixed-use redevelopment in Asheville, NC (parcel 9728-55-3341). Design lead Tomás Alvarez must submit the stormwater management calculation package to the City of Asheville Stormwater Services by 2026-05-04 to support a Type III site plan review. The city requires compliance with the Asheville UDO Article 7 and the NCDEQ Stormwater Design Manual (July 2023 update). Receiving water is an unnamed tributary to Ross Creek (impaired stream), triggering enhanced nutrient controls.

## Inputs
- **Site:** 12.4 ac gross, pre-development 82% woods (HSG B/C), 18% meadow. Post-development 4.1 ac building, 5.9 ac pavement, 2.4 ac landscaped/pervious.
- **Soils:** NRCS web soil survey — Evard-Cowee complex (HSG B, CN woods=55, CN meadow=58, CN impervious=98, CN lawn good=61).
- **Rainfall (NOAA Atlas 14, Point Precip, Buncombe Co, 24-hr Type II):**
  - 1-yr: 2.91 in, 2-yr: 3.46 in, 10-yr: 5.02 in, 25-yr: 6.03 in, 100-yr: 8.14 in.
- **Governing criteria (Asheville UDO + NCDEQ):**
  - Peak control: post ≤ pre for 1-, 10-, 25-yr storms.
  - Water-quality volume: 1.0 in runoff from impervious (SCM required — proposed wet pond).
  - Nutrient: 30% TN, 30% TP removal credits (wet pond meets).
  - Discharge to stable outlet with ≤ 2 fps non-erosive velocity.
- **Proposed SCM:** Wet detention pond, primary spillway = riser/barrel, emergency spillway = broad-crested weir, per NCDEQ SCM Manual Chapter C-2.
- **Geotech:** SHWT at elev 2,194.0 ft; pond bottom must be ≥ 1.0 ft above SHWT.
- **Topography:** Pond site footprint available = 0.85 ac @ avg existing elev 2,198.5 ft.

## Artifact specification
Stormwater calculation package memo/narrative with:
1. **Cover sheet** — project, PE seal block (placeholder), reviewer list, date, revision.
2. **Project description & regulatory basis** — cite UDO §7-12 and NCDEQ Manual sections used.
3. **Pre/post development hydrologic analysis** — land use tables with CN-weighted values, Tc calcs (SCS lag method or TR-55 segmental), peak discharges via TR-55 graphical or unit hydrograph.
4. **Peak discharge summary table** — Qpre vs Qpost for 1/2/10/25/100-yr, with and without SCM.
5. **Water-quality volume (WQv) calc** — per NCDEQ §3.4: WQv = (1.0 in)(Rv)(A), Rv = 0.05 + 0.9·i.
6. **Wet pond sizing** — permanent pool volume, forebay (20% of PP), surface area at permanent pool (SA/DA method per NCDEQ Table C-2.1 at 90% TSS removal), stage-storage curve.
7. **Routing** — inflow vs outflow hydrograph for 10-yr and 100-yr, riser & barrel stage-discharge, emergency spillway check for 100-yr + 1 ft freeboard.
8. **Outlet protection** — riprap apron sized per NCDEQ D-50, exit velocity ≤ 2 fps.
9. **SCM geometry** — ASCII profile & plan sketch of pond, riser, barrel, emergency spillway, with elevations.
10. **Conclusion/compliance matrix** — each regulatory criterion → computed value → pass/fail.

## Output format
Single Markdown (.md) file, ~300–400 lines. Tables for CNs, peaks, stage-storage, and compliance matrix. ASCII plan/profile sketches. Formulas inline (e.g., `Q = (P - 0.2S)² / (P + 0.8S)` where `S = 1000/CN - 10`).

## Iteration targets
1. First pass commonly conflates WQv and peak control — require both treated separately, with the WQv shown as a dedicated permanent pool calc, not mixed into routing.
2. Push for time-of-concentration (Tc) broken into sheet/shallow concentrated/channel segments, each with its own length, slope, and velocity.
3. Demand an SA/DA lookup from NCDEQ Table C-2.1 (or equivalent) with the actual impervious fraction, not a guessed surface area.
4. Require the stage-storage curve as a table with at least 6 stages, not just "volume ≈ X."
5. Tighten the emergency spillway: broad-crested weir equation `Q = C·L·H^1.5` with specified C (2.65-3.1), and demonstrate 100-yr + 1 ft freeboard.
6. Add riprap D50 sizing with actual tailwater condition and apron length/width.

## Success criteria
- Cites NCDEQ Stormwater Design Manual (2023), NOAA Atlas 14, TR-55/NRCS methods.
- Pre/post peaks computed for at least 1/10/25-yr with Qpost ≤ Qpre after SCM.
- WQv computed with the Rv formula, not just volume ≈ 1 in over impervious.
- Stage-discharge includes riser, barrel, and emergency spillway controls and shows which governs at each stage.
- Geotech constraint (SHWT + 1 ft) is respected in pond bottom elevation.
- Compliance matrix explicitly enumerates each criterion and shows the computed value meeting it.

## Scope target
For a 15-minute v1: project description with cited standards, CN-weighted pre/post tables, one Tc segmental calc, peak flows for 10-yr, WQv calc with Rv, rough permanent pool sizing from SA/DA, stage-storage table skeleton, ASCII pond profile sketch, and a compliance matrix with a few rows filled and rest marked TODO.
