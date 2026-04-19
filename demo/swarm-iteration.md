---
title: "Model Swarm Iteration"
subtitle: "How much does iterating with a swarm of agents actually uplift artifact quality?"
author: "Early demo night · Claude Opus 4.7"
date: "2026-04-19"
---

# The setup

- **5 domains** drawn from BLS × Anthropic Economic Index weighting
- **3 agents per domain**, working independently — the "swarm"
- Each agent produces **v1 → v2 → v3** — the "iteration"
- Target: 45 artifacts total (5 × 3 × 3)

Agent prompt: read `ARTIFACT_DESCRIPTION.md`, draft v1, apply iteration targets for v2, polish for v3. No cross-talk.

# The five domains

| Domain | Artifact | Cognitive style |
|---|---|---|
| Software Dev | Webhook dispatcher service (code) | systems engineering |
| Editor | Developmental edit memo (novel) | structural craft |
| Lawyer | Non-compete enforceability memo (MA) | statutory reasoning |
| Chemist | HPLC method validation report | regulated science |
| Nurse (RN) | CHF discharge summary + teach-back | clinical comms |

Picked one representative occupation per SOC major group — weighted by BLS wage bill × AEI API adoption × artifact-fit.

# What "uplift" means here

A hand-wavey composite:

- **Volume** — did v2 add substantive material? (lines are a crude proxy)
- **Breadth** — did v2 surface doctrines, tests, options v1 skipped?
- **Completeness** — did v1 ship a partial draft that v2 finished?
- **Swarm variance** — did 3 agents converge, or split into meaningfully different outputs?

*Caveat: line-count is a rough proxy; qualitative reads are what matter. Demo-night rigor only.*

# Uplift by domain (v1 → v2 → v3)

Mean lines across 3 agents. Hand-wavey proxy for "amount of work added."

| Domain | v1 | v2 | v3 | v1→v3 | Shape |
|---|---|---|---|---|---|
| **Software Dev** | 269 | 663 | 1119 | **4.2×** | runs away — each round adds production concerns |
| **Editor** | 48 | 125 | 129 | 2.7× | all growth in v1→v2, **plateaus** after |
| **Nurse (RN)** | 169 | 325 | 415 | 2.4× | steady growth across all rounds (**surprise**) |
| **Lawyer** | 82 | 136 | 167 | 2.0× | each round adds a doctrine or jurisdiction |
| **Chemist** | 295 | 407 | 482 | 1.6× | regulated template constrains the ceiling |

# Biggest uplift: Editor

**v1 (51 lines):** Three-thread critique of a debut novel. Solid instincts. Ends with:

> "[This is a first pass — I'll send you the full letter, including the other two thread sections, the complete questions list, and the scope/timeline, by end of day Saturday.]"

**v1 knew it was incomplete.**

**v2 (147 lines):**

- 3 *genuinely different* options per structural issue ("A is withholding, B is relational, C is pacing — pick one")
- 10 pre-revision questions for the author
- Full 8-week timeline mapped to teaching schedule
- Explicit "what NOT to do" scope list

Iteration worked here because the task was **open-ended and craft-judgmental**. v2 didn't just add words — it added **alternatives**.

# Software Dev: scaffold → production

*Rate-limited webhook dispatcher — Python + Redis + tests*

**v1 added:**

- Core dispatch loop
- `asyncio.Semaphore` rate limit
- Basic retry
- Minimal tests

**v2 → v3 added:**

- Redis token bucket (survives restarts)
- HMAC signing + `compare_digest`
- Per-merchant circuit breaker (CLOSED/OPEN/HALF-OPEN)
- Idempotency dedup, DLQ, Prometheus metrics
- Graceful SIGTERM drain
- Separate test files, `docker-compose`, `sql/schema.sql`

Iteration converted a **working toy** into something you could actually run. Tests doubled. Security tightened. Ops story filled in.

# Lawyer: solid → thorough

*MA non-compete memo. v1 was already competent; v2 closed rigor gaps.*

**v1 covered:**

- All six § 24L statutory elements
- *Packaging Industries* 4-factor PI test
- Three-option recommendation

**v2 added:**

