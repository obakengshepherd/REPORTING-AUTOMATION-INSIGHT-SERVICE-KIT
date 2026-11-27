# FNEOS Project Handoff & Coordination

**Project:** Reporting Automation & Insight Service Kit  
**Primary AI:** ChatGPT — architecture, documentation and integration owner  
**Specialist AI:** Claude — assigned engineering and code owner  
**Authority:** Product Owner  
**Historical cutoff:** 25 November 2026  
**Last governance reset:** 27 November 2026

## 1. Historical baseline

The authoritative accepted project baseline is commit:

`c9f1ae085f48521f954af7173918be523282108e`

This baseline records Phase 0 foundation accepted, Phase 1 NOT STARTED and substantial service implementation NOT STARTED. It preserves the modular, workflow-oriented, local-first toolkit, six approved service categories and synthetic/public-safe data requirements.

The reset preserves valid requirements and historical commits. It supersedes conflicting collaboration arrangements and handoffs introduced on 26 November 2026. No history rewrite or force-push is authorised.

## 2. Current repository state

Repository: https://github.com/obakengshepherd/REPORTING-AUTOMATION-INSIGHT-SERVICE-KIT  
Default branch: `main`  
Latest main inspected for this specification update: `c2ff7ea279c2e268d9f007b6e0b0bc8464aa4063`

## 3. Current project status

- **Phase 0 — Foundation and repository setup:** ACCEPTED, 25 November 2026.
- **Phase 1 — Spreadsheet Cleaning & Restructuring:** specification refinement IN PROGRESS; implementation NOT STARTED.
- **Substantial implementation:** NOT STARTED.
- **Current activity:** incorporating Product Owner-approved architecture review recommendations into the Phase 1 specification and standards.
- **Current Claude assignment:** NONE.

The six approved service categories remain progressively sequenced; no simultaneous implementation is authorised.

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

No next implementation assignment is issued before this checkpoint.

## 6. Phase 1 review and decisions

Claude's read-only architecture review `RASK-ARCH-REV-001` was returned against main commit `c2ff7ea279c2e268d9f007b6e0b0bc8464aa4063`. The Product Owner approved the recommendations as proposed.

The approved Phase 1 direction is recorded in `docs/DECISIONS.md` and `docs/PHASE-1-SPECIFICATION.md`, including:
- Python/pandas and pytest; XLSX and CSV outputs; Power Query deferred for this phase.
- Synthetic sales/orders dataset, 1,000–10,000 target rows, one order line per row and `OrderLineID` candidate key.
- Fixed-seed deterministic generator and seeded-issue manifest.
- Value-level and structural issue coverage, exact and near-duplicate policies and human-review ambiguity case.
- Severity distinct from mutually exclusive final record disposition.
- Source-row lineage, artefact contracts, SHA-256 run fingerprint and count/control-total reconciliation.
- Service-specific directory; no generic shared framework or speculative shared library.

## 7. Remaining Phase 1 specification work

Before implementation approval, ChatGPT must finalise:
1. Exact dataset field schema and data dictionary.
2. Currency, rounding and control-total formulas.
3. Seeded-issue manifest structure and expected test outcomes.
4. Exact repository paths and bounded code-file assignment.
5. Test matrix and final acceptance evidence.

The revised specification remains a draft until the Product Owner explicitly approves it for implementation.

## 8. Current ownership and assignment register

- **Product Owner:** final decisions, local assembly, execution and acceptance.
- **ChatGPT:** all documentation, architecture, assignment preparation, return/alignment review and main integration.
- **Claude:** no active assignment and no file ownership.
- **Current Claude assignment:** NONE.
- **Active branches or PRs authorised by this handoff:** NONE.

## 9. Next authorised action

Complete the remaining Phase 1 specification details and present the complete bounded task for explicit Product Owner implementation approval.

**Implementation remains NOT STARTED. No Claude code assignment is active.**
