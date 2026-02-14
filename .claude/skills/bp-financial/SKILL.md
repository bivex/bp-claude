---
name: bp-financial
description: Generate Financial Projections section of a business plan. Use when writing section 7 — P&L, cash flow, balance sheet, unit economics, scenarios.
user-invocable: false
---

# Financial Projections Generator (Section 7)

You are writing **Section 7: Financial Projections** of an investor-grade business plan.

## Revenue Model & Assumptions

List ALL assumptions explicitly:
- Pricing tiers and expected mix
- Customer acquisition rate (monthly)
- Churn rate
- Revenue per customer (ARPU)
- Seasonality factors
- Growth rate assumptions (and why)

## P&L — 3 Years

Year 1: monthly breakdown. Years 2-3: quarterly.

| Period | Revenue | COGS | Gross Profit | OpEx | EBITDA | Net Income |
|--------|---------|------|-------------|------|--------|------------|

### OpEx breakdown:
- Salaries & benefits
- Marketing & sales
- R&D
- G&A (rent, utilities, insurance)
- Professional services (legal, accounting)

## Cash Flow Statement — 3 Years

| Period | Operating CF | Investing CF | Financing CF | Net CF | Cash Balance |
|--------|-------------|-------------|-------------|--------|-------------|

Highlight months where cash goes negative.

## Balance Sheet — 3 Years (Annual)

| Item | Y1 | Y2 | Y3 |
|------|-----|-----|-----|
| **Assets** | | | |
| Cash | | | |
| Accounts Receivable | | | |
| Fixed Assets | | | |
| **Liabilities** | | | |
| Accounts Payable | | | |
| Debt | | | |
| **Equity** | | | |

## Unit Economics

| Metric | Value | Benchmark | Status |
|--------|-------|-----------|--------|
| CAC | | | |
| LTV | | | |
| LTV/CAC | | >3x | |
| Payback period | | <12 mo | |
| Gross margin | | >50% | |
| Contribution margin | | | |

## Break-Even Analysis

- **Fixed costs** / (Price per unit − Variable cost per unit)
- Month when break-even is reached
- Sensitivity: what if price is 20% lower? What if CAC is 50% higher?

## EBITDA Trajectory

Show the path from negative to positive EBITDA with key inflection points.

## CAPEX & OPEX

**CAPEX** (one-time): equipment, licenses, build-out
**OPEX** (monthly): rent, salaries, marketing, software, hosting

## Scenario Analysis

| Metric | Pessimistic | Base | Optimistic |
|--------|------------|------|-----------|
| Customer growth | | | |
| Churn | | | |
| ARPU | | | |
| CAC | | | |
| Revenue Y3 | | | |
| Cash needed | | | |
| Break-even month | | | |

Describe what drives each scenario.

## DCF Valuation (if applicable)

- Discount rate and justification
- Terminal value methodology
- Implied valuation range

## Writing rules
- Every number must trace to an assumption
- Flag high-uncertainty estimates with [ESTIMATE]
- All three financial statements must be internally consistent
- Show the math: investors will check
- Include a "cash runway" calculation: months of runway at current burn
