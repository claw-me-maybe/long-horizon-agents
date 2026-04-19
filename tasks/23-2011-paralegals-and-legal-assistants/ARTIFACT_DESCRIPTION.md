# Privilege Log and Responsive-Document Index — Keswick v. Fairhaven Manufacturing, Rule 34 Production Set 2

## Occupation
- **SOC:** 23-2011
- **Title:** Paralegals and Legal Assistants

## Scenario
You are a senior litigation paralegal at Thorne & Whitfield LLP supporting partner Marisol Reyes in *Keswick v. Fairhaven Manufacturing, Inc.*, No. 1:25-cv-11427-ADB, pending in the U.S. District Court for the District of Massachusetts before Judge Burroughs. The case is a putative products-liability class action alleging that Fairhaven's "TorqueLock 400" industrial fasteners caused a November 2024 conveyor-line failure at Keswick Logistics' Worcester DC, injuring two workers. Plaintiffs served their Second Request for Production on 2/27/2026 (47 requests). The production deadline is **5/1/2026**. After review of a 38,400-document custodian set from four Fairhaven engineers and two in-house counsel, the associate team has tagged 4,612 documents as responsive; of those, 418 are being withheld on privilege grounds and 92 are being produced in redacted form. You must produce the Rule 34 production index (responsive-document log) and the privilege log that will be served with the production rolling.

## Inputs

**Case metadata**
- Caption: *Keswick v. Fairhaven Manufacturing, Inc.*, No. 1:25-cv-11427-ADB (D. Mass.)
- Governing rules: Fed. R. Civ. P. 26(b)(5)(A) (privilege log); Fed. R. Civ. P. 34(b)(2)(E) (form of production); Local Rule 26.5 (D. Mass.); Judge Burroughs' standing order re: ESI (dated 1/14/2025).
- Protective order entered 12/18/2025 (two tiers: "Confidential" and "Attorney's Eyes Only").
- ESI protocol stipulated 1/22/2026: TIFF+ extracted text, native production for spreadsheets and CAD files, metadata fields per Exhibit A (17 fields).

**Review tool output (from Relativity export, CSV):**
| ControlNum | BegBates | EndBates | Custodian | DocDate | DocType | FileName | Author | Recipients | PrivTag | RedactTag | IssueTag | ReviewerInitials |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 018422 | FHV-0148201 | FHV-0148203 | J. Okonkwo (Engr) | 2024-09-14 | Email | RE_TorqueLock_spec_deviation.msg | J. Okonkwo | R. Whelan; M. Pasternak | — | — | ROOT-CAUSE; DESIGN-CHG | KAC |
| 018599 | FHV-0151880 | FHV-0151881 | M. Pasternak (VP Eng) | 2024-11-20 | Email | FW_post-incident_call_w_counsel.msg | M. Pasternak | S. Ortega (GC); D. Hu (outside counsel, Thorne&W) | ACP | — | POST-INC; COUNSEL | KAC |
| 019104 | FHV-0160044 | FHV-0160088 | S. Ortega (GC) | 2024-12-02 | Memo | Torquelock_root_cause_memo_DRAFT.docx | S. Ortega | M. Pasternak; D. Hu | ACP; WP | — | POST-INC; ROOT-CAUSE | TLM |
| 019220 | FHV-0162115 | FHV-0162116 | R. Whelan (Engr) | 2024-08-11 | Email | fatigue_testing_q2_summary.msg | R. Whelan | J. Okonkwo; external — acme-materials.com | — | REDACT-3P | DESIGN-CHG | KAC |
| 019488 | FHV-0169900 | FHV-0169923 | D. Hu (outside counsel) | 2024-12-09 | Memo | Preservation_and_litigation_hold_update.docx | D. Hu | S. Ortega; M. Pasternak | ACP; WP | — | HOLD; COUNSEL | TLM |
| 019712 | FHV-0175402 | FHV-0175402 | J. Okonkwo | 2024-07-02 | Spreadsheet | torquelock_qc_failures_2024.xlsx | J. Okonkwo | — | — | REDACT-PII | QC-DATA | KAC |
| (4,600+ more rows …) | | | | | | | | | | | | |

