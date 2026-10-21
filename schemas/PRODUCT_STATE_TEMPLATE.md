# Canonical Product Decision State

Only the latest approved module outputs belong in active sections. Drafts are reviewed outside these sections. Stale outputs remain visible but cannot be used downstream.

## Decision metadata

- **Decision name:** [...]
- **Owner:** [...]
- **Opened:** [...]
- **Decision deadline:** [...]
- **Canonical location:** [...]

<!-- PRODUCT_STATE_START -->
## Current state

```text
PRODUCT_BRIEF: v1 | APPROVED

FRAME: v0 | NOT RUN | Based on: PRODUCT_BRIEF v1
ANALYZE: v0 | NOT RUN | Based on: FRAME v0
DIAGNOSE: v0 | NOT RUN | Based on: FRAME v0 + ANALYZE v0
SOLUTIONS_DECIDE: v0 | NOT RUN | Based on: FRAME v0 + ANALYZE v0 + DIAGNOSE v0
EXECUTION_VALIDATE: v0 | NOT RUN | Based on: FRAME v0 + ANALYZE v0 + DIAGNOSE v0 + SOLUTIONS_DECIDE v0
CRITIQUE_RECONCILE: v0 | NOT RUN | Based on: FRAME v0 + ANALYZE v0 + DIAGNOSE v0 + SOLUTIONS_DECIDE v0 + EXECUTION_VALIDATE v0
COMMUNICATE: v0 | NOT RUN | Based on: FRAME v0 + ANALYZE v0 + DIAGNOSE v0 + SOLUTIONS_DECIDE v0 + EXECUTION_VALIDATE v0 + CRITIQUE_RECONCILE v0
```

Allowed statuses: `NOT RUN`, `DRAFT`, `APPROVED`, `STALE`, `FINAL`.
<!-- PRODUCT_STATE_END -->

<!-- PRODUCT_BRIEF_START -->
## Product Brief — Canonical Input

- **Status:** APPROVED
- **Version:** v1
- **Original brief:** [...]
- **Provided facts and data:** [...]
- **Constraints:** [...]
- **Files and references:** [...]
<!-- PRODUCT_BRIEF_END -->

<!-- FRAME_START -->
## 1. Frame — Canonical Approved Output

- **Status / version:** [...]
- **Based on:** PRODUCT_BRIEF [...]
- **Decision:** [...]
- **Objective:** [...]
- **Primary outcome metric:** [...]
- **Primary user / stakeholder:** [...]
- **Scope and horizon:** [...]
- **Constraints:** [...]
- **Material assumptions:** [...]
- **Decision-critical unknowns:** [...]
<!-- FRAME_END -->

<!-- ANALYZE_START -->
## 2. Analyze — Canonical Approved Output

- **Status / version:** [...]
- **Based on:** FRAME [...]
- **Analytical questions and model:** [...]
- **Calculations:** [...]
- **Key evidence:** [...]
- **Interpretations:** [...]
- **Does not establish:** [...]
- **Segmentation / concentration:** [...]
- **Contradictions:** [...]
- **Decision-critical gaps:** [...]
<!-- ANALYZE_END -->

<!-- DIAGNOSE_START -->
## 3. Diagnose — Canonical Approved Output

- **Status / version:** [...]
- **Based on:** FRAME [...] + ANALYZE [...]
- **Problem area / tension:** [...]
- **Competing hypotheses:** [...]
- **Leading diagnosis:** [...]
- **Confidence:** [...]
- **Strongest competing explanation:** [...]
- **Prediction:** [...]
- **Falsifier:** [...]
- **Decision-critical uncertainty:** [...]
<!-- DIAGNOSE_END -->

<!-- SOLUTIONS_DECIDE_START -->
## 4. Solutions + Decide — Canonical Approved Output

- **Status / version:** [...]
- **Based on:** FRAME [...] + ANALYZE [...] + DIAGNOSE [...]
- **Solution altitude:** [...]
- **Credible approaches:** [...]
- **Comparison method and criteria:** [...]
- **Chosen approach:** [...]
- **Why it wins:** [...]
- **Strongest alternative:** [...]
- **What it does better / why it loses:** [...]
- **Trade-off:** [...]
- **First bet / consciously not pursuing:** [...]
- **Decision sensitivity:** [...]
<!-- SOLUTIONS_DECIDE_END -->

