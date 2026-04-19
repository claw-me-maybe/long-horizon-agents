# First-Pass Plan: 17-2051-civil-engineers

## Goal
Produce a stormwater calculation package memo that separates water-quality treatment from peak-control routing, demonstrates compliance with Asheville and NCDEQ requirements, and gives reviewers a clear pass/fail matrix.

## Working assumptions
- This is a permit-submittal narrative, so clarity of method and traceability matter as much as raw numbers.
- The first pass can be partially schematic, but it must already show the governing standards, CN tables, WQv formula, initial routing logic, and pond geometry constraints.
- The geotechnical constraint on pond bottom elevation is non-negotiable.

## First-pass execution sequence
1. Establish the regulatory basis and calculation method references.
   - Asheville UDO.
   - NCDEQ manual.
   - NOAA Atlas 14.
   - TR-55/NRCS equations.
2. Build the pre/post land-use and CN tables.
3. Perform initial Tc and runoff calculations.
   - At minimum, one segmental Tc breakdown in v1.
4. Separate the two sizing problems.
   - WQv/permanent pool sizing.
   - Peak attenuation/routing for design storms.
5. Draft a stage-storage table skeleton and ASCII plan/profile sketch.
6. Draft the compliance matrix with completed and TODO rows.

## What must be true in v1
- WQv is shown with the required `Rv` formula.
- Peak-control calculations are not conflated with WQv.
- The pond bottom elevation respects SHWT + 1 ft.
- The memo already shows which regulatory criteria are passed, pending, or need refinement.

## Main risks
- Mixing permanent pool sizing with detention routing.
- Using guessed surface area instead of tying it back to SA/DA logic.
- Omitting stage-storage detail or emergency spillway math.
- Producing a narrative without enough numeric scaffolding to survive review.

## Immediate iteration queue
- Expand Tc into sheet/shallow/channel segments.
- Add 1-, 10-, 25-, and 100-year peak summaries.
- Flesh out stage-discharge and emergency spillway equations.
- Add riprap sizing and outlet-velocity verification.
