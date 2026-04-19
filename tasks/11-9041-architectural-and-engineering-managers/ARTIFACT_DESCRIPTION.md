# Preliminary Design Review (PDR) Package — Kestrel-2 Satellite Communications Subsystem

## Occupation
- **SOC:** 11-9041
- **Title:** Architectural and Engineering Managers

## Scenario
Orbital Signal Systems (OSS) is developing Kestrel-2, a 180-kg LEO satellite platform
commissioned for the Athena-3 Earth observation constellation (prime: Vermeer Imaging;
contract value $94M for 6 satellites; launch cadence 2 per year starting Q4 2027).
Director of Spacecraft Engineering Dr. Kelsey Whitfield chairs the Preliminary Design
Review (PDR) for the Communications Subsystem (Comm) on November 18-19, 2026, before
proceeding to Critical Design Review (CDR) in March 2027 and integration Q3 2027.
Whitfield must produce the PDR package for the Comm subsystem covering architecture,
trade studies, interfaces, risks, verification plan, and compliance crosswalk, to be
distributed to the customer (Vermeer, represented by Chief Systems Engineer Dr. Arjun
Pradhan), the internal review board (Systems Engineering Lead Dr. Carmen Vega, Chief
Engineer Dr. Ilya Moravec), and the independent technical consultant (Dr. Arpad Molnar,
retired from JPL). A failed PDR means 6-8 weeks of rework and $800K of program budget
impact; a successful PDR proceeds to CDR procurement commitments.

## Inputs
The model starts with:

### Mission context
- 6-satellite LEO constellation, 530-km sun-synchronous orbit, 10:30 LTDN local time at
  descending node
- Data budget: 2.8 TB/day/satellite (imagery + telemetry); must downlink within 3 contacts/
  day over Svalbard (SvalSat) and Inuvik ground stations
- Mission design life: 5 years
- Radiation environment: 5 krad (Si) TID budget at component level with 2x RDM (margin)

### Comm subsystem requirements (subset from SRD, current baseline)
- **COMM-001:** S-band TT&C uplink ≥ 64 kbps, downlink ≥ 512 kbps; CCSDS-compliant
- **COMM-002:** X-band payload downlink ≥ 500 Mbps; DVB-S2X compliant; 8-PSK and 32-APSK
  modulation support
- **COMM-003:** Ranging accuracy ≤ 10 m (1σ) via CCSDS PN ranging sequence
- **COMM-004:** Mass ≤ 18 kg including antennas (target 16 kg, contract allocation 18 kg)
- **COMM-005:** Orbit-average power ≤ 42 W
- **COMM-006:** Operational temp -20°C to +55°C; survival -40°C to +75°C
- **COMM-007:** Radiation tolerance 15 krad (TID) per part; SEE LET threshold ≥
  37 MeV·cm²/mg (LOR-immune at this LET)
- **COMM-008:** TRL ≥ 6 at CDR for all elements per NASA TRL definitions

### Architecture trade options being evaluated
- **Option A: Integrated S-band + X-band transponder** (single vendor: Satelle TRX-180).
  Lower mass (14.2 kg), higher cost ($1.48M/unit), TRL 7 (heritage on 4 missions), schedule
  risk low.
- **Option B: Discrete S-band + X-band transmitters** (L3Harris S-band XCVR + Tesat
  HLX-50 X-band). Mass 17.1 kg, cost $1.12M/unit combined, TRL 8 each (extensive heritage),
  schedule risk low but integration complexity moderate.
- **Option C: Build-to-print internal development** using heritage from Kestrel-1 (our own
  in-house transponder). Mass 15.8 kg, cost $0.78M/unit amortized (lowest), TRL 5 at PDR
  needing to reach 6 by CDR, schedule risk moderate-to-high.

### Interface budgets (allocated from system)
- Comm-to-OBC: 2 × SpaceWire, 200 Mbps; 1 × RS-422 TT&C backup
- Comm-to-EPS: 28V±6V bus, inrush ≤ 8A peak, steady-state ≤ 1.5A per channel
- Comm-to-Structure: 4-point flexure mount, fundamental frequency < 500 Hz
- Comm-to-Thermal: -20°C to +55°C operational, dissipation 35 W typical, 48 W peak

