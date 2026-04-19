# Analytical Method Validation Report: HPLC-UV Assay for Losartan Potassium in Film-Coated Tablets (50 mg)

## Occupation
- **SOC:** 19-2031
- **Title:** Chemists

## Scenario
Dr. Priya Ramanathan, Senior Analytical Chemist at Meridian Pharma Sciences (Cambridge, MA),
is leading method transfer of a reversed-phase HPLC assay for losartan potassium 50 mg
film-coated tablets from R&D to the QC laboratory supporting a commercial launch
scheduled for Q3 2026. The program is funded internally under project code LP-50-CMC-412,
and the method must satisfy ICH Q2(R2) validation expectations before the PAI
(pre-approval inspection) anticipated in August 2026. The artifact is the formal
Analytical Method Validation Report (AMVR) that will be filed with Module 3.2.P.5.3 of
the CTD and defended during FDA inspection; a failed validation package would delay
launch by an estimated 4-6 months and place approximately $28M in first-year revenue at risk.

## Inputs

**Drug product:**
- Losartan potassium 50 mg film-coated tablets (strength dose, once daily, antihypertensive).
- Excipients: microcrystalline cellulose (Avicel PH-102), pregelatinized starch,
  lactose monohydrate NF, magnesium stearate (vegetable-derived), and
  Opadry II white 85F18422 film coat.
- Tablet weight target 180.0 mg +/- 7.5%; assay label claim 50.0 mg losartan potassium.

**Analytical method under validation (AM-LP50-007 Rev 03):**
- Technique: reversed-phase HPLC with UV detection.
- Column: Waters XBridge C18, 150 x 4.6 mm, 3.5 um particle.
- Mobile phase A: 0.01 M KH2PO4 buffer adjusted to pH 3.0 +/- 0.05 with
  o-phosphoric acid.
- Mobile phase B: acetonitrile (HPLC grade, >=99.9%).
- Isocratic 65:35 (A:B), flow 1.0 mL/min, column temperature 35 C,
  injection volume 10 uL, detection UV at 254 nm.
- Run time 10 min; losartan retention time approximately 4.2 min; k' approximately 3.5.
- Sample prep: 20 tablets composite, ground, portion equivalent to 50 mg losartan
  extracted into diluent (mobile phase A : ACN 50:50) in 100 mL volumetric,
  sonicated 15 min, filtered 0.45 um PVDF, discarding first 3 mL.

**Instrumentation and data systems:**
- Primary: Agilent 1260 Infinity II LC system (asset tag QC-HPLC-07) with
  DAD G7117B for peak-purity evaluation.
- Secondary (intermediate precision): Agilent 1260 Infinity II (QC-HPLC-11) with
  VWD G7114A.
- Data system: Waters Empower 3 FR5 CDS, project "LP50_MV_2026", audit trail enabled.
- Balance: Mettler Toledo XPR205 (asset QC-BAL-14), last calibrated 12 Feb 2026.

**Reference standards and reagents:**
- Losartan Potassium USP Reference Standard, Lot R049F0, potency 99.8% (as-is),
  moisture 0.42% (KF), expiry 30 Nov 2027.
- Losartan Related Compound A (carboxylic acid impurity) USP RS, Lot F0J234.
- Acetonitrile (Honeywell LC-MS grade, Lot AX1289), water (Milli-Q, 18.2 Mohm-cm),
  KH2PO4 (ACS grade), o-phosphoric acid 85% (ACS grade).

**Regulatory and compendial references:**
- ICH Q2(R2) "Validation of Analytical Procedures" (adopted Nov 2023).
- USP General Chapter <1225> "Validation of Compendial Procedures".
- USP General Chapter <621> "Chromatography" for system suitability baseline.
- USP monograph "Losartan Potassium Tablets" (current revision).
- FDA Guidance for Industry "Analytical Procedures and Methods Validation for
  Drugs and Biologics" (July 2015).
- 21 CFR 211.165(e) and 21 CFR 211.194(a)(2) for cGMP documentation expectations.

**Validation parameters in scope:**
- Specificity, linearity, accuracy, precision (repeatability and intermediate
  precision), range, robustness, solution stability, filter compatibility,
  and system suitability.
- LOQ/LOD not required for this Category I assay but will be stated by calculation
  from signal-to-noise at low-end linearity.

