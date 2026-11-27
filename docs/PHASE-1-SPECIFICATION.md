# Phase 1 Specification — Spreadsheet Cleaning & Restructuring

**Specification status:** APPROVED FOR IMPLEMENTATION — 27 NOVEMBER 2026  
**Implementation status:** IN PROGRESS — RASK-P1-I1 ASSIGNED  
**Phase:** 1  
**Specification owner:** ChatGPT — Primary AI  
**Decision authority:** Product Owner  
**Architecture review:** Claude, RASK-ARCH-REV-001  
**Product Owner review decision:** Recommendations approved as proposed

## 1. Purpose and outcome

Deliver a bounded, reproducible service demonstration that receives a deliberately imperfect small-business sales/order spreadsheet, profiles it, applies explicit and traceable cleaning rules, restructures the data, produces client-usable outputs and reconciles every source record candidate.

The demonstration must make its work explainable. It must not silently invent business values, erase exceptions or imply that a synthetic scenario represents a real client engagement.

This document incorporates the Product Owner-approved recommendations from Claude's read-only architecture review and the Product Owner's engineering activation directive of 27 November 2026. The Phase 1 implementation scope is approved.

## 2. Business scenario

A small business operations team exports order-line records from a basic order-management process. The spreadsheet has accumulated inconsistent formatting, missing fields, repeated records and structural artefacts. Before the information can support routine reporting, it needs controlled preparation and a clean, consistent output.

The scenario is illustrative and synthetic. It does not represent a real client, contract, business outcome or production system.

## 3. Dataset and grain

### 3.1 Approved direction

- Scenario: synthetic small-business sales/orders.
- Target size: approximately 1,000–10,000 source data rows, including seeded structural artefacts.
- Grain: one order line per valid business record.
- Candidate key: `OrderLineID`.
- Data source: generated synthetic dataset with documented generator and fixed random seed.
- Provenance: generator, generation parameters, seed, creation date and synthetic-data statement documented in the repository.

The generator and manifest must be deterministic: the same approved seed and parameters should reproduce the same source dataset and seeded issue set.

### 3.2 Final source schema

One row represents one order line.

| Field | Type / rules |
|---|---|
| `OrderLineID` | Required string, `OL-` plus six digits; candidate business key |
| `OrderID` | Required synthetic string, `ORD-` plus six digits |
| `OrderDate` | Required ISO date in clean output; ambiguous source dates quarantined |
| `CustomerID` | Nullable synthetic string; preserve missing value and report WARNING |
| `ProductID` | Required synthetic string, `PRD-` plus four digits |
| `ProductCategory` | Nullable string; trim/canonicalise known labels only; ambiguous/unknown labels quarantined |
| `Quantity` | Required positive integer; invalid/non-positive values rejected |
| `UnitPrice` | Required non-negative decimal, 2 fractional digits; missing/unparseable values quarantined |
| `DiscountRate` | Required decimal fraction, inclusive range 0–1; out-of-range values rejected |
| `CurrencyCode` | ZAR only; other currencies rejected |
| `LineAmount` | Derived/check field, 2 fractional digits |

Use fictional identifiers/categories only. Do not generate real names, contact details, addresses or account identifiers. Dates are synthetic and confined to 2025–2026.

**Canonical financial rule:** `LineAmount = Quantity × UnitPrice × (1 − DiscountRate)`, calculated with `Decimal` and rounded per line to two decimal places using `ROUND_HALF_UP`. Currency is ZAR. No tax, shipping or foreign-exchange calculations are in scope.

### 3.3 Seeded issue manifest

The machine-readable manifest is `manifests/seeded-issues.json`. Use fixed generator seed `20261127`. It must encode stable business identifiers or structural anchors, issue class, source field/location, expected detection, severity and expected disposition.

