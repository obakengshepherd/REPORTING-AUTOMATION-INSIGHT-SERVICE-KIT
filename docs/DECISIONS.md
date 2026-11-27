# Project Decision Register

**Authority:** Product Owner  
**Maintainer:** ChatGPT — Primary AI  
**Status:** Active register  
**Historical baseline:** 25 November 2026

This register records material project decisions and their approval status. Recommendations and pending proposals must not be represented as approved decisions.

## Approved project foundation decisions

| ID | Decision | Approved position | Approval / source |
|---|---|---|---|
| DEC-001 | Business purpose | Reusable demonstration of practical reporting and data automation services; no implied existing clients or commercial validation | Product Owner-approved foundation, 25 Nov 2026 |
| DEC-002 | Architecture | Modular, workflow-oriented, local-first service toolkit | Product Owner-approved foundation, 25 Nov 2026 |
| DEC-003 | Service scope | Six categories: spreadsheet cleaning, data quality, SQL reporting, recurring automation, dashboards and small-scale analytics | Product Owner-approved foundation, 25 Nov 2026 |
| DEC-004 | Project toolkit | Excel/Power Query; SQL Server 2022/T-SQL; Python/pandas where justified; Power BI; Git/GitHub; justified local automation | Product Owner-approved foundation, 25 Nov 2026 |
| DEC-005 | Data safety | Synthetic or appropriately licensed public datasets for public demonstrations; no confidential, personal or client data in public repository | Product Owner-approved foundation, 25 Nov 2026 |
| DEC-006 | Commercial integrity | Distinguish demonstrations, reusable templates, actual engagements and commercially validated services; no invented customers, outcomes or revenue | Product Owner-approved foundation, 25 Nov 2026 |
| DEC-007 | Delivery and QA | Discover, assess, prepare, develop, verify and deliver; document intake, quality, exceptions, reconciliation and handover | Product Owner-approved foundation, 25 Nov 2026 |
| DEC-008 | Phase sequencing | All six service categories are approved but implemented progressively; Phase 1 is Spreadsheet Cleaning & Restructuring | Approved roadmap, 25 Nov 2026 |
| DEC-009 | Foundation acceptance | Foundation documentation accepted as baseline; Phase 0 accepted; Phase 1 and substantial implementation not started | Product Owner acceptance, 25 Nov 2026 |

## FNEOS governance decisions

| ID | Decision | Approved position | Approval / source |
|---|---|---|---|
| DEC-010 | FNEOS collaboration and ownership | ChatGPT owns architecture, documentation and integration; Claude owns only explicitly assigned code files; user performs local assembly/execution and remains final authority | Product Owner-approved FNEOS reset, 27 Nov 2026 |
| DEC-011 | Three-stage workflow | Stage 1 ChatGPT architecture/documentation; Stage 2 Claude engineering/code; Stage 3 user + VS Code + ChatGPT assembly, alignment and integration | Product Owner-approved FNEOS reset, 27 Nov 2026 |
| DEC-012 | Zero-overlap | ChatGPT owns project documentation; Claude may modify only assigned code files; no simultaneous editing | Product Owner-approved FNEOS reset, 27 Nov 2026 |
| DEC-013 | Git/branch controls | Claude must not push, commit to main or independently modify repository; branch-based work requires explicit Product Owner authorisation | Product Owner-approved FNEOS reset, 27 Nov 2026 |
| DEC-014 | Return/alignment checkpoint | After Claude work or local assembly, ChatGPT inspects latest main and supplied changes/results before issuing another assignment | Product Owner-approved FNEOS reset, 27 Nov 2026 |
| DEC-015 | Historical cutoff | Preserve project state through 25 Nov 2026 as historical baseline; supersede conflicting 26 Nov workflow changes without rewriting history | Product Owner-approved FNEOS reset, 27 Nov 2026 |

## Phase 1 decisions — approved direction

| ID | Decision | Approved position | Approval / source |
|---|---|---|---|
| DEC-016 | Phase 1 architecture review | Adopt Claude RASK-ARCH-REV-001 recommendations as approved design direction, refined by ChatGPT's assessment | Product Owner approval, 27 Nov 2026 |
| DEC-017 | Phase 1 technology | Python/pandas for deterministic processing; pytest for automated tests; XLSX human-facing output and CSV machine-readable output; Power Query deferred for this phase | Product Owner approval, 27 Nov 2026 |
| DEC-018 | Dataset scenario and grain | Synthetic small-business sales/orders dataset, approximately 1,000–10,000 rows; one order line per business record; `OrderLineID` candidate key; fixed-seed deterministic generator | Product Owner approval, 27 Nov 2026 |
| DEC-019 | Seeded issue coverage | Value-level issues, exact and near-duplicate cases, at least two structural issue types and one ambiguity case; define seeded-issue manifest before cleaning implementation | Product Owner approval, 27 Nov 2026 |
| DEC-020 | Duplicate handling | Exact duplicates may be removed only under explicit business-field equality rules with retained-counterpart traceability; near-duplicates are flagged for review, not automatically merged | Product Owner approval, 27 Nov 2026 |
| DEC-021 | Missing values | Preserve nulls; do not impute or replace missing numeric values with zero by default; quarantine/reject only under explicit critical rules | Product Owner approval, 27 Nov 2026 |
| DEC-022 | Quality taxonomy | Separate INFO/WARNING/ERROR issue severity from mutually exclusive final record disposition | Product Owner approval, 27 Nov 2026 |
| DEC-023 | Final dispositions | RETAINED_AS_IS, CORRECTED, QUARANTINED, REJECTED, EXCLUDED_NON_RECORD, REMOVED_AS_DUPLICATE | Product Owner approval, 27 Nov 2026 |
| DEC-024 | Artefact contracts | Use explicit data dictionary, rule register, exception register, reconciliation ledger/summary, run record and seeded-issue manifest; no generic shared framework | Product Owner approval, 27 Nov 2026 |
| DEC-025 | Phase 1 repository approach | Use a service-specific directory; no speculative shared library; final exact paths confirmed in implementation task assignment | Product Owner approval, 27 Nov 2026 |
| DEC-026 | Phase 1 reconciliation | Every source candidate receives exactly one final disposition; counts and relevant control totals must reconcile with no unexplained differences | Product Owner approval, 27 Nov 2026 |

## Pending decisions and approvals

| ID | Topic | Status |
|---|---|---|
| PENDING-001 | Final Phase 1 field schema, data dictionary and control-total formulas | To be completed in the final specification/task design |
| PENDING-002 | Exact seeded issue rows, structural artefacts and expected outcomes | To be defined in the deterministic seeded-issue manifest before implementation |
| PENDING-003 | Exact repository paths, dependency versions and file-level code assignment | To be finalised in the implementation assignment |
| PENDING-004 | Final approval of the completed Phase 1 specification for implementation | Not yet granted |

## Change control

Material changes to business requirements, scope, architecture, technology stack, security boundaries, data integrity rules, major dependencies or infrastructure require explicit Product Owner approval.

For each new material decision, record an identifier, date, context, alternatives where relevant, decision, rationale, consequences and approval evidence. Do not silently replace an approved decision. Superseded decisions remain traceable.
