# Stormwater Detention Pond Sizing Calculation Package — Maple Ridge Commons Redevelopment (Permit Submittal to City of Asheville)

## Occupation
- **SOC:** 17-2051
- **Title:** Civil Engineers

## Scenario
Ridgeline Civil Group is the engineer of record for Maple Ridge Commons, a 12.4-acre infill
mixed-use redevelopment in Asheville, NC (parcel 9728-55-3341). Design lead Tomás Alvarez
must submit the stormwater management calculation package to the City of Asheville
Stormwater Services by 2026-05-04 to support a Type III site plan review. The city requires
compliance with the Asheville Unified Development Ordinance (UDO) Article 7 and the NCDEQ
Stormwater Design Manual (July 2023 update). The receiving water is an unnamed tributary
to Ross Creek, which is listed as impaired on the 2022 §303(d) list, triggering enhanced
nutrient control requirements. A pre-application meeting on 2026-03-18 with the city's
stormwater engineer (Angela Reyes, PE) confirmed that a wet detention pond will be the
preferred stormwater control measure (SCM).

## Inputs

### Site characteristics
- Gross site area: 12.4 acres.
- Pre-development cover: 82 % woods (NRCS Hydrologic Soil Group B/C), 18 % meadow.
- Post-development cover:
  - Buildings (roofs): 4.1 ac impervious.
  - Pavement (parking, drives, walks): 5.9 ac impervious.
  - Landscaped / pervious: 2.4 ac (HSG B, lawn in good condition).
- Total post-development impervious: 10.0 ac → 80.6 % of site.

### Soils (NRCS Web Soil Survey)
- Map unit: Evard-Cowee complex, 15–25 % slopes.
- Hydrologic Soil Group: B.
- Curve numbers (24-hr TR-55, AMC II):
  - Woods (good), HSG B: CN = 55.
  - Meadow, HSG B: CN = 58.
  - Impervious, connected: CN = 98.
  - Lawn / open space in good condition, HSG B: CN = 61.

### Rainfall (NOAA Atlas 14, Volume 2, Version 3)
- Point: latitude 35.5951°, longitude −82.5515° (Buncombe County).
- Distribution: 24-hour, Type II.

| Storm      | Depth (in) |
|------------|-----------:|
| 1-yr/24-hr | 2.91       |
| 2-yr/24-hr | 3.46       |
| 10-yr/24-hr | 5.02      |
| 25-yr/24-hr | 6.03      |
| 100-yr/24-hr | 8.14     |

### Regulatory criteria
- **Peak control (UDO §7-12-4(a)):** post-development peak discharge ≤ pre-development peak
  for the 1-, 10-, and 25-year, 24-hour storms.
- **Water-quality volume (WQv, NCDEQ §3.4):** runoff from 1.0 in of rainfall falling on the
  impervious area, using the Schueler Rv formula: Rv = 0.05 + 0.9 · i, where i is the
  impervious fraction (decimal).
- **Nutrient removal:** 30 % TN and 30 % TP, meeting Nutrient Sensitive Waters rule via
  wet pond (NCDEQ SCM Manual Table C-2, 90 % TSS removal tier).
- **Receiving channel stability:** non-erosive exit velocity ≤ 2.0 fps for 2-yr storm.

### Proposed SCM
- Wet detention pond per NCDEQ SCM Manual Chapter C-2 (Wet Pond).
- Primary spillway: perforated riser with circular barrel.
- Emergency spillway: broad-crested weir.

### Geotechnical
- Seasonally High Water Table (SHWT): elevation 2194.0 ft (measured, 2026-02 piezometer).
- NCDEQ requires pond bottom ≥ 1.0 ft above SHWT.
- Available pond footprint: 0.85 acre at average existing elevation 2198.5 ft.

### Topography & hydrology
- Longest flow path pre-development: 2,140 ft, average slope 6.8 %.
- Longest flow path post-development: 1,890 ft, average slope 4.2 % (regraded).
- Tailwater at outfall: 2,189.5 ft (10-yr), 2,191.0 ft (100-yr).

## Artifact specification
A stormwater management calculation package (narrative-plus-calculations memo) with the
following numbered sections:

