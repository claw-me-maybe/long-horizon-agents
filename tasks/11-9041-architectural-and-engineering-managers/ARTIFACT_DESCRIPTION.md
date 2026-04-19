# Preliminary Design Review (PDR) Package — Kestrel-2 Satellite Communications Subsystem

## Occupation
- **SOC:** 11-9041
- **Title:** Architectural and Engineering Managers

## Scenario
Orbital Signal Systems (OSS) is developing Kestrel-2, a 180-kg LEO satellite platform commissioned for the Athena-3 Earth observation constellation (prime: Vermeer Imaging; contract value $94M for 6 satellites). Director of Spacecraft Engineering Dr. Kelsey Whitfield chairs the Preliminary Design Review (PDR) for the Communications Subsystem (Comm) on November 18-19, 2026, before proceeding to Critical Design Review (CDR) in March 2027 and integration Q3 2027. Whitfield must produce the PDR package for the Comm subsystem covering architecture, trade studies, interfaces, risks, verification plan, and compliance crosswalk, to be distributed to the customer (Vermeer), the internal review board, and the independent technical consultant (Dr. Arpad Molnar, retired from JPL).

## Inputs
The model starts with:

- **Mission context:**
  - 6-satellite LEO constellation, 530-km sun-synchronous orbit, 10:30 LTDN.
  - Data budget: 2.8 TB/day/satellite (imagery + telemetry); must downlink within 3 contacts/day over Svalbard (SvalSat) and Inuvik ground stations.
  - Mission design life: 5 years; radiation environment 5 krad (Si) TID budget with 2x margin.
- **Comm subsystem requirements (from SRD, subset):**
  - COMM-001: S-band TT&C uplink ≥ 64 kbps, downlink ≥ 512 kbps; CCSDS-compliant.
  - COMM-002: X-band payload downlink ≥ 500 Mbps; DVB-S2X compliant; 8-PSK and 32-APSK support.
  - COMM-003: Ranging accuracy ≤ 10 m (1σ) via PN sequence.
  - COMM-004: Mass ≤ 18 kg including antennas.
  - COMM-005: Orbit-average power ≤ 42 W.
  - COMM-006: Operational temp -20°C to +55°C; survival -40°C to +75°C.
  - COMM-007: Radiation tolerance 15 krad (TID) per part; SEE LET threshold ≥ 37 MeV·cm²/mg.
  - COMM-008: TRL ≥ 6 at CDR for all elements.
- **Architecture trade options being evaluated:**
  - Option A: Integrated S-band + X-band transponder (single vendor: Satelle TRX-180). Lower mass (14.2 kg), higher cost ($1.48M/unit), TRL 7.
  - Option B: Discrete S-band + X-band transmitters (L3Harris S-band XCVR + Tesat HLX-50 X-band). Mass 17.1 kg, cost $1.12M/unit, TRL 8 each.
  - Option C: Build-to-print internal development using heritage from Kestrel-1. Mass 15.8 kg, cost $0.78M/unit amortized, TRL 5 at PDR rising to 6 by CDR.
- **Interface budgets (allocated from system):**
  - Comm-to-OBC: 2 × SpaceWire, 200 Mbps; 1 × RS-422 TT&C backup.
  - Comm-to-EPS: 28V±6V bus, inrush ≤ 8A peak.
  - Comm-to-Structure: 4-point flexure mount, < 500g fundamental.
- **Link budget draft (X-band downlink to Svalbard, 10° elevation, clear sky):**
  - EIRP satellite: 18.5 dBW (0.8 m antenna, 9 W RF, efficiency 0.52).
  - Free-space path loss: 166.2 dB.
  - Atmospheric: 0.8 dB.
  - G/T ground: 32 dB/K.
  - Required C/N₀ for 500 Mbps DVB-S2X 8-PSK 3/4: 84.3 dB-Hz.
  - Margin: 3.2 dB at 10° elevation; 6.1 dB at 30° elevation.
- **Heritage and risk context:** Kestrel-1 (launched 2024) flew a predecessor S-band transponder that had a latch-up event on orbit in July 2025 (recovered via power cycle); root cause traced to inadequate SEL margin in one FPGA. Customer (Vermeer) is sensitive to this.

