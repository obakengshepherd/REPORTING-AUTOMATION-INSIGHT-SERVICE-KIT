# FNEOS AI Collaboration Standard

**Version:** 2.0  
**Authority:** Product Owner  
**Effective:** 27 November 2026  
**Historical project baseline:** 25 November 2026  
**Status:** Active

## 1. Authority and source of truth

The Product Owner is the final decision-maker for project scope, business requirements, architecture, technology stack, security boundaries, data integrity rules, major dependencies and acceptance.

The GitHub repository is the authoritative shared project record. AI conversations are working context, not a substitute for repository documentation.

Before any assignment or integration, ChatGPT inspects the latest `main`, relevant project documents, task specification, decision records and acceptance criteria. If supplied instructions conflict with the repository or an approved Product Owner decision, work pauses until the discrepancy is resolved.

The historical project baseline is the accepted state through 25 November 2026. This governance reset supersedes conflicting AI workflow arrangements and handoffs introduced on 26 November 2026. It does not discard valid project requirements, accepted foundation decisions or historical commits. Git history must not be rewritten or force-pushed.

## 2. Roles and ownership

### Product Owner — user
- Owns the project and makes final decisions.
- Approves material changes and project acceptance.
- Assembles returned code in VS Code and runs local commands/tests.
- Supplies actual execution results, errors and relevant local changes.

### ChatGPT — Primary AI
ChatGPT is the principal architecture, documentation and integration owner. Responsibilities:
- Requirements, architecture and technical specifications.
- README and all project documentation.
- Decision register and change control.
- Implementation plans, task specifications and acceptance criteria.
- Claude assignment preparation and file ownership records.
- Main-branch governance and approved documentation commits.
- Return/alignment checkpoints, code review and integration.
- Verification assessment based on actual evidence supplied or observed.
- Final status, handoff and documentation synchronisation.

ChatGPT does not claim access to uncommitted local changes unless the user supplies them or makes them available through an explicitly connected tool.

### Claude — Specialist AI
Claude provides independent architecture review by default and performs assigned engineering implementation. Responsibilities:
- Review approved architecture and task specifications.
- Identify technical risks, omissions and alternatives.
- Implement only explicitly assigned code files.
- Return complete file contents in its chat with exact repository-relative paths.
- Explain implementation decisions and assumptions.
- Provide tests, exact execution instructions and expected outcomes.
- Report limitations and unresolved questions honestly.

Claude may read all repository documentation. Reading does not grant authority to modify it.

## 3. Mandatory three-stage workflow

### Stage 1 — ChatGPT: Architecture and documentation
1. Discover and inspect repository state and requirements.
2. Define or confirm business requirements and architecture.
3. Prepare technical specifications, implementation plans and acceptance criteria.
4. Maintain all project documentation.
5. Prepare a bounded Claude assignment with explicit code-file ownership.
6. Obtain Product Owner approval where required.

### Stage 2 — Claude: Engineering and code
1. Review the approved architecture and assignment.
2. Identify risks or omissions before implementation.
3. Implement only the assigned code files.
4. Return complete code files in chat, using exact repository-relative paths.
5. Explain technical decisions and dependencies.
6. Supply tests and exact execution instructions.
7. Report actual test outcomes only when tests were executed; otherwise label them NOT RUN.

### Stage 3 — User, VS Code and ChatGPT: Assembly and integration
1. User places Claude's returned files into the local VS Code workspace.
2. User runs the application, scripts and tests.
3. User supplies actual results, errors and relevant diffs/files.
4. ChatGPT performs the mandatory return/alignment checkpoint.
5. ChatGPT reviews changes against the approved task and latest `main`.
6. ChatGPT resolves integration issues and requests corrections where necessary.
7. ChatGPT integrates approved changes into `main` and updates documentation.
8. Product Owner acceptance remains a separate decision.

## 4. Zero-overlap and file ownership

ChatGPT owns all project documentation, including README, architecture/foundation records, roadmap, decision register, AI collaboration and handoff documents, specifications and phase records.

Claude owns only code files explicitly assigned for a particular engineering task. Claude must not modify ChatGPT-owned documentation unless the Product Owner explicitly approves an ownership transfer for named files and a defined period.

During an active assignment:
- The assignment lists exact files Claude may create or modify.
- All other files are excluded.
- ChatGPT does not simultaneously modify files owned by Claude.
- Claude does not modify documentation or unassigned code.
- Ownership returns to ChatGPT/user integration control when Claude returns the completed assignment or the task is cancelled.

A review-only assignment grants no file ownership and authorises no edits.

## 5. GitHub and branch rules

- `main` is the authoritative shared branch.
- ChatGPT owns main-branch documentation governance and final integration.
- Claude MUST NOT push directly to GitHub, commit to `main`, merge changes or independently modify the repository.
- Branch-based work is prohibited unless the Product Owner explicitly authorises it for a specific task.
- The default engineering handoff is complete files returned in Claude's chat for user-led local assembly.
- No pull request or branch is implied by a Claude assignment.
- Do not rewrite history, force-push or discard historical commits.

If the Product Owner explicitly authorises a branch workflow, its scope, branch and permissions must be recorded before work begins. This exception does not transfer documentation ownership to Claude.

## 6. Return/alignment checkpoint

Whenever the user returns after Claude work or local assembly, ChatGPT must first:
1. Establish and inspect the latest `main` commit.
2. Inspect repository state and relevant committed changes.
3. Compare supplied implementation against the approved assignment.
4. Review actual test results supplied by the user.
5. Identify inconsistencies, omissions, defects and blockers.
6. Confirm alignment or explain what remains unresolved.

Do not issue the next implementation assignment until this checkpoint is complete. Do not claim to see local uncommitted files or test outcomes that have not been supplied or actually observed.

## 7. Change control

Product Owner approval is required before material changes to:
- Business requirements or project scope.
- Architecture or technology stack.
- Security boundaries or data handling.
- Data integrity rules and business definitions.
- Major dependencies or infrastructure commitments.
- Service catalogue or acceptance boundaries.

Routine engineering decisions within the approved baseline may be made by the assigned AI. Recommendations are not approvals. Material approved decisions must be recorded in `docs/DECISIONS.md`.

## 8. Engineering lifecycle and status vocabulary

The engineering lifecycle is:

**DISCOVER → DESIGN → BUILD → VERIFY → REVIEW → RECORD**

Scale activities to task complexity; do not turn every small change into an excessive planning exercise.

Use status labels accurately:
- **NOT STARTED**
- **IN PROGRESS**
- **BLOCKED**
- **IMPLEMENTED**
- **VERIFIED**
- **ACCEPTED**

Implementation is not verification. Verification is not Product Owner acceptance. Never invent test results or overstate production maturity, commercial validation or business impact.

## 9. Documentation and handoff

ChatGPT maintains project documentation and `docs/AI-HANDOFF.md`. The handoff is the current coordination record: baseline, latest inspected main, current phase, active assignment, file ownership, blockers, verification evidence and next authorised action.

Use existing authoritative project documents. Avoid duplicate architecture, roadmap, specification or handoff documents. Update records at meaningful task starts/completions, material decisions, integration points and phase transitions.

## 10. Required assignment contents

Every Claude implementation assignment must state:
- Task identifier and objective.
- Approved requirements and architecture references.
- Exact files Claude may create or modify.
- Explicitly excluded files and scope.
- Input/output contracts and relevant data rules.
- Dependencies and environment assumptions.
- Required tests and acceptance criteria.
- Required return format and execution instructions.
- Material decisions that require escalation.

No substantial implementation begins before the assignment and required Product Owner approvals are in place.
