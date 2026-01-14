# EIL Bootstrap Prompt — v1.3.1

This prompt is used to bootstrap a model’s understanding of **Event–Invariant Language (EIL)**.
It is not a replacement for the specification, but an operational aid.

---

```text
⟦event⟧: specification.bootstrap
⟦agent⟧: human
⟦object⟧: Event–Invariant Language (EIL) v1.3.1

⟦intent⟧:
  establish shared understanding of EIL grammar and semantics
  enable correct interpretation of EIL blocks in future prompts
  teach distinction between invariants, constraints, and procedure

⟦invariants⟧:
  EIL is an intent-level intermediate representation
  EIL is a specification, not a framework
  EIL is not a programming language
  EIL constrains interpretation, not execution
  English may surround or interleave with EIL blocks
  Partial EIL blocks are valid
  Invariants must be preserved across paraphrase, summarization, and handoff

⟦constraints⟧:
  usage-modes:
    allowed:
      - alignment
      - execution-handoff
      - verification
  procedural-invariant-rule:
    description:
      If violating a procedure would violate an invariant,
      that procedure MAY be treated as invariant-bearing and included inline.
    guidance:
      Multiple algorithms satisfy invariants → keep procedure external
      Safety, bounds, or error-mapping depends on procedure → procedure may be inline

⟦time⟧:
  version: 1.3.1

⟦closure⟧:
  model can correctly explain EIL’s purpose and non-goals
  model can distinguish invariants from implementation detail
  model understands when to request external algorithm specifications
  model does not treat EIL as executable code
```

---

### Instructions to the Model

- Acknowledge understanding of EIL before acting on future EIL blocks.
- When asked to generate EIL, prioritize clarity of invariants over verbosity.
- When asked to verify work, use EIL to detect drift, omission, or weakened constraints.
- If an EIL block appears incomplete, ask for clarification rather than inferring invariants.

This prompt establishes the **interpretive contract** for subsequent interactions.
