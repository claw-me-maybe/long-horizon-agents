# Solution Design Brief: Northstar Manufacturing Cloud QMS and Shop-Floor Integration Proposal

## Occupation
- **SOC:** 41-9031
- **Title:** Sales Engineers

## Scenario
You are the lead Sales Engineer at Meridian Stack, a mid-market SaaS vendor that sells quality-management and production-visibility software to discrete manufacturers. Northstar Manufacturing, a 430-employee contract manufacturer in Ohio, is evaluating a replacement for a brittle mix of spreadsheets, email approvals, and an aging on-prem MES add-on. Their VP of Operations, Carla Medina, asked for a written technical proposal and a live demo plan before the final commercial review on Friday, May 8, 2026. The buying committee includes operations, IT, quality, and finance. Your task is to produce a concrete solution design that proves Meridian Stack can connect to Northstar’s existing systems, support their compliance needs, and launch a pilot in one plant within 30 days.

The deal is at risk if the proposal sounds hand-wavy. Northstar wants a plan they can forward internally without additional interpretation. You need to show the recommended architecture, implementation phases, security posture, assumptions, and a demo flow that maps directly to their use cases: electronic deviation intake, approval routing, and shop-floor event visibility.

## Inputs
The model starts with:

- **Northstar environment**
  - ERP: Epicor Kinetic 2024 on Azure-hosted SQL.
  - MES: legacy on-prem system at Plant 2 only.
  - Identity: Microsoft Entra ID, SSO required for internal users.
  - Data volume: about 1,200 production orders per week; 80 to 120 quality events per month.
  - Deployment preference: cloud-first, but plant-floor downtime windows are limited to Sunday 2:00 a.m. to 6:00 a.m. ET.

- **Core requirements from Medina’s RFP note**
  - Replace spreadsheet-based deviation and CAPA tracking.
  - Integrate with Epicor for work orders, item master, and customer-specific quality requirements.
  - Sync selected shop-floor events from the MES to quality records within 15 minutes.
  - Support role-based approvals, audit history, and immutable change logs.
  - Go live with one pilot line at Plant 1 first, then expand to Plant 2 after validation.

- **Meridian Stack product facts**
  - Cloud QMS application with deviation, CAPA, supplier nonconformance, and document control modules.
  - REST API plus webhook support.
  - Standard connectors for Epicor Kinetic and Microsoft Entra ID.
  - Optional edge relay for on-prem MES polling when outbound-only network access is required.
  - Security: SOC 2 Type II, TLS 1.2+, AES-256 at rest, configurable retention policies, customer-managed export.
  - Implementation teams typically complete a single-plant pilot in 4 to 6 weeks if source-system access is available.

- **Commercial / delivery constraints**
  - Northstar wants a pilot proposal that stays within a 6-week evaluation window.
  - IT will reject any design that requires inbound firewall openings at the plant.
  - Quality wants e-signatures, audit trails, and read-only history for closed records.
  - Finance wants a rough rollout order-of-magnitude estimate, but this artifact should not become a full pricing proposal.

## Artifact specification
Create a written solution design brief that a Sales Engineer could send to the account team after discovery and before the final commercial proposal. The artifact should be practical and implementation-oriented, but still readable by non-technical stakeholders. Required sections, in order:

1. **Title and one-paragraph purpose statement** - identify the customer, the pilot scope, and the decision this document supports.
2. **Current-state summary** - brief description of Northstar’s process pain points and system landscape, using only facts from the inputs.
3. **Recommended solution overview** - describe the proposed cloud QMS deployment at a high level, including which modules are in scope for v1 and which are explicitly out of scope.
4. **Architecture diagram in words** - explain the flow between Epicor, the cloud QMS, Entra ID, and the MES/edge relay. This can be prose or a simple ASCII block diagram, but it must be concrete.
5. **Integration plan** - list the main data objects and sync directions, including work orders, item master, users/roles, deviations, approvals, and shop-floor events.
6. **Security and compliance notes** - explain authentication, auditability, retention, outbound-only networking, and how the system supports quality-regulated workflows.
7. **Pilot implementation plan** - 3 phases with rough timing, owner assumptions, and what Northstar must provide to start.
8. **Demo script** - a step-by-step 10- to 12-minute demo flow that shows intake, approval, escalation, and visibility of a shop-floor event.
9. **Risks / assumptions / dependencies** - capture the main items that could delay the pilot, such as data access, MES API limitations, and validation timing.
10. **Next steps** - end with a concrete ask for the technical review meeting and a pilot kickoff checklist.

Tone: crisp, practical, and confidence-building. It should sound like a competent Sales Engineer who can translate discovery into an implementable plan. Avoid generic marketing language, deep product fluff, and pricing-heavy prose. The brief should make clear what is configured now versus what is a future phase.

## Output format
Markdown document, roughly 4 to 6 rendered pages. Use short headings, bullets, and at least one simple architecture table or ASCII flow if that makes the integration path easier to follow. The demo script should be easy to hand to an AE or SE for rehearsal. The document should be suitable for export to PDF and internal circulation.

## Iteration targets
1. **Make the architecture executable.** v1 often says “integrates with ERP and MES” without naming the direction or trigger. Iterate so each system has a specific role, sync direction, and timing window.
2. **Separate v1 pilot scope from later expansion.** v1 tends to blur the first plant pilot with the full rollout. Iterate so Plant 1, Plant 2, and any future supplier portal work are clearly distinguished.
3. **Write the demo like a workflow, not a feature list.** v1 often lists features in isolation. Iterate so the demo script follows one deviation from intake through approval to audit trail, with one shop-floor event included.
4. **Surface the implementation risks early.** v1 may bury the hard parts. Iterate so network constraints, MES polling limitations, and validation dependencies are explicit, not hidden in a footnote.
5. **Keep compliance concrete.** v1 often says “SOC 2 and audit logs” generically. Iterate so the brief names authentication, record retention, immutable history, and e-signature handling in plain terms.
6. **Add a pilot success definition.** v1 may not define what Northstar will accept at the end of the pilot. Iterate so success criteria are measurable and tied to a decision to expand.

## Success criteria
(For evaluator use only.)
1. The document names the customer, pilot scope, and decision being supported within the first paragraph.
2. The recommended solution clearly states what is in scope for v1 and what is deferred.
3. The integration plan identifies at least four concrete objects or events and the direction of data flow for each.
4. The demo script is ordered, time-boxed, and shows a realistic quality workflow from intake to approval and audit history.
5. The security and compliance section addresses SSO, audit trail, retention, and outbound-only networking.
6. The implementation plan includes phases, approximate timing, and the customer inputs required to start.
7. The document includes risks or assumptions that a real SE would need to manage before kickoff.

## Scope target
A v1 at about 15 minutes should produce:
- A customer-specific title and purpose statement.
- A short current-state summary of the ERP, MES, identity, and process pain points.
- A recommended solution overview with module scope for the pilot.
- A basic architecture explanation, even if it is only prose.
- A short integration list covering Epicor, Entra ID, and the MES or edge relay.
- A simple 3-phase pilot plan.
- A demo script with 4 to 6 steps.
- A brief risks / assumptions section.

Iteration can improve:
- A clearer boundary between pilot and rollout phases.
- More explicit data-field mapping.
- A stronger acceptance-definition section for the pilot.
- A more polished diagram or table format.
- Tighter wording for the demo to make it easier to rehearse live.
