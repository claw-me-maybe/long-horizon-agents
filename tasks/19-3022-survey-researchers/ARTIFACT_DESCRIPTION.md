# Methodology Report and Pre-Analysis Plan: 2026 Midwest Rural Broadband Adoption Survey (Wave 2)

## Occupation
- **SOC:** 19-3022
- **Title:** Survey Researchers

## Scenario
Dr. Elena Vasquez, Principal Research Scientist at the Heartland Policy Institute
(Iowa City, IA), is fielding Wave 2 of the Midwest Rural Broadband Adoption Survey
(MRBAS) under a cooperative agreement with the USDA Rural Utilities Service
(award 2024-RUS-RBI-0412, $847,000, PI: Vasquez; Co-PI: J. Okonkwo). Wave 2 data
collection runs 4 May - 12 July 2026 across six states (IA, NE, KS, MO, SD, ND)
with a target n=3,600 adults (18+) in counties classified non-metropolitan by
the 2023 USDA ERS Rural-Urban Continuum Codes (RUCC 4-9). The artifact is the
AAPOR Transparency Initiative-compliant Methodology Report and Pre-Analysis Plan (PAP),
due to USDA RUS and posted to the Heartland open-methods portal before any data
is released; the pre-registration must be timestamped prior to the first completed
case so that experimental results cannot be retrofitted.

## Inputs

**Study design:**
- Sequential mixed-mode survey: address-based sampling (ABS) with push-to-web
  invitation, mail questionnaire and business-reply envelope (BRE) at Wave 2
  of contact, and CATI nonresponse follow-up for address-matched phone numbers.
- Embedded survey experiment on framing of federal broadband subsidies:
  half-sample receives BEAD (Broadband Equity, Access, and Deployment) program
  language, half receives generic "internet assistance" language, randomized
  at household (HH) level with block-randomization within state x RUCC stratum.

**Sampling frame:**
- Marketing Systems Group (MSG) GENESYS ABS frame, covering residential delivery
  points in 147 RUCC 4-9 counties.
- Stratified by state (6) x RUCC band (two bands: 4-6 "micropolitan/adjacent"
  and 7-9 "remote rural"), yielding 12 primary strata.
- Oversample of RUCC 8-9 remote rural stratum: design-effect-adjusted target
  n=900 in remote strata (vs. proportionate n=~540), to support precise
  rural-remote subgroup estimates.
- Hispanic oversample flagged via CASS-appended surname indicators in targeted
  census tracts with >15% Hispanic population per ACS 5-year 2018-2022.

**Mode protocol (contact schedule):**
- Day 0: Priority-mail invitation with $2 pre-incentive (cash), URL, and unique
  8-digit access code.
- Day 7: Reminder postcard with URL and access code.
- Day 21: Second full mailing with paper questionnaire, BRE, and incentive reminder.
- Days 35-60: CATI follow-up to matched landline/cell numbers (Marketing Systems
  Group phone append) for units that have not yet responded.
- Web instrument: Qualtrics XM (JFE v2026.03), mobile-responsive, median
  Wave 1 completion 14.1 minutes.
- CATI instrument: Voxco Acuity 6, interviewer team of 22 (16 English, 6 bilingual
  English/Spanish), trained 18 hours per new hire plus 6 hours refresher for returners.

**Incentives and IRB:**
- $2 cash pre-incentive in initial mailer.
- $10 post-completion incentive, respondent choice of Amazon e-gift card or paper check.
- IRB-approved via University of Iowa IRB-02, Protocol #202512-0487, expedited
  Category 7, approved 14 Feb 2026.

**Wave 1 (2024) benchmarks for planning:**
- AAPOR RR3 = 14.8%.
- Web-starter completion rate = 87.2%.
- Median completion time = 14.1 min; 90th percentile 24.6 min.
- 24 items flagged with item-nonresponse > 5% (predominantly income and
  political-party items); revised for Wave 2 per cognitive testing.

**Weighting plan (pre-specified):**
- Base weight = inverse probability of selection, adjusted for subsampling
  within RUCC 8-9 strata and for multi-adult-HH within-HH selection (Kish grid
  on paper, random-adult next-birthday prompt on web).
- Nonresponse adjustment via weighting-class method using frame-level auxiliaries
  (census tract % rural, median HH income, % broadband subscription per
  ACS table S2801) built into 12-18 weighting classes per Little & Vartivarian (2005).
- Raking to ACS 2023 1-year PUMS marginals on age x sex (5 x 2), education
  (4 levels), race/Hispanic origin (4 categories), and state x RUCC band (12 cells),
  using the IPF algorithm to convergence criterion 1e-5.
- Trimming at the 2nd and 98th percentiles following Battaglia, Izrael, Hoaglin,
  and Frankel (2009), with re-raking after trim.

**Variance estimation:**
- Taylor series linearization in Stata 18 svy: suite, declaring PSU = county,
  strata = state x RUCC band.
