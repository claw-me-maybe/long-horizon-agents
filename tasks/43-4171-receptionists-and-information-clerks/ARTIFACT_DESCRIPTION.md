# Front-Desk Escalation and De-escalation Standard Operating Procedure — Cascade Ridge Medical Plaza Reception

## Occupation
- **SOC:** 43-4171
- **Title:** Receptionists and Information Clerks

## Scenario
Cascade Ridge Medical Plaza is a 5-tenant multi-specialty medical office building in Bend, OR, sharing a single ground-floor reception desk staffed by 3 receptionists in rotation. You are Jordan Ahmadi, the senior receptionist (4 years tenure), and the Plaza Operations Manager, Mirela Costea, has asked you to draft a formal front-desk escalation and de-escalation SOP by April 30, 2026. The trigger: a March 14 incident where an agitated family member of a patient shouted at a receptionist, and staff did not know whether to call security, the clinic, or 911. The SOP will be signed off by Mirela, the 5 clinic practice managers, building security vendor (Northstar Security), and posted at the desk + in the staff onboarding binder.

## Inputs

**Building tenants (and their primary patient type / vulnerability factors):**
1. Cascade Primary Care — adult family medicine, high volume (~140 visits/day).
2. Rimrock Behavioral Health — outpatient psychiatry and therapy (~45/day). Patients may be in crisis. No walk-ins permitted per their policy; reception must not disclose patient presence.
3. High Desert Pediatrics — pediatric primary care (~90/day).
4. Cascade Radiology — imaging, mostly scheduled (~60/day).
5. Pine Meadow Oncology — outpatient oncology infusion (~25/day). Patients often immunocompromised, family members often emotionally charged.

**Physical layout:**
- Single reception desk in lobby, staffed 7:00 AM - 6:00 PM M-F, 8:00-12:00 Sat.
- Panic button under desk, silent alarm to Northstar (avg response 7 min).
- Security guard on-site 10 AM - 6 PM weekdays only (stationed in east corridor).
- Two staff restrooms, one family restroom. Side corridor to Rimrock has keypad lock.
- Camera coverage: lobby only. No audio.

**Incident log (past 12 months, as provided by Mirela):**
- 4 incidents involving shouting/aggression (2 Rimrock-related, 1 Oncology family, 1 unrelated visitor).
- 1 medical emergency in lobby (syncope, Primary Care patient) — EMS called appropriately but staff reported confusion about lobby CPR readiness.
- 2 AMA situations (person left before being seen, later complained).
- 3 suspected intoxicated walk-ins, unclear whether patients or visitors.
- 1 attempted photography of other patients in waiting area (ejected, no escalation).
- 0 weapons incidents in 12 months; 2 in prior 24 months (historical context).

**Existing guidance (fragmentary, inconsistent):**
- Rimrock has a 1-page "do not confirm patient presence" card taped to desk.
- Primary Care gave staff a phone list last year; partially out of date.
- No written procedure for when to call 911 vs. security vs. a clinic practice manager.
- Staff trained informally by "whoever was there when it happened."

**Regulatory/legal context:**
- HIPAA: reception must not confirm whether a named individual is a patient. Applies to all tenants, not just behavioral health.
- OSHA: workplace violence prevention guidance for healthcare settings (general duty clause).
- Oregon mandatory reporter status does NOT apply to receptionists directly, but does to clinical staff; reception should route concerns appropriately.

## Artifact specification
Produce a formal SOP document with:

1. **Cover page / header** — Title, owner (you + Mirela), effective date proposed 2026-05-15, review cadence annual, version 1.0, distribution list.

2. **Purpose and scope** — one paragraph each.

3. **Definitions** — agitation, verbal aggression, physical aggression, medical emergency, behavioral crisis, suspicious person, AMA (against medical advice), tenant-specific terms.

4. **Decision matrix** — a table or flowchart readable in under 30 seconds: trigger → primary response → escalation path. Columns/rows should cover at minimum: verbal aggression, physical aggression (incl. toward staff vs. other patrons), medical emergency (consciousness unknown), behavioral crisis suspected, weapons observed, intoxicated person, photography/privacy breach, unauthorized area access, child left unaccompanied.

5. **Contact directory** — per tenant: practice manager name + direct line + backup; Northstar dispatch; 911 guidance; building engineering after hours.

6. **De-escalation script** — short, memorizable opening lines for agitated visitors, keyed to common triggers (wait time, insurance coverage, "I just need to see the doctor"). Stage-by-stage: greeting, acknowledging, offering choice, setting limit. Not therapy; not debate.

7. **HIPAA and privacy handling** — what never to confirm, what safe phrases to use ("I can take a message for our clinical team"), and tenant-specific rules (Rimrock non-confirmation is absolute).

8. **Post-incident documentation template** — fields: date/time, parties, trigger, actions taken, outcome, witnesses, camera reference, follow-up needed. Where it gets filed. Who reviews.

9. **Training and drill schedule** — onboarding requirements, quarterly scenario drills, annual refresh.

10. **Revision history** — table.

Tone: calm, instructional, imperative voice for actions ("Call 911 if…"). Written so a brand-new receptionist on their second day can use it. No clinical content; explicit boundary that receptionists do not triage, they route.

## Output format
Single Markdown file with tables and at least one ASCII decision flow, ~4 pages rendered (250-380 lines source).

## Iteration targets
1. **Make the decision matrix actually scannable in 30 seconds** — v1 may have a narrative; v2 is a one-page table/chart with clear rows, columns, and a single unambiguous primary action per cell.
2. **Distinguish security-callable vs. 911-only vs. clinic-handled** — v2 removes ambiguity on whether the guard, Northstar dispatch, or 911 is called for each trigger category, including the hours-when-no-guard-is-present case.
3. **Respect tenant rules properly** — Rimrock non-confirmation must be absolute; v2 includes sample exchanges for a determined walk-in demanding to know if someone is there.
4. **De-escalation script should not overreach** — staying in reception-scope: no therapeutic interventions, no debating the insurance question; boundary + choice + route.
5. **Handle the weapons case conservatively** — v1 may treat weapons and shouting on the same scale; v2 escalates weapons immediately to 911 + silent alarm + lockdown guidance, regardless of stated intent.
6. **Address the after-hours gap** — Saturday 8-12 has no guard; v2 names the fallback (direct 911, panic button, tenant manager on-call rotation) rather than leaving it silent.

## Success criteria
- A new receptionist on day two could find and execute the right action in under 30 seconds for the 9 trigger categories.
- HIPAA non-confirmation is correct and tenant-appropriate (Rimrock strictest, but universal baseline).
- Weapons scenario escalates immediately, not through the tiered process.
- After-hours and guard-absent windows are explicitly covered.
- De-escalation script is realistic — short, humane, within reception scope.
- Post-incident template captures what a practice manager needs without burdening the receptionist with clinical questions.

## Scope target
A v1 at ~15 minutes should contain: cover page, purpose, definitions (at least 6), a first-pass decision matrix covering at least 7 of the 9 trigger categories, contact directory skeleton, and a draft de-escalation script. Hardening the decision matrix into a true 30-second scannable artifact, fully resolving tenant-specific HIPAA exchanges, and closing the after-hours gap belong to iteration.
