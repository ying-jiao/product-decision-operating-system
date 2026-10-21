# Dependencies

## Graph

```text
PRODUCT BRIEF
  └─ FRAME
      └─ ANALYZE
          └─ DIAGNOSE
              └─ SOLUTIONS + DECIDE
                  └─ EXECUTION + VALIDATE
                      └─ CRITIQUE + RECONCILE
                          └─ COMMUNICATE
```

The direct graph is linear for workflow control, while each downstream module may read several earlier approved outputs to preserve traceability.

## Required inputs

| Module | Required approved inputs |
|---|---|
| FRAME | PRODUCT BRIEF |
| ANALYZE | FRAME |
| DIAGNOSE | FRAME, ANALYZE |
| SOLUTIONS + DECIDE | FRAME, ANALYZE, DIAGNOSE |
| EXECUTION + VALIDATE | FRAME, ANALYZE, DIAGNOSE, SOLUTIONS + DECIDE |
| CRITIQUE + RECONCILE | All modules through EXECUTION + VALIDATE |
| COMMUNICATE | All modules through CRITIQUE + RECONCILE |

Relevant raw data remains available to ANALYZE and any downstream module that needs to verify a claim. A downstream module must not rely on a summary when the complete approved output is required.

## Stale propagation matrix

When an approved module changes, mark every existing dependent output below it `STALE`:

| Changed module | Existing outputs made stale |
|---|---|
| PRODUCT BRIEF | FRAME through COMMUNICATE |
| FRAME | ANALYZE through COMMUNICATE |
| ANALYZE | DIAGNOSE through COMMUNICATE |
| DIAGNOSE | SOLUTIONS + DECIDE through COMMUNICATE |
| SOLUTIONS + DECIDE | EXECUTION + VALIDATE through COMMUNICATE |
| EXECUTION + VALIDATE | CRITIQUE + RECONCILE, COMMUNICATE |
| CRITIQUE + RECONCILE | COMMUNICATE |
| COMMUNICATE | No upstream output |

Do not delete stale work. Preserve its status and provenance until it is replaced, but never use it as input.

## Rerun scope

Route a discovered issue to the earliest module capable of correcting it:

| Issue | Earliest rerun |
|---|---|
| Wrong decision, outcome, user, scope, or constraint | FRAME |
| Evidence, calculation, denominator, baseline, segmentation, or data-quality error | ANALYZE |
| Causal explanation, bottleneck, or competing hypothesis error | DIAGNOSE |
| Missing alternative, wrong decision criteria, or wrong chosen solution | SOLUTIONS + DECIDE |
| Product mechanics, MVP, sequencing, metrics, decision rules, or execution risk | EXECUTION + VALIDATE |
| Story, audience, or artifact problem with sound underlying reasoning | COMMUNICATE |

Rerun from the earliest affected module forward. Do not rerun unrelated upstream modules.

## Dependency validation

Before a module starts, confirm for every required input:

- status is `APPROVED` or, where appropriate, `FINAL`;
- version matches the expected canonical version;
- downstream `Based on` declarations are internally consistent;
- no unresolved non-waived rerun directive blocks the module;
- complete content and required data references are accessible.

Any failed check stops the run.
