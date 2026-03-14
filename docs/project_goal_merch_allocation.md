# Project Goal: Merchandise Allocation Web Tool

## 1. High-Level Objective

Convert the existing Excel-based merchandise allocation model
("Template Allocate_MC 09.02.2026.xlsx") into a centralised internal
web application for fashion retail merchandising and allocation teams. [file:56]

The webapp should:
- Improve traceability and consistency of allocation decisions.
- Make it easier to manage size master data and range plans.
- Provide a clear, editable allocation grid per product (model_col_sap).
- Prepare data for downstream ordering and integration. [file:56]

## 2. Core Modules (Scope)

The project is split into four main modules, plus future monitoring: [file:56]

- Size Master
  - Manage size mappings, size profiles per store, and size ratios. [file:56]
- Range Planning
  - Plan parameters and targets per model_col_sap and season. [file:56]
- Allocation
  - Run an allocation engine and editable allocation grid per model_col_sap,
    with system proposals and user overrides. [file:56]
- Ordering
  - Turn approved allocations into buy quantities and order summaries. [file:56]
- Monitoring (future)
  - Dashboards for sell-through, stock cover, broken sizes. [file:56]

## 3. Phased Delivery Plan

The implementation is planned in phases: [file:56]

- Phase 1 – Foundations & Size Master (Weeks 1–4)
- Phase 2 – Range Planning (Weeks 5–8)
- Phase 3 – Allocation Engine (Weeks 9–14)
- Phase 4 – Ordering & Integration (Weeks 15–18)
- Phase 5 – Performance & Enhancements (Weeks 19+) [file:56]

Agents should:
- Respect these phases when proposing work.
- Prefer building foundation pieces earlier when they unblock later phases.

## 4. Technical Stack (Target)

Preferred high-level stack: [file:56]

- Frontend:
  - Next.js (TypeScript, App Router)
  - Tailwind CSS + a component library (e.g. shadcn/ui)
  - TanStack Table for data grids

- Backend:
  - REST-style API service

- Database:
  - PostgreSQL

Agents must:
- Align suggestions with this stack unless the user explicitly decides
  to change it.
- Reference this file instead of redefining the stack.

## 5. Key Allocation Logic (Summary)

For each product (model_col_sap), the system must be able to: [file:56]

- Use inputs from:
  - Product details and hierarchy
  - Range Plan
  - Size Master (size_profiles, size_ratios)
  - Store Master (stores, channels, clusters)
  - Density Rules (channel + cluster + density → units_per_store)

- Generate an initial allocation:
  - Determine eligible stores.
  - Look up size profiles and size ratios per store.
  - Apply density rules to compute units_per_store per store.
  - Distribute units across sizes using ratios, with rounding rules.
  - Persist allocation header and allocation lines. [file:56]

- Apply validation rules before approval:
  - Density consistency per store row.
  - Size ratio alignment vs expected profiles.
  - Total vs planned TTL initial.
  - Channel distribution alignment.
  - Data completeness for eligible stores. [file:56]

Agents working on Allocation must:
- Follow these concepts and rules.
- Refer to the detailed spec file (e.g.
  `docs/spec/Merch_Allocation_Project_Spec_v1.2.docx`) for full details.

## 6. Out-of-Scope (for Now)

Unless the user explicitly expands the project scope, the following are
considered out-of-scope for this project:

- External ERP integration beyond preparing clean data outputs.
- Advanced forecasting or optimisation beyond the rules in the current spec.
- Complex monitoring dashboards (Phase 5+ only, future work). [file:56]

Agents should:
- Flag any request that appears outside this scope.
- Offer options, but let the user decide whether to extend the project.
