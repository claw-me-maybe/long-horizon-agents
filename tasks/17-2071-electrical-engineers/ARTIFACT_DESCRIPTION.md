# 15 kV Protective Device Coordination Study — Cascadia Biotech Phase-2 Substation (Everett, WA)

## Occupation
- **SOC:** 17-2071
- **Title:** Electrical Engineers

## Scenario
Cascadia Biotech is commissioning Phase-2 of its Everett, WA bioprocessing campus.
Snohomish PUD feeds a new 15 kV class customer-owned loop at 12.47 kV, with two 5 MVA
pad-mount transformers stepping down to 480Y/277 V for two production buildings (B3 and B4).
EE of record Samira Haddad (PE, WA #58392) at Meridian Power Engineering must deliver a
PE-stamped protective device coordination study (PDCS) to the utility and to the customer's
property insurer (FM Global) by 2026-05-29 to support energization on 2026-06-22. The study
must comply with IEEE Std 242 (Buff Book), IEEE C37.112, ANSI C57.109 (through-fault),
IEEE 1584-2018 (arc flash), and NEC 2023. A pre-submittal review with Snohomish PUD's
protection engineer Marcus Liu is scheduled for 2026-05-12.

## Inputs

### Utility source
- Nominal voltage: 12.47 kV, three-phase, three-wire delta primary / grounded-wye on
  customer side.
- Available three-phase short-circuit at service point: **8,400 A symmetrical**, X/R = 14.2.
- Available SLG fault at service point: **6,900 A**, X/R = 9.8.
- Utility protection upstream: recloser R-4912 on feeder, TCC curve Cooper KPE.
- Service entrance metering: PUD current transformers 600:5 multi-ratio.

### Customer 15 kV switchgear (SG-1)
- Construction: NEMA metal-clad, 15 kV, 95 kV BIL.
- Main bus: 1200 A continuous, 25 kA symmetrical three-phase short-circuit rating.
- Breakers: Eaton VCP-W vacuum, 1200 A, with Eaton EDR-5000 multifunction relays.
- Active elements: 50, 51, 50N, 51N, 67, 86.
- Breaker tags: 52M (main), 52T (tie), 52F1 (feeder to TX-1), 52F2 (feeder to TX-2).
- CT ratios: main 1200:5 (C400); feeders 600:5 (C400); neutral 300:5 (C200).

### Transformers TX-1 and TX-2
- Rating: 5000 kVA ONAN, 12.47 kV delta primary, 480Y/277 V wye secondary, 55 °C rise.
- Impedance Z: 5.75 % on self-cooled base.
- Inrush: 12 × FLA for 0.1 s (typical for dry-type liquid-filled distribution class).
- Primary FLA: 5,000,000 / (√3 · 12,470) = 231.5 A.
- Secondary FLA: 5,000,000 / (√3 · 480) = 6,014 A.
- Through-fault damage curve: ANSI C57.109 Category II (500–5,000 kVA single-phase
  equivalent; three-phase Category III at 5 MVA but operating per Category II per IEEE
  242 conservative application).

### Downstream 480 V switchboards (MSB-B3, MSB-B4)
- Configuration: main-tie-main.
- Main breakers: GE PowerBreak II 3200 AF / 3200 AT, MicroVersaTrip Plus LSIG.
- Largest downstream motor: 400 HP VFD-driven chilled-water pump.
- Motor contribution on 480 V bus: ≈ 4 × FLA (IEC 60909 subtransient).

### Coordination criteria
- CTI (Coordination Time Interval): ≥ **0.30 s** between any two time-overcurrent (51)
  curves evaluated at the maximum fault current seen by the downstream device.
- Transformer 51 primary curve must sit below ANSI C57.109 through-fault damage curve
  across 2×–50× FLA.
- Instantaneous (50) pickup on transformer primary must be set above 1.6 × inrush
  magnitude.
- NEC 230.95 ground-fault protection on 480 V service: maximum setting 1,200 A, maximum
  clearing time 1 s at 3,000 A.

### Standards
- IEEE Std 242-2001 (R2007) — Buff Book.
- IEEE C37.112 — standard inverse-time characteristic curves.
- ANSI C57.109 — transformer through-fault protection.
- IEEE 1584-2018 — arc-flash incident energy calculation.
- ANSI C37.06 — preferred breaker ratings.
- NEC 2023 — Articles 240, 250, 450.
- NFPA 70E-2024 — electrical safety in the workplace (PPE tables).
- IEEE Std 141 (Red Book) for power distribution planning inputs.

### Fault X/R and asymmetry handling
- Use X/R of 14.2 at SG-1 to compute first-cycle asymmetrical fault via ANSI C37.010
  multiplier (≈ 1.27 at X/R = 14, 0.5-cycle).
- At 480 V MSB, assume local motor X/R = 6; asymmetrical multiplier ≈ 1.12 at
  0.5 cycle per ANSI C37.010.

### Pickup and time-dial candidates (for the study to evaluate)
- 52M (SG-1 main, 1200:5 CT): pickup ≈ 80 % of bus FLA, curve EI (extremely inverse),
  TD candidate range 1.0–3.0.
- 52F1/52F2 (feeder to transformer, 600:5 CT): pickup ≈ 1.25 × TX primary FLA,
  curve EI, TD candidate 0.5–1.5.
- 50 instantaneous on feeder: ≥ 1.6 × inrush (≥ 1.6 · 12 · 231.5 = 4,445 A primary).
- LV main (GE PowerBreak II with MicroVersaTrip Plus):
  LT pickup 100 % of frame, ST pickup 4–6 × LT, INST 10× frame.

### Asymmetrical fault for arc-flash bolted-fault input
- Per IEEE 1584-2018, use bolted three-phase fault current at each bus.
- 480 V MSB fault duty includes motor contribution (~4 × FLA × 0.3 decrement at
  3 cycles).

## Artifact specification
A PE-stamped protective device coordination study with the following numbered sections:

1. **Cover & PE seal block** — stamp placeholder, author, date, project, rev, distribution.
2. **One-line diagram** — ASCII one-line showing utility source → SG-1 bus → 52M / 52T /
   52F1 / 52F2 → TX-1 / TX-2 → 480 V MSB-B3 / MSB-B4. Each bus labeled with voltage and
   fault duty. CT ratios shown on breakers. Relay device numbers shown next to each
   breaker.
3. **System data** — source impedance expressed in per-unit on a 10 MVA base; transformer
   per-unit impedance; motor contribution assumption.
4. **Short-circuit calculations**
   - Three-phase and SLG fault duty at SG-1 bus.
   - Three-phase and SLG fault duty at 480 V MSB bus (include motor contribution).
   - Calculation method (per-unit or MVA) shown with arithmetic.
5. **Device inventory** — table: device tag, type, CT ratio, relay model, active elements,
   pickup, time dial, curve type.
6. **Coordination plan (narrative)** — for each upstream/downstream pair:
   - Primary pickup in secondary and primary amps.
   - Curve family (IEEE C37.112 EI / VI / MI) with justification.
   - Time dial.
   - CTI check at the maximum fault seen by the downstream device.
   - Verification of transformer 51 curve vs ANSI C57.109 damage curve and inrush.
7. **ASCII TCC sketch** — axis: time (log seconds) vs current (log amperes at the 12.47 kV
   base). Show at least four curves (utility recloser, 52M, 52F1, TX-1 primary) plus
   C57.109 damage curve and inrush point.
8. **Arc-flash preliminary (IEEE 1584-2018)**
   - Incident energy at SG-1 bus using the chosen 52M clearing time.
   - Incident energy at 480 V MSB bus using the chosen LV main clearing time.
   - Working distance 36 in for MV, 18 in for LV.
   - PPE category per NFPA 70E 2024.
9. **Ground-fault coordination** — 50N / 51N settings on feeders; NEC 230.95 compliance
   check at 480 V service with computed clearing time at 3,000 A.
10. **Final settings summary table** — commissioning-ready values for every device (CT
    ratio, pickup primary amps, curve, time dial, instantaneous pickup).
11. **Conclusions, recommendations, and waivers** — any mis-coordinations, recommended
    re-sequences, or approved exceptions.
12. **Appendix A** — hand calc of C57.109 damage curve anchor points for TX-1.

## Output format
Single Markdown (.md) file, approximately 320–400 lines. ASCII one-line and ASCII TCC
sketches inside fenced code blocks. Markdown pipe-syntax tables for the device inventory
and settings summary. Formulas inline
(e.g., `Z_pu = (Z%/100) · (MVA_base / MVA_xfmr)`).

## Iteration targets
1. First pass often selects relay settings without justifying CT ratio and accuracy class
   — require a CT burden / accuracy check (C200 or better) at maximum fault, and confirm
   CT is not saturated.
2. Push for a named IEEE C37.112 curve family (EI / VI / MI) with an explicit time dial
   and the CTI arithmetic at the maximum downstream fault, not a qualitative "CTI looks
   OK."
3. Demand that transformer protection hit both criteria: (a) the 51 curve sits below the
   ANSI C57.109 damage curve across 2×–50× FLA, and (b) the 50 instantaneous is set
   above 1.6 × inrush.
4. Add 50G / 51G on feeders and a NEC 230.95 check with a numeric trip time ≤ 1 s at
   3,000 A.
5. Require the arc-flash incident energy in cal/cm² with the computed clearing time,
   not just "PPE 2."
6. Force the ASCII TCC to show clear curve separation at the governing fault current
   with annotated CTI values.

## Success criteria
- Cites IEEE Std 242, IEEE C37.112, ANSI C57.109, IEEE 1584-2018, and relevant NEC 2023
  articles by number.
- Short-circuit duty at each bus is computed explicitly, not assumed.
- Each coordinating pair has a CTI computed at a specific fault current and meets
  CTI ≥ 0.30 s.
- Transformer 51 curve stays under the C57.109 damage curve; the 50 is above inrush.
- Settings table is commissioning-ready (CT ratio, pickup in primary amps, curve family,
  time dial).
- Arc-flash calc references IEEE 1584-2018 equations and working distance and produces
  incident energy in cal/cm² along with PPE category.

## Scope target
For a 15-minute v1: ASCII one-line, fault current at SG-1 bus and 480 V MSB (simple
per-unit), device inventory skeleton, one coordinating pair (52F1 vs TX-1 primary) with
curve family and CTI at max fault, approximate settings, and an arc-flash placeholder
citing IEEE 1584-2018 but with a TODO for the full incident-energy calc. Ground-fault
and the downstream LV pair may be stubbed.
