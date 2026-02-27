---
name: bp-validate
description: Run a quality validation pass on a completed business plan. Checks numerical consistency across sections, assumption labeling, missing critical fields, internal logic gaps, and ethics guardrails. Use before /bp-compile to catch errors investors will find.
argument-hint: "[path to business-plan directory, e.g. ./business-plan/]"
disable-model-invocation: true
allowed-tools: Read, Write, Edit, Grep, Glob
---

# Business Plan Validator

Run a structured quality check on all draft sections before final compile.

## Input

Business plan directory: `$ARGUMENTS` (default: `./business-plan/`)

## Step 1: Read all sections

Read every `.md` file in the directory. Extract key numbers into a working table:

| Metric | Value found | Location (file:section) |
|--------|------------|------------------------|
| Revenue Y1 | | |
| Revenue Y2 | | |
| Revenue Y3 | | |
| CAC (blended) | | |
| LTV | | |
| LTV/CAC ratio | | |
| Funding ask | | |
| Team size at launch | | |
| TAM | | |
| Break-even month | | |

## Step 2: Numerical cross-consistency check

Compare extracted values across sections:

- `01-executive-summary.md` §1.7 vs `07-financial-projections.md` §7.2 — revenue match?
- `06-marketing-sales.md` §6.5 vs `07-financial-projections.md` §7.5 — CAC/LTV/ratio match?
- `01-executive-summary.md` §1.8 vs `08-funding-request.md` §8.1 — funding ask match?
- `01-executive-summary.md` §1.5 vs `03-market-analysis.md` §3.1 — TAM match?
- `04-organization.md` §4.7 vs `07-financial-projections.md` §7.8 — headcount/OPEX match?
- `08-funding-request.md` §8.6 milestones vs `07-financial-projections.md` §7.3 runway — timeline match?

Flag mismatches. Rounding differences < 5% are acceptable — note but don't flag as critical.

## Step 3: Assumption labeling audit

Search all sections for these patterns using Grep:

- Percentage claims without source (e.g., "conversion rate of 12%")
- Market size figures without methodology citation
- Competitor analysis claims without evidence ("competitor X is weak at Y")
- Financial projections derived from industry benchmarks — need source or `[ASSUMPTION]`
- Growth rates cited without CAGR methodology

Each should carry `[ASSUMPTION]` or a cited source. List every violation.

## Step 4: Completeness check

Verify no section contains:
- Blank required subsections
- "TBD", "TODO", "PLACEHOLDER", "N/A" without explanation
- Subsections that exist in the template but have no content

List all `[TO BE DETERMINED]` items found — do not remove them, just catalog them.

## Step 5: Internal logic check

Verify:

- **Team capacity:** Can the headcount in §4.7 realistically execute the roadmap in §5.9 and sales targets in §6.13?
- **Revenue timing:** Does revenue start date in §7.2 align with product launch in §5.8?
- **Operational load:** Can the ops plan in §9.2 handle the customer volumes projected in §6.13?
- **Budget coverage:** Does the funding ask in §8.3 cover the OPEX in §7.8 for the stated runway?
- **Risk coverage:** Does §10.1 risk matrix cover the major risks mentioned in §3.11, §5.6, and §7.12?

## Step 6: Ethics and quality guardrails

Flag:

- Claims of "no competition" or "first in market" in established categories — investors will research this
- Projections with only optimistic/base scenarios and no pessimistic case
- Missing AI-generated content disclaimer (check §11.3 or title page)
- Forward-looking statements presented as facts rather than projections
- Personal data collection described without privacy/compliance mention (cross-check §10.12)

## Step 7: Output report

Write `validation-report.md` in the business plan directory:

```markdown
# Business Plan Validation Report

**Generated:** [date]
**Directory:** [path]
**Sections reviewed:** [list of files]
**Validator score:** X/10

---

## 🔴 Critical issues (fix before any investor sees this)
...

## 🟡 High-priority issues
...

## 🟢 Minor issues
...

---

## Numerical cross-check table
[table with match/mismatch for each metric]

## Unlabeled assumptions
[list with section, quote, recommended fix]

## [TO BE DETERMINED] items
[catalog with section and why it's needed]

## Potential hallucinations
[list with section, statistic, recommended action]

## Missing disclaimers
- [ ] AI-generated content disclaimer
- [ ] Forward-looking statements note
...

## Logic gaps
...

## Passed checks ✓
...
```

**Do not modify any section files.** This skill is read-only and report-only.
Fixes are made by spawning the relevant specialist agents with the validation report as context.
