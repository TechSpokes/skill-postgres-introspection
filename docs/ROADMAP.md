# Roadmap

This roadmap describes a direction, not dated commitments. It exists so contributors and users can see where the skill is heading and why.

## Global goal

Make the data layer easier for AI agents to work with and safer for people, especially newcomers, to operate. The database should be a single living source of truth for both its data and the intent behind its shape, readable and shareable without a running database or credentials, and every change to it should be grounded, aligned to the repository's goals, and safe.

## Shipped in v1.0

The introspection method and its invariants, a runnable PostgreSQL reference implementation, the commenting discipline for capturing intent, the judgment and alignment loop, the data-safety rules, and the offline sharing and time-series properties of the committed state.

## Lower the barrier for new users

A guided first run that explains each step and every safety check in plain language, so a user who does not know what a data layer is can still set up introspection without risking their data. Reports phrased for people, not only for tools.

## Broaden reach

Reference adapters for more databases, starting with MySQL, SQLite, and SQL Server, that keep the method while changing the catalog source. Autodetection of common migration tools. Worked examples for wiring introspection into continuous integration.

## Deepen value

Tooling for the structured side of comments, so intent can be surfaced to the right audience. Drift and time-series reports built from the committed state, so a reviewer sees not only the current schema but how it changed and where it diverges from intent.

## Horizon

Data-layer health summaries that read the state against a repository's stated goals and constraints, and companion capabilities for the two neighbors this skill deliberately excludes: validation, which asserts that reality matches an expectation, and documentation derivation, which keeps human docs in step with the database.

## Invariants across the roadmap

Safety comes first; the database is the source of truth; intent lives next to the data; and the agent diagnoses and confirms rather than changing the data layer on its own. No item on this roadmap may weaken these.
