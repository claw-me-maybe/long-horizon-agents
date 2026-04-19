# Cross-Functional Project Kickoff Meeting Minutes — Meridian Logistics Q2 Warehouse Relocation

## Occupation
- **SOC:** 43-6014
- **Title:** Secretaries and Administrative Assistants, Except Legal, Medical, and Executive

## Scenario
Meridian Logistics (a 340-employee regional 3PL based in Toledo, OH) is relocating its main distribution warehouse from Maumee to Perrysburg between May 12 and June 28, 2026. On April 15, 2026, Operations Director Janelle Okafor convened a 90-minute cross-functional kickoff with 11 attendees (Ops, IT, HR, Facilities, Fleet, Safety, Finance, and two floor supervisors). You are Dana Reyes, the admin supporting the Operations department, and you must turn your handwritten notes plus a partial audio recording (last 18 minutes inaudible due to HVAC noise) into formal meeting minutes that will be distributed to 23 stakeholders by end-of-day April 17.

## Inputs
The model begins with the following raw materials:

**Attendee list (from Outlook invite):**
- Janelle Okafor (Ops Director, chair)
- Marcus Chen (IT Infrastructure Lead)
- Priya Balasubramanian (HR Business Partner)
- Tom Delacroix (Facilities Manager)
- Rebecca Liu (Fleet Coordinator)
- Gabriel Ortiz (Safety Officer)
- Susan Whitford (Finance Controller)
- Wes Hamadi (Floor Supervisor, Maumee)
- Ingrid Svenson (Floor Supervisor, incoming Perrysburg)
- David Nkomo (Procurement)
- Dana Reyes (admin, minute-taker)

**Your raw notes (verbatim, messy):**
```
9:02 JO opens - goal = zero-downtime cutover. Reminds everyone PO deadline for new racking = 4/24.
9:07 MC - network drops at Perrysburg pulled to 5/8. Needs 2 IT techs on-site wk of 5/11. Risk: fiber provider (Everstream) hasn't confirmed install slot. MC to escalate by 4/19.
9:14 TD - HVAC commissioning behind 6 days. Likely ready 5/20 not 5/14. JO: acceptable if cold storage stays offline til 5/25. TD to confirm w vendor Friday.
9:22 PB - 41 warehouse staff need relocation notices by 4/30 per CBA Art. 14. Drafting w legal. 3 staff have requested accommodation (disability - 1, childcare - 2). Will triage.
9:28 RO (Rebecca) - yard redesign needs striping redone. Vendor quote $18,400 from Blackline. JO pushes back, wants 2 more bids by 4/22.
9:35 GO - Safety walkthrough 5/18 required. Forklift recert for 7 operators due before move.
9:41 SW - capex tracking $1.24M against $1.4M budget. Concerned about contingency. Asked for weekly burn report starting 4/20.
9:48 WH - floor workers nervous, rumor of layoffs. JO: NO LAYOFFS planned, PB to draft all-hands comms by 4/21.
9:55 IS - needs org chart for Perrysburg finalized. PB: by 5/1.
10:02 DN - racking PO in review, vendor Steel King confirmed 6-wk lead time. Cutoff 4/24 is firm.
10:08 — audio cuts out —
[from memory]: discussed phased cutover across 3 weekends; IT wanted 6/13, Ops wanted 6/20; unresolved. Also some debate about overtime approval authority. JO said Susan would circulate revised budget by 4/24. Meeting ended ~10:31.
```

**Prior context:** You have access to the meeting invite, the project charter (dated 3/28/2026), and last week's steering committee update.

**Reference documents on file:**
- Project charter "Perrysburg DC Relocation Project," version 2.1, approved 3/28/2026 by COO Ralph Stein
- CBA Article 14 ("Facility Relocation and Reassignment"), effective 2024-01-01
- Steering committee update 4/10/2026 — flagged risks: fiber-install slot, racking lead time, forklift recert
- IT network-cutover runbook draft v0.3 (Marcus Chen, 4/12/2026)
- HR relocation comms template library (internal, last used 2022 warehouse consolidation)

**Distribution list for the minutes (23 people):**
- All 11 attendees
- COO Ralph Stein (project sponsor)
- CEO Diana Pallavi (FYI)
- General Counsel Hannah Rothko (for CBA/legal compliance notes)
- 4 additional floor supervisors (Maumee + Perrysburg)
- 2 IT deputies (for technical routing of action items)
- 3 external recipients: Everstream account rep (fiber), Steel King account rep (racking), Blackline account rep (yard striping)

**Constraint on distribution:** external recipients must receive a redacted version (HR content, internal budget figures, and personnel-specific items removed).

## Artifact specification
Produce formal meeting minutes with the following sections:
1. **Header block** — meeting title, date, time (start/end), location (hybrid: Conference Room B + Teams), chair, minute-taker
2. **Attendees** — present, absent with apologies, distribution list (non-attendees who get the minutes)
3. **Agenda recap** — 1 line per agenda item
4. **Discussion and decisions** — organized by topic, NOT chronologically. Each topic: short narrative, decisions made, dissent noted if any.
5. **Action items table** — columns: #, Owner, Action, Due date, Status (New)
6. **Open issues / parking lot** — unresolved items, including the cutover-weekend debate
7. **Next meeting** — proposed date/agenda
8. **Attachments referenced**

