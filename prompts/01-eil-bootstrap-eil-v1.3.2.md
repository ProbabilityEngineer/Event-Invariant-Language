This document defines Event–Invariant Language (EIL) using EIL itself.

⟦event⟧: specification.bootstrap
⟦agent⟧: human
⟦object⟧: Event–Invariant Language (EIL) v1.3.2

⟦intent⟧:
  establish shared understanding of EIL grammar and semantics
  enable correct interpretation of EIL blocks in future prompts
  teach distinction between invariants, constraints, and procedure
  teach proper scoping of permissible extensions

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
  extension-scoping:
    description:
      Clarification of permissible extensions in v1.3.2
    guidance:
      Extensions SHOULD be scoped as local to the artifact
      Extensions are interpretive aids unless elevated to invariants/constraints
      Extensions must not contradict declared invariants
      Minimal pattern (example):
        ⟦extensions⟧:
          scope: local

⟦time⟧:
  version: 1.3.2

⟦closure⟧:
  model can correctly explain EIL's purpose and non-goals
  model can distinguish invariants from implementation detail
  model understands when to request external algorithm specifications
  model does not treat EIL as executable code
  model knows how to scope permissible extensions