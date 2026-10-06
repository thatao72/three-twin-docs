# ThreeTwinDocs Agent Guidance

This repository publishes explanatory documentation for ThreeTwin.

## Source of truth

- Treat `thatao72/three-twin-architecture-next` current architecture authority as the source of truth for architecture semantics.
- Documentation in this repository is explanatory and must not create new product or architecture authority.
- Prefer durable conceptual responsibilities over issue-local, PR-local, implementation-local, or historical correction language.

## Architecture publication model

Architecture documentation has two publication surfaces:

- `content/architecture/overview.md` — first-principles Web explanation for readers new to the architecture.
- `content/architecture/white-paper.md` — technical due-diligence treatment of the formal model, bounded implementation, compatibility boundaries, and validation status.

Both surfaces consume the shared claim registry:

- `content/architecture/claims.yaml`

The claim registry is a publication-control artifact, not architecture authority. It records the claims currently made by the docs, their layer, their ArchitectureNext authority sources, and the reviewed source commit.

Do not introduce a separate narrative authority unless explicitly required later.

## Three documentation layers

Keep these layers distinct:

1. **Conceptual** — durable responsibilities and first-principles explanation.
2. **Mathematical** — formal semantic objects, fields, maps, and invariants.
3. **Implementation** — current bounded realization, compatibility, maturity, and traceability.

Implementation topology must not define the conceptual architecture.

## Documentation style

- Write for a reader who has not participated in design discussions.
- Explain affirmatively from first principles before presenting formal notation, constraints, migration detail, or edge cases.
- Do not narrate architecture history unless history is necessary to explain a current compatibility boundary.
- Do not give disproportionate emphasis to a point merely because it was previously debated or corrected.
- Preserve technically important invariants while keeping implementation-specific detail out of the Web overview unless it materially changes understanding.
- Prefer Concept → intuition → example → formalization.
- Keep Web and White Paper semantically consistent without requiring identical wording.

## Architecture update workflow

When ThreeTwinArchitectureNext changes materially:

1. Read current bootstrap/authority rather than extrapolating from prior docs.
2. Compare ArchitectureNext main with the `source_checkpoint.reviewed_commit` in `claims.yaml`.
3. Identify which registered claims are affected by the semantic diff.
4. Add, revise, retire, or reclassify claims before editing publication prose.
5. Update only the Web/White Paper sections that consume affected claims.
6. Recheck conceptual, mathematical, and implementation layers for cross-layer contradiction.
7. Advance the reviewed source checkpoint only after semantic review is complete.

A source commit difference alone does not imply that publication prose must change. Implementation-only changes may require only review and checkpoint advancement.

## Current architecture Web story

The Web overview should broadly proceed from:

1. personalization as justified inference,
2. learner response is not learner state,
3. exact observable learning coordinates,
4. assessment as measurement,
5. rich measurement before learner inference,
6. learner state,
7. why Three Twins,
8. decision before realization,
9. closed loop,
10. curriculum scaling,
11. measurement quality,
12. concept / mathematics / implementation boundary.

The White Paper may follow the same conceptual logic at greater formal depth and include current compatibility and implementation boundaries.
