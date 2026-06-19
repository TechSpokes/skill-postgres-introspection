# How this skill was built

This skill has an origin, a generator, and a refinement process. This page records all three. It will be enriched when the full skill-builder template is published.

## Origin

The method came from real work, not from theory alone. It grew out of designing a PostgreSQL-native data layer for legal-document analysis at LAWXER, where the public surface was views and functions and the security was row-level security on private tables. The real contract and boundary lived in the database catalog, not in the application code, and there was no easy, credential-free way to see the current state or to record the reasons behind it. Introspection was built to solve that, and this skill generalizes it into a reusable method.

## Generator

The repository was generated from the [Skill Base Template](https://github.com/TechSpokes/skill-base-template), a public TechSpokes template that turns raw intake into a structured, validated, releasable agent-skill repository. The template's workflow moves from intake to a bootstrap build to release: source material goes into an intake area, an AI coding agent assesses its adequacy and builds the skill package, and validation and packaging produce release assets. After the build, the repository is converted from template mode into a standalone skill repository.

## Refinement

The generated skill was then refined through an iterative conversation with an AI coding agent. That process is where the skill's distinctive commitments took shape: data safety as a hard rule, the database as the single source of truth for both data and intent, capturing the architect's hidden reasons as compact database comments, and a judgment discipline that diagnoses and confirms rather than changing the data layer on its own. The frameworks behind these choices are described in [FOUNDATIONS.md](FOUNDATIONS.md).

## More to come

A deeper account of the skill-builder template and the bootstrap method will be added here once that material is published.
