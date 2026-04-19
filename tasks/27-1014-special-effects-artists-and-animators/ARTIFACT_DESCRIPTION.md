# VFX Shot Breakdown + Creature Rigging Spec: "The Hollow Cathedral" Shot HC_087

## Occupation
- **SOC:** 27-1014
- **Title:** Special Effects Artists and Animators

## Scenario
You are the VFX supervisor for **"The Hollow Cathedral,"** a feature animated film in production at a mid-size studio (Blackbird Interactive Animation, Vancouver) co-producing with Netflix, scheduled for a Q4 2027 release. The film is a stop-motion-inspired CG feature; the lead creature is the "Verger," a 9-foot-tall stilt-limbed sanctuary keeper whose body is partly wicker, partly cloth, and whose joints rattle audibly when it moves. Shot HC_087, in Sequence HC (the cathedral confrontation, the film's Act II climax), requires the Verger to emerge from behind a 40-foot altarpiece, kneel before the child protagonist (Mira, 8 years old), and extend its papery hand — the shot is a developing lock-off-push, 14 seconds, at a 36-frame-per-second capture simulating stop-motion. Lead character animator is Takashi Mori; creature TD is Aliya Novak; the shot breakdown and updated rigging requirements are due to the animation department by April 29, 2026, with animation kicking off May 4. The existing Verger rig (v2.3) has been flagged as insufficient for this shot — specifically the kneel and the hand extension.

## Inputs
Materials on your desk:
- Storyboards for HC_087 (12 panels) and the surrounding shots HC_085 through HC_089.
- Director's intent note from Rosa Thiel (director): "I want the kneel to feel like the Verger is asking the room's permission. If it creaks, I want us to believe the creak." 
- Animatic timing (14 sec; 504 frames at 36 fps): frames 1-72 emergence, 73-252 kneel, 253-420 hand extension, 421-504 Mira's reaction (Verger held still).
- Existing Verger rig v2.3: standard FK/IK skeleton (187 joints), secondary cloth sim (Houdini Vellum), wicker-panel deformers with broken-edge shader. Known issues: (a) the IK kneel collapses the pelvis-to-floor distance non-organically; (b) the wicker shoulder-to-elbow has no slack/tension control; (c) the fingers are too rigid for the "paper rustle" Rosa wants.
- Production constraints: two shots per-day average farm budget; this is a hero shot so 4-day render budget is approved. 4K Redshift render. Alembic publishing pipeline.
- Adjacent shot HC_086 (the approach) is already animated on v2.3 and cannot be re-animated — the rig changes must be additive/backwards-compatible.
- Reference library: the studio has curated 18 reference clips for the Verger's movement vocabulary (mantis religiosa, Bunraku puppet manipulation, a specific 1987 Švankmajer short).
- Simulation dept review: the audible creak (Rosa's note) will be designed in sound, but the rig must produce a motion profile that a foley artist can believably creak — i.e., visible micro-tremors during held poses.

## Artifact specification
Produce a **shot breakdown + rigging requirements document**. Structure:
1. **Shot header** — shot code, sequence, duration, fps, resolution, render budget, director intent restated in one line.
2. **Shot intent** (2-3 paragraphs) — the emotional objective, the one frame that must exist, the sound-image relationship Rosa asked for.
3. **Frame map** — table mapping frame ranges to action beats, key poses, camera moves, and reference clips by name/timestamp.
4. **Rig gap analysis** — three subsections on the three flagged issues (pelvis collapse, shoulder-elbow slack, finger paper-rustle). For each: what breaks, why, and a proposed solution at the rigging layer (new controls, new deformers, new sim inputs).
5. **New rigging requirements** (the meat) — a spec for rig v2.4 additions:
   - New controls (name, type, purpose, default values, limits).
   - New deformers (e.g., a "pelvis-to-floor compression spline").
   - New simulation hookups (what Vellum needs to know).
   - Attribute publishing to the alembic layer so downstream shot HC_086 doesn't break.
6. **Backwards compatibility plan** — explicit contract: v2.4 is additive; shots already animated on v2.3 continue to work because [mechanism].
7. **Micro-tremor / held-pose spec** — requirement for the "creak-able" held poses, quantified (e.g., ±0.3 cm tremor on shoulder joints at 4-7 Hz during held frames).
8. **References** — named clips for each beat, timestamps, what is being borrowed (silhouette, weight transfer, eye line).
9. **Handoff checklist** — what animation department receives on May 4 (rig build, published controls, sample motion test, shotfile with camera locked).
10. **Risks and unknowns** — 3-5 technical unknowns and the plan to de-risk them before animation lock.

Voice: technical, precise, unafraid of jargon. Correct vocabulary: FK/IK, Vellum, alembic, deformer, constraint, space switch, pivot offset, sim cache. Number the requirements so the rigging team can track per-ticket. Use imperative when specifying ("Add a compression spline control called `verger_pelvis_compress_ctrl`..."). Avoid vague deliverables; prefer "publishable by end of day April 30" over "soon."

## Output format
Single markdown file. Frame map and controls spec in GFM tables. One ASCII diagram showing the pelvis-to-floor compression concept. Requirements numbered (REQ-01 through REQ-NN) so they can be cross-referenced. Rough length: 300-500 lines.

## Iteration targets
1. Rig gap analysis sections must each offer exactly one recommended solution plus at least one alternative — don't leave TD Aliya to pick from hand-waving.
2. Every numbered requirement must have: name, purpose, type, and a testable acceptance condition (otherwise the TD can't close the ticket).
3. Frame map should reference specific storyboard panels and specific reference clips — generic "see reference" entries are a failure.
4. Backwards-compatibility plan should be one-paragraph specific, not "should remain compatible" — name the mechanism (namespace, proxy control, default-on attribute).
5. Micro-tremor spec should quantify — frequency, amplitude, which joints. A foley artist and a renderer should both be able to implement against it.
6. Risks should include at least one schedule risk, not only technical risks (e.g., "v2.4 build by May 4 assumes no regression in shoulder sim; if regression found, add 2 days").

## Success criteria
- Creature TD Aliya Novak can scope the rig v2.4 work from this doc in a sprint-planning meeting without further questions.
- Lead animator Takashi Mori can begin blocking on May 4 with a concrete frame map and pose-reference plan.
- The director's "creak" note is traceable to at least two concrete technical requirements.
- The shot's 14-second, 504-frame timing is internally consistent across the frame map and the beat allocations.
- Backwards-compatibility contract is explicit enough that shot HC_086 can be re-published without re-animation.
- Document uses the correct rigging vocabulary consistently — no "bone" where "joint" is meant, no "skin" where "deformer" is meant in this pipeline.

## Scope target
A 15-minute v1 should include: shot header, shot intent paragraph, frame map (possibly at coarse beat granularity), the three rig gap analyses (diagnosis written; solutions in rough), and a numbered requirements list of 5-8 items. Missing: the full requirements set (est. 12-18 total), the micro-tremor quantified spec, the backwards-compatibility paragraph, the ASCII compression diagram, and the handoff checklist.
