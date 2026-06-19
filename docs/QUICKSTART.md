# Quickstart

This skill teaches an AI coding agent to build a database introspection capability inside a repository. This page shows how to install it and what to expect when you run it.

## Install the skill

Install the skill into a location your agent host reads. See [INSTALL.md](INSTALL.md) for standalone and plugin options. Keep `SKILL.md` and its `references/`, `scripts/`, and `test-fixtures/` folders together so relative paths resolve.

## Use it on a repository

Open the repository whose database you want to introspect, and ask the agent to set up database introspection. A request like "set up database introspection in this repository" activates the skill.

The agent confirms with you before building anything, checks that you have a safe database to point at, fits the tool to your repository's stack, generates the committed state, and offers to wire generation to your migration process.

## What to expect from the agent

The skill directs the agent to read your database read-only and never to reset, wipe, or run migrations against a database with real data to obtain a clean state, and never to touch a production database without your explicit, informed consent.

It captures the intent behind schema decisions as compact database comments, applied through migrations with your consent, and treats the database as the source of truth from which documentation derives.

When it finds gaps or conflicts between the database, the code, and the documentation, it surfaces them with evidence and a recommendation and asks you how to proceed, rather than changing schema, security, or indexing on its own.

## What you get

A runnable introspection tool that lives in your repository and keeps working without this skill, committed state files you can read and share without a database or credentials, and an entry in your repository's agent instructions so future agents find the capability.

## Related

- [INSTALL.md](INSTALL.md) - Installation options.
- [ARCHITECTURE.md](ARCHITECTURE.md) - The skill's design and goal.
