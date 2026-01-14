# JPEG Execution Example — Structural Validator (Execution Handoff)

This example demonstrates **Execution Handoff** using Event–Invariant Language (EIL).
It shows how EIL can define *what must not change* while leaving implementation details flexible.

---

## Context

Goal: add a lightweight, deterministic **JPEG structural validator** that runs **before decode**,
detecting malformed structure without changing concurrency, UI, or dependencies.

---

## EIL (Execution Handoff)

```text
⟦use⟧: execution-handoff
⟦event⟧: feature.add
⟦agent⟧: sam
⟦object⟧: jpeg-structural-validator

⟦intent⟧:
  add pre-decode structural validation for JPEG
  detect malformed marker/segment structure deterministically
  supersede legacy EOI tail check

⟦invariants⟧:
  concurrency: unchanged
  enumeration: unchanged
  ui: unchanged
  progress: unchanged
  dependencies: none-added
  storage: none-added
  hashing: none-added
  reason-plumbing: preserve(task1)

⟦constraints⟧:
  scope: structural-only (no entropy decode)
  tolerance: permissive marker ordering except SOF-before-SOS
  language: pure Swift
  memory: full-file load acceptable (v1)

⟦closure⟧:
  valid-jpeg → good
  missing-eoi → corrupt("JPEG_MissingEOI")
  truncated-segment → corrupt("JPEG_TruncatedSegment" | "JPEG_BadSegmentLength")
  sos-before-sof → corrupt("JPEG_InvalidMarkerOrder")
```

---

## Notes

- The EIL block defines **intent and invariants**, not a full algorithm.
- Marker byte constants and error mappings are invariant.
- Traversal strategy (index scan, state machine, etc.) is an implementation choice.
- Detailed algorithms may be provided separately when needed.

---

## Why This Works

- Multiple valid implementations can satisfy the same invariants.
- Drift is detectable via **Verification mode** after implementation.
- The handoff is complete without over-constraining execution.

This is a canonical example of **EIL as an execution handoff artifact**.
