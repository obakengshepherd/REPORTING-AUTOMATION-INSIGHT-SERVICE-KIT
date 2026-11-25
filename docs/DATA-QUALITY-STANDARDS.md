# Data Quality Standards

## Quality dimensions

- **Completeness:** Required values and records are present.
- **Validity:** Values conform to defined types, formats and permitted ranges.
- **Uniqueness:** Records satisfy the agreed uniqueness rules.
- **Consistency:** Values agree across fields, records and sources where expected.
- **Integrity:** Relationships and business constraints are respected.
- **Timeliness:** Data is sufficiently current for the reporting purpose.
- **Accuracy:** Values are supported by an appropriate source or reconciliation process.

## Validation outcomes

- **PASS:** The record or check satisfies the defined rule.
- **WARNING:** An issue exists but may be retained with documented treatment or disclosure.
- **FAIL:** A critical rule is violated; the record or dataset is held or rejected pending resolution.

These statuses apply only relative to explicit rules. They do not imply universal correctness.

## Required controls

- Define each rule and its business rationale.
- Record input and output counts.
- Quantify missing, duplicate, invalid and rejected records where relevant.
- Preserve rejected records or a traceable exception record.
- Document cleaning and transformation logic.
- Reconcile important counts, totals and aggregations.
- Record assumptions, thresholds and known limitations.
- Re-run checks after material transformations.

## Important handling decisions

A missing numeric value must not automatically become zero. A repeated record must not automatically be deleted. A format correction must not change meaning. Currency, units, time zones and reporting periods must be explicit.

## Quality report

A service quality report should identify dataset/version, profiling scope, rules executed, results, exception counts, remediation, unresolved issues and suitability for the intended use.
