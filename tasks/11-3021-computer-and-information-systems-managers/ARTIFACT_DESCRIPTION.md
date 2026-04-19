# Incident Review: March 22, 2026 Checkout API Outage at Lumenfield Commerce

## Occupation
- **SOC:** 11-3021
- **Title:** Computer and Information Systems Managers

## Scenario
Lumenfield Commerce, a $1.2B DTC home-goods retailer (4.2M active customers, 28 US warehouses),
suffered a 2-hour-47-minute checkout API outage on Saturday March 22, 2026, from 11:14 AM to
2:01 PM Eastern. Approximately $1.9M in estimated lost GMV, 41,300 failed sessions, and
elevated cart-abandonment the following 48 hours. IT Director Elena Choi must deliver a
post-incident review to the CTO, Raj Mehta, and the VP of Engineering, Marcus Brennan (no
relation to the on-call SRE), by April 3, 2026, which will be shared with the CEO staff, the
Audit Committee, and with Datacore (their payment processor partner) as part of a joint RCA.
The review drives a reliability investment request of up to $1.4M for H2 2026 that will
compete against product-roadmap priorities.

## Inputs
The model starts with:

### Timeline fragments from PagerDuty + Datadog + Slack #incident-2026-03-22
- 11:14:22 AM ET: `checkout-api` p50 latency jumps from 180ms to 2,400ms; error rate rises
  to 47% within 90 seconds. PagerDuty Sev-1 auto-fires at 11:15:47.
- 11:18 AM: On-call SRE (Tom Brennan) paged. Acknowledged at 11:20 after second page.
- 11:26 AM: Initial hypothesis — Redis cluster degraded based on elevated connection pool
  metrics. Failover initiated at 11:31.
- 11:39 AM: Failover completes; error rate unchanged at ~45%.
- 11:48 AM: Status page updated to "Degraded - Investigating" (34 minutes after detection).
- 11:52 AM: Incident commander (Priya Shah) takes over from SRE. Datacore engaged at 11:54
  via email (Slack Connect channel not yet established).
- 12:02 PM: Datacore's on-call responds after SRE escalates through their PagerDuty tenant.
- 12:18 PM: Root cause identified — Datacore's fraud-scoring service returning 503s after
  a 12:02 PM deploy on their side (ironically pushed during our outage); `checkout-api` did
  not have a circuit breaker for this dependency, so the thread pool starved.
- 12:44 PM: Temporary mitigation — fraud-scoring bypassed for orders <$200 (74% of traffic),
  with elevated fraud risk accepted for the window. Approved by VP Risk on the bridge.
- 1:26 PM: Datacore deploys rollback of their 12:02 PM change.
- 2:01 PM: All-clear; checkout latency back to p50 190ms. Status page updated "Resolved"
  at 2:05 PM.

### Contributing factors surfaced during the incident
- The `checkout-api` service's dependency map in Backstage was last updated 2024-09;
  fraud-scoring was documented as "optional" but code-path was actually synchronous and
  blocking. The "optional" label referred to a feature-flag controlled integration that
  had been removed in 2025.
- Runbook pointed to a 2023 version of the Datacore escalation contact; correct on-call
  reached via LinkedIn by the SRE after 20 minutes of trying the runbook number.
- Status page was not updated until 11:48 AM (34 minutes after detection). Company SLO
  commits to 15-minute status-page updates.
- No circuit breaker or bulkhead pattern in place for any external synchronous dependency.
- The fraud-scoring timeout was set to 30 seconds — long enough to starve the checkout
  thread pool under load.

### Prior incident history and open items
- 4 Sev-1 or Sev-2 affecting checkout in the last 12 months; 2 involved third-party
  dependency failures (both payment gateway; one tax service).
