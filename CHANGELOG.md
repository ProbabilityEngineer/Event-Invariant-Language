# Changelog — Event–Invariant Language (EIL)

This changelog records **substantive changes and clarifications** to the EIL specification.
Patch releases indicate clarification-only updates with no grammar or semantic changes.

---

## v1.3.1 — Verification Clarification (Current)

**Type:** Clarification-only (no grammar changes)

### Added / Clarified
- Named **Verification** as a first-class EIL use mode alongside Alignment and Execution Handoff.
- Documented **reverse prompts** as the primary technique for Verification:
  - checking for intent drift
  - detecting missing or weakened invariants
  - validating implementations against original constraints.
- README updated with a small inline Verification example.

### Unchanged
- Core grammar
- Field semantics
- Extension rules

---

## v1.3 — Procedural Invariant Boundary

**Type:** Clarification and boundary definition

### Added
- **Procedural Invariant Rule**:
  - Procedures MAY be included inline when violating them would violate an invariant.
  - Procedures SHOULD remain external when multiple algorithms satisfy the same invariants.
- Explicit guidance distinguishing:
  - invariant facts
  - invariant-bearing procedural properties
  - implementation-specific procedure.
- Formalized **permissible scoped extensions** (e.g. `[acceptance]`, `[implementation]`).

### Improved
- Resolved ambiguity between intent-only use and execution-handoff use.
- Clarified that EIL is a **specification, not a framework**.

---

## v1.2 — Misunderstanding Resolution

**Type:** Clarification and robustness

### Added
- Appendix describing **classes of common EIL misunderstandings**.
- A **misunderstanding checklist** to aid correct usage.
- Explicit guidance on intended-use framing (alignment vs execution handoff).

### Improved
- Clearer separation between:
  - intent preservation
  - algorithm specification
  - implementation detail.

---

## v1.1 — Acknowledgment and Interpretation

**Type:** Clarification

### Added
- Guidance on **acknowledgment**:
  - how receivers (human or AI) signal understanding of invariants.
- Clarified expectations around invariant preservation across paraphrase and handoff.

---

## v1.0 — Initial Public Specification

**Type:** Initial release

### Introduced
- Core EIL grammar:
  - ⟦event⟧
  - ⟦agent⟧
  - ⟦intent⟧
  - ⟦invariants⟧
  - ⟦closure⟧
- Optional fields and graceful degradation model.
- Intent-preservation as the central design goal.
- Explicit non-goals:
  - not a programming language
  - not a framework
  - not a model-internal representation.

---

## Versioning Notes

- **Minor versions (v1.x)** may add clarifications, rules, and guidance.
- **Patch versions (v1.x.y)** indicate documentation or interpretation clarifications only.
- Grammar-breaking changes would require **v2.0**.

---

> Compression across versions reflects increasing clarity, not loss of meaning.
