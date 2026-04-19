# 2.4 GHz LNA Design Memo with Simulation — "Osprey" BLE 5.3 Asset Tag Front-End (Rev A2)

## Occupation
- **SOC:** 17-2072
- **Title:** Electronics Engineers, Except Computer

## Scenario
Wayfinder Telemetry is finalizing the RF front-end of its "Osprey" BLE 5.3 asset tag
(P/N WT-OSP-2A) ahead of FCC Part 15.247 and ETSI EN 300 328 V2.2.2 certification scheduled
for 2026-06-30 at TUV SUD. Senior RF engineer Arjun Rao must produce a 2.4 GHz LNA design
memo with simulation results for the system architect Mei Zhao and the EMC reviewer
Kai Storm ahead of the design freeze on 2026-05-13. The LNA sits between a ceramic chip
antenna and a Nordic nRF54L15 SoC; the receive path is shared with a TDD BLE radio and
must bypass cleanly during the 4 dBm Tx burst. The board is 4-layer FR-4 (Isola 370HR,
Dk = 4.2 @ 2.45 GHz, Df = 0.02), total thickness 0.8 mm. Rev A1 failed EN 300 328 radiated
spurious at the second harmonic (4.88 GHz) by 3 dB.

## Inputs

### Band and waveform
- PHY: BLE 5.3 (LE 1M, LE 2M, LE Coded).
- Frequency band: 2.400–2.4835 GHz, center 2.44 GHz.
- Channel bandwidth: 2 MHz (LE 2M).
- Occupied bandwidth target: 83.5 MHz.

### Link-budget-derived LNA specification
| Parameter         | Target                           | Notes                             |
|-------------------|----------------------------------|-----------------------------------|
| Noise figure (NF) | ≤ 1.5 dB                         | After front-end switch            |
| Gain (|S21|)     | 14–16 dB                         | 2.40–2.485 GHz                    |
| IIP3              | ≥ −10 dBm                        | Two-tone, 2.440/2.441 GHz          |
| P1dB (input)      | ≥ −18 dBm                        |                                   |
| Input return loss | ≤ −10 dB                         | 2.40–2.485 GHz                    |
| Output return loss| ≤ −10 dB                         | 2.40–2.485 GHz                    |
| Stability         | K > 1, |Δ| < 1, μ > 1           | Unconditional across 0.5–6 GHz    |

### Antenna & source impedance
- Antenna: Johanson Technology 2450AT18B100E ceramic chip antenna.
- VSWR: ≤ 2.0:1 over 2.400–2.4835 GHz, giving source Γ up to 0.33.
- Antenna port matching target: 50 Ω nominal at center frequency.

### Candidate LNA devices
- **Baseline:** Qorvo QPL9547, integrated matching, NF = 0.6 dB typ, gain = 18 dB typ,
  IIP3 = +8 dBm, P1dB = −5 dBm, 3.3 V / 32 mA, SMT 2×2 mm DFN.
- **Alternate:** Skyworks SKY67151-396LF, NF = 0.44 dB typ, gain = 16 dB typ, 5 V / 70 mA.

### Supply and biasing
- Rail: 3.3 V from TI TPS7A20 LDO, PSRR = 60 dB @ 1 MHz, dropout 170 mV.
- Bias trace shared with PA (BOM freeze prevents split at rev A2).
- Decoupling ladder near LNA VCC:
  10 µF tantalum (Kemet T491A) + 1 µF X5R 0402 + 100 nF X7R 0402 + 10 nF C0G 0402 +
  1 nF C0G 0201, all within 2 mm of the VCC pin.

### Switching topology
- RF switch: Skyworks SKY13317-373LF SPDT, insertion loss 0.6 dB typ, isolation ≥ 25 dB
  at 2.4 GHz, return loss 18 dB typ.
- Path: Antenna → Switch → LNA → SAW BPF (Murata SAFFB2G45BA0F0A) → SoC RX LNA input.

### Simulation environment
- Tool: Keysight ADS 2024.
- Vendor S-parameter file: QPL9547_3V3_VGS.S2P (Qorvo, revision 2023-11).
- Passives library: Modelithics MDLX v11 (includes SRF and Q vs frequency).

### Compliance standards
- FCC 47 CFR §15.247 (intentional radiator, 2.4 GHz ISM).
- ETSI EN 300 328 V2.2.2 (wideband data transmission systems, 2.4 GHz).
- IEC 61000-4-2:2008 (ESD, ±8 kV contact, ±15 kV air).
- IPC-2221B (generic PCB design), IPC-7351B (SMT land patterns), IPC-2141A (impedance).

## Artifact specification
An LNA design memo with simulation results, organized in the following numbered sections:

1. **Header & revision history** — project, rev, author, reviewers, date, change log.
2. **Purpose & requirements** — link-budget-derived LNA specification table (see Inputs)
   with each parameter traced to its system origin (Rx sensitivity, adjacent channel
   rejection, emissions compliance).
