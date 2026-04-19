# MTM Comprehensive Medication Review and Patient Handout for Ms. Priya Dalrymple (Polypharmacy, 11 Meds)

## Occupation
- **SOC:** 29-1051
- **Title:** Pharmacist

## Scenario
Ms. Priya Dalrymple is a 74-year-old woman enrolled in a Medicare Part D Medication Therapy Management (MTM) program at Willow Grove Community Pharmacy. She was flagged for a Comprehensive Medication Review (CMR) on 2026-04-15 after her last two refills triggered interaction alerts and she reported "sometimes feeling woozy when I stand up." A pharmacist-led CMR appointment is scheduled for 2026-04-22; the artifact is the pharmacist's written CMR workup (for the clinical record and prescriber communication) plus a one-page patient-facing Medication Action Plan (MAP) handout.

## Inputs

### Patient profile (from pharmacy PMR + intake interview)
- **Demographics:** 74 F, 65 kg, 162 cm, CrCl 48 mL/min (Cockcroft-Gault from today's Cr 1.1)
- **Allergies:** Sulfa drugs (rash)
- **Active problem list:** HTN, T2DM, hyperlipidemia, osteoarthritis (bilateral knees), GERD, insomnia, anxiety, seasonal allergies, mild cognitive concerns per daughter
- **Adherence:** Pharmacy refill data shows diltiazem PDC 72%, metformin PDC 95%, others >85%
- **Recent BP log (home cuff, average of last 14 days):** 138/82 mmHg; orthostatic drop reported on standing
- **A1c (2026-03-10):** 6.9%
- **Most recent lipids (2026-02-22):** LDL 78, HDL 52, TG 140
- **eGFR trend:** 58 → 52 → 48 over 18 months

### Current medication list (reconciled, generic names)
1. Lisinopril 20 mg PO daily
2. Amlodipine 5 mg PO daily
3. Diltiazem ER 240 mg PO daily
4. Metformin 1,000 mg PO BID
5. Glipizide 10 mg PO daily
6. Atorvastatin 40 mg PO nightly
7. Omeprazole 20 mg PO daily (started 2019, no recent reassessment)
8. Diphenhydramine 50 mg PO at bedtime PRN sleep (patient uses nightly x 3 years)
9. Alprazolam 0.25 mg PO TID PRN anxiety (uses ~2x/day on average)
10. Ibuprofen 400 mg PO TID PRN knee pain (uses most days)
11. Loratadine 10 mg PO daily (spring/summer)

### OTC / supplements
- Calcium carbonate 600 mg + vitamin D 400 IU BID
- Magnesium oxide 400 mg PO nightly (for "leg cramps")
- Fish oil 1 g PO daily

### Patient-reported concerns
- "I feel woozy when I first stand up — sometimes I have to grab the counter."
- "My knees hurt every day; the ibuprofen helps."
- "I can't sleep without Benadryl."
- Near-fall on stairs 2 weeks ago (no injury)

### Relevant clinical context
- Beers Criteria 2023: relevant to diphenhydramine (strong anticholinergic), alprazolam (benzodiazepine in older adults), glipizide (preferred over glyburide but still caution), NSAIDs in CKD/HTN/elderly
- STOPP/START criteria: omeprazole >8 weeks without indication review; NSAID with HTN and reduced eGFR; benzodiazepine ≥4 weeks
- Her prescribers: PCP Dr. Henrietta Oyelaran (lisinopril, amlodipine, diltiazem, atorvastatin, metformin, glipizide); Rheum NP Owen Batra (prescribed ibuprofen); Psych NP Felicia Mwangi (alprazolam)

## Artifact specification

Produce a single Markdown document with two clearly separated sections:

### Part A — Clinical CMR Workup (for prescriber + chart)

#### A1. Patient Summary
Demographics, active conditions, relevant labs (CrCl, A1c, BP avg, lipids), allergies.

#### A2. Medication Table
All meds listed with columns: Medication | Dose/Route/Frequency | Indication | Prescriber | Start date (if known) | Appropriateness assessment (appropriate / review / recommend change).

#### A3. Drug Therapy Problems (DTPs) — numbered list
For each identified problem use the format:
- **DTP #, Category** (unnecessary therapy / needs additional therapy / ineffective / dosage too low / dosage too high / adverse drug reaction / non-adherence)
- **Medications involved**
- **Clinical rationale** (cite Beers / STOPP / KDIGO / ADA / guideline where applicable)
- **Recommendation** (specific: drug, dose, route, frequency, taper plan if needed)
- **Monitoring** (what to watch, how often)
- **Priority** (high / medium / low)

At minimum address:
- Anticholinergic burden and fall risk (diphenhydramine)
- Benzodiazepine use in older adult (alprazolam) — taper considerations
- Chronic NSAID use with reduced eGFR and HTN (ibuprofen)
- PPI duration / deprescribing review (omeprazole)
- Possible duplicative antihypertensive therapy / orthostatic symptoms (amlodipine + diltiazem + lisinopril)
- Hypoglycemia risk in older adult with tight A1c (glipizide + metformin, A1c 6.9%)

#### A4. Drug-Drug / Drug-Disease Interactions
Short narrative flagging clinically relevant interactions (e.g., diltiazem + simvastatin class effect — confirm atorvastatin is acceptable substitute; NSAID + ACEi + diuretic-like effects; CNS-depressant stacking of alprazolam + diphenhydramine).

#### A5. Prescriber Communication
Draft a concise message (≤200 words) to the PCP summarizing top 3 recommendations with clinical justification, suitable for secure-message send.

### Part B — Patient Medication Action Plan (MAP) Handout

One-page, patient-facing, plain language (6th-8th grade reading level). Sections:
- **Your medicine goals** (2-3 bullets tied to patient concerns: fewer dizzy spells, better sleep, knee pain)
- **What is changing** (table: Medicine | What is changing | Why | What to do this week)
- **How to take your medicines** (simple schedule, morning/noon/evening/bedtime)
- **What to watch for** (clear, observable signs — low blood sugar, dizziness when standing, black stools)
- **Questions to ask your doctor** (3-5 open-ended prompts the patient can bring to the next PCP visit)

Avoid jargon. Define unavoidable terms in parentheses the first time (e.g., "NSAID (a type of pain reliever like ibuprofen)").

## Output format
- File type: `.md`
- Length: approximately 250-450 lines total
- Use H2 for Part A and Part B, H3 for each subsection

## Iteration targets
1. **DTP specificity.** Each recommendation must include a concrete drug, dose, route, frequency, and (where indicated) taper schedule — not "consider reducing" language.
2. **Guideline citation.** Every Beers/STOPP/ADA/KDIGO reference should be named with the specific criterion invoked, not a generic "per guidelines."
3. **Deprescribing practicality.** Replace abstract deprescribing suggestions with concrete, patient-safe taper plans (e.g., alprazolam 25% dose reduction every 2 weeks with sleep-hygiene substitute for diphenhydramine).
4. **Patient-facing plain language.** MAP handout must pass a read-aloud test — short sentences, defined jargon, numerals written for easy reading.
5. **Non-pharmacologic alternatives.** For each deprescribing recommendation, add a concrete alternative the patient can act on (CBT-I resource for insomnia, topical diclofenac or acetaminophen scheduled for knee pain, sleep hygiene handout reference).
6. **Prescriber message tone.** CMR prescriber communication must be concise, collegial, and action-oriented; no hedging that obscures the recommendation.

## Success criteria (evaluator only)
1. At least 6 DTPs identified covering the required domains (anticholinergic, benzodiazepine, NSAID+CKD, PPI, antihypertensive/orthostasis, hypoglycemia risk).
2. Every recommendation contains drug, dose, route, frequency, and monitoring parameter.
3. Beers Criteria 2023 and STOPP are cited by name with the specific criterion referenced, not generically.
4. Patient MAP is written at approximately 6th-8th grade reading level with no undefined clinical jargon.
5. At least one non-pharmacologic alternative is offered for each deprescribing recommendation.
6. Prescriber communication draft is ≤200 words, names specific drugs and concrete proposed changes, and avoids ambiguous phrasing.

## Scope target
A v1 produced in ~15 minutes should contain:
- Complete medication table (A2) for all 11 Rx meds and key supplements
- At least 4 of the 6 required DTPs with recommendation and monitoring filled in
- A first draft prescriber message (even if over the word limit)
- A skeleton MAP handout with the "What is changing" table populated for at least 3 medication changes
Deferred to later iterations: full plain-language polish of the MAP, every interaction pair fully analyzed, full taper schedules with week-by-week dose changes, and every DTP having a fully formed non-pharmacologic alternative.
