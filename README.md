# Postgres Introspection Skill

See your database clearly, keep the reasons behind it, and share both without a database or credentials.

This is an agent skill: a set of instructions an AI coding assistant loads to gain a new capability. This one teaches your assistant to read your database and write its current state into plain, readable files in your repository, and to record the reasons behind the design right next to the data. It is built for PostgreSQL and the method works for other databases too.

## What it gives you

A readable map of your database that stays current, so you and your AI tools stop piecing the truth together from migration files.

A picture you can share without access. Teammates and AI assistants can read, search, and review the schema with no running database and no credentials.

The "why" kept with the data. The reasons behind a design live in the database itself as short comments, not scattered across documents that drift out of date.

A history you can follow. Because the files are regenerated as the database changes, each change shows up as a clean, reviewable diff over time.

Safety by default. The skill tells the assistant to only read your database and to ask before anything that could affect your data.

## Install

You do not need to clone this repository. Download the latest release from the [Releases page](https://github.com/TechSpokes/skill-postgres-introspection/releases) and install the piece that matches your tool.

### Standalone skill (works across tools)

Download `postgres-introspection-vX.Y.Z.zip`, unzip it, and copy the `postgres-introspection/` folder into a skills directory in your repository:

- `.agents/skills/` is the cross-tool standard location, recognized by Codex, GitHub Copilot, and other compatible tools. Prefer this when several tools share one repository.
- `.claude/skills/` for Claude Code; use `~/.claude/skills/` to install it for all your projects.
- `.github/skills/` is also recognized by GitHub Copilot.

Keep the folder intact so the skill can find its supporting files.

### Claude Code plugin

Download `postgres-introspection-claude-plugin-vX.Y.Z.zip`, unzip it, and install it as a Claude Code plugin.

### Codex plugin

Download `postgres-introspection-codex-plugin-vX.Y.Z.zip`, unzip it, and install it as a Codex plugin.

For step-by-step help, see [docs/INSTALL.md](docs/INSTALL.md).

## Using it

Once installed, ask your assistant to set it up, for example:

```text
Set up database introspection in this repository.
```

The assistant confirms with you first, checks that you have a safe database to point at, fits the tooling to your project, generates the readable state files, and offers to keep them up to date as your database changes. For a walkthrough of what to expect, see [docs/QUICKSTART.md](docs/QUICKSTART.md).

## Your data stays safe

The skill instructs the assistant to treat your data as sacred: read-only access only, never resetting or wiping a database to get a clean state, never touching a production database without your clear and informed consent, and bringing any change to your schema, security, or indexing to you instead of deciding alone.

What an assistant ultimately does is outside this project's control. The skill's job is to make these the rules it is told to follow.

## What you get

Plain files under a `state/` folder in your repository: one navigable data file, one complete document of the whole schema, and one self-contained file per table, view, and function. You can open them, search them, paste one into a review, or hand them to another AI tool, all without opening the database.

## Learn more

- [docs/PURPOSE.md](docs/PURPOSE.md) for why this skill exists and what it gives you, especially as a new developer.
- [docs/QUICKSTART.md](docs/QUICKSTART.md) and [docs/INSTALL.md](docs/INSTALL.md) to get started.
- [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) and [docs/FOUNDATIONS.md](docs/FOUNDATIONS.md) to understand the design and the ideas behind it.
- [docs/ROADMAP.md](docs/ROADMAP.md), [docs/HOW-THIS-SKILL-WAS-BUILT.md](docs/HOW-THIS-SKILL-WAS-BUILT.md), and [docs/ABOUT.md](docs/ABOUT.md) for where it is going and who builds it.
- [SUPPORT.md](SUPPORT.md) and [SECURITY.md](SECURITY.md) for help and reporting.

## For maintainers and contributors

These steps are for working on this repository, not for installing the skill. Clone the repository, then validate the package:

```bash
npm run validate
```

Build the release assets for a tag:

```bash
npm run package -- vX.Y.Z
```

Assets are written to `dist/assets/`. The contribution and release process is in [CONTRIBUTING.md](CONTRIBUTING.md) and [docs/RELEASING.md](docs/RELEASING.md).

## Credits and license

Authored and maintained by TechSpokes. See [docs/ABOUT.md](docs/ABOUT.md) for the people and companies behind the skill and [docs/PROVENANCE.md](docs/PROVENANCE.md) for attribution. This repository is licensed under the terms in [LICENSE](LICENSE).
