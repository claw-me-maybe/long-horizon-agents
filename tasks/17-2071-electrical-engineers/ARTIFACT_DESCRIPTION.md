# 15 kV Protective Device Coordination Study — Cascadia Biotech Phase-2 Substation (Everett, WA)

## Occupation
- **SOC:** 17-2071
- **Title:** Electrical Engineers

## Scenario
Cascadia Biotech is commissioning Phase-2 of its Everett, WA bioprocessing campus. Snohomish PUD feeds a new 15 kV class customer-owned loop at 12.47 kV, with two 5 MVA pad-mount transformers stepping to 480Y/277V for two production buildings (B3 and B4). EE of record Samira Haddad (PE, WA #58392) at Meridian Power Engineering must deliver a protective device coordination study to the utility and to the customer's insurer (FM Global) by 2026-05-29 to support energization on 2026-06-22. Study must meet IEEE 242 (Buff Book) and IEEE 1584-2018 (arc flash) and be stamped.

## Inputs
- **Utility source:** Snohomish PUD, 12.47 kV three-phase, three-wire delta-wye, available three-phase short-circuit 8,400 A sym @ customer service point, X/R = 14.2. SLG fault 6,900 A, X/R = 9.8.
- **Customer equipment:**
  - 15 kV metal-clad switchgear (SG-1), 1200 A main bus, Eaton VCP-W vacuum breakers with Eaton EDR-5000 relays (50/51, 50/51N, 67, 86).
  - Main breaker 52M (1200 A), tie 52T, two feeders 52F1 / 52F2 to 5 MVA transformers TX-1 / TX-2.
- **Transformers (TX-1, TX-2):** 5000 kVA, 12.47 kV delta – 480Y/277 V wye, Z = 5.75% @ 55 °C rise, ONAN, NEMA TR-1, inrush 12·FLA for 0.1 s, ANSI C57.109 through-fault damage curve applies.
- **Downstream (per building):** 480 V main-tie-main switchboards with GE PowerBreak II 3200 AF/AT breaker with MicroVersaTrip Plus (LSIG), LV motor loads up to 400 HP VFD-driven.
- **Standards/refs:** IEEE 242-2001 (Buff), IEEE C37.112 (inverse-time curve), NEC 2023 §240, §450, IEEE 1584-2018 (arc flash), ANSI C57.109 (transformer through-fault), ANSI C37.06.
- **Coordination criteria:** CTI ≥ 0.30 s between upstream/downstream 51 curves at max fault; 51 curves below ANSI TX damage curve; 50 instantaneous at ≥ 1.6× TX inrush; downstream LV main selective with upstream 51.

## Artifact specification
Protective device coordination study memo with:
1. **Cover & PE seal block** — placeholder for stamp, author, date, project, rev.
2. **One-line diagram** — ASCII one-line of source → SG-1 → 52M/52T/52F1/52F2 → TX-1/TX-2 → 480 V MSB. Label device numbers, CT ratios, fault currents at each bus.
3. **System data** — source impedance (R+jX or per-unit on 10 MVA base), transformer %Z, motor contribution assumptions.
4. **Short-circuit calcs** — fault duty at each bus (3-phase and SLG) with per-unit or MVA method shown.
5. **Device inventory** — table: device tag, type, CT ratio, relay model, element list, pickup, time dial, curve type.
6. **Coordination plan (TCC) narrative** — for each upstream/downstream pair, specify:
   - Primary pickup in secondary amps and primary amps.
   - Curve type (IEEE EI, VI, MI per C37.112).
   - Time dial.
   - CTI check at the maximum fault seen by the downstream device.
   - Verification against ANSI TX damage curve (category II, 8% Z, through-fault) and inrush.
7. **ASCII TCC sketch** — axis: time (s, log) vs current (A, log @ 12.47 kV base); show at least 4 curves and damage/inrush points.
8. **Arc-flash preliminary** — IEEE 1584-2018 incident energy at SG-1 bus and LV MSB with chosen device clearing times; PPE category and working distance.
9. **Ground-fault coordination** — 50N/51N settings on feeders, NEC 230.95 compliance at 480 V service.
10. **Settings summary table** — final relay settings ready for commissioning.
11. **Conclusions & recommendations** — list any mis-coordinations or waivers.

## Output format
Single Markdown (.md) file, ~320–400 lines. ASCII one-line and TCC sketches in fenced code blocks. Markdown tables for device inventory and settings summary. Formulas inline.

## Iteration targets
1. First pass often picks relay settings without CT ratio selection justification — require CT burden/accuracy class (C200 or better) check at max fault.
2. Push for a named IEEE C37.112 curve family (EI/VI/MI) with explicit time dial and the CTI arithmetic at the max downstream fault, not "CTI looks OK."
3. Demand transformer protection hit both: (a) below ANSI damage curve across 2–50× FLA, and (b) instantaneous set above 1.6× inrush.
4. Add 50G/51G on feeders with NEC 230.95 trip time ≤ 1 s at 1200 A check.
5. Require arc-flash incident energy in cal/cm² with computed clearing time, not just "PPE 2."
6. Force the ASCII TCC to show clear curve separation at the governing fault current with annotated CTI.

## Success criteria
- Cites IEEE 242, IEEE C37.112, ANSI C57.109, IEEE 1584-2018, and relevant NEC 2023 articles.
- Short-circuit duties at each bus are computed, not assumed.
- Each coordinating pair has CTI computed at a specific fault current, ≥ 0.3 s.
- Transformer 51 curve stays under C57.109 damage curve; 50 set above inrush.
- Settings table is commissioning-ready (CT ratio, pickup in primary amps, curve, TD).
- Arc-flash calc references IEEE 1584-2018 equations/working distance and produces cal/cm² + PPE category.

## Scope target
For a 15-minute v1: ASCII one-line, fault current at SG-1 bus and 480 V MSB (simple per-unit), device inventory skeleton, one coordinating pair (52F1 vs TX-1 primary fuseless protection) with curve and CTI, approximate settings, and an arc-flash placeholder citing IEEE 1584 but with TODO for full calc. Ground-fault and downstream LV pair can be stubbed.