Tone: neutral, professional, third-person. Do not editorialize. Flag gaps where audio was lost with "[Note: portion of discussion not captured in audio; summary reconstructed from minute-taker's recollection]."

Section conventions:
- Each workstream block in "Discussion and decisions" begins with a single short paragraph of context, followed by bulleted "Decisions:" and bulleted "Open items rolled forward:".
- Action items numbered sequentially across the whole document (not per section), so they can be referenced in follow-up correspondence.
- Open issues entries carry forward a row number from the previous steering committee's parking lot where applicable.
- Attachments referenced by filename + version + date (e.g., "IT network-cutover runbook v0.3, Chen M., 2026-04-12").

## Output format
Single Markdown file, ~2-3 pages when rendered (roughly 180-260 lines in source).

If a second "external vendor" version is produced, it is a separate Markdown file (or a clearly demarcated appendix) that contains only the workstream and action items relevant to that vendor, with all internal personnel, budget, and HR content removed. Formatting should match the primary minutes; only content is scoped.

## Iteration targets
1. **Reorganize from chronological to topical** — v1 may preserve the time-stamped flow; v2 should group by workstream (IT, HR, Facilities, Fleet, Safety, Finance, Ops).
2. **Extract every action item into the action table** — ensure all commitments (e.g., "MC to escalate by 4/19", "PB to draft all-hands by 4/21", "2 more striping bids by 4/22") appear with owner and due date; none should remain buried only in prose.
3. **Distinguish decisions from discussion** — explicit "Decision:" lines for resolved items (HVAC slip accepted; no layoffs; PO deadline 4/24 firm), vs. open items in parking lot.
4. **Handle the audio gap honestly** — reconstruct the cutover-weekend debate accurately, clearly mark it as reconstructed, and put the IT-vs-Ops date conflict into open issues rather than claiming a decision.
5. **Normalize names and acronyms on first use** — e.g., "CBA" → "Collective Bargaining Agreement (CBA)"; full names on first mention, last-name-only thereafter.
6. **Redact or soften sensitive HR content** — the three accommodation requests should be referenced at an aggregate level, not by category, given broad distribution.
7. **Produce the redacted external-vendor version** — a second render suitable for Everstream/Steel King/Blackline that contains only their relevant workstream items and strips internal budget and personnel detail.

## Common pitfalls to avoid
- Including dollar amounts for items still in procurement competition (Blackline's $18,400 quote should not be shared with the other striping bidders).
- Exposing who specifically is behind schedule in a way that might be read as blame (e.g., "TD has not followed up with vendor" → better: "HVAC commissioning confirmation pending, due Friday").
- Leaving the NO LAYOFFS commitment buried in a narrative paragraph; it should be flagged prominently because it was escalated verbally by the Ops Director.
- Misattributing decisions to the wrong owner (Finance's weekly-burn-report cadence belongs to Susan, not Janelle).

## Success criteria
- Every commitment in the raw notes appears in the action items table with owner and due date.
- Topics are grouped logically, not purely by timestamp.
- The audio-gap reconstruction is explicitly flagged.
- No HR-sensitive detail (specific accommodation categories) is exposed in a document distributed to 23 people.
- The cutover-weekend date conflict is in "Open Issues," not falsely resolved.
- Tone is neutral and professional; no first-person or editorial language.
- Redacted external-vendor version, if produced, contains only the workstream relevant to that vendor.
- Cross-references (to charter section numbers, CBA articles, or steering committee update) are accurate.
- The 9:02 start time and ~10:31 end time appear in the header block with note that audio cut ~10:08.

## Scope target
A v1 produced in ~15 minutes should include: header block, full attendee list, a decisions-vs-discussion structure covering at least 5 of the 7 workstreams, an action items table with at least 8 entries, and a parking lot entry for the cutover-weekend conflict. Polish of cross-references, redaction nuance, and full topical reorganization is expected to come in iteration.

## Evaluator notes (context for scoring, not for the model)
- The minute-taker role here is archetypal for 43-6014: the admin is the only neutral party in the room capable of producing the institutional record. The iteration space is real because v1 outputs of timestamped-transcript style are the default failure mode, and the task of reorganizing into topical, action-oriented, redacted-where-appropriate minutes is exactly where a junior admin improves over the course of a year's mentoring.
- Meridian Logistics, Toledo-to-Perrysburg relocation, and all named individuals are fictional. CBA Article 14 is plausible but a fabrication. The 6-week racking lead time, the 30-day CBA notice convention, and the HVAC commissioning slip pattern are realistic.
- The document should feel like a work product Dana would actually hand Janelle at end of day Friday, ready to go to 23 recipients Monday morning.
