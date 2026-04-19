# NIH R01 Grant Proposal — "Single-Cell Transcriptomic Mapping of Pancreatic Islet Dysfunction in Pre-T2D"

## Occupation
- **SOC:** 11-9121
- **Title:** Natural Sciences Managers

## Scenario
Dr. Mara Levchenko, Associate Director of the Islet Biology Core at Evergreen Diabetes Research Institute (EDRI), must submit an NIH R01 grant proposal (parent PA-25-303, NIDDK assignment preferred) for the October 5, 2026 standard deadline. The lab is re-applying after a prior submission (March 2026) received an impact score of 38 with recurring reviewer concerns about (1) justification of single-cell resolution over bulk approaches, (2) donor sample size and diversity, and (3) analytic plan for distinguishing technical from biological variability. The renewal proposal must address these critiques while incorporating the lab's newly validated pipeline for simultaneous snRNA-seq + ATAC-seq on human cryopreserved pancreatic islets.

## Inputs
The model starts with:

- **Specific Aims (prior submission, to be revised):**
  - Aim 1: Characterize single-cell transcriptomic heterogeneity of β-cells in normoglycemic vs. pre-T2D human donors (n=12 vs. 12).
  - Aim 2: Identify regulatory elements distinguishing dysfunctional β-cell states using integrated snATAC-seq.
  - Aim 3: Validate a set of candidate driver genes using CRISPRi in EndoC-βH1 cells and glucose-stimulated insulin secretion assays.
- **Prior critique summary (Summary Statement, March 2026):**
  - Impact score 38 (10th percentile ≈ 18).
  - Significance: strong (1.2).
  - Investigator: strong (1.5).
  - Innovation: moderate (2.8) — reviewer asked for justification over existing HPAP/IIDP datasets.
  - Approach: weak (4.1) — reviewers cited donor n, lack of demographic diversity, and insufficient detail on batch correction.
  - Environment: strong (1.4).
- **New preliminary data (since March):**
  - Pilot snRNA+ATAC on n=4 donors (2 normoglycemic, 2 pre-T2D) showing robust β-cell subclustering (8 transcriptomic states), and 2,340 differentially accessible peaks enriched for MAFA, NKX6-1, and UCN3 motifs.
  - Improved tissue dissociation protocol increasing islet yield 1.6x and viability from 78% to 91%.
  - Computational pipeline (Scanpy + Signac + scVI harmonization) benchmarked against 3 public datasets.
- **Lab resources:**
  - 2 postdocs (Dr. Jaya Ramanathan, comp bio; Dr. Omar Saidi, wet lab), 1 senior staff scientist, 3 graduate students.
  - Access to 28 human islet samples through IIDP partnership; demographically stratified: 12 Black/African American, 8 Hispanic, 8 non-Hispanic white; age 34-68; BMI range 24-38.
  - Co-I: Dr. Priscilla Vang (UCSF, bioinformatics); Co-I: Dr. Tariq Hashmi (Mt. Sinai, endocrinology).
- **Budget envelope:** R01 modular up to $250K direct/year, 5 years; non-modular justification acceptable for years with higher sequencing costs.
- **Institutional commitments available:** 0.25 FTE biostatistics core support; $45K pilot sequencing credit.

## Artifact specification
The model produces the core sections of an NIH R01 proposal following NIH guidelines. Required sections:
1. **Specific Aims page** (exactly 1 page when rendered; ~900-1,000 words) — opening paragraph framing significance and critical barrier, central hypothesis, three Aims with sub-aims and expected outcomes, closing "Innovation" paragraph. Must address the prior-submission Innovation and Approach critiques in the opening/closing framing.
2. **Research Strategy outline** — Significance (1/2 page), Innovation (1/2 page), Approach (approximately 3-4 pages as outline with detail in Aim 1 and partial Aim 2).
3. **Response-to-prior-critiques crosswalk** (separate Introduction page, required for A1 resubmission) — each prior concern stated, response with specific change, pointer to section of Research Strategy.
4. **Rigor and Reproducibility** — experimental design, sample-size justification with power calculation for key contrasts, biological and technical replicates, sex as a biological variable, blinding/randomization where applicable.
5. **Analytic plan detail** — batch correction approach (named methods), threshold criteria, multiple-hypothesis correction, planned sensitivity analyses. This directly answers prior-submission weakness.
6. **Timeline & milestones** — Year 1-5 by quarter. Must have quarterly or semi-annual decision points.
7. **Budget justification summary** — personnel % effort, key sequencing and reagent costs, year-over-year variation rationale. Reconcile to $250K direct/year modular (or justify non-modular).
8. **Risk & alternative strategies** — 4-6 risks (donor attrition, batch effects, cell viability, negative CRISPRi results) with alternative strategies.

