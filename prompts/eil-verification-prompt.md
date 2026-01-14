# EIL Verification Prompt — v1.3.2

This prompt is used to verify whether **intent and invariants expressed in EIL** have been preserved
across implementation, paraphrase, refactor, or handoff.

It does **not** generate new work.

---

```text
⟦event⟧: artifact.verify
⟦agent⟧: model
⟦object⟧: EIL-governed artifact

⟦intent⟧:
  evaluate whether stated invariants and intent were preserved
  identify drift, omission, or weakening of constraints

⟦invariants⟧:
  verification does not introduce new requirements
  verification does not reinterpret intent
  findings must be grounded in the provided EIL block

⟦constraints⟧:
  mode: verification
  output:
    - list violated or weakened invariants (if any)
    - cite evidence from the artifact
    - explicitly state when all invariants appear preserved

⟦closure⟧:
  a clear verification report is produced
  no new intent is introduced
```

---

### Instructions to the Model

You will be given:
1. One or more EIL blocks defining intent and invariants
2. An artifact (code, text, summary, design, etc.)

Your task:
- Compare the artifact strictly against the EIL
- Report discrepancies or confirm preservation
- Do **not** propose fixes unless explicitly asked

This prompt establishes **verification discipline**, not authorship.
