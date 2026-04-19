# NIH R01 Grant Proposal (A1 Resubmission) — "Single-Cell Transcriptomic Mapping of Pancreatic Islet Dysfunction in Pre-T2D"

## Occupation
- **SOC:** 11-9121
- **Title:** Natural Sciences Managers

## Scenario
Dr. Mara Levchenko, Associate Director of the Islet Biology Core at Evergreen Diabetes
Research Institute (EDRI), must submit an NIH R01 grant proposal (parent PA-25-303, NIDDK
assignment preferred) for the October 5, 2026 standard deadline. The lab is re-applying
(A1 resubmission) after a prior submission (March 2026) received an impact score of 38
with recurring reviewer concerns about (1) justification of single-cell resolution over
bulk approaches, (2) donor sample size and diversity, and (3) analytic plan for
distinguishing technical from biological variability. The renewal proposal must address
these critiques while incorporating the lab's newly validated pipeline for simultaneous
snRNA-seq + ATAC-seq on human cryopreserved pancreatic islets. This is Dr. Levchenko's
first R01 as a PI (she was previously a Co-I); the lab's funding depends materially on
this grant.

## Inputs
The model starts with:

### Specific Aims (prior submission, to be revised)
- Aim 1: Characterize single-cell transcriptomic heterogeneity of β-cells in normoglycemic
  vs. pre-T2D human donors (n=12 vs. 12).
- Aim 2: Identify regulatory elements distinguishing dysfunctional β-cell states using
  integrated snATAC-seq.
- Aim 3: Validate a set of candidate driver genes using CRISPRi in EndoC-βH1 cells and
  glucose-stimulated insulin secretion assays.

### Prior critique summary (Summary Statement, March 2026 submission)
- Impact score 38 (10th percentile ≈ 18; fundable range ≈ top 12th percentile)
- Significance: strong (criterion score 1.2)
- Investigator: strong (1.5)
- Innovation: moderate (2.8) — "Reviewers question whether single-cell adds sufficient
  value beyond existing HPAP and IIDP bulk datasets; innovation claim undermined."
- Approach: weak (4.1) — "Donor n underpowered for demographic stratification; lacks
  detail on batch correction and technical-biological variance decomposition; analytic
  plan insufficient."
- Environment: strong (1.4)
- Three specific written critiques from reviewers (key):
  - R1: "The central hypothesis is that β-cell transcriptomic heterogeneity drives
    pre-T2D, but the proposed n=12 per group is unlikely to detect subcluster shifts
    with meaningful effect sizes."
  - R2: "No donor demographic stratification plan. HPAP has shown that AA donors have
    different islet composition; this must be addressed."
  - R3: "Batch correction is stated as 'will use Harmony' but no validation criteria or
    sensitivity analysis."

### New preliminary data (since March 2026)
- Pilot snRNA+ATAC on n=4 donors (2 normoglycemic, 2 pre-T2D) showing robust β-cell
  subclustering into 8 transcriptomic states (Figure 1, manuscript in prep)
- 2,340 differentially accessible peaks enriched for MAFA, NKX6-1, and UCN3 motifs
  (Figure 2)
- Improved tissue dissociation protocol increasing islet yield 1.6x and viability from
  78% to 91%
- Computational pipeline (Scanpy + Signac + scVI harmonization) benchmarked against 3
  public datasets (HPAP, Fasolino et al. 2022, Shrestha et al. 2021) showing 89% concordance
  in major cell-type annotations

### Lab resources
- 2 postdocs (Dr. Jaya Ramanathan, computational biology; Dr. Omar Saidi, wet lab)
- 1 senior staff scientist
- 3 graduate students (2 in CB rotation, 1 wet)
- Access to 28 human islet samples through IIDP partnership, demographically stratified:
  12 Black/African American, 8 Hispanic, 8 non-Hispanic white
  Age range: 34-68; BMI range 24-38; 14 male, 14 female