### Link budget draft (X-band downlink to Svalbard, 10° elevation, clear sky)
- EIRP satellite: 18.5 dBW (0.8 m antenna, 9 W RF, antenna efficiency 0.52)
- Free-space path loss: 166.2 dB at 2,400 km slant range
- Atmospheric attenuation (clear sky): 0.8 dB
- Polarization + pointing loss allowance: 1.5 dB
- G/T ground (SvalSat X-band): 32 dB/K
- Required C/N₀ for 500 Mbps DVB-S2X 8-PSK 3/4 coding: 84.3 dB-Hz
- System margin at 10° elevation, clear sky: 3.2 dB
- System margin at 30° elevation, clear sky: 6.1 dB
- System margin at 10° elevation + rain (Svalbard worst-case 3mm/hr): 1.4 dB (tight)

### Heritage and risk context
- **Kestrel-1 (launched 2024):** flew a predecessor S-band transponder that had a
  single-event latch-up (SEL) event on orbit in July 2025. Recovered via power cycle.
  Root cause traced to inadequate SEL margin in one FPGA (Xilinx Virtex-5 SIRF; LET
  threshold of 28 MeV·cm²/mg, below Kestrel-2 requirement of 37 MeV·cm²/mg).
- **Customer sensitivity:** Vermeer's CSE Dr. Pradhan has explicitly flagged SEL
  mitigation as a review focus and will ask direct questions about FPGA part selection
  and current-limiting.

### Program context
- PDR must be closed by December 6, 2026 to hold the March 2027 CDR
- Long-lead procurement items: RF power amp (26-week lead), X-band antenna (18-week),
  radiation-hardened FPGAs (22-week)
- Design team: 4 RF engineers, 2 digital design, 2 systems, 1 radiation/parts engineer

## Artifact specification
A formal PDR package structured for a two-day engineering review. Sections:

1. **Executive overview** — mission context, subsystem role, recommended architecture,
   outstanding risks, path to CDR (including decision gate dates).
2. **Requirements compliance matrix** — each requirement (COMM-001 through COMM-008) vs.
   current design, status (Compliant / Partially Compliant / Not Yet Verified / Waiver
   Pending), evidence pointer (analysis/test/inspection document or plan).
3. **Architecture trade study** — Options A, B, C scored on at least 6 criteria (mass,
   power, cost, TRL risk, schedule risk, mission robustness, in-house capability, SEL
   mitigation) with weighted decision matrix (weights sum to 1.0). Explicit recommendation.
4. **Subsystem architecture block diagram** — described in text/ASCII with named blocks
   (transponder, diplexer, RF switch, antennas, modulator, decoder, BDM, FPGA), interfaces,
   data flow, and redundancy architecture.
5. **Link budget analysis** — detailed X-band downlink and S-band uplink/downlink budgets
   with margin under worst-case (10° elevation, rain attenuation, antenna pointing error,
   component aging) and nominal conditions. Sensitivity analysis on dominant contributors.
6. **Interface Control Document (ICD) excerpt** — Comm-to-OBC, Comm-to-EPS,
   Comm-to-Structure, Comm-to-Thermal interface specifications at PDR level of detail.
7. **Radiation & reliability analysis** — TID and SEE analysis at the part level with
   budget rollup, SEL mitigation approach (especially given Kestrel-1 heritage issue),
   redundancy architecture, FMECA summary.
8. **Verification plan** — V&V matrix mapping each requirement to verification method
   (Test / Analysis / Inspection / Demonstration), with qualification model approach
   (qual + protoflight? qual separate?), test equipment, and pass/fail criteria for key
   tests.
9. **Risk register** — top 8-12 risks with likelihood × consequence (numeric 1-5 each),
   mitigation, owner, and trip-wires. Must include the Kestrel-1 heritage SEL risk
   explicitly with current status.
10. **Schedule to CDR** — key engineering milestones, long-lead procurement commitments,
    risk-reduction prototypes (breadboard, engineering model), weekly cadence.
11. **Open actions / RFAs (Requests for Action)** from this PDR — items to close before
    CDR, with owner and due date.

Tone: aerospace-engineering rigorous. Review-board-defensible, citing standards (CCSDS,
ECSS, MIL-STD-883, GEVS). Assumes a reader who is technical but has not memorized the
SRD. Avoid marketing language ("advanced," "cutting-edge"); state specifications.

## Output format
Markdown document with embedded tables, 12-18 pages rendered. Block diagrams can be ASCII
or text-described; link budget and compliance matrix are tabular. Designed to be printable
and annotated during a 2-day review.

## Iteration targets
1. **Make the trade study decision defensible** — v1 often handwaves the scoring. Iterate
   to explicit criteria weights (e.g., mission robustness 0.25, SEL-risk mitigation 0.15,
   schedule 0.15, cost 0.15, mass 0.10, power 0.10, TRL at CDR 0.10) that sum to 1.0,
   numeric scoring 1-5 per criterion, and a rationale paragraph for each score. Show the
   arithmetic. Demonstrate that the recommended option wins on the weighted total.
