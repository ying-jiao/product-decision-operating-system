# Module 5 — Execution + Validate

## Purpose

Translate the approved choice into a concrete, right-sized product plan and define how the team will learn whether the implementation, solution, and diagnosis are working.

EXECUTION + VALIDATE answers: **What do we do first, and how will we know?**

## Inputs

- latest approved FRAME, ANALYZE, DIAGNOSE, and SOLUTIONS + DECIDE;
- relevant product, technical, operational, and data context.

## Method

1. Restate the diagnosis, chosen approach, reason for selection, and inherited trade-off.
2. Describe the mechanism: `Trigger / need → Input → Product logic → Experience → User action → Expected outcome`.
3. For AI, specify input, task, output, why AI is preferable, failure modes, and guardrails. State explicitly when AI is not central.
4. Define a solution hypothesis linking target user, diagnosed problem, chosen approach, expected behavior, business outcome, validation signal, and guardrail.
5. Define the smallest MVP that creates meaningful value and tests the core hypothesis.
6. Specify included and excluded scope, target segment or moment, and what learning unlocks NEXT.
7. Name attractive work that is deliberately NOT DOING / NOT YET.
8. Define the ultimate outcome, primary leading signal, diagnostics, and guardrails. Test whether each metric could improve while the real outcome worsens.
9. Convert metrics into action rules: condition → interpretation → action.
10. Identify implementation-specific trade-offs and material risks with mitigations.
11. Separate three reconsideration levels: implementation, product solution, and diagnosis/strategy.

## Required output

### Chosen approach

Leading diagnosis / chosen approach / why selected / inherited trade-off.

### How it works

> Trigger or need → Input → Product or AI logic → User experience → User action → Expected outcome

### Solution hypothesis

> We believe that [approach] for [target user/segment] will improve [problem, behavior, or friction], which should contribute to [business outcome]. We will consider the hypothesis supported if [leading signal] improves while [guardrail] remains healthy.

- **Invalidating evidence:** [...]

### NOW / MVP

- **Included:** [...]
- **Excluded:** [...]
- **Target:** [...]
- **Why first:** [...]
- **What it tests:** [...]

### NEXT

What follows only if NOW produces the required learning.

### NOT DOING / NOT YET

Attractive work deliberately deferred and why.

### Metrics and decision rules

- **Ultimate outcome:** [...]
- **Primary leading signal:** [...]
- **Diagnostics:** [...]
- **Guardrails:** [...]

| Condition | Interpretation | Action |
|---|---|---|
| | | scale / iterate / pause / rollback / reconsider |

### Trade-offs and risks

| Risk or trade-off | Why it matters | Mitigation | Mitigation cost |
|---|---|---|---|
| | | | |

### Reconsideration conditions

- **Implementation:** If [...], iterate execution while preserving the chosen solution and diagnosis.
- **Product solution:** If [...], revisit SOLUTIONS + DECIDE.
- **Diagnosis / strategy:** If [...], rerun DIAGNOSE or the earliest affected module.

## Executive view

Show the mechanism, hypothesis, NOW/NEXT/NOT DOING, key metrics and guardrails, actionable rules, material risks, three reconsideration levels, and judgments requiring review.

## Approval handoff

```text
EXECUTION_VALIDATE vX — APPROVED
Based on: FRAME vX + ANALYZE vX + DIAGNOSE vX + SOLUTIONS_DECIDE vX
Chosen approach: ...
Solution hypothesis: ...
NOW / MVP: ...
NEXT: ...
NOT DOING: ...
Leading signal: ...
Guardrails: ...
Decision rules: ...
Reconsideration conditions: ...
```

## Quality gate

- Does the plan faithfully implement the chosen approach?
- Does the hypothesis trace diagnosis → solution → behavior → outcome?
- Is the MVP small enough to learn and large enough to create value?
- Are exclusions and deferrals meaningful?
- Do metrics distinguish supported, weakened, and rejected?
- Do decision rules lead to different actions?
- Is technology specific and justified?
- Are the three reconsideration levels genuinely different?