**Pre-approved acceptance criteria (per protocol MV-LP50-001 Rev 02):**
- Assay recovery 98.0-102.0% of theoretical at 50%, 100%, and 150% label claim.
- Repeatability RSD <= 2.0% (n=6 independent preparations at 100%).
- Intermediate precision overall RSD <= 3.0% (2 analysts x 2 days x 2 instruments).
- Linearity r^2 >= 0.999 across 50-150% label claim; y-intercept <= 2.0% of 100% response.
- System suitability: USP tailing <= 2.0, theoretical plates >= 2000, RSD of
  5 replicate standard injections <= 2.0%.
- Solution stability: deviation from initial <= 2.0% absolute at each time point.

**Raw data available to the author:**
- All chromatograms, peak integration tables, weight sheets, and preparation
  records signed by analysts A. Chen (primary) and M. Okafor (secondary),
  reviewed by laboratory supervisor S. Delgado.
- Forced-degradation study completed per ICH Q1A(R2) stress conditions:
  acid 1 N HCl 60 C 2 h, base 1 N NaOH 60 C 2 h, peroxide 3% H2O2 RT 2 h,
  thermal 80 C 48 h, photolytic ICH Option 2 (1.2 million lux-hours visible,
  200 Wh/m^2 UV).
- Two validation deviations logged: DEV-2026-087 (column temperature excursion
  to 37 C for 14 min during Day 2 intermediate precision) and DEV-2026-092
  (single injection integration anomaly, reintegrated per SOP QC-025).

## Artifact specification

**Format:** GMP-compliant Analytical Method Validation Report following Meridian
SOP QA-040 "Preparation of Analytical Validation Reports" and structured to
ICH Q2(R2) expectations.

**Voice and style:**
- Passive voice, past tense, no first-person pronouns.
- Numerical results carried to the significant figures appropriate to instrument
  capability: assay values to 0.1%, RSD to 0.01%, r^2 to four decimals,
  recoveries to 0.1%, retention times to 0.01 min.
- Every numerical claim must be traceable to a raw-data reference
  (notebook page, Empower result ID, or attachment number).

**Required sections in order:**

1. **Cover page** — report number, title, product, method number, revision,
   effective date, approval signature block (Author / Technical Reviewer /
   QA Approver), and page count.
2. **Purpose and Scope** — what is being validated, against which method version
   (AM-LP50-007 Rev 03), and intended use (release and stability testing of
   commercial 50 mg tablets).
3. **Reference Documents** — protocol MV-LP50-001 Rev 02, relevant SOPs,
   and compendial references.
4. **Materials, Reagents, and Equipment** — itemized table with lot numbers,
   expiries, and calibration status.
5. **Summary of Method** — short narrative (5-10 lines), not full procedure;
   direct the reader to AM-LP50-007 for full instructions.
6. **Validation Results** — one subsection per parameter, each with
   (a) procedure executed, (b) pre-approved acceptance criterion,
   (c) tabulated results, and (d) explicit pass/fail statement.
   - 6.1 System Suitability
   - 6.2 Specificity — including placebo interference, forced-degradation peak
     purity via DAD, and mass balance (% assay + % total degradants = 95-105%).
   - 6.3 Linearity and Range — minimum 5 levels across 50-150%.
   - 6.4 Accuracy — spiked-placebo recovery, triplicate at 50%/100%/150%.
   - 6.5 Precision — Repeatability — n=6 at 100%.
   - 6.6 Precision — Intermediate Precision — 2 analysts x 2 days x 2 instruments.
   - 6.7 Robustness — Plackett-Burman or fractional factorial preferred over OFAT;
     typical factors: flow +/- 0.1 mL/min, column temp +/- 5 C, pH +/- 0.2,
     %B +/- 2% absolute, wavelength +/- 2 nm.
   - 6.8 Solution Stability — standard and sample at RT (bench) and 2-8 C,
     time points 0, 24, 48 h, each against freshly prepared reference.
   - 6.9 Filter Compatibility — unfiltered vs PVDF 0.45 um vs nylon 0.45 um,
     %difference from centrifuged reference.
7. **Deviations and Investigations** — each protocol deviation or OOT result
   logged with investigation number and disposition.
8. **Conclusion** — explicit statement that the method is validated for its
   intended use, with any stated limitations.
9. **Attachments** — chromatograms, calculation spreadsheets, and raw-data pointers.

