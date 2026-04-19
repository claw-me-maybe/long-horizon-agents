# Shareholder Letter: FY2026 Annual Report — Tessen Therapeutics

## Occupation
- **SOC:** 11-1011
- **Title:** Chief Executives

## Scenario
Tessen Therapeutics (NASDAQ: TSSN), a clinical-stage biotech with a market cap of $1.9B at
year-end, is writing the CEO shareholder letter for its FY2026 annual report (fiscal year
ended December 31, 2026). CEO Dr. Ingrid Halvorsen must publish it alongside the 10-K on
February 26, 2027. The year contained a major clinical setback (TSN-201 Phase 2 missed
primary endpoint in atopic dermatitis, April 2026) and a strategic pivot toward the company's
oncology program (TSN-405, which received FDA Fast Track designation in September). Cash
runway is 22 months. Shareholder sentiment is skeptical — stock is down 38% YTD, and an
activist investor (Fenwick Park Capital, 6.8% holder) has called for a board refresh and
has filed a 13D. The letter will be read by sell-side analysts (Bernstein, Leerink,
Wedbush), long-only shareholders, the activist, regulators, and the scientific community.

## Inputs
The model starts with:

### Year in review (key events, with facts)
- January 2026: Entered 2026 with $392M cash; consensus Wall Street view was "cash runway
  through Phase 2b TSN-201 readout, with optionality."
- April 15, 2026: TSN-201 Phase 2b readout in moderate-to-severe atopic dermatitis —
  failed primary endpoint (EASI-75 at Week 16: 31% on TSN-201 vs. 28% on placebo, p=0.41).
  Secondary endpoints also missed. Stock dropped 52% on the day to close at $6.80.
- June 2026: Announced strategic reset — paused TSN-201 entirely, concentrated resources
  on TSN-405 (oncology) and preclinical pipeline (TSN-620 in solid tumors, TSN-710 in
  hematologic malignancies).
- July 2026: Workforce reduction of 22% (84 employees); restructuring charge $17M. RIF
  fell disproportionately on the dermatology team (as that program was paused).
- September 2026: TSN-405 received FDA Fast Track designation in relapsed/refractory
  diffuse large B-cell lymphoma (r/r DLBCL). Phase 1 data (presented at ESMO) showed 41%
  overall response rate (ORR) at the 600mg top dose (n=22; 9 responders including 2 CRs),
  with manageable safety (no DLTs at RP2D).
- November 2026: Completed $140M follow-on offering at $8.50/share (pre-money $1.2B;
  18.5% dilution; clears runway through Phase 2 TSN-405 interim).
- December 2026: Fenwick Park Capital files 13D with 6.8% stake, calls for two board seats
  and a "strategic review."
- End FY2026: Cash $286M; projected burn $155M/year; runway 22 months (through Feb 2029).

### Forward pipeline milestones
- TSN-405 Phase 2 registrational start: Q2 2027 (planned n=90, single-arm in r/r DLBCL)
- TSN-405 Phase 2 interim data: Q4 2027 (first ~30 patients)
- TSN-620 IND filing: Q3 2027
- TSN-710 preclinical proof-of-concept data package: Q2 2027

### Comparable peer performance
- XBI biotech index: -14% in 2026 (vs. TSSN -38%)
- Oncology-focused small/mid-caps: +6% (TSSN thus badly underperformed the most relevant
  comp set)
- The three closest business-model comps (Arvinas, Kymera, Nuvation) averaged -2% for 2026

### Activist background
- Fenwick Park has a track record of successful proxy campaigns (3 of 4 wins in biotech
  since 2022). Their typical ask: faster capital return or strategic sale. Their public
  letter (Dec 14, 2026) asked for (a) two board seats, (b) engagement of a strategic
  advisor, and (c) a "comprehensive cost review."

### Tone guidance from IR advisors
- Acknowledge TSN-201 failure directly; do not minimize. Shareholders already know.
- Avoid defensive language re: Fenwick Park but do not endorse activist demands.
- The scientific community reads for whether leadership learned from TSN-201. Show what
  was learned.
- Long-only holders read for capital allocation discipline — the $140M raise needs to be
  contextualized, not justified defensively.

## Artifact specification
A CEO shareholder letter with the following implicit structure (no Table of Contents; the
letter is read as continuous prose with H2 section breaks at most):

