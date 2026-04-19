# US Software Engineering Market Pricing Study — Stricklerwood Robotics, FY2026 Comp Planning

## Occupation
- **SOC:** 13-1141
- **Title:** Compensation, Benefits, and Job Analysis Specialists

## Scenario
Stricklerwood Robotics, a 1,250-person Series E warehouse-robotics firm headquartered in Boston with engineering hubs in Boston, Austin, and Remote-US, has flagged software-engineering attrition at 21% annualized in Q1 2026 (vs. 13% companywide). The Chief People Officer, Beatrix Hampshire-Yoke, needs a defensible market-pricing study for the Engineering ladder (IC1–IC7, M1–M4) by May 15, 2026, to inform a mid-year salary adjustment budget request of up to $4.8M going to the Compensation Committee on June 3. The study must also address whether the current geographic differentials (Boston 100, Austin 92, Remote 88) are still defensible given regret-attrition patterns.

## Inputs

**Internal population (SWE ladder only, 3/31/26)**
| Level | Title                 | # Incumbents | Median base | Avg TCC (base+bonus+equity) |
|-------|-----------------------|--------------|-------------|------------------------------|
| IC1   | Engineer I            | 42           | $128K       | $144K                        |
| IC2   | Engineer II           | 87           | $152K       | $178K                        |
| IC3   | Senior Engineer       | 134          | $182K       | $228K                        |
| IC4   | Staff Engineer        | 68           | $215K       | $298K                        |
| IC5   | Senior Staff Engineer | 29           | $252K       | $380K                        |
| IC6   | Principal Engineer    | 11           | $288K       | $465K                        |
| IC7   | Distinguished Eng.    | 3            | $340K       | $590K                        |
| M1    | Engineering Manager   | 24           | $218K       | $305K                        |
| M2    | Sr. Engineering Mgr.  | 14           | $252K       | $398K                        |
| M3    | Director              | 7            | $295K       | $510K                        |
| M4    | Senior Director       | 2            | $345K       | $650K                        |

**Survey sources subscribed**
- Radford Global Technology (GTIS) April 2026 refresh, robotics/industrial-tech cut
- Mercer M/BD Technology April 2026
- Levels.fyi (self-reported; not used for pricing, used as a sanity check on TCC tails)
- Pave peer benchmarks (anonymized cohort N=38 private tech, Series D–pre-IPO)

**Regret attrition insights (Talent Analytics provided)**
- Top 3 stated reasons in exit interviews: "total comp below market" (58%), "equity refresh lag" (47%), "location flexibility" (34%)
- Regrets concentrated at IC3/IC4 and in Remote segment
- 74% of IC3+ leavers went to Series E–public companies within 30 miles of their home

**Constraints**
- Budget ceiling: $4.8M mid-year adjustment; annualized impact ≤ $6.6M
- Philosophy: pay to 65th percentile of cash; 55th percentile of equity (current stated policy)
- No downward adjustment of any individual's base pay
- California/Colorado/Washington pay transparency obligations apply to externally-facing bands
- Leveling change (reclassification up) is allowed for a limited number of incumbents only with CPO sign-off

## Artifact specification
Market-pricing study deliverable. Required sections:
1. **Executive summary** — headline competitive position, recommended adjustments, $ ask, risk if not funded
2. **Scope and methodology** — job matching approach (benchmarking vs. slotting), survey aging, weighting, geo-differential treatment
3. **Job-to-survey matching table** — for each level, the survey jobs used, match quality, and rationale
4. **Market data** — by level: market 50th/65th/75th for base, TCC, and equity; source-by-source reconciliation
5. **Competitive position analysis** — internal median vs. market 65th by level; compa-ratio distribution; red-circle and green-circle populations
6. **Attrition correlation analysis** — regret attrition vs. competitive position by level and geo; statement on causation limits
7. **Geographic differentials assessment** — Boston/Austin/Remote differential vs. observed market and attrition
8. **Recommendation** — proposed adjustments, by level and geo; logic for who gets moved (percentile, not ad hoc); equity refresh changes
9. **Budget model** — waterfall from headcount × per-incumbent change → $ impact; multi-year view
10. **Pay-equity impact check** — stated methodology (e.g., regression with controls) and directional finding
11. **Rollout and comms** — manager talking points outline, employee comms principles, transparency-law implications
12. **Appendix** — survey cuts used, aging assumption, sensitivity table

Tone: compensation-professional, conservative with claims, decision-oriented. Use "market 65th" (not "P65") consistently; define terms once.

## Output format
Markdown document with tables. Target 2,600–3,300 words.

## Iteration targets
1. Job-matching table often states "matched" without documenting match quality; add an A/B/C match rating with rationale per level.
2. Survey aging is often hand-waved; declare the aging factor (e.g., +4.1% Jan→April 2026) with source.
3. Geo differential section tends to answer "are the numbers defensible" as a yes/no; recommend a specific differential (e.g., move Remote from 88 to 92) with magnitude and attrition-impact reasoning.
4. Pay-equity impact check is often absent or reduced to "we checked"; describe method, controls, and a directional finding.
5. Budget model sometimes shows headline number without a waterfall — add the incumbent-count × %-adjustment × base-salary rollup.
6. Recommendation often reads as "raise everyone to P65"; sharpen to target only below-band or at-risk populations and specify criteria.

## Success criteria
- Recommendations are grounded in survey data with documented matching and aging — a comp committee skeptic could not trip the methodology.
- Geographic differential proposal is backed by data (market + attrition), not assertion.
- Budget ask ties cleanly to headcount and percentile targets; the math is auditable.
- Pay-equity analysis is present and methodologically sound for a directional study (regression w/ appropriate controls).
- Regret-attrition correlation is presented with appropriate caution about causation.
- Transparency-law implications are addressed (how posted ranges change, if at all).

## Scope target
v1 at ~15 minutes should contain: executive summary with a preliminary $ ask, scope and methodology, job-to-survey matching table for IC1–IC7 (initial), one market-data table with aged Radford data, competitive position snapshot by level, draft recommendation text, and a rough budget waterfall. Roughly 1,500–1,900 words; multi-source reconciliation, the pay-equity regression details, and the full rollout plan are iteration work.
