# Versioning

## Version identity

Each approved output uses a positive integer version:

```text
FRAME: v3 | APPROVED | Based on: PRODUCT_BRIEF v1
ANALYZE: v2 | APPROVED | Based on: FRAME v3
```

`v0` means no approved version exists. Draft iterations do not increment the canonical version.

## Increment rule

Increment a module version only after explicit human approval. Editing language, correcting a calculation, changing a recommendation, or accepting a rerun all create a new version when approved.

Never:

- increment on `RUN`;
- overwrite an approved version without incrementing;
- reuse a version number for different content;
- infer approval from silence or continued discussion.

## Provenance

Every module header records all required upstream versions:

```text
SOLUTIONS_DECIDE: v2 | APPROVED
Based on: FRAME v2 + ANALYZE v3 + DIAGNOSE v1
Approved by: <name or role>
Approved at: <ISO-8601 timestamp>
```

Optional provenance fields include source-data snapshot, query version, research access date, repository commit, and artifact link.

## Change log

For each approved change record:

- timestamp;
- changed module;
- old and new versions;
- concise reason;
- approving human;
- exact basis;
- downstream modules marked stale;
- associated critique or waiver IDs.

The change log is an index, not a substitute for complete canonical output or external version history.

## Product brief changes

Treat any material change to the original problem, supplied facts, constraints, or decision scope as a new `PRODUCT_BRIEF` version. Preserve the original wording and separately record amendments. A material brief change makes every existing module stale.

## Artifact versions

`COMMUNICATE` can produce multiple formats from the same reasoning basis, such as a decision memo and an executive deck. Record each artifact and its source versions. Cosmetic re-exports need not change the reasoning version, but any substantive narrative or decision change requires review and a new approved `COMMUNICATE` version.

## Reproducibility

A reviewer should be able to answer:

1. What was approved?
2. Who approved it and when?
3. Which exact upstream versions and data supported it?
4. What changed from the prior version?
5. Which downstream outputs became invalid?