1. **Opening (200-300 words)**: Honest framing of the year. Must acknowledge TSN-201
   failure by the second paragraph at latest. Avoid corporate euphemism ("challenging
   year," "navigated headwinds") — shareholders see through it. Land on the year's single
   most important truth.
2. **What we learned from TSN-201** — substantive, specific (biomarker hypothesis, trial
   design, patient selection, where the science and the clinical evidence diverged).
   Demonstrates scientific integrity, not spin. This is the section where scientific
   credibility is re-earned.
3. **The strategic reset** — why oncology, why TSN-405 specifically, the scientific case
   and the commercial logic. Connect to the Phase 1 signal (41% ORR at top dose, n=22) and
   its significance in r/r DLBCL context (comparable agents: CAR-T axi-cel ~52% CR rate but
   with cytokine release; bispecifics like glofitamab ~39% CR; TSN-405 differentiator must
   be named — e.g., outpatient, oral, combinability).
4. **2026 operational actions** — the workforce reduction, the follow-on, the Fast Track.
   Treat difficult decisions (like the 22% RIF) with dignity, not passive voice. Do not
   thank employees who were laid off; do not pretend the decision was easy.
5. **2027 milestones and capital plan** — what investors should watch, what de-risks value
   creation, how the $286M is being deployed. Include a near-term catalyst list and
   honest discussion of the runway-to-data question.
6. **On governance** — acknowledge Fenwick Park's engagement constructively but not
   capitulatingly. State the board's posture and what's already been done (new audit-chair,
   any director additions, etc. — these can be reasonable stated facts for the scenario).
7. **Closing** — not a platitude. Something that a skeptical shareholder reading at minute
   6 finds memorable. The closing paragraph should carry the letter's emotional weight.

Tone: candid, scientifically literate, accountable. Written in first-person singular (CEO
voice: "I" for personal responsibility statements, "we" for team achievements) but
recognizing the team.

### Banned words/phrases (reviewer will check)
- "excited," "thrilled," "journey"
- "navigated headwinds," "transformative year"
- "committed to creating shareholder value"
- "unprecedented," "leverage our platform"

### Style constraints
- Paragraphs < 120 words
- Total length 1,600-2,400 words
- No bullet lists in the opening or closing paragraphs; bullets allowed in pipeline and
  milestone sections
- Must pass a "read aloud" test: flows when read

## Output format
A Markdown document formatted as a shareholder letter (no headings beyond H2 section
breaks, no tables in the body — tables reserved for a pipeline summary appendix). Target
1,600-2,400 words.

## Iteration targets
1. **Replace corporate-euphemism verbs in v1** — "navigated," "pivoted," "transformed" are
   giveaways. Iterate toward plain verbs and specific nouns. (E.g., "We paused TSN-201"
   not "We transitioned away from our dermatology program." "We laid off 84 colleagues" not
   "We right-sized our organization.")
2. **Give the TSN-201 failure a real post-mortem** — v1 usually has 2 sentences. A great
   version has 1-2 paragraphs: the biomarker rationale (e.g., IL-13/IL-4 pathway
   hypothesis), the patient population heterogeneity (broad enrollment including moderate
   and severe, which may have diluted signal in a population where approved agents already
   perform well), the trial design choice that in hindsight limited ability to detect
   effect (comparator arm, duration of exposure, endpoint selection) — enough that a
   biotech analyst feels they understand what the company learned and that it's
   transferable to future programs.
3. **Concretize TSN-405's scientific case** — v1 may say "promising mechanism." Iterate
   to: what's the target (state a hypothetical but plausible mechanism — e.g., a novel
   covalent BTK inhibitor with activity in resistant clones), why r/r DLBCL is the right
   indication (unmet need post-CAR-T, commercial opportunity), how the 41% ORR at top
   dose compares to approved agents in the same setting (CAR-T, bispecifics, Pola-R-ICE),
   and what the Phase 2 design will test (single-arm, biomarker-enriched? all-comer?).
4. **Handle Fenwick Park with precision** — v1 tends to either ignore them or thank them
   effusively. Iterate to a one-paragraph posture: we listen, we evaluate on merits, our
   board has discussed, we engage constructively, our strategic plan proceeds.
5. **Make the capital plan legible** — v1 often just says "22 months of runway." A better
   version walks through 2027 burn rate ($155M), how much is R&D vs. G&A (typically 75/25
   for companies like this), what the Q4 interim readout triggers in either direction, and
   how the company would handle a financing pre-interim (would not require raise between
   now and Q4 '27).
6. **End on something memorable** — v1 closes with "thank you to our team, patients, and
   shareholders." Iterate to a closing paragraph that picks one specific truth about the
   year or the mission and lands it — a mission reminder, a patient's story, a scientific
   observation that crystalizes why the company exists.

## Success criteria
(For evaluator use only.)
1. TSN-201 failure is named in the first 300 words with the actual endpoint result
   (EASI-75 31% vs. 28% placebo, p=0.41, or equivalent specificity).
2. The banned words ("excited," "thrilled," "journey," "navigated headwinds,"
   "transformative year") do not appear.
3. Fenwick Park is addressed in a dedicated governance paragraph that is neither
   dismissive nor capitulating.
4. At least one paragraph demonstrates scientific specificity beyond press-release
   language (discusses ORR in context of comparable agents, or discusses a specific
   biomarker hypothesis from TSN-201).
5. A quantitative 2027 milestone list exists with at least 3 items and specific quarters.
6. The letter reads in a consistent first-person CEO voice throughout; no mid-document
   drift into third-person corporate voice.
7. Total length is 1,600-2,400 words; opening paragraph is <200 words.
8. The 22% RIF is named in operational voice (not euphemistic).

## Scope target
A v1 at ~15 minutes should contain: opening that names TSN-201 failure by paragraph two
with at least one specific number; a brief TSN-405 scientific case (even if not deeply
comparative); explicit mention of the RIF and the follow-on; a 2027 milestone list; a
short Fenwick Park paragraph; and a closing. TSN-201 post-mortem depth, TSN-405 competitive
positioning detail, and capital plan granularity are iteration targets for v2/v3. By v3,
the letter should pass the "read aloud" test and the closing should be memorable rather
than a platitude.
