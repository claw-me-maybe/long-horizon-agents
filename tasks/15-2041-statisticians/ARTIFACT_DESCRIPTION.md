# Pre-Registered Analysis Plan: Checkout Button Color A/B Test at Marlowe & Fig

## Occupation
- **SOC:** 15-2041
- **Title:** Statisticians

## Scenario
Marlowe & Fig, a mid-market DTC home goods retailer (annual GMV ~$84M), is running an experiment swapping the "Place Order" button from teal (#2CA6A4) to deep coral (#D9534F). Growth PM Jordan Ahuja asked statistician Dr. Ines Okoro to pre-register the analysis plan before the experiment launches on April 27, 2026. The prior two experiments were called "significant" at day 3 after repeated peeking — CFO Marta Velez has frozen future rollouts pending a proper SAP.

## Inputs
- **Primary metric:** `conversion_rate` = orders_placed / checkout_sessions_started (Bernoulli, per-visitor, deduped on `visitor_id`).
- **Baseline:** 30-day pre-period mean 4.82%, std 0.31% (day-level), n ≈ 112K sessions/day.
- **MDE target:** relative +2.5% lift (4.82% → 4.94%), two-sided.
- **Secondary metrics:** AOV (log-normal; baseline median $68.40), 14-day repeat-purchase rate, refund rate.
- **Guardrails:** page load time p95 (must not increase >50ms), add-to-cart rate (must not drop >1% relative).
- **Assignment:** visitor-level via MurmurHash3 of `visitor_id` + salt `mf_2026q2`; 50/50 split.
- **Traffic:** ~112K sessions/day across both arms combined.

Known prior issue: cookie churn on Safari 17 ITP means ~6% of visitors are re-bucketed within 7 days.

## Artifact specification
A **Statistical Analysis Plan (SAP)** written as a pre-registration document, suitable for internal sign-off and later journal-style post-mortem. Required H2 sections in order:

1. **Hypotheses** — H0/H1 stated in terms of the primary metric's treatment effect parameter, with direction and scale (absolute vs relative).
2. **Design** — unit of randomization, assignment method, allocation ratio, exclusion criteria (bots, internal IPs, fraud-flagged).
3. **Sample size & power** — show the power calc (Fisher exact or two-proportion z); include the exact formula and numeric result. Target 80% power at alpha 0.05.
4. **Analysis** — primary test, estimator (e.g. delta method with CUPED adjustment using pre-period conversion as covariate), confidence interval construction, multiple-comparison correction for secondaries (BH-FDR at q=0.10).
5. **Stopping rules** — no peeking before planned duration; if early-stop is needed, use mSPRT or Group Sequential (O'Brien-Fleming) with pre-specified alpha-spending function.
6. **Guardrails & SRM check** — chi-square on assignment ratio (fail if p<0.001), guardrail thresholds, and what triggers rollback.
7. **Threats to validity** — cookie churn, novelty effect, weekday seasonality, and how each is handled.
8. **Reporting template** — exact table columns for the writeup (metric, control mean, treatment mean, lift, CI, p-value, SRM check).

## Output format
Single `.md` file, ~280 lines. Must include one LaTeX-rendered formula for sample size and one for CUPED variance reduction.

## Iteration targets
1. Replace pooled z-test with CUPED-adjusted estimator using the 4-week pre-period covariate; quantify expected variance reduction.
2. Add sequential testing via mSPRT so the team can peek daily without alpha inflation.
3. Address cookie-churn bias: either switch to user-level when logged in, or add a sensitivity analysis using an intent-to-treat vs compliant-users contrast.
4. Specify heterogeneous treatment effect analysis (pre-specified subgroups: new vs returning, mobile vs desktop) with interaction test and BH correction.
5. Add a novelty-effect check: compare week-1 vs week-2+ treatment effect, with pre-specified threshold for concern.

## Success criteria
- Power calculation is numerically correct for the stated baseline, MDE, and traffic (reviewer can reproduce).
- SRM check and guardrails are explicit and quantitative (no "monitor closely").
- Stopping rule is pre-specified and alpha-controlling — no ad-hoc peeking.
- CUPED or variance-reduction method is correctly specified with the right estimator.
- Multiple-comparison adjustment is applied to secondaries, not primary.
- Reporting table template is specific enough that a junior analyst could fill it in without guesswork.

## Scope target
V1 at ~15 min: hypotheses, a sample-size calc (pooled two-proportion z, no CUPED), plain t-test/z-test primary, flat guardrail list, and a placeholder stopping rule ("run for 14 days"). Sequential testing, CUPED, HTE, and novelty checks come in v2/v3.
