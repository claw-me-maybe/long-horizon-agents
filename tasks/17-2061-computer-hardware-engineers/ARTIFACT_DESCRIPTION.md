# DDR5-6400 Memory Channel Signal Integrity Pre-Layout Analysis Memo — Project "Kestrel" 2U Edge Inference Server

## Occupation
- **SOC:** 17-2061
- **Title:** Computer Hardware Engineers

## Scenario
Halcyon Compute Systems is designing the "Kestrel" 2U edge-inference motherboard (rev B1) targeting
tape-out on 2026-07-15. The board uses a single AMD EPYC 9334 "Genoa" SP5 socket with 12 DDR5
RDIMM channels routed to 24 DIMM slots (2 DPC) on a 14-layer stackup. SI lead Priya Desai needs
a pre-layout signal integrity memo she can hand to layout designer Tom Ng and to the hardware
review board (chaired by VP Eng Marcus Yeh) before the layout kickoff on 2026-04-29. The same
memo must satisfy contract manufacturer Jabil's DFM review and the Micron DRAM vendor sign-off
package that accompanies the IBIS-AMI correlation report.

## Inputs

### Silicon
- **CPU package:** AMD EPYC 9334, Socket SP5, LGA-6096, 32 cores, 210 W TDP.
- **Memory controller:** per JESD79-5B (DDR5), 12 independent channels, each 40 bits wide
  (32 data + 8 ECC).
- **Data rate:** 6400 MT/s (Gen-5 speed bin), tCK = 312.5 ps, unit interval UI = 156.25 ps.
- **DRAM vendor:** Micron 32 GB 1Rx4 RDIMM MTC20F1045S1RC48BA (DDR5-4800 rated; derated to 6400
  via strict channel budget).

### Stackup (14 layer, Panasonic Megtron-6, Dk = 3.4 @ 5 GHz, Df = 0.002)
| Layer | Type      | Copper | Dielectric below (mil) | Notes           |
|-------|-----------|--------|------------------------|-----------------|
| L1    | Sig (µstrip) | 0.5 oz | 3.5 prepreg         | Surface routing |
| L2    | GND       | 1.0 oz | 2.8 core              | Primary return  |
| L3    | Sig (stripline) | 0.5 oz | 3.5 prepreg       | DDR5 DQ bytes 0–3 |
| L4    | PWR (VDDQ) | 1.0 oz | 2.8 core             | 1.1 V plane     |
| L5    | Sig       | 0.5 oz | 3.5 prepreg           | DDR5 DQ bytes 4–7 |
| L6    | GND       | 1.0 oz | 2.8 core              |                 |
| L7    | Sig       | 0.5 oz | 3.5 prepreg           | CMD/ADDR fly-by |
| L8    | Sig       | 0.5 oz | 2.8 core              | Low-speed I/O   |
| L9    | GND       | 1.0 oz | 3.5 prepreg           |                 |
| L10   | Sig       | 0.5 oz | 2.8 core              | DDR5 DQ bytes 8–11 |
| L11   | PWR (VCCIO) | 1.0 oz | 3.5 prepreg         | 1.8 V / 0.75 V  |
| L12   | Sig       | 0.5 oz | 2.8 core              | DDR5 DQS/CK     |
| L13   | GND       | 1.0 oz | 3.5 prepreg           |                 |
| L14   | Sig (µstrip) | 0.5 oz | —                  | Bottom surface  |

### Topology
- **CMD/ADDR/CTL:** fly-by daisy-chain, single-drop RTT at the far end DIMM.
- **DQ/DQS:** point-to-point per DIMM, T-topology branching from CPU package ball pad.
- **2 DPC:** two DIMMs per channel; stub length 0.35–0.60 in from T-junction to each DIMM.

### Impedance targets
- Single-ended DQ/CMD: **40 Ω ±10%** (36–44 Ω).
- Differential DQS/CK: **80 Ω ±10%** (72–88 Ω).
- Skin-effect/dielectric loss budget at Nyquist (3.2 GHz): IL ≤ 0.8 dB/in.

### Length & skew targets
- Max channel length: 4.5 in CPU → nearest DIMM, 5.8 in CPU → farthest DIMM.
- Intra-byte DQ skew: ≤ 2 ps.
- Byte-to-byte skew: ≤ 10 ps.
- CMD-to-DQS: nominal matched ±25 ps, trained per RDIMM SPD.

### Budgets (JEDEC DDR5 6400 B0 channel budget)
- Eye height at DRAM pin: ≥ 140 mV.
- Eye width at DRAM pin: ≥ 0.25 UI (39.1 ps).
- Total jitter Tj @ BER = 1e-16: ≤ 0.3 UI.
- Crosstalk: NEXT ≤ 3 %, FEXT ≤ 5 %.
- Return loss at DRAM pin: ≤ −10 dB from 100 MHz to 3.2 GHz.

### Reference documents
- JEDEC JESD79-5B (DDR5 spec) and JESD400-5B (RDIMM).
- AMD SP5 DDR5 design guide rev 1.3 (baseline; deviate only with written justification).
- IPC-2141A (impedance), IPC-2221B (generic design), IPC-6012F (fabrication class 3).
- Micron TN-40-08 DDR5 Layout Guidelines Rev 1.2.

