# Product Decision OS

**Turn an ambiguous product problem into a decision you can explain, test, and revisit—with AI as your thinking partner.**

Product Decision OS is a seven-stage workflow for product managers, founders, and teams. It helps you define the decision, understand the evidence, diagnose the problem, compare approaches, choose what to build first, and decide what success would look like. You review and approve each stage before the next one uses it.

You start with a product question, available evidence, and constraints. You finish with a recommendation, its strongest alternative, a concrete first move, a validation plan, and a memo or presentation your team can act on.

**[How it works](#how-it-solves-a-product-problem) · [Why use it](#what-makes-this-workflow-useful) · [Get started](#start-here-run-your-first-product-decision) · [Worked example](examples/ai-feature-launch/README.md)**

## The problem it helps solve

“Should we launch this feature?” usually contains several unanswered questions: Who needs it? What is preventing a better outcome? Does the evidence support our explanation? What else could we do? How would we know our choice worked?

Those questions are easy to skip when an AI assistant can produce a convincing recommendation immediately. They are also easy to lose across long conversations: assumptions become facts, earlier decisions disappear, and an updated analysis never reaches the final plan.

Product Decision OS gives each question a place in the process and keeps a record of what you approved. The final recommendation remains connected to the evidence and judgments behind it.

## What you get

- **A clearly framed decision:** the user, desired outcome, metric, scope, and constraints.
- **An evidence-backed explanation:** what is happening, what may explain it, and what remains uncertain.
- **A real choice:** a recommended approach, a credible runner-up, and the benefit you are choosing to give up.
- **A testable execution plan:** MVP scope, NOW / NEXT / NOT DOING, success measures, guardrails, and actions to take when results arrive.
- **A communication artifact:** a decision memo, roadmap recommendation, PRD direction, experiment brief, or executive presentation.
- **A decision record:** approved versions, source references, unresolved risks, and conditions that would change your mind.

This repository contains Markdown instructions, prompts, templates, a quality rubric, and a fictional example. It is a workflow kit: your assistant and connected storage carry out its commands. There is no application to install, and GitHub itself does not execute the workflow.

## How it solves a product problem

Each stage answers one question and produces the input for the next. The starting point is a **PRODUCT BRIEF** containing your question, context, evidence, and constraints.

| Stage | Question | What you review before moving on |
|---|---|---|
| **1. [FRAME](modules/01_FRAME.md)** | What decision are we making, and for whom? | Objective, primary outcome metric, user, scope, constraints, and assumptions. |
| **2. [ANALYZE](modules/02_ANALYZE.md)** | What does the evidence actually establish? | Calculations, relevant segments, qualitative findings, contradictions, and missing data. |
| **3. [DIAGNOSE](modules/03_DIAGNOSE.md)** | What problem should we solve? | Leading explanation, competing explanations, confidence, and evidence that would disprove it. |
| **4. [SOLUTIONS + DECIDE](modules/04_SOLUTIONS_DECIDE.md)** | Which approach should come first? | Distinct alternatives, comparison criteria, chosen approach, strongest alternative, and trade-off. |
| **5. [EXECUTION + VALIDATE](modules/05_EXECUTION_VALIDATE.md)** | What do we build first, and how will we learn? | Product mechanism, MVP, sequencing, metrics, guardrails, and decision rules. |
| **6. [CRITIQUE + RECONCILE](modules/06_CRITIQUE_RECONCILE.md)** | Does the recommendation survive a serious challenge? | Weak claims, necessary revisions, targeted reruns, and explicitly accepted risks. |
| **7. [COMMUNICATE](modules/07_COMMUNICATE.md)** | How do we help others understand and act? | A recommendation-first artifact, supporting evidence, and DECISION DEFENSE. |

The review loop is the same at every stage:

```text
Run one stage → Review the draft → Request revisions → Approve → Continue
```

### A concrete example: should we build an AI insight summary?

Imagine a product team whose customers spend time comparing dashboards but still struggle to decide what to do next. The team is considering an AI-generated weekly summary.

1. **Frame:** Decide whether to invest a quarter in a constrained MVP. Define the desired outcome as useful customer action, rather than summary views.
2. **Analyze:** Examine usage data, research, and support feedback. Separate evidence of interpretation difficulty from evidence of actual follow-up behavior.
3. **Diagnose:** Test whether the main problem is interpreting scattered information. Keep a competing explanation visible: users may understand the data but lack the authority to act.
4. **Choose:** Compare AI summaries, fixed-rule alerts, and analyst-led guidance. Explain why one comes first and what the runner-up does better.
5. **Plan and validate:** Define a limited MVP with source citations, a target segment, action signals, and quality guardrails. Specify when to expand, iterate, or stop.
6. **Challenge:** Check whether the team can actually measure follow-up actions. If instrumentation is inadequate, revisit the validation plan before relying on its results.
7. **Communicate:** Present the recommendation, evidence limits, trade-off, MVP, and reversal conditions in one coherent story.

This is an illustrative path, not evidence that AI summaries are the right answer. [Read the full fictional example →](examples/ai-feature-launch/README.md)

## What makes this workflow useful

### One shared record keeps the work connected

The **canonical state** is a document or file holding the product brief, complete approved outputs, versions, and open issues. Every stage reads this record. You can change conversations or collaborators without manually reconstructing the decision from chat history.

### Your approval controls what becomes an input

`RUN` produces a draft. You challenge it, request changes, and explicitly `APPROVE` it. Only then can downstream stages use it. The assistant records the exact versions used and reads back each saved change before claiming success.

### Changed evidence makes outdated work visible

Suppose a corrected denominator changes the analysis. Approving `ANALYZE v2` marks existing diagnosis, solution, execution, critique, and communication outputs `STALE`. They must be reviewed again against the updated evidence. An old presentation cannot silently remain the current answer.

These are operating rules the assistant must follow; this repository does not include a background service that enforces them.

### Evidence and uncertainty stay distinguishable

Facts, calculations, estimates, assumptions, inferences, and hypotheses have separate labels. The workflow asks what evidence does **not** establish, what else could explain the pattern, and what would change the diagnosis. Missing data stays missing.

### A recommendation includes a meaningful sacrifice

The decision must name the strongest alternative, what it does better, and why it still loses. Execution then connects the chosen approach to user behavior and a business outcome, with distinct responses to implementation problems, solution failure, and a wrong diagnosis.

### Critique leads to a specific next action

Findings receive stable IDs and route back to the earliest stage that can correct them. You can explicitly accept an unresolved concern through a **waiver**; its severity and residual risk remain visible. Unverifiable state or missing required inputs stop the workflow instead of inviting guesses.

### Deep review becomes clear communication

Each draft includes an **EXECUTIVE VIEW** for the central argument and a **FULL REVIEW** for inspecting evidence and reasoning. The complete approved output is saved. Final communication reorganizes it around the audience's decision, with a **DECISION DEFENSE** covering likely questions, evidence, and limitations.

## When to use it

Use the workflow when the cost of a weak decision warrants deliberate review: prioritizing a feature, diagnosing an activation or retention problem, choosing a product strategy, evaluating pricing or packaging, or planning an AI product launch.

It works best when a person owns the decision, relevant evidence is accessible, and the team can act on what it learns. Scale the depth of each stage to the stakes. A small, easily reversible choice may need only a lightweight discussion.

## Start here: run your first product decision

Download or clone this repository and make its instructions available to your assistant. The assistant needs to read the `core/` rules and relevant module files, access your evidence, and read and write your chosen state document. The workflow stops when required state cannot be verified.

Keep real customer data, internal research, and approved decision records in an appropriately private workspace; this public repository provides reusable templates.

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

Initialize once for a new decision. To resume existing work, use `STATUS` or `WHAT NEXT?`; initialization clears active module outputs.

### Step 4 — Run and approve each module

Use [`prompts/module-bootstrap.md`](prompts/module-bootstrap.md) with the relevant module SOP. Run the modules in this order:

For the first run, replace the prompt's placeholders with `FRAME`, `modules/01_FRAME.md`, and your canonical-state location. Update the module and SOP for each later run. You can use one conversation or separate module conversations; all must read the same canonical state.

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

Send each approval only after reviewing that stage's output. If using separate conversations, perform approval in the one that has the complete reviewed draft and write access to the shared state. The assistant retrieves approved upstream work from that record; you do not need to paste earlier outputs or remember their versions.

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

Then run and approve the affected stages in dependency order. Accepting a rerun plan does not automatically execute or approve those stages.

To accept a known residual risk without rerunning:

```text
WAIVE C2
```

or:

```text
WAIVE ALL AND PROCEED
```

A waiver removes the workflow block; it does not resolve the concern. The original finding and severity remain in canonical state and must appear as residual risk in later work.

A waiver cannot make unavailable state or unverified evidence valid, or make an already stale dependency current.

### Step 7 — Produce the final artifact

Run COMMUNICATE only after every required upstream module is current and approved and every rerun directive is completed or explicitly waived.

Choose the artifact that fits the decision: a decision memo, PRD direction, roadmap recommendation, experiment brief, or executive presentation. The final artifact should lead with the recommendation and hide the internal module structure.

For example:

```text
RUN COMMUNICATE
Create a decision memo for the product and engineering leads.
Make the recommendation, strongest alternative, trade-off, MVP,
validation plan, and unresolved risks easy to find.
```

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

## License

MIT. See [`LICENSE`](LICENSE).
