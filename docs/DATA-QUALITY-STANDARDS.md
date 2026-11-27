# Data Quality Standards

## Quality dimensions

- **Completeness:** Required values and records are present.
- **Validity:** Values conform to defined types, formats and permitted ranges.
- **Uniqueness:** Records satisfy the agreed uniqueness rules.
- **Consistency:** Values agree across fields, records and sources where expected.
- **Integrity:** Relationships and business constraints are respected.
- **Timeliness:** Data is sufficiently current for the reporting purpose.
- **Accuracy:** Values are supported by an appropriate source or reconciliation process.

## Separate issue severity from record disposition

Severity describes the seriousness of an issue. It does not determine by itself whether a record is retained, corrected, quarantined or rejected.

Use the following severity labels:
- **INFO:** Informational observation; no material quality failure identified.
- **WARNING:** Issue requiring disclosure, review or controlled treatment; record may remain usable.
- **ERROR:** Violation of a defined critical rule; record or dataset requires quarantine, rejection or remediation.

A record may have multiple issue entries and more than one severity.

## Final record disposition

For workflows that require record-level accountability, assign exactly one mutually exclusive final disposition to each source record candidate:

- **RETAINED_AS_IS:** retained without value correction.
- **CORRECTED:** retained after approved deterministic correction(s).
- **QUARANTINED:** held for human review because safe treatment or business meaning is uncertain.
- **REJECTED:** excluded for violation of a defined critical rule.
- **EXCLUDED_NON_RECORD:** structural content that is not a business record, such as a repeated header, title, blank separator or subtotal.
- **REMOVED_AS_DUPLICATE:** exact duplicate removed under an explicit policy, with its retained counterpart identified.

Do not conflate severity with disposition. Multiple issue rows may refer to one source record, but its final disposition must be singular. Disposition rules must be explicit, justified and consistently applied.

## Duplicate and missing-value handling

- Do not assume repeated rows are duplicates.
- Distinguish exact duplicates from near-duplicate candidates.
- Remove exact duplicates only under an explicit business-field equality rule and retain traceability to the retained counterpart.
- Flag near-duplicates for review; do not automatically merge them without an approved rule.
- Preserve missing values when no defensible replacement exists.
- Do not convert missing numeric values to zero or infer business values by default.
- Quarantine or reject missing/invalid values only where explicit critical rules require it.

## Lineage, exceptions and reconciliation

- Preserve a stable source reference for each record candidate, including source file and original sheet/row location where applicable.
- Carry lineage into clean outputs, exception registers and reconciliation artefacts.
- Record rule ID, field, issue, severity, treatment and review status for exceptions.
- Account for every source candidate exactly once in a mutually exclusive final disposition ledger.
- Identify retained counterparts for removed exact duplicates.
- Record structural non-record rows as excluded, not silently discarded.
- Reconcile source counts to disposition counts and output counts.
- Reconcile relevant control totals with documented treatment of exclusions, corrections, currencies and rounding.
- Investigate and explain all differences; no unexplained variance is acceptable.

## Validation outcomes

- **PASS:** The record or check satisfies the defined rule.
- **WARNING:** An issue exists but may be retained with documented treatment or disclosure.
- **FAIL:** A critical rule is violated; the record or dataset is held or rejected pending resolution.

These statuses apply only relative to explicit rules. They do not imply universal correctness. A check result is separate from issue severity and final record disposition.

## Required controls

- Define each rule and its business rationale.
- Record input and output counts.
- Quantify missing, duplicate, invalid and rejected records where relevant.
- Preserve rejected records or a traceable exception record.
- Document cleaning and transformation logic.
- Reconcile important counts, totals and aggregations.
- Record assumptions, thresholds and known limitations.
- Re-run checks after material transformations.
- For reproducible file workflows, record source fingerprint, run identifier, tool/rule versions and output fingerprints.

## Quality report

A service quality report should identify dataset/version, profiling scope, rules executed, results, severity counts, disposition counts, remediation, reconciliation, unresolved issues and suitability for the intended use.