| Seed | Target | Condition | Expected treatment |
|---|---|---|---|
| 001 | OL-000101 | Category whitespace | CORRECTED |
| 002 | OL-000202 | Category case variation | CORRECTED |
| 003 | OL-000303 | Missing CustomerID | RETAINED_AS_IS; WARNING; preserve null |
| 004 | OL-000404 | Quantity zero | REJECTED |
| 005 | OL-000505 | Missing UnitPrice | QUARANTINED |
| 006 | OL-000606 | DiscountRate greater than 1 | REJECTED |
| 007 | OL-000707 compared with OL-000706 | Near-duplicate pattern, distinct line IDs | Keep both; WARNING; no merge |
| 008 | OL-000808 | Incorrect source LineAmount | CORRECTED using canonical formula |
| 009 | OL-001010 | Ambiguous date `03/04/2026` | QUARANTINED; do not guess locale |
| 010 | Duplicate occurrence of OL-000909 | Exact duplicate | REMOVED_AS_DUPLICATE; retained counterpart recorded |
| 011 | Workbook opening | Merged title row and blank separator before headers | EXCLUDED_NON_RECORD |
| 012 | After source record 500 | Repeated header row | EXCLUDED_NON_RECORD |
| 013 | After source record 1,000 | Subtotal row | EXCLUDED_NON_RECORD |

Generate 1,500 base order-line records in one worksheet named `Orders`. Place the title and blank row before headers on row 3. Insert repeated-header and subtotal artefacts at the stated record anchors. Tests must assert manifest cases against independent expected outcomes; do not derive expected results from the cleaner itself.

## 4. Scope

### 4.1 In scope

1. Inspect workbook/file structure, sheet names, headers, row grain and schema.
2. Preserve the original source as immutable input for each run.
3. Profile completeness, validity, uniqueness, consistency and relevant control totals.
4. Detect and classify structural and value-level issues.
5. Apply deterministic, documented transformations approved in the rule register.
6. Retain nulls when no defensible replacement is available; do not impute.
7. Identify exact duplicates and near-duplicate candidates using distinct policies.
8. Maintain source-row lineage through every output and exception.
9. Produce clean structured data, exception evidence, rule register, reconciliation and run metadata.
10. Export client-facing XLSX and machine-readable CSV outputs.
11. Execute automated tests for seeded cases and core invariants.
12. Document reproducibility, limitations and handover instructions.

### 4.2 Out of scope

- Real client, personal, confidential or regulated data.
- Production ingestion, external integrations, APIs, cloud infrastructure or orchestration.
- SQL Server, Power BI, Power Query or a second parallel implementation for this phase.
- General-purpose cleaning platform, shared framework or speculative `shared/` library.
- GUI, web application, service API or deployment packaging.
- Automatic imputation or inference of ambiguous business values.
- Fuzzy matching that silently merges near-duplicates.
- Enterprise-scale performance claims.
- Commercial or client outcome claims.

## 5. Technology decision for Phase 1

**Approved Phase 1 implementation direction:** Python with pandas for deterministic data processing; pytest for automated tests; XLSX as the human-facing workbook output; CSV as the machine-readable output.

Excel remains the delivery format, not a second transformation engine. Power Query is deferred for this phase to avoid implementing the same workflow twice. The broader project toolkit approved in the foundation remains unchanged; this is a phase-specific tool selection.

Pinned baseline: Python 3.11 or 3.12, pandas 2.2.3, openpyxl 3.1.5 and pytest 8.3.4. Record actual versions in run metadata. No additional dependencies without demonstrated need.

## 6. Workflow

1. **Intake:** record source identifier, provenance, permission, file format, reporting period, expected grain, sensitivity and limitations.
2. **Fingerprint:** calculate SHA-256 for the source file and record the fingerprint in run metadata.
3. **Inspect/profile:** identify sheets, header rows, structural artefacts, field types, nulls, ranges, candidate keys, duplicates and distributions.
4. **Classify:** apply explicit rule IDs, severity and proposed disposition; ambiguous cases are flagged for review.
5. **Transform:** run deterministic, documented transformations on a working copy; never mutate the source.
6. **Disposition:** assign exactly one final disposition to each source record candidate in the reconciliation ledger.
7. **Validate:** run quality checks, invariant tests and count/value reconciliation.
8. **Deliver:** write XLSX and CSV clean outputs plus exception, rule, reconciliation and run artefacts.
9. **Record:** retain execution instructions, versions, fingerprints, known limitations and verification evidence.

