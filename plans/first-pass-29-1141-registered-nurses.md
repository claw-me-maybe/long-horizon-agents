# First-Pass Plan: 29-1141-registered-nurses

## Goal
Produce a combined discharge summary and teach-back plan that lowers readmission risk, makes the medication changes unmistakable, and gives the bedside nurse a plain-language script for Mr. Kendrick and his daughter.

## Working assumptions
- The artifact must satisfy both clinical-documentation needs and patient-facing education needs in one markdown document.
- Readmission prevention hinges on four items: daily weights, sodium restriction, medication reconciliation, and red-flag escalation.
- The patient has marginal health literacy, so v1 must default to short sentences and concrete instructions.

## First-pass execution sequence
1. Convert the chart excerpt into a clean SBAR summary.
   - Situation: why admitted and key findings.
   - Background: PMH, home baseline, caregiver context.
   - Assessment: discharge vitals, weight change, fluid status, labs, mobility.
   - Recommendation/Plan: home disposition, follow-up, restrictions, DME.
2. Build the medication reconciliation table early.
   - Explicitly mark torsemide as NEW and replacement for furosemide.
   - Add a STOPPED row for furosemide.
   - Include timing guidance and old-bottle disposal instructions.
3. Draft the highest-risk teach-back topics first.
   - Daily weights.
   - Medication changes.
   - Symptom red flags.
   - When to call HF clinic vs 911.
4. Add follow-up logistics and daughter role.
   - Weight log support.
   - Evening reminder support.
   - What the patient does while daughter is at work.
5. Add the HF Zones quick reference.

## What must be true in v1
- All prompts are open-ended and non-shaming.
- The weight thresholds appear in pounds and tie to a phone number.
- The furosemide-to-torsemide switch is impossible to miss.
- The first follow-up within 7 days is named and dated.

## Main risks
- Using nurse-facing jargon instead of patient-facing language.
- Forgetting a STOPPED med row and risking double-dosing.
- Giving vague escalation advice instead of measurable triggers.
- Treating the daughter as solely responsible rather than supportive.

## Immediate iteration queue
- Simplify all teach-back text to a consistent 6th-grade reading level.
- Add the remaining required topics: low sodium, fluid restriction, fall prevention, transportation/follow-up details.
- Improve caregiver integration and time-of-day dosing cues.
- Add more observable symptom wording for dizziness, edema, bleeding, hypoglycemia, and hyperkalemia.
