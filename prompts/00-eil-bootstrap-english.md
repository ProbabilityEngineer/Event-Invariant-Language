# English Bootstrap — Event–Invariant Language (EIL)

## Purpose

This document introduces **Event–Invariant Language (EIL)** to a fresh instance with no prior exposure.

EIL is **not code** and **not executable**.  
It is a structured way of expressing **intent and meaning** so that they remain stable across paraphrase, summarization, compression, translation, and handoff between models or contexts.

Your task when reading EIL is to **constrain interpretation, not execution**.

---

## What EIL Is

EIL is:

- An **intent-level intermediate representation**
- A way to express **what must remain true**, independent of wording
- A language for **constraints on meaning**, not procedures
- A tool for preserving semantics across time and systems

EIL exists to reduce ambiguity and drift, not to prescribe implementation.

---

## What EIL Is Not

EIL is **not**:

- A programming language
- Executable instructions
- A framework or runtime
- A replacement for natural language
- A schema you should extend casually

Do not treat EIL blocks as commands to run.

---

## Structure of EIL

EIL uses labeled fields enclosed in double brackets, such as:

- ⟦event⟧
- ⟦agent⟧
- ⟦intent⟧
- ⟦invariants⟧
- ⟦constraints⟧
- ⟦closure⟧

Not all artifacts will contain every field.  
Partial EIL blocks are valid.

Each field has a **semantic role**, not a syntactic one.

---

## Invariants (Highest Priority)

**Invariants are the most important element in EIL.**

They describe truths that must hold across:
- paraphrase
- summarization
- rewording
- translation
- compression
- handoff to another model or system

If an interpretation would violate an invariant, it is incorrect —  
even if it sounds reasonable in natural language.

When in doubt, preserve invariants over fluency.

---

## Relationship Between EIL and English

English may appear:
- before EIL blocks
- after EIL blocks
- interleaved with them

English provides **context, explanation, and narrative**.  
EIL provides **semantic anchors**.

If English prose and EIL conflict:
- **EIL invariants take precedence**

Do not silently reinterpret or “smooth over” EIL structure.

---

## Procedures vs Meaning

Some EIL artifacts may reference procedures, algorithms, or steps.

Unless explicitly marked as invariant-bearing:
- Treat procedures as **examples**, not requirements
- Assume multiple implementations may satisfy the same invariants

Only treat a procedure as required if violating it would violate an invariant.

---

## Extensions and Scope

Some artifacts may define **extensions** or clarifications.

- Extensions are **scoped** (usually local to the artifact)
- Extensions must not contradict declared invariants
- Extensions are interpretive aids unless explicitly elevated

If extension scope or meaning is unclear:
- Ask for clarification
- Do not invent semantics

---

## Handling Uncertainty

If you are unsure how to interpret an EIL construct:

- Ask for clarification
- Do not guess
- Do not normalize away structure
- Do not assume missing fields imply default values

Correct handling of uncertainty is preferred over confident error.

---

## Success Criteria

You have understood EIL correctly when you can:

- Explain what must remain true, independent of wording
- Distinguish invariant meaning from implementation detail
- Preserve intent across reformulation
- Hand off understanding to another model without loss

---

## Next Step

You will next be given a **formal EIL specification** written using EIL itself.

Read it using the rules defined in this document.