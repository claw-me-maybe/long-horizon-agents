# Indirect-Spend RFP — Managed Print Services (FY2027–FY2029) for Aviolla Food Group

## Occupation
- **SOC:** 13-1020
- **Title:** Buyers and Purchasing Agents

## Scenario
Aviolla Food Group, a 9,400-employee frozen-foods manufacturer (HQ Chicago; 14 plants across IL, IA, OH, TX, NC), is re-bidding its Managed Print Services contract. The current multi-year contract with GlyphCopy Solutions expires December 31, 2026; under it, Aviolla spends $2.3M annually across 1,412 devices with growing complaints about service response in the plants and no meaningful secure-print controls. The Category Manager for Indirect, Perpetua Ikechukwu-Lamb, has tasked you with issuing a full RFP package by May 20, 2026, with bids due July 3, for award by August 29, to enable a clean 4-month transition. A three-year $6.8M TCV commitment is at stake.

## Inputs

**Current-state baseline**
- 1,412 devices: 912 MFPs (Canon imageRunner mostly), 372 desktop printers (HP), 128 production label printers (Zebra)
- Annual page volume: 21.4M (65% mono, 35% color)
- Annual spend: $2.31M (51% lease/hardware, 29% service, 14% toner/supplies, 6% software/security)
- Contract term: 60 months (expires 12/31/2026)
- Current SLA: 4-hr response urban, 8-hr response rural plants; actual 2025 performance: 6.1 hr urban, 11.8 hr rural
- Security posture: no follow-me print; no user PIN; shared-tray printing; drive encryption on 61% of fleet
- 2025 ticket mix: 38% "out of toner despite auto-replenish," 24% hardware fail, 19% firmware, 11% security/config, 8% training

**Strategic priorities (from CIO Hallvard Nakashima and CFO Wren Staveley-Marx)**
- Reduce TCO by ≥15% over 3 years vs. current run rate
- 100% secure release printing (badge or PIN) by end of Year 1
- 95% SLA adherence (urban 4 hr / rural 8 hr / plants 6 hr)
- Sustainability: target 30% reduction in total pages and Energy Star devices only
- Executive preference for a minority/women-owned subcontracting path where viable

**Business constraints**
- No single-source award above $3M TCV without competing bids (corporate policy P-FIN-024)
- Must include tier-2 supplier diversity spend target: 20% minimum
- OFAC and FCPA standard clauses mandated
- Cyber insurance minimum $25M aggregate; SOC 2 Type II required
- Plant operations cannot have more than 30 min unplanned downtime per device in transition
- Aviolla legal must approve Master Services Agreement template (Aviolla paper preferred; limited fallback to supplier paper)

**Shortlist identified by pre-RFI (5 suppliers)**
- GlyphCopy Solutions (incumbent; Ricoh/Canon mix)
- Emerald Sigil Print Services (WBE certified; Xerox-centric)
- Polymath Print Systems (national, HP-heavy)
- Brambleaxe Imaging (regional, Canon-heavy)
- VaultQuire Managed Services (security-differentiated, Lexmark)

## Artifact specification
Complete RFP package. Required sections:
1. **Cover letter and submission instructions** — timeline, point of contact, Q&A window, NDA, submission format, page limits
2. **Background and objectives** — Aviolla context, strategic priorities, current pain
3. **Scope of services** — in-scope / out-of-scope by device class and site; plant vs. office delineation
4. **Volumes and baseline data** — device inventory, page volumes, SLA expectations
5. **Technical and security requirements** — secure print, identity integration (Azure Entra ID), encryption, SOC 2, zero-trust print-server architecture posture
6. **Service levels and KPIs** — SLA matrix, credits, governance cadence
7. **Sustainability and device standards** — Energy Star, take-back, page-reduction commitment
8. **Pricing schedule** — explicit pricing model (CPP tiered, device lease, service floor) with required tables to be completed; must enable apples-to-apples TCO comparison
9. **Legal and commercial terms** — MSA framework, liability caps, IP, data privacy (CCPA if applicable), insurance, diversity, OFAC/FCPA
10. **Supplier response requirements** — mandatory sections; weighting
11. **Evaluation methodology** — scoring rubric (e.g., Technical 35% / Service 25% / Price 25% / Sustainability 10% / Diversity 5%)
12. **Transition plan expectations** — 90-day plan, device swap sequencing, risk posture
13. **Appendices** — device list sample, NDA, diversity attestation form, reference-check template

Tone: formal, neutral, explicit. Every requirement labeled Must (M), Should (S), or Nice-to-have (N). No proprietary preferences leaking.

## Output format
Markdown RFP package (document that a supplier could respond to directly). Target 3,000–4,200 words plus tables.

## Iteration targets
1. Requirements often mix M/S/N without labeling; apply the labels consistently so suppliers know what is disqualifying.
2. Pricing schedule typically asks for "pricing" without structuring tables that force comparability; add required CPP tiers, per-device lease tables, service minimums, and volume bands.
3. Evaluation weighting is often a number without rubric; include a sub-criteria rubric for at least Technical and Service so suppliers see how they'll be judged.
4. Security section sometimes stops at SOC 2; add explicit requirements for zero-trust print architecture, BadgeIn/PIN, and Entra ID integration.
5. Sustainability is often a checkbox; require suppliers to commit to a quantified page-reduction glidepath.
6. Diversity requirement often lacks enforcement teeth; require attestation and a Tier-2 reporting cadence.

## Success criteria
- A qualified supplier reading the RFP can respond without needing fundamental clarifications — the ask is unambiguous.
- The pricing schedule forces comparable bids across suppliers — no supplier can hide margin in a non-compared line item.
- Requirements are labeled M/S/N and traceable to the strategic priorities.
- Evaluation methodology is transparent: weightings, sub-criteria, and tie-break.
- Transition expectations protect plant operations (30-min downtime cap is explicit, not implicit).
- Legal and commercial terms reference specific clauses (OFAC, FCPA, cyber-insurance min, SOC 2) rather than generic "applicable law."

## Scope target
v1 at ~15 minutes should contain: cover/instructions, background, scope-of-services outline, a first-cut pricing schedule with tables defined (not all fields fully specified), technical/security requirements labeled M/S/N (partial), SLA matrix, evaluation weighting with top-level categories, and a transition plan outline. Roughly 1,900–2,300 words; full sub-criteria rubrics, appendices, and legal term templates are iteration work.
