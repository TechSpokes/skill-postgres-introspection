# Install

The skill installs as a standalone skill folder or as a plugin package. Install the contents of a release ZIP rather than cloning the whole repository, so you get only the runtime skill.

## Installation goal

Keep the skill directory intact so `SKILL.md` can find its referenced resources. The references, scripts, and fixtures load only when needed, but they must stay next to `SKILL.md` for relative paths to resolve.

## Standalone skill

Copy the skill folder from the standalone release ZIP into a supported skill location. Common locations include:

- `.github/skills/`
- `.codex/skills/`
- `.claude/skills/`

Keep `SKILL.md` and its support folders together.

## Codex plugin

Use the Codex plugin ZIP from the release. The package contains `.codex-plugin/plugin.json` and a `skills/` directory.

## Claude plugin

Use the Claude plugin ZIP from the release. The package contains `.claude-plugin/plugin.json` and a `skills/` directory.

## Removing the skill after setup

This skill can install introspection tooling directly into a repository. Once that tooling exists in the repository and works on its own, you may remove the skill if it was installed locally to that repository. A globally installed copy should stay, because it serves other repositories.