1. **Cover sheet** — project name, permit number (pending), preparer (Ridgeline Civil
   Group, Tomás Alvarez PE, NC #045112), reviewer, date, revision, PE seal block placeholder.
2. **Project description & regulatory basis** — one paragraph narrative citing Asheville UDO
   §7-12-4 and NCDEQ SCM Manual §3.4 and §C-2.
3. **Pre- and post-development hydrologic analysis**
   - Pre-development CN-weighted table.
   - Post-development CN-weighted table.
   - Time of concentration (Tc) calculation broken into sheet flow, shallow concentrated
     flow, and channel flow segments per TR-55 Chapter 3.
   - Peak discharges via TR-55 graphical or small-watershed unit hydrograph method.
4. **Peak discharge summary table** — Qpre vs Qpost for 1-, 2-, 10-, 25-, and 100-year
   storms; with and without the SCM in place.
5. **Water-quality volume (WQv) calculation** — show Rv = 0.05 + 0.9·i (i = 0.806 here),
   WQv = (1.0 in / 12 in/ft) · Rv · A · 43,560 ft²/ac.
6. **Wet pond sizing**
   - Permanent pool surface area via SA/DA method (NCDEQ Table C-2.1, 90 % TSS, 3.5 ft
     depth, impervious fraction 80 %).
   - Forebay volume = 20 % of permanent pool volume (NCDEQ §C-2.5).
   - Stage-storage curve — table of stage (ft), incremental storage (ft³), cumulative
     storage (ft³), for at least 6 elevations from pond bottom to emergency spillway crest.
7. **Routing**
   - Inflow hydrograph (TR-55 or WinTR-55 export) for 10-yr and 100-yr.
   - Stage-discharge relation for riser (orifice / weir as appropriate), barrel (inlet
     control vs outlet control), and emergency spillway (broad-crested weir
     Q = C · L · H^1.5 with C = 2.65–3.1).
   - Routed outflow hydrograph with peak attenuation.
   - 100-yr + 1 ft freeboard check to top of dam.
8. **Outlet protection** — riprap apron sized per NCDEQ D-50 design chart, apron length
   per NCHRP or NCDEQ §D, exit velocity ≤ 2.0 fps at tailwater.
9. **SCM geometry** — ASCII plan and profile sketches of the pond, riser, barrel, and
   emergency spillway, with all critical elevations labeled (bottom, permanent pool,
   principal spillway crest, emergency spillway crest, top of dam).
10. **Compliance matrix** — one row per regulatory criterion; columns for criterion,
    computed value, pass/fail, reference.
11. **Conclusion & PE sign-off block.**

## Output format
Single Markdown (.md) file, approximately 300–400 lines. Markdown pipe-syntax tables for
CNs, peak discharges, stage-storage, and the compliance matrix. ASCII plan and profile
sketches inside fenced code blocks. Equations inline (e.g.,
`Q = (P − 0.2S)² / (P + 0.8S)`, `S = 1000 / CN − 10`).

## Iteration targets
1. First pass often conflates WQv and peak control — require both treated separately, with
   the WQv shown as a dedicated permanent pool calc and not mixed into routing.
2. Push for the time-of-concentration (Tc) to be broken into sheet, shallow concentrated,
   and channel segments, each with its own length, slope, and velocity.
3. Demand an SA/DA lookup from NCDEQ Table C-2.1 (or equivalent) using the actual
   impervious fraction, not a guessed surface area.
4. Require the stage-storage curve as a table with at least six stages, not a one-line
   volume estimate.
5. Tighten the emergency spillway sizing: broad-crested weir equation Q = C·L·H^1.5 with
   a specific C value (2.65–3.1) and an explicit freeboard check at 100-yr + 1 ft.
6. Add riprap D₅₀ sizing with tailwater condition and an apron length/width per NCDEQ
   design chart.

## Success criteria
- Memo cites the NCDEQ Stormwater Design Manual (July 2023), NOAA Atlas 14, and TR-55 /
  NRCS methods.
- Pre- and post-development peaks are computed for at least the 1-, 10-, and 25-year
  storms, and Qpost ≤ Qpre after the SCM is in place.
- WQv is computed using the Rv formula, not approximated as "1 in over impervious."
- Stage-discharge includes riser, barrel, and emergency spillway controls and shows which
  control governs at each stage.
- The geotechnical constraint (pond bottom ≥ SHWT + 1.0 ft) is respected in the pond
  bottom elevation.
- The compliance matrix explicitly enumerates each regulatory criterion and shows the
  computed value meeting it.

## Scope target
For a 15-minute v1: project description with cited standards, CN-weighted pre/post tables,
one Tc segmental calc, peak flows for at least the 10-year storm, WQv calc with Rv,
rough permanent pool sizing from SA/DA, a skeleton stage-storage table, an ASCII pond
profile sketch, and a compliance matrix with 2–3 rows filled and the rest marked TODO.
