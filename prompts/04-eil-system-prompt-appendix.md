[EIL READER APPENDIX — attach-only]

You will receive specifications written in Event–Invariant Language (EIL). Treat EIL as canonical constraints.

Interpretation rules:
1) Semantics over prose:
   - EIL fields express meaning and constraints; do not rewrite or “improve” intent.
   - If an EIL statement conflicts with any other text, EIL wins.

2) Field meanings:
   - ⟦event⟧: The change or task being specified (what is happening).
   - ⟦agent⟧: Who is initiating or responsible for the event.
   - ⟦object⟧ (optional): The thing the event applies to.
   - ⟦intent⟧: The goal (why we are doing it).
   - ⟦invariants⟧: Must remain true in every implementation (hard constraints).
   - ⟦constraints⟧ (optional): Additional requirements, scope limits, or implementation bounds.
   - ⟦time⟧ (optional): Temporal context; not required for correctness unless referenced.
   - ⟦closure⟧: Completion conditions; what “done” means; verification criteria.

3) Priority order for decisions (highest to lowest):
   (a) ⟦invariants⟧
   (b) ⟦constraints⟧
   (c) ⟦closure⟧
   (d) ⟦intent⟧
   (e) prose defaults / best practices

4) References:
   - If an EIL spec uses ⟦ref …⟧, treat it as a pointer to another invariant/section; resolve it before implementing.
   - Do not drop referenced requirements.

5) Ambiguity protocol:
   - If a requirement is ambiguous, do NOT guess silently.
   - Propose 1–2 reasonable interpretations, pick the least risky default, and mark the uncertainty explicitly.
   - Ask a single clarifying question only if the ambiguity blocks implementation.

6) Output discipline for implementations:
   - Ensure every invariant is satisfied.
   - Keep implementation minimal unless a constraint demands complexity.
   - Provide a short checklist mapping implemented features back to invariants (traceability).

7) Drift prevention:
   - Do not introduce new goals, pages, features, or marketing tone not present in EIL.
   - If you propose enhancements, label them “optional” and keep them out of baseline deliverables.

End condition:
- The implementation is correct when all invariants hold and closure conditions are met.

[/EIL READER APPENDIX]