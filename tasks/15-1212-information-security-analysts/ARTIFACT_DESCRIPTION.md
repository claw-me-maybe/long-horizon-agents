# Incident Response Playbook: Business Email Compromise at Sterling & Rowe LLP

## Occupation
- **SOC:** 15-1212
- **Title:** Information Security Analysts

## Scenario
Sterling & Rowe LLP, a 340-attorney Chicago firm with an M&A practice, experienced a suspected BEC on April 10, 2026: the CFO's assistant received a wire request for $1.4M appearing to come from partner Elena Petrov, but the email header later showed `From: epetrov@sterling-rowe.co` (note the `.co` TLD). Security analyst Dara Nwosu (reports to CISO Martin Chen) must produce a BEC-focused incident response playbook before the May 5, 2026 tabletop exercise with the executive committee. An external firm found that the previous playbook (authored 2022) never specified who can authorize outbound statements to clients about an incident, causing a 9-hour delay in last year's ransomware drill.

## Inputs
- **Environment:**
  - Microsoft 365 E5 + Defender for Office 365 Plan 2; Entra ID with Conditional Access + FIDO2 keys for partners.
  - Mimecast for email hygiene (in front of M365).
  - Okta for SaaS SSO (iManage, NetDocuments, Kira).
  - SIEM: Microsoft Sentinel, 90-day retention.
- **Threat model context:**
  - Firm has done $2.4B of M&A deals YTD; client funds occasionally flow via escrow.
  - High-value target; prior phishing attempts include W-2 fraud and vendor-invoice redirection.
- **Current capabilities:**
  - MFA enforced; ~6% of users still on SMS (partners grandfathered; being migrated).
  - Mail transport rules exist but unaudited.
  - No current playbook for BEC specifically; general IR playbook is generic.
- **Regulatory:** Illinois PIPA §530; ABA Model Rule 1.6 (client confidentiality); SEC Reg S-P for client financial data.
- **External retainers:** Kroll for DFIR (4-hour SLA), Hunton Andrews Kurth for breach counsel, Arete for ransomware.

## Artifact specification
A **BEC-specific incident response playbook** that maps to NIST SP 800-61r2 phases. Required H2 sections:

1. **Document metadata** — classification (Confidential - Internal), version, approver (CISO), review cadence (quarterly), last tabletop date.
2. **Scope & threat model** — what this playbook covers (wire-fraud BEC, vendor invoice fraud, payroll redirect) vs excludes (ransomware, insider threat).
3. **Roles & authorities** — named IR team, backup, decision authorities, RACI for key decisions.
4. **Detection signals** — MITRE ATT&CK mapping (T1566, T1534, T1114), specific Sentinel/Defender alerts, user-reported indicators, look-alike-domain watchlist.
5. **Severity classification** — tiers with examples and escalation criteria.
6. **Preparation controls (standing)** — what must be true before an incident: DMARC p=reject, impossible-travel alerts, mailbox rule auditing, wire-approval policy, look-alike domain monitoring.
7. **Identification** — triage checklist: confirm headers, MessageTraceV2, authentication-results, attachment hash, linked sign-ins.
8. **Containment** — short-term (disable compromised account, kill tokens, revoke OAuth grants, block sender + TLD) and longer-term (reset creds, re-enroll MFA).
9. **Eradication** — remove mailbox rules, purge malicious mail via Compliance Search + Purge, quarantine identical messages tenant-wide.
10. **Recovery** — re-enable user with new credentials, validate no persistence, monitor for 14 days.
11. **Post-incident** — lessons learned, RCA template, regulator/client notification decision tree, insurance notification trigger (Chubb cyber policy).
12. **Communications templates** — internal, client, regulator (Illinois AG), law enforcement (IC3, FBI Field Office Chicago).
13. **Technical appendix** — KQL queries for Sentinel (mailbox rule creation, impossible travel, unusual mail forwarding), PowerShell for Exchange Online containment, Entra ID revoke-token command.
14. **Tabletop exercise scenarios** — 3 scenarios of escalating complexity.

## Output format
Single `.md` file, ~380 lines. Must include: a RACI table, at least 3 fenced KQL queries, at least 2 PowerShell snippets, a MITRE ATT&CK mapping table, and a decision flowchart (mermaid) for notification obligations.

## Iteration targets
1. Replace the generic "notify legal" step with a decision tree specifying when Illinois PIPA notification is triggered (encryption safe-harbor, risk-of-harm threshold, 45-day statutory clock).
2. Convert containment from prose to a ranked sequence with **decision point → action → expected outcome → fallback**, including commands.
3. Add KQL for detecting auto-forward rule creation (`MessageTraceV2` or `ExchangeEnvelopeAttributes`) and for OAuth consent grant anomalies.
4. Harden the communications template — remove all passive voice, pre-fill legal-approved language for client notice, and mark which fields require breach counsel review.
5. Add a "wire-fraud rapid response" sub-playbook: the 4-hour window for FinCEN Kill Chain + FBI IC3 + receiving bank SWIFT GPI recall.
6. Tie each phase to specific MITRE ATT&CK techniques (IDs, not just names).

## Success criteria
- Named roles with backups — no "the security team" without specifying who.
- Contains copy-pasteable, correct KQL and PowerShell (no placeholders).
- Illinois PIPA and ABA Rule 1.6 obligations are addressed with specific triggers, not hand-waved.
- Severity classification is unambiguous and drives concrete actions.
- Wire-recall steps are time-boxed to the 72-hour FinCEN Kill Chain window.
- Post-incident section names an RCA format (e.g. 5 Whys or fishbone) and ties to a ticketing system.

## Scope target
V1 at ~15 min: metadata, a one-paragraph threat model, a RACI with 4-5 roles, a simple severity table, a prose identification+containment section, a single KQL for suspicious sign-ins, and a skeletal client notification template. MITRE mapping, decision flowchart, PIPA decision tree, and tabletop scenarios come in v2/v3.
