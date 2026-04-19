# Churn Prediction Notebook: 90-Day Attrition Model for Cascade Fiber Internet

## Occupation
- **SOC:** 15-2051
- **Title:** Data Scientists

## Scenario
Cascade Fiber, a Pacific-Northwest regional ISP with 340,000 residential subscribers, wants a 90-day churn prediction model to target retention offers. Head of Analytics Mei-Lin Hsu needs a reproducible notebook from data scientist Tomás Oliveira by May 22, 2026, covering EDA → features → model → calibration → business uplift analysis. The 2025 model shipped by a departed contractor used a logistic regression trained on leaky features (it included `days_until_churn`), produced a glossy AUC of 0.96 in dev and promptly failed in prod — the retention team lost faith. Tomás must not repeat this.

## Inputs
- **Data warehouse tables (BigQuery):**
  - `analytics.subs_monthly`: one row per subscriber-month, 2023-01 through 2026-03, ~13M rows. Columns: `sub_id`, `month`, `plan_tier` (Bronze/Silver/Gold/Platinum), `mrr`, `tenure_months`, `data_usage_gb`, `outages_30d`, `support_tickets_30d`, `nps_last`, `payment_method`, `zip`, `is_bundle`, `churned_flag` (T if cancelled in that month).
  - `ops.service_incidents`: per-outage rows with sub_id, start_ts, duration_min, severity.
  - `billing.invoices`: monthly invoice with late_pay_count.
- **Label definition:** churn = subscriber cancels within 90 days after feature snapshot date.
- **Train/test split:** temporal — train on snapshots 2023-01 to 2025-09, validate 2025-10 to 2025-12, test 2026-01 (so prediction horizon is 2026-01 → 2026-04).
- **Class balance:** ~3.2% positive rate.
- **Business context:** retention offer costs $35 on average, saves $680 LTV if successful (72% offer acceptance among churners), zero value if given to non-churner.
- **Regulatory note:** WA CROCS Act prohibits using zip as a direct feature for price discrimination — use only for service-area aggregates.

## Artifact specification
A **Jupyter notebook** (exported as `.ipynb` OR a Python script with clear cell markers) documenting the full analysis. Required sections:

1. **Problem framing** — business objective, target definition, success metric, decision-use explained.
2. **Data audit** — row counts per table, date ranges, missingness, label prevalence by month (plot).
3. **Leakage checks** — explicit list of excluded/forbidden features; temporal-split diagram.
4. **EDA** — at least 4 plots: churn rate by tenure bucket, by plan tier, by outages_30d, by ticket volume. One correlation heatmap.
5. **Feature engineering** — lagged aggregates (outages_90d, rolling ticket count, MRR delta), tenure buckets, NPS decay, payment-method encoding. At least 15 features.
6. **Modeling** — baseline logistic, LightGBM with early stopping, and a calibrated version (isotonic or Platt). Report ROC-AUC, PR-AUC, Brier score on validation.
7. **Calibration** — reliability diagram and calibration curves before/after.
8. **Threshold selection** — cost-sensitive threshold using the $35 offer / $680 save economics; show expected-value-optimal cut.
9. **Business uplift estimate** — on test set: expected monthly $ saved vs blanket-offer baseline.
10. **Fairness / guardrails** — churn-rate error parity across plan tiers and service regions (aggregated zips, per compliance).
11. **Next steps & risks** — model drift plan, monitoring metrics, re-train cadence.

## Output format
Single `.ipynb` (or `.py` with `# %%` cell markers), ~340 lines. Must include at least 5 plots (embedded or saved to `./figures/`), reproducible with a fixed random seed (42) and a `pip freeze` requirements list at the top.

## Iteration targets
1. Replace random k-fold CV with **time-series / walk-forward** CV; show that the previous validation overstated AUC by measuring the delta.
2. Add SHAP values for the LightGBM model and produce a ranked feature importance plot + one individual-prediction explanation.
3. Implement calibration with isotonic regression and show Brier score improvement; update the threshold using the calibrated probabilities.
4. Add a drift-monitoring section: population stability index (PSI) on the top 5 features between train and test periods, with a threshold alert.
5. Add the fairness check: error-rate parity across plan tiers, and flag any tier with TPR gap >0.08 vs overall.
6. Replace the notional "blanket offer" baseline with a random-offer baseline at equal budget so uplift comparison is apples-to-apples.

## Success criteria
- No leakage: forbidden-feature list is explicit and the final model excludes them.
- Temporal split is correctly implemented (no future data in train).
- Calibration is measured (Brier + reliability diagram), not assumed.
- Threshold is chosen on business economics ($35 vs $680), not on a default 0.5.
- Uplift estimate is framed in dollars and compared to a realistic baseline.
- Code is reproducible end-to-end with a documented random seed and dependency pin.

## Scope target
V1 at ~15 min: data audit, 2-3 EDA plots, a basic LightGBM with default params and random CV, ROC-AUC on a holdout, and a prose "next steps" list. Calibration, SHAP, walk-forward CV, fairness checks, and uplift vs baseline are v2/v3 targets.
