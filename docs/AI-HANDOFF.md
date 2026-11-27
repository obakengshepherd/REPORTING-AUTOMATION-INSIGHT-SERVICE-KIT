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
Latest main inspected for RASK-P1-I1 handoff: `e639c255035d8963dc5072f13d0b3d3d615153e1`

## 3. Current project status

- **Phase 0 — Foundation and repository setup:** ACCEPTED, 25 November 2026.
- **Phase 1 — Spreadsheet Cleaning & Restructuring:** implementation IN PROGRESS; scope approved 27 November 2026.
- **Substantial implementation:** NOT YET RETURNED; RASK-P1-I1 is assigned.
- **Current activity:** Claude one-time handoff review followed by implementation under the same assignment.
- **Current Claude assignment:** RASK-P1-I1 — ACTIVE.

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

## 7. Phase 1 implementation approval

The Product Owner's 27 November 2026 engineering activation directive approves the completed Phase 1 implementation scope. The source schema, deterministic generator, seeded issue manifest, ZAR financial rules, reconciliation, dependency baseline, acceptance criteria and bounded file assignment are fixed. No further general architecture review or Product Owner decision is required for this increment.

## 8. Active engineering assignment — RASK-P1-I1

**Phase/increment:** Phase 1, Increment 1 — Spreadsheet Cleaning & Restructuring.  
**Latest verified main SHA at assignment preparation:** `e639c255035d8963dc5072f13d0b3d3d615153e1`.  
**Objective:** implement a reproducible synthetic spreadsheet-cleaning workflow with traceable source disposition, exceptions, reconciliation and XLSX/CSV outputs.

**Approved references:**
- `docs/PROJECT-FOUNDATION.md`
- `docs/PHASE-1-SPECIFICATION.md`
- `docs/DATA-INTAKE-STANDARDS.md`
- `docs/DATA-QUALITY-STANDARDS.md`
- `docs/QUALITY-ASSURANCE.md`
- `docs/DECISIONS.md`, DEC-016 through DEC-032

**Claude may CREATE only these files:**
1. `services/spreadsheet-cleaning/pyproject.toml`
2. `services/spreadsheet-cleaning/README.md`
3. `services/spreadsheet-cleaning/src/spreadsheet_cleaning/__init__.py`
4. `services/spreadsheet-cleaning/src/spreadsheet_cleaning/contracts.py`
5. `services/spreadsheet-cleaning/src/spreadsheet_cleaning/generate_source.py`
6. `services/spreadsheet-cleaning/src/spreadsheet_cleaning/cleaning.py`
7. `services/spreadsheet-cleaning/src/spreadsheet_cleaning/run.py`
8. `services/spreadsheet-cleaning/manifests/seeded-issues.json`
9. `services/spreadsheet-cleaning/tests/test_pipeline.py`

**Explicit exclusions:** all existing documentation and root files; all unlisted paths; SQL Server, Power Query, Power BI, cloud, APIs, GUI, orchestration, shared libraries/frameworks, real/client data, deployment packaging, branches and pull requests. Claude must not push, commit or modify GitHub.

**Dependencies/environment:** Python 3.11 or 3.12; pandas 2.2.3; openpyxl 3.1.5; pytest 8.3.4. Use a local virtual environment. No additional dependency without demonstrated need and escalation.

**Input/output and expected behaviour:**
- Generate 1,500 synthetic base order-line records with fixed seed `20261127`, in one worksheet named `Orders`.
- Use the 11-field schema and rules in PHASE-1-SPECIFICATION.md; candidate key `OrderLineID`.
- Seed value-level issues, an exact duplicate, near-duplicate, ambiguous date, merged title/blank opening rows, repeated header and subtotal artefacts exactly as specified in the manifest.
- Preserve the original input; calculate and record SHA-256; retain source file/sheet/physical row lineage.
- Separate INFO/WARNING/ERROR severity from one mutually exclusive disposition per source candidate.
- Use Decimal for ZAR amounts and per-line ROUND_HALF_UP to two decimals; formula: Quantity × UnitPrice × (1 − DiscountRate). No tax, shipping or FX.
- Produce cleaned XLSX and CSV, data dictionary, rule register, exception register, one-row-per-source-candidate reconciliation ledger and summary, run metadata/fingerprints and a human-readable quality summary.
- Do not commit generated run workbooks/reports.

**Acceptance criteria:**
1. Generator and manifest are deterministic for the fixed seed.
2. Every manifest case is detected and receives its expected treatment.
3. Every source candidate has exactly one disposition; structural rows are recorded as EXCLUDED_NON_RECORD.
4. Exact duplicate removal identifies its retained counterpart; near-duplicates are not merged.
5. Missing values remain null where specified; no silent imputation or zero substitution.
6. Ambiguous dates are quarantined, not guessed.
7. Source SHA-256 and row lineage appear in run/exception/reconciliation artefacts.
8. Disposition counts balance exactly; computable quantity and monetary controls reconcile by disposition.
9. Repeated runs produce equivalent data outputs; volatile run timestamps/IDs may differ only in run metadata.
10. XLSX and CSV business data agree.
11. pytest covers manifest cases, contracts, deterministic generation, dispositions, lineage, outputs and reconciliation.
12. README commands reproduce generation and cleaning from a clean environment.

**Claude review and implementation sequence:** review this handoff once. Classify findings as BLOCKING, NON-BLOCKING or PRODUCT OWNER DECISION. If no genuine blocker exists, proceed immediately with implementation under this same assignment. Non-blocking observations must be documented without stopping work. Stop only affected work for a genuine blocker and submit one consolidated report containing issue, impact and recommended resolution.

**Complete-file return format:** return every assigned file in full, each under its exact repository-relative path. No diffs, partial snippets, placeholders or omitted files. Include design/implementation explanation, dependencies, VS Code assembly steps, exact install/generation/clean/test commands, expected outcomes, actual outcomes only if executed (otherwise NOT RUN), limitations and known issues.

**VS Code assembly and local verification:** create/activate a venv; from `services/spreadsheet-cleaning`, install with `python -m pip install -e ".[dev]"`; use the documented CLI to generate the source workbook and run the cleaner into a separate output directory; run `pytest`. The README, CLI and tests must use consistent commands. User supplies actual terminal output/results for the return/alignment checkpoint.

**Stop conditions:** stop only if implementation cannot meet approved requirements without a material change to scope, architecture, security/data integrity or dependencies. Routine implementation choices are delegated.

## 9. Current ownership and assignment register

- **Product Owner:** final authority, local assembly, execution and acceptance.
- **ChatGPT:** architecture, all documentation, assignment, return/alignment review and main integration.
- **Claude:** RASK-P1-I1 only; owns only the nine code files listed above until complete return.
- **Active Claude assignment:** RASK-P1-I1.
- **Active branches or PRs authorised:** NONE.

## 10. Next authorised action

Claude performs the one-time handoff review and proceeds with RASK-P1-I1 unless a genuine blocker exists. Product Owner assembles and tests returned files in VS Code. ChatGPT then performs one return/alignment checkpoint before integration.

**Implementation is IN PROGRESS by assignment. It is not yet IMPLEMENTED, VERIFIED or ACCEPTED.**
