# LLM Coding Rules

## Rule 1 — Think Before Coding

- State assumptions explicitly before acting.
- Ask rather than guess when ambiguity affects correctness, safety, architecture, data ownership, or user intent.
- Push back when a simpler approach exists.
- Stop and clarify when confused — do not proceed on uncertainty.

---

## Rule 2 — Simplicity First

- Write the minimum code that solves the problem.
- Do not add speculative features, abstractions, or "future-proofing."
- No abstractions for single-use code.

---

## Rule 3 — Surgical Changes

- Touch only what you must to accomplish the task.
- Do not improve, refactor, or "clean up" adjacent code.
- Match existing style, naming, and patterns in the file.
- Do not refactor what is not broken.

---

## Rule 4 — Goal-Driven Execution

- Turn vague commands into verifiable milestones before coding.
- For behavior changes, write or update a failing test first (red), apply the fix, then confirm it passes (green).
- For docs, config, or mechanical changes, define the smallest relevant verification instead of forcing a test harness.
- Each step should have a clear definition of done.

---

## Rule 5 — Read Before Writing

- Inspect existing code, exports, imports, and call sites before making changes.
- Understand how the surrounding system works before adding or modifying behavior.
- Reuse existing functions and patterns rather than reimplementing.

---

## Rule 6 — Tests Verify Intent

- Tests must encode **why** behavior matters, not just **what** it does.
- Create tests that explain intent and can actually fail when behavior regresses.
- Avoid surface-level tests that pass regardless of correctness.

---

## Rule 7 — Checkpoint Operations

- For multi-step work, summarize progress after each meaningful step.
- Pause if you cannot describe the current state clearly.
- Do not continue building on an unclear or unverified foundation.

---

## Rule 8 — Match Conventions

- Strictly adhere to the existing codebase's style over personal preference.
- Match naming, file structure, import order, error handling, and documentation level.
- Do not silently introduce new patterns or conventions.

---

## Rule 9 — Fail Loudly

- "Completed" is wrong if anything was skipped silently.
- "Tests pass" is wrong if any tests were skipped or not run.
- Surfacing uncertainty is better than silent failure.
- Ensure all relevant tests pass and nothing was skipped without explicit acknowledgment.

---

## Rule 10 — Hard Token Budgets

- Set strict usage limits to prevent infinite loops (e.g., max attempts, max files touched).
- If the budget is exceeded, summarize current state and what remains.
- Restart with a focused scope rather than continuing to spin.

---

## Rule 11 — Avoid Duplication

- Inventory neighboring code before writing new functions.
- Reuse or extend existing utilities instead of creating redundant implementations.
- If duplication is unavoidable, explain why.

---

## Rule 12 — No Blind Overwriting

- Halt on errors — do not build on a broken state.
- Do not silently overwrite files or revert unrelated changes.
- Force manual review and rollback when state is uncertain.

---

## Rule 13 — Surface Conflicts, Don't Average Them

- If two patterns in the codebase contradict each other, pick one (prefer more recent or more tested).
- Explain why you chose that pattern.
- Flag the conflicting pattern for cleanup — do not blend incompatible approaches.

---

## Rule 14 — Table Summary After Logic Changes

After finishing a refactor or a change to existing logic, display a table summarizing before vs. after:

| Aspect | Before | After | Reason |
|--------|--------|-------|--------|
| ...    | ...    | ...   | ...    |

Include behavior, interfaces, or architecture — whatever changed and why.

---

## Rule 15 — Integration Tests for Cross-Cutting Changes

- If a feature touches multiple modules or layers, create an integration test if one does not exist.
- When core logic changes, update the test to match — but base assertions on **input and output**, not internal implementation.
- Do not overfit tests to current code structure; test observable behavior.

---

## Rule 16 — Linting

- Always run the project's linter (e.g., Pylint, ESLint, Ruff) after code changes.
- Fix linting issues introduced by your changes.
- Design code so it does not require lint ignores. Refactor or restructure first — do not silence the linter to avoid changing code.
- Exception handling is the narrow exception. Linters sometimes flag catch patterns (`bare except`, broad `Exception`, empty handlers) that are intentional. A targeted ignore is acceptable only when the catch behavior is deliberate, bounded, and documented.
- For any other lint ignore, use it only when that design is **objectively better** than the lint-clean alternative — not because fixing the lint is inconvenient.
- Every lint ignore must include a brief comment explaining **why** the ignored design is better than complying with the rule.

---

## Rule 17 — Red Lines (Stop and Flag)

Stop immediately and flag to the user when encountering:

| Condition | Action |
|-----------|--------|
| Unclear state ownership | Stop — ask who owns what |
| Unknown blast radius | Stop — map impact before proceeding |
| Timing / race condition hazards | Stop — do not guess at concurrency fixes |
| Security issues (secrets, auth, injection) | Stop — flag and propose safe approach |
| Significant complexity debt | Stop — propose simpler alternative |
| Unknown unknowns on non-trivial changes | Stop — gather context first |

Do not proceed past a red line without explicit user approval.

---

## Rule 18 — Coding Principles

Apply these principles unless the codebase explicitly does otherwise:

| Principle | Guideline |
|-----------|-----------|
| **Separation of Concerns (SoC)** | Separate presentation/UI, business logic, and data access into distinct modules. Never mix them in one file. |
| **Single Responsibility (SRP)** | Every function, class, or module does one thing and has one reason to change. |
| **KISS** | Prefer the simplest, most direct solution using native language features. Avoid hyper-abstraction. |
| **YAGNI** | Do not write code for hypothetical future requirements, scale, or edge cases that do not exist yet. |
| **DRY** | Consolidate duplicate logic into reusable utilities — but only when duplication is real, not anticipated. |
| **Dependency Inversion & Injection** | Pass dependencies (API clients, DB instances, config) into functions/classes. Do not hardcode or instantiate them inside. |

---

## Rule 19 — Feature Documentation

When the project uses feature documentation, `docs/feature/*.md` holds the **detailed** documentation for each feature — behavior, configuration, examples, edge cases, and limitations. One file per feature.

Keep it in sync with feature changes:

- If a new feature has been added, add it in `docs/feature/*.md`.
- If an existing feature has been modified, update the file.
- If a feature has been removed, remove the file.

Do not put this depth of detail in `README.md` (see Rule 20).

---

## Rule 20 — README

Create and maintain a `README.md` at the project root. Follow README best practices and keep it current when the project changes.

Required sections:

| Section | Purpose |
|---------|---------|
| **Title** | Project name and one-line identity |
| **Summary** | What the project does, who it is for, and key capabilities |
| **How to use** | Quick start, common workflows, and examples |
| **How to build, install** | Prerequisites, install steps, and build/run commands |

Add additional sections when they apply — for example: requirements, configuration, testing, project structure, contributing, license, and links to deeper docs (`docs/feature/*.md`, API references, etc.).

Update `README.md` in the same change when project-level docs are affected:

| Change | Update in README |
|--------|------------------|
| Feature added, changed, or removed | Summary, feature list, and links to `docs/feature/*.md` — not the full feature write-up (Rule 19) |
| Dependency added, changed, or removed | How to build, install, and requirements |
| Workflow added, changed, or removed | How to use and quick-start examples |

---
