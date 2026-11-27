# Project Roadmap

**Foundation approved:** 25 November 2026  
**Governance standard:** FNEOS v1.0 — adopted 27 November 2026  
**Current status:** Phase 0 foundation accepted. Phase 1 implementation has not started.

## FNEOS delivery gates

All phases follow the engineering lifecycle:

**DISCOVER → DESIGN → BUILD → VERIFY → REVIEW → RECORD**

The project uses the mandatory three-stage collaboration workflow documented in `docs/AI-COLLABORATION.md`:
1. **ChatGPT — Architecture & Documentation:** requirements, specifications, architecture, acceptance criteria, documentation and bounded engineering assignments.
2. **Claude — Engineering & Code:** architecture review and implementation of explicitly assigned code files only; return complete files in chat with paths, rationale and test instructions.
3. **User + VS Code + ChatGPT — Assembly & Integration:** user assembles and runs code locally; ChatGPT completes the return/alignment checkpoint before integration and documentation updates.

ChatGPT owns all project documentation. Claude owns only explicitly assigned code files during an active task. Claude may not push, commit to main, merge or modify documentation. Branch-based work requires explicit Product Owner authorisation. No simultaneous editing is permitted.

A return/alignment checkpoint is mandatory after each Claude/local assembly cycle and before the next implementation assignment. It inspects latest main, supplied changes, assignment compliance and actual test evidence.

**Status discipline:** NOT STARTED → IN PROGRESS → IMPLEMENTED → VERIFIED → ACCEPTED, with BLOCKED used when a dependency prevents progress. Implementation, verification and Product Owner acceptance are distinct states.

Material changes to approved requirements, scope, architecture, stack, security, data integrity or major dependencies require Product Owner approval and a record in `docs/DECISIONS.md`.

## Phase 0 — Foundation and repository setup

- Record approved purpose, scope, architecture and toolkit.
- Establish service, intake, quality and QA standards.
- Establish repository conventions and initial backlog.
- Inspect and verify the initial repository state.

**Exit:** Product Owner acceptance recorded on 25 November 2026. Foundation documentation exists in the authoritative repository and repository setup has been inspected.

**Status:** ACCEPTED.

## Phase 1 — Spreadsheet Cleaning & Restructuring

**Status:** NOT STARTED.  
**Specification:** `docs/PHASE-1-SPECIFICATION.md` — DRAFT, NOT APPROVED FOR IMPLEMENTATION.

Proposed work:
- Select and approve a synthetic or appropriately licensed dataset.
- Confirm scenario, row grain, candidate key and control totals.
- Agree cleaning, exception and reconciliation rules.
- Profile and document source structure.
- Implement controlled cleaning and restructuring only after task approval.
- Produce a reusable output, issue/exception evidence and handover guide.

**Pre-build gate:** Product Owner approves the final bounded Phase 1 specification, dataset and unresolved business rules. ChatGPT then issues a separate explicit Claude code assignment.

**Exit:** Reproducible workflow with documented transformations, traceable exceptions and verified results. Product Owner acceptance is recorded separately.

## Phase 2 — Data Quality Assessment

- Define quality dimensions and business rules.
- Implement profiling and validation checks.
- Produce issue register and quality report.

**Exit:** Validation outcomes and exception handling are evidenced.

## Phase 3 — SQL Reporting & Data Extraction

- Define a bounded relational reporting scenario.
- Create schema and synthetic data scripts.
- Implement reusable extraction and aggregation queries.
- Reconcile key outputs.

**Exit:** Queries and reported figures are verified and documented.

## Phase 4 — Recurring Reporting Automation

- Define a recurring reporting requirement.
- Build a repeatable workflow and output template.
- Document configuration, execution and failure handling.

**Exit:** Repeatable report generation is demonstrated and checked.

## Phase 5 — Dashboard Development

- Define audience, questions and KPI dictionary.
- Prepare a suitable model and measures.
- Build and verify a Power BI demonstration.

**Exit:** Dashboard behaviour, measures and limitations are documented.

## Phase 6 — Small-scale Business Analytics

- Frame a bounded business question.
- Assess data suitability and analytical method.
- Produce evidence-based findings and recommendations.

**Exit:** Analysis is reproducible, caveated and understandable.

## Phase 7 — Service packaging and review

- Consolidate reusable service briefs, templates and handover guidance.
- Review consistency across all six service demonstrations.
- Record gaps and future improvements.

**Exit:** The toolkit can be understood and reproduced from repository documentation.

## Sequencing

All six service categories are approved, but implementation is progressive. Phase order may be adjusted only where dependencies and learning value justify it; material scope or architecture changes require Product Owner approval.
