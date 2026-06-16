# Contributing

Contributions are welcome. The goal is to keep these rules useful for real coding work, not to grow a large policy document.

## What makes a good change

- Improve a rule that is ambiguous, incomplete, or hard to apply.
- Add guidance for a recurring failure mode seen in real LLM coding workflows.
- Remove wording that creates unnecessary complexity or contradicts another rule.
- Keep examples concrete and tool-agnostic unless the rule is explicitly tool-specific.

## Pull request checklist

- The change is limited to the rule, README, or release metadata it actually affects.
- The README quick reference stays aligned with `LLM_CODING_RULES.md`.
- New or changed rules explain the behavior expected from the assistant.
- The wording is direct enough that another maintainer can enforce it in review.

## Release notes

Use Conventional Commit style in pull request titles, for example:

- `feat: add guidance for public repository initialization`
- `fix: clarify lint-ignore exceptions`
- `docs: improve contribution checklist`