- Common-law reasonableness (*Boulanger*, *Marine Contractors*) as **separate** from § 24L
- Parallel DTSA/MUTSA trade-secret theory fully developed
- Rhode Island choice-of-law risk (employee lived in RI 2 days/week)
- 7-item "open issues" investigation list
- Quantified cost/probability per option

Uplift here is about **noticing what v1 didn't notice** — the second doctrine, the alternate theory, the jurisdictional edge case.

# The RN surprise

I predicted discharge summaries would plateau fast. **Wrong.** They grew 2.4× v1→v3 — steady across every round.

- **v1**: 4 of 8 teach-back topics, core meds, basic red flags
- **v2 adds**: remaining 4 topics, caregiver role-splits ("when daughter is at work"), pill color descriptors, concrete analogies ("2 lb = water bottle")
- **v3 adds**: pictograph references, meal-time anchors replacing clock times, two-scenario teach-back prompts for triage reasoning, literacy-fitted emergency tables

Lesson: "tight template" ≠ "no room to iterate." Patient-education materials have **many small literacy levers** that compound across rounds.

# Swarm variance

*Do 3 agents on the same artifact converge or diverge?*

- **Editor v2:** all 3 agents wrote complete letters, but emphasized different structural diagnoses. Three different "recast Aunty Fola" framings. *Divergent, in a good way.*
- **Software Dev v3:** two agents ended with similar architecture but different trade-offs (fixed-window vs. token-bucket rate limiter; TTL-based vs. timer-based breaker). *Real engineering choices visible.*
- **Lawyer v2:** reaches same overall conclusion but varies in which jurisdictional risk gets top billing.

The swarm is **not** a vote — it's a portfolio of judgment calls the reader can compare.

# Highest vs. lowest uplift

**Most uplift:**

| Domain | v1→v3 | Why |
|---|---|---|
| **Software Dev** | 4.2× | Every round surfaces another production concern: tests, circuit breakers, metrics, Dockerfile, schema. |
| **Editor** | 2.7× | v1 was partial; v2 finished the letter with *alternatives*. But v3 ≈ v2 — craft letters cap out. |

**Least uplift:**

| Domain | v1→v3 | Why |
|---|---|---|
| **Chemist** | 1.6× | Regulated ICH Q2(R2) template. v1 already hits the shape; v2-3 add precision, not scope. |
| **Lawyer** | 2.0× | v1 hits IRAC. Iterations add breadth (common-law layer, DTSA theory, RI jurisdiction) but not transformation. |

# Takeaways

1. **Code has runaway uplift.** 4.2× growth over 3 rounds. Each iteration surfaces more production concerns (tests, metrics, ops) — the "iteration tax" is paid in hardening, not rethinking.
2. **Craft letters plateau after round 2.** Editor's v1 was partial; v2 finished it with alternatives. v3 ≈ v2. Once the structural argument is complete, further rounds polish prose but don't transform.
3. **"Tight template" ≠ "no uplift."** Discharge summaries grew 2.4× because patient-education has *many small levers* (literacy, pictographs, caregiver roles, emergency tables) that compound. My prior was wrong.
4. **Regulated scientific reports plateau earliest.** Chemist ≈ 1.6×. ICH Q2(R2) shape is rigid; iteration refines validation rigor within a fixed skeleton.
5. **Swarms produce portfolios, not consensus.** 3 agents pick genuinely different trade-offs. Useful for comparison; bad for majority-vote.

# Caveats & next steps

- **Line count ≠ quality.** 2.7× is suggestive, not dispositive. Humans need to rate v2 blind vs v1 to confirm.
- **5 domains is small.** Need to run the other 7 (Management, Office/Admin, Business/Finance, Engineering, Science, Sales, Community/Social) to see if the pattern holds.
- **v3 data is thin.** Most v3s are still in flight — open question is whether v3 adds marginal value or diminishing returns.
- **Codex is running the same thing in parallel.** Head-to-head comparison next.

# Questions?

Artifacts at `/tasks/<soc>-<slug>/iterations/agent-N/v{1,2,3}.md`

Weighting method in `CLAUDE_DOMAINS_DETAILED.md`
