# Solution Design Brief: Northstar Manufacturing Cloud QMS and Shop-Floor Integration Proposal

## Occupation
- **SOC:** 41-9031
- **Title:** Sales Engineers

## Scenario
You are the lead Sales Engineer at Meridian Stack, a mid-market SaaS vendor that sells quality-management and production-visibility software to discrete manufacturers. Northstar Manufacturing, a 430-employee contract manufacturer in Ohio, is evaluating a replacement for a brittle mix of spreadsheets, email approvals, and an aging on-prem MES add-on. Their VP of Operations, Carla Medina, asked for a written technical proposal and a live demo plan before the final commercial review on Friday, May 8, 2026. The buying committee includes operations, IT, quality, and finance. Your task is to produce a concrete solution design that proves Meridian Stack can connect to Northstar's existing systems, support their compliance needs, and launch a pilot in one plant within 30 days.

The deal is at risk if the proposal sounds hand-wavy. Northstar wants a plan they can forward internally without additional interpretation. You need to show the recommended architecture, implementation phases, security posture, assumptions, and a demo flow that maps directly to their use cases: electronic deviation intake, approval routing, and shop-floor event visibility.

## Inputs
The model starts with:

- **Northstar environment**
  - Plants: Plant 1 (Dayton, OH — 260 employees, 4 production lines, new Kinetic install); Plant 2 (Mansfield, OH — 170 employees, 3 production lines, legacy MES).
  - ERP: Epicor Kinetic 2024 on Azure-hosted SQL. Primary integration surface: Epicor REST services 2.0.
  - MES: legacy on-prem "ProdMon 4.7" at Plant 2 only; outbound polling available over HTTPS to a shop-floor historian. No inbound access permitted.
  - Identity: Microsoft Entra ID, SSO required for internal users; SCIM provisioning available.
  - Data volume: about 1,200 production orders per week; 80 to 120 quality events per month; ~14,000 finished-goods SKUs in the item master.
  - Deployment preference: cloud-first, but plant-floor downtime windows are limited to Sunday 2:00 a.m. to 6:00 a.m. ET.
  - Compliance scope: ISO 9001 certified; a subset of Plant 1 lines (medical-device sub-assembly customer) operates under ISO 13485 requirements.
  - Key users: ~45 quality engineers and line supervisors expected on the system day-one; ~180 shop-floor operators as occasional deviation-reporters.

- **Core requirements from Medina's RFP note**
  - Replace spreadsheet-based deviation and CAPA tracking.
  - Integrate with Epicor for work orders, item master, and customer-specific quality requirements.
  - Sync selected shop-floor events from the MES to quality records within 15 minutes.
  - Support role-based approvals, audit history, and immutable change logs.
  - Go live with one pilot line at Plant 1 first, then expand to Plant 2 after validation.
  - Preserve existing paper-form fields in the new electronic deviation form so operators do not have to relearn fundamentals.
  - Support offline-tolerant intake on a tablet at the line (network drops are common on Line 3).

- **Meridian Stack product facts**
  - Cloud QMS application with deviation, CAPA, supplier nonconformance, and document-control modules.
  - REST API plus webhook support; bulk-import endpoints for master data.
  - Standard connectors for Epicor Kinetic (first-party, GA Q4 2024) and Microsoft Entra ID (first-party).
  - Optional edge relay ("MStack EdgeSync") for on-prem MES polling when outbound-only network access is required. Runs as a container on a plant-local server.
  - Security: SOC 2 Type II (current report Nov 2025), TLS 1.2+, AES-256 at rest, configurable retention policies, customer-managed export, FedRAMP Moderate Ready (not ATO).
  - Compliance: 21 CFR Part 11-ready with e-signature module; supports ISO 9001 and ISO 13485 templates out of the box.
  - Implementation teams typically complete a single-plant pilot in 4 to 6 weeks if source-system access is available.
  - Tablet app supports offline-cache for deviation intake; syncs on reconnect.

- **Commercial / delivery constraints**
  - Northstar wants a pilot proposal that stays within a 6-week evaluation window (targeting pilot go-live no later than June 19, 2026).
  - IT (Sr. Director Darius Owens) will reject any design that requires inbound firewall openings at the plant.
  - Quality (Director Priya Desai) wants e-signatures, audit trails, and read-only history for closed records.
  - Finance (CFO Raj Patel) wants a rough rollout order-of-magnitude estimate, but this artifact should not become a full pricing proposal. The commercial proposal is a separate artifact the AE will produce.
  - Medina has explicitly said she does not want the demo to be a generic product tour; she wants to see *her* deviation flow.

