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

## Phase 1 implementation decisions — approved 27 November 2026

| ID | Decision | Approved position | Approval / source |
|---|---|---|---|
| DEC-027 | Source schema | Fixed 11-field order-line schema and constraints in PHASE-1-SPECIFICATION.md | Product Owner implementation-scope approval, 27 Nov 2026 |
| DEC-028 | Synthetic data | 1,500 base records; one Orders worksheet; seed 20261127; deterministic generator and synthetic identifiers | Product Owner implementation-scope approval, 27 Nov 2026 |
| DEC-029 | Financial controls | ZAR only; Decimal; per-line ROUND_HALF_UP; canonical formula Quantity × UnitPrice × (1 − DiscountRate); no tax, shipping or FX | Product Owner implementation-scope approval, 27 Nov 2026 |
| DEC-030 | Seeded ground truth | manifests/seeded-issues.json with stable value, duplicate, ambiguity and structural cases | Product Owner implementation-scope approval, 27 Nov 2026 |
| DEC-031 | Runtime baseline | Python 3.11/3.12, pandas 2.2.3, openpyxl 3.1.5, pytest 8.3.4 | Product Owner implementation-scope approval, 27 Nov 2026 |
| DEC-032 | First engineering increment | RASK-P1-I1: generator, manifest, cleaner, artefact contracts, XLSX/CSV, reconciliation and tests within bounded handoff | Product Owner implementation-scope approval, 27 Nov 2026 |

## Open engineering choices (delegated within approved scope)

Routine module internals, CLI argument names, logging format and test organisation are delegated within the approved architecture. No outstanding Product Owner decision blocks RASK-P1-I1. Material changes to scope, stack, data integrity, security or major dependencies still require approval.

## Change control

Material changes to business requirements, scope, architecture, technology stack, security boundaries, data integrity rules, major dependencies or infrastructure require explicit Product Owner approval.

For each new material decision, record an identifier, date, context, alternatives where relevant, decision, rationale, consequences and approval evidence. Do not silently replace an approved decision. Superseded decisions remain traceable.
