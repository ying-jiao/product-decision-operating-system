# Product Decision OS

A versioned, human-in-the-loop workflow for making consequential product decisions with AI without losing context, mixing assumptions with facts, or allowing downstream work to depend silently on outdated reasoning.

Product Decision OS is not a prioritization framework or an autonomous product manager. It is a lightweight operating system for moving from an ambiguous product brief to a defensible decision and clear communication artifact.

## What it preserves

- one canonical source of truth;
- explicit module dependencies;
- versioned approvals and status tracking;
- automatic stale-state propagation;
- targeted reruns and explicit waivers;
- evidence, inference, and hypothesis separation;
- human approval between major decisions;
- fail-closed behavior when state cannot be verified;
- separation between internal reasoning and audience-facing communication.

## Workflow

```text
PRODUCT BRIEF
    ↓
FRAME
    ↓
ANALYZE
    ↓
DIAGNOSE
    ↓
SOLUTIONS + DECIDE
    ↓
EXECUTION + VALIDATE
    ↓
CRITIQUE + RECONCILE
    ↓
COMMUNICATE
```

The modules solve bottom-up but communicate top-down:

```text
Internal: Evidence → Interpretation → Diagnosis → Options → Decision → Execution → Validation
External: Recommendation → Reasons → Evidence → Trade-off → Plan → Decision rules
```

## Start here: run your first product decision

You need an AI assistant that can read and write the canonical state location you choose. The workflow will stop rather than rely on conversational memory when that state is unavailable.

### Step 1 — Create the canonical state

Make a working copy of [`schemas/PRODUCT_STATE_TEMPLATE.md`](schemas/PRODUCT_STATE_TEMPLATE.md) for the decision. Give it a durable location such as:

```text
decisions/weekly-insights/STATE.md
```

This file is the single source of truth for the brief, approved reasoning, versions, reruns, waivers, and final artifact. Do not use chat history as a substitute.

The canonical state can also live in a shared document or database. The storage technology is optional; the invariants in [`core/STATE_MODEL.md`](core/STATE_MODEL.md) are not.

### Step 2 — Write the product brief

Complete [`schemas/PRODUCT_BRIEF_TEMPLATE.md`](schemas/PRODUCT_BRIEF_TEMPLATE.md). Include the original request, known facts, available data, constraints, stakeholders, deadline, and desired output.

Do not diagnose the problem or propose solutions in this step.

### Step 3 — Initialize the workflow

Give your assistant [`prompts/control-room.md`](prompts/control-room.md), the canonical-state location, and the completed brief. Then send:

```text
INITIALIZE PRODUCT BRIEF
```

The assistant should store the brief verbatim as `PRODUCT_BRIEF v1`, reset every module to `v0 | NOT RUN`, verify the write, and return:

```text
NEXT → RUN FRAME
```

Confirm initialization with:

```text
STATUS
```

### Step 4 — Run and approve each module

Use [`prompts/module-bootstrap.md`](prompts/module-bootstrap.md) with the relevant module SOP. Run the modules in this order:

| Order | Draft command | SOP | Approval command |
|---:|---|---|---|
| 1 | `RUN FRAME` | [`modules/01_FRAME.md`](modules/01_FRAME.md) | `APPROVE FRAME` |
| 2 | `RUN ANALYZE` | [`modules/02_ANALYZE.md`](modules/02_ANALYZE.md) | `APPROVE ANALYZE` |
| 3 | `RUN DIAGNOSE` | [`modules/03_DIAGNOSE.md`](modules/03_DIAGNOSE.md) | `APPROVE DIAGNOSE` |
| 4 | `RUN SOLUTIONS + DECIDE` | [`modules/04_SOLUTIONS_DECIDE.md`](modules/04_SOLUTIONS_DECIDE.md) | `APPROVE SOLUTIONS + DECIDE` |
| 5 | `RUN EXECUTION + VALIDATE` | [`modules/05_EXECUTION_VALIDATE.md`](modules/05_EXECUTION_VALIDATE.md) | `APPROVE EXECUTION + VALIDATE` |
| 6 | `RUN CRITIQUE + RECONCILE` | [`modules/06_CRITIQUE_RECONCILE.md`](modules/06_CRITIQUE_RECONCILE.md) | `APPROVE CRITIQUE + RECONCILE` |
| 7 | `RUN COMMUNICATE` | [`modules/07_COMMUNICATE.md`](modules/07_COMMUNICATE.md) | `APPROVE COMMUNICATE` |

Every module follows the same review loop:

```text
RUN module
→ read EXECUTIVE VIEW
→ inspect FULL REVIEW
→ challenge assumptions and request revisions
→ approve explicitly when satisfied
→ verify the canonical write
→ move to the next module
```

