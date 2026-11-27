# AI Handoff & Project Coordination

**Maintainer:** ChatGPT — Primary AI  
**Authority:** Product Owner  
**Last updated:** 26 November 2026  
**Current branch:** `main`

## 1. Current project status

**Foundation:** ACCEPTED by the Product Owner on 25 November 2026.  
**Phase 0 — Foundation and repository setup:** Complete; accepted baseline is recorded in `docs/PROJECT-FOUNDATION.md`.  
**Phase 1 — Spreadsheet Cleaning & Restructuring:** NOT STARTED.  
**Current activity:** Phase 1 methodology and dataset-readiness review assigned to Claude as REVIEW ONLY.  
**Implementation:** No substantial service implementation has begun.

The accepted project configuration remains:
- Modular, workflow-oriented, local-first architecture.
- Approved toolkit: Excel/Power Query, SQL Server 2022/T-SQL, Python/pandas where justified, Power BI, Git/GitHub and justified local automation.
- Six approved service categories, delivered progressively.
- Synthetic or appropriately licensed public data for demonstrations; no confidential/client data in the public repository.

## 2. Authoritative baseline

Repository: https://github.com/obakengshepherd/REPORTING-AUTOMATION-INSIGHT-SERVICE-KIT  
Default branch: `main`  
Latest inspected main commit at this handoff update: `2d732d7f28409e06e23d49e73b7ee2e1a0a7ce4c`  
Latest commit message: `docs(reporting): align README with accepted foundation status`

The latest commit updates README status to reflect accepted foundation and Phase 1 not started. It is preserved.

Relevant accepted documents:
- `README.md`
- `docs/PROJECT-FOUNDATION.md`
- `docs/PROJECT-ROADMAP.md`
- `docs/SERVICE-CATALOGUE.md`
- `docs/SERVICE-DELIVERY-METHODOLOGY.md`
- `docs/DATA-INTAKE-STANDARDS.md`
- `docs/DATA-QUALITY-STANDARDS.md`
- `docs/QUALITY-ASSURANCE.md`

No pre-existing `docs/AI-COLLABORATION.md` or `docs/AI-HANDOFF.md` was present on the inspected `main`; these documents establish the missing collaboration controls and live handoff record.

## 3. Approved service catalogue

1. Spreadsheet Cleaning & Restructuring.
2. Data Quality Assessment.
3. SQL Reporting & Data Extraction.
4. Recurring Reporting Automation.
5. Dashboard Development.
6. Small-scale Business Analytics.

All six are approved. This does not authorise simultaneous implementation of all six.

## 4. Completed work

- Product Owner approved modular architecture, recommended toolkit and six-service demonstration scope.
- Product Owner accepted the foundation documentation on 25 November 2026.
- Foundation acceptance was recorded in `docs/PROJECT-FOUNDATION.md`.
- Roadmap was updated to mark Phase 0 accepted and Phase 1 NOT STARTED.
- README status was corrected on main and is preserved.
- Latest main, repository metadata, root/docs listings, relevant project documentation, recent commit history and pull-request listing were inspected for collaboration initialisation.
- No open pull requests were returned by the inspected repository pull-request listing.

## 5. Active assignment register

### PH1-REVIEW-001 — Phase 1 methodology and dataset readiness

- **Classification:** REVIEW AND RECOMMEND (review-only; no file modification authorised).
- **Assigned AI:** Claude — Specialist AI.
- **Status:** PREPARED / AWAITING CLAUDE REVIEW.
- **Branch:** Not applicable; review-only assignments do not create branches.
- **Base reference:** `main` at `dd4b127b2fc1d1a4d0ae0af39e9a74024baf6229` (latest main commit after collaboration documentation setup).
- **Files owned by Claude:** None.
- **Files excluded:** All repository files; no edits or commits are authorised for this review.
- **Files ChatGPT maintains:** `docs/AI-HANDOFF.md` and routine coordination documentation.
- **Expected deliverable:** Written technical review and recommendation for a suitable synthetic/public dataset profile, Phase 1 cleaning methodology, rules, validation and reconciliation approach, tool selection and bounded implementation scope.
- **Verification:** Review must be reasoned against the accepted repository standards; distinguish requirements from recommendations and identify assumptions, risks and open decisions.
- **Next gate:** ChatGPT evaluates Claude's review and presents the proposed dataset and Phase 1 scope to the Product Owner where confirmation is required. No implementation until scope and dataset are settled and an explicit implementation assignment is issued.

### Review topics

Claude is asked to assess:
1. Spreadsheet intake and source profiling.
2. Preservation and traceability of raw inputs.
3. Duplicate detection, classification and treatment.
4. Missing-value classification and treatment.
5. Data-type and format standardisation.
6. Date, numeric and currency handling.
7. Whitespace and text normalisation.
8. Invalid and inconsistent records.
9. Transformation documentation and assumptions.
10. Before-and-after record-count and value reconciliation.
11. QA, repeatability and exception handling.
12. Reusable workbook and output design.
13. Appropriate roles for Excel, Power Query, SQL Server and Python/pandas.
14. Synthetic or appropriately licensed public dataset characteristics suitable for a realistic first demonstration.

Claude must not invent a real client dataset, imply client provenance, use confidential data, choose a dataset on behalf of the Product Owner as an approved decision, or modify repository files during this review.

## 6. Pending decisions and approvals

- Phase 1 dataset/source selection.
- Phase 1 business scenario, dataset grain and scope.
- Specific cleaning and transformation rules where business meaning is ambiguous.
- Final Phase 1 deliverable and acceptance criteria.

These will be proposed after the specialist review. Existing high-level toolkit and six-service scope are already approved and should not be reopened without a material reason.

## 7. File ownership and active changes

- **ChatGPT:** Maintains this handoff and collaboration documentation on `main`.
- **Claude:** No file ownership; review-only assignment.
- **Product Owner:** Final authority on material decisions and acceptance.

No simultaneous editing is authorised. If Claude receives a later implementation or documentation assignment, create a dedicated `claude/<work-item-slug>` branch from the latest appropriate main commit, record assigned/excluded files and ownership here, and require a PR to main. Claude must not push to or merge into main.

## 8. Review and integration record

No Claude findings have been received yet. No specialist review has been completed, no Claude branch or PR exists, and no implementation has been integrated.

When findings arrive, record:
- Summary and recommendation.
- Findings accepted, modified or rejected by ChatGPT, with reasons.
- Product Owner decisions required and their outcomes.
- Any resulting implementation assignment and ownership.
- Verification evidence and integration commit, if applicable.

## 9. Next authorised action

1. Send the PH1-REVIEW-001 assignment to Claude for review only.
2. Receive and assess Claude's written findings.
3. Prepare a dataset recommendation and bounded Phase 1 scope.
4. Obtain Product Owner confirmation where required.
5. Only then issue a separately authorised implementation assignment under the branch and PR controls in `docs/AI-COLLABORATION.md`.

**Current gate: Awaiting Claude's review. Phase 1 implementation remains NOT STARTED.**
