# Event–Invariant Language (EIL) Specification

## 1. Purpose

Event–Invariant Language (EIL) is a lightweight, intent-level notation for communicating:

- what happened,
- why it matters,
- what must not change,
- and how completion is recognized.

Its purpose is to reduce silent intent drift across paraphrase, time, and handoff between humans and AI systems.

EIL is a **specification, not a framework**. Implementations may vary.

---

## 2. Design Principles

- **Intent preservation over phrasing**
- **Explicit invariants**
- **Graceful degradation to natural language**
- **Human-legible, machine-usable**
- **No claims about model internals**

EIL constrains interpretation; it does not prescribe execution unless explicitly declared.

---

## 3. Core Grammar

### Required fields

- `⟦event⟧` — what changed
- `⟦agent⟧` — who initiated the event
- `⟦intent⟧` — why the event exists
- `⟦invariants⟧` — what must not change
- `⟦closure⟧` — when the work is considered complete

### Optional fields

- `⟦object⟧`
- `⟦constraints⟧`
- `⟦time⟧`

Partial EIL blocks are valid. English may surround EIL blocks.

---

## 4. Semantics

- **Event** describes state change
- **Intent** describes purpose
- **Invariants** define non-negotiable constraints
- **Constraints** bound allowable solutions
- **Closure** defines success/failure criteria

---

## 5. Intended Use Modes

EIL supports three primary usage modes:

1. **Alignment** — establish shared understanding
2. **Execution Handoff** — define invariant-complete work
3. **Verification** — check whether intent and invariants were preserved

Verification is commonly performed using **reverse prompts**, where a model evaluates artifacts instead of generating them.

---

## 6. Procedural Invariants

EIL is not a programming language.

However, **procedural detail MAY be included inline if violating the procedure would violate an invariant**.

### Guidance

Include procedural detail when:
- safety depends on procedure
- termination or bounds behavior is invariant
- error mappings are contractually fixed

Keep procedures external when:
- multiple algorithms satisfy the same invariants
- performance tradeoffs are implementation-defined

---

## 7. Permissible Extensions

- Additional labeled sections may appear
- Extensions must be explicitly scoped
- Extensions must not contradict invariants
- Extensions must not claim to be core grammar

Examples:
- `[acceptance]`
- `[implementation]`
- `[tests.optional]`

---

## 8. Non‑Goals

EIL is **not**:

- a programming language
- a full algorithm specification
- a task framework
- a universal inter-model language
- a description of internal model representations

---

## 9. Summary

> **EIL allows you to say: “You may rephrase this however you want — but you may not change *this*.”**

---

## Version History

### v1.3.2 — Extension Scoping Clarification
- Clarified that permissible extensions (non-core fields) SHOULD be explicitly scoped as local.
- Clarified that extensions are interpretive aids unless elevated into ⟦invariants⟧ or ⟦constraints⟧.
- No grammar or semantic changes.

### v1.3.1 — Verification Clarification
- Introduced verification as an explicit usage mode.
- Clarified reverse prompts and drift checking.
- No grammar changes.

### v1.3 — Procedural Invariant Rule
- Formalized the Procedural Invariant Rule.
- Clarified boundary between invariants and implementation detail.
- No grammar changes.

### v1.2 — Misunderstanding Classes
- Documented five classes of EIL misunderstanding.
- Added usage guidance and failure modes.

### v1.1 — Receiver Semantics
- Clarified acknowledgment and receiver understanding of invariants.

### v1.0 — Initial Specification
- Defined core grammar and non-goals.
