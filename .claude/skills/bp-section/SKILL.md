---
name: bp-section
description: Generate a single specific section of a business plan. Use when you need just one section, not the whole plan.
argument-hint: "[section-number] [business idea]"
disable-model-invocation: true
allowed-tools: Read, Write, Edit, Grep, Glob, Skill
---

# Single Section Generator

Generate a specific section of a business plan.

## Usage

`/bp-section [section-number] [business idea description]`

Example: `/bp-section 3 AI-powered inventory management for restaurants`

## Section mapping

| # | Section | Specialist agent |
|---|---------|-----------------|
| 1 | Executive Summary | bp-ceo |
| 2 | Company Description | bp-ceo |
| 3 | Market Analysis | bp-researcher |
| 4 | Organization & Management | bp-legal |
| 5 | Products & Services | bp-cto |
| 6 | Marketing & Sales | bp-cmo |
| 7 | Financial Projections | bp-cfo |
| 8 | Funding Request | bp-cfo |
| 9 | Operational Plan | bp-coo |
| 10 | Risk Management | bp-legal |
| 11 | Appendix | bp-legal |
| review | Investor Review | bp-investor |

## Instructions

1. Parse `$ARGUMENTS` — first word is section number, rest is the business idea
2. Identify the correct specialist agent from the table above
3. Delegate to that agent with the business idea as the brief
4. Save the output to `business-plan/[section-number]-[section-name].md`

If the section number is not provided, ask the user which section they want.
