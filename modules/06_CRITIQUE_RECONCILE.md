# Module 6 — Critique + Reconcile

## Purpose

Stress-test the complete decision chain, then decide whether to keep, refine, switch, or reframe the recommendation. Route material problems to targeted reruns and preserve explicitly accepted risk.

CRITIQUE + RECONCILE answers: **Does the decision hold under the strongest reasonable challenge?**

## Inputs

- latest approved outputs from FRAME through EXECUTION + VALIDATE;
- raw evidence needed to audit material claims;
- Product Decision Quality Rubric.

## Part A — Critique

Challenge every transition:

```text
brief → frame → evidence → diagnosis → alternatives → choice → implementation → validation
```

Test:

- decision, objective, user, scope, metric, denominator, and proxy risk;
- calculation integrity, source labels, baselines, bias, mix shift, and missing evidence;
- causal overreach and credible competing explanations;
- diagnosis fit, solution altitude, missing approaches, and option overlap;
- decision criteria, double counting, strongest alternative, and real trade-off;
- mechanism, MVP, sequencing, hidden dependencies, and technology necessity;
- metric gaming, guardrails, action rules, and three reconsideration levels;
- consistency across users, claims, assumptions, recommendation, and plan.

Steelman both the strongest alternative diagnosis and strongest alternative solution. Identify the most fragile assumption.

### Finding format

Give every actionable finding a stable ID and severity:

```text
ID: C1
Severity: BLOCKING | MATERIAL | ADVISORY
Issue: ...
Why it matters: ...
Affected module: ...
Recommended action: ...
```

### Critique output

- **Overall verdict:** strong and consistent / directionally strong with revisions / materially flawed / not defensible
- **Findings:** all decision-relevant findings
- **Strongest alternative diagnosis:** [...]
- **Strongest alternative solution:** [...]
- **Most fragile assumption:** [...]
- **Likely executive and cross-functional challenges:** [...]

## Part B — Reconcile

For each finding choose `ACCEPT — MAJOR`, `ACCEPT — MINOR`, `MITIGATED`, `REJECT`, or `WAIVED BY USER`.

Choose one recommendation status:

- **KEEP** — no material change;
- **REFINE** — recommendation remains, with targeted revision;
- **SWITCH** — choose a different solution;
- **REFRAME** — the decision or diagnosis must change.

Route accepted issues to the earliest module capable of fixing them. Do not preserve the original answer merely for consistency.

### Reconciliation output

| ID | Severity | Finding | Resolution | Required change or residual risk |
|---|---|---|---|---|
| | | | | |

Then provide:

- recommendation status;
- reconciled recommendation and core reasoning;
- strongest alternative and what it does better;
- final trade-off;
- final NOW / NEXT / NOT DOING;
- final metrics, guardrails, and decision rules;
- implementation, solution, and diagnosis reconsideration conditions;
- remaining uncertainty and waived residual risk;
- recommended reruns;
- DECISION DEFENSE questions and responses.

### Decision defense format

For each likely challenge:

- **Question:** [...]
- **Best response:** [...]
- **Evidence:** [...]
- **What we acknowledge or concede:** [...]

## Reruns and waivers

End with open rerun directives and the available human choices:

```text
ACCEPT RERUNS
WAIVE <FINDING_IDS>
WAIVE ALL AND PROCEED
```

Waived findings retain their original severity and become explicit residual risk. Follow [`../core/APPROVALS_AND_RERUNS.md`](../core/APPROVALS_AND_RERUNS.md).

## Executive view

Show the verdict, most important findings, recommendation status, revised decision, open reruns or waivers, and judgments requiring review.

## Approval handoff

```text
CRITIQUE_RECONCILE vX — APPROVED
Based on: FRAME vX + ANALYZE vX + DIAGNOSE vX + SOLUTIONS_DECIDE vX + EXECUTION_VALIDATE vX
Recommendation status: KEEP | REFINE | SWITCH | REFRAME
Final recommendation: ...
Core reasoning: ...
Strongest alternative: ...
Trade-off: ...
Final plan and validation: ...
Waived findings / residual risks: ...
Top decision-defense risks: ...
```

## Quality gate

- Does each conclusion follow from its inputs?
- Were the strongest competing diagnosis and solution steelmanned?
- Are finding severity and resolution kept separate?
- Are reruns routed to the earliest responsible module?
- Are waived risks still visible?
- Can the recommendation survive evidence, trade-off, execution, and reversal questions without contradiction?