## 7. Rule and issue model

### 7.1 Severity

Severity communicates issue seriousness and is independent of what happens to a record:
- `INFO`
- `WARNING`
- `ERROR`

A record may have multiple issues of different severities.

### 7.2 Final record disposition

Every source record candidate must receive exactly one final disposition:
- `RETAINED_AS_IS` — valid and retained without a value correction.
- `CORRECTED` — retained after one or more approved deterministic corrections.
- `QUARANTINED` — held for human review because meaning or safe treatment is uncertain.
- `REJECTED` — excluded because it violates a defined critical rule and is not suitable for use.
- `EXCLUDED_NON_RECORD` — structural content such as a repeated header, title, blank separator or subtotal that is not a business record.
- `REMOVED_AS_DUPLICATE` — exact duplicate removed under the approved exact-duplicate policy, with its retained counterpart identified.

The disposition is mutually exclusive per source candidate. Severity is not a disposition. The exception register may contain multiple issue rows for one source candidate.

## 8. Duplicate and missing-value policies

### 8.1 Exact duplicates
Exact duplicates may be removed from the clean output only when equality is evaluated against the approved business-record fields and the retained counterpart is identified. Preserve every source occurrence in the reconciliation ledger and log the removed duplicate. Do not treat structural rows as duplicate business records.

### 8.2 Near-duplicates
Near-duplicate candidates must be flagged for review. Do not automatically merge, delete or select a winner based on similarity alone. Unless a separate approved rule resolves them, preserve them as records and record the review issue.

### 8.3 Missing values
Do not impute missing business values. Preserve nulls where the output schema permits and report the missingness. If a missing field violates a critical rule, quarantine or reject according to the explicit rule. Never convert missing numeric values to zero by default.

## 9. Source-row lineage and traceability

Assign a stable source reference to every source row/candidate, based on source file fingerprint, sheet and original row position or an equivalent reproducible identifier.

Carry that reference into:
- Clean output rows.
- Exception records.
- Reconciliation ledger.
- Transformation/rule evidence where applicable.

For exact duplicates, record both the removed source reference and the retained counterpart. For structural non-record rows, record their source location and `EXCLUDED_NON_RECORD` disposition. No source candidate may disappear without a ledger entry.

## 10. Artefact contracts

Use small, explicit artefacts rather than a generic shared software framework.

| Artefact | Minimum content |
|---|---|
| Data dictionary | Field name, definition, type, business meaning, nullability and relevant constraints |
| Rule register | Rule ID, field/scope, description, rationale, severity, action, expected result and version |
| Exception register | Source reference, rule ID, field, observed issue/value (safe synthetic data only), severity, proposed/final treatment and review status |
| Reconciliation ledger | One row per source candidate; source reference, candidate key if available, final disposition, retained counterpart where applicable and reason |
| Reconciliation summary | Source candidates, clean records, counts by disposition, exception counts, control totals and unexplained differences |
| Run record | Run ID/time, source SHA-256, generator/seed where relevant, tool versions, parameters, rule-set version and output fingerprints |
| Seeded-issue manifest | Seeded issue ID, class, source location, field/structural location, expected detection and expected treatment |

The artefacts are file-level contracts for this workflow. Do not create a general shared framework or library in Phase 1.

## 11. Outputs and proposed repository layout

Approved service-specific layout:

- `services/spreadsheet-cleaning/README.md`
- `services/spreadsheet-cleaning/src/`
- `services/spreadsheet-cleaning/tests/`
- `services/spreadsheet-cleaning/manifests/`

Runtime inputs/outputs and reports are created on demand and supplied through CLI paths. Do not commit generated workbooks/reports. Commit the generator, manifest, source code and tests. Tests use temporary directories.

Expected run outputs:
- Cleaned XLSX workbook.
- Cleaned CSV.
- Exception register.
- Reconciliation ledger and summary.
- Rule register and data dictionary.
- Run metadata with input/output fingerprints.
- Human-readable quality summary and execution instructions.