2. **Confront the Kestrel-1 heritage risk head-on** — v1 may mention it briefly. Iterate
   to a dedicated subsection: root cause of the July 2025 SEL (Xilinx Virtex-5 SIRF LET
   threshold of 28 MeV·cm²/mg, below our new 37 requirement), what design change in
   Kestrel-2 addresses it (part change to Xilinx KU60 with LET >60 MeV·cm²/mg, or RTAX,
   or equivalent rad-hard FPGA family; plus current-sense circuit for fast SEL detection
   with automatic power-cycle), and independent analysis by Dr. Molnar to validate.
3. **Sharpen the link budget margin discussion** — v1 may just state margin at 10°.
   Iterate to explicit worst-case (10° elevation + 3mm/hr rain fade + 0.5° pointing loss
   + 1 dB component aging over 5 years) vs. best-case, with sensitivity to EIRP, antenna
   pointing, and receiver G/T. Call out whether 1.4 dB worst-case margin is sufficient
   (typically want 3+ dB at worst-case per NASA/GSFC practice) and what drives it — if
   tight, propose a change (e.g., larger antenna, higher RF power, or ACM fallback to
   QPSK in rain).
4. **Tighten the verification matrix** — v1 may map requirements to "Test" generically.
   Iterate to specific tests: "COMM-002 verified by X-band downlink throughput test at
   22°C and at ±hot/cold qualification extremes; equipment: ETS-Lindgren anechoic chamber,
   Keysight N9040B signal analyzer, Kratos DVB-S2X decoder; success criterion: BER
   < 1E-9 at 500 Mbps over 60 min continuous at each temperature."
5. **Convert the risk register from qualitative to semi-quantitative** — v1 may use
   "High/Med/Low." Iterate to likelihood (1-5) × consequence (1-5) with numeric score,
   explicit trip-wire (e.g., "If TID margin analysis shows < 2x RDM at CDR on any critical
   part, elevate to program risk review and initiate alternate part selection").
6. **Resolve the TRL-6-at-CDR question for Option C** — if recommending Option C (internal
   build), v1 may assume TRL 6 is achievable without evidence. Iterate to a TRL-advancement
   plan with named tests (breadboard end-to-end at PDR+2mo, engineering model hot+cold
   cycling at PDR+4mo, TID test at PDR+5mo), schedule, and a fallback to Option B if
   TRL goal not achieved by a named gate date (e.g., January 15, 2027). If NOT
   recommending Option C, include the rationale for why TRL risk outweighs the cost
   advantage.

## Success criteria
(For evaluator use only.)
1. Requirements compliance matrix covers all 8 listed requirements (COMM-001 through
   COMM-008) with a status and an evidence pointer.
2. Trade study has explicit criteria weights summing to 1.0, numeric scores, and a
   recommendation that follows from the weighted math.
3. Link budget is complete with gain/loss items summed correctly to a stated margin;
   distinguishes worst-case (with rain) vs. nominal (clear sky).
4. Kestrel-1 heritage SEL is explicitly addressed with a specific Kestrel-2 design
   mitigation (named part change or architectural change), not just acknowledged.
5. Verification matrix maps each requirement to a verification method (T/A/I/D) with at
   least test-level specificity for COMM-002 and COMM-007.
6. Risk register has at least 8 risks with semi-quantitative scoring (L × C numerics) and
   trip-wires; the Kestrel-1 heritage risk is present.
7. Subsystem block diagram (text/ASCII) shows all major blocks and all three primary
   interfaces (OBC, EPS, Structure) plus redundancy paths.
8. TRL plan for the recommended option shows how TRL 6 is achieved by CDR with named
   test milestones.

## Scope target
A v1 at ~15 minutes should contain: executive overview with recommended architecture;
compliance matrix for all 8 requirements (even if with coarse status); trade study table
with the 3 options and 4-5 criteria (weights can be unweighted in v1); a block diagram
sketch; a one-row link budget showing total margin; a verification matrix with at least
half the requirements mapped; a risk register with 5-6 risks including Kestrel-1; and a
to-CDR milestone list. Detailed SEE analysis, full ICD excerpt, rigorous trade-study
arithmetic, and TRL-advancement plan detail are iteration targets for v2/v3. By v3, the
trade-study weights should sum to 1.0, the Kestrel-1 mitigation should name a specific
FPGA or architectural change, and the link budget worst-case margin should be defended
against NASA/GSFC 3+ dB practice.
