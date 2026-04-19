# Shareholder Letter: FY2026 Annual Report — Tessen Therapeutics

## Occupation
- **SOC:** 11-1011
- **Title:** Chief Executives

## Scenario
Tessen Therapeutics (NASDAQ: TSSN), a clinical-stage biotech with a market cap of $1.9B, is writing the CEO shareholder letter for its FY2026 annual report (fiscal year ended December 31, 2026). CEO Dr. Ingrid Halvorsen must publish it alongside the 10-K on February 26, 2027. The year contained a major clinical setback (TSN-201 Phase 2 missed primary endpoint in atopic dermatitis, April 2026) and a strategic pivot toward the company's oncology program (TSN-405, which received FDA Fast Track designation in September). Cash runway is 22 months. Shareholder sentiment is skeptical — stock is down 38% YTD, and an activist investor (Fenwick Park Capital, 6.8% holder) has called for a board refresh.

## Inputs
The model starts with:

- **Year in review (facts):**
  - Jan 2026: Entered 2026 with $392M cash.
  - April 15, 2026: TSN-201 Phase 2b readout — failed primary endpoint (EASI-75 at Week 16: 31% vs. 28% placebo, p=0.41). Stock dropped 52% on the day.
  - June 2026: Announced strategic reset — paused TSN-201, concentrated resources on TSN-405 (oncology) and preclinical pipeline (TSN-620, TSN-710).
  - July 2026: Workforce reduction of 22% (84 employees); restructuring charge $17M.
  - September 2026: TSN-405 received FDA Fast Track in relapsed/refractory DLBCL. Phase 1 data showed 41% ORR at the top dose (n=22).
  - November 2026: Completed $140M follow-on at $8.50/share (pre-money $1.2B; 18.5% dilution).
  - December 2026: Fenwick Park Capital files 13D, calls for two board seats.
  - End FY2026: Cash $286M; projected burn $155M/year; runway 22 months.
- **Forward pipeline milestones:**
  - TSN-405 Phase 2 registrational start: Q2 2027
  - TSN-405 interim data: Q4 2027
  - TSN-620 IND filing: Q3 2027
- **Comparable peer performance:** Average biotech XBI index -14% in 2026; TSSN -38%. Oncology-focused peers +6%.
- **Tone guidance from IR advisors:** Acknowledge TSN-201 failure directly; do not minimize. Avoid defensive language re: Fenwick Park but do not endorse activist demands.

## Artifact specification
A CEO shareholder letter with the following structure:
1. **Opening (200-300 words)**: Honest framing of the year. Must acknowledge TSN-201 failure on the second paragraph at latest. Avoid corporate euphemism ("challenging year," "navigated headwinds") — shareholders see through it.
2. **What we learned from TSN-201** — substantive, specific (biomarker hypothesis, trial design, patient selection). Demonstrates scientific integrity, not just spin.
3. **The strategic reset** — why oncology, why TSN-405 specifically, the scientific case. Connect to the Phase 1 signal (41% ORR at top dose, n=22) and its significance in r/r DLBCL context.
4. **2026 operational actions** — the workforce reduction, the follow-on, the Fast Track. Treat difficult decisions (like the 22% RIF) with dignity, not passive voice.
5. **2027 milestones and capital plan** — what investors should watch, what de-risks value creation, how the $286M is being deployed. Include a near-term catalyst list.
6. **On governance** — acknowledge Fenwick Park's engagement constructively but not capitulatingly. State the board's posture.
7. **Closing** — not a platitude. Something that a skeptical shareholder reading at minute 6 finds memorable.

Tone: candid, scientifically literate, accountable. Written in first-person singular (CEO voice) but recognizing the team. Avoid three words entirely: "excited," "thrilled," "journey."

Style constraints: paragraphs < 120 words, total ~1,600-2,400 words. No bullet lists in the opening or closing; bullets allowed in pipeline and milestones. Avoid cliches of the form "we are committed to creating shareholder value."

## Output format
A Markdown document formatted as a shareholder letter (no headings beyond H2 section breaks, no tables in the body — tables reserved for an appendix). Target 1,600-2,400 words. Must pass a "read aloud" test: flows when read.

## Iteration targets
1. **Replace corporate-euphemism verbs in v1** — "navigated," "pivoted," "transformed" are giveaways. Iterate toward plain verbs and specific nouns. (E.g., "paused TSN-201" not "transitioned away from our dermatology program.")
2. **Give the TSN-201 failure a real post-mortem** — v1 usually has 2 sentences. A great version has 1-2 paragraphs: the biomarker rationale that didn't hold, the patient population heterogeneity, the design choice that in hindsight limited ability to detect effect — enough that a biotech analyst feels they understand what the company learned.
3. **Concretize TSN-405's scientific case** — v1 may say "promising mechanism." Iterate to: what's the target, why is r/r DLBCL the right indication, how the 41% ORR at top dose compares to approved agents in the same setting (e.g., CAR-T, bispecifics), and what the Phase 2 design will test.
4. **Handle Fenwick Park with precision** — v1 tends to either ignore them or thank them effusively. Iterate to a one-paragraph posture: we listen, we evaluate on merits, our board has added X directors since Y, we are proceeding on our strategic plan.
5. **Make the capital plan legible** — v1 often just says "22 months of runway." A better version walks through 2027 burn rate, how much is R&D vs. G&A, and how the company would handle a financing pre-Phase 2 interim.
6. **End on something memorable** — v1 closes with "thank you to our team, patients, and shareholders." Iterate to a closing paragraph that picks one specific truth about the year or the mission and lands it.

## Success criteria
(For evaluator use only.)
1. TSN-201 failure is named in the first 300 words with the actual endpoint result (EASI-75, p=0.41 or similar specificity).
2. The three banned words ("excited," "thrilled," "journey") do not appear.
3. Fenwick Park is addressed in a dedicated governance paragraph that is neither dismissive nor capitulating.
4. At least one paragraph demonstrates scientific specificity beyond press-release language (e.g., discusses ORR in context of comparable agents, or discusses a specific biomarker hypothesis from TSN-201).
5. A quantitative 2027 milestone list exists with at least 3 items and specific quarters.
6. The letter reads in a consistent first-person CEO voice throughout; no mid-document drift into third-person corporate voice.
7. Total length is 1,600-2,400 words; opening paragraph is < 200 words.

## Scope target
A v1 at ~15 minutes should contain: opening that names TSN-201 failure early, a brief TSN-405 scientific case (even if not deeply comparative), explicit mention of the RIF and the follow-on, a 2027 milestone list, a short Fenwick Park paragraph, and a closing. TSN-201 post-mortem depth, TSN-405 competitive positioning, and capital plan detail are all iteration targets.
