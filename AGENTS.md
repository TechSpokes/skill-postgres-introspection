# Agent Instructions for the Postgres Introspection Skill

## Summary

This repository maintains and releases one agent skill: `postgres-introspection`. The skill teaches an AI agent to build a read-only database introspection capability inside the repository it works in, to capture the architect's intent in database comments, and to read the generated state with judgment. Maintain the skill so future agents and humans can discover it, follow it, and update it as the domain changes.

## Canonical entry point

`src/SKILL.md` is the canonical skill entry point. Its YAML frontmatter (`name` and `description`) is the discovery surface that hosts use to activate the skill. The body carries the goal, the gates, the workflow, and pointers into `src/references/`.

Keep `src/SKILL.md` short and load-bearing. Detail belongs in `src/references/`, loaded only when a step needs it.

## Repository map

- `src/SKILL.md` is the entry point.
- `src/references/` holds the durable knowledge: `approach.md` (method and invariants), `reference-implementation.md` (the PostgreSQL example and how to adapt it), `reading-the-state.md` (consumption patterns), `using-the-reports.md` (judgment and the alignment loop), `commenting.md` (capturing intent), `layers.md` (the database and surrounding layers), `other-databases.md` (porting the method), and `agents-integration.md` (wiring to migrations and discoverability).
- `src/scripts/` is the runnable PostgreSQL reference implementation.
- `src/test-fixtures/` holds a generic example and verification prompts.
- `docs/` explains the skill for humans and maintainers.
- `packaging/` holds the Codex and Claude plugin manifests.
- `scripts/` holds the repository's validate and package tooling.

## Defined terms

- Introspection: reading a live source read-only and rendering its current state into files. Generated, never hand-authored.
- State: the rendered snapshot of the database's structure, security, and exposed surface, as of a migration version.
- Subject: one thing introspected; the database is the core subject, with the cluster, a pooler, and a REST layer as additional subjects.
- Cluster: a PostgreSQL server instance, not a Kubernetes or sharding cluster.

## Core principles the skill must keep

The database is the single source of truth for both the data and the intent behind its shape; documentation derives from it. Intent lives in compact, single-line database comments, with longer rationale in the code or docs referenced from the comment.

The data is sacred. The tool reads read-only; no skill guidance may instruct an agent to reset, wipe, or run migrations against a data-bearing or production database, or to touch production without explicit, informed user consent. Every database change, including a comment, flows through a migration with consent.

Judgment is shared. The skill must keep its diagnose-and-confirm stance: surface findings as obstacles to the repository's goals, weigh local context, and bring decisions to the user rather than acting alone or silently deferring.

## How to maintain

When you change skill behavior, update `src/SKILL.md` and the relevant `src/references/` file together, and keep cross-references valid. When you change the PostgreSQL reference, update `src/scripts/` and `src/references/reference-implementation.md` together.

When you change observable behavior, update `src/test-fixtures/verification-prompts.md` so the expectations still describe correct behavior.

When you add or rename a reference file, update the reference-loading guidance in `src/SKILL.md`.

Keep the example in `src/test-fixtures/` generic. Do not introduce a real application's domain schema.

## Documentation and Markdown rules

Write Markdown for humans, agents, and tools at once: real headings with no skipped levels, prose paragraphs of one to three sentences on a single line each, flat atomic lists, backticks for identifiers and paths, no bold used as a heading, no em dashes, and a language identifier on every code block.

On Windows, never redirect output to `nul`; use `/dev/null`, which Git Bash translates correctly.

## Workflow

Work on a branch and land changes through a pull request; do not push directly to `main`. Commit and push only when the user asks.

## Validation and release

Run `npm run validate` after any change to `src/`, `docs/`, `packaging/`, or the workflows. It checks the frontmatter, the manifests, the internal links, the release notes, and the workflow mode.

To release, follow `docs/RELEASING.md`: update the skill and references, update `README.md` and docs, add a `## [vX.Y.Z]` section to `CHANGELOG.md`, add `docs/releases/vX.Y.Z.md`, run `npm run validate`, then run `npm run package -- vX.Y.Z` and tag the release.
