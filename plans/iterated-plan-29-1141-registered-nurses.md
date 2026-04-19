# Iterated Plan: 29-1141-registered-nurses

## Objective
Produce a discharge packet that is simultaneously clinically complete and teachable: accurate SBAR summary for the chart, plain-language education for patient and daughter, and concrete red-flag/escalation guidance that reduces 30-day heart-failure readmission risk.

## Required output shape
1. Part A: SBAR discharge summary.
2. Part B: Teach-back education plan by topic.
3. Part C: HF Zones quick reference.

## Execution roadmap
### Pass 0: Normalize the source data
- Extract admission reason, PMH, discharge condition, med changes, social context, follow-up logistics, and phone numbers into a working sheet.
- Treat four data items as high-risk and non-negotiable:
  - weight trend from 88.1 kg to 82.3 kg,
  - creatinine and potassium at discharge,
  - torsemide replacing furosemide,
  - follow-up within 7 days on April 24, 2026.
- Safe assumption for now: no fluid restriction was ordered; document this plainly and flag for confirmation if needed.

### Pass 1: Draft the SBAR summary
- Situation: admission for acute-on-chronic HFrEF exacerbation with dyspnea, orthopnea, edema, weight gain, BNP elevation, and oxygen requirement.
- Background: PMH, cane use, prior fall, marginal literacy, daughter as working caregiver, home scale available.
- Assessment: discharge vitals, improved volume status, weight change, creatinine 1.5, potassium 4.3, trace edema, room-air status, mobility.
- Recommendation/Plan: home discharge, HF clinic and PCP follow-up dates, diet/activity, DME, and home support.

### Pass 2: Harden the medication reconciliation
- Build a complete table with NEW / CHANGED / UNCHANGED / STOPPED flags.
- Add an explicit STOPPED row for home furosemide.
- State in plain language that torsemide is now the only water pill.
- Add practical instructions:
  - take torsemide in the morning with breakfast,
  - do not take old furosemide,
  - return old bottles to the pharmacy drop box,
  - use time-of-day cues instead of relying only on milligrams.

### Pass 3: Draft the minimum teach-back topics
- Start with the four highest-risk topics:
  - daily weights,
  - medication changes,
  - symptom red flags,
  - when to call HF clinic vs 911.
- Use a repeatable template:
  - key message,
  - teach-back prompt,
  - red-flag/action/contact.
- Every prompt must be open-ended and framed as nurse accountability.

### Pass 4: Expand to full topic coverage
- Add low-sodium diet with practical food swaps and explicit use of the 2 g sodium handout.
- Add fluid restriction status.
- Add fall prevention tied to cane use, prior fall, and morning diuretic timing.
- Add follow-up appointments, transport plan, and what to do if daughter is unavailable.
- Embed the HF Zones chart with the exact green/yellow/red thresholds.

### Pass 5: Literacy and caregiver revision pass
- Rewrite for REALM-SF 5:
  - short sentences,
  - define `diuretic` once,
  - plain verbs,
  - pictograph references if available,
  - time-of-day phrasing.
- Split responsibility correctly:
  - patient owns daily weight and symptom monitoring,
  - daughter supports logging and reminders,
  - plan still works when daughter is at work.

## High-risk failure modes
- Double-dosing due to furosemide/torsemide confusion.
- Missed escalation due to vague or non-measurable red flags.
- Readability failure for marginal literacy.
- Overloading the daughter and leaving no solo plan for the patient.
- Omitting fall-risk implications of diuretic timing.

## QA checklist
- SBAR sections appear in the correct order.
- Weight thresholds are numeric and actionable.
- All required phone numbers are present and used correctly.
- All teach-back prompts are open-ended.
- Every required topic is covered.
- HF Zones use the provided thresholds exactly.

## Definition of done
- A bedside nurse could walk through the packet without improvising.
- Mr. Kendrick and his daughter could restate the weight rule, the med changes, and when to call.
- The artifact clearly supports the unit's readmission-prevention audit requirements.