**Privilege tag legend (internal):**
- `ACP` = attorney-client privilege
- `WP` = work product
- `ACP; WP` = both asserted
- `JD` = joint defense / common interest
- `REDACT-PII` = personal information redaction only
- `REDACT-3P` = third-party confidentiality redaction

**Case schedule pressures**
- Rolling production ordered: 25% by 4/10 (already served); 50% by 4/24; 100% by 5/1.
- Meet-and-confer with plaintiffs' counsel (Halsey & Doud) scheduled 4/28/2026; likely challenge to the privilege log.
- Judge Burroughs' standing order requires **document-by-document logging** (categorical logging is NOT permitted absent advance motion), and requires that emails-with-attachments be logged as separate entries.

**Attorney instructions from M. Reyes (4/15/2026 email):**
> Please prepare (a) the privilege log in the format we used in *Halverson v. Pemberton* last year — document-by-document, with subject-matter descriptions precise enough to survive a Burroughs challenge but not so detailed they waive privilege; and (b) the responsive-production index cross-walking Bates ranges to RFP numbers. Cite the rule basis for each withholding (ACP, WP, or both). Flag the five highest-risk log entries for my personal review before service. The 12/2 Ortega draft memo (019104) needs particular care — the subject-matter description must not reveal the factual investigative content, only the legal-advice framing.

**Known issues the reviewer team flagged for escalation (not yet resolved):**
- 31 emails between in-house counsel S. Ortega and outside counsel D. Hu (Thorne & Whitfield) dated pre-incident (before 11/14/2024). Privilege asserted, but several appear to concern routine commercial contracting, not legal advice — candidate for re-review.
- 14 documents where the custodian is an engineer but the email chain "loops in counsel" at the bottom. Plaintiffs will challenge as non-privileged under *In re Grand Jury*, 13 F.4th 710 (9th Cir. 2021) (dominant-purpose test) — note: First Circuit test may differ; flag for attorney.
- 4 documents authored by a *former* outside counsel (Rickover & Associates, terminated 2023) — need to confirm ACP still attaches and log accordingly.
- The 12/2 Ortega root-cause memo (019104) exists in 3 drafts (019104, 019105, 019106) — decide whether to log as 3 separate entries or one with a drafting-history note.

## Artifact specification
This is a two-part deliverable in a single markdown file:

### Part A — Privilege Log
Table with the following columns, per Local Rule 26.5 and Judge Burroughs' standing order:
1. **Log No.** (sequential, PL-0001, PL-0002, …)
2. **Bates Range** (or "Withheld in Full — no Bates")
3. **Document Date**
4. **Document Type** (Email, Memo, Draft, Attachment, Spreadsheet, etc.)
5. **Author / From**
6. **Recipients (To; Cc; Bcc)** — full names with role/affiliation on first occurrence; thereafter initials acceptable only if a master legend appears at end
7. **Subject / Subject Matter Description** — sufficient detail to permit assessment per *United States v. Construction Products Research, Inc.*, 73 F.3d 464 (2d Cir. 1996), without disclosing privileged content. Use formulations like "Email reflecting request for legal advice regarding [subject matter, generalized]" rather than "Email about root cause of conveyor failure."
8. **Privilege Asserted** — ACP / WP / ACP & WP / Common Interest
9. **Basis (rule citation)** — Fed. R. Civ. P. 26(b)(3) for WP; common-law ACP; *Upjohn Co. v. United States*, 449 U.S. 383 (1981) for corporate ACP where applicable
10. **Redaction vs. Withheld in Full** — R / WIF
11. **Attachment Parent / Child Link** — required for family groupings

Must include a master legend of names/roles at the end. Must include at least 15 representative log entries drawn from the inputs above, with a clear placeholder/pagination indicating the full log continues.

### Part B — Responsive-Production Index
Table mapping served production to plaintiffs' RFP numbers:
1. **Bates Range**
2. **RFP No.(s) Responsive**
3. **Custodian**
4. **Doc Date**
5. **Produced As** (Native / TIFF+text / Redacted TIFF)
6. **Confidentiality Designation** (None / Confidential / AEO per protective order)
7. **Notes** (e.g., "Redacted for third-party PII per ¶7 of PO")

