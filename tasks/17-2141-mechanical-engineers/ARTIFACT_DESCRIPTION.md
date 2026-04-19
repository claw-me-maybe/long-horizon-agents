# Planetary Gearbox Output Shaft-to-Bearing Tolerance Stack-Up Analysis — SolarTrack ST-450 Slew Drive

## Occupation
- **SOC:** 17-2141
- **Title:** Mechanical Engineers

## Scenario
Helios Kinetics is releasing the ST-450 slew drive for utility-scale solar trackers, with PPAP submission to customer AxiomSolar due 2026-05-22. ME Rachel Okonkwo owns the output shaft subassembly (P/N 04-ST450-200 Rev C) and must produce a tolerance stack-up analysis memo that proves bearing preload and axial clearance stay within vendor (SKF 7214 BECBM angular contact) limits across all manufacturing conditions. The memo will be reviewed by Quality manager Dave Lin and customer STR (supplier technical review) on 2026-05-08.

## Inputs
- **Subassembly:** Output shaft (17-4 PH H1025, GD&T per ASME Y14.5-2018) → 2× SKF 7214 BECBM 40° angular contact bearings in back-to-back (DB) configuration → bearing carrier (ductile iron 65-45-12, machined) → retaining shoulder and locknut (SKF KM14 + MB14 washer).
- **Vendor data:** SKF 7214 BECBM bore Ø70 k5 (+0.015/+0.002), outer Ø125 M6 (housing), width 24 mm ±0.12, axial play before mounting 35 ±10 µm, required preload class GB (light, target 50 ±20 N axial after mount).
- **Nominal critical dims (in mm):**
  - Shaft bearing seat Ø70.000, tolerance k5 (+0.015/+0.002).
  - Housing bore Ø125.000, tolerance H6 (+0.022/0).
  - Distance between shaft shoulders (bearing stack axial envelope) 48.000 ±0.030.
  - Bearing width (each) 24.000 ±0.120.
  - Spacer ring width between bearings 0.000 (no spacer) — direct back-to-back.
- **Operating conditions:** ΔT from 20 °C assembly to 85 °C steady-state at full load; shaft CTE 10.8e-6 /°C, carrier CTE 11.8e-6 /°C, bearing steel 52100 11.5e-6 /°C.
- **Standards:** ASME Y14.5-2018 (GD&T), ASME B4.2-1978 (fits, reaffirmed), ISO 286-1:2010.

## Artifact specification
A tolerance stack-up analysis memo with:
1. **Header** — part number, rev, author, date, reviewers, applicable drawings.
2. **Purpose & scope** — what dimensions are stacked, acceptance criterion.
3. **Assembly sketch** — ASCII cross-section of shaft/bearing/housing with dimension call-outs and datum references (A, B, C).
4. **Loop definition** — numbered vector loop with signs (+/−), one row per contributor.
5. **Worst-case (WC) analysis** — tabular, each contributor with nominal, +tol, −tol, and arithmetic sum.
6. **Root-sum-square (RSS) analysis** — same table extended with σ, assumed distribution (normal, Cp=1.33 unless stated), and 3σ bound.
7. **Thermal stack** — separate loop for ΔT expansion, superimposed on mechanical stack.
8. **Bearing preload check** — axial clearance vs SKF preload spec, pass/fail with margin in N.
9. **Capability discussion** — note which contributors drive variation, recommend tightened tolerances if needed.
10. **Conclusion & action items** — pass/fail verdict, sign-off block.

## Output format
Single Markdown (.md) file, ~260–360 lines. Use Markdown tables for stack-up. ASCII cross-section in a fenced code block. Formulas inline (e.g., `σ_total = sqrt(Σσᵢ²)`).

## Iteration targets
1. First pass often omits thermal contribution — require a separate ΔT stack using CTE values, not lumped into mechanical tolerance.
2. Distinguish WC from RSS correctly: WC uses ±full tolerance, RSS uses σ = tol/3 (for Cp=1) or tol/(3·Cp). Push for the Cp assumption to be explicit.
3. Enforce GD&T rigor: perpendicularity of bearing seat face to shaft axis (|⊥| 0.010 A) should appear as a contributor, not just diameter tolerances.
4. Add sensitivity ranking: which single contributor, tightened by 50%, reduces total variation most?
5. Require the preload pass/fail to show math — convert axial clearance into force via bearing stiffness (SKF 7214 axial stiffness ≈ 340 N/µm).
6. Tighten ASCII sketch: label datums A/B/C consistently with GD&T conventions.

## Success criteria
- References ASME Y14.5-2018 and a recognized fits standard.
- Stack-up loop is closed (vector sum returns to start, signs consistent).
- Both WC and RSS results presented, with correct statistical assumption stated.
- Thermal expansion handled as a distinct loop with per-material CTE.
- Preload check has a number-vs-number pass/fail, not a qualitative statement.
- Identifies at least one contributor as dominant and proposes a tightening action.

## Scope target
For a 15-minute v1: header, ASCII cross-section with datums, one mechanical stack-up table (WC + RSS), a rough thermal adjustment, and a preload pass/fail with margin. Detailed Cp justification, sensitivity ranking, and tolerance tightening proposals can be TODOs.
