# Verification Example — Detecting Intent Drift with EIL

This example demonstrates **Verification mode** in Event–Invariant Language (EIL) using a **reverse prompt**.
No new code is generated; the goal is to check whether intent and invariants were preserved.

---

## Original EIL (Execution Handoff)

```text
⟦use⟧: execution-handoff
⟦event⟧: feature.add
⟦agent⟧: sam
⟦object⟧: jpeg-structural-validator

⟦intent⟧:
  add pre-decode structural validation for JPEG
  detect malformed marker/segment structure deterministically

⟦invariants⟧:
  concurrency: unchanged
  ui: unchanged
  dependencies: none-added
  storage: none-added
  hashing: none-added

⟦closure⟧:
  missing-eoi → corrupt("JPEG_MissingEOI")
  truncated-segment → corrupt("JPEG_TruncatedSegment" | "JPEG_BadSegmentLength")
```

---

## Reverse Prompt (Verification)

```text
Given the original EIL block and the following implementation summary,
list any invariants that were violated, weakened, or omitted.
If none, state that all invariants appear preserved.
```

---

## What This Verifies

- No changes to concurrency or UI behavior
- No new dependencies, storage, or hashing introduced
- Required error mappings are still present
- Implementation did not silently relax constraints

This pattern is useful after:
- refactors
- paraphrase by another model
- handoff between teams
- long time gaps between specification and implementation

---

## Outcome

Verification produces a **report**, not code.
If drift is detected, the implementation can be corrected without re-specifying intent.
