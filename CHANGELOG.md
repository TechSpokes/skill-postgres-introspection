# Changelog

## [Unreleased]

- No unreleased changes.

## [v1.2.0]

- Lead the README with how to install the skill for normal use: download a ZIP from the Releases page and install the standalone skill, the Claude Code plugin, or the Codex plugin.
- Move the maintainer commands (`npm run validate`, `npm run package`) into a "For maintainers and contributors" section, so end users are not told to clone and build.
- Align `docs/INSTALL.md` with the Releases download path and name the asset for each install option.

## [v1.1.0]

- Document the release process and the repository workflow in `docs/RELEASING.md`, including how changes land, the `main` ruleset, the CI gate, and the tag-triggered draft release.
- Make `docs/RELEASING.md` the single source for the release process; `AGENTS.md` now points to it instead of repeating the steps, so the two cannot drift.
- Reconcile release instructions across `CONTRIBUTING.md` and the pull request template, and replace the hardcoded `npm run package -- v1.0.0` with a version-neutral `vX.Y.Z`.
- Record the branch protection setup: pull requests required, the `Validate skill package` check required, squash-only merges, linear history, and enforcement for administrators.

## [v1.0.0]

- First release of the `postgres-introspection` skill.
- Teach an agent to build a read-only database introspection tool inside the repository it works in, fitted to the repository's stack.
- Provide a runnable PostgreSQL reference implementation for the database, the cluster, a connection pooler, and a REST layer.
- Define the method and its invariants: read-only, sourced from live catalogs, deterministic, one model rendered many ways, one classification path.
- Document the commenting discipline for capturing the architect's intent as compact database comments, with the database as the source of truth.
- Document reading the state and using the reports with judgment, including the alignment loop and conflict handling.
- Establish data-safety rules: never reset or wipe a database, never touch production without informed consent, and route every database change through a migration with consent.
- Include a generic example and verification prompts.
