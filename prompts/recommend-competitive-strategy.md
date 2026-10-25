---
type: prompt
id: recommend-competitive-strategy
title: Recommend Strategy
description: "Produces prioritized competitive strategy recommendations from the comparative analysis"
tags: [Production, Competitive, Strategy]
context_params:
  source:
    label: "Competitive Analysis"
    description: "The consolidated competitive analysis supplied by the upstream step."
    required: true
inputs:
  your_product:
    label: "Your Product"
    description: "Your product name and brief description"
    example: "Skrptiq — AI workflow builder for structured content production"
    required: true
    type: text
metadata:
  output_format: markdown
  prompt_type: synthesis
---

## Purpose

Drives the strategic recommendation skill. Runs after the consolidation step. Translates the comparative analysis into actionable decisions.

## Prompt

You are a product strategist advising a leadership team. Based on the competitive analysis below, produce prioritized strategic recommendations.

### Your Product

{{input.your_product}}

### Competitive Analysis

{{step.context.source}}

### Instructions

Produce recommendations in three categories. For each recommendation, include:

- **Action:** What specifically to do
- **Rationale:** Which competitive insight drives this recommendation
- **Impact:** High / Medium / Low
- **Timeframe:** Immediate (this sprint) / Quarter (next 90 days) / Year (strategic bet)

**Differentiate** — Where can you establish a unique position?

List 2-3 recommendations for areas where your product can carve out territory that no competitor currently owns. These should be realistic given your product's current capabilities.

**Defend** — Where are you most at risk?

List 2-3 recommendations for areas where competitors are strong and you need to protect your position. Focus on threats that could cause customers to switch.

**Invest** — What bets should you make?

List 1-2 recommendations for capabilities or markets where no competitor is strong yet. These are higher-risk, higher-reward moves.

### Priority Summary

After the detailed recommendations, produce a single prioritized table:

| Priority | Action | Category | Impact | Timeframe |
|----------|--------|----------|--------|-----------|
| 1 | [Most important action] | Differentiate/Defend/Invest | High/Medium/Low | Immediate/Quarter/Year |
| 2 | ... | ... | ... | ... |
| ... | ... | ... | ... | ... |

Rank by a combination of impact and urgency. Defensive actions with high threat level should rank above speculative investments.

## Formatting Rules

- Use British English throughout
- Be specific: "Add a Jira integration to match Competitor X's workflow automation" — not "improve integrations"
- Each recommendation should be actionable by a product team — not a vague strategic platitude
- Limit to 7 recommendations maximum — fewer, better recommendations beat an exhaustive list
