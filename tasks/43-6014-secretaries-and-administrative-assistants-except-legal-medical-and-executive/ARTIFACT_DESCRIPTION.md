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

## Output format
Single Markdown file, ~2-3 pages when rendered (roughly 180-260 lines in source).

## Iteration targets
1. **Reorganize from chronological to topical** — v1 may preserve the time-stamped flow; v2 should group by workstream (IT, HR, Facilities, Fleet, Safety, Finance, Ops).
2. **Extract every action item into the action table** — ensure all commitments (e.g., "MC to escalate by 4/19", "PB to draft all-hands by 4/21", "2 more striping bids by 4/22") appear with owner and due date; none should remain buried only in prose.
3. **Distinguish decisions from discussion** — explicit "Decision:" lines for resolved items (HVAC slip accepted; no layoffs; PO deadline 4/24 firm), vs. open items in parking lot.
4. **Handle the audio gap honestly** — reconstruct the cutover-weekend debate accurately, clearly mark it as reconstructed, and put the IT-vs-Ops date conflict into open issues rather than claiming a decision.
5. **Normalize names and acronyms on first use** — e.g., "CBA" → "Collective Bargaining Agreement (CBA)"; full names on first mention, last-name-only thereafter.
6. **Redact or soften sensitive HR content** — the three accommodation requests should be referenced at an aggregate level, not by category, given broad distribution.

## Success criteria
- Every commitment in the raw notes appears in the action items table with owner and due date.
- Topics are grouped logically, not purely by timestamp.
- The audio-gap reconstruction is explicitly flagged.
- No HR-sensitive detail (specific accommodation categories) is exposed in a document distributed to 23 people.
- The cutover-weekend date conflict is in "Open Issues," not falsely resolved.
- Tone is neutral and professional; no first-person or editorial language.

## Scope target
A v1 produced in ~15 minutes should include: header block, full attendee list, a decisions-vs-discussion structure covering at least 5 of the 7 workstreams, an action items table with at least 8 entries, and a parking lot entry for the cutover-weekend conflict. Polish of cross-references, redaction nuance, and full topical reorganization is expected to come in iteration.
