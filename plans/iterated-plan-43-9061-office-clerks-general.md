# Iterated Plan: 43-9061-office-clerks-general

## Objective
Produce a manager-ready retention audit report that separates clearly authorized actions from unresolved decisions, quantifies the workload, and elevates PII/security exposure without overstating minor housekeeping issues.

## Required output shape
1. Cover block.
2. Executive summary with severity counts.
3. Methodology.
4. Findings table.
5. Disposal queue.
6. Archive queue.
7. Open questions for Leo.
8. Environmental and security observations.
9. Sign-off block.

## Execution roadmap
### Pass 0: Normalize the inventory
- Convert the clipboard tally into a structured list by cabinet, drawer, category, year range, and volume.
- Create four action buckets:
  - destroy now,
  - archive offsite,
  - retain on-site,
  - hold pending manager/system review.
- Keep policy logic separate from physical-location observations.

### Pass 1: Build the findings table
- One row per actionable finding.
- Include category, description, volume, severity, recommended action, and target date.
- Severity model:
  - Critical: PII exposure or immediate regulatory/security risk.
  - Major: retention-policy or offsite-storage violation.
  - Minor: housekeeping/environmental issue.

### Pass 2: Draft the executable queues
- Disposal queue:
  - include only items clearly beyond retention with no unresolved status dependency,
  - cite the specific retention schedule row on each line.
- Archive queue:
  - board packets 2016-2020,
  - security incident reports older than the 2-year on-site window, while still within 10-year retention.
- Open questions:
  - signature cards require Symitar account-status cross-check,
  - HR banker boxes require controlled Ops + HR review,
  - unsorted timesheets require sorting before any recommendation,
  - unclaimed property notices require escheat-year verification.

### Pass 3: Elevate security and environmental observations
- Same-day remediation items:
  - loan files with visible SSNs,
  - broken lock on Cabinet A drawer 2,
  - overflowing shred bin if it creates ongoing exposure.
- Housekeeping/preservation:
  - humidity above policy threshold,
  - misplaced storage that is not yet a destruction issue.

### Pass 4: Tighten scannability
- Exec summary should answer:
  - how many critical / major / minor findings,
  - what can be destroyed now,
  - what needs offsite archive,
  - what needs Leo's decision.
- Keep prose factual and non-alarming.

## High-risk failure modes
- Accidentally recommending destruction of records with unresolved retention status.
- Treating all policy misses as equal severity.
- Hiding Leo-decision items inside prose instead of isolating them.
- Failing to quantify volume well enough for shred vendor planning.

## Specific handling rules
- Signature cards: never recommend destruction without account-status confirmation.
- HR boxes: no speculation; controlled review only.
- Exposed SSNs: Critical and same-day remediation.
- Board packets: archive, not shred.
- Security reports: retain, but move offsite per policy.

## Intermediate artifacts
- Normalized inventory sheet by cabinet/drawer/category/year range.
- Severity rubric applied before prose drafting.
- Separate disposal, archive, and open-question queues built as standalone lists.
- Same-day remediation list for security issues.
- Volume summary to support shred-vendor scoping.

## Checkpoints
- Checkpoint 1: nothing enters the disposal queue unless retention status is unambiguous.
- Checkpoint 2: all PII/security exposures are elevated before housekeeping items are written up.
- Checkpoint 3: every queue item cites the retention schedule or policy basis.
- Checkpoint 4: open questions remain open questions, not disguised directives.

## Final QA gate
- If a reader could confuse an approval-required item with clerk-executable action, rewrite the formatting.
- If any category lacks volume context, add best-available quantification.
- If severity labels feel interchangeable, rebalance before finalizing.

## Definition of done
- Leo can read the findings table and queues and make decisions immediately.
- Nothing in the report authorizes destruction that should remain on hold.
- Severity calibration is consistent and defensible.
