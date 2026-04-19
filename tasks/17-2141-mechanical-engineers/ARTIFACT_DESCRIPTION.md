# Planetary Gearbox Output Shaft-to-Bearing Tolerance Stack-Up Analysis — SolarTrack ST-450 Slew Drive

## Occupation
- **SOC:** 17-2141
- **Title:** Mechanical Engineers

## Scenario
Helios Kinetics is releasing the ST-450 slew drive for utility-scale solar trackers, with PPAP
submission to customer AxiomSolar due 2026-05-22. ME Rachel Okonkwo owns the output shaft
subassembly (P/N 04-ST450-200 Rev C) and must produce a tolerance stack-up analysis memo that
proves bearing preload and axial clearance stay within vendor (SKF 7214 BECBM angular contact)
limits across all manufacturing conditions. The memo will be reviewed by Quality manager
Dave Lin and presented at a customer Supplier Technical Review (STR) on 2026-05-08. The
analysis must cover both worst-case (WC) and statistical (RSS) methods and include a thermal
expansion sub-loop from the assembly reference temperature (20 °C) to the worst-case operating
temperature (85 °C).

## Inputs

### Subassembly stack (axial, from fixed shoulder to locknut face)
- Output shaft (17-4 PH H1025, machined on a Mazak Integrex i-200).
- Rear angular-contact bearing SKF 7214 BECBM (40° contact, DB face).
- Front angular-contact bearing SKF 7214 BECBM (40° contact, DB face) — back-to-back.
- Bearing carrier housing bore (ductile iron ASTM A536 65-45-12, bored & honed).
- Retaining shoulder on carrier, locknut (SKF KM14) with MB14 lockwasher.
- Direct back-to-back installation (no spacer ring).

### SKF 7214 BECBM vendor data
- Bore tolerance class: k5 (+0.015 / +0.002 mm on Ø70).
- OD tolerance class: housing fit M6 (applied to Ø125 bore), width B = 24 ±0.12 mm.
- Axial internal play, free: 35 ±10 µm.
- Target preload class: GB (light), axial preload target 50 ±20 N after mount.
- Axial stiffness (datasheet Fig. 14 for DB pair at GB preload): ≈ 340 N/µm.
- Contact angle α = 40°.

### Nominal critical dimensions (mm)
| Dim | Description                           | Nominal | Tol (bilateral) | Distribution (assumed) |
|-----|---------------------------------------|---------|-----------------|------------------------|
| A   | Shaft bearing seat Ø                  | 70.000  | k5 (+0.015/+0.002) | Normal, Cp = 1.33   |
| B   | Housing bore Ø                        | 125.000 | H6 (+0.022/0)   | Normal, Cp = 1.33     |
| C   | Shaft shoulder-to-shoulder axial len  | 48.000  | ±0.030          | Normal, Cp = 1.0      |
| D   | Bearing width (each)                  | 24.000  | ±0.120          | Normal, Cp = 1.0      |
| E   | Carrier bore shoulder-to-shoulder     | 48.060  | ±0.050          | Normal, Cp = 1.0      |
| F   | Locknut face runout to bearing face   | 0.000   | TIR 0.020       | One-sided, rectangular |

