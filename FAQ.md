# EIL FAQ

This FAQ explains **why Event–Invariant Language (EIL) exists**, what problem it solves, and why it is intentionally *not* built on existing formats like YAML or JSON.

---

## What problem does EIL solve?

Most failures in AI-assisted work are not caused by weak models or poor reasoning.

They are caused by **lost intent**.

A task is paraphrased, summarized, handed to another model, or revisited after time has passed — and constraints that once felt obvious quietly disappear.

EIL exists to make those constraints **explicit, durable, and reviewable**.

---

## Why is intent loss a real problem?

Natural language is flexible by design.

That flexibility is valuable for creativity and communication, but it makes meaning fragile across:
- paraphrase
- summarization
- handoff between humans and models
- time gaps

Without an explicit place to say *“this must not change”*, drift is silent and often discovered late.

---

## What is EIL?

EIL is a **small, intent-level specification**.

It is:
- a way to state invariants explicitly
- a lightweight intermediate representation between English and execution
- usable by both humans and AI systems

EIL constrains **interpretation**, not execution.

---

## What is EIL not?

EIL is not:
- a programming language
- a framework
- an SDK
- a task runner
- a description of model internals
- a universal inter-model language

If you need those things, EIL is the wrong tool.

---

## Why not just write better prompts?

Better prompts help, but they optimize **generation**, not **preservation**.

EIL optimizes for:
- keeping constraints intact across paraphrase
- detecting drift after the fact
- reviewing work without re-specifying it
- verifying that intent survived handoff

Prompts help you *say* things better.  
EIL helps you ensure the *same thing is still being said* later.

---

## Why not YAML?

YAML is a **data serialization format**, not a meaning-preservation language.

It is good for:
- configuration
- structured data
- machine ingestion

It is weak at:
- expressing intent
- distinguishing invariants from context
- surviving paraphrase or summarization
- guiding interpretation by humans and models

YAML encourages a false sense of completeness.  
If something is missing, it looks accidental rather than deliberate.

EIL is intentionally **partial**:
- missing fields are allowed
- English may surround or interleave with EIL
- absence can be meaningful

YAML answers *“What are the fields?”*  
EIL answers *“What must not change?”*

---

## Why not JSON?

JSON shares many of YAML’s limitations, with additional ones.

JSON is:
- rigid
- verbose
- schema-driven
- optimized for machines first, humans second

This makes JSON good for:
- APIs
- storage
- programmatic contracts

It makes JSON poorly suited for:
- conversational use
- incremental refinement
- human–AI collaboration
- graceful degradation back into English

JSON optimizes for **validity**.  
EIL optimizes for **interpretability**.

---

## Could EIL be represented in YAML or JSON?

Yes.

That may be useful for:
- storage
- transport
- tooling

But that would be a **representation choice**, not the language itself.

EIL’s semantics do not depend on strict schemas or complete field presence.
They depend on how readers interpret roles like *intent* and *invariants*.

---

## When should I use EIL?

EIL is useful when:
- work spans time gaps
- multiple models or people are involved
- summarization or refactoring occurs
- correctness depends on non-obvious constraints
- you want to verify that intent survived

---

## When should I not use EIL?

EIL may be unnecessary if:
- the task is fully expressible as code
- a stable schema already exists
- no handoff or reinterpretation occurs
- constraints are obvious and trivial

EIL should earn its place.  
If it doesn’t, don’t use it.

---

---

## How do extensions work in EIL?

EIL allows non-core fields (extensions) for clarity (e.g. `context`, `scope`, `procedures`).

Best practice is to **explicitly scope extensions as local** to a given artifact so they are not mistaken for core grammar.
Extensions are interpretive aids unless elevated into `⟦invariants⟧` or `⟦constraints⟧`.

## In one sentence

EIL exists to let you say:

> *“You may rephrase this however you want — but you may not change this.”*
