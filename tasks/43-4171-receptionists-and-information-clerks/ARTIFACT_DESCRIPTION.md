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

## Example of v1 failure modes
- Writing a de-escalation script that escalates into negotiation: "I understand you're frustrated; let me see if we can work out a payment plan for your visit today" — this is clinical/billing scope, not reception scope.
- Unifying all escalations into "call security first." Weapons and active medical emergencies require 911 without delay; routing through a 7-minute Northstar response is dangerous.
- Treating HIPAA non-confirmation as a "soft" rule: "I'd rather not say whether she has an appointment." The correct stance is "I can take a message for our clinical team if you'd like."
- Assuming the security guard covers Saturday 8-12; he does not. v2 must name the fallback.
- Making the post-incident documentation template too long; receptionists won't complete it reliably if it's more than one page of fields.
- Omitting the photography-attempt scenario; it's a real past incident and has a clean response (ask person to stop; if refused, request they leave; if they don't, panic button).
- Missing the child-left-unaccompanied scenario, which overlaps with mandatory reporter concerns (route to the tenant's clinical staff, who are mandatory reporters).

## Common pitfalls to avoid
- Do not draft a "zero-tolerance" tone that forecloses de-escalation; a firm-and-warm tone de-escalates better than a scripted hard line.
- Do not write rules that require the receptionist to assess whether aggression is "real" or "just venting"; the decision matrix should be based on observable behavior (shouting, profanity, proximity, refusal to leave), not inferred intent.
- Do not expose any tenant-specific patient information to other tenants' staff by accident (e.g., a receptionist routing a Rimrock crisis through the Primary Care practice manager).
- Do not make the de-escalation script longer than can be held in working memory; receptionists in an escalation cannot read a script.
- Do not require a receptionist to be the primary 911 caller if they are physically engaged with a situation; the decision matrix should specify who calls when multiple staff are present.

## Evaluator notes (context for scoring, not for the model)
- Receptionist work is often cited as "non-iteration-worthy" because greeting-scripts and call-logs are shallow artifacts. The SOP choice here is deliberate: a multi-tenant medical plaza front desk with heterogeneous patient populations produces a rich, iteration-improvable artifact, and a well-crafted SOP is exactly the kind of document a senior receptionist contributes to as a career-development milestone.
- Cascade Ridge Medical Plaza, tenants, and incidents are fictional. The tenant mix (primary care / behavioral health / pediatric / radiology / oncology) mirrors realistic medical-office building composition. The 7-minute Northstar response time and the solo-weekend-morning coverage gap are common real-world constraints.
- The iteration arc: v1 produces a reasonable SOP with most triggers covered; v2 hardens the decision matrix to be truly 30-second scannable, correctly separates weapons/medical-emergency from verbal aggression, closes the after-hours gap, tunes tenant-specific HIPAA exchanges, and gets the de-escalation script to memorizable length.

## Elements that specifically distinguish this from a generic greeting-script artifact
- Decision matrix with multiple concurrent response paths (security, 911, clinic, panic button).
- Tenant-specific privacy rules (Rimrock absolute non-confirmation).
- Shift-dependent escalation (guard on vs. off; Saturday morning gap).
- Documented scope boundary (receptionists route, do not triage).
- Legal/regulatory references (HIPAA, OSHA workplace violence prevention, mandatory reporter routing).

## Required elements in the decision matrix
- **Weapons observed:** Call 911 immediately; press panic button; move away from line of sight; do not engage; lockdown guidance per building policy. No security-first route.
- **Physical aggression toward staff or patrons:** 911; panic button; attempt to create distance; name witnesses.
- **Verbal aggression (no physical threat):** De-escalation script; offer choice and time-limit; if unresolved, request person leave; if refusal, security (Northstar) or (after-hours) 911 non-emergency.
- **Medical emergency, conscious:** Call 911; notify nearest tenant's clinical staff; stay with patient; document.
- **Medical emergency, unconscious/unknown:** Call 911; notify clinical staff (primary care nearest by default, unless patient is identified with another tenant); do not attempt CPR unless trained and authorized.
- **Behavioral crisis suspected:** If person identifies as Rimrock patient, route discreetly to Rimrock intake using tenant-specific channel; do not confirm patient status; do not discuss with third parties.
- **Intoxicated person:** If presenting safety concern, security or 911; if not, offer chair and water; notify clinical staff of affected tenant.
- **Photography/privacy breach:** Ask person to stop; if refused, request they leave; if they don't, panic button; document.
- **Child left unaccompanied:** Stay with child; notify nearest clinical staff (mandatory reporters); attempt to contact parent via tenant records; if no resolution in 30 min, follow tenant CPS protocol (clinic-handled, not reception-handled).
- **Unauthorized area access:** Redirect; if refusal, security; camera note.

## Tenant-specific HIPAA exchange templates (minimum necessary)
- Inquirer asks whether a named person has an appointment: "I can take a message for our clinical team if you'd like" — universal baseline; never confirm or deny.
- Inquirer states they are a family member and insists: "I understand this is frustrating. For privacy reasons, I'm not able to confirm. Would you like me to pass a note to the clinical team?" — no confirmation of any kind.
- Rimrock-specific: never confirm presence, appointment, or even whether the person is a patient of any kind. If inquirer becomes aggressive, escalate per verbal-aggression path.
- Parent/guardian of minor for pediatric tenant: confirm appointment scheduling, not clinical content; route clinical questions to practice staff.

## What distinguishes this from a generic greeting-script artifact (summary)
- Decision matrix across 9+ trigger categories, not a single greeting workflow.
- Tenant-specific privacy rules with Rimrock treated most strictly.
- Shift-dependent escalation with explicit after-hours coverage.
- Receptionist scope boundary maintained (route, don't triage).
- Legal/regulatory grounding in HIPAA, OSHA, and mandatory reporter routing.

## Final sanity checks before submitting to Mirela
- Decision matrix fits on one scannable page and covers all 9 trigger categories.
- Weapons and medical emergency escalate immediately to 911 without tiered routing.
- Rimrock non-confirmation is absolute and has a sample exchange.
- After-hours (Saturday morning) gap has a named fallback.
- De-escalation script is memorizable length (ideally < 8 lines).
- Post-incident template is one-page and fills out in under 3 minutes.
