# Phase 1 Specification — Spreadsheet Cleaning & Restructuring

**Specification status:** DRAFT — READY FOR PRODUCT OWNER FINAL SPECIFICATION APPROVAL  
**Implementation status:** NOT STARTED — NOT AUTHORISED  
**Phase:** 1  
**Specification owner:** ChatGPT — Primary AI  
**Decision authority:** Product Owner  
**Architecture review:** Claude, RASK-ARCH-REV-001  
**Product Owner review decision:** Recommendations approved as proposed

## 1. Purpose and outcome

Deliver a bounded, reproducible service demonstration that receives a deliberately imperfect small-business sales/order spreadsheet, profiles it, applies explicit and traceable cleaning rules, restructures the data, produces client-usable outputs and reconciles every source record candidate.

The demonstration must make its work explainable. It must not silently invent business values, erase exceptions or imply that a synthetic scenario represents a real client engagement.

This document incorporates the Product Owner-approved recommendations from Claude's read-only architecture review. It is a substantially refined task specification, but remains subject to the final approval gate in Section 15. Approval of the architecture review does not itself authorise code implementation.

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

### 3.2 Proposed fields

The exact schema is finalised in the implementation design, but should include fields sufficient for order-line identification, order/customer references, order date, product/category, quantity, unit price, discount where applicable, currency and line amount.

Use synthetic identifiers and fictional categories. Do not generate real personal data or use actual names, email addresses, telephone numbers, addresses or account identifiers.

### 3.3 Seeded issue manifest

A machine-readable or otherwise structured seeded-issue manifest must be defined and committed alongside the generator before cleaning logic is implemented. It must describe the intended issue class, affected source row/field or structural location, expected detection and expected treatment. This gives the tests a known ground truth.

Include:
- Value-level issues: whitespace/casing, inconsistent category labels, mixed date/number representations, missing values and invalid values.
- Duplicate cases: exact duplicate rows and near-duplicate candidates.
- Structural issues: at least two distinct spreadsheet artefacts, such as repeated header rows, title/blank rows, embedded subtotal/total rows, merged-cell effects or inconsistent header placement.
- At least one ambiguity case that must be flagged for human review rather than automatically corrected.

Do not seed or automatically repair issues whose business meaning cannot be justified.

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

Dependencies must remain minimal and justified. Exact supported versions and setup instructions are recorded in the implementation handoff.

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

Final paths are to be confirmed in the implementation task assignment. Use a service-specific layout, provisionally:

- `services/spreadsheet-cleaning/README.md`
- `services/spreadsheet-cleaning/src/`
- `services/spreadsheet-cleaning/tests/`
- `services/spreadsheet-cleaning/data/source/`
- `services/spreadsheet-cleaning/data/output/`
- `services/spreadsheet-cleaning/reports/`
- `services/spreadsheet-cleaning/manifests/`

Do not commit generated run outputs unnecessarily; define repository retention and ignore rules during implementation design. The public repository may contain the synthetic generator, manifest and a small illustrative fixture, but must not accumulate redundant generated files.

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

The implementation must define the control-total calculation and rounding/currency rules before build. Do not compare unlike currencies or silently aggregate across currencies.

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

## 15. Final Product Owner approval gate

The Product Owner has approved the recommendations from RASK-ARCH-REV-001 and the design direction recorded here. Before implementation, ChatGPT must present this completed specification, final field/control-total definitions and exact file-level task scope for explicit approval.

Until that final task approval:
- Phase 1 remains NOT STARTED.
- No implementation is authorised.
- No Claude code assignment is active.
- No code files are assigned to Claude.
