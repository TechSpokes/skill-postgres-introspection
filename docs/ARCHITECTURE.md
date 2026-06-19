# Architecture

This document explains the design of the `postgres-introspection` skill: its global goal, the three capabilities it transfers, how the package is organized, and why it is shaped that way. It is the design authority for maintenance; `src/SKILL.md` is the runtime implementation and should stay aligned with it.

## Global goal

Make the database the single living source of truth for both the data and the intent behind its shape, and give any intelligence, human or AI, across teams, a safe, current, shareable view of that truth without a running database or credentials, so that every decision about the data layer is grounded, aligned to the repository's real goals, and never taken at the expense of the data or the operability of the database.

## The two problems

The skill addresses two problems at once. The first is a tooling gap: there is rarely an easy, read-only way to see the current state of a database, so the truth lives in a large dump and a history of migrations. The second is an intent gap: the architect's reasons behind the schema are not in the database at all. The tool solves the first; the commenting discipline solves the second.

## Three capabilities

The skill transfers three intertwined capabilities, not a single recipe.

It teaches the agent to build a read-only introspection tool in the repository, fitted to the repository's own stack, which exports the current state into committed, navigable files.

It teaches the agent to capture the architect's hidden intent directly in the database as the authoritative record, with documentation deriving from it.

It teaches the agent to read the exported state with judgment, running an alignment loop that surfaces gaps and conflicts against the repository's goals, confirms with the user, and never changes schema, security, or indexing unilaterally.

## Design values

- The database is authoritative; intent lives next to the data, and docs derive from it.
- The data is sacred; the tool reads read-only and never risks data or operability without informed consent.
- Judgment is shared; the agent diagnoses, grounds, recommends, and confirms, and never silently defers.
- Every database change, including a comment, flows through a migration with consent.
- The method is portable; the PostgreSQL scripts are a worked example, not a mandate.

## Package layout

`src/SKILL.md` is the canonical entry point and is kept short. It carries the goal stack, the defined terms, the gates, the workflow, and pointers into the references.

`src/references/` carries the durable detail, one focused file per concern, loaded only when a step needs it. This is progressive disclosure: the entry point activates the skill and orients the agent, while references protect the context budget until depth is required.

`src/scripts/` is the runnable PostgreSQL reference implementation, one file per pipeline stage, so the agent can read how each invariant becomes code and then translate it into the host's stack.

`src/test-fixtures/` holds a generic example and verification prompts that confirm the skill still behaves correctly after a change.

## Why this shape

The invariants in `references/approach.md` (read-only, sourced from live catalogs, deterministic, one model rendered many ways, one classification path) are what make the output trustworthy and addressable. The entry point leads with the must-know and the gates so a skimming agent cannot miss the confirm-first and data-safety rules. References lead with the point and then the rationale, so an agent that loads one file still gets the goal it needs to make good local decisions. The generated output follows minimal, greppable Markdown so it stays parseable by humans, agents, and tools, and its heading outline serves as a cheap map.

## Maintenance implication

Keep the runtime implementation in `src/SKILL.md` aligned with this design. When a change alters the design rather than the implementation, update this document so future maintainers can tell the difference. Preserve the rationale that supports local judgment; drop detail that no longer serves the skill.
