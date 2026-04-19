# Change Order Package #CO-017 — Elevator Shaft Rework, Cedarhurst Medical Office Building

## Occupation
- **SOC:** 11-9021
- **Title:** Construction Managers

## Scenario
Merrick Construction is the CM-at-Risk on the Cedarhurst Medical Office Building, a $48M four-story, 94,000 sq-ft MOB outside Charlotte, NC, scheduled for substantial completion on May 28, 2027. During elevator shaft inspection on September 11, 2026, a 3" out-of-plumb deviation was identified in the north shaft (Shaft N-1) from the 2nd floor slab through the roof, which prevents KONE from installing the already-fabricated jack and car rails per shop drawings. Project Manager Luis Caballero must prepare Change Order Package #CO-017 for submission to the Owner (Piedmont Health Properties, LLC, represented by Director of Development Olivia Reyes) and the Architect (Kessler+Nomura Architects, PIC Rhonda Tan) by September 25, 2026. The package drives a request for $187,400 and 18 calendar days of schedule extension.

## Inputs
The model starts with:

- **Contract basis:**
  - CM-at-Risk with GMP of $47,950,000 (executed February 4, 2025).
  - AIA A133-2019 with A201-2017 General Conditions.
  - Current Contract Sum: $48,423,910 (GMP + 4 prior approved change orders, #CO-013, CO-014, CO-015, CO-016).
  - Current Substantial Completion date: May 28, 2027. LDs: $3,500/day after SC.
  - Elevator procurement agreement (KONE, subcontract value $1,840,000).
- **Non-conformance facts:**
  - Cause under investigation: survey control from concrete subcontractor (Piedmont Structural, PSI) reference benchmark used on the 2nd floor slab pour (March 11, 2026) was 0.5" off plumb; propagated through successive pours. ATC Surveyors (3rd-party) confirmed 3" total out-of-plumb at roof, gradient of 0.5"/floor above level 2.
  - Discovery: Shop-drawing clash identified during KONE pre-installation inspection Sept 11.
  - Effect: Rails cannot be installed without remediation; KONE requires rework of shaft walls (CMU) and slab edges between Level 2 and Level 4.
- **Proposed remediation (scope):**
  - Demo / cut existing CMU shaft walls between Levels 2-4 on affected face (approx. 380 SF per floor × 2 faces).
  - Reset plumb with new blockwork + rebuild.
  - Grind and repour slab edges at shaft penetrations (6 locations).
  - Re-shoot survey and produce as-built shaft geometry before KONE re-engages.
  - Remobilize CMU subcontractor (Skylark Masonry), concrete subcontractor (Piedmont Structural), and KONE.
- **Cost build-up (draft):**
  - Demo / rework CMU (Skylark): $52,300 (direct labor 320 hrs @ $74, mat'l $18,900, equipment)
  - Concrete grind/repour (Piedmont Structural): $41,200 (labor, mat'l, pump, finishing)
  - KONE remobilization + engineering: $38,500 (shop drawing update, remobilization, pre-install re-inspection)
  - General conditions extension (18 days × $2,850/day): $51,300
  - CM fee (stated in contract at 3.75%): $6,911
  - Subtotal: $190,211 — proposing $187,400 (rounded after negotiation with Skylark reducing labor hrs)
- **Schedule impact analysis:**
  - Shaft rework critical path: 14 working days (demo 4, CMU reset 6, concrete 3, cure+survey 1).
  - KONE installation delay: original mobilization was Oct 1; revised Oct 23 (3 weeks later due to KONE crew availability).
  - Net critical-path impact: 18 calendar days.
- **Cost responsibility question (open):** Piedmont Structural's benchmark error is plausibly a subcontractor defect, but the original surveyor's QC sign-off is in dispute; the Owner may assert CM is responsible under the contract's quality control provisions. The change order will likely be filed as a Change Directive with cost responsibility to be resolved later.
- **Current project status:** 63% complete by schedule, 65% by cost. Weather-related float burned in Q2 2026 due to heavy rain; current schedule float on critical path = 6 days.

## Artifact specification
A Change Order Package following AIA-style conventions. Sections required:
1. **Change Order Summary (Cover)** — CO #017 identification, brief description, cost delta, time delta, new Contract Sum, new Substantial Completion date, signature block layout (Owner / Architect / CM).
2. **Narrative description** — 1-2 page narrative of (a) the non-conformance, (b) discovery, (c) required remediation, (d) reason for the change, (e) position on cost responsibility (written to preserve the CM's rights without prejudicing the Owner's ability to backcharge).
3. **Cost breakdown** — detailed schedule of values by subcontractor + CM fee + GCs. Conforms to AIA G701/G702-style detail.
4. **Backup documentation list** — itemized list of attached backup (subcontractor proposals, labor certified payroll, material invoices, equipment rate sheets, ATC survey report, KONE field report). Even if not attached, list what's referenced.
5. **Time Impact Analysis (TIA)** — baseline schedule fragnet excerpt showing critical path before and after. 18-day extension justified with activity-level logic, not just a claim.
6. **Schedule fragnet narrative** — activity-by-activity sequence for the 14 working days of rework, with predecessor/successor logic and resource constraints (KONE availability).
7. **Quality & re-acceptance plan** — re-survey criteria, re-inspection by KONE before reinstatement, hold points.
8. **Reservation of rights language** — standard AIA reservation to preserve Owner's and CM's positions on root cause, indemnification, subcontractor backcharge, and warranty.
9. **Risk notes** — latent condition discovery risk (what if 3" isn't the extent?), weather risk during the rework window (exterior wall exposure), trade stacking risk for other MEP work adjacent to the shaft.

Tone: formal, contract-aware, precise. Written to be defensible in potential dispute while preserving working relationship with Owner and Architect.

## Output format
Markdown document formatted as a Change Order Package, 6-9 pages rendered. Must include: Cover sheet, cost breakdown table, schedule fragnet table (or text representation), backup list, and contract-language snippets for reservation of rights. Structured so that it could be transposed directly into AIA G701 + G702 formats.

## Iteration targets
1. **Fix the narrative cost-responsibility position** — v1 often either admits fault or blames the subcontractor outright. Iterate to the careful CM-at-Risk position: describe facts, note open root-cause investigation, proceed under Change Directive with cost to be resolved, reserve rights.
2. **Make the TIA defensible** — v1 often claims 18 days with a sentence. Iterate to a fragnet with named activities, durations, predecessors, and a critical-path demonstration. Must explain why the 3-week KONE remobilization doesn't just add as pure float but affects CP.
3. **Tighten the cost buildup** — v1 may round or bundle. Iterate to line-item granularity with labor hours × rate, material quantities × unit cost, equipment rates, and CM fee correctly calculated at 3.75% of direct cost (not total).
4. **Strengthen the backup documentation list** — v1 may list "subcontractor quotes." Iterate to: Skylark Masonry Proposal #SM-6621 dated 9/18/26; Piedmont Structural Change Proposal CP-14 dated 9/19/26; ATC Surveyors Report ATC-2026-0911 dated 9/14/26; KONE Field Deficiency Report KDR-N1-0911.
5. **Add risk language about latent extent** — v1 may claim 3" is fully bounded. A better version notes the possibility that survey of Level 1 (below the assumed point of origin) could reveal additional out-of-plumb, and includes a contingency/hold for additional scope if discovered.
6. **Clarify new Substantial Completion date math** — v1 may say "+18 days." Iterate to name the new SC date (May 28, 2027 + 18 cal days = June 15, 2027), note LD implication, and reference what this does to the 6-day remaining float.

## Success criteria
(For evaluator use only.)
1. Cost breakdown lines sum to the CO total ($187,400 ± $2,000 with rounding note) with correct CM fee calculation.
2. Schedule extension is supported by an activity-level fragnet with named durations and predecessors totaling the claimed critical-path impact.
3. Cost-responsibility language explicitly reserves rights and avoids pre-admitting fault; proceeds as a Change Directive pending root-cause resolution.
4. New Substantial Completion date is stated (calendar date), and the LD impact ($3,500/day) is acknowledged in the time-extension justification.
5. Backup documentation list names specific documents (dates, numbers) not generic "subcontractor quotes."
6. Latent-extent risk (further investigation of Level 1 or below) is addressed explicitly with a contingency or hold.

## Scope target
A v1 at ~15 minutes should contain: cover summary with cost and time delta; cost breakdown table with the 5 major cost categories and CM fee; a narrative paragraph describing the non-conformance and remediation; a time-impact statement with the 18-day claim (even if supported by only a paragraph, not a fragnet); a backup document list (even if generic); and reservation-of-rights boilerplate. Full fragnet detail, Piedmont Structural/Skylark proposal references, and risk language polish are iteration targets.
