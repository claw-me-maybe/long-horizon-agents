# RAID Log — Workday HCM Go-Live Project "Project Quillstone," Cutover Window May 30–June 2, 2026

## Occupation
- **SOC:** 13-1082
- **Title:** Project Management Specialists

## Scenario
You are the PMO lead for "Project Quillstone" at Falbridge Industries, a 7,800-employee specialty-chemicals manufacturer replacing its legacy PeopleSoft HCM with Workday HCM, Payroll, Time, and Absence. The cutover is a hard-dated 4-day window (Fri May 29 1800 ET to Tue June 2 0800 ET) gated by the May 31 payroll run. You have three weeks to go-live as of the project steering committee on May 1, 2026. The Program Director, Imogene Vachss-Ortiz, has asked for an updated RAID log that she can walk the CIO and CHRO through at the May 8 gate review — the artifact that will drive "go / no-go" conversations right up to cutover.

## Inputs

**Project metadata**
- Name: Project Quillstone (Workday HCM Phase 1)
- Implementation partner: Collier-Brandt Advisory (lead PM: Nasir Elshafei)
- Budget: $9.8M; spent $8.1M YTD; remaining $1.7M
- Resources: 62 Falbridge + 38 Collier-Brandt; 24 SMEs on-call
- Module scope: HCM Core, Payroll (US only), Time, Absence (not Benefits — Phase 2)

**Current state (from last week's status report)**
- UAT Cycle 3 pass rate: 88% (target 95%)
- 47 open UAT defects: 6 Sev 1, 14 Sev 2, 27 Sev 3
- Payroll parallel run 2 of 3: $412 net-pay variance across 7,800 employees (target < $100 total)
- Cutover rehearsal #2 executed 4/24; completed in 51 hours (budget is 62)
- Integration to ADP tax filings not yet E2E tested; vendor availability limited
- Change-management training: 68% of managers have completed required course (target 95%)
- Data migration: 7,812 of 7,814 workers loaded; 2 leaves-of-absence blocked by an EIB validation

**Stakeholders**
- Executive Sponsor: CIO Ottavia Blass-Hirano
- Co-Sponsor: CHRO Renfrew Takahashi-Deen
- Business Owner: VP Total Rewards, Lea Kisselgof
- IT Ops Lead: Quigley Marquand
- Payroll Manager (DRI for May 31 run): Darnelia Pickard

**Constraints**
- No go-live delay options past June 15 (SOX-audit lock date)
- Payroll must run on May 31 regardless of system state
- CFO has capped change-orders at $150K additional through close

## Artifact specification
Live RAID log (Risks, Assumptions, Issues, Dependencies). Each entry is a structured row. Required columns:
- ID (R-###, A-###, I-###, D-###)
- Type (Risk / Assumption / Issue / Dependency)
- Description (action-oriented: what could happen or what is happening)
- Category (Technical / Resource / Schedule / Scope / Quality / Vendor / Change Mgmt / Regulatory)
- Raised date
- Owner (named individual)
- Probability (H/M/L) — risks only
- Impact (H/M/L with brief consequence statement)
- Exposure score (Prob × Impact) — risks only
- Mitigation / Response (preventive AND contingent)
- Trigger (observable condition that escalates it)
- Status (Open / In Progress / Mitigated / Closed / Escalated)
- Target resolution date
- Last updated

Plus:
- **RAID summary dashboard** — counts by status and severity, top 5 exposures, trend vs. last week
- **Decision log section** — recent steering decisions that close out RAID items
- **Go/No-Go criteria matrix** — 8–12 named criteria with current status (green/amber/red), thresholds, and DRIs

Tone: operational, terse, observable. No speculation without a named trigger.

## Output format
Markdown file containing the dashboard, the RAID table (at minimum 18 entries spanning all four types), decision log, and go/no-go criteria matrix. Target 1,600–2,100 words (a lot of it tabular).

## Iteration targets
1. v1 entries often blur issue and risk — reclassify any "risk" that has already occurred as an issue; separate the materialized event from the forward-looking exposure.
2. Mitigations commonly state only preventive steps; add contingent (what we do if it triggers) for every H-impact risk.
3. Triggers are often absent or vague ("if things get worse"); every risk needs an observable threshold (e.g., "Sev 1 count > 4 at UAT4 exit").
4. Owner column sometimes shows teams — every row needs an individual accountable.
5. Go/No-Go criteria matrix often mixes binary gates with leading indicators; split into a clear "hard gate" set and "monitor" set.
6. Dependencies often don't show the upstream owner AND the downstream dependent task; both must be visible.

## Success criteria
- Imogene could drive a 30-minute steering conversation from this artifact alone without additional prep.
- Every high-exposure risk has both a preventive and a contingent plan, with a named trigger.
- Risks vs. issues vs. assumptions vs. dependencies are correctly typed — no category confusion.
- Go/No-Go matrix shows thresholds, current status, and who makes the call, not just green/amber/red.
- Decisions recorded in the decision log resolve specific RAID IDs, not abstract topics.
- The artifact is scannable: a CIO looking for the top 3 risks in 60 seconds finds them.

## Scope target
v1 at ~15 minutes should contain: RAID dashboard with counts, at least 18 RAID entries (roughly 7 risks, 3 assumptions, 4 issues, 4 dependencies) populated with owners and target dates, a decision log with 3–4 recent decisions, and an initial go/no-go criteria matrix with 8 criteria and status. Roughly 1,100–1,400 words; full trigger/threshold calibration, contingent-plan depth, and trend analysis are iteration work.
