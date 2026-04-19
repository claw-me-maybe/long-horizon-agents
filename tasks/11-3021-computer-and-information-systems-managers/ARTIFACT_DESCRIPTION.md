# Incident Review: March 22, 2026 Checkout API Outage at Lumenfield Commerce

## Occupation
- **SOC:** 11-3021
- **Title:** Computer and Information Systems Managers

## Scenario
Lumenfield Commerce, a $1.2B DTC home-goods retailer, suffered a 2-hour-47-minute checkout API outage on Saturday March 22, 2026, from 11:14 AM to 2:01 PM Eastern. Approximately $1.9M in estimated lost GMV, 41,300 failed sessions, and elevated cart-abandonment the following 48 hours. IT Director Elena Choi must deliver a post-incident review to the CTO, Raj Mehta, and the VP of Engineering by April 3, 2026, that will also be shared with the CEO staff and with Datacore (their payment processor partner) as part of a joint RCA. The review drives a reliability investment request of up to $1.4M for H2 2026.

## Inputs
The model starts with:

- **Timeline fragments from PagerDuty + Datadog + Slack #incident-2026-03-22:**
  - 11:14:22 AM ET: `checkout-api` p50 latency jumps from 180ms to 2,400ms; error rate rises to 47%.
  - 11:18 AM: On-call SRE (Marcus Brennan) paged. Acknowledged 11:20.
  - 11:26 AM: Initial hypothesis — Redis cluster degraded. Failover initiated 11:31.
  - 11:39 AM: Failover completes; error rate unchanged.
  - 11:52 AM: Incident commander (Priya Shah) takes over from SRE. Datacore engaged 11:54.
  - 12:18 PM: Root cause identified — Datacore's fraud-scoring service returning 503s after a 12:02 PM deploy on their side; `checkout-api` did not have a circuit breaker for this dependency.
  - 12:44 PM: Temporary mitigation — fraud-scoring bypassed for orders <$200 (74% of traffic).
  - 1:26 PM: Datacore deploys rollback.
  - 2:01 PM: All-clear; checkout latency back to p50 190ms.
- **Contributing factors surfaced during the incident:**
  - The `checkout-api` service's dependency map in Backstage was last updated 2024-09; fraud-scoring was documented as "optional" but code-path was actually synchronous and blocking.
  - Runbook pointed to a 2023 version of the Datacore escalation contact; correct on-call reached via LinkedIn by SRE.
  - Status page was not updated until 11:48 AM (34 minutes after detection).
- **Prior incidents (last 12 months):** 4 Sev-1 or Sev-2 affecting checkout; 2 involved third-party dependency failures; 1 previously-identified action item ("implement circuit breakers for all external dependencies") was opened Nov 2025 and closed as "won't do" in Jan 2026 due to competing priorities.
- **Current reliability budget:** SLO is 99.9% checkout availability (43 min/month error budget). YTD consumption: 187 min (3.3x budget).
- **Team:** 6 engineers on Checkout, 3 SREs shared across platform. No dedicated reliability engineer.

## Artifact specification
A formal post-incident review (PIR) document following a blameless-review methodology. Required sections:
1. **Incident summary**: Sev level, duration, customer impact ($ and session count), systems affected.
2. **Timeline** with timestamps, actor, action, and system signal — at least 12 entries spanning detection to resolution.
3. **Root cause analysis** using the Five Whys or equivalent, arriving at systemic (not individual) cause(s). Identify both proximate cause (fraud-scoring 503s) and contributing factors (missing circuit breaker, stale docs, stale runbook, prior deprioritization).
4. **What went well** — minimum 3 items. Counterbalance the critique.
5. **What went poorly** — minimum 4 items, each grounded in a specific timeline entry.
6. **Action items table** — 6-10 actions, each with: owner role, priority (P0/P1/P2), effort estimate (eng-weeks), due date, success criterion, and whether it addresses detection / mitigation / prevention.
7. **SLO + error-budget discussion** — what this incident does to the Q1 and YTD error budget; what that should trigger per reliability policy.
8. **Joint RCA section for Datacore** — what we're asking them to commit to, and what we commit to.
9. **Investment recommendation** — a 3-option framing for the $1.4M request, with cost/benefit per option.

Tone: blameless, precise, no euphemisms. Individuals named only where they took specific actions; no attribution of fault to individuals.

## Output format
Markdown document, ~5-8 pages rendered. At least two tables (timeline, actions). Must be shareable with an external vendor (Datacore) — so nothing internally confidential.

## Iteration targets
1. **Fix the Five Whys** — v1 often stops at "the fraud-scoring service failed." Iterate to get to "why did we not have a circuit breaker for a synchronous external dependency on our highest-revenue code path" and beyond, to the organizational cause (deprioritization in Jan 2026).
2. **Quantify the error-budget implications correctly** — v1 may handwave. A better version states that 167 minutes of this incident consume 3.9x the monthly budget alone, and connects to what the SLO policy says should happen (feature freeze? reliability sprint?).
3. **Differentiate the action items by leverage** — v1 lists 10 items of roughly equal priority. Iterate so the top 2-3 (e.g., circuit-breaker framework, dependency-graph auto-validation) are clearly the highest leverage and the others are supporting.
4. **Address the recurring-theme dimension** — 2 of the last 4 Sev incidents involved third-party dependencies. v1 may miss this. A strong version connects this incident to a pattern and proposes a systemic fix.
5. **Make the Datacore ask specific** — v1 writes "improve communication." Iterate to concrete commitments: pre-deploy notification SLA, runbook-sharing cadence, joint tabletop exercise every 6 months.
6. **Sharpen the investment options** — v1 presents a single $1.4M plan. Iterate to three tiered options ($400K minimum-viable, $900K recommended, $1.4M comprehensive) with stated reliability delta for each.

## Success criteria
(For evaluator use only.)
1. Root cause reaches a systemic/organizational level, not just the technical proximate cause.
2. The prior Nov-2025 "won't do" closure of the circuit-breaker action item is explicitly named as a contributing factor.
3. Timeline has at least 10 entries with real timestamps matching the provided data.
4. At least one action item is P0 with an owner role and due date within 30 days; total action list is rank-ordered by leverage.
5. SLO/error-budget math is computed correctly (e.g., 167 min of checkout impact against a 43-min monthly budget).
6. The Datacore section distinguishes what THEY commit to vs. what WE commit to, with 2+ items each.

## Scope target
A v1 at ~15 minutes should contain: incident summary, 8-10 timeline entries from the provided data, a first-pass root cause reaching at least the "missing circuit breaker" layer, 4-5 action items with owners, a brief what-went-well/what-went-poorly, and a single-option investment framing. Error-budget math, Datacore section, and three-option investment can be stubs.
