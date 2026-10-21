# State Model

## Canonical source of truth

The canonical state is the sole authority for:

- the active product brief;
- module versions, statuses, and dependency basis;
- complete approved module outputs;
- critique findings, rerun directives, and waivers;
- change history;
- current decision, trade-off, assumptions, and reconsideration logic.

Chat history, memory, slide decks, notes, and derived artifacts are not canonical unless their contents are approved and written back to the canonical state.

## Allowed statuses

| Status | Meaning | Valid downstream input? |
|---|---|---|
| NOT RUN | No approved output exists for the current decision. | No |
| DRAFT | Work is under review and is not canonical. | No |
| APPROVED | A human accepted this version as the active source of truth. | Yes |
| STALE | The output exists, but at least one approved upstream input changed. | No |
| FINAL | The current communication artifact is approved for use. | Yes, as an artifact only |

`DRAFT` may be tracked in working metadata, but draft content must not replace the active approved output.

## State invariants

1. There is exactly one active canonical version of each module.
2. Only explicit human approval can create a new approved version.
3. Every approved module identifies its exact upstream versions.
4. No module can be approved from stale or unverified inputs.
5. An approved upstream change immediately invalidates existing dependent outputs.
6. A module that never ran remains `NOT RUN`; it does not become `STALE`.
7. Old complete versions are not kept in active sections. Use version history or an archive plus a concise change log.
8. Waived findings retain their severity, evidence, recommended action, and residual risk.
9. Final communication is derived from approved reasoning; it does not become a new source of analytical truth.

## State transitions

```text
NOT RUN ──RUN──> DRAFT ──APPROVE──> APPROVED
                     │
                     └──REVISE──> DRAFT

APPROVED ──UPSTREAM CHANGE──> STALE ──RERUN──> DRAFT

COMMUNICATE DRAFT ──APPROVE──> FINAL
FINAL ──UPSTREAM CHANGE──> STALE
```

Approval does not promote downstream modules automatically. A rerun creates a new draft against the latest approved inputs.

## Read and write protocol

Before a write:

- read current state;
- confirm target section and expected version;
- confirm required dependencies and their versions;
- reject concurrent or inconsistent changes.

After a write:

- re-read the changed state and complete target section;
- verify status, version, `Based on`, content, stale propagation, and change-log entry;
- report the write as successful only if readback matches intent.

## Fail-closed conditions

Stop with a clear error when:

- canonical state is unavailable or ambiguous;
- a required SOP cannot be loaded;
- an upstream dependency is missing, draft, stale, or based on a different version;
- required data cannot be accessed or its meaning cannot be established;
- a write cannot be verified;
- resolving a conflict would require inventing facts or silently selecting a version.

Suggested messages:

```text
CANONICAL STATE UNAVAILABLE
MODULE SOP UNAVAILABLE: <path>
DEPENDENCY INVALID: <module> requires <expected>, found <actual>
WRITE NOT VERIFIED: no canonical change was claimed
```

## Concurrency

If more than one person or agent can edit state, use document versioning, locks, or compare-and-swap semantics. A writer must abort if the canonical state changed after it was read. Parallel analysis is acceptable; parallel canonical approval writes are not.