## Artifact specification
A formal PDR package structured for a two-day engineering review. Sections:
1. **Executive overview** — mission context, subsystem role, recommended architecture, outstanding risks, path to CDR.
2. **Requirements compliance matrix** — each requirement (COMM-001 through COMM-008) vs. current design, status (Compliant / Partially Compliant / Not Yet Verified), evidence pointer.
3. **Architecture trade study** — Options A, B, C scored on at least 6 criteria (mass, power, cost, TRL risk, schedule risk, mission robustness, in-house capability) with weighted decision matrix. Explicit recommendation.
4. **Subsystem architecture block diagram** — described in text/ASCII with named blocks, interfaces, data flow.
5. **Link budget analysis** — detailed X-band downlink and S-band uplink/downlink budgets with margin under worst-case (10° elevation, rain attenuation) and nominal conditions.
6. **Interface Control Document (ICD) excerpt** — Comm-to-OBC, Comm-to-EPS, Comm-to-Structure interface specifications.
7. **Radiation & reliability analysis** — TID and SEE analysis at the part level with budget rollup, SEL mitigation approach (especially given Kestrel-1 heritage issue), redundancy architecture.
8. **Verification plan** — V&V matrix mapping each requirement to test/analysis/inspection/demonstration, with qualification model plan and protoflight approach.
9. **Risk register** — top 8-12 risks with likelihood × consequence, mitigation, owner, and trip-wires. Must include the Kestrel-1 latch-up heritage risk explicitly.
10. **Schedule to CDR** — key engineering milestones, long-lead procurement, risk-reduction prototypes.
11. **Open actions / RFAs (Requests for Action)** from this PDR — items to close before CDR.

Tone: aerospace-engineering rigorous. Review-board-defensible, citing standards (CCSDS, ECSS, MIL-STD-883). Assumes a reader who is technical but has not memorized the SRD.

## Output format
Markdown document with embedded tables, 12-18 pages rendered. Block diagrams can be ASCII or text-described; link budget and compliance matrix are tabular. Designed to be printable and annotated during a 2-day review.

## Iteration targets
1. **Make the trade study decision defensible** — v1 often handwaves the scoring. Iterate to explicit criteria weights (e.g., mission robustness 0.25, schedule 0.20, cost 0.15...) that sum to 1.0, numeric scoring 1-5 per criterion, and a rationale paragraph for each score. Show the arithmetic.
2. **Confront the Kestrel-1 heritage risk head-on** — v1 may mention it briefly. Iterate to a dedicated subsection: root cause of the July 2025 SEL, what design change in Kestrel-2 addresses it (FPGA part change? SEL-immune family? current-sense circuit?), and independent analysis by the consultant to validate.
3. **Sharpen the link budget margin discussion** — v1 may just state margin at 10°. Iterate to explicit worst-case (10° elevation + rain fade + pointing loss + aging) vs. best-case with sensitivity to EIRP, antenna pointing, and receiver G/T. Call out whether 3.2 dB is sufficient (typically want 3-6 dB at worst-case) and what drives it.
4. **Tighten the verification matrix** — v1 may map requirements to "Test" generically. Iterate to specific tests: "COMM-002 verified by X-band downlink throughput test at 22°C and at ±hot/cold qualification extremes; equipment: ETS-Lindgren chamber, Keysight N9040B; success criterion: BER < 1e-9 at 500 Mbps over 60 min."
5. **Convert the risk register from qualitative to semi-quantitative** — v1 may use "High/Med/Low." Iterate to likelihood (1-5) × consequence (1-5) with numeric score, explicit trip-wire (e.g., "If TID margin analysis shows < 2x at CDR, elevate to program risk review").
6. **Resolve the TRL-6-at-CDR question for Option C** — if recommending Option C (internal build), v1 may assume TRL 6 is achievable without evidence. Iterate to a TRL-advancement plan with named tests, schedule, and fallback to Option B if TRL goal not achieved by a gate date.

## Success criteria
(For evaluator use only.)
1. Requirements compliance matrix covers all 8 listed requirements (COMM-001 through COMM-008) with a status and an evidence pointer.
2. Trade study has explicit criteria weights summing to 1.0, numeric scores, and a recommendation that follows from the math.
3. Link budget is complete with gain/loss items summed correctly to a stated margin, distinguishes worst-case vs. nominal.
4. Kestrel-1 heritage SEL is explicitly addressed with a specific Kestrel-2 design mitigation, not just acknowledged.
5. Verification matrix maps each requirement to a verification method (T/A/I/D) with at least test-level specificity for COMM-002 and COMM-007.
6. Risk register has at least 8 risks with semi-quantitative scoring and trip-wires; the Kestrel-1 heritage risk is present.
7. Subsystem block diagram (text/ASCII) shows all major blocks and all three primary interfaces (OBC, EPS, Structure).

## Scope target
A v1 at ~15 minutes should contain: executive overview with recommended architecture; compliance matrix for all 8 requirements (even if with coarse status); trade study table with the 3 options and 4-5 criteria (weights can be unweighted in v1); a block diagram sketch; a one-row link budget showing total margin; a verification matrix with at least half the requirements mapped; a risk register with 5-6 risks including Kestrel-1; and a to-CDR milestone list. Detailed SEE analysis, full ICD excerpt, and rigorous trade-study arithmetic are iteration targets.
