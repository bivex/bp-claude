# Business Plan Generator — Claude Code Project

This workspace contains a system of Claude Code **skills** and **agents** that work as a coordinated dream-team to produce investor-grade business plans.

## How to use

### Full business plan (team approach)
```
/business-plan [describe your business idea in detail]
```
This orchestrates 8 specialist agents in sequence, each writing their section.

### Full business plan (agent team — parallel)
```
/business-plan-team [describe your business idea in detail]
```
This spawns an agent team where specialists work in parallel and communicate with each other.
Requires `CLAUDE_CODE_EXPERIMENTAL_AGENT_TEAMS=1` in settings.

### Compile sections into final document
```
/bp-compile ./business-plan/
```

### Investor-readiness sprint (harden for fundraising)
```
/bp-investor-sprint ./business-plan/
```
Run after `/business-plan` to iterate CEO + CFO + Investor in a loop until deal readiness score ≥ 7/10.
Max 3 cycles. Outputs `sprint-summary.md` with resolved gaps and remaining founder action items.

## Team roles

| Role | Agent | Sections | Skill |
|------|-------|----------|-------|
| CEO / Founder | `bp-ceo` | 1. Executive Summary, 2. Company Description | `bp-executive-summary` |
| Market Researcher | `bp-researcher` | 3. Market Analysis | `bp-market-research` |
| Legal Counsel & Risk Manager | `bp-legal` | 4. Organization, 10. Risk Management, 11. Appendix | `bp-legal-risk`, `bp-organization` |
| CTO / Product Director | `bp-cto` | 5. Products & Services | `bp-product` |
| CMO / Marketing Director | `bp-cmo` | 6. Marketing & Sales | `bp-marketing` |
| CFO / Financial Director | `bp-cfo` | 7. Financial Projections, 8. Funding Request | `bp-financial`, `bp-funding` |
| COO / Operations Director | `bp-coo` | 9. Operational Plan | `bp-operations` |
| Investment Banker / VC Advisor | `bp-investor` | Investor Review | `bp-funding` |

## Business plan sections

1. **Executive Summary** — mission, product, value proposition, market, financials summary
2. **Company Description** — legal entity, history, mission/vision/values, achievements
3. **Market Analysis** — TAM/SAM/SOM, trends, personas, competitive landscape
4. **Organization & Management** — structure, team, hiring plan, compensation
5. **Products & Services** — product details, USP, roadmap, IP, pricing
6. **Marketing & Sales** — go-to-market, channels, funnel, CAC/LTV, sales plan
7. **Financial Projections** — P&L, cash flow, balance sheet, unit economics, scenarios
8. **Funding Request** — amount, terms, use of funds, milestones, exit strategy
9. **Operational Plan** — processes, logistics, IT, quality, compliance, HR
10. **Risk Management** — risk matrix, mitigation plans, Plan B/C, early warnings
11. **Appendix** — document checklist, supporting materials

## Agent synergies

The system has three validated collaboration patterns that produce the best results:

| Synergy | Agents | Purpose |
|---------|--------|---------|
| **Strategy + Finance** | `bp-ceo` + `bp-cfo` | CEO vision grounded by CFO numbers — prevents economically unviable plans |
| **Product-Market Fit** | `bp-researcher` + `bp-cmo` + `bp-cto` | Market data → positioning → product adaptation |
| **Risk + Compliance** | `bp-legal` + `bp-coo` | Operations validated against regulatory constraints before launch |

**Conflict resolution priority:** Legal/compliance > Financial viability > Market opportunity > Operational preference

**Data flow order (validation priority):**
1. Financials & Legal — errors here are fatal
2. Market Research — without market evidence, revenue projections are guesses
3. Product & Operations — how it actually works
4. Executive Summary — a synthesis of all the above, written last

## Quality standards

- All content in English
- Target audience: sophisticated investors / VCs
- Every claim needs evidence or is labeled `[ASSUMPTION]`
- Missing data marked as `[TO BE DETERMINED]`
- Financial numbers must be internally consistent across sections
- 30-50 pages when compiled
