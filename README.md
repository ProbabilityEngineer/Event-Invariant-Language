# Event–Invariant Language (EIL)

**Event–Invariant Language (EIL)** is a lightweight, intent-level notation for preserving *what must not change* when humans and AI systems collaborate.

It is designed to prevent silent intent loss across paraphrase, iteration, time gaps, and handoff between humans and models.

> **EIL is a specification, not a framework. Implementations may vary.**

---

## Why EIL Exists

Most failures in AI-assisted work are not caused by bad models or weak reasoning.

They are caused by **lost intent**.

A task is:
- explained slightly differently,
- partially summarized,
- handed to another agent,
- revisited days later,

…and critical constraints quietly disappear.

**EIL exists to make those constraints explicit.**

Think of EIL as a **checksum for meaning**:
- it does not replace English,
- it tells you what English *must not change*.

---

## What EIL Is

EIL is an **intent-level Intermediate Representation (IR)**.

It sits between:
- natural language (rich but ambiguous)
- execution (code, actions, automation)

EIL captures:
- the event that occurred,
- the intent behind it,
- the invariants that must be preserved,
- the conditions under which work is considered complete.

---

## What EIL Is Not

EIL is **not**:
- a programming language
- a full algorithm specification
- a task framework or workflow engine
- a claim about how AI models internally represent knowledge
- a universal lossless inter-model language

EIL constrains interpretation.  
It does not prescribe implementation unless explicitly declared.

---

## Before and After EIL

### Before (English-only)

> “Add a JPEG validator that checks structure before decode, but don’t break concurrency or UI.  
> Replace the old EOI check and make sure errors are reported correctly.”

What gets lost:
- what “structure” means
- which errors are mandatory
- which parts must *not* change
- whether algorithm details are flexible or fixed

Different agents may implement *different but reasonable* solutions.

---

### After (English + EIL)

```text
⟦use⟧: execution-handoff

⟦event⟧: feature.add
⟦object⟧: jpeg-structural-validator

⟦intent⟧:
  detect-obvious-structural-corruption-predecode
  supersede-legacy-eoi-tail-check

⟦invariants⟧:
  concurrency: unchanged
  ui: unchanged
  dependencies: none-added
  error-mapping: deterministic

⟦closure⟧:
  valid-jpeg → good
  missing-eoi → corrupt("JPEG_MissingEOI")
```

English can vary.  
**Meaning cannot.**

---

## Intended Use Modes

EIL supports three primary usage modes:

- **Alignment** — establish shared understanding
- **Execution Handoff** — provide invariant-complete task definitions
- **Verification** — check whether intent and invariants were preserved

---

## Prompt Artifacts

The `prompts/` directory contains ready-to-use prompts that support correct use of EIL:

- **eil-bootstrap-prompt-v1.3.2.md** — establish shared understanding of EIL before use
- **eil-review-prompt.md** — improve clarity and completeness of EIL blocks without changing intent
- **eil-verification-prompt.md** — verify that intent and invariants were preserved in downstream artifacts

These prompts are operational aids.  
They do not replace the specification.

Non-core fields (permissible extensions) should be explicitly scoped as **local** to the artifact.

---

## Examples

The `examples/` directory contains small, canonical EIL artifacts illustrating common use cases:

- **jpeg-execution-example.md** — an execution-handoff example showing how EIL defines invariants without prescribing an algorithm
- **verification-example.md** — a verification (reverse-prompt) example for detecting intent drift after implementation

These examples are illustrative, not exhaustive.

---

## FAQ

For rationale, boundaries, and common questions (e.g. “Why not YAML or JSON?”), see **FAQ.md**.

---

## Verification Example (Reverse Prompt)

EIL can be used to *verify* work after the fact by asking a model to evaluate artifacts instead of generating them.

**Example reverse prompt:**

```text
Given the following EIL block and this implementation summary,
list any invariants that were violated, weakened, or not addressed.
If none, state that all invariants appear preserved.
```

This makes drift and omission visible without re-executing the task.

---

## Procedural Invariants (Important)

EIL is not a programming language.

However, **procedural detail may appear in EIL when the procedure itself is non-negotiable**.

Guiding rule:
- If multiple algorithms satisfy the invariants, keep procedure external.
- If violating a procedure would violate an invariant, the procedure may appear inline.

---

## Status

- Current version: **v1.3.2**
- README version: **1.3.2**
- Stability: grammar-stable, clarification-only changes expected
- License: **Apache 2.0**

See `CHANGELOG.md` for version history.

Contributions are welcome, but EIL prioritizes stability and clarity over feature growth.
See CONTRIBUTING.md for details.

---

## In One Sentence

> **EIL is a way to say: “You can phrase this however you want — but you may not change *this*.”**

© 2026 Samuel Collins. Licensed under Apache 2.0.
