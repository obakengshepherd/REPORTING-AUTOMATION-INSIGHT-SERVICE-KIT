# Phase 1 Specification — Spreadsheet Cleaning & Restructuring

**Status:** DRAFT — NOT APPROVED FOR IMPLEMENTATION  
**Phase:** 1  
**Project baseline:** Accepted foundation dated 25 November 2026  
**Document owner:** ChatGPT — Primary AI  
**Approval authority:** Product Owner

## 1. Purpose

Define a bounded first service demonstration that shows a repeatable, explainable process for inspecting, cleaning, restructuring and validating a business spreadsheet.

This specification is a planning document only. It does not authorise implementation, select a final dataset or approve unresolved business rules.

## 2. Business scenario — provisional

A small business operations team receives a recurring spreadsheet export containing inconsistently formatted operational records. Before the information can be used for routine reporting, the file requires profiling, standardisation, duplicate review, exception handling and reconciliation.

The demonstration will show how to turn an imperfect source workbook into a clean, structured output with traceable transformation decisions.

The scenario is illustrative and must not imply a real client or engagement.

## 3. Scope

### Proposed in-scope capabilities
- Inspect workbook structure, sheets, headers, data types and row grain.
- Preserve the original input and work on a controlled copy.
- Profile missing, duplicate, invalid and inconsistent values.
- Apply approved text, date, numeric and category standardisation.
- Restructure the data into a consistent tabular output.
- Separate or clearly identify exceptions requiring review.
- Record transformation rules and assumptions.
- Reconcile source and output record counts and relevant totals.
- Provide a repeatable execution and handover guide.

### Proposed exclusions
- Live client data or confidential personal information.
- Production integrations or automated ingestion from external systems.
- Cloud infrastructure, APIs, orchestration platforms or message brokers.
- Enterprise-scale data engineering or a general-purpose cleaning platform.
- Automated business decisions where human review is required.
- Unsupported claims of business impact or commercial validation.

## 4. Dataset requirements — pending Product Owner selection

The dataset should be synthetic or appropriately licensed for public redistribution and should:
- Represent a plausible small-business operational process.
- Have a clearly defined row grain and candidate key.
- Include enough records to demonstrate meaningful profiling.
- Contain intentional but realistic data-quality issues.
- Include fields with clear types and business meanings.
- Permit at least one meaningful reconciliation check.
- Avoid real personal, confidential or regulated data.

Potential issue categories include inconsistent labels/casing, whitespace, mixed date formats, numeric formatting, missing values, candidate duplicates, invalid categories and malformed records. The final dataset and issue profile remain pending.

## 5. Proposed workflow

1. **Intake:** Record dataset provenance, permission, format, reporting period, grain and sensitivity.
2. **Profile:** Inspect sheets, columns, data types, counts, nulls, candidate duplicates, ranges and category distributions.
3. **Specify:** Agree cleaning rules and classify issues before modifying data.
4. **Prepare:** Preserve raw source; apply controlled transformations to a working copy.
5. **Handle exceptions:** Retain, quarantine or flag records according to approved rules; do not silently delete or invent values.
6. **Validate:** Re-run quality checks and reconcile input/output counts and selected totals.
7. **Deliver:** Package clean output, exception report, transformation log and reproducibility instructions.

## 6. Proposed tool approach

Excel and Power Query are the leading initial candidates for a spreadsheet-centred workflow. SQL Server 2022/T-SQL or Python/pandas may be used only if a specific requirement justifies them and the additional tool does not complicate the demonstration unnecessarily.

Final tool allocation is pending task design and Product Owner confirmation where it changes the approved baseline.

## 7. Proposed deliverables

Exact paths and file formats are to be defined after the task is approved. Candidate deliverables:
- Synthetic source workbook or dataset with provenance/licence note.
- Cleaned and restructured output.
- Exception/issue register.
- Data profile and quality summary.
- Transformation/rules log.
- Reconciliation and QA evidence.
- Reproduction and handover instructions.

## 8. Proposed acceptance criteria

A completed Phase 1 implementation should demonstrate that:
1. Dataset source and usage permission are documented.
2. Original input is preserved.
3. Dataset grain, schema and cleaning rules are explicit.
4. Transformations are repeatable and do not silently invent or discard business values.
5. Exceptions remain traceable.
6. Input/output counts reconcile with explained differences.
7. Selected business totals or control values reconcile.
8. Quality checks have recorded expected and actual outcomes.
9. Another technically competent person can reproduce the workflow from the repository instructions.
10. Known limitations and unhandled cases are disclosed.

Implementation, verification and Product Owner acceptance remain separate states.

## 9. Open decisions before implementation

- Select and approve the synthetic/public dataset and business scenario.
- Confirm dataset grain, candidate key and control totals.
- Agree issue types and which cases are intentionally seeded.
- Define handling for missing values, duplicates and invalid records.
- Confirm output structure and exception-report format.
- Confirm the minimum justified toolset.
- Finalise exact deliverable paths, tests and acceptance criteria.

## 10. Approval gate

This document is DRAFT and NOT APPROVED FOR IMPLEMENTATION. ChatGPT must review and refine it, present unresolved dataset and business-rule decisions to the Product Owner, and obtain explicit approval of the final task specification before preparing an implementation assignment for Claude.
