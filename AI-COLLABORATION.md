# AI Collaboration Agreement

**Version:** 1.0  
**Authority:** Product Owner  
**Applies to:** All project work in this repository  
**Status:** Active

## 1. Authority and source of truth

The Product Owner is the final decision-maker for project scope, business requirements, architecture, technology stack, security boundaries, data integrity rules, major dependencies and project acceptance.

The GitHub repository is the authoritative project record. AI conversations are coordination context, not a substitute for repository documentation. Before acting, collaborators inspect the latest `main`, README, this agreement, `docs/AI-HANDOFF.md` and all task-relevant project documents, decision records, roadmaps and acceptance criteria.

If a conversation conflicts with the repository, stop and investigate. Do not silently overwrite the repository's more recent decision.

## 2. ChatGPT — Primary AI and maintainer

ChatGPT is responsible for:
- Project continuity, coordination and task decomposition.
- Routine approved documentation and implementation changes on `main`.
- Preparing bounded Claude assignments and recording file ownership.
- Reviewing Claude branches and pull requests.
- Requesting corrections, approving or rejecting contributions.
- Integrating approved contributions into `main`.
- Verifying the integrated result and recording actual evidence.
- Maintaining `docs/AI-HANDOFF.md` at meaningful project transitions.
- Preventing duplicate, conflicting or simultaneous edits.

ChatGPT may implement work directly or assign it to Claude. The engineer is selected according to task suitability.

## 3. Claude — Specialist engineering contributor

Claude is the specialist contributor. Its default role is review and recommendation. Review does not authorise file changes.

Assignments must be explicitly classified:
- **REVIEW ONLY**
- **REVIEW AND RECOMMEND**
- **IMPLEMENTATION ASSIGNMENT**
- **DOCUMENTATION ASSIGNMENT**
- **DEBUGGING / REFACTORING ASSIGNMENT**

When explicitly authorised, Claude may design, implement, test, debug, refactor and document assigned work within the accepted project baseline. Claude must not expand the assignment or make material Product Owner decisions.

## 4. Main branch ownership

ChatGPT is the primary maintainer of `main` and may commit routine, approved changes directly to it.

Claude must never independently commit or push to `main`, and must never merge its own contribution. Claude implementation and documentation work must be performed on a dedicated branch and submitted through a pull request targeting `main`.

A review-only assignment does not require a branch because it does not modify repository files.

## 5. Claude branch and pull-request procedure

For every Claude assignment that modifies files:

1. Inspect the latest appropriate `main` state and relevant documentation.
2. Create a dedicated branch from the latest appropriate main commit, named `claude/<work-item-slug>`.
3. Record task ID, assigned AI, branch, base commit, assigned and excluded files, file ownership, deliverables and verification requirements in `docs/AI-HANDOFF.md`.
4. Modify only assigned files.
5. Run relevant tests and checks; report exact commands and actual outcomes.
6. Commit changes only to the dedicated branch.
7. Open a pull request targeting `main`.
8. Provide an engineering handoff with changed files, decisions, evidence, limitations and outstanding questions.

If Claude cannot create a branch or pull request, it must report the limitation and provide its branch and commit details. It must not bypass the process.

## 6. File ownership and no simultaneous editing

Only one AI may own and modify a particular file at a time.

Before an assignment, record:
- Task identifier and classification.
- Assigned AI.
- Branch and base commit, where applicable.
- Files assigned and files excluded.
- Current file owner.
- Expected deliverables and verification requirements.

A review-only assignment owns no files. If Claude owns a file on its branch, ChatGPT must not edit that file until it is handed back or the assignment is cancelled. If ChatGPT is editing a file on `main`, Claude must not independently edit it.

## 7. Branch freshness and conflict resolution

Claude must confirm its branch is based on an appropriate current main commit. If `main` changes during the task, do not blindly overwrite, force-push or discard work. Report the divergence and reconcile it through explicit review. Update the branch safely before integration and re-run affected checks.

## 8. ChatGPT review and integration

ChatGPT reviews the actual branch and pull request for:
- Requirements and assignment compliance.
- Architecture and domain correctness.
- Data integrity, privacy and security.
- Code quality, maintainability and compatibility.
- Documentation accuracy.
- Test coverage and actual test evidence.
- Unassigned or unintended file changes.
- Compatibility with current `main`.

ChatGPT may request changes, approve or reject. Only approved contributions may be integrated into `main`. A commit, passing workflow or open pull request is not automatically an accepted deliverable. ChatGPT verifies the integrated result and records evidence. Product Owner acceptance remains separate.

## 9. Pull-request quality requirements

Every Claude implementation or documentation PR must include:
- Objective and task reference.
- Summary of changes.
- Files changed.
- Important technical decisions.
- Tests/checks executed and actual results.
- Known limitations and outstanding questions.
- Confirmation that no unassigned files were modified.

## 10. Decision and approval boundaries

Product Owner approval is required before materially changing:
- Business requirements or scope.
- Architecture or project topology.
- Technology stack.
- Security boundaries.
- Data integrity, governance or handling rules.
- Major dependencies or infrastructure.
- Business definitions and KPI rules.
- Project acceptance.

Claude may identify and recommend changes. ChatGPT may explain trade-offs and prepare proposals. Neither AI may represent a recommendation as an approved Product Owner decision.

Routine implementation decisions may be made by the assigned engineer within the accepted baseline.

## 11. Documentation and handoff

Maintain this agreement as the permanent collaboration standard. Maintain `docs/AI-HANDOFF.md` as the living coordination record for current status, assignments, ownership, review outcomes, decisions, next actions and verification evidence.

ChatGPT normally maintains the handoff. Update it at assignment starts and completions, reviews, integrations, material decisions and project transitions. Do not create duplicate AI instruction documents without a demonstrated need.

## 12. Required workflow

**DISCOVER → DESIGN → ASSIGN → BUILD → VERIFY → REVIEW → INTEGRATE → RECORD**

Scale the workflow to task complexity. Prefer small, reviewable increments. Preserve accepted decisions and verified functionality. Do not introduce unnecessary architecture, dependencies or documentation.
