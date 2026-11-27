# FNEOS Project Handoff & Coordination

**Project:** Reporting Automation & Insight Service Kit  
**Primary AI:** ChatGPT — architecture, documentation and integration owner  
**Specialist AI:** Claude — assigned engineering and code owner  
**Authority:** Product Owner  
**Historical cutoff:** 25 November 2026  
**Reset recorded:** 27 November 2026

## 1. Historical baseline

The authoritative accepted project baseline is commit:

`c9f1ae085f48521f954af7173918be523282108e`

This baseline records:
- Phase 0 foundation accepted.
- Phase 1 — Spreadsheet Cleaning & Restructuring — NOT STARTED.
- Substantial service implementation NOT STARTED.
- Modular, workflow-oriented, local-first toolkit.
- Six approved service categories.
- Excel/Power Query, SQL Server 2022/T-SQL, Python/pandas where justified, Power BI and Git/GitHub.
- Data intake, data quality, QA, commercial integrity and synthetic/public-safe data requirements.

The reset preserves valid requirements and historical commits. It supersedes conflicting collaboration arrangements and handoffs introduced on 26 November 2026. No history rewrite or force-push is authorised.

## 2. Repository state at reset

Repository: https://github.com/obakengshepherd/REPORTING-AUTOMATION-INSIGHT-SERVICE-KIT  
Default branch: `main`  
Latest inspected main before corrective commits: `fbf5d0807ea3a89a785deb78a5e1e856b34af7cd`

The inspected 26 November history included:
- `2d732d7` — README status alignment; preserve its valid status correction.
- `3f4ab9f` — AI collaboration agreement; superseded by FNEOS.
- `76feaee` — prior handoff and Phase 1 review assignment; superseded.
- `dd4b127` — README links to AI documents; retain and align links.
- `fbf5d08` — prior handoff baseline correction; superseded by this handoff.

The accepted foundation and standards documents remain authoritative and are not being reopened.

## 3. Current project status

**Phase 0 — Foundation and repository setup:** ACCEPTED by Product Owner on 25 November 2026.  
**Phase 1 — Spreadsheet Cleaning & Restructuring:** NOT STARTED.  
**Substantial implementation:** NOT STARTED.  
**Current activity:** FNEOS governance reset and documentation synchronisation.

The six approved services remain:
1. Spreadsheet Cleaning & Restructuring.
2. Data Quality Assessment.
3. SQL Reporting & Data Extraction.
4. Recurring Reporting Automation.
5. Dashboard Development.
6. Small-scale Business Analytics.

All six are approved for progressive demonstration; they are not to be implemented simultaneously.

## 4. FNEOS workflow and ownership

### Stage 1 — ChatGPT
Owns architecture, requirements, technical specifications, README and all documentation, decision register, task specifications, Claude assignment preparation, main governance and final integration.

### Stage 2 — Claude
Reviews architecture by default and implements only explicitly assigned code files. Returns complete files in chat with exact repository-relative paths, engineering explanations, tests and execution instructions.

Claude has no default permission to push, commit, merge, create branches or modify documentation. Branch-based work requires explicit Product Owner authorisation.

### Stage 3 — User + VS Code + ChatGPT
User assembles returned code locally and runs tests. ChatGPT performs the return/alignment checkpoint, reviews against the approved assignment, resolves issues, integrates approved changes into main and updates documentation.

**Zero-overlap:** ChatGPT owns documentation. Claude owns only named code files during an active implementation assignment. No simultaneous file editing.

## 5. Return/alignment checkpoint

Whenever the user returns after Claude work or local assembly, ChatGPT first inspects latest main, relevant repository changes and supplied files/results; compares implementation to the approved assignment; reviews actual test evidence; identifies omissions and blockers; and confirms alignment or explains remaining issues.

ChatGPT must not claim visibility into uncommitted local changes or test results that were not supplied or observed. No next implementation assignment is issued before this checkpoint.

## 6. Documentation authority

- `README.md`: public project overview and concise current status.
- `docs/PROJECT-FOUNDATION.md`: accepted business purpose, requirements, scope and architecture.
- `docs/PROJECT-ROADMAP.md`: phases, sequencing and exit criteria.
- `docs/DECISIONS.md`: material approved decisions and change history.
- `docs/AI-COLLABORATION.md`: permanent FNEOS role, ownership and workflow rules.
- `docs/AI-HANDOFF.md`: this living coordination record.
- `docs/PHASE-1-SPECIFICATION.md`: bounded Phase 1 requirements and acceptance criteria.

ChatGPT maintains these documents. Claude may read them but may not modify them without explicit Product Owner-approved ownership transfer.

## 7. Phase 1 boundary

The next engineering direction is Spreadsheet Cleaning & Restructuring using a bounded synthetic-data demonstration. Before implementation:
1. Complete and review the Phase 1 specification.
2. Establish dataset characteristics, business scenario, grain and selection criteria.
3. Define cleaning rules, exception treatment and reconciliation expectations.
4. Confirm appropriate tools and exact deliverables.
5. Obtain Product Owner approval of unresolved business choices and the task specification.
6. Issue a separate, explicitly scoped Claude implementation assignment.

No dataset has been selected or approved by this handoff. No code files are currently assigned to Claude.

## 8. Superseded records and assignments

The 26 November AI collaboration model, branch/pull-request workflow and `PH1-REVIEW-001` handoff assignment are superseded and inactive. They remain in Git history for traceability; they are not current instructions.

## 9. Current ownership and assignment register

- **Product Owner:** final decisions, local assembly, execution and acceptance.
- **ChatGPT:** all documentation, architecture, assignment preparation, return/alignment review and main integration.
- **Claude:** no active assignment and no file ownership at reset.
- **Current Claude assignment:** NONE.
- **Active branches or PRs authorised by this handoff:** NONE.

## 10. Next authorised action

Complete and review the bounded Phase 1 specification under ChatGPT documentation ownership, then present any unresolved dataset/business decisions and the specification for Product Owner approval.

**Implementation remains NOT STARTED. No Claude code assignment is active.**
