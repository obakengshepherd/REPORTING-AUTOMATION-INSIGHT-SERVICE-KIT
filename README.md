# Reporting Automation & Insight Service Kit

**Practical Data Services · Reporting Automation · Business Insights**

## Project status

**Foundation accepted — 25 November 2026. Phase 1 implementation scope approved — 27 November 2026. RASK-P1-I1 handoff finalised; implementation NOT STARTED pending Claude dispatch.**

## Purpose

This project demonstrates how raw or semi-structured business data can be transformed into reliable, validated, repeatable and professionally presented reporting deliverables. It is a service demonstrator and reusable toolkit, not a claim of existing clients, contracts, revenue or production deployments.

## Approved architecture

A modular, workflow-oriented, local-first toolkit. Capabilities are organised as reusable service workflows rather than forced into one integrated application.

## Service catalogue

1. Spreadsheet Cleaning & Restructuring
2. Data Quality Assessment
3. SQL Reporting & Data Extraction
4. Recurring Reporting Automation
5. Dashboard Development
6. Small-scale Business Analytics

All six service categories are in the approved demonstration scope and will be implemented progressively.

## Approved toolkit

- Microsoft Excel and Power Query
- SQL Server 2022 and T-SQL
- Python and pandas, where justified
- Microsoft Power BI
- Git and GitHub
- Supporting local automation techniques when justified

Phase 1 uses Python/pandas and pytest for its processing and test workflow, with XLSX and CSV deliverables. Power Query is deferred for this phase; the wider project toolkit remains unchanged.

## Delivery lifecycle

**Discover → Assess → Prepare → Develop → Verify → Deliver**

Every service should define its business requirement, scope, source data, transformations, validation approach, deliverables and handover instructions.

## Repository guide

- `docs/PROJECT-FOUNDATION.md` — approved purpose, scope, constraints and architecture
- `docs/SERVICE-CATALOGUE.md` — six approved service categories
- `docs/SERVICE-DELIVERY-METHODOLOGY.md` — common delivery lifecycle
- `docs/DATA-INTAKE-STANDARDS.md` — source assessment and intake requirements
- `docs/DATA-QUALITY-STANDARDS.md` — validation, quality classification and handling principles
- `docs/QUALITY-ASSURANCE.md` — verification and acceptance controls
- `docs/PROJECT-ROADMAP.md` — phased implementation, FNEOS gates and exit criteria
- `docs/DECISIONS.md` — material approved decisions and change control
- `docs/PHASE-1-SPECIFICATION.md` — approved Phase 1 requirements, source schema, controls and acceptance criteria
- `docs/AI-COLLABORATION.md` — FNEOS roles, file ownership and three-stage workflow
- `docs/AI-HANDOFF.md` — current status, assignments, ownership and next authorised action

## Data and commercial integrity

Use synthetic or appropriately licensed public datasets for demonstrations. Do not commit confidential, personal or client data. Clearly distinguish demonstrations and reusable templates from actual client engagements and commercially validated services. Do not claim business impact without measured evidence.

## Current boundary

The Product Owner accepted the foundation on 25 November 2026 and approved the Phase 1 implementation scope on 27 November 2026. Claude's RASK-ARCH-REV-001 review is closed with recommendations adopted. RASK-P1-I1 is the approved first engineering increment; its bounded handoff is prepared and committed. Implementation has not started because Claude has not yet received the assignment. Verification and Product Owner acceptance remain separate.