- **Competitive context (light, do not disparage)**
  - Incumbent vendor is not pursuing — MES add-on is going end-of-life.
  - Two other finalists: QualityWorks (strong QMS, weak shop-floor integration) and Shopfloor Central (strong MES-side, weak on CAPA workflow).
  - Meridian Stack's positioning differentiator here is the combined QMS + shop-floor visibility in one platform with the edge relay.

## Artifact specification
Create a written solution design brief that a Sales Engineer could send to the account team after discovery and before the final commercial proposal. The artifact should be practical and implementation-oriented, but still readable by non-technical stakeholders. Required sections, in order:

1. **Title and one-paragraph purpose statement** — identify the customer, the pilot scope, and the decision this document supports.
2. **Current-state summary** — brief description of Northstar's process pain points and system landscape, using only facts from the inputs.
3. **Recommended solution overview** — describe the proposed cloud QMS deployment at a high level, including which modules are in scope for v1 and which are explicitly out of scope.
4. **Architecture diagram in words** — explain the flow between Epicor, the cloud QMS, Entra ID, and the MES/edge relay. This can be prose or a simple ASCII block diagram, but it must be concrete.
5. **Integration plan** — list the main data objects and sync directions, including work orders, item master, users/roles, deviations, approvals, and shop-floor events. For each, name the trigger, direction, transport, and cadence/latency target.
6. **Security and compliance notes** — explain authentication, auditability, retention, outbound-only networking, and how the system supports quality-regulated workflows (including the ISO 13485 medical-device sub-assembly customer's requirements).
7. **Pilot implementation plan** — 3 phases with rough timing, owner assumptions, and what Northstar must provide to start. Include a named pilot line at Plant 1 (recommend Line 2, highest deviation volume).
8. **Demo script** — a step-by-step 10- to 12-minute demo flow that shows intake, approval, escalation, and visibility of a shop-floor event. Use Northstar-specific terminology: "deviation," "work order," "line supervisor," not "ticket" or "record."
9. **Risks / assumptions / dependencies** — capture the main items that could delay the pilot, such as data access, MES API limitations, offline-tablet reliability at Line 3, and validation timing. At least 6 entries.
10. **Pilot success criteria** — measurable conditions under which Northstar will agree to expand to Plant 2.
11. **Next steps** — end with a concrete ask for the technical review meeting and a pilot kickoff checklist (accounts, network, data, people).

Tone: crisp, practical, and confidence-building. It should sound like a competent Sales Engineer who can translate discovery into an implementable plan. Avoid generic marketing language, deep product fluff, and pricing-heavy prose. The brief should make clear what is configured now versus what is a future phase. Distinguish explicitly from the AE's commercial proposal — this artifact is about solution design, not pricing or contract terms.

## Output format
Markdown document, roughly 4 to 6 rendered pages. Use short headings, bullets, and at least one simple architecture table or ASCII flow if that makes the integration path easier to follow. Include at least one integration-plan table (object, direction, trigger, cadence). The demo script should be easy to hand to an AE or SE for rehearsal. The document should be suitable for export to PDF and internal circulation.

## Iteration targets
1. **Make the architecture executable.** v1 often says "integrates with ERP and MES" without naming the direction or trigger. Iterate so each system has a specific role, sync direction, transport, and timing window. Name the edge relay as the outbound-only mechanism at Plant 2.
2. **Separate v1 pilot scope from later expansion.** v1 tends to blur the first plant pilot with the full rollout. Iterate so Plant 1 Line 2 (pilot), Plant 1 remaining lines (Phase 2), and Plant 2 (Phase 3) are clearly distinguished. Supplier portal and document control remain out-of-scope for v1.
3. **Write the demo like a workflow, not a feature list.** v1 often lists features in isolation. Iterate so the demo script follows one deviation from intake on a line tablet through approval routing to audit trail, with one shop-floor event triggering the deviation.
4. **Surface the implementation risks early.** v1 may bury the hard parts. Iterate so network constraints (outbound-only), MES polling limitations (ProdMon 4.7 historian cadence), offline-tablet reliability, and ISO 13485 validation dependencies are explicit, not hidden in a footnote.
5. **Keep compliance concrete.** v1 often says "SOC 2 and audit logs" generically. Iterate so the brief names authentication (Entra SSO + SCIM), record retention (configurable, default 7 years for closed records), immutable history, e-signature handling (21 CFR Part 11 module), and how ISO 13485 template maps to the medical-device sub-assembly customer.
6. **Add a pilot success definition.** v1 may not define what Northstar will accept at the end of the pilot. Iterate so success criteria are measurable (e.g., 100% of Line 2 deviations entered electronically within 10 days; ≤15-minute shop-floor event sync; at least 20 approvals routed end-to-end) and tied to a formal decision to expand.
7. **Stay out of the commercial lane.** v1 may drift into license counts or pricing. Iterate to reference the AE's commercial proposal for pricing, and keep this artifact on technical design, integration, and implementation.

## Success criteria
(For evaluator use only.)
1. The document names the customer, pilot scope, and decision being supported within the first paragraph.
2. The recommended solution clearly states what is in scope for v1 and what is deferred to later phases.
3. The integration plan identifies at least four concrete objects or events (work orders, item master, deviations, shop-floor events) and the direction of data flow, trigger, and cadence for each.
4. The demo script is ordered, time-boxed, and shows a realistic Northstar quality workflow from intake to approval and audit history — using Northstar terminology.
5. The security and compliance section addresses SSO (Entra), audit trail, retention, outbound-only networking, and at least one explicit nod to the ISO 13485 sub-assembly line's needs.
6. The implementation plan includes named phases, approximate timing that fits within the 6-week pilot window, and the customer inputs required to start.
7. The risks/assumptions section includes at least 6 items — with the outbound-only-network, ProdMon-polling, offline-tablet, and validation items among them.
8. The pilot success criteria are measurable and tied to the expansion decision.
9. The document stays technical/implementation-focused and defers pricing to the commercial proposal.

## Scope target
A v1 at about 15 minutes should produce:
- A customer-specific title and purpose statement.
- A short current-state summary of the ERP, MES, identity, and process pain points.
- A recommended solution overview with module scope for the pilot.
- A basic architecture explanation, even if it is only prose.
- A short integration list covering Epicor, Entra ID, and the MES or edge relay.
- A simple 3-phase pilot plan.
- A demo script with 4 to 6 steps.
- A brief risks / assumptions section (3–4 items).
- A stub pilot success criteria section.

Iteration can improve:
- A clearer boundary between pilot and rollout phases (Plant 1 Line 2 → Plant 1 full → Plant 2).
- More explicit data-field mapping (Epicor work-order IDs to QMS deviation context fields).
- A stronger acceptance-definition section for the pilot (measurable, tied to expansion).
- A more polished diagram or table format (ASCII flow or table).
- Tighter wording for the demo to make it easier to rehearse live and stay within 10–12 minutes.
- Explicit treatment of the ISO 13485 sub-assembly customer's requirements in the compliance section.
- Full treatment of the ProdMon 4.7 historian polling contract, including fallback if cadence slips beyond the 15-minute SLO.

## Non-goals (explicit)
- No pricing, ARR, or license-count detail. That lives in the AE's commercial proposal.
- No deep product datasheet content — reference product capability, do not reproduce marketing collateral.
- No comparative disparagement of QualityWorks or Shopfloor Central. Differentiation is through design specificity, not vendor criticism.
- Do not commit to FedRAMP ATO — the product is FedRAMP-Moderate-Ready but not authorized.
- Do not design Plant 2 rollout in full — that is Phase 3 and depends on pilot success.
- Keep the demo to Medina's exact flow (deviation on Line 2 → approval → shop-floor event context); avoid feature-tour tangents.

## Audience and distribution
- Primary: Northstar technical committee — VP Ops Carla Medina, Sr. Director IT Darius Owens, Director Quality Priya Desai. CFO Raj Patel is secondary (for Phase scope, not pricing).
- Internal Meridian Stack readers: AE (for companion commercial proposal), Implementation PM (for pilot kickoff), VP SE (for review).
- Must be forwardable internally at Northstar without re-interpretation — written for their committee, not for an SE peer.
- Pair with the AE's commercial proposal at delivery; link each artifact to the other by name.

## Reference integration-plan skeleton
The integration plan should fill in a table of this shape. Exact fields, directions, and cadences are for the SE to specify:

| Object / event | Direction | Transport | Trigger | Cadence / latency target | Notes |
|---|---|---|---|---|---|
| Epicor work order | Epicor → QMS | Epicor REST 2.0 pull | QMS schedule | Every 5 min | For deviation context linking |
| Item master (SKU) | Epicor → QMS | REST bulk-import | Daily full, hourly delta | ≤1 h for delta | ~14,000 SKUs |
| User / role (SSO) | Entra → QMS | SCIM | Provision/deprovision events | Near-real-time | SSO mandatory |
| Deviation record | QMS only (master) | — | Line-tablet intake | Immediate | Offline-tolerant cache |
| Approval event | QMS → Epicor (optional) | Webhook | On final disposition | ≤1 min | Phase 2 candidate |
| Shop-floor event (MES) | ProdMon 4.7 → EdgeSync → QMS | Outbound HTTPS polling | EdgeSync poll | ≤15 min | Plant 2 only |

If the design diverges (e.g., moves approvals to Phase 1 or omits the MES integration from pilot), the design should defend the choice explicitly.

## Reference architecture (text-form sketch the SE may reuse or replace)
```
 [ Line 2 tablets @ Plant 1 ]    [ Entra ID ]
           |                          |
           | offline-tolerant         | SSO / SCIM
           v                          v
    +----------------------------------------+
    |         Meridian Stack (SaaS)          |
    |   QMS: deviation / CAPA / approval     |
    |   Audit history, e-sig, retention      |
    +------+------------------+--------------+
           ^                  ^
           | REST (pull)      | outbound HTTPS
           |                  |
    +------+-----+     +------+-----+
    | Epicor    |     | EdgeSync   |
    | Kinetic   |     | (Plant 2)  |
    +-----------+     +------+-----+
                             |
                             v
                      [ ProdMon 4.7 historian ]
```

## Pilot success-criteria template
The SE should define measurable criteria at this level of specificity:

- 100% of Line 2 deviations entered electronically within 10 calendar days of go-live.
- ≥95% of shop-floor events synced within the 15-minute SLO over a rolling 7-day window.
- At least 20 end-to-end approvals routed, including one escalation path.
- Zero record-integrity incidents (duplicate, lost, or incorrectly-finalized records) over the pilot window.
- ISO 13485-eligible deviation records (for the medical-device sub-assembly customer's line) validated against the customer's format requirements.
- Audit-trail export successfully demonstrated to Quality Director Desai.

A v2 should tie each criterion to a specific measurement method and source of truth (who checks it, against what).

## Pilot kickoff checklist (partial — for Next Steps section)
- Entra ID tenant details and test-tenant for pre-prod.
- Epicor Kinetic service account (read-only on work orders, item master).
- Network egress whitelist review (outbound HTTPS 443 to Meridian Stack tenant; no inbound).
- EdgeSync container host at Plant 2 — Linux VM or Docker-capable host.
- ProdMon 4.7 historian credentials (read-only).
- Four line-tablet devices (Android 12+ or iOS 16+) provisioned for Line 2.
- Northstar-side project lead named (proposed: Quality Engineer Lead, pending Desai confirmation).
- ISO 13485 deviation-template review with the medical-device sub-assembly customer's QA (owner: Desai).
- Change-management communication plan to Line 2 operators (owner: Medina).

## Implementation timeline (illustrative phases)
- **Week 1:** Discovery artifacts signed, Entra + Epicor access provisioned, EdgeSync installed at Plant 2 (for Phase 3 readiness).
- **Week 2:** QMS tenant configured; deviation, CAPA, and approval workflows configured to Northstar templates.
- **Week 3:** Line 2 tablets provisioned; offline-cache tested; ISO 13485 template validated.
- **Week 4:** Parallel-run (paper + electronic) on Line 2 deviations.
- **Week 5:** Electronic-only on Line 2; first audit-trail export to Desai.
- **Week 6:** Pilot success-criteria review; go/no-go for Phase 2 (remainder of Plant 1).
- **Phase 2 (Weeks 7–12):** Roll to Plant 1 Lines 1, 3, 4.
- **Phase 3 (Weeks 13–18):** Plant 2 + full shop-floor-event integration via EdgeSync.

The SE should confirm that the Week 1–6 window fits within the 6-week pilot evaluation that Medina requested, and flag any slippage risk in the Risks section.
