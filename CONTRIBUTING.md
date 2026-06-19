# Contributing

Thank you for improving the Postgres Introspection skill.

## Purpose

This repository maintains and releases the `postgres-introspection` agent skill. Contributions should preserve its purpose: teaching an agent to build a read-only database introspection capability, capture intent in the database, and read the state with judgment, while keeping data safe.

## Good contributions

- Improve the clarity or correctness of `src/SKILL.md` and the files in `src/references/`.
- Improve or extend the PostgreSQL reference implementation in `src/scripts/`.
- Improve the worked examples and verification prompts in `src/test-fixtures/`.
- Improve documentation for humans and maintainers.
- Strengthen the data-safety, source-of-truth, and judgment guidance.

## How changes land

Changes reach `main` only through a squash-merged pull request that passes the `Validate skill package` check. Direct pushes to `main` are blocked for everyone. The full workflow and the repository protections are described in `docs/RELEASING.md`.

## Before opening a pull request

- Read `README.md` and `docs/ARCHITECTURE.md`.
- Run `npm run validate`.
- Run `npm run package -- vX.Y.Z` with any tag when changing packaging or release behavior, to confirm the assets build.

## Documentation standards

Use plain Markdown with real headings, prose paragraphs of one to three sentences, flat atomic lists, and fenced code blocks with language identifiers. Do not use bold as a heading or em dashes as punctuation. Prefer explaining why a rule exists when a future agent may need to adapt it.

## Pull request expectations

Each pull request should explain what changed, why it matters, and how it was validated.

## Security and privacy

Do not commit credentials, tokens, or a real application's domain schema. Use minimal, generic public examples when demonstrating the skill.
