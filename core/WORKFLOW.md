# Workflow

## Purpose

Product Decision OS turns a product brief into an evidence-backed, reviewable product decision. It is designed for sequential work with a human decision owner at every approval gate.

## Operating principles

1. **One canonical source of truth.** Current state, approved versions, provenance, waivers, and change history live in one durable record.
2. **Solve bottom-up; communicate top-down.** Internal work follows evidence to decision. Final communication starts with the recommendation.
3. **Match depth to decision complexity.** Use one meaningful solution-generation cycle by default. Add layers only when the decision genuinely has layers.
4. **Preserve uncertainty.** Name the strongest competing explanation, alternative solution, material assumption, and reversal condition.
5. **Require a real choice.** State what comes first, what the strongest alternative does better, why it loses, and what is deliberately given up.
6. **Make the recommendation falsifiable.** Separate implementation failure, solution failure, and diagnosis failure.
7. **Fail closed.** Stop when required state, evidence, or dependencies cannot be verified.

## Evidence vocabulary

| Label | Meaning |
|---|---|
| GIVEN FACT | Directly supplied in the product brief or approved source data. |
| EXTERNAL FACT | Verified from a cited external source. |
| CALCULATION | Derived mathematically from known facts. |
| ESTIMATE | Derived from facts plus explicit assumptions. |
| ASSUMPTION | Temporarily accepted but not established. |
| QUALITATIVE EVIDENCE | Research, feedback, observations, or other non-numeric evidence. |
| INFERENCE | An interpretation of evidence. |
| HYPOTHESIS | A testable explanation or prediction. |

Never present one category as another. Qualitative evidence can support a hypothesis but does not, by itself, establish prevalence. Correlation does not establish causation.

## Modules

| # | Module | Question answered | Canonical output |
|---|---|---|---|
| 1 | FRAME | What decision are we making? | Decision, objective, outcome metric, users, scope, constraints, assumptions. |
| 2 | ANALYZE | What does the evidence establish? | Decision-relevant findings, calculations, tensions, and gaps. |
| 3 | DIAGNOSE | What do we need to solve? | Leading diagnosis, competing explanations, confidence, prediction, falsifier. |
| 4 | SOLUTIONS + DECIDE | What should we do? | Credible alternatives, comparison, chosen first bet, trade-off, sensitivity. |
| 5 | EXECUTION + VALIDATE | What do we do first, and how will we learn? | Product mechanism, hypothesis, MVP, sequence, metrics, decision rules. |
| 6 | CRITIQUE + RECONCILE | Does the full decision chain hold? | Findings, resolutions, rerun directives, final reconciled decision, defense. |
| 7 | COMMUNICATE | How should the decision be understood and used? | Executive view, chosen artifact, appendix, notes, decision defense. |

## Initialize a product decision

On `INITIALIZE PRODUCT BRIEF`:

1. Read the current canonical state.
2. Store the original brief verbatim as `PRODUCT_BRIEF v1`.
3. Preserve supplied facts, constraints, files, links, and data references.
4. Do not analyze the brief.
5. Reset every module to `v0 | NOT RUN`.
6. Clear active module outputs while retaining section markers and change history.
7. Add a concise change-log entry.
8. Re-read the state and verify the write.
9. Return `NEXT → RUN FRAME`.

## Run a module

On `RUN <MODULE>`:

1. Load that module's SOP.
2. Read canonical state, the product brief, and complete approved outputs of every required upstream dependency.
3. Verify that versions match each dependency's `Based on` record.
4. Display a concise dependency check before substantive work.
5. Stop if an input is missing, `DRAFT`, `STALE`, inconsistent, or unverifiable.
6. Run only the requested module.
7. Return a `DRAFT`; do not write it into an approved canonical module section.
8. Present an `EXECUTIVE VIEW` followed by a `FULL REVIEW`.
9. Do not automatically run or approve the next module.

Suggested dependency check:

```text
DEPENDENCY CHECK
SOP: modules/03_DIAGNOSE.md — LOADED
PRODUCT BRIEF: v1 — APPROVED
FRAME: v2 — APPROVED
ANALYZE: v1 — APPROVED
```

## Review layers

Every module draft has two views:

- **EXECUTIVE VIEW** — the conclusion, minimum decisive evidence, important uncertainty, next implication, and specific judgments requiring human review.
- **FULL REVIEW** — complete reasoning, evidence traceability, alternatives, calculations, assumptions, and quality checks required by the SOP.

The executive view is not a substitute for the complete canonical output. Approval stores the full reviewed output.

## Approve a module

On explicit `APPROVE <MODULE>`:

1. Incorporate agreed revisions from the review.
2. Produce the complete final module output.
3. Increment that module's version by one.
4. Record exact upstream versions in `Based on`.
5. Replace the active canonical module section; do not compress it into a summary.
6. Update status and change log.
7. Mark every existing dependent downstream module `STALE`.
8. Leave modules that never ran as `NOT RUN`.
9. Re-read state and the saved module section.
10. Report success only after readback verification.

## Status and next action

`STATUS` reports the product brief version, every module's version/status/basis, active rerun directives, waivers, and the next valid action.

`WHAT NEXT?` selects the earliest `NOT RUN` or `STALE` module whose required dependencies are current and approved. It does not perform module work.

## Data and research

- Keep large raw data in its native file or warehouse; store references and decision-relevant findings in canonical state.
- Use computation for nontrivial calculations, funnels, cohorts, segmentation, sensitivity analysis, or charts.
- Verify numerator, denominator, comparison group, time window, and metric definition.
- Research only missing facts that could materially alter the decision.
- Preserve source citations and access dates for external facts.

## Completion

A product decision is ready for `COMMUNICATE` only when every required upstream module is `APPROVED`, no non-waived dependency is stale, the strongest alternative and trade-off are explicit, and reconsideration logic is actionable.
