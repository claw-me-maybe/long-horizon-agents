# DDR5-6400 Memory Channel Signal Integrity Pre-Layout Analysis Memo — Project "Kestrel" 2U Edge Inference Server

## Occupation
- **SOC:** 17-2061
- **Title:** Computer Hardware Engineers

## Scenario
Halcyon Compute Systems is designing the "Kestrel" 2U edge-inference motherboard (rev B1) targeting tape-out on 2026-07-15. The board uses a single AMD EPYC 9334 "Genoa" SP5 socket with 12 DDR5 RDIMM channels routed to 24 DIMM slots (2 DPC) on a 14-layer stackup. SI lead Priya Desai needs a pre-layout signal integrity memo she can hand to layout designer Tom Ng and to the hardware review board (chaired by VP Eng Marcus Yeh) before the layout kickoff on 2026-04-29.

## Inputs
- **CPU package:** AMD EPYC 9334 (Socket SP5, LGA-6096), DDR5 controller per JESD79-5B, target data rate 6400 MT/s (tCK = 312.5 ps, UI = 156.25 ps).
- **Topology:** T-topology with fly-by for CMD/ADDR, 2 DPC per channel. On-die termination (ODT) per DDR5 spec; RTT_WR = 40 Ω, RTT_NOM = 60 Ω, RTT_PARK = Hi-Z for idle rank.
- **Stackup (14 layers, FR4 Megtron-6, Dk=3.4 @ 5 GHz, Df=0.002):**
  - L1 Sig (microstrip), L2 GND, L3 Sig (stripline), L4 PWR, L5 Sig, L6 GND, L7 Sig, L8 Sig, L9 GND, L10 Sig, L11 PWR, L12 Sig, L13 GND, L14 Sig.
  - Core thickness 2.8 mil, prepreg 3.5 mil.
- **Trace targets:** Single-ended 40 Ω ±10%, differential 80 Ω ±10%. Max channel length 4.5 in CPU-to-nearest-DIMM, 5.8 in CPU-to-farthest.
- **Budgets (per JEDEC DDR5 6400 B0):** Eye height ≥ 140 mV, eye width ≥ 0.25 UI (39 ps) at DRAM pin, jitter Tj (BER 1e-16) ≤ 0.3 UI.
- **Reference designs:** Use AMD SP5 DDR5 design guide rev 1.3 as baseline; deviate only where justified.

## Artifact specification
A pre-layout SI analysis memo (engineering report) addressed to layout and review board. Must include:
1. **Header block** — project, rev, author, date, distribution list.
2. **Executive summary** — 1 paragraph, pass/fail per-channel summary, top 3 risks.
3. **Topology & stackup** — ASCII diagram of T-topology with stub/main lengths, stackup table with Zo calcs.
4. **Impedance calcs** — formulas used (Wadell/IPC-2141), trace width/spacing chosen for 40/80 Ω targets with tolerances.
5. **Channel budgets** — table of loss budget (IL in dB/in @ Nyquist 3.2 GHz), crosstalk (NEXT/FEXT) allocation, skew budget (intra-pair ≤ 2 ps, inter-byte ≤ 10 ps).
6. **Routing rules** — spacing (3W rule for DQ bytes, 5W between byte lanes), serpentine radius, via stub policy, reference plane transitions.
7. **Termination & ODT plan** — RTT settings per rank combination, VTT decap strategy.
8. **Power delivery callout** — VDDQ target 1.1 V ±3%, decoupling plan (bulk + ceramic 0.01/0.1 µF placement, target impedance ≤ 10 mΩ to 500 MHz).
9. **Simulation plan** — IBIS-AMI models to use (Micron MT60B2G8HB-48B IBIS-AMI rev 2.1), corner cases (SS/TT/FF + temp -40/+85 °C), pass/fail gates.
10. **Open risks & mitigations** — numbered list, each with owner and ECD.

## Output format
Single Markdown (.md) file, ~280–380 lines. ASCII block diagrams for stackup and topology. Tables (Markdown pipe syntax) for budgets and stackup. No external images.

## Iteration targets
1. First pass often misses skew budget decomposition — push for intra-byte / inter-byte / CMD-to-DQS skew separation with actual ps numbers, not just "match lengths."
2. Sharpen impedance calcs: add actual trace widths (e.g., 4.5 mil on L3 stripline) with sensitivity to prepreg tolerance (±0.5 mil).
3. Add explicit via stub guidance (max stub 10 mil, backdrill to 8 mil residual) tied to Nyquist harmonic content.
4. Expand crosstalk section with NEXT/FEXT coupling length limits and a numeric aggressor-victim budget (e.g., 3% NEXT, 5% FEXT).
5. Add corner-analysis matrix (process × temperature × voltage) rather than single nominal simulation.
6. Tighten termination section with RTT table for all 4 rank-population combinations (1R/1R, 1R/2R, 2R/1R, 2R/2R).

## Success criteria
- Memo references JEDEC JESD79-5B or JESD400-5B, AMD SP5 design guide, and IPC-2141/2221 where appropriate.
- Every numeric target carries units AND a tolerance (no bare "40 Ω" without ±).
- Skew budget arithmetic closes: intra-pair + inter-pair + package + DRAM ≤ total channel skew allowance.
- Impedance calculations show chosen trace geometry with a sanity check against a known calculator/formula.
- Simulation plan names specific IBIS-AMI models and spec-compliant corner combinations.
- ASCII topology diagram distinguishes main-line vs stub sections with labeled lengths.

## Scope target
For a 15-minute v1, expect: executive summary (pass/fail sketch), stackup table with approximate Zo, T-topology ASCII diagram, one channel budget table (loss + crosstalk + skew), basic ODT plan for 2 DPC, named IBIS models for simulation. Corner matrix and per-rank RTT combinations can be stubbed as TODOs with placeholders.