- Tissue culture and ChIP-seq core on site
- Biostatistics core (Dr. Lina Abramson) with 0.25 FTE committed
- Co-I: Dr. Priscilla Vang (UCSF, bioinformatics, snATAC expertise)
- Co-I: Dr. Tariq Hashmi (Mt. Sinai, endocrinology, clinical phenotyping)

### Budget envelope
- R01 modular up to $250K direct/year, 5 years (total direct $1.25M)
- Non-modular justification acceptable for years with higher sequencing costs (Years 1-2)
- Institutional commitments: 0.25 FTE biostatistics core, $45K pilot sequencing credit,
  $25K computational compute allocation

### Published context (for Innovation framing)
- HPAP (Human Pancreas Analysis Program): large-scale bulk + some scRNA dataset; limited
  ATAC integration; heavy cryopreservation caveats
- IIDP (Integrated Islet Distribution Program): sample source rather than dataset
- Fasolino et al. 2022: Nature Metabolism — scRNA of T1D
- Shrestha et al. 2021: Cell Metabolism — multi-omic islet dataset but T2D-established,
  not pre-T2D

## Artifact specification
The model produces the core sections of an NIH R01 proposal following NIH guidelines.
Required sections:

1. **Specific Aims page** (exactly 1 page when rendered; ~900-1,000 words) — opening
   paragraph framing significance and critical barrier, central hypothesis, three Aims
   with sub-aims and expected outcomes, closing "Innovation" paragraph. Must address the
   prior-submission Innovation and Approach critiques in the opening/closing framing.
2. **Research Strategy outline** — Significance (~1/2 page), Innovation (~1/2 page),
   Approach (approximately 3-4 pages as outline with full detail in Aim 1 and partial
   detail in Aim 2).
3. **Response-to-prior-critiques crosswalk** (separate Introduction page, required for
   A1 resubmission) — each prior concern stated verbatim or summarized, response with
   specific change, pointer to section of Research Strategy. Must address at minimum the
   three numbered R1/R2/R3 critiques above.
4. **Rigor and Reproducibility** — experimental design, sample-size justification with
   power calculation for key contrasts, biological and technical replicates, sex as a
   biological variable statement, blinding/randomization where applicable.
5. **Analytic plan detail** — batch correction approach (named methods: scVI primary,
   Harmony sensitivity), threshold criteria (LISI score target), multiple-hypothesis
   correction (FDR method), planned sensitivity analyses. This directly answers prior-
   submission weakness on Approach.
6. **Timeline & milestones** — Year 1-5 by quarter, with Go/No-Go decision points tied
   to specific data readouts.
7. **Budget justification summary** — personnel % effort for PI, postdocs, staff;
   key sequencing and reagent costs; year-over-year variation rationale; reconcile to
   $250K direct/year modular (or justify non-modular for Years 1-2).
8. **Risk & alternative strategies** — 4-6 risks (donor attrition, batch effects,
   cell viability, negative CRISPRi results, shift in sequencing technology) with
   alternative strategies.

Tone: scientifically rigorous, precise, NIH-convention-compliant. Active voice. No
puffery; reviewers score down for promotional language ("groundbreaking,"
"paradigm-shifting"). First-person plural ("we") throughout. Hypotheses stated as
testable predictions, not research questions.

## Output format
Markdown document, 10-14 pages rendered. Must include: Specific Aims as a distinguishable
one-page section, a response-to-prior-critiques table (3 columns), a power-calculation
statement with numbers, and a quarter-by-quarter timeline table. Preliminary data figures
can be referenced as "Figure 1" / "Figure 2" with descriptive captions, even without
actual images.

## Iteration targets
1. **Tighten the Specific Aims page to one page** — v1 will overflow. Iterate to a crisp
   one-page version with (a) a one-sentence central hypothesis, (b) Aims titled as
   testable statements ("Determine whether X..." not "Characterize X"), and (c) a closing
   impact paragraph that lands the significance.
