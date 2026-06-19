# Postgres Introspection Skill

This repository packages an agent skill that teaches an AI coding agent to build a database introspection capability inside whatever repository it is working in. The skill is database-agnostic in method, with a runnable PostgreSQL reference implementation.

## What introspection is

Introspection is a read-only tool that reads a live database's catalogs and renders the current structure, security (row-level security, roles, grants), views, functions, and extensions into committed, navigable files. It is generated from the live database, not authored by hand, so it always reflects reality.

It is distinct from two neighbors. Validation asserts that reality matches an expectation and answers yes or no. Documentation records intent and is written by a person. This skill builds introspection only.

## Why it exists

The real state of a database-backed system lives in the database, yet it is hard to see: the authoritative record is usually a large dump and a history of migrations, and the architect's reasons behind the schema are not stored anywhere at all. This skill closes both gaps. It gives the repository a tool that exports the current state into files anyone can read, and a discipline for capturing the architect's intent as comments next to the data.

The committed output has two properties that make it valuable. It is shareable offline: anyone can read, search, and diff the schema with no running database and no credentials, which lets teams and different AI agents reason about the database together. It is a time series: because the output is deterministic and stamped with the migration version, the git history becomes a reviewable record of how the database evolved.

## What the skill produces in a target repository

A runnable introspection tool fitted to the repository's own stack, which keeps working after this skill is gone.

Committed state files: a single navigable data file, a single complete document, and a per-object file per table, view, and function.

Generation wired to the migration run, and an entry in the repository's agent instructions so future agents find the capability and read the state instead of reconstructing it.

## How a human drives it

Ask an AI coding agent that has this skill to set up database introspection in your repository. Following the skill, the agent confirms with you before building anything, checks that you have a safe database to point at, fits the tool to your stack, generates the committed state, captures intent in comments through migrations with your consent, and wires generation to your migration process.

The skill instructs the agent to treat your data as sacred: to read the database read-only, never reset or wipe a database to obtain a clean state, never touch production without your explicit, informed consent, and bring decisions about schema, security, and indexing to you rather than taking them on its own. What any given agent actually does is outside this project's control; the skill makes these the rules it is told to follow.

## The skill package

- `src/SKILL.md` is the canonical skill entry point.
- `src/references/` holds the method, the reference implementation guide, the reading and judgment guides, the commenting discipline, the layers guide, the other-databases guide, and the agent-instructions integration.
- `src/scripts/` is the runnable PostgreSQL reference implementation to read and adapt.
- `src/test-fixtures/` holds a generic example and verification prompts.

## Documentation

- [docs/QUICKSTART.md](docs/QUICKSTART.md) - Install the skill and run it against a repository.
- [docs/INSTALL.md](docs/INSTALL.md) - Standalone and plugin installation.
- [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) - The skill's design, goal, and structure.
- [docs/RELEASING.md](docs/RELEASING.md) - Release checklist and packaging.
- [docs/VERSION.md](docs/VERSION.md) - Versioning and tag format.
- [docs/PROVENANCE.md](docs/PROVENANCE.md) - Attribution and distilled sources.
- [CONTRIBUTING.md](CONTRIBUTING.md), [SUPPORT.md](SUPPORT.md), [SECURITY.md](SECURITY.md).

## Background and project

- [docs/HOW-THIS-SKILL-WAS-BUILT.md](docs/HOW-THIS-SKILL-WAS-BUILT.md) - Its origin, the template that generated it, and how it was refined.
- [docs/FOUNDATIONS.md](docs/FOUNDATIONS.md) - The frameworks that shaped the skill, at a conceptual level.
- [docs/ROADMAP.md](docs/ROADMAP.md) - Where the skill is heading and why.
- [docs/ABOUT.md](docs/ABOUT.md) - The people and companies behind it.

## Validation

Run:

```bash
npm run validate
```

## Packaging

Run:

```bash
npm run package -- vX.Y.Z
```

Use the intended release tag. Packaging writes release assets to `dist/assets/`.

## Author

Authored and maintained by TechSpokes. See [docs/ABOUT.md](docs/ABOUT.md) for the people and companies behind the skill, and [docs/PROVENANCE.md](docs/PROVENANCE.md) for attribution.

## License

This repository is licensed under the terms in [LICENSE](LICENSE).
