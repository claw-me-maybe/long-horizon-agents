# US Urban Cyclist Segmentation Report — Velozen DTC Launch, Fall 2026

## Occupation
- **SOC:** 13-1161
- **Title:** Market Research Analysts and Marketing Specialists

## Scenario
Velozen Mobility, a Dutch e-bike manufacturer, is launching direct-to-consumer in the United States in October 2026, starting with Chicago, Austin, and Seattle. The VP of Growth, Marguerite Salas, has commissioned a segmentation report to decide which 2–3 rider archetypes deserve the $3.8M launch budget. The report will be presented to the global exec team on May 7, 2026, and will directly shape paid media creative, retail partnerships (e.g., REI vs. local bike shops), and the Year-1 SKU assortment.

## Inputs

**Commissioned survey** (fielded by Arborvue Research, n=2,412 US adults 22–64 in the three launch cities, March 2026). Weights adjust to ACS for age, income, race, density.

**Representative excerpt (15 of 72 variables)**
```
respondent_id, city, age, hh_income, owns_car, weekly_bike_trips,
trip_purpose_commute, trip_purpose_errands, trip_purpose_fitness,
trip_purpose_social, max_bike_spend, ebike_interest_0_10,
climate_motivation_0_10, safety_concern_0_10, brand_awareness_velozen
```

**Sample rows**
```
2201, CHI, 34, 92000, Y, 3, 1, 1, 0, 1, 2800, 8, 7, 9, 0
2202, AUS, 47, 138000, Y, 1, 0, 1, 0, 1, 4500, 6, 4, 6, 0
2203, SEA, 29, 61000, N, 9, 1, 1, 1, 0, 1800, 9, 9, 8, 1
```

**Secondary sources provided**
- Light Electric Vehicle Assn. 2025 report ("US e-bike units shipped: 1.41M, +18% YoY")
- NHTS 2022 commuting-mode tables
- Strava Metro 2025 ride-density heatmaps (Chicago, Austin, Seattle)
- Velozen internal EU persona deck (4 existing archetypes: "Stadsritter," "Langstrecke," "Zusteller," "Freizeit")

**Competitor shelf scan (provided CSV, excerpt)**
| Brand   | Flagship model     | MSRP    | Range  | Retail channel         |
|---------|--------------------|---------|--------|------------------------|
| Rad     | RadCity 5 Plus     | $1,999  | 45 mi  | DTC + 20 stores        |
| Specialized | Turbo Vado SL  | $3,250  | 70 mi  | 700+ IBDs              |
| Aventon | Level.2            | $1,999  | 40 mi  | DTC + Walmart          |
| Gazelle | Ultimate T10+      | $4,499  | 70 mi  | Premium IBDs           |

**Constraints noted by Marguerite**
- Launch assortment is 3 SKUs max
- EU personas must be tested against US data, not copy-pasted
- Segments must be "actionable" — distinct in media targeting, price, and channel

## Artifact specification
Segmentation report suitable for an exec readout. Required sections:
1. **Executive summary** — recommended 2–3 priority segments and the strategic call
2. **Methodology** — survey design, segmentation approach (latent-class or k-means justified), validation
3. **Segment profiles** — one page per segment: demographics, psychographics, JTBD, price sensitivity, media habits, sample verbatim
4. **Sizing** — TAM/SAM/SOM by segment, with assumptions traceable
5. **Competitive fit** — where each segment currently shops, whitespace for Velozen
6. **Activation implications** — channel, creative hook, SKU, pricing band
7. **Risks and open questions**
8. **Appendix** — variable list, segmentation diagnostics (BIC, silhouette, stability)

Tone: decision-oriented, hypothesis-forward, quantitative where it matters but not drowning in numbers. Segments should have memorable names, not "Segment A, B, C."

## Output format
Markdown report formatted for printing to PDF. Target 2,500–3,400 words plus segment-profile cards and sizing tables.

## Iteration targets
1. v1 segments are likely demographic-heavy; push toward behavioral/attitudinal differentiation with at least two non-obvious variables driving the split.
2. Sizing section needs explicit assumption chain: population → qualified → interest → purchase intent → conversion → Y1 revenue. v1 will skip steps.
3. Compare explicitly to the four EU personas — state which carry over, which don't, and why. v1 tends to ignore them.
4. Verbatim quotes are either missing or generic — add one sharp, specific verbatim per segment.
5. Activation implications should name specific media vehicles (e.g., "Reddit r/chibike sponsored post" vs. "social media").
6. Risks section should flag at least one finding that contradicts Marguerite's hypothesis, not just soft risks.

## Success criteria
- Segments pass the "actionability test": could a media planner, merchandiser, and retail-ops lead each act on them without needing to re-segment?
- Recommendations are backed by triangulation across primary, secondary, and competitive data — not just survey output.
- Sizing is defensible down to the final $ figure; any exec can follow the math.
- The report makes a clear recommendation and doesn't hedge toward "it depends."
- EU-persona comparison is substantive (tests and discards as needed), not perfunctory.
- The analytical method (e.g., latent-class model) is justified for this use case, not chosen by default.

## Scope target
v1 at ~15 minutes should contain: exec summary with a preliminary segment recommendation, methodology section naming the technique and rationale, 3–4 draft segment profiles (names + 2-paragraph descriptions each), a sizing table with placeholders for the conversion assumptions, and a skeleton activation implications table. Roughly 1,500 words; detailed verbatims, competitive-fit heatmap, and appendix diagnostics are iteration work.