Tone: scientifically rigorous, precise, NIH-convention-compliant. Active voice. No puffery; reviewers score down for promotional language.

## Output format
Markdown document, 10-14 pages rendered. Must include: Specific Aims as a distinguishable one-page section, a response-to-prior-critiques table, a power-calculation statement with numbers, and a quarter-by-quarter timeline table.

## Iteration targets
1. **Tighten the Specific Aims page to one page** — v1 will overflow. Iterate to a crisp one-page version with a central hypothesis sentence, Aims titled as testable statements (not "Characterize X"), and a closing impact paragraph.
2. **Elevate the Innovation framing** — v1 often says "we use single-cell." Iterate to: "We deploy the first paired snRNA+ATAC profiling in a demographically stratified pre-T2D cohort using a CRISPRi validation arm in primary human islets, integrated via [method]. This addresses the limitation of HPAP (frozen-tissue only) and IIDP (bulk-primarily) datasets."
3. **Sharpen the response-to-critiques section** — v1 may just describe changes. Iterate to a 3-column table: prior concern / specific revision / where to find it. Reviewers read this first.
4. **Power calculation specificity** — v1 may say "adequately powered." Iterate to: "With n=14 per group, we detect a 1.5-fold change in β-cell subcluster proportion at α=0.05, 80% power, assuming CV=0.35 based on pilot data (cite preliminary data figure)."
5. **Strengthen the analytic plan for batch correction** — v1 may name methods generically. Iterate to specify scVI for integration, Harmony or Combat-seq as sensitivity analyses, MELD or MiloDE for differential abundance testing, FDR control method, and a criterion for deciding integration quality pre-analysis (e.g., LISI scores).
6. **Make the CRISPRi validation plan quantitative and feasible** — v1 may say "validate top candidates." Iterate to: a rank-and-select rule (top 12 genes by a named composite score), EndoC-βH1 knockdown with 3 guides, primary islet validation in a subset, GSIS and RNA-seq readout, with expected time per gene and total target count achievable in Aim 3.

## Success criteria
(For evaluator use only.)
1. Specific Aims section is approximately one page (~900-1,000 words or equivalent) with a clear central hypothesis and three distinct, testable Aims.
2. Response-to-critiques directly addresses at least the three main prior concerns (innovation vs. HPAP/IIDP, donor diversity/sample size, batch correction/analytic rigor) with specific revisions.
3. Sample-size justification includes a power-calculation statement with specific effect size, α, and power.
4. Batch correction and integration approach names at least two specific methods (e.g., scVI + Harmony as sensitivity) and a quality-control criterion.
5. Timeline has Year 1-5 resolution with at least quarterly or semi-annual granularity and named milestones tied to Aims.
6. Budget justification addresses both modular cap and sequencing-cost year variation.
7. Donor demographic stratification is explicitly leveraged (not just mentioned) in Aim or analytic plan as a planned covariate or stratum.

## Scope target
A v1 at ~15 minutes should contain: a 1-page Specific Aims draft with central hypothesis and three Aims; a response-to-critiques table addressing the three main prior concerns; a Significance paragraph; an Approach outline for Aim 1 with sample size and key methods named; a power-calculation statement; and a year-by-year milestone list. Full Aim 2 and 3 Approach detail, risk/alternatives, and budget justification polishing are iteration targets.
