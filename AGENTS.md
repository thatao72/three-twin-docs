# ThreeTwinDocs Agent Guidance

This repository publishes explanatory documentation for ThreeTwinArchitectureNext.

## Source of truth

- Treat `thatao72/three-twin-architecture-next` current architecture authority as the source of truth for architecture semantics.
- Documentation in this repository is explanatory and must not create new product or architecture authority.
- Prefer durable conceptual responsibilities over issue-local, PR-local, implementation-local, or historical correction language.

## Documentation style

- Write for a reader who has not participated in design discussions.
- Explain the architecture affirmatively from first principles before presenting constraints or edge cases.
- Avoid framing durable architecture as a sequence of corrections such as “X is not Y; instead it is Z” unless the distinction is intrinsically necessary for comprehension.
- Do not give disproportionate emphasis to a point merely because it was previously debated or corrected.
- Separate conceptual architecture, mathematical realization, persistence, and implementation traceability so current implementation details do not define the conceptual model.
- Preserve technically important invariants, but place implementation-specific or misconception-prevention detail after the primary explanation.

## Current documentation structure

`content/architecture.md` should proceed broadly from:

1. enduring architecture principle,
2. Three Twin responsibilities,
3. reasoning / evidence / persistent-state separation,
4. learner feedback loop,
5. mathematical observation model,
6. canonical execution flow,
7. persistence and implementation traceability.

When ThreeTwinArchitectureNext changes materially, validate this document against current architecture authority before updating explanatory wording.
