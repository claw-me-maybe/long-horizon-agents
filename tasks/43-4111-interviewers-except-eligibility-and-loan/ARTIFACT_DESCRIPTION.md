# Household Health Survey Interview Case Summary and Data Quality Notes — MERIDIAN-H Study, Household 2026-04-0341

## Occupation
- **SOC:** 43-4111
- **Title:** Interviewers, Except Eligibility and Loan

## Scenario
You are Teresa Vasquez, a field interviewer on the MERIDIAN-H longitudinal household health study (a CDC-funded cooperative study administered by RTI International in partnership with the University of North Carolina Gillings School of Global Public Health). You conducted an in-home interview on April 15, 2026, in Greensboro, NC, with Household 2026-04-0341. The interview ran 2 hrs 40 min across two respondents and produced both structured survey data (CAPI entered) and open-ended narrative that must be summarized. Your Field Supervisor, Dr. Anne Westbury, requires a case summary with data-quality notes within 72 hours (due April 18), before the case is locked for data processing. The summary will feed a supervisor spot-check and, if the case is selected, a data-quality audit by the prime contractor.

## Inputs

**Case metadata:**
- Case ID: 2026-04-0341
- Wave: 3 (of 6 planned)
- Household size: 4 (2 adults, 2 minors)
- Respondents interviewed: HH1 ("Ms. J.R.", age 47, female, Hispanic); HH2 ("Mr. D.M.", age 49, male, Non-Hispanic Black). Both adults in household interviewed. Minors not interviewed (per protocol, parent-proxy only).
- Interview language: 60% English / 40% Spanish (HH1's preference). Teresa is certified bilingual.
- Date/time: 2026-04-15, 5:40 PM - 8:20 PM
- Location: kitchen table, household home. Children present during first 40 min (ages 8 and 12), then went to neighbor's; Mr. D.M. arrived home at 6:15, participated from 6:20.
- Prior wave participation: HH1 Waves 1 and 2; HH2 Wave 1 only (missed Wave 2).

**Survey modules administered (CAPI):**
- A. Household roster and demographics
- B. Health status and conditions (self-report)
- C. Health care access and utilization
- D. Insurance coverage history
- E. Food security (USDA 6-item)
- F. Mental health (PHQ-2 + GAD-2)
- G. Substance use (AUDIT-C; NIDA quick screen)
- H. Neighborhood and housing
- I. COVID-19 experience (long COVID module)
- J. Narrative segment (unstructured, audio-recorded with consent) — "Tell me about a time in the past year when you had trouble getting the care you or someone in your family needed."

**Data quality events logged during the interview:**
1. HH1 paused 4 minutes at Module G (substance use); asked to confirm confidentiality; continued after explanation.
2. HH2 declined 2 items in Module F (mental health PHQ-2 both items).
3. Tablet connection dropped during Module H, 7:14-7:23; reconnection successful, no data loss per CAPI log.
4. Children's return from neighbor's at 7:45 created 6-min pause during Module I.
5. HH1's answer in Module C re: PCP visits in past 12 mo (said "three" verbally; entered "3"); later in Module J narrative, HH1 referenced "four visits" — inconsistency noted.
6. HH2 appeared fatigued after Module G; Teresa offered break; HH2 declined and pushed to finish.
7. Module J: 18 minutes of narrative audio, both respondents contributing.

**Narrative highlights (for the case summary):**
- HH1: Described a February 2026 urgent care visit for HH1's mother (non-household member, lives nearby) that was denied coverage due to an out-of-network determination; mother is on Medicare Advantage with a different network. Patient navigation not provided. HH1 handled rebilling herself over 6 weeks.
- HH2: Described a work-related musculoskeletal injury in November 2025; saw an occupational health provider twice, then was "cut off" by the employer's workers-comp carrier; sought care at a community health center subsequently; reports ongoing back pain, no current treatment.
- HH1 (returning to topic): Noted her 8-year-old's dental visit was delayed 4 months waiting for a Medicaid dental provider accepting new patients.
- Both expressed frustration but also "we're doing okay compared to some people we know."

**Interviewer observations (Teresa's field notes):**
- Home well-kept; evidence of adequate food in kitchen; no obvious housing instability.
- HH1 holds primary health-information role in household; was coaching HH2 on recall.
- HH2 engaged more on work-injury topics; more reticent on mental health.
- Respondent burden appeared manageable but non-trivial. Incentive ($60 per adult) provided at close; both signed receipt.

**Protocol rules relevant here:**
- Case summary must not identify the household by name, street address, or any direct identifier. Use anonymized labels only.
- Narrative quotes can be paraphrased; direct quotes require respondent's prior opt-in to quotation (both opted in at consent).
- Data quality events must be logged per item where applicable in CAPI metadata; the case summary also flags them at case level.
- Inconsistencies between structured and narrative data must be noted, not reconciled by interviewer — data team decides.

## Artifact specification
Produce a case summary with data quality notes, structured as:

1. **Case header** — case ID, wave, date, duration, interviewer ID, language mix, location type, respondents (anonymized labels, e.g., "Adult-1 female, 47, Hispanic"), minors present but not interviewed.

2. **Completion status** — modules administered, any refusals/partial-refusals by module, total time, device stability.

3. **Respondent experience narrative** — 1 paragraph per respondent, neutral, focused on engagement quality and comfort; do not interpret.

4. **Substantive narrative (Module J) summary**
   - Theme 1: Out-of-network denial and self-advocacy (HH1's mother case)
   - Theme 2: Workers' comp cutoff and safety-net care (HH2)
   - Theme 3: Medicaid dental access (HH1's child)
   - Theme 4: Resilience/comparison framing (both)
   - Paraphrased content only unless direct quote is tagged with quote-consent citation.

5. **Data quality events log** — enumerated, per-item where applicable (e.g., "Module F item 2: refused — respondent HH2"), with interviewer observation when relevant.

6. **Structured-narrative inconsistencies** — the "three vs four PCP visits" discrepancy logged, no reconciliation attempted. Any other divergences.

7. **Protocol deviations (if any)** — none expected, but if any (e.g., minors briefly present at start), noted.

8. **Follow-up actions** — cases requiring supervisor review (e.g., HH1 mother's billing issue described — is this a patient-navigation referral opportunity? Protocol may allow offering the participant-care-navigation hotline).

9. **Interviewer reflection** — short section: what went well, what was hard, what would you do differently. Kept honest and non-defensive.

10. **Sign-off block** — interviewer ID, date submitted, intended supervisor reviewer.

Tone: neutral, observational, research-appropriate. Do not advocate or interpret themes (that's the qualitative analyst's job downstream). Maintain participant anonymity strictly. Use the codebook/module letters when referring to sections.

## Output format
Single Markdown file, ~3 pages rendered (210-340 lines source).

## Iteration targets
1. **Scrub identifiers rigorously** — v1 may leave "Greensboro," "mother," "8-year-old," etc.; v2 uses anonymized labels ("Adult-1," "extramural family member," "child-2"), strips location beyond state/region if protocol requires, and reviews narrative paraphrases for inadvertent re-identification.
2. **Don't interpret narrative themes** — v1 may say "systemic barriers to care"; v2 keeps summary descriptive ("HH1 described an out-of-network coverage denial for a non-household member"); interpretation is for downstream coders.
3. **Log the PHQ-2 refusal precisely** — module-level note is not enough; item-level (which items), who refused, and confirmation that CAPI metadata matches.
4. **Flag the 3-vs-4 visits discrepancy without resolving** — v2 records both data points, does not pick a winner, marks for data-team adjudication.
5. **Honor the quotation consent correctly** — direct quotes are permitted here (both opted in); v2 can use sparingly where high-value, else paraphrase. v1 should not invent direct quotes.
6. **Reflect honestly on interviewer effects** — e.g., Teresa's bilingual role; children-present period; the ending fatigue — in a brief reflection that serves data-quality interpretation, not self-assessment.

## Success criteria
- No direct identifiers (name, street, household-identifiable detail) appear in the summary.
- All logged data quality events (PHQ-2 refusals, tablet drop, pause events, fatigue) are present with correct module references.
- The 3-vs-4 PCP visits inconsistency is flagged for the data team, not reconciled.
- Narrative themes are reported descriptively, not interpreted.
- Protocol rules (minors not interviewed, quote-consent status, anonymization) are visibly respected.
- Interviewer reflection is short, specific, and non-defensive.

## Scope target
A v1 at ~15 minutes should contain: case header, completion status with module list, respondent experience narratives, narrative themes summarized descriptively (at least 3 of 4), a data quality events log with item-level refusals, the structured-narrative inconsistency flagged, and an interviewer reflection. Tightening anonymization, removing any interpretive language, and formalizing quote-consent attribution belong to iteration.

## Example of v1 failure modes
- Writing interpretive statements: "This household exemplifies systemic failures in network adequacy." Interpretation is a coder's job, not an interviewer's.
- Including location detail beyond state/region: "Greensboro" or "the household on X Road" must not appear.
- Listing "refused PHQ-2" at module level instead of item level; the protocol specifies item-level logging.
- Treating the 3-vs-4 PCP visits inconsistency as a reconciliation task: picking one or "averaging"; protocol requires flagging, not resolving.
- Quoting the respondents verbatim beyond the scope of opt-in; though both opted in at consent, selective quotation still requires relevance and minimum-necessary framing.
- Mentioning the 8-year-old's dental referral using the child's age and gender, creating potential re-identification; the module spec permits "child-2" labeling.
- Using the interviewer reflection as advocacy or performance self-assessment ("I felt the participants needed more support"); reflection is for data-quality interpretation, not emotional content.
- Omitting the protocol-permitted patient-navigation hotline referral consideration; if protocol allows offering resources in response to issues raised in Module J, this should be flagged as a supervisor-review item.

## Common pitfalls to avoid
- Do not describe the household by income, education, or immigration-related detail not in the structured modules.
- Do not speculate on why HH2 refused the PHQ-2 items (could be stigma, could be fatigue, could be preference for privacy); log the refusal, not the inference.
- Do not list the employer or workers-comp carrier names even if respondents named them; those are identifiable and irrelevant to case-summary aggregation.
- Do not use "frustration" or "anger" as affect labels; use behavioral description ("HH1 raised her voice while describing the February urgent-care denial" if accurate, or omit entirely).
- Do not annotate the file with the audio file path or recording device serial; study protocol keeps media references in a separate chain-of-custody log.

## Evaluator notes (context for scoring, not for the model)
- The 43-4111 interviewer artifact is unusual in the SOC list because the core work is verbal and transactional. The case summary + data quality notes is the artifact-shaped output that does survive the interview and does have iteration room, specifically around: anonymization rigor, item-level quality logging, discipline against interpretation, and protocol-faithful handling of structured-narrative inconsistencies.
- MERIDIAN-H, Household 2026-04-0341, and all respondents are fictional. The multi-module CAPI structure (A-I + narrative J), the Wilson/6-item/AUDIT-C/PHQ-2 module components, and the $60 per-adult incentive all mirror real research-interviewer practice.
- A strong v2: strips identifiers rigorously, logs the PHQ-2 items at the item level, preserves the 3-vs-4 visits inconsistency without reconciliation, and keeps the interviewer reflection short and data-quality-oriented.

## Anonymization conventions the model should follow
- Adult-1, Adult-2 for respondents; avoid "husband/wife" or relationship inference beyond what structured data supports.
- Child-1, Child-2 for minors; no age beyond cohort (e.g., "school-age child").
- "Extramural family member, older adult, on Medicare Advantage" in place of "HH1's mother."
- Month/year granularity for event dates; no exact date unless required by protocol and non-identifying.
- State/region granularity for location; no city/neighborhood/street.
- No direct employer names, insurer names, or provider names unless they are population-scale and non-identifying (e.g., "a community health center" is fine; "Cone Health's Main Street clinic" is not).

## What distinguishes this from an ethnographic field note
- The artifact is protocol-governed, not reflective or literary.
- It is paired with structured CAPI data and must reference that data by module letter.
- It is written for a supervisor and a data team, not for publication.
- It is evaluated for compliance (anonymization, quote-consent, item-level logging) as much as for content.
- Interpretation is explicitly forbidden; description is required.

## Final sanity checks before submitting to Dr. Westbury
- All direct identifiers scrubbed (no household name, street, city, employer, provider names).
- Item-level logging of PHQ-2 refusals, not module-level.
- The 3-vs-4 PCP visits inconsistency is flagged but NOT reconciled.
- Narrative themes described, never interpreted.
- Interviewer reflection is short, specific, and data-quality-oriented.
