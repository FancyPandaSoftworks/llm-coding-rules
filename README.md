# LLM Rules

A compact, opinionated rule set for LLM coding assistants. These rules are meant for developers who want AI-assisted coding to stay simple, verifiable, and aligned with the codebase in front of it.

Full rules: [LLM_CODING_RULES.md](LLM_CODING_RULES.md).

Everyone is encouraged to improve these LLM rules. If a rule is unclear, incomplete, too rigid, or missing a real-world failure mode, open an issue or pull request with a concrete improvement.

## How to use

Copy the rules into your AI coding assistant's project instructions, system prompt, or repository-level guidance file. Keep the full rule text available to the assistant and use the quick reference below as a human checklist during reviews.

For repository-scoped use, link or copy [LLM_CODING_RULES.md](LLM_CODING_RULES.md) into your project's `AGENTS.md`, `.cursorrules`, Claude project instructions, or equivalent tool-specific configuration.

## How to build, install

This is a documentation-only project. There is no build step and no runtime dependency.

To work on the rules locally:

```sh
git clone https://github.com/FancyPandaSoftworks/llm-rules.git
cd llm-rules
```

Edit the Markdown files and open a pull request.

## Quick Reference

| # | Rule | One-liner |
|---|------|-----------|
| 1 | Think Before Coding | Ask, don't guess |
| 2 | Simplicity First | Minimum viable code |
| 3 | Surgical Changes | Touch only what's needed |
| 4 | Goal-Driven Execution | Verifiable milestones, proportional tests |
| 5 | Read Before Writing | Inspect before editing |
| 6 | Tests Verify Intent | Test why, not just what |
| 7 | Checkpoint Operations | Summarize and pause when unclear |
| 8 | Match Conventions | Follow existing patterns |
| 9 | Fail Loudly | No silent skips |
| 10 | Hard Token Budgets | Stop and restart when stuck |
| 11 | Avoid Duplication | Inventory before writing |
| 12 | No Blind Overwriting | Halt on errors |
| 13 | Surface Conflicts | Pick one pattern, flag the other |
| 14 | Table Summary | Before/after table after logic changes |
| 15 | Integration Tests | Cross-cutting changes need integration tests |
| 16 | Linting | Fix linter issues; avoid ignores unless objectively better |
| 17 | Red Lines | Stop on ownership, blast radius, security, etc. |
| 18 | Coding Principles | SoC, SRP, KISS, YAGNI, DRY, DI |
| 19 | Feature Documentation | Sync project feature docs with feature changes |
| 20 | README | Maintain root `README.md` with required sections |

## Releases

Versioning is automated by [Release Please](.github/workflows/release-please.yml) on merge to `main`. Use [Conventional Commits](https://www.conventionalcommits.org/) in PR titles (e.g. `feat: add rule 19`).

The workflow expects a `RELEASE_PLEASE_TOKEN` GitHub Actions secret. Use a fine-grained personal access token with access to this repository and the permissions needed to write contents and pull requests.

## Contributing

Rule changes should be specific, practical, and easy to apply across real codebases. See [CONTRIBUTING.md](CONTRIBUTING.md) before opening a pull request.
