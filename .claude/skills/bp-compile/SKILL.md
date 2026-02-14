---
name: bp-compile
description: Compile all business plan sections into a single final document. Use after all specialists have written their sections.
disable-model-invocation: true
argument-hint: "[business-plan-directory]"
allowed-tools: Read, Write, Edit, Grep, Glob
---

# Business Plan Compiler

Compile all business plan section files into a single, polished final document.

## Instructions

1. Read all section files from the business plan directory (`$ARGUMENTS` or `./business-plan/`):
   - `01-executive-summary.md`
   - `02-company-description.md`
   - `03-market-analysis.md`
   - `04-organization.md`
   - `05-product-services.md`
   - `06-marketing-sales.md`
   - `07-financial-projections.md`
   - `08-funding-request.md`
   - `09-operational-plan.md`
   - `10-risk-management.md`
   - `11-appendix.md`

2. Also read `investor-review.md` if it exists.

3. Compile into `00-full-plan.md` with:
   - Title page (company name, date, version, confidentiality notice)
   - Table of contents with page references
   - All 11 sections in order
   - Investor review as a separate appendix
   - Consistent heading levels (H1 for sections, H2 for subsections)
   - Consistent formatting throughout

4. Run a consistency check:
   - Financial numbers match across sections (revenue in exec summary = revenue in financials)
   - Team sizes match between org structure and hiring plan
   - Market size in exec summary matches market analysis
   - CAC/LTV in marketing matches financial projections
   - Timeline milestones are consistent

5. Generate a `plan-status.md` file with:
   - Completion status per section
   - List of all `[TO BE DETERMINED]` items
   - List of all `[ASSUMPTION]` items
   - Identified inconsistencies (if any)
   - Word count per section and total
   - Recommended next steps

## Output

Write the compiled plan to `00-full-plan.md` and the status report to `plan-status.md`.
