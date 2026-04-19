# Referral Coordination Package for Complex Multi-Specialty Patient — Meadowbrook Internal Medicine, Patient Case of 04/17/2026

## Occupation
- **SOC:** 43-6013
- **Title:** Medical Secretaries and Administrative Assistants

## Scenario
You are Sylvie Donaldson, medical secretary at Meadowbrook Internal Medicine (a 6-provider primary care practice in Asheville, NC, part of Blue Ridge Health Partners IPA). On April 17, 2026, Dr. Marcus Weill completes an office visit with patient "Harold T." (DOB 1952-03-22) and dictates a complex plan requiring: (1) outpatient cardiology consult, (2) outpatient endocrinology consult, (3) sleep study referral, (4) a diagnostic coronary CTA, and (5) lab pre-work before those appointments. Dr. Weill asks you to handle coordination, prepare a referral package for each specialist, and produce a patient-facing care-navigation summary. Dr. Weill wants the complete package ready for his EHR co-signature by end of day April 18. The patient is overwhelmed and has limited health literacy; his daughter Patricia is the identified care partner (HIPAA authorization on file).

## Inputs

**Patient (use "Harold T." in any distributable artifact; full identifiers internal only):**
- DOB 1952-03-22 (age 74)
- MRN MBIM-0048213
- Insurance: Medicare Part A/B + BCBS NC Supplement Plan G (member ID ZGZ 123456789)
- PCP: Dr. Marcus Weill
- Pharmacy: Ingles Pharmacy, Asheville
- Emergency contact/care partner: Patricia T. (daughter), HIPAA auth signed 2024-11-02
- Preferred contact: home phone, voicemail OK; text OK for appointment reminders only
- Language: English primary; health literacy noted as limited by Dr. Weill

**Relevant active problems (from chart):**
- Type 2 diabetes, HbA1c 8.4% (04/10/2026) — worsening trend
- Hypertension, last in-office BP 156/92 on 04/17 after 15 min rest
- Hyperlipidemia
- Obesity (BMI 33)
- Obstructive sleep apnea, suspected; Epworth 14 today
- Mild chronic kidney disease, eGFR 54 (04/10/2026)
- Iodinated-contrast: no prior reaction on file; but eGFR <60 is a flag for contrast imaging
- No known drug allergies

**Current medications (key ones):**
- Metformin 1000 mg BID
- Lisinopril 20 mg daily
- Atorvastatin 40 mg daily
- Aspirin 81 mg daily
- Metformin contraindication at eGFR <30 — not at issue now; but relevant if CKD progresses.

**Dr. Weill's plan (dictated, raw):**
1. "Cardiology consult with Dr. Shivani Patel at Blue Ridge Cardiology for evaluation of hypertension and coronary risk stratification; order coronary CTA within the next 6 weeks; given eGFR 54 review pre-procedure hydration protocol and metformin hold per standard."
2. "Endocrinology consult with Dr. Rafael Obando at Mountain West Endocrinology for diabetes management; HbA1c 8.4 and trending up; consider GLP-1 agonist."
3. "Sleep study — refer to Pisgah Sleep Center; home-study preferred; Epworth 14."
4. "Lab pre-work before specialty visits: fasting lipid panel, HbA1c, CMP, TSH, urine micro albumin/creatinine ratio."
5. "Patient to return to me in 6 weeks or after all three specialist visits, whichever first. Send patient-friendly care plan summary to him and his daughter."

**Practice / coverage context:**
- Blue Ridge IPA has in-network referral requirements; Blue Ridge Cardiology and Mountain West Endocrinology are in-network. Pisgah Sleep Center is in-network; confirm.
- Medicare does not require prior auth for cardiology consult but BCBS supplement may require notification for CTA; verify.
- Coronary CTA ordering location: Blue Ridge Cardiology has in-house; otherwise Asheville Imaging.
- Typical referral response time: cardiology 2-4 weeks, endocrinology 4-6 weeks, sleep 3-5 weeks.
- Patient's transportation: drives himself short distances only; daughter drives for anything downtown.

## Artifact specification
Produce a multi-part coordination package:

