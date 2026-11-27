# Data Intake Standards

## Purpose

Establish a consistent, safe and documented process for receiving and assessing data before transformation or reporting.

## General intake checklist

1. **Source:** Identify origin, owner, extraction date and provenance where known.
2. **Permission:** Confirm authority to use the data for the stated purpose.
3. **Format:** Identify file/database format, encoding, delimiters and sheet/table structure.
4. **Structure:** Inspect columns, keys, relationships, row grain and schema consistency.
5. **Completeness:** Identify missing required fields and unexpected empty records.
6. **Validity:** Inspect data types, formats, ranges, categories and date values.
7. **Uniqueness:** Identify candidate keys and possible duplicates; do not assume every repeated row is erroneous.
8. **Consistency:** Check naming, units, currencies, time zones and category conventions.
9. **Integrity:** Check relationships and business rules where applicable.
10. **Sensitivity:** Identify personal, confidential, financial or otherwise restricted information.
11. **Suitability:** Decide whether the dataset can support the requested reporting question.

## Spreadsheet-specific intake checklist

For spreadsheet-centred services, additionally record:
- Workbook filename, file type, size and SHA-256 fingerprint.
- Sheet names, hidden sheets and relevant workbook structure.
- Header row locations and duplicate/blank/merged header concerns.
- Title rows, blank separators, repeated headers, footers and embedded subtotals/totals.
- Formula cells, hard-coded values, merged cells, filters, hidden rows/columns and formatting-dependent values where relevant.
- Expected record grain and candidate key.
- Original worksheet row position for source lineage.
- Locale-sensitive date, decimal and thousands separators.
- Currency, units, time zone and reporting-period assumptions.
- Whether structural artefacts can be distinguished from genuine business records.

Do not remove a row solely because it is blank, repeated or formatted differently. Classify it using explicit rules and retain its source location in the intake/profile or reconciliation evidence.

## Intake record

For each demonstration or engagement, record:
- Dataset identifier and description.
- Source and permission basis.
- Received date and reporting period.
- File format/schema and expected grain.
- Record count and relevant field inventory.
- Sensitivity classification and handling requirements.
- Known limitations and assumptions.
- Intake decision and reviewer/date.
- For reproducible file-based runs, source fingerprint and run identifier.

## Handling rules

- Preserve the original source as read-only where practical.
- Work from a controlled copy.
- Never commit confidential, personal or client data to a public repository.
- Do not place secrets, credentials or connection strings in source control.
- Use synthetic or appropriately licensed public data in public demonstrations.
- Restrict access and retention according to the data owner's requirements.
- Do not infer missing business values or silently discard records.
- Keep source-row references when transforming, filtering, quarantining or excluding records.
- Record transformations and exclusions in a traceable register.

## Intake outcomes

**ACCEPT:** Suitable for the defined purpose and handling requirements are met.  
**ACCEPT WITH CONDITIONS:** Usable only with documented limitations, exclusions or remediation.  
**REJECT / HOLD:** Permission, sensitivity, integrity or suitability concerns prevent safe processing.
