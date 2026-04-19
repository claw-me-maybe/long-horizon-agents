# Iterated Plan: 17-2051-civil-engineers

## Objective
Produce a permit-ready stormwater calculation package that clearly distinguishes water-quality sizing from detention routing, shows traceable TR-55 / NCDEQ methodology, and gives Asheville reviewers a clean compliance matrix tied to numeric results.

## Required output shape
1. Cover sheet.
2. Project description and regulatory basis.
3. Pre/post hydrologic analysis.
4. Peak discharge summary.
5. Water-quality volume calculation.
6. Wet pond sizing.
7. Routing.
8. Outlet protection.
9. SCM geometry.
10. Conclusion / compliance matrix.

## Execution roadmap
### Pass 0: Method and assumptions sheet
- Fix the governing references at the top:
  - Asheville UDO Article 7,
  - NCDEQ Stormwater Design Manual (2023),
  - NOAA Atlas 14,
  - TR-55 / NRCS runoff equations.
- Record hard constraints:
  - 12.4-acre site,
  - pond footprint 0.85 ac,
  - SHWT 2194.0 ft,
  - pond bottom at least 1 ft above SHWT.

### Pass 1: Hydrology baseline
- Build pre- and post-development land-use tables.
- Compute weighted CN values for pre and post conditions.
- Show the runoff equation explicitly.
- At minimum, do one segmental Tc breakdown in v1; expand later to sheet, shallow concentrated, and channel segments.

### Pass 2: Split the sizing problem in two
- Water quality:
  - compute impervious fraction,
  - compute `Rv = 0.05 + 0.9i`,
  - compute `WQv = (1.0 in)(Rv)(A)`,
  - translate WQv into permanent pool sizing.
- Peak control:
  - compute pre and post peaks for required storms,
  - then route through the wet pond.
- Never mix WQv storage logic with detention-routing logic in the narrative.

### Pass 3: Wet pond geometry and storage
- Size the forebay at 20% of permanent pool.
- Tie permanent-pool surface area to the NCDEQ SA/DA method rather than guessing.
- Build a stage-storage table with at least 6 stages.
- Add ASCII plan/profile sketches with elevations, riser, barrel, emergency spillway, and freeboard.

### Pass 4: Routing and outlet controls
- Prepare inflow/outflow hydrograph summaries for 10-year and 100-year events.
- Show which outlet element controls at each stage:
  - riser,
  - barrel,
  - emergency spillway.
- Use broad-crested weir equation for emergency spillway and demonstrate `100-year + 1 ft freeboard`.
- Add outlet-protection sizing and show exit velocity `<= 2 fps`.

### Pass 5: Compliance matrix and review pass
- One row per requirement with:
  - criterion,
  - computed value,
  - pass/fail,
  - note or citation.
- Include nutrient-removal credit and impaired-stream context.
- Ensure geotech constraint is explicitly shown in the geometry section and matrix.

## High-risk failure modes
- Conflating water-quality storage and detention routing.
- Using hand-wavy SA/DA surface area.
- Omitting enough stage-storage detail for review.
- Failing to show governing outlet control by stage.
- Missing the geotechnical bottom-elevation constraint.

## Intermediate artifacts
- Method/criteria sheet with all governing standards and equations.
- Pre/post CN and land-use tables.
- Tc worksheet with segment definitions.
- WQv worksheet kept separate from detention-routing worksheet.
- Stage-storage table, stage-discharge table, and compliance matrix drafted as standalone components before final narrative assembly.

## Checkpoints
- Checkpoint 1: weighted CNs and runoff equations are complete before routing begins.
- Checkpoint 2: WQv is fully computed and translated into permanent-pool geometry before peak-control narrative is drafted.
- Checkpoint 3: stage-storage has at least six rows before freeboard claims are made.
- Checkpoint 4: outlet-control transitions are explicit rather than implied.

## Final QA gate
- If the memo could be read as mixing permanent-pool and detention-storage logic, restructure it.
- If any pass/fail claim lacks a cited computed value, fill it in or mark it pending.
- If the geotechnical elevation constraint is not visible in both geometry and compliance sections, the package is incomplete.

## Definition of done
- Reviewers can trace every major result back to a cited method.
- Peak control, WQv, emergency spillway, and outlet protection are all separately documented.
- The compliance matrix can stand alone as a permit-review checklist.
