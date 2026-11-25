# Quality Assurance

## Objective

Provide evidence that a service deliverable behaves as intended, its figures are defensible and its workflow can be understood and repeated.

## QA areas

### Data
- Input/output record counts are understood.
- Required fields and types are checked.
- Duplicates, missing values and invalid values are handled according to documented rules.
- Rejected records and exceptions are traceable.

### Transformation
- Transformation rules are documented.
- Outputs are consistent with expected examples.
- Repeated execution does not introduce unintended changes or duplicates.
- Raw source data remains preserved.

### Business logic and calculations
- KPI definitions are explicit.
- Reporting periods, filters, units and currencies are correct.
- Totals and aggregations reconcile to trusted source values or independently calculated checks.
- No double counting is introduced by joins or grouping.

### Presentation
- Titles, reporting periods, units and labels are clear.
- Visuals suit the question and audience.
- Filters and calculations behave as expected.
- Findings are supported by evidence and limitations are visible.

### Handover
- Inputs, outputs and dependencies are identified.
- Execution and reproduction instructions are complete.
- Known limitations and unresolved defects are disclosed.

## Verification status vocabulary

- **NOT STARTED:** Work has not begun.
- **IN PROGRESS:** Work is underway.
- **BLOCKED:** A dependency prevents progress.
- **IMPLEMENTED:** Functionality has been developed.
- **VERIFIED:** Evidence confirms expected behaviour.
- **ACCEPTED:** Product Owner approves the deliverable.

Implementation is not verification. Verification is not Product Owner acceptance.

## Evidence record

For each meaningful verification activity, record scope, environment/tool version where relevant, test or check performed, expected result, actual result, status, evidence location and unresolved issue. Never report a test as passed unless it was executed and its result observed.
