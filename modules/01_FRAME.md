# Module 1 — Frame

## Purpose

Define the product decision, desired outcome, boundaries, and material uncertainty before diagnosing causes or proposing solutions.

FRAME answers: **What decision are we making?**

## Inputs

- latest approved PRODUCT BRIEF;
- supplied business, user, product, and market context;
- explicit time horizon, constraints, and data references.

Avoid external research unless the business or product model cannot otherwise be understood.

## Method

1. Rewrite the brief as a decision: `What should <team/company> do over <time horizon> to achieve <outcome>?`
2. Identify the real business or mission objective. Do not default to engagement, adoption, or feature usage.
3. Select the primary outcome metric closest to that objective. Check its denominator and proxy risk.
4. Identify the primary user or stakeholder whose behavior or outcome must change. Do not invent personas.
5. Define scope: product surface, segment, geography, lifecycle moment, and decision horizon where known.
6. Capture only constraints that could materially affect the choice.
7. List up to five material assumptions. For each, state what changes if it is false.
8. Identify only unknowns that could change diagnosis, prioritization, or the recommendation.

## Required output

### Decision

[...] 

### Objective and outcome metric

- **Objective:** [...]
- **Primary outcome metric:** [...]
- **Denominator / proxy check:** [...]

### Primary user and scope

- **Primary user or stakeholder:** [...]
- **Scope:** [...]
- **Time horizon:** [...]

### Constraints

- [...]

### Material assumptions

1. **Assumption:** [...]  
   **If false:** [...]

### Decision-critical unknowns

- **Unknown:** [...]  
  **Why it could change the decision:** [...]

### Boundary statement

> FRAME has not concluded what causes the problem or which product approach should be chosen.

## Executive view

Show the decision, intended outcome, primary user, boundaries, highest-leverage assumption, most important unknown, and the judgments requiring human review.

## Approval handoff

```text
FRAME vX — APPROVED
Based on: PRODUCT_BRIEF vX
Decision: ...
Objective: ...
Primary outcome metric: ...
Primary user: ...
Scope and horizon: ...
Constraints: ...
Material assumptions: ...
Decision-critical unknowns: ...
```

## Quality gate

- Does this frame the actual brief without broadening it?
- Is the objective outcome-oriented rather than a proxy?
- Is the metric definition and denominator clear?
- Are scope and constraints decision-relevant?
- Are assumptions material rather than filler?
- Has diagnosis and solution leakage been removed?
