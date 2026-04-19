# Records Retention Audit Report — Harborstone Community Credit Union Q1 2026

## Occupation
- **SOC:** 43-9061
- **Title:** Office Clerks, General

## Scenario
Harborstone Community Credit Union (a 4-branch CU in Bellingham, WA, ~$320M assets) is preparing for its biennial NCUA examination scheduled June 8, 2026. The Operations Manager, Leo Faraday, has asked you (Morgan Kessler, general office clerk, 2 years tenure) to audit the main-office file room and produce a findings report by April 24. You spent three afternoons between April 13-15 physically auditing the paper file cabinets in Room 214 and cross-referencing against the credit union's published Records Retention Schedule v4.2 (issued 2024-11-01).

## Inputs
**Records Retention Schedule v4.2 — relevant categories:**
| Category | Retention | Disposal method |
|---|---|---|
| Member loan files (closed) | 7 years post-payoff | Shred |
| Member account signature cards | Life of account + 7 yrs | Shred |
| Employee timesheets (paper) | 4 years | Shred |
| Vendor invoices paid | 7 years | Shred |
| Monthly board packets | 10 years | Archive to offsite |
| Marketing proofs/drafts | 2 years | Recycle |
| Daily teller proof sheets | 5 years | Shred |
| Training attendance rosters | 3 years | Recycle |
| Security incident reports | 10 years | Archive to offsite |
| Unclaimed property notices | 5 years + escheat year | Shred |

**Your audit tally (raw, from clipboard):**
```
Cabinet A (4-drawer, north wall):
  Drawer 1: Loan files, closed 2012-2015 — 47 folders. Past retention (>7 yrs).
  Drawer 2: Loan files, closed 2016-2019 — 62 folders. Mixed; some past, some within.
  Drawer 3: Loan files, closed 2020-2023 — 84 folders. Within retention.
  Drawer 4: Signature cards, 1998-2008 accounts — 211 cards. Accounts status unknown; need cross-check w Symitar.

Cabinet B (4-drawer, east wall):
  Drawer 1: Teller proof sheets, 2018-2020 — complete. Within retention (5 yr).
  Drawer 2: Teller proof sheets, 2015-2017 — complete. Past retention.
  Drawer 3: Vendor invoices 2017-2019 — 14 binders. Within retention.
  Drawer 4: Vendor invoices 2010-2016 — 22 binders. Past retention.

Cabinet C (3-drawer lateral, south wall):
  Drawer 1: Board packets 2016-2020 — 60 packets. Within retention (10 yr). Should be offsite, NOT here.
  Drawer 2: Marketing drafts 2019-2024 — approx. 3 linear feet. Past retention except 2024.
  Drawer 3: Training rosters 2019-2023 — 41 rosters. Mixed.

Cabinet D (file safe, fireproof):
  Top shelf: Security incident reports 2014-2025 — 18 reports. Within retention but per policy should be offsite after 2 yrs on-site.
  Middle: Unclaimed property notices 2018-2024 — 7 bundles. Need to verify escheat years.
  Bottom: EMPTY.

Loose items on top of Cabinet A: 4 banker's boxes labeled "misc HR 2015" — unknown contents, not opened yet.
Loose items behind Cabinet B: stack of employee timesheets in rubber bands — approx 2019-2022, not sorted.

Noted during audit:
- Shred bin in Room 214 is overflowing (last pickup was 2/28 per log).
- Cabinet A drawer 2 has a broken lock.
- Humidity in Room 214 was 62% on 4/14 (policy: <55%).
- Found 2 loan files with member SSNs visible through torn folder windows.
```

## Artifact specification
Produce an internal findings report with the following sections:
1. **Cover block** — title, author, date, addressee (Leo Faraday), audit period, scope (Main Office Room 214)
2. **Executive summary** — 3-5 sentences: overall disposition, count of findings by severity
3. **Methodology** — dates of fieldwork, sources of criteria, what was and was not examined
4. **Findings table** — columns: Finding #, Category, Description, Volume (folders/linear feet), Severity (Critical/Major/Minor), Recommended action, Target date
5. **Disposal queue** — explicit list of what can be destroyed now, with retention citations
6. **Archive queue** — what must be boxed and sent offsite (board packets, security reports >2yr)
7. **Open questions requiring Ops Manager decision** — the 4 banker's boxes, the signature-card cross-check with core system (Symitar), the unsorted timesheets
8. **Environmental and security observations** — humidity, broken lock, exposed SSNs, overflowing shred bin
9. **Sign-off block**

Tone: factual, non-alarming, actionable. Severity levels should be applied consistently (Critical = regulatory exposure or PII risk; Major = policy violation; Minor = housekeeping).

## Output format
Single Markdown file, ~3 pages rendered (180-280 lines source).

## Iteration targets
1. **Assign severity consistently** — v1 may label everything the same; v2 should treat exposed SSNs and unsorted timesheets-with-PII as Critical, offsite-policy violations as Major, and humidity/shred-bin as Minor.
2. **Separate what you can do alone from what needs Leo's approval** — the disposal queue should only list items where retention is clearly exceeded AND policy allows clerk-initiated shred; everything else belongs in open questions.
3. **Cite the retention schedule explicitly** — each disposal recommendation should reference the category row, not just say "past retention."
4. **Address the signature-card problem properly** — v1 may propose shredding 1998-2008 cards; v2 recognizes these cannot be destroyed without a Symitar cross-check because "Life of account + 7 years" requires knowing account status.
5. **Handle the 4 unlabeled HR boxes** — don't speculate on contents; propose a controlled review by Ops + HR before any disposition.
6. **Quantify** — replace vague "approx 3 linear feet" with best-available volume estimates and folder counts so Leo can scope the shred vendor PO.

## Success criteria
- No recommendation destroys records that are still within retention or whose status is indeterminate (signature cards, HR boxes).
- Exposed-SSN finding is elevated to Critical with same-day remediation proposed.
- Every disposal line includes a retention-schedule citation.
- Board packets 2016-2020 are correctly routed to archive, not kept or shredded.
- Open questions are genuinely open, not disguised recommendations.
- Report is scannable: a manager could read the exec summary and findings table and make decisions without reading the prose.

## Scope target
A v1 in ~15 minutes should contain: cover block, exec summary, findings table covering at least 8 of the cabinets/items, explicit disposal and archive queues, and the environmental/security observations. Refining severity gradations, adding retention citations per line, and fully treating the signature-card ambiguity belong to iteration.