### GD&T datums
- Datum A: rear bearing seat OD (cylindricity 0.005 at MMC).
- Datum B: rear bearing face, perpendicular to A (|⊥| 0.010 A).
- Datum C: front bearing face, parallel to B (|//| 0.010 A–B).

### Operating conditions
- Assembly temperature: 20 °C nominal.
- Worst-case steady-state operating temperature at bearing: 85 °C.
- Shaft material 17-4 PH H1025 CTE: 10.8 × 10⁻⁶ /°C.
- Carrier material ductile iron CTE: 11.8 × 10⁻⁶ /°C.
- Bearing steel 52100 CTE: 11.5 × 10⁻⁶ /°C.

### Standards referenced
- ASME Y14.5-2018 (dimensioning and tolerancing).
- ASME B4.2-1978 (reaffirmed) preferred fits.
- ISO 286-1:2010 (limits & fits).
- SKF Rolling Bearings Catalog PUB BU/P1 17000 EN (2022).
- SKF Mounting and Dismounting of Rolling Bearings PUB MP/P2 10000/3 EN.
- AGMA 923-B05 metrics of gearing (referenced for related shaft-end features).

### Acceptance criteria (from PPAP element 11 — dimensional validation)
- Room-temperature axial gap at assembly: 15 to 55 µm (ensures SKF GB preload window).
- Hot-condition axial gap at 85 °C steady state: positive (no bearing separation) and
  ≤ 80 µm.
- Bearing preload at 85 °C: 30 to 70 N axial (stays inside SKF GB preload band
  50 ±20 N).
- Process capability target for the dominant contributor: Cpk ≥ 1.33.

### Manufacturing process assumptions
- Shaft critical diameters ground to k5 on Studer S242 cylindrical grinder,
  Cpk ≥ 1.50 demonstrated on tool qualification run TQR-2026-009.
- Housing bore honed on Sunnen SV-310, Cpk = 1.42 demonstrated on TQR-2026-004.
- Shaft shoulder axial length turned on Mazak Integrex i-200, Cpk = 1.10 on TQR-2026-008
  (the dominant variation contributor and the most likely target for tightening).
- Locknut tightening torque 105 Nm per SKF MP/P2 Table 7, verified by hydraulic nut
  with 3 % torque repeatability.

### Failure modes to consider
- **Bearing skidding** at light preload (< 30 N axial): ball-on-race skid, shortened
  L10 life; addressed by ensuring minimum preload at hot condition.
- **Excessive preload** at cold startup (−20 °C field condition): friction torque
  climb; noted for field-condition check but outside primary stack-up scope.
- **Shoulder runout** (Datum B perpendicularity): translates to cyclic preload
  variation per revolution; addressed via |⊥| 0.010 A callout.

## Artifact specification
A tolerance stack-up analysis memo with the following numbered sections:

1. **Header** — part number, revision, author, date, reviewers, applicable drawings
   (04-ST450-200-A, 04-ST450-201-A, 04-ST450-205-B).
2. **Purpose & scope** — which dimensions are stacked, which are excluded, acceptance
   criterion (axial preload 50 ±20 N; no bearing gap under hot operation).
3. **Assembly sketch** — ASCII cross-section of shaft / bearing / housing with dimension
   callouts, datum flags (A, B, C), and direction arrows for each stack contributor.
4. **Loop definition** — numbered vector loop. Each row specifies: dimension ID, description,
   sign (+/−), nominal, tolerance. Loop must close (sum of signed nominals = gap/interference
   nominal).
5. **Worst-case (WC) analysis** — table with nominal, +tol, −tol, and arithmetic sum giving
   max/min envelope.
6. **Root-sum-square (RSS) analysis** — table extended with σ (= tolerance / 3 for Cp = 1),
   RSS σ, ±3σ envelope; annotate any non-normal distribution (e.g., rectangular for
   perpendicularity).
7. **Thermal stack** — separate loop computing ΔL = L·α·ΔT for each contributor, then
   superimposed on mechanical stack to produce hot-condition clearance.
8. **Bearing preload check** — convert computed axial clearance into axial force using
   bearing stiffness (340 N/µm). Compare against SKF GB target (50 ±20 N). Pass/fail with
   numeric margin.
9. **Capability discussion** — identify dominant contributor (typically C or E), propose
   tightened tolerance if margin is negative (e.g., C ±0.030 → C ±0.015).
10. **Sensitivity ranking** — one row per contributor; sensitivity =
    ∂(gap)/∂(dim) × tol. Sort descending.
11. **Conclusion & action items** — pass/fail verdict, open ECR numbers, sign-off block.

## Output format
Single Markdown (.md) file, approximately 260–360 lines. Markdown pipe-syntax tables for the
WC and RSS stack-ups. ASCII cross-section sketch inside a fenced code block. Formulas inline
(use backticks for `σ_total = sqrt(Σσᵢ²)` etc.). No images.

## Iteration targets
1. First pass often omits the thermal contribution — require a separate ΔT sub-loop using
   the per-material CTE values rather than lumping thermal into mechanical tolerance.
2. Distinguish WC and RSS correctly: WC uses ±full tolerance, RSS uses σ = tol / 3 for
   Cp = 1 or σ = tol / (3·Cp). Force the Cp assumption to be stated explicitly.
3. Enforce GD&T rigor: perpendicularity of the bearing seat face to shaft axis (|⊥| 0.010 A)
   should appear as a contributor with a rectangular distribution, not just diameter
   tolerances.
4. Add a sensitivity ranking table: show which single contributor, if tightened by 50 %,
   reduces total variation most.
5. Require the preload pass/fail to show arithmetic — convert axial clearance to force via
   bearing axial stiffness (340 N/µm), not a qualitative "pass."
6. Tighten the ASCII sketch: label datums A/B/C consistently with Y14.5 conventions and show
   bearing contact-angle arrows for the DB configuration.

## Success criteria
- References ASME Y14.5-2018 and ASME B4.2 (or ISO 286-1) for fits and tolerancing
  conventions.
- The stack-up loop is closed: signed vector sum returns to the gap nominal.
- Both WC and RSS results are presented, with the statistical assumption (Cp, distribution)
  stated for each contributor.
- Thermal expansion is a distinct loop with per-material CTE and the ΔT explicit.
- The preload check is number-vs-number pass/fail with margin quoted in newtons, not a
  qualitative statement.
- The memo identifies at least one dominant contributor and proposes a concrete tightening
  action (specific dimension and new tolerance value).

## Scope target
For a 15-minute v1: header, ASCII cross-section with datums labeled, one mechanical stack-up
table (WC and RSS columns), a rough thermal adjustment using per-material CTE, and a preload
pass/fail with margin expressed in newtons. Detailed Cp justification, full sensitivity
ranking, and specific tolerance tightening proposals may be recorded as TODOs.
