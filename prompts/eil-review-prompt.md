# EIL Review Prompt — v1.3.1

This prompt is used to **critique or improve clarity** of an EIL block itself.
It is distinct from Verification and Execution Handoff.

---

```text
⟦event⟧: eil.review
⟦agent⟧: model
⟦object⟧: EIL block

⟦intent⟧:
  improve clarity and completeness of EIL expression
  surface ambiguity or missing invariants
  suggest structural or wording improvements

⟦invariants⟧:
  original intent must not be altered
  no new requirements may be introduced without flagging
  suggested changes must preserve meaning

⟦constraints⟧:
  mode: review
  output:
    - list ambiguities or weaknesses
    - suggest clarifications
    - flag assumed or inferred invariants

⟦closure⟧:
  review feedback is provided
  original intent remains intact
```

---

### Instructions to the Model

You will be given an EIL block.

Your task:
- Evaluate whether it is clear, complete, and well-scoped
- Identify missing invariants or unclear closures
- Suggest improvements *without rewriting intent*

This prompt supports **quality control of EIL itself**, not execution.
