# Tier-1 Knowledge Base Article: Outlook 365 Fails to Connect on Cisco AnyConnect VPN (KB-4821)

## Occupation
- **SOC:** 15-1232
- **Title:** Computer User Support Specialists

## Scenario
Vanguard Orthopedic Partners, a 280-person multi-specialty clinic group, rolled out Cisco AnyConnect 5.1 on April 6, 2026. Since then, the help desk (led by Daniela Ortega, daniela.ortega@vop.health) has logged 47 tickets of "Outlook won't connect to the mailbox when I'm on VPN." Average handle time is 28 minutes; resolutions inconsistent across the 5 tier-1 agents. You must write a KB article that lets a new agent resolve 90% of these in under 8 minutes without escalation. Due before April 24, 2026 training day.

## Inputs
- **Environment:** Windows 11 23H2, Outlook for Microsoft 365 (Version 2403, Build 17425.20000), Cisco AnyConnect 5.1.2.42, Microsoft 365 E3 tenant `vop.onmicrosoft.com`, Exchange Online (no hybrid).
- **Observed symptoms across 47 tickets:**
  - Outlook shows "Disconnected" in status bar; Send/Receive returns error 0x8004011D.
  - Issue appears only when AnyConnect is connected.
  - OWA (outlook.office.com) works fine in the browser while VPN is up.
  - `Test-NetConnection outlook.office365.com -Port 443` succeeds.
  - `nslookup outlook.office365.com` returns correct IP.
- **VPN config note from network team:** AnyConnect is configured for **full tunnel** (all traffic routed through VPN) per compliance memo VOP-COMP-2025-14.
- **Known Microsoft guidance:** M365 endpoints should be **split-tunnel excluded** per Microsoft KB 334066 "Optimize, Allow, Default" categories.
- **User population:** mostly non-technical clinicians; cannot be asked to edit hosts files or registry without guidance.

## Artifact specification
A **tier-1 troubleshooting runbook / KB article** with these H2 sections in order:

1. **Article metadata** — KB ID, version, author, last-reviewed date, applies-to products, tags.
2. **Symptom summary** — one-paragraph user-facing description plus bulleted "what you'll see" list (error codes, dialogs).
3. **Affected users / scope** — who is affected, how to confirm it's this issue vs a similar one.
4. **Root cause (plain language)** — 2-3 sentences non-technical explanation the agent can read to the user.
5. **Prerequisites for the agent** — tools needed (admin creds? ServiceNow ticket? remote session?).
6. **Diagnostic steps** — numbered steps with expected output. Each step should be a <30-second check that narrows the issue.
7. **Resolution path A (end-user self-serve)** — steps a user can do themselves, screenshot callouts.
8. **Resolution path B (requires elevated rights)** — steps if A fails; requires agent remote-in.
9. **Escalation criteria** — exact triggers to escalate to tier 2 (network team or M365 admin), with what info to attach.
10. **Related articles & known conflicts** — cross-refs to KB-4712 (AnyConnect install), KB-3991 (Outlook profile rebuild).
11. **Revision history** — dated entries.

Style: second-person imperative ("Click Start, then type..."). No jargon without a one-line gloss. Include verbatim UI text in bold. Include command snippets in fenced code blocks.

## Output format
Single `.md` file, ~280 lines. Must include at least 3 copy-pasteable commands (PowerShell or CMD), one decision flowchart (mermaid), and one "if you see this error, do that" table.

## Iteration targets
1. Add a decision flowchart distinguishing KB-4821 from similar-looking issues (profile corruption, expired password, MFA loop) with 3-4 yes/no branches.
2. Replace prose diagnostic steps with a numbered list where each step has **Command**, **Expected output**, **If different:** format.
3. Add a scripted one-liner (PowerShell) that captures diagnostic bundle (AnyConnect route print, `Get-NetRoute`, Outlook OST size, connectivity test) as a ServiceNow attachment.
4. Add an "agent script" callout box with exact words to say to the user during each phase — reduces dead air and sets expectations.
5. Document the permanent fix (network team adds M365 URLs to AnyConnect split-tunnel ACL) separately from the tier-1 workaround, and make clear which one the agent owns.
6. Add estimated time-to-resolve for each branch of the flowchart.

## Success criteria
- A new tier-1 agent could resolve a fresh ticket using only this article in under 8 minutes.
- Error codes and dialog text are verbatim (searchable).
- Clear hand-off trigger to tier 2 (not "if it's hard, escalate").
- Commands actually work on Windows 11 23H2 as written (no typos in flag names).
- Separates the user-serviceable path from the admin path — doesn't assume admin rights.
- Revision history makes the article auditable for HIPAA change-control.

## Scope target
V1 at ~15 min: metadata, symptoms, one-paragraph root cause, a 5-step diagnostic sequence, a single "fix: restart Outlook after connecting VPN" resolution path, and a sentence about when to escalate. Flowchart, diagnostic bundle script, agent script, and error-code table come in v2/v3.
