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
| DEC-004 | Toolkit | Excel/Power Query; SQL Server 2022/T-SQL; Python/pandas where justified; Power BI; Git/GitHub; justified local automation | Product Owner-approved foundation, 25 Nov 2026 |
| DEC-005 | Data safety | Synthetic or appropriately licensed public datasets for public demonstrations; no confidential, personal or client data in public repository | Product Owner-approved foundation, 25 Nov 2026 |
| DEC-006 | Commercial integrity | Distinguish demonstrations, reusable templates, actual engagements and commercially validated services; no invented customers, outcomes or revenue | Product Owner-approved foundation, 25 Nov 2026 |
| DEC-007 | Delivery and QA | Discover, assess, prepare, develop, verify and deliver; document intake, quality, exceptions, reconciliation and handover | Product Owner-approved foundation, 25 Nov 2026 |
| DEC-008 | Phase sequencing | All six service categories are approved but implemented progressively; Phase 1 is Spreadsheet Cleaning & Restructuring | Approved roadmap, 25 Nov 2026 |
| DEC-009 | Foundation acceptance | Foundation documentation accepted as baseline; Phase 0 accepted; Phase 1 and substantial implementation not started | Product Owner acceptance, 25 Nov 2026 |

## Governance decision

| ID | Decision | Approved position | Approval / source |
|---|---|---|---|
| DEC-010 | FNEOS collaboration and ownership | ChatGPT owns architecture, documentation and integration; Claude owns only explicitly assigned code files; user performs local assembly/execution and remains final authority | Product Owner-approved FNEOS reset, 27 Nov 2026 |
| DEC-011 | Three-stage workflow | Stage 1 ChatGPT architecture/documentation; Stage 2 Claude engineering/code; Stage 3 user + VS Code + ChatGPT assembly, alignment and integration | Product Owner-approved FNEOS reset, 27 Nov 2026 |
| DEC-012 | Zero-overlap | ChatGPT owns project documentation; Claude may modify only assigned code files; no simultaneous editing | Product Owner-approved FNEOS reset, 27 Nov 2026 |
| DEC-013 | Git/branch controls | Claude must not push, commit to main or independently modify repository; branch-based work requires explicit Product Owner authorisation | Product Owner-approved FNEOS reset, 27 Nov 2026 |
| DEC-014 | Return/alignment checkpoint | After Claude work or local assembly, ChatGPT inspects latest main and supplied changes/results before issuing another assignment | Product Owner-approved FNEOS reset, 27 Nov 2026 |
| DEC-015 | Historical cutoff | Preserve project state through 25 Nov 2026 as historical baseline; supersede conflicting 26 Nov workflow changes without rewriting history | Product Owner-approved FNEOS reset, 27 Nov 2026 |

## Pending decisions

| ID | Topic | Status |
|---|---|---|
| PENDING-001 | Phase 1 synthetic dataset and business scenario | Not yet selected; prepare recommendation and obtain Product Owner approval where needed |
| PENDING-002 | Phase 1 detailed cleaning rules where business meaning is ambiguous | Pending Phase 1 specification review |
| PENDING-003 | Phase 1 final implementation task and exact code-file assignment | Pending specification approval |

## Change control

Material changes to business requirements, scope, architecture, technology stack, security boundaries, data integrity rules, major dependencies or infrastructure require explicit Product Owner approval.

For each new material decision, record an identifier, date, context, alternatives where relevant, decision, rationale, consequences and approval evidence. Do not silently replace an approved decision. Superseded decisions remain traceable.