- 1 previously-identified action item ("implement circuit breakers for all external
  dependencies") was opened Nov 2025 and closed as "won't do" in Jan 2026 due to
  competing priorities (Q1 promo platform work). Closure was approved by a VP no longer
  at the company.
- Backstage dependency graph last full audit: 2024-09. 18 months stale.

### Current reliability state
- SLO is 99.9% checkout availability (43 min/month error budget). YTD consumption as of
  March 22: 187 min (4.3x of monthly budget, 1.1x annual budget in one quarter).
- This incident alone: 167 minutes of full impact = 3.9x monthly budget.
- Reliability policy states: >2x monthly budget consumption triggers feature freeze.
  Not enforced in past consumption spikes.

### Team
- 6 engineers on Checkout team, led by Engineering Manager Felicia Ogundimu.
- 3 SREs shared across platform.
- No dedicated reliability/SRE engineer embedded in Checkout.
- Datacore relationship: single technical point of contact on their side (Saanvi Kapoor).

### Business context for the investment ask
- H2 2026 product roadmap: new subscription product (launching Sep), international
  expansion to Canada (launching Oct). Both high-revenue.
- Reliability investment competing directly against 3 product engineers worth of capacity.

## Artifact specification
A formal post-incident review (PIR) document following a blameless-review methodology.
Required sections in this order:

1. **Incident summary**: Sev level, duration (detection → resolution in minutes), customer
   impact ($ GMV and session count), systems affected, one-sentence root cause.
2. **Timeline** with timestamps, actor, action, and system signal — at least 12 entries
   spanning detection to resolution. Presented as a table.
3. **Root cause analysis** using the Five Whys or equivalent, arriving at systemic (not
   individual) cause(s). Identify both proximate cause (fraud-scoring 503s) and contributing
   factors (missing circuit breaker, stale docs, stale runbook, prior deprioritization, late
   status-page update).
4. **What went well** — minimum 3 items. Counterbalance the critique; identify team
   behaviors and systems that worked correctly.
5. **What went poorly** — minimum 4 items, each grounded in a specific timeline entry or
   data point.
6. **Action items table** — 6-10 actions, each with: owner role (not name), priority
   (P0/P1/P2), effort estimate (eng-weeks), due date, success criterion, and whether it
   addresses detection / mitigation / prevention. Prioritized in the document.
7. **SLO + error-budget discussion** — what this incident does to the Q1 and YTD error
   budget; what that should trigger per reliability policy; recommendation on whether to
   enforce feature freeze.
8. **Joint RCA section for Datacore** — what we're asking them to commit to, and what we
   commit to (bidirectional).
9. **Investment recommendation** — a 3-option framing for the $1.4M request (e.g.,
   $400K minimum / $900K recommended / $1.4M comprehensive), with cost/benefit per option
   in terms of SLO impact, mean-time-to-recover improvement, and feature-roadmap trade-off.

Tone: blameless, precise, no euphemisms. Individuals named only where they took specific
actions that are facts of record (e.g., "SRE acknowledged page at 11:20"); no attribution
of fault to individuals. Use "the on-call" or "the team" when describing decisions that
multiple people contributed to.

## Output format
Markdown document, ~5-8 pages rendered. At least two tables (timeline, action items). Must
be shareable with an external vendor (Datacore) — so nothing internally confidential. A
"For Internal Only" appendix may contain sensitive details.

## Iteration targets
1. **Fix the Five Whys to reach systemic causes** — v1 often stops at "the fraud-scoring
   service failed." Iterate to: "why did we not have a circuit breaker for a synchronous
   external dependency on our highest-revenue code path?" and beyond, to the organizational
   cause ("the circuit-breaker work was deprioritized in Jan 2026 by a VP who weighted
   promo-platform features higher; there is no standing reliability-investment gate").
2. **Quantify the error-budget implications correctly** — v1 may handwave. A better version
   states that 167 minutes of this incident consume 3.9x the monthly budget alone, connects
   to what the SLO policy says should happen (feature freeze), and makes an explicit
   recommendation on whether to invoke it now (political call — but should be made).
3. **Differentiate the action items by leverage** — v1 lists 10 items of roughly equal
   priority. Iterate so the top 2-3 (e.g., circuit-breaker framework, dependency-graph
   auto-validation) are clearly the highest leverage and the others are supporting. Rank
   order the list.
4. **Address the recurring-theme dimension** — 2 of the last 4 Sev incidents involved
   third-party dependencies. v1 may miss this. A strong version connects this incident to
   a pattern and proposes a systemic fix (e.g., standing process for auditing synchronous
   external dependencies on critical paths).
5. **Make the Datacore ask specific** — v1 writes "improve communication." Iterate to
   concrete commitments: pre-deploy notification SLA (e.g., 24 hours for any change to
   fraud-scoring, status-page integration, joint-on-call roster), runbook-sharing cadence
   (quarterly refresh), joint tabletop exercise every 6 months.
6. **Sharpen the investment options** — v1 presents a single $1.4M plan. Iterate to three
   tiered options ($400K minimum-viable, $900K recommended, $1.4M comprehensive) with
   stated reliability delta for each, and connect the product-roadmap trade-off honestly.

## Success criteria
(For evaluator use only.)
1. Root cause reaches a systemic/organizational level, not just the technical proximate
   cause; explicitly names the Nov 2025 "won't do" closure.
2. The prior Nov-2025 circuit-breaker deprioritization is explicitly named as a contributing
   factor.
3. Timeline has at least 10 entries with real timestamps matching the provided data.
4. At least one action item is P0 with an owner role and due date within 30 days; total
   action list is rank-ordered by leverage; effort estimates in eng-weeks.
5. SLO/error-budget math is computed correctly (e.g., 167 min of checkout impact against
   a 43-min monthly budget = 3.9x) and connected to policy triggers.
6. The Datacore section distinguishes what THEY commit to vs. what WE commit to, with 2+
   items each.
7. Investment recommendation has 3 tiered options with distinct scope and distinct
   reliability-delta claims.
8. Blameless tone maintained throughout — no language assigning fault to Brennan, Shah, or
   named individuals for judgment calls.

## Scope target
A v1 at ~15 minutes should contain: incident summary with Sev level and duration, 8-10
timeline entries from the provided data, a first-pass root cause reaching at least the
"missing circuit breaker" layer (ideally to organizational deprioritization), 4-5 action
items with owners, a brief what-went-well/what-went-poorly (3 items each), and a single-
option investment framing. Error-budget math should have the basic ratio (e.g., "3.9x
monthly budget"). Datacore section may list one ask and one commit. Three-option investment
framing and detailed SLO-policy enforcement recommendation are iteration targets for v2/v3.
