# Requirements & System Design Doc: Unified Patient Intake at Northcrest Pediatric Group

## Occupation
- **SOC:** 15-1211
- **Title:** Computer Systems Analysts

## Scenario
Northcrest Pediatric Group operates 11 clinics across Ohio and runs three incompatible intake flows (Epic-integrated at the flagship Columbus location, a paper packet at six suburban offices, and a custom Jotform at four acquired practices). COO Dr. Anand Srivastava has committed $640K of 2026 capex to unify intake by Q4. You (the analyst) must deliver a system requirements & design document by May 15, 2026 that product engineering (lead: Clara Benavides) can hand to a build team. The artifact must translate clinic workflow into system specs, not write code.

## Inputs
- Interviews conducted 2026-03-18 to 2026-04-02 with: 4 front-desk staff, 2 clinic managers, compliance officer (HIPAA), billing lead, 3 pediatricians.
- Current-state pain points documented: duplicate data entry (avg 7 min/patient), 14% insurance verification errors, vaccination history lost in 23% of cross-location visits.
- Constraints: HIPAA + Ohio HB 7 (parental consent for minors >13 on behavioral health), Epic FHIR R4 integration (read/write), billing via Waystar API, SSO via Okta.
- Annual volume: ~38,000 new-patient intakes, ~180,000 return visits, 68% Medicaid mix.
- Known exclusions: the system does NOT replace Epic EHR; it replaces only the intake funnel and feeds Epic.

Sample problem user story (raw from interview): "When a family with 3 kids moves from our Dayton office to Columbus, front desk rekeys insurance, allergies, and vaccine history three times. If it's flu season, that's 25 minutes before the first kid sees a nurse."

## Artifact specification
A **Business & System Requirements Document (BRD/SRS hybrid)** with these H2 sections in order:

1. **Executive summary** — problem, scope, out-of-scope, target go-live (Q4 2026).
2. **Stakeholders & RACI** — named roles with responsibilities.
3. **Current-state process map** — as-is flow for each of the 3 intake variants, with cycle times.
4. **Future-state process map** — unified to-be flow, swim-laned across patient, front-desk, clinical, billing.
5. **Functional requirements** — numbered FR-### with priority (MoSCoW). At least 20 requirements covering: registration, insurance eligibility, consent capture, vaccine reconciliation, prior-auth, sibling linking, EHR sync.
6. **Non-functional requirements** — NFR-### covering performance (p95 page load <2s on 4G), availability (99.5%), security (HIPAA Technical Safeguards §164.312), accessibility (WCAG 2.2 AA), i18n (English + Spanish + Somali — Columbus demographic).
7. **Data model** — ER diagram (mermaid) for core entities: Patient, Guardian, Insurance, Consent, Encounter, VaccineRecord.
8. **Integration map** — sequence diagrams for: Epic FHIR Patient $match, Waystar eligibility (270/271), Okta SSO, consent e-signature via DocuSign.
9. **User roles & permissions matrix** — who can do what (front-desk, nurse, MD, billing, parent-portal user).
10. **Acceptance criteria** — testable Given/When/Then for top 10 FRs.
11. **Risks & assumptions** — with owner and mitigation.
12. **Phased rollout plan** — pilot clinic, success gate, rollout order by volume.

## Output format
Single `.md` file, ~380 lines. Must include at least 2 mermaid diagrams (flow + ER) and one table of FRs.

## Iteration targets
1. Tighten vague requirements ("system should be fast") into measurable NFRs with thresholds.
2. Add the vaccine-reconciliation FR: specify how the system merges CDC IIS data + Epic immunization records + parent-reported, including conflict resolution rules.
3. Expand the consent sub-flow to handle Ohio HB 7 (minor age-gating) with explicit decision tree.
4. Add an integration sequence diagram for the Waystar 270/271 eligibility flow including timeout and fallback behavior.
5. Convert the risk register from prose to a scored table (likelihood x impact) with named owner per risk.
6. Add acceptance criteria in Gherkin form for the top 10 FRs.

## Success criteria
- Every FR is testable (has a verifiable pass/fail condition, not "support X").
- Current-state vs future-state maps are distinct and the delta is explicit.
- HIPAA technical safeguards are mapped to specific NFRs (not hand-waved).
- Data model shows cardinalities (1-to-many, etc.) and at least one consent/version pattern for audit.
- Rollout plan has a go/no-go gate with numeric success criteria (e.g. "intake time <4 min p50 at pilot clinic").
- No implementation decisions (no "use React" or "store in Postgres") — this is a specification, not a design-build.

## Scope target
V1 at ~15 min: executive summary, stakeholder list, current-state prose for one variant, 8-10 FRs, 3-5 NFRs, a skeletal ER diagram, and a one-paragraph rollout plan. Integration sequence diagrams, Gherkin ACs, and scored risk register arrive later.
