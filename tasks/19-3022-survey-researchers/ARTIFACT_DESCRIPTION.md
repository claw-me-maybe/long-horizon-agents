# Methodology Report and Pre-Analysis Plan: 2026 Midwest Rural Broadband Adoption Survey (Wave 2)

## Occupation
- **SOC:** 19-3022
- **Title:** Survey Researchers

## Scenario
Dr. Elena Vasquez, Principal Research Scientist at the Heartland Policy Institute (Iowa City, IA), is fielding Wave 2 of the Midwest Rural Broadband Adoption Survey (MRBAS) under a cooperative agreement with the USDA Rural Utilities Service (award 2024-RUS-RBI-0412, $847,000, PI: Vasquez; Co-PI: J. Okonkwo). Wave 2 data collection runs 4 May - 12 July 2026 across six states (IA, NE, KS, MO, SD, ND) with a target n=3,600 adults (18+) in counties classified non-metropolitan by the 2023 USDA ERS Rural-Urban Continuum Codes (RUCC 4-9). The artifact is the AAPOR Transparency Initiative-compliant Methodology Report and Pre-Analysis Plan (PAP), due to USDA RUS and posted to the Heartland open-methods portal before data release.

## Inputs
- **Study design:** Sequential mixed-mode (ABS address-based sampling -> push-to-web with mail and phone follow-up), with an embedded survey experiment on framing of federal broadband subsidies (BEAD program language vs. generic "internet assistance" language).
- **Sampling frame:** Marketing Systems Group (MSG) GENESYS ABS frame, residential addresses in 147 RUCC 4-9 counties; stratified by state x RUCC band (4-6 "micropolitan adjacent", 7-9 "remote rural"), with oversample of RUCC 8-9 (design-effect-adjusted target n=900 in remote strata). Hispanic oversample flagged via CASS-appended surname indicators in targeted census tracts (>15% Hispanic per ACS 5-year 2018-2022).
- **Mode protocol:** Wave 1 invitation (priority mail, $2 pre-incentive), reminder postcard at day 7, second full mailing at day 21 with paper questionnaire and BRE, CATI follow-up to matched landline/cell (days 35-60) for non-responders using Marketing Systems Group phone append. Web instrument hosted on Qualtrics XM (JFE v2026.03); CATI on Voxco Acuity 6.
- **Incentives:** $2 pre-incentive + $10 post-completion Amazon e-gift card or paper check (respondent choice). IRB-approved via University of Iowa IRB-02 (Protocol #202512-0487, expedited Category 7, approved 14 Feb 2026).
- **Wave 1 benchmarks (2024):** AAPOR RR3 = 14.8%; completion rate among web starters 87.2%; median completion time 14.1 min; 24 items flagged with item-nonresponse > 5%.
- **Weighting plan:** Base weight = inverse probability of selection, adjusted for subsampling and multi-adult-HH within-HH selection (Kish grid on paper, random-adult prompt on web). Nonresponse adjustment via weighting-class method using frame-level auxiliaries (census tract % rural, median HH income, % broadband subscription per ACS S2801). Raking to ACS 2023 1-year PUMS marginals on age x sex, education, race/Hispanic origin, and state x RUCC band, with trimming at the 2nd/98th percentiles following Battaglia et al. (2009).
- **Variance estimation:** Taylor series linearization in Stata 18 svy: with PSU = county, strata = state x RUCC band; replicate weights (100 BRR replicates) also produced for public-use file.
- **Standards invoked:** AAPOR Code of Professional Ethics and Practices (rev. 2021), AAPOR Transparency Initiative disclosure elements (2024), AAPOR Standard Definitions 10th ed. (2023), OMB Statistical Policy Directive No. 2, ISO 20252:2019, WAPOR/ESOMAR guidelines, 45 CFR 46 (Common Rule).
- **Pre-registration:** Study registered at OSF (osf.io/mrbas-w2, timestamp prior to first mailer drop) and EGAP Registry ID 20260422AA; pre-analysis plan hashed and deposited before first completed case.

## Artifact specification
Format: A combined Methodology Report + Pre-Analysis Plan, structured to satisfy (a) the 20 AAPOR Transparency Initiative disclosure elements and (b) pre-registration norms common in experimental social science (hypotheses stated before data lock, primary vs secondary outcomes distinguished, analysis decisions specified in advance). Third-person, past/future tense appropriate to the section (methodology executed = past; planned analyses = future or "will"). Must cite instruments by version and vendor, and cite standards and methods literature (e.g. Groves & Heeringa 2006 for responsive design, Kalton & Flores-Cervantes 2003 for weighting, Valliant Dever & Kreuter 2018 for variance estimation).

Required sections in order:
1. **Title, Authors, Affiliations, Funding, and Conflict Disclosure** — grant number, sponsor role ("USDA RUS reviewed the instrument but had no role in analysis"), IRB number.
2. **Study Objectives and Research Questions** — primary RQs and hypotheses, labeled H1, H2, ...; embedded experiment hypotheses stated with expected direction and effect size of interest (e.g. "H3: BEAD-framed subsidy description will increase stated intent-to-enroll by >= 4 percentage points (Cohen's h >= 0.08)").
3. **Target Population, Frame, and Coverage** — define target population, frame, coverage error sources, non-covered units.
4. **Sample Design** — stratification, allocation (include Neyman vs proportional justification), oversample mechanics, expected and achieved MOE for key estimates at alpha=0.05 assuming DEFF ~1.8.
5. **Instrument Development** — cognitive interviewing (n=24, two rounds per Willis 2005), expert review, Wave 1 carryover items, new items for 2026, reading-level assessment (Flesch-Kincaid target <= 8th grade), translation protocol (TRAPD for Spanish version per Harkness et al. 2010).
6. **Data Collection Protocol** — mode sequence, contact timing, response-enhancement tactics, field-period dates, interviewer training hours and content (for CATI), disposition code mapping to AAPOR categories.
7. **Response Rates and Disposition** — formulas used (RR1 vs RR3; CR1; e-estimation method for unknown eligibility per Callegaro & DiSogra 2008).
8. **Weighting and Variance Estimation** — base weights, nonresponse adjustment cells, raking targets and sources, trimming rules, final weight diagnostics (coefficient of variation, unequal weighting effect L).
9. **Measurement** — key constructs, scale sources (e.g. Pew broadband adoption battery, USDA ERS food-security short-form for related covariate), reliability evidence (Cronbach alpha for multi-item scales from Wave 1, target >= 0.75).
10. **Experiment Design and Pre-Analysis Plan** — randomization unit, balance checks planned, primary estimand (ATE on intent-to-enroll), secondary estimands, multiple-comparison correction (Benjamini-Hochberg FDR q=0.10 within family), subgroup analyses pre-specified (age band, prior broadband subscription, political party).
11. **Analysis Plan for Descriptive Estimates** — how means/proportions are computed, how small-cell suppression is applied (n < 30 or RSE > 30%).
12. **Ethical Considerations** — IRB, informed consent language, data security (encrypted at rest AES-256, FedRAMP Moderate for Qualtrics), re-identification risk assessment.
13. **Deviations from Pre-Registration** — section held open; deviations will be timestamped and logged.
14. **Limitations** — coverage, nonresponse, mode effects, self-report biases.
15. **Data and Code Availability** — public-use file release schedule, restricted-use conditions, DOI plan (Zenodo).
16. **Disclosure Checklist** — 20-row AAPOR TI table with disclosure element and pointer to the section where it is addressed.

Style conventions: APA 7th ed. for reference list; AAPOR Standard Definitions 10th ed. terminology (no use of "response rate" without specifying which formula); weighted N always reported with both unweighted n and weighted proportion; confidence intervals rather than bare point estimates for any preview estimates; explicit distinction between "pre-specified" and "exploratory" analyses.

## Output format
Single Markdown file of roughly 8-12 pages typeset (approximately 250-400 lines in Markdown). References compiled at the end in APA 7th. Instrument items not reproduced in full; rather, cited with item numbers keyed to the appendix instrument file (Appendix A, not produced here).

## Iteration targets
1. **AAPOR TI completeness** — The disclosure checklist must cover all 20 required elements (sponsor, purpose, population, frame, sample design, sample size, margin of sampling error and variance estimation method, field dates, mode(s), instrument languages, weighting, nonresponse treatment, disposition codes, response-rate calculation, etc.); flag any element marked "not applicable" with justification rather than leaving blank.
2. **Pre-analysis plan specificity** — Hypotheses must have pre-specified effect sizes, estimators, and decision rules (e.g. "we will reject H0 if the one-sided p < 0.025 after BH correction and the 90% CI excludes zero"); avoid vague "we will examine whether..." phrasing for primary outcomes.
3. **Coverage and nonresponse error treatment** — Distinguish coverage error (frame vs target population) from nonresponse error (frame vs responding sample); state auxiliary variables used in nonresponse adjustment and justify why they are plausibly related to both response propensity and key outcomes (per Little & Vartivarian 2005).
4. **Weighting transparency** — Raking targets must specify the ACS vintage, universe (e.g. civilian noninstitutionalized adults 18+), and source table numbers; trimming rule must be stated before data are seen.
5. **Experimental rigor** — Randomization mechanism, block/stratification structure, balance check plan, compliance/attrition handling, pre-specified subgroup list, and exploratory-vs-confirmatory labeling must all be present.
6. **Ethical and disclosure honesty** — Sponsor role statement must go beyond "sponsor had no role" to specify what sponsor did and did not do (e.g. reviewed instrument; had no access to raw data; did not approve publication of results).

## Success criteria
- Every AAPOR Transparency Initiative disclosure element is present and pointed to a specific section; none are silently omitted.
- Primary hypotheses are stated in testable form with pre-specified estimators, effect sizes of interest, alpha levels, and multiple-comparison handling; secondary and exploratory analyses are clearly demarcated.
- Sampling plan specifies frame, stratification, allocation rule, and expected MOE with a stated design effect assumption; oversample mechanics are justified quantitatively.
- Weighting plan names the specific auxiliary variables and population targets (with ACS table numbers/vintages) and specifies trimming rules ex ante.
- Response-rate reporting cites AAPOR Standard Definitions and names the specific formula used (e.g. RR3), including the e-estimation method for cases of unknown eligibility.
- Ethical treatment includes IRB number, consent language summary, data-security posture, and an explicit re-identification risk statement, not just boilerplate.

## Scope target
A v1 produced in ~15 minutes should contain: title block with funder, grant number, IRB, and PI; at least three labeled primary research questions or hypotheses with directional predictions; target population defined with RUCC reference; sample design described as stratified ABS with stated strata and oversample; mode sequence and field dates; response-rate formula named (RR3) with an illustrative calculation framework; weighting plan listing base weight, nonresponse adjustment, and raking variables with ACS source; experiment subsection identifying randomization unit, primary estimand (ATE), and multiple-comparison plan; an AAPOR TI disclosure checklist table listing all 20 elements with pointers (some may be "see Section X" placeholders). References section should cite at least five methods sources (AAPOR Standard Definitions, Groves & Heeringa, Kalton & Flores-Cervantes, Valliant et al., Harkness et al. or equivalent). It is acceptable for v1 to have cognitive-interview details thin and exploratory-analysis list short, which iteration will deepen.
