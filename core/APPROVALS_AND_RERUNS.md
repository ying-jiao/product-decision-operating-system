# Approvals and Reruns

## Human approval gate

AI may analyze, draft, challenge, and suggest. A named human decision owner approves canonical product decisions.

Approval must be explicit, for example:

```text
APPROVE DIAGNOSE
APPROVE SOLUTIONS + DECIDE WITH THE REVIEWED REVISIONS
```

Approval means the human accepts the complete output as the current basis for downstream work. It does not mean the conclusion is certain or permanent.

## Approval transaction

An approval is complete only when all of the following succeed:

1. integrate reviewed revisions;
2. validate dependencies again;
3. increment the version;
4. write the complete approved output and provenance;
5. propagate stale status to existing downstream work;
6. add a change-log entry;
7. re-read and verify the write.

If any step fails, do not claim approval was saved.

## Critique findings

Every actionable critique receives a stable ID such as `C1` and a severity:

- **BLOCKING** — materially undermines the recommendation, evidence, diagnosis, or decision chain.
- **MATERIAL** — the decision remains defensible, but the issue could meaningfully change confidence or quality.
- **ADVISORY** — useful improvement unlikely to change the core decision.

Severity and resolution are separate. Resolve each finding as:

- **ACCEPT — MAJOR** — changes framing, diagnosis, chosen solution, or recommendation;
- **ACCEPT — MINOR** — local correction;
- **MITIGATED** — valid and already addressed adequately;
- **REJECT** — not persuasive or not decision-relevant;
- **WAIVED BY USER** — intentionally accepted without the recommended correction.

## Rerun directive

Accepted findings route to the earliest module that can fix them. The directive records:

```text
Finding ID: C2
Severity: BLOCKING
Earliest affected module: ANALYZE
Reason: conversion rates use mismatched denominators
Required rerun path: ANALYZE → DIAGNOSE → SOLUTIONS + DECIDE → EXECUTION + VALIDATE → CRITIQUE + RECONCILE
Status: OPEN
```

The rerun path follows stale propagation. Unaffected upstream modules remain approved.

## Waivers

The human decision owner can use:

```text
WAIVE C2
WAIVE C2, C4
WAIVE ALL AND PROCEED
```

A waiver:

1. retains the original finding, severity, evidence, and recommended action;
2. records who waived it, when, and why if a rationale is supplied;
3. removes that finding as a workflow blocker;
4. does not label the concern fixed, mitigated, or rejected;
5. carries material residual risk into later modules and final communication;
6. becomes part of the decision defense and reconsideration logic.

A waiver cannot make unavailable canonical state available, verify an unverified write, or convert fabricated evidence into acceptable evidence. Those are operational integrity failures, and the workflow must remain closed.

## Proceeding after critique

If reruns are recommended, present:

```text
RECOMMENDED RERUNS
C1 — BLOCKING — DIAGNOSE — leading explanation conflicts with segment evidence
C3 — MATERIAL — EXECUTION + VALIDATE — guardrail has no decision rule

USER OPTIONS
ACCEPT RERUNS
WAIVE <IDS>
WAIVE ALL AND PROCEED
```

Proceed to `COMMUNICATE` only when all rerun directives are either completed and re-approved or explicitly waived, and all remaining dependencies are current.

## Local edits versus reruns

A local edit is appropriate when it clarifies language without changing a module's decision content or basis. If a correction changes evidence, diagnosis, selection criteria, recommendation, scope, metrics, or decision rules, rerun and reapprove the earliest affected module.

When uncertain, prefer the rerun. Hidden inconsistency costs more than a small amount of repeated work.
