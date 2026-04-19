# Equity Research Initiation — Ardent Shoals Semiconductor Corp. (NYSE: ARSC)

## Occupation
- **SOC:** 13-2051
- **Title:** Financial and Investment Analysts

## Scenario
You are a sell-side semiconductor analyst at Hollinscroft & Reyes Securities in New York, initiating coverage on Ardent Shoals Semiconductor Corp. (ticker ARSC), an $11.8B market-cap fabless designer of power-management ICs for EVs and datacenter cooling. Your director of research, Silje Ramnes, wants the initiation note published on the institutional portal by market open May 12, 2026, ahead of the company's analyst day on May 19. Your rating and 12-month price target will anchor the desk's position during the Q2 earnings season; a major buy-side client (Baitenrode Capital) has asked to speak within 24 hours of publication.

## Inputs

**Company snapshot**
- Ticker: ARSC (NYSE); FY = calendar year
- Share price (4/15/26 close): $38.92
- Shares out: 302.6M (basic); 311.1M diluted (incl. $420M of 0.50% convertibles maturing 2028)
- Market cap: $11.78B; EV ~$10.9B (net cash $885M)
- Last reported quarter: Q1 2026 (3/30/26 press release)

**Key FY2025 10-K and Q1 2026 10-Q data**
| Metric (USD M, unless noted)   | FY2023 | FY2024 | FY2025 | Q1 2026 |
|--------------------------------|--------|--------|--------|---------|
| Revenue                        | 2,110  | 2,640  | 3,185  | 855     |
| Gross margin %                 | 54.1%  | 56.8%  | 58.2%  | 59.1%   |
| Op. margin (non-GAAP) %        | 22.4%  | 26.1%  | 28.9%  | 30.2%   |
| R&D / revenue %                | 17.8%  | 17.1%  | 16.8%  | 16.4%   |
| FCF                            | 382    | 611    | 842    | 214     |
| Net cash / (debt)              | 415    | 640    | 855    | 885     |

**Segment mix (FY2025)**
- Automotive PMIC: 62% of revenue, growing 28% YoY, 61% GM
- Datacenter thermal controllers: 24%, growing 47% YoY, 57% GM
- Industrial/IoT: 14%, growing 5% YoY, 53% GM

**Qualitative intel**
- Two supply deals disclosed: Lüttlich AG (German EV Tier-1, framework agreement 2025–2029) and Prismatrix Data Centers (4-year supply)
- TSMC 5nm wafer starts secured through 2027; competitor NXP publicly complaining about allocation
- April 2026 DOE grant ($84M) for US packaging facility in Chandler, AZ
- Short interest 4.2%, down from 7.1% six months ago
- Two-member family (Vanderplaat Trust) holds 8.6% via Class B super-voting shares

**Consensus (Bloomberg as of 4/15/26)**
- FY2026E revenue: $3,920M; FY2027E: $4,690M
- FY2026E non-GAAP EPS: $2.41; FY2027E: $3.02
- 14 analysts: 9 Buy, 4 Hold, 1 Sell; median PT $44

**Comps set (4/15/26)**
| Ticker | FY2026E EV/Rev | FY2026E EV/EBITDA | FY2026E P/E |
|--------|----------------|-------------------|-------------|
| ADI    | 10.8x          | 24.1x             | 30.2x       |
| MPWR   | 13.6x          | 32.4x             | 38.9x       |
| NXPI   | 4.9x           | 11.2x             | 17.1x       |
| ON     | 3.2x           | 8.6x              | 13.4x       |
| Median (5) | 6.8x       | 17.3x             | 23.5x       |

## Artifact specification
Sell-side initiation note with full model references. Required sections:
1. **Front page** — rating (Buy/Hold/Sell), 12-mo PT, current price, implied return, key catalysts, risks, analyst name
2. **Investment thesis** — 3 punchy reasons the stock works (or doesn't), each with a falsifiable proof point
3. **Company overview** — segments, end markets, geographic mix, competitive position
4. **Market and thesis deep-dive** — TAM/CAGR for PMIC and datacenter thermal; share trajectory
5. **Financial model summary** — 5-year P&L forecast, FCF, balance sheet; explicit revenue build by segment
6. **Valuation** — triangulated: DCF (primary), EV/EBITDA multiple, P/E; walk to 12-mo PT
7. **Scenarios** — Bull / Base / Bear PTs with drivers
8. **Risks** — 4–6 named, categorized (secular, cyclical, idiosyncratic, governance)
9. **ESG and governance note** — Class B super-voting structure is material
10. **Appendix** — DCF assumption table, comps detail, catalyst calendar

Tone: institutional sell-side — punchy, data-dense, opinionated. Every claim cited or calculated.

## Output format
Markdown document with embedded tables (would later flow to the bank's research template / PDF). Target 2,200–2,900 words plus financial tables.

## Iteration targets
1. Investment thesis bullets are often descriptive ("Strong automotive exposure") rather than differentiated ("TSMC 5nm allocation advantage lets ARSC convert 18% more Lüttlich wafer demand in 2027 than NXP") — sharpen.
2. DCF often lacks disclosed WACC decomposition and terminal-growth sensitivity; add a WACC table and a 2-D sensitivity grid (WACC vs. TGR).
3. Bull/Bear PTs often lack probability weights; anchor each to a specific, observable 2026 event (analyst day, Q3 ER, AZ fab groundbreaking).
4. Governance section frequently treats super-voting stock as a checkbox; it's a material discount/risk — discuss magnitude.
5. Revenue build by segment is usually reported, not modeled — explicitly show ASP × units growth assumptions for auto PMIC.
6. Risk section has too many "macro" entries; at least 3 should be firm-specific (customer concentration, convertible dilution, AZ fab ramp).

## Success criteria
- The recommended rating follows from the model; the PT is not an anchoring number backfilled with assumptions.
- Valuation is triangulated and the DCF is fully auditable: WACC build, FCF assumptions, terminal value method.
- Thesis points are falsifiable — a reader can name the data point that would flip them.
- Competitive positioning is argued, not asserted; references specific peer data (e.g., NXP allocation complaints).
- Catalyst calendar is specific: dated events with expected directional impact.
- Risks include firm-specific items that could undermine the thesis, not just market-level risks.

## Scope target
v1 at ~15 minutes should contain: front page with preliminary rating/PT, three-bullet investment thesis, company overview paragraph, segment revenue build for 2026–2028, a skeleton DCF with key assumptions, comps-based valuation check, draft bull/bear bullets, and 4 risks named. Roughly 1,400–1,700 words; the WACC sensitivity, governance deep-dive, and scenario probability weighting are iteration work.