## Artifact specification
A pre-layout SI analysis memo (engineering report) addressed to the layout team and HW review
board. The memo must contain the following numbered sections in this order:

1. **Header block** — project name, rev, author (PE or SI lead), date, distribution list
   (layout, DRI, DFM, vendor SI).
2. **Executive summary** — one paragraph. Pass/fail sketch per-channel-group summary.
   Top three risks with mitigation owners.
3. **Topology & stackup**
   - Narrative of chosen T-topology vs alternatives (daisy-chain, direct point-to-point).
   - ASCII block diagram of T-topology showing CPU, T-junction, DIMM0, DIMM1, stub lengths.
   - Stackup table (see Inputs) with Zo-per-layer computed using IPC-2141 or Wadell.
4. **Impedance calculations**
   - Chosen trace width/spacing for each signal class (e.g., L3 stripline 4.5 mil / 6 mil gap).
   - Formula cited (Wadell stripline, IPC-2141A §4, or HyperLynx Fast Eye solver).
   - Sensitivity: show ΔZo for ±0.5 mil prepreg and ±10 % Dk variation.
5. **Channel budgets**
   - Table: total insertion loss, CTLE budget, package loss, DRAM buffer loss.
   - Crosstalk NEXT/FEXT allocation.
   - Skew breakdown: intra-pair, intra-byte, byte-to-byte, CMD-to-DQS.
6. **Routing rules**
   - 3W rule within DQ byte, 5W between byte lanes.
   - Serpentine radius ≥ 3× trace width.
   - Via stub policy (max stub 10 mil, back-drill target 8 mil residual).
   - Reference-plane transitions — stitching via rule (1 stitch via per transition within 50 mil).
7. **Termination & ODT plan**
   - RTT_WR, RTT_NOM, RTT_PARK settings for each of the 4 rank-population cases
     (1R/1R, 1R/2R, 2R/1R, 2R/2R).
   - VTT decoupling: one 0.1 µF per termination resistor within 80 mil.
8. **Power delivery callout**
   - VDDQ target: 1.1 V ±3 %, ripple ≤ 15 mV p-p @ 1 MHz.
   - VPP target: 1.8 V ±5 %.
   - Decoupling plan: bulk 47 µF + 10 µF tantalum + 0.1 µF + 0.01 µF per DIMM pocket.
   - Target plane impedance ≤ 10 mΩ to 500 MHz.
9. **Simulation plan**
   - IBIS-AMI models:
     - CPU: AMD SP5 IBIS-AMI rev 0.9 (preliminary, pending GA).
     - DRAM: Micron MT60B2G8HB-48B IBIS-AMI rev 2.1.
   - Tool: HyperLynx DDR5 wizard or Ansys SIwave.
   - Corner matrix: SS/TT/FF process × −40/+25/+85 °C × Vdd ±3 %.
   - Pass/fail gates: eye height, eye width, jitter as in Inputs.
10. **Open risks & mitigations** — numbered list. Each risk has owner, severity (H/M/L),
    expected close date (ECD).

## Output format
Single Markdown (.md) file, approximately 280–380 lines. ASCII block diagrams for stackup and
topology inside fenced code blocks. Markdown pipe-syntax tables for budgets, skew decomposition,
and stackup. No external images or binary attachments.

## Iteration targets
1. First pass often misses skew budget decomposition — push for intra-byte / inter-byte /
   CMD-to-DQS skew shown as separate line items with numeric ps budgets, not lumped
   "match lengths" guidance.
2. Sharpen impedance calcs: require actual trace widths (e.g., 4.5 mil on L3 stripline) with
   a sensitivity table for ΔZo vs ±0.5 mil prepreg and ±10 % Dk.
3. Add explicit via-stub guidance (max stub 10 mil, back-drill residual 8 mil) and tie it to
   the Nyquist harmonic content at 3.2 GHz.
4. Expand the crosstalk section with NEXT/FEXT coupling length limits, a 3 %/5 % aggressor-
   victim budget, and 3W/5W rule enforcement.
5. Add a corner-analysis matrix (process × temperature × voltage) rather than presenting only
   a single nominal simulation.
6. Tighten the termination section with an RTT table covering all four rank-population
   combinations (1R/1R, 1R/2R, 2R/1R, 2R/2R).

## Success criteria
- Memo references JEDEC JESD79-5B (or JESD400-5B), the AMD SP5 DDR5 design guide, and
  IPC-2141/2221 where appropriate.
- Every numeric target carries units AND a tolerance; no bare "40 Ω" without the ±.
- Skew budget arithmetic closes: intra-pair + inter-pair + package + DRAM ≤ total channel
  skew allowance.
- Impedance calculations show chosen trace geometry with at least one sanity check against
  a known field-solver output or closed-form formula.
- The simulation plan names specific IBIS-AMI model files and spec-compliant PVT corner
  combinations (not just "typical conditions").
- ASCII topology diagram distinguishes main-line vs stub sections and labels lengths in
  mils or inches.

## Scope target
For a 15-minute v1, expect: executive summary (pass/fail sketch), stackup table with
approximate Zo for two critical layers, T-topology ASCII diagram, one channel budget table
(loss + crosstalk + skew), basic ODT plan for 2 DPC, and named IBIS models for simulation.
A full corner matrix and complete per-rank RTT combinations may be stubbed as TODOs with
placeholder values.
