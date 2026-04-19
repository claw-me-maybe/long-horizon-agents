# AML Sanctions-Screening Risk Assessment — Tesselfold Payments, Q2 2026

## Occupation
- **SOC:** 13-1041
- **Title:** Compliance Officers

## Scenario
Tesselfold Payments, a US-registered MSB and FinCEN-registered money transmitter operating in 46 states with $18.4B in annual payment volume, received a "matters requiring attention" letter from its primary federal banking partner (Ridgebrook Trust, NA) on March 28, 2026. The letter cited gaps in Tesselfold's real-time sanctions screening after two alerts on an OFAC-listed Belarusian intermediary were auto-cleared by the vendor's fuzzy-match engine in January. You are the BSA Officer; the Board Audit Committee has asked for a formal AML/OFAC sanctions-screening risk assessment and remediation memo by June 10, 2026. The bank partner has threatened to exit the relationship if gaps are not closed by Q3.

## Inputs

**Regulatory context**
- 31 CFR Part 1022 (MSB obligations)
- OFAC 50% Rule; sectoral sanctions (SDN, SSI, CAPTA, NS-PLC lists)
- FFIEC BSA/AML Exam Manual, "OFAC Compliance Program" section (2021 update)
- FinCEN Geographic Targeting Orders in effect (including the 1/15/26 crypto-ATM GTO)

**Internal data (provided)**
- Screening vendor: ClarionWatch v4.2; fuzzy-match threshold 85%; list refresh cadence T+1
- Q1 2026 screening volume: 42.1M transactions screened; 31,208 alerts generated; 812 escalated; 14 SAR-filed
- Two missed hits (Jan 14 and Jan 22, 2026): both involved transliterated Cyrillic names; ClarionWatch scored 79% and 81%
- Last AML independent review (3rd party, Berenger & Duralt LLP): dated 9/30/2025; 6 open findings, 2 medium-rated
- Current sanctions-screening policy version 3.1 (10/1/2024)
- Q1 2026 new-customer onboarding: 94,200; 18% from medium/high-risk jurisdictions per FATF list

**Personnel**
- BSA Officer: You (reports to CCO Pell Tiverton)
- Sanctions analyst team: 6 FTE (1 lead, 5 analysts), reviewing alerts 24x7 in two pods
- Q1 2026 average alert-to-disposition time: 41 hours (SLA is 24)

**Constraints**
- Board wants a funded remediation plan ≤$1.4M (capex+opex, 2026)
- No new staff headcount in 2026 without CEO approval
- Ridgebrook Trust wants weekly status updates until remediation is closed
- Parent company considers ClarionWatch strategic; ripping it out is politically difficult

## Artifact specification
Combined risk assessment + remediation memo. Required sections:
1. **Memo header and privilege mark** — "Privileged & Confidential — Attorney-Client Privileged / Attorney Work Product"
2. **Executive summary** — max 200 words; residual risk rating and recommendation
3. **Scope and methodology** — period covered, risk factors considered (product, geography, customer, channel), data sources
4. **Inherent risk assessment** — scored by product, geography, customer, channel; rationale per score
5. **Controls assessment** — mapped to FFIEC OFAC expectations: governance, risk assessment, internal controls, testing/audit, training; include a controls-maturity view
6. **Gap analysis** — specific findings tied to the January 2026 incidents and the independent review; severity-rated
7. **Residual risk rating** — after controls; explain the residual-rating methodology
8. **Remediation plan** — each gap → action → owner → target date → status metric → budget
9. **Governance and reporting** — escalation paths, MI/KRI dashboard, Board reporting cadence
10. **Appendices** — list of regulations cited, vendor config table, alert volumetrics

Tone: formal, regulator-ready, factual. No hedging verbs where findings are supported; clear calls where not.

## Output format
Markdown memo formatted for Board Audit Committee package. Target 2,500–3,400 words including tables.

## Iteration targets
1. v1 inherent-risk scores are typically narrative; convert to a visible matrix (product × geography) with scores and rationale.
2. Controls maturity is often assessed against "industry best practice" rather than the FFIEC manual directly — cite the specific FFIEC chapter and sub-heading per control.
3. Gap remediation items often lack measurable exit criteria; every action should state what "done" looks like (e.g., "fuzzy-match threshold A/B tested against 2-year hit history; false negatives < 0.5%").
4. The $1.4M budget is usually implicitly allocated; present an explicit cost table by workstream.
5. Residual risk should show both a dimension-level view and an enterprise rating, with an explanation of the aggregation method.
6. Consider whether to recommend retaining ClarionWatch with config changes vs. layering a secondary screening engine; state the recommendation and rationale, not both options.

## Success criteria
- An examiner could trace every finding to specific data and regulatory expectation.
- The residual risk rating is supported by the controls assessment — no inconsistencies between sections.
- Remediation actions are specific, owned, dated, measurable, and budget-allocated.
- The memo addresses the two January 2026 incidents directly: root cause, scope of lookback, and preventive control.
- Governance section shows a functioning escalation path (BSA Officer → CCO → Board), including how the incidents reached the Board.
- Tone is appropriate for regulator/Board distribution: precise, no marketing language, privilege preserved.

## Scope target
v1 at ~15 minutes should contain: privilege-marked header, exec summary with preliminary residual rating, methodology, inherent-risk matrix (4 factors, populated), controls assessment against 5 FFIEC pillars with maturity ratings, gap analysis enumerating at least 6 gaps, remediation table skeleton with owners and target dates, governance section with reporting cadence. Roughly 1,600–2,000 words; detailed budget table, KRI dashboard design, and appendices are iteration work.