1. **Internal routing cover sheet** (for Dr. Weill's co-sign)
   - Patient MRN, date, referrals listed with priority ranking (hypertension-cardiology first given 156/92)
   - Checklist of what Sylvie has prepared
   - Items requiring MD decision before send

2. **Three referral letters** — one per specialist (cardiology, endocrinology, sleep). Each letter:
   - Meadowbrook letterhead block (placeholder ok)
   - Date, recipient name/address, patient identifiers (internal version full; external version limited per HIPAA minimum necessary)
   - Referral reason, clinical question, urgency
   - Relevant history (pertinent problems, not the full chart)
   - Current medications relevant to the specialty (cardiology gets full med list; endocrinology gets diabetes-specific; sleep gets focused subset)
   - Recent labs relevant to the specialty
   - Specifics requested (e.g., for cardiology: "please arrange coronary CTA with pre-procedure hydration and metformin hold per standard; eGFR 54 on 04/10/2026")
   - Return of care plan requested
   - PCP signature block

3. **Lab order summary** — what's ordered, where the patient can draw, fasting requirements, instruction to complete before specialist visits (ideally within 14 days).

4. **Patient-facing care navigation summary** (the core patient-facing artifact)
   - Plain language, 6th-grade reading level
   - "What's happening and why" — 3-4 sentences
   - "What you need to do" — numbered list with dates, phone numbers, transportation notes, what to bring
   - "Before each appointment" — fasting rules, med instructions (specifically metformin hold for CTA), when to stop eating, hydration guidance
   - "Who to call if…" — symptoms warranting call-back to Meadowbrook vs. 911
   - "Your daughter Patricia can help by" — specific supports
   - Appointment tracker table (provider, date, address, phone, prep)

5. **Insurance/authorization workflow checklist** — who to call for what, which items need prior auth, which are Medicare-automatic.

6. **Schedule of follow-ups** — proactive call-outs Sylvie will make: day-before reminder to patient, post-specialist consult chase for notes, 6-week PCP return appointment.

Tone: varies by audience. Internal routing sheet: efficient, directive. Referral letters: clinical, concise, professional peer-to-peer. Patient summary: warm, concrete, respectful of health literacy.

## Output format
Single Markdown file, organized by artifact type with clear section headers. ~4 pages rendered (280-400 lines source).

## Iteration targets
1. **Apply HIPAA minimum-necessary discipline** — each referral letter should include only the history relevant to that specialty; v1 may send the full chart to all three; v2 tailors.
2. **Handle the eGFR 54 + CTA contrast interaction** — v2 explicitly calls out metformin hold and pre-hydration in the cardiology letter and in the patient-facing summary; v1 may miss this.
3. **Match patient-facing reading level to literacy notes** — v1 may write at 10th-grade level; v2 shortens sentences, defines specialty terms, and uses "before you stop driving yourself" type concrete framing.
4. **Get the priority right** — hypertension 156/92 + HbA1c 8.4 + suspected OSA are all chronic-urgent; priority ranking should reflect this, not a flat "all routine."
5. **Address the insurance authorization path correctly** — Medicare primary, BCBS supplement; CTA may need BCBS notification; Sylvie should propose verifying, not assuming.
6. **Integrate the daughter appropriately** — care partner role is explicit in the patient-facing summary, with specific supports; respects HIPAA auth on file; doesn't overreach into decision-making that's the patient's.

## Success criteria
- No referral letter leaks full chart detail where minimum-necessary applies.
- eGFR 54 + CTA interaction is addressed in at least the cardiology letter and the patient summary.
- Patient-facing summary reads at approximately 6th-grade level.
- Appointment tracker in patient summary has real fields (provider, date, address, phone, prep) even if date is TBD after scheduling.
- Priority ranking is medically coherent.
- Insurance/auth items are flagged for verification, not asserted.
- Patient's literacy, driving, and care-partner context shape the patient-facing artifact visibly.

## Scope target
A v1 at ~15 minutes should contain: internal routing cover sheet, full draft of the cardiology referral letter plus abbreviated drafts of endocrinology and sleep referrals, lab order summary, a first-pass patient-facing care navigation summary with at least 3 of the 5 elements, and a first sketch of the insurance checklist. Tailoring each referral for minimum-necessary, adjusting the patient summary to literacy level, and polishing the CTA/metformin/hydration instructions belong to iteration.