<!-- EXECUTION_VALIDATE_START -->
## 5. Execution + Validate — Canonical Approved Output

- **Status / version:** [...]
- **Based on:** FRAME [...] + ANALYZE [...] + DIAGNOSE [...] + SOLUTIONS_DECIDE [...]
- **Chosen approach and mechanism:** [...]
- **Solution hypothesis:** [...]
- **Technology role:** [...]
- **NOW / MVP:** [...]
- **NEXT:** [...]
- **NOT DOING / NOT YET:** [...]
- **Ultimate outcome / leading signal / diagnostics / guardrails:** [...]
- **Decision rules:** [...]
- **Execution trade-offs and risks:** [...]
- **Implementation iterate condition:** [...]
- **Product-solution reconsideration condition:** [...]
- **Diagnosis / strategy reconsideration condition:** [...]
<!-- EXECUTION_VALIDATE_END -->

<!-- CRITIQUE_RECONCILE_START -->
## 6. Critique + Reconcile — Canonical Approved Output

- **Status / version:** [...]
- **Based on:** FRAME [...] + ANALYZE [...] + DIAGNOSE [...] + SOLUTIONS_DECIDE [...] + EXECUTION_VALIDATE [...]
- **Overall verdict:** [...]
- **Findings and resolutions:** [...]
- **Recommendation status:** KEEP / REFINE / SWITCH / REFRAME
- **Final recommendation and reasoning:** [...]
- **Strongest alternative / what it does better:** [...]
- **Final trade-off:** [...]
- **Final plan and validation:** [...]
- **Remaining uncertainty:** [...]
- **Waived findings / residual risks:** [...]
- **Decision defense:** [...]
<!-- CRITIQUE_RECONCILE_END -->

<!-- COMMUNICATE_START -->
## 7. Communicate — Final Artifact State

- **Status / version:** [...]
- **Based on latest approved upstream versions:** [...]
- **Audience / decision requested:** [...]
- **Artifact:** [...]
- **Executive view:** [...]
- **Supporting appendix:** [...]
- **Notes:** [...]
- **Decision defense:** [...]
- **Residual waived risks disclosed:** [...]
<!-- COMMUNICATE_END -->

<!-- RERUN_WAIVER_START -->
## Rerun Directives and Waivers

| Finding ID | Severity | Earliest module | Recommended action | Status | Waived by / at | Residual risk |
|---|---|---|---|---|---|---|
| | | | | OPEN / COMPLETED / WAIVED | | |
<!-- RERUN_WAIVER_END -->

<!-- CHANGE_LOG_START -->
## Change Log

| Timestamp | Module | Old → new | Reason | Approved by | Basis | Marked stale | Finding / waiver IDs |
|---|---|---|---|---|---|---|---|
| | | | | | | | |
<!-- CHANGE_LOG_END -->

## Current decision summary

- **Recommendation:** [...]
- **Highest-risk assumption:** [...]
- **Strongest alternative:** [...]
- **Trade-off:** [...]
- **Implementation iterate if:** [...]
- **Reconsider the solution if:** [...]
- **Reconsider the diagnosis / strategy if:** [...]

## Ready to communicate?

- [ ] FRAME approved
- [ ] ANALYZE approved
- [ ] DIAGNOSE approved
- [ ] SOLUTIONS + DECIDE approved
- [ ] EXECUTION + VALIDATE approved
- [ ] CRITIQUE + RECONCILE approved
- [ ] No required non-waived dependency is stale
- [ ] Open rerun directives are completed or explicitly waived
- [ ] Strongest alternative and trade-off are explicit
- [ ] NOW / NEXT / NOT DOING is explicit
- [ ] Three reconsideration levels are actionable
- [ ] Assumptions are consolidated
- [ ] Waived findings remain visible as residual risk
- [ ] Decision-defense vulnerabilities are understood