**Table/figure conventions:**
- Tables numbered (Table 1, Table 2, ...) with title above.
- Figures numbered with caption below.
- Units follow SI / compendial conventions.
- "n/a" permitted only where a parameter is genuinely inapplicable, with justification.

## Output format
Single Markdown file representing the full AMVR narrative and tables,
approximately 8-14 pages typeset (roughly 250-400 lines in Markdown).
Tables rendered as Markdown pipe tables. No external images required;
chromatograms referenced as "Attachment X" placeholders with figure captions only.

## Iteration targets

1. **Specificity rigor** — Ensure the forced-degradation section reports peak
   purity angle vs purity threshold for each stress condition, calculates
   mass balance within 95-105%, and identifies the major degradant under base
   hydrolysis (losartan carboxylic acid impurity) against the ICH identification
   threshold for a daily dose of 50 mg.
2. **Statistical defensibility** — Intermediate precision must report a proper
   nested ANOVA (analyst, day, instrument) with between-group and within-group
   variance components rather than a single pooled RSD; linearity must include
   a residuals plot interpretation and the y-intercept expressed as a percentage
   of the 100% response (ICH Q2(R2) expects <= 2%).
3. **Traceability** — Every tabulated value must cite its source (e.g.
   "Empower Result ID 20260312-A-LP50-STD-005 [Att. 3, p. 12]"); no orphan
   numbers anywhere in the body of the report.
4. **Robustness design** — Upgrade from one-factor-at-a-time to a fractional
   factorial (e.g. 2^(5-2) or Plackett-Burman with 5 factors in 8 runs),
   with a main-effects table and an explicit conclusion on which factors are
   critical to method performance.
5. **Regulatory voice** — Remove hedging language ("seems", "appears",
   "approximately met"), replace with declarative pass/fail statements tied to
   numeric acceptance criteria; ensure each deviation is linked to a formal
   investigation number (INV-2026-XXX) rather than described informally.
6. **System suitability embedding** — Include a dedicated SST criteria table
   formatted to be copied verbatim into the routine method (AM-LP50-007),
   so QC analysts can apply it without re-derivation from the validation report.

## Success criteria

- Every ICH Q2(R2) validation characteristic required for a Category I assay
  (specificity, linearity, range, accuracy, precision, robustness) is addressed
  with a pre-stated acceptance criterion and an explicit pass/fail conclusion.
- At least one forced-degradation condition produces meaningful degradation
  (5-20% loss of parent) and peak purity is evaluated via DAD, with purity
  angle < purity threshold for the losartan peak under that condition.
- Accuracy is demonstrated by spiked-placebo recovery (not merely serial
  dilution of standard) at a minimum of three levels covering 50-150% of label
  claim, with at least triplicate preparations per level.
- Linearity r^2, slope, intercept, and residual analysis are reported, with the
  intercept expressed as a percentage of the 100% response.
- Intermediate precision includes at least two analysts on different days using
  at least two different columns or instruments, with variance decomposed
  rather than collapsed into a single pooled statistic.
- The conclusion explicitly names the method identifier and revision being
  validated (AM-LP50-007 Rev 03) and states any limitations (e.g. "not
  validated for content uniformity at the single-tablet level").

## Scope target

A v1 produced in roughly 15 minutes should contain:

- Cover page with report number, method identifier, revision, and signature block.
- Purpose and Scope paragraph naming AM-LP50-007 Rev 03 and the intended use.
- Reference Documents list including protocol, ICH Q2(R2), USP <1225>.
- Materials/Equipment table with at least columns, reagents, reference standard,
  and instrument identifiers.
- Summary of Method paragraph (5-10 lines) matching the method conditions
  in Inputs.
- All nine validation subsections (6.1-6.9) present, each with the pre-approved
  acceptance criterion stated and plausible tabulated results (skeletal tables
  acceptable for robustness and stability).
- Conclusion paragraph that explicitly passes the method for intended use.
- Placeholder Attachments list (Att. 1 Chromatograms, Att. 2 Linearity
  calculation sheet, etc.).

Internal consistency requirements for v1:

- Forced degradation must appear under Specificity with at least five rows:
  acid, base, peroxide, thermal, photolytic.
- Linearity standards concentrations must align with the stated 50-150% range.
- System suitability RSD and tailing values quoted in multiple sections must
  match exactly.
- Reference-standard potency (99.8%) must flow through all assay calculations.

It is acceptable for v1 to have shallow ANOVA treatment and OFAT robustness;
iteration will deepen these per the iteration targets above.