## 12. Reconciliation requirements

Every source row/candidate must be accounted for exactly once in the final disposition ledger. Reconciliation must establish:
- Source row candidates = sum of counts across all mutually exclusive final dispositions.
- Clean output row count = `RETAINED_AS_IS` + `CORRECTED` records, subject to documented output-grain rules.
- `REMOVED_AS_DUPLICATE` entries identify a retained counterpart.
- `EXCLUDED_NON_RECORD`, `QUARANTINED` and `REJECTED` records are not silently included in the clean output.
- No unexplained source-to-output count difference.
- Relevant order-line quantities and monetary control totals reconcile according to the explicitly defined treatment of exclusions, corrections, duplicates and quarantined records.
- Any legitimate difference is itemised by disposition and reason.

Approved controls: ZAR only; Decimal arithmetic; per-line ROUND_HALF_UP to two decimals; no FX, tax or shipping. Report physical worksheet rows separately from business source candidates; counts by mutually exclusive disposition; clean output count = RETAINED_AS_IS + CORRECTED; computable quantity and canonical amount totals by disposition; clean-output totals; exact duplicate counts and retained-counterpart references. A monetary control is computable only when quantity, unit price and discount are valid. Never coerce invalid/null values to zero. The disposition partition and computable source quantity/amount totals must balance exactly. Clean-output totals are a subset and need not equal full source totals when records are rejected, quarantined, excluded or removed as duplicates.

## 13. Verification and acceptance criteria

Phase 1 can be proposed for acceptance only when all of the following are evidenced:

1. Synthetic provenance, generator parameters and fixed seed are documented.
2. No real personal or confidential information is present.
3. Original input is preserved and SHA-256 is recorded.
4. Source schema, grain and candidate key are documented.
5. Seeded-issue manifest exists and matches the test fixture.
6. Structural and value-level issues are detected as expected.
7. Every transformation is deterministic and mapped to a documented rule.
8. Severity and final disposition are represented separately.
9. Every source candidate has exactly one disposition and traceable lineage.
10. Exact duplicates are removed only under the stated policy; near-duplicates are flagged, not automatically merged.
11. Missing values are not silently imputed.
12. Exceptions and ambiguous cases remain traceable for review.
13. Reconciliation counts balance with zero unexplained difference.
14. Defined control totals reconcile with documented currency/rounding treatment.
15. Automated tests cover seeded cases, contracts, reconciliation and key invariants.
16. XLSX and CSV outputs are readable and consistent.
17. A technically competent person can reproduce the run from repository instructions.
18. Known limitations and unhandled cases are documented.

Implementation, verification and Product Owner acceptance remain separate lifecycle states.

## 14. Risks and controls

| Risk | Control |
|---|---|
| Incorrectly treating business rows as structural artefacts | Explicit structure rules, source-row lineage and tests |
| Deleting legitimate repeated orders | Exact vs near-duplicate distinction and retained-counterpart evidence |
| Concealing data loss | Mutually exclusive disposition ledger and count reconciliation |
| Incorrectly imputing values | Preserve nulls; require explicit rule and approval for any imputation |
| Unreproducible outputs | Fixed seed, deterministic rules, versions and fingerprints |
| Ambiguous business meaning | Quarantine/flag for human review |
| Scope expansion | No second transformation engine, shared framework, GUI or infrastructure |

## 15. Implementation approval

The Product Owner's engineering activation directive of 27 November 2026 explicitly approves this completed Phase 1 implementation scope. The specialist architecture review is closed; its recommendations are adopted. The approved first increment is RASK-P1-I1: deterministic synthetic workbook generation, seeded manifest, intake/cleaning pipeline, traceable artefacts, reconciliation, XLSX/CSV outputs and automated tests. Claude performs one independent review of the handoff and proceeds under the same assignment if no genuine blocker exists. Non-blocking observations do not pause work. Implementation is IN PROGRESS once the assignment is issued; verification and Product Owner acceptance remain separate.