`RUN` creates a draft and must not overwrite canonical approved work. `APPROVE` stores the complete reviewed output, increments that module's version, records its exact upstream basis, and verifies the write. Approval must never be inferred from silence.

For `COMMUNICATE`, approval sets the artifact to `FINAL` rather than merely `APPROVED`.

### Step 5 — Handle revisions correctly

Before approval, ask for changes normally and keep the module in `DRAFT`:

```text
Revise the primary metric to include the eligible-account denominator, then show the updated draft.
```

After approval, a material change creates a new version. For example, approving `ANALYZE v2` after changing `ANALYZE v1` makes existing DIAGNOSE through COMMUNICATE outputs `STALE`. Rerun from DIAGNOSE rather than continuing with old reasoning.

Use this check at any time:

```text
WHAT NEXT?
```

The control room should identify the earliest valid `NOT RUN` or `STALE` module without performing it automatically.

### Step 6 — Resolve critique findings

CRITIQUE + RECONCILE assigns stable IDs such as `C1` and recommends the earliest module that can fix each issue.

To follow the recommended reruns:

```text
ACCEPT RERUNS
```

To accept a known residual risk without rerunning:

```text
WAIVE C2
```

or:

```text
WAIVE ALL AND PROCEED
```

A waiver removes the workflow block; it does not resolve the concern. The original finding and severity remain in canonical state and must appear as residual risk in later work.

### Step 7 — Produce the final artifact

Run COMMUNICATE only after every required upstream module is current and approved and every rerun directive is completed or explicitly waived.

Choose the artifact that fits the decision: a decision memo, PRD direction, roadmap recommendation, experiment brief, or executive presentation. The final artifact should lead with the recommendation and hide the internal module structure.

After review, send:

```text
APPROVE COMMUNICATE
```

The expected end state is:

```text
COMMUNICATE: v1 | FINAL | Based on: latest approved upstream versions
```

For a compact worked example, see [`examples/ai-feature-launch/README.md`](examples/ai-feature-launch/README.md).

## What happens when something goes wrong?

| Situation | Required response |
|---|---|
| The assistant cannot read canonical state | Stop: `CANONICAL STATE UNAVAILABLE` |
| A required module is not approved | Stop and run or approve the missing dependency |
| An approved upstream module changes | Mark existing dependent outputs `STALE` |
| A calculation or diagnosis is wrong | Rerun from the earliest module that can fix it |
| The decision owner accepts an unresolved critique | Record an explicit waiver and carry the residual risk forward |
| A canonical write cannot be read back | Do not claim the save or approval succeeded |

## Core commands

```text
INITIALIZE PRODUCT BRIEF
STATUS
WHAT NEXT?
RUN <MODULE>
APPROVE <MODULE>
ACCEPT RERUNS
WAIVE <FINDING_IDS>
WAIVE ALL AND PROCEED
```

`RUN` produces a draft for review. `APPROVE` is the only action that increments a module version and replaces its canonical output. Major modules never run automatically.

## Repository map

- [`core/WORKFLOW.md`](core/WORKFLOW.md) — end-to-end operating protocol.
- [`core/STATE_MODEL.md`](core/STATE_MODEL.md) — canonical state and status invariants.
- [`core/DEPENDENCIES.md`](core/DEPENDENCIES.md) — dependency graph and stale propagation.
- [`core/VERSIONING.md`](core/VERSIONING.md) — version and provenance rules.
- [`core/APPROVALS_AND_RERUNS.md`](core/APPROVALS_AND_RERUNS.md) — review gates, critique routing, and waivers.
- [`modules/`](modules) — the seven module SOPs.
- [`schemas/`](schemas) — copyable product brief and canonical state templates.
- [`rubrics/PRODUCT_DECISION_QUALITY.md`](rubrics/PRODUCT_DECISION_QUALITY.md) — quality rubric.
- [`prompts/`](prompts) — portable control-room and module prompts.
- [`examples/ai-feature-launch/README.md`](examples/ai-feature-launch/README.md) — a compact fictional walkthrough.

## Non-negotiable rules

1. Separate facts, calculations, estimates, assumptions, qualitative evidence, inferences, and hypotheses.
2. Never invent missing data or precision.
3. Only `APPROVED` or `FINAL` outputs may be used downstream.
4. Every approved output records the exact upstream versions it used.
5. When an approved input changes, every existing dependent output becomes `STALE`.
6. A waiver removes a workflow block; it does not resolve the underlying concern.
7. If canonical state, required inputs, or version consistency cannot be verified, stop rather than guess.

## Scope

Use Product Decision OS for product strategy, roadmap choices, new feature bets, growth problems, retention issues, platform investments, pricing and packaging decisions, marketplace design, or AI product launches. Right-size the depth to the decision. Small reversible choices should not require heavyweight ceremony.

## License

MIT. See [`LICENSE`](LICENSE).
