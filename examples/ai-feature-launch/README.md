# Example: AI Feature Launch

This fictional example shows how state and decisions move through Product Decision OS. The numbers are illustrative and are not benchmarks.

## Product brief

Northstar Analytics is considering an AI-generated weekly insight summary for team leads. Research suggests that some team leads struggle to identify meaningful changes across dashboards, but the company does not yet know whether summaries will improve decision-making or merely increase passive reading. The team must decide whether to invest one quarter in an MVP for existing mid-market customers.

Available evidence:

- product event data for dashboard visits and saved reports;
- twelve recent customer research sessions;
- support tickets tagged `report interpretation`;
- no causal evidence that summaries improve downstream action;
- a one-quarter, two-engineer constraint.

## State snapshot

```text
PRODUCT_BRIEF: v1 | APPROVED
FRAME: v1 | APPROVED | Based on: PRODUCT_BRIEF v1
ANALYZE: v1 | APPROVED | Based on: FRAME v1
DIAGNOSE: v1 | APPROVED | Based on: FRAME v1 + ANALYZE v1
SOLUTIONS_DECIDE: v1 | APPROVED | Based on: FRAME v1 + ANALYZE v1 + DIAGNOSE v1
EXECUTION_VALIDATE: v1 | APPROVED | Based on: FRAME v1 + ANALYZE v1 + DIAGNOSE v1 + SOLUTIONS_DECIDE v1
CRITIQUE_RECONCILE: v1 | APPROVED | Based on: FRAME v1 + ANALYZE v1 + DIAGNOSE v1 + SOLUTIONS_DECIDE v1 + EXECUTION_VALIDATE v1
COMMUNICATE: v1 | FINAL | Based on all v1 upstream modules
```

## 1. Frame

- **Decision:** Should Northstar build and test an AI weekly insight summary for existing mid-market team leads this quarter?
- **Objective:** Improve the rate at which team leads identify and act on meaningful account changes.
- **Primary outcome:** Percentage of eligible accounts taking a relevant follow-up action after a material change is surfaced.
- **Constraint:** Two engineers for one quarter; summaries must cite source metrics.
- **Highest-risk assumption:** Surfacing the change, rather than workflow authority or data trust, is the main barrier to action.

## 2. Analyze

- **GIVEN FACT:** Research participants reported spending time comparing dashboards manually.
- **CALCULATION:** Accounts using saved reports return more often, but the analysis does not establish that saved reports cause action.
- **QUALITATIVE EVIDENCE:** Several support tickets ask what changed, not only how to find a chart.
- **Tension:** High dashboard activity coexists with reported interpretation difficulty.
- **Gap:** The team cannot yet connect dashboard reading to a defined follow-up action.

## 3. Diagnose

- **Leading diagnosis:** For a subset of team leads, the bottleneck is converting scattered metric changes into a prioritized interpretation.
- **Confidence:** Medium; evidence is consistent but not causal or prevalence-establishing.
- **Strongest competitor:** Users understand the changes but lack authority or workflow capacity to act.
- **Falsifier:** If users can consistently identify the important change unaided but still do not act, interpretation is not the leading bottleneck.

## 4. Solutions + Decide

Credible approaches:

1. AI weekly summary with cited metric changes and suggested questions;
2. deterministic anomaly alerts for a small fixed metric set;
3. analyst-authored playbooks and office hours.

The team selects a constrained AI summary because it can synthesize across account-specific metrics while preserving source citations. Deterministic alerts are the strongest alternative: they are easier to inspect and safer, but cover fewer patterns.

> We are willing to give up some predictability and simplicity in exchange for broader account-specific synthesis, with citations and abstention as guardrails.

The choice reverses if evaluation shows that a small fixed rule set covers most valuable changes.

## 5. Execution + Validate

- **NOW:** Weekly summaries for one customer segment, limited to supported metrics, with source links, feedback controls, and abstention on low-confidence synthesis.
- **NEXT:** Add configurable priorities only if users understand the summary and take relevant actions.
- **NOT DOING:** Free-form chat, automated actions, and organization-wide rollout.
- **Leading signal:** Eligible accounts opening a cited source and recording a relevant follow-up action.
- **Guardrails:** Unsupported-claim rate, user correction rate, opt-out rate, and time-to-review.
- **Decision rule:** If summaries are read but do not change source inspection or follow-up actions, reconsider the product approach rather than merely rewriting the prose.

## 6. Critique + Reconcile

Finding `C1 — MATERIAL`: the follow-up action event is not consistently instrumented. The team accepts a targeted EXECUTION + VALIDATE rerun, adds the event definition, and approves v2. This makes the prior CRITIQUE + RECONCILE and COMMUNICATE outputs stale.

```text
EXECUTION_VALIDATE: v2 | APPROVED
CRITIQUE_RECONCILE: v1 | STALE
COMMUNICATE: v1 | STALE
```

After rerunning critique against v2, the recommendation is `REFINE`: keep the MVP, but treat action logging quality as an explicit launch prerequisite.

## 7. Communicate

The executive view leads with the constrained experiment, not with the seven internal modules. It shows the user problem, evidence limits, why the AI summary beats fixed alerts for this test, the safety trade-off, MVP boundaries, and the three change-of-course conditions.

The DECISION DEFENSE includes:

- Why AI instead of deterministic rules?
- What evidence would show interpretation is not the real bottleneck?
- How will unsupported summaries be detected?
- Why exclude automated actions?
- What result would justify stopping after the MVP?

## What this example demonstrates

- evidence is not upgraded into causality;
- the strongest alternative remains visible;
- an execution defect triggers a targeted rerun rather than a full restart;
- stale propagation prevents an old executive artifact from surviving a changed validation plan;
- the final communication hides workflow mechanics while preserving decision traceability.
