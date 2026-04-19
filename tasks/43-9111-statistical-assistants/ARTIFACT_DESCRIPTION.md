# County Public Health Vaccination Coverage Data Tables and Methods Note — Marquette County Q1 2026

## Occupation
- **SOC:** 43-9111
- **Title:** Statistical Assistants

## Scenario
You are Priya Seshadri, a statistical assistant at the Marquette County (WI) Department of Public Health, reporting to Dr. Helen Ngo (Epidemiologist). Dr. Ngo has a State Health Quarterly Briefing on April 29, 2026, where she must present Q1 2026 childhood vaccination coverage by ZIP code and demographic stratum. She has given you the raw immunization registry pull and asked you to produce, by April 23, a clean data-tables package with a short methods note. The package will be the statistical backbone of her slide deck; others will design the charts. A secondary audience is the state's Data Transparency Portal, which will ingest the tables verbatim.

## Inputs

**Raw data description (the model should treat as if provided):**
- Immunization registry extract (WI-IR): 18,412 child records, ages 0-6, residing in Marquette County as of 2026-03-31.
- Fields: child ID (anonymized), DOB, ZIP (5-digit), sex (M/F/X/Missing), race (6 categories + Multiple + Missing), ethnicity (Hispanic/Non-Hispanic/Missing), insurance (Medicaid/Private/Uninsured/Other/Missing), each vaccine dose record with date administered.
- Data issues already noted on your intake QC:
  - 347 records missing ZIP (1.88%)
  - 612 records missing race (3.33%)
  - 89 records with DOB after 2026-03-31 (erroneous; exclude)
  - 214 records with >1 address in registry during Q1 — use most recent
  - WI-IR known to under-capture private-insurance administrations by ~6-9% (state's published estimate)

**Target denominator:** Census Bureau 2024 ACS 5-year estimates for Marquette County children 0-6 by ZIP, used as the population denominator. Known discrepancy vs. registry counts.

**Vaccines to report (per state quarterly spec):**
1. DTaP (≥4 doses by 24 mo)
2. IPV (≥3 doses by 24 mo)
3. MMR (≥1 dose by 24 mo)
4. Varicella (≥1 dose by 24 mo)
5. Hib (≥3 doses by 24 mo)
6. PCV13 (≥4 doses by 24 mo)
7. HepB (≥3 doses by 18 mo)
8. RV (≥2 or 3 doses depending on product, by 8 mo)
9. Influenza (≥1 dose during 2025-2026 season)
10. Combined Series ("7-vaccine combined") — standard CDC definition

**Reporting spec from state:**
- Age cohorts: 19-35 months (primary), 24-35 months (secondary for some antigens).
- Stratification: ZIP, sex, race, ethnicity, insurance.
- Coverage = numerator (children up-to-date) / denominator (eligible children in cohort).
- Small-cell suppression: <11 numerator OR <20 denominator → suppress, show "†"
- Confidence intervals: Wilson score 95% CI
- Equity analysis: disparity ratio vs. overall county average

**Historical comparison:** Q1 2025 coverage figures provided by state (one column per antigen).

**File formats requested:**
- Primary deliverable: a Markdown/CSV-friendly table set that can be copied into both a slide deck and the state portal.
- Methods note: separate document, 1 page.

## Artifact specification
Produce a data tables package plus methods note:

1. **Methods note (1 page)**
   - Data source (WI-IR extract pull date, record count before/after exclusions)
   - Denominator source (ACS 2024 5-year, limitations)
   - Age cohort definitions
   - Up-to-date definitions per antigen (with dose counts and age thresholds)
   - Missingness handling (ZIP imputation rule, race/ethnicity treatment, "Missing" as its own category vs. excluded)
   - Small-cell suppression rule
   - Confidence interval method (Wilson 95%)
   - Known limitations: WI-IR private-insurance undercapture 6-9%; self-reported race in registry
   - Comparison to Q1 2025: like-for-like or change in definition?
   - Prepared by / date / version

2. **Table set (primary)**
   - **Table 1.** County-level coverage, by antigen, 19-35 mo cohort, with 95% CI, and Δ vs. Q1 2025.
   - **Table 2.** Coverage by ZIP (all 7 ZIPs in county), per antigen, 19-35 mo. Small cells suppressed.
   - **Table 3.** Coverage by race/ethnicity, per antigen. Suppressed where cells too small.
   - **Table 4.** Coverage by insurance status, per antigen.
   - **Table 5.** Disparity ratios: each stratum's coverage ÷ county overall, per antigen, flagged if <0.85 or >1.15.
   - **Table 6.** Combined-series coverage by stratum (single summary column).

3. **Appendix**
   - Suppression counts per table (how many cells suppressed, why)
   - Record-level exclusion ledger: 89 erroneous DOBs, 347 missing ZIPs, etc.
   - QC checks performed (denominator-numerator consistency, dose-date monotonicity)

Tone: neutral, technical, auditable. Every number should be traceable. No narrative interpretation — that's Dr. Ngo's job. Use footnotes liberally for caveats.

## Output format
Single Markdown file with embedded tables. ~3-4 pages rendered (220-380 lines source). Can include fabricated but plausible numbers.

## Iteration targets
1. **Apply suppression consistently** — v1 may forget to suppress small cells; v2 applies the <11 numerator OR <20 denominator rule uniformly and counts suppressed cells in the appendix.
2. **Present CIs correctly** — Wilson 95%, not normal-approximation; narrower than Wald for small denominators; clearly labeled.
3. **Handle the "Missing" problem transparently** — don't silently drop; show "Missing" as its own row where appropriate; note in methods; avoid imputing race.
4. **Flag disparity appropriately** — the <0.85 or >1.15 threshold should be applied mechanically; include a footnote reminding readers that a flag is a prompt, not a conclusion.
5. **Note the WI-IR under-capture honestly** — v1 may report raw numbers; v2 includes a methods caveat and, for the combined-series, a sensitivity note ("if WI-IR under-captures private-insurance administrations by 6-9%, true coverage could be ~X-Y percentage points higher").
6. **Make Q1 2025 comparison like-for-like** — if antigen definitions or age cohorts changed, say so; don't present Δ without noting.

## Success criteria
- Every number is traceable to a defined numerator/denominator.
- Suppression rule is applied consistently and audited in appendix.
- CIs appear for every estimate, with method named.
- Methods note fits on one page and is readable by non-statisticians.
- No interpretation, no advocacy, no recommendation language — these belong to the epidemiologist.
- Exclusions (89 erroneous DOBs, 347 missing ZIPs) are disclosed and quantified.
- Formatting is portable: Markdown tables copy cleanly to both slide deck and state portal.

## Scope target
A v1 at ~15 minutes should include: methods note with at least 6 of the 10 methodological elements, Tables 1-3 populated with plausible numbers, Wilson CIs on the county-level table, and at least a partial Table 5 disparity ratio with threshold flagging. Completing Tables 4-6, refining suppression audit, and adding the under-capture sensitivity note belong to iteration.

## Example of v1 failure modes
- Reporting point estimates without CIs; or reporting Wald (normal-approximation) CIs instead of Wilson, which are misleading at small denominators common in by-ZIP breakdowns.
- Silently imputing race based on surname or geography; never acceptable.
- Reporting "Missing" race as a bucket but then including it in the denominator for disparity ratios, which distorts equity readings.
- Suppressing cells with <11 numerator but forgetting the <20 denominator half of the rule.
- Applying the disparity threshold (0.85 / 1.15) without noting that it is a flag, not a conclusion; readers will over-read flags as causal claims.
- Reporting Q1 2026 vs. Q1 2025 as a Δ without disclosing that any antigen definition or age cohort changed (if it did).
- Producing tables that are visually clean but not machine-parseable for the state's Data Transparency Portal ingest.
- Interpreting findings ("coverage lower in ZIP 53949 likely due to…"); this is Dr. Ngo's job, not yours.

## Common pitfalls to avoid
- Do not compute coverage with a registry-derived denominator when the spec calls for ACS-derived; this inflates rates where registry enrollment is high.
- Do not carry Q1 2026 to more than 1 decimal place in the primary table; CIs already convey precision.
- Do not produce heat-map-style tables in Markdown (color coding does not survive the ingest pipeline); if flagging, use text markers like asterisks or daggers with a footnote key.
- Do not include any child-level record in the tables; aggregate only.
- Do not include PII in the exclusion ledger; row-level reasons for exclusion are fine (e.g., "DOB > report end date: 89 records"), but no identifiers.

## Evaluator notes (context for scoring, not for the model)
- The 43-9111 statistical-assistant role is well-suited to artifact iteration because the craft layer (suppression, CIs, missingness handling, like-for-like comparison, producing neutral tables) is exactly what improves with mentoring over months, and the task is defined enough that failure modes are concrete and detectable.
- MERIDIAN-H, Marquette County data, and the antigen reporting spec are fictional but realistic. The Wilson CI, <11/<20 suppression rule, and CDC combined-series definition reflect actual public-health statistical practice. Wisconsin's WI-IR registry has a known private-insurance under-capture pattern modeled here.
- A strong v2 handles every mode of missingness transparently, applies suppression mechanically, distinguishes flags from conclusions, and disclaims the under-capture bias in the methods note.

## Machine-parseability requirements
- Column headers must be stable strings (no line breaks, no merged cells).
- Numeric cells must be plain numbers or the explicit suppression marker "†" (not "n/a", not em-dashes).
- The table must be reproducible in CSV without post-processing (no rowspans, no colspans).
- Any footnote markers (†, ‡, §) appear in a single key block at the bottom of each table.

## What distinguishes this from a narrative public-health report
- No interpretation, causation, or recommendation.
- Every estimate has a CI.
- Every cell has a clear status: reportable, suppressed, or excluded, with reason.
- The methods note is more detailed than a typical briefing would carry.
- The output is designed for ingest, not for reading.

## Expected Wilson CI formula (for the model's reference)
For proportion p̂ = x/n, 95% CI is:
(p̂ + z²/(2n) ± z·√(p̂(1-p̂)/n + z²/(4n²))) / (1 + z²/n)
where z = 1.96.

This produces narrower, more accurate bounds than Wald approximation at small n, which is material for by-ZIP and by-race stratifications.

## Final sanity checks before submitting to Dr. Ngo
- Every reportable estimate has a Wilson 95% CI.
- Suppression applied uniformly (<11 numerator OR <20 denominator).
- "Missing" categories are reported, not silently dropped.
- No interpretive language appears.
- Methods note fits on one page and is readable by non-statisticians.
- Exclusion ledger matches the record count delta (18,412 → processed records).
