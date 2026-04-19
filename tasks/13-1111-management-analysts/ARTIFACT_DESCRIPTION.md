# Claims-Intake Process Redesign Recommendation Deck — Orinthia Mutual Insurance

## Occupation
- **SOC:** 13-1111
- **Title:** Management Analysts

## Scenario
Orinthia Mutual Insurance, a $4.2B GWP regional P&C carrier in Hartford, has an auto-claims intake process averaging 11.3 days from FNOL to first estimate — industry median is 4.1. COO Temeka Barston-Hale engaged your consulting team for a 6-week diagnostic ending May 20, 2026. Field interviews and ops data are complete; you must produce the 18-slide steering-committee readout that lands the problem diagnosis, presents three redesign options, makes a recommendation, and gets approval for a $2.4M 9-month implementation.

## Inputs

**Process map artifacts** (provided)
- Current-state swim-lane (FNOL → Triage → Assignment → Inspection → Estimate → Reserve); 23 handoffs, 7 systems, 4 queues
- Sampled 412 claims from Jan–Mar 2026; median cycle time 11.3 days; P90 = 27 days
- 18 front-line interviews (adjusters, triage clerks, vendor intake, SIU) summarized in thematic codebook

**Quant dataset excerpt (cycle_times_2026Q1.csv)**
```
claim_id, fnol_ts, triage_end_ts, assigned_ts, inspection_ts, estimate_ts, system_hops, touches
AC-88201, 2026-01-04 08:14, 2026-01-04 14:02, 2026-01-06 10:11, 2026-01-11, 2026-01-15, 7, 9
AC-88202, 2026-01-04 09:20, 2026-01-07 08:44, 2026-01-07 11:02, 2026-01-13, 2026-01-18, 6, 11
AC-88203, 2026-01-04 11:05, 2026-01-04 11:38, 2026-01-04 13:22, 2026-01-07, 2026-01-08, 4, 5
```

**Top 5 interview themes (frequency)**
1. "I rekey the same customer data 3–4 times" (15/18)
2. "I can't see the photo estimator's queue without calling" (12/18)
3. "Supervisor approval for reserves <$5K is theater" (11/18)
4. "Vendor inspectors accept work in a separate portal, so I chase them" (9/18)
5. "New adjusters don't know the reserve playbook" (7/18)

**Benchmarks (provided)**
- Progressive: 3.2 days FNOL-to-estimate (2025 public disclosure)
- Allstate, Liberty Mutual, Nationwide: peer average 4.8 days
- Guidewire customer panel median (carriers w/ similar TIV mix): 5.1 days

**Constraints from COO intake**
- No new core system; must work within Guidewire ClaimCenter.
- Budget ceiling $2.5M; needs 12-month payback.
- Cannot reduce adjuster headcount in year 1 (recent union MOU).
- Must preserve SIU referral workflow.

## Artifact specification
Executive steering-committee deck (outline form — slide titles + body bullets + speaker notes). Required slide sequence:
1. **Title** — engagement, dates, presenters
2. **Executive summary / ask** — 3 bullets + the $ ask
3. **Why now** — competitive and loss-ratio framing
4. **Approach** — workstreams, methods, sample sizes
5. **Current state — the cycle time breakdown** (waterfall)
6. **Current state — the 5 themes** (with supporting data)
7. **Root cause synthesis** (fishbone or similar, one page)
8. **Design principles for the redesign**
9. **Option A** (incremental)
10. **Option B** (recommended — redesign + tech)
11. **Option C** (transformational)
12. **Option comparison matrix** (cost, time, impact, risk)
13. **Recommendation** and rationale
14. **Implementation roadmap** — 9 months, 3 phases
15. **Cost and benefit** — NPV, payback
16. **Risks and mitigations**
17. **Change-management approach** — union MOU considerations
18. **Decisions we're asking for today**

Tone: McKinsey/BCG-style. Pyramid principle — answer first. Every chart must have an action title, not a descriptive one.

## Output format
Markdown slide-outline file (headings are slide titles; bullets are on-slide content; italicized block after each slide = speaker notes). Target 1,800–2,400 words across the 18 slides.

## Iteration targets
1. Slide action titles ("Progressive completes FNOL-to-estimate in 3.2 days — we can close the gap in 9 months") not descriptive ones ("Benchmark comparison"). v1 usually has 6–8 descriptive titles.
2. The root-cause slide is typically a laundry list; compress to 3–4 causes with data-backed attribution of cycle-time impact.
3. Option comparison matrix often treats the options asymmetrically; normalize dimensions (Cost, Time, Gain, Risk, Fit-to-Constraints).
4. Implementation roadmap needs named workstream owners and a critical path, not just months.
5. Cost-benefit slide: v1 often shows benefits without a clear assumption chain — add a sensitivity box.
6. Change-management slide routinely ignores the union MOU constraint — it must be named and addressed.

## Success criteria
- The recommendation follows from the diagnosis with no analytical gaps; a skeptical CFO could not find an unjustified leap.
- Every slide passes "can I understand this in 10 seconds from the title alone?"
- Cost ask ($2.4M) and benefits are traceable to specific cycle-time reductions and loss-ratio impact.
- Options are genuinely different in cost/ambition; none is a strawman.
- The deck is decision-ready: explicit asks on the final slide.
- Constraints (Guidewire-only, no headcount cut, union) are visibly honored in the recommended option, not just mentioned.

## Scope target
v1 at ~15 minutes should contain: draft for all 18 slides with action titles (even if some are approximate), fully fleshed slides for the exec summary, current-state waterfall, options A/B/C one-liners, and recommendation. Comparison matrix can be partially populated; detailed speaker notes can be stubs on slides 14–17. Roughly 1,200–1,500 words; the NPV model and speaker-note polish are iteration work.
