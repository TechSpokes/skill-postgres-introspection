# Changelog

## [Unreleased]

- No unreleased changes.

## [v1.0.0]

- First release of the `postgres-introspection` skill.
- Teach an agent to build a read-only database introspection tool inside the repository it works in, fitted to the repository's stack.
- Provide a runnable PostgreSQL reference implementation for the database, the cluster, a connection pooler, and a REST layer.
- Define the method and its invariants: read-only, sourced from live catalogs, deterministic, one model rendered many ways, one classification path.
- Document the commenting discipline for capturing the architect's intent as compact database comments, with the database as the source of truth.
- Document reading the state and using the reports with judgment, including the alignment loop and conflict handling.
- Establish data-safety rules: never reset or wipe a database, never touch production without informed consent, and route every database change through a migration with consent.
- Include a generic example and verification prompts.