3. **Topology choice**
   - ASCII block diagram: Antenna → SPDT Switch → LNA → SAW BPF → SoC RX.
   - Justification for the integrated-match QPL9547 vs a discrete-match alternative.
   - Reference to Qorvo app note AN-2045 as baseline.
4. **Small-signal design**
   - Source-match network: topology (shunt-L / series-C) and component values from the
     Modelithics library (e.g., Murata LQW15AN 1.8 nH ±2 %, Murata GRM1555 0.8 pF C0G
     ±0.1 pF).
   - Load-match network: topology and component values.
   - Smith-chart reference points described textually, with the trajectory annotated in
     an ASCII schematic.
   - Calculated |S11| and |S22| across band.
5. **Noise and stability**
   - Cascaded noise figure using Friis:
     NF_total = NF_sw + (NF_lna − 1) / G_sw.
   - Simulated NF from the Qorvo S2P file at min/typ/max corners.
   - Rollett stability: K factor and μ factor across 0.5–6 GHz.
6. **Linearity**
   - Two-tone test setup (f1 = 2.440 GHz, f2 = 2.441 GHz, each at −30 dBm input).
   - IIP3 extrapolation via 3rd-order intercept.
   - P1dB sweep from −30 dBm to −5 dBm input.
7. **Bias & supply**
   - Decoupling ladder (see Inputs) with PDN impedance target ≤ 0.5 Ω to 1 GHz.
   - LDO PSRR vs any in-band spur; margin computation.
8. **Layout rules & EMC**
   - 50 Ω coplanar waveguide with ground (CPWG) trace geometry: width 0.45 mm, gap
     0.20 mm, solved against IPC-2141A with tolerance from fab.
   - Via fence pitch ≤ λ/10 at 2.45 GHz (≈ 5 mm).
   - ESD: Littelfuse SP1003-01WTG TVS at antenna port, Ct ≈ 0.3 pF — folded into the
     source match.
   - Second-harmonic trap or filter strategy for EN 300 328 compliance at 4.88 GHz.
9. **BOM review** — table: reference designator, part number, manufacturer, tolerance,
   SRF, Q at 2.4 GHz, RoHS status.
10. **Simulation results summary** — table of S11, S22, S21, NF, IIP3, P1dB, K, μ at
    each PVT corner (typ 25 °C, SS −40 °C min Vdd, FF 85 °C max Vdd).
11. **Risks and mitigations** — at least three, each with owner and due date.
12. **Sign-off block.**

## Output format
Single Markdown (.md) file, approximately 300–400 lines. ASCII block diagrams and
schematic snippets inside fenced code blocks. Markdown pipe-syntax tables for the
specification, BOM, and simulation corners. Formulas inline (Friis, K factor,
CPWG impedance from IPC-2141A).

## Iteration targets
1. First pass often skips stability analysis — require numeric K and μ across 0.5–6 GHz,
   not just a pass/fail verdict.
2. Push for simulation across PVT corners (typical / min / max; temperature −40 / +25 /
   +85 °C; Vdd ±3 %) rather than a single nominal number.
3. Tighten the matching network description: include the SRF of the chosen inductor
   (e.g., LQW15AN 1.8 nH SRF ≈ 8 GHz) and the Q at 2.4 GHz (Q ≈ 30), not only the
   inductance value.
4. Demand an explicit NF cascade: show NF_total = NF_sw + (NF_lna − 1)/G_sw, with switch
   insertion loss (0.6 dB) degrading the front-end NF by an exact amount.
5. Require the ESD TVS capacitance to be folded into the source match rather than
   assumed transparent.
6. Sharpen layout rules with numeric targets (CPWG width / gap, via fence pitch, decap
   placement distances, and a second-harmonic suppression strategy).

## Success criteria
- Memo cites FCC §15.247, ETSI EN 300 328 V2.2.2, IPC-2141A, and a relevant vendor app
  note.
- The LNA specification is traceable to the system link budget (Rx sensitivity ⇒ NF
  budget).
- The matching network is specified with real part numbers, tolerances, SRF, and Q.
- Stability is proven with K and μ factors across a wide band (not only in-band).
- Simulation results are presented for at least three PVT corners with explicit
  pass/fail against the specification.
- Front-end NF cascade closes arithmetically: switch + LNA + BPF ≤ system NF budget.

## Scope target
For a 15-minute v1: header, requirements table traced to the link budget, ASCII block
diagram, chosen topology with the QPL9547 baseline and source-match starter values,
NF cascade with the switch, a stability check concept (K / μ), the bias decoupling
ladder, and a nominal simulation-results table. A full 3-corner PVT sim, the ESD-into-
match folding, and the full BOM with tolerances may be recorded as TODOs.