- Replicate weights (100 BRR replicates with Fay's adjustment rho=0.3) produced
  for the public-use file per Valliant, Dever, and Kreuter (2018).

**Standards and guidelines invoked:**
- AAPOR Code of Professional Ethics and Practices (revised 2021).
- AAPOR Transparency Initiative disclosure elements (2024 edition).
- AAPOR Standard Definitions 10th ed. (2023).
- OMB Statistical Policy Directive No. 2 (Standards and Guidelines for
  Statistical Surveys).
- ISO 20252:2019 Market, opinion and social research.
- WAPOR/ESOMAR Guidelines for Conducting Public Opinion Research.
- 45 CFR 46 (Common Rule) for human subjects protection.

**Pre-registration:**
- Study registered at OSF (osf.io/mrbas-w2) with timestamp prior to the first
  mailer drop.
- Pre-analysis plan also registered on the EGAP Registry (ID 20260422AA).
- Cryptographic hash of PAP deposited with the Heartland data-governance team
  before any completed case is loaded into the analytic environment.

## Artifact specification

**Format:** Combined Methodology Report + Pre-Analysis Plan, structured to
satisfy both (a) the AAPOR Transparency Initiative disclosure elements and
(b) pre-registration norms common in experimental social science (hypotheses
stated before data lock, primary vs secondary outcomes distinguished, analysis
decisions specified in advance).

**Voice and style:**
- Third person; past tense for executed methodology, "will" or future tense
  for planned analyses.
- Instruments cited by version and vendor (e.g. "Qualtrics XM, JFE v2026.03").
- Standards and methods literature cited in APA 7th ed. throughout; no
  undefined acronyms (expand AAPOR, RUCC, ACS, ABS, CATI, PUMS, etc. on first use).
- Weighted N always reported alongside unweighted n; confidence intervals
  reported in place of bare point estimates for any preview results.
- Clear distinction maintained between "pre-specified" and "exploratory" analyses.

**Required sections in order:**

1. **Title, Authors, Affiliations, Funding, and Conflict Disclosure** —
   full grant number, sponsor role statement ("USDA RUS reviewed the instrument
   but had no role in analysis, interpretation, or decision to publish"),
   IRB number, competing-interests disclosure.
2. **Study Objectives and Research Questions** — primary RQs and hypotheses
   labeled H1, H2, ...; experimental hypotheses stated with expected direction
   and effect size of interest (e.g. "H3: BEAD-framed subsidy description will
   increase stated intent-to-enroll by >= 4 percentage points, corresponding to
   Cohen's h >= 0.08").
3. **Target Population, Frame, and Coverage** — define target population, the
   frame used, coverage error sources, and units not covered (e.g. group
   quarters, unhoused adults, HHs without mail delivery).
4. **Sample Design** — stratification, allocation (Neyman vs proportional,
   with justification), oversample mechanics, and expected and achieved MOE
   for key estimates at alpha=0.05 assuming a design effect of approximately 1.8.
5. **Instrument Development** — cognitive interviewing (two rounds, n=24 total,
   following Willis 2005), expert review panel (n=5), Wave 1 carryover items,
   new items for 2026, reading-level assessment (Flesch-Kincaid target <= 8th
   grade), and translation protocol (TRAPD per Harkness, Villar, and Edwards 2010)
   for the Spanish version.
6. **Data Collection Protocol** — mode sequence, contact timing, response-
   enhancement tactics, field-period dates, interviewer training hours and content,
   and mapping of final disposition codes to AAPOR categories.
7. **Response Rates and Disposition** — formula used (RR1 vs RR3), completion
   rate (CR1), and e-estimation method for unknown eligibility per Callegaro
   and DiSogra (2008).
8. **Weighting and Variance Estimation** — base weights, nonresponse adjustment
   cells, raking targets and sources, trimming rules, and final weight
   diagnostics (coefficient of variation, Kish's unequal-weighting effect L).
9. **Measurement** — key constructs with scale sources (e.g. Pew Research Center
   broadband adoption battery, USDA ERS food-security short-form for a covariate),
   and reliability evidence (Cronbach's alpha for multi-item scales, target >= 0.75
   based on Wave 1).
10. **Experiment Design and Pre-Analysis Plan** — randomization unit (household),
    balance checks planned on pre-treatment covariates, primary estimand
    (average treatment effect on intent-to-enroll), secondary estimands,
    multiple-comparison correction (Benjamini-Hochberg FDR q=0.10 within family),
    and pre-specified subgroup analyses (age band, prior broadband subscription,
    political-party self-ID).
11. **Analysis Plan for Descriptive Estimates** — how weighted means and
    proportions will be computed, how subgroup estimates will be suppressed
    (unweighted n < 30 or relative standard error > 30%), and how missing data
    will be handled (multiple imputation via chained equations per Azur et al. 2011
    with m=20 imputations).
12. **Ethical Considerations** — IRB protocol, informed-consent language summary,
    data security posture (AES-256 encryption at rest, FedRAMP Moderate for
    Qualtrics), and re-identification risk assessment for the public-use file.
13. **Deviations from Pre-Registration** — section held open; deviations will be
    timestamped and logged with rationale.
14. **Limitations** — coverage, nonresponse, mode effects, self-report biases,
    generalizability bounds.
15. **Data and Code Availability** — public-use file release schedule,
    restricted-use data access conditions, Zenodo DOI plan, code repository on
    GitHub under the Heartland organization.
16. **Disclosure Checklist** — 20-row table listing each AAPOR Transparency
    Initiative disclosure element with a pointer to the section where it is addressed.

**Terminology conventions:**
- Use AAPOR Standard Definitions 10th ed. terminology; never write "response rate"
  without specifying which formula.
- Use "estimated" for all statistics drawn from the sample; "approximately" only
  where the number is itself a planning assumption.
- Cite all literature in APA 7th ed. with DOI where available.

## Output format
Single Markdown file of roughly 8-12 pages typeset (approximately 250-400 lines
in Markdown). References compiled at the end in APA 7th. Instrument items are
not reproduced in full; they are cited with item numbers keyed to Appendix A
(the instrument file, not produced in this artifact).

## Iteration targets

1. **AAPOR TI completeness** — The disclosure checklist must cover all 20
   required elements (sponsor, purpose, population, frame, sample design,
   sample size, margin of sampling error, variance estimation method, field
   dates, mode(s), instrument languages, weighting, nonresponse treatment,
   disposition codes, response-rate calculation, contact procedures, incentive
   details, question wording availability, contact information, date of release);
   any element marked "not applicable" must include explicit justification
   rather than being left blank.
2. **Pre-analysis plan specificity** — Hypotheses must have pre-specified effect
   sizes, estimators, and decision rules (e.g. "H0 is rejected if the one-sided
   p < 0.025 after BH correction and the 90% CI on the estimated ATE excludes
   zero"); vague "we will examine whether..." phrasing must be eliminated from
   primary-outcome descriptions.
3. **Coverage and nonresponse error treatment** — Coverage error (frame vs
   target population) must be clearly distinguished from nonresponse error
   (frame vs responding sample); the auxiliary variables used in nonresponse
   adjustment must be named and justified as plausibly related to both response
   propensity and key outcomes per Little and Vartivarian (2005).
4. **Weighting transparency** — Raking targets must specify ACS vintage,
   universe (e.g. civilian noninstitutionalized adults 18+), and source table
   numbers; the trimming rule must be stated before data are seen and not
   adjusted post-hoc.
5. **Experimental rigor** — Randomization mechanism, block/stratification
   structure, balance-check plan, compliance and attrition handling, the
   pre-specified subgroup list, and exploratory-vs-confirmatory labeling
   must all be present and internally consistent.
6. **Ethical and disclosure honesty** — The sponsor-role statement must go
   beyond "sponsor had no role" to specify what the sponsor did and did not do
   (e.g. reviewed instrument, had no access to raw data, did not approve
   publication of results).

## Success criteria

- Every AAPOR Transparency Initiative disclosure element is present and pointed
  to a specific section of the document; none are silently omitted.
- Primary hypotheses are stated in testable form with pre-specified estimators,
  effect sizes of interest, alpha levels, and multiple-comparison handling;
  secondary and exploratory analyses are clearly demarcated from confirmatory
  tests.
- The sampling plan specifies the frame, stratification, allocation rule, and
  expected MOE with a stated design effect assumption; oversample mechanics
  are justified quantitatively (expected sub-stratum precision).
- The weighting plan names the specific auxiliary variables and population
  targets (with ACS table numbers and vintages) and specifies trimming rules
  ex ante; weight diagnostics are listed.
- Response-rate reporting cites AAPOR Standard Definitions 10th ed. and names
  the specific formula used (e.g. RR3), including the e-estimation method
  for cases of unknown eligibility.
- Ethical treatment includes the IRB number, a consent-language summary,
  the data-security posture, and an explicit re-identification risk statement,
  not merely boilerplate assurances.

## Scope target

A v1 produced in roughly 15 minutes should contain:

- Title block with funder, grant number, IRB number, and PI name.
- At least three labeled primary research questions or hypotheses with
  directional predictions and stated effect sizes of interest.
- Target population defined with an explicit RUCC reference and state list.
- Sample design described as stratified ABS with named strata and the
  RUCC 8-9 oversample; planning MOE quoted for key overall and subgroup
  estimates.
- Mode sequence with day-numbered contact events and stated field dates.
- Response-rate formula named (RR3) with an illustrative calculation skeleton
  (numerator/denominator structure even if illustrative values only).
- Weighting plan listing base weight, nonresponse adjustment, and raking
  variables with the ACS source table (S2801) cited.
- Experiment subsection identifying randomization unit (household), primary
  estimand (ATE on intent-to-enroll), and multiple-comparison plan
  (BH FDR q=0.10).
- An AAPOR TI disclosure checklist table listing all 20 elements with
  pointers (some may be "see Section X" placeholders).
- References section citing at least five methods sources: AAPOR Standard
  Definitions, Groves & Heeringa (2006), Kalton & Flores-Cervantes (2003),
  Valliant et al. (2018), and Harkness et al. (2010) or Willis (2005).

It is acceptable for v1 to have the cognitive-interview details thin and the
exploratory-analysis list short; iteration per the targets above will deepen
both.