2. **Elevate the Innovation framing** — v1 often says "we use single-cell." Iterate to:
   "We deploy the first paired snRNA-seq + snATAC-seq profiling in a demographically
   stratified pre-T2D cohort (n=28, including 12 AA, 8 Hispanic donors), integrated via
   scVI with Harmony sensitivity analysis and a CRISPRi validation arm in primary human
   islets. This addresses the limitation of HPAP (bulk RNA + partial scRNA, limited ATAC
   integration) and IIDP (sample source without integrated analysis) by generating the
   first pre-T2D-specific multi-omic cell atlas with demographic diversity."
3. **Sharpen the response-to-critiques section** — v1 may just describe changes. Iterate
   to a 3-column table: prior concern (verbatim quote) / specific revision (with page
   reference to Research Strategy) / preliminary data that supports the revision.
   Reviewers read this first and hardest.
4. **Power calculation specificity** — v1 may say "adequately powered." Iterate to:
   "With n=14 per group (normoglycemic vs. pre-T2D), we detect a 1.5-fold change in
   β-cell subcluster proportion at α=0.05, 80% power, assuming CV=0.35 based on
   preliminary data (Figure 1, subcluster 3 variance)." Use MiloDE or similar
   differential-abundance framework for the calculation.
5. **Strengthen the analytic plan for batch correction** — v1 may name methods
   generically. Iterate to specify: scVI for primary integration (pre-registered
   hyperparameters), Harmony and Combat-seq as sensitivity analyses, MELD or MiloDE for
   differential abundance testing, FDR control via Benjamini-Hochberg, and a criterion
   for deciding integration quality pre-analysis (e.g., LISI scores > 1.5 at
   patient-id level; <0.5 at cell-type level).
6. **Make the CRISPRi validation plan quantitative and feasible** — v1 may say "validate
   top candidates." Iterate to: a rank-and-select rule (top 12 genes by a composite score
   of differential expression + differential accessibility + motif enrichment + prior
   literature support), EndoC-βH1 knockdown with 3 guides/gene via lentiviral dCas9-KRAB,
   primary islet validation in a subset of 4 donors for top 3 hits, GSIS and RNA-seq
   readout, with expected time per gene (2 months including primary islet validation for
   lead candidates) and total target count achievable in Aim 3 (12 genes screened,
   3-4 deeply validated).

## Success criteria
(For evaluator use only.)
1. Specific Aims section is approximately one page (~900-1,000 words or equivalent) with
   a clear central hypothesis and three distinct, testable Aims stated as hypotheses.
2. Response-to-critiques directly addresses at least the three main prior concerns
   (innovation vs. HPAP/IIDP; donor diversity/sample size; batch correction/analytic
   rigor) with specific revisions and page references.
3. Sample-size justification includes a power-calculation statement with specific effect
   size, α, power, and stated variance assumption.
4. Batch correction and integration approach names at least two specific methods (e.g.,
   scVI + Harmony as sensitivity) and a quality-control criterion (e.g., LISI score).
5. Timeline has Year 1-5 resolution with at least quarterly or semi-annual granularity
   and named milestones tied to Aims and to Go/No-Go decision points.
6. Budget justification addresses both modular cap and sequencing-cost year variation.
7. Donor demographic stratification (12 AA, 8 Hispanic, 8 non-Hispanic white) is
   explicitly leveraged in Aim or analytic plan as a planned covariate or stratum — not
   just mentioned in the Environment section.
8. CRISPRi validation plan has a named ranking rule and a feasible target count.

## Scope target
A v1 at ~15 minutes should contain: a 1-page Specific Aims draft with central hypothesis
and three Aims; a response-to-critiques table addressing the three main prior concerns
(even if short); a Significance paragraph; an Approach outline for Aim 1 with sample
size and key methods named; a power-calculation statement; and a year-by-year milestone
list. Full Aim 2 and 3 Approach detail, risk/alternatives, and budget justification
polishing are iteration targets for v2/v3. By v3, the Specific Aims should fit one page,
the Innovation paragraph should contrast explicitly with HPAP/IIDP/Fasolino/Shrestha,
and the CRISPRi validation should have a rank-and-select rule.