Required: a short **Production Cover Statement** above the index citing Fed. R. Civ. P. 34(b)(2)(B) & (E), stating the production is being made subject to the 12/18/2025 protective order, identifying the production set number (Set 2), and referencing the ESI protocol.

### Additional required elements
- **Open-issues memo to Reyes** (1 page) flagging the four known escalation items above plus the five highest-risk log entries for partner review before service. Internal-use only; will not be served.
- **Tag-to-log reconciliation table** (short) showing counts: total reviewed, total responsive, total privileged (broken out by ACP, WP, ACP+WP, CI), total redacted, total produced. Used for QC before service.

Citation style: **Bluebook (21st ed.)** for any case law; federal rule citations in standard form ("Fed. R. Civ. P. 26(b)(5)(A)"). Tone: neutral, procedural, precise. No advocacy. This is a service document, not a brief.

## Output format
Single Markdown file rendering:
- Production Cover Statement (short prose)
- Privilege Log (table; at least 15 representative entries plus a "[log continues — PL-0016 through PL-0418 omitted for brevity in fixture]" placeholder)
- Responsive-Production Index (table; at least 12 representative rows plus continuation marker)
- Master Legend of names/roles
- Tag-to-log reconciliation
- Internal open-issues memo to partner

Target length: 350–500 lines of markdown source (most in tables).

## Iteration targets
1. **Tighten subject-matter descriptions on ACP entries to avoid the two failure modes** — (a) overly vague ("legal matters"), which invites a Burroughs challenge and potential in-camera review, and (b) overly specific ("root cause analysis of 11/14 TorqueLock failure"), which risks subject-matter waiver. Target formulation: "Communication seeking / reflecting legal advice regarding [generalized topic]."
2. **Fix the email-family logging.** v1 often logs a parent email and silently drops attachments into the same row; Burroughs' standing order requires separate entries with parent/child cross-references.
3. **Reconcile the 12/2 Ortega draft-memo issue.** Three drafts (019104–019106) should be logged either as three separate entries or as one with explicit drafting-history notation; v1 is likely inconsistent. Flag for partner decision rather than silently choosing.
4. **Apply the correct ACP framework for corporate in-house counsel communications** — cite *Upjohn*, and note First Circuit practice for dominant-purpose analysis rather than reflexively applying the Ninth Circuit *In re Grand Jury* test; the engineer-led chains "looping in counsel" need the most careful treatment.
5. **Cross-check the Production Index against the privilege log** — no Bates range should appear on both. v1 frequently has overlaps because of redacted-and-produced items being double-counted.
6. **Flag the four pre-incident in-house/outside-counsel communications for re-review**, rather than quietly claiming privilege; these are the weakest link and are the most likely to draw a motion to compel.

## Success criteria
- Every log entry has all 11 required columns populated; no "TBD" or placeholder text in served columns.
- Subject-matter descriptions are specific enough to permit *prima facie* privilege assessment (per *Constr. Prods. Rsch.*) but do not disclose the privileged content itself.
- Email-family relationships (parent emails and attachments) are logged as separate entries with cross-references, consistent with Burroughs' standing order.
- The Production Index and the Privilege Log do not double-list the same Bates range except where redaction-and-production is explicit.
- The internal open-issues memo identifies at least the four escalation items plus five highest-risk entries, with a recommended disposition for each.
- Tag-to-log reconciliation numbers internally reconcile (privileged + produced + redacted = total responsive) with no unexplained variance.
- No privileged content is inadvertently disclosed in the log descriptions themselves (paralegal-level waiver risk).

## Scope target
v1 at ~15 minutes should contain: a Production Cover Statement citing Rule 34 and the PO; a privilege log with at least 15 entries populated in all 11 columns, including all six sample rows from the inputs plus representative entries covering ACP-only, WP-only, ACP+WP, and common-interest assertions; a responsive-production index with at least 12 rows cross-walked to RFP numbers; and a master legend with at least the six named individuals. Likely deferred to iteration: the tag-to-log reconciliation table, the full open-issues memo with recommended dispositions for the four escalation items, the family-group parent/child cross-references for every email-attachment pair, and refinement of the subject-matter descriptions to the *Upjohn* / First-Circuit-dominant-purpose standard. Expect approximately 250–320 lines on first pass.
