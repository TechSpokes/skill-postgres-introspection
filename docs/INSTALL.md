# Install

The skill installs as a standalone skill folder or as a plugin package. Download the latest release from the [Releases page](https://github.com/TechSpokes/skill-postgres-introspection/releases) and use the asset that matches your tool, rather than cloning the whole repository, so you get only the runtime skill. Each release attaches three ZIP files: the standalone skill, the Claude plugin, and the Codex plugin.

## Installation goal

Keep the skill directory intact so `SKILL.md` can find its referenced resources. The references, scripts, and fixtures load only when needed, but they must stay next to `SKILL.md` for relative paths to resolve.

## Standalone skill

Download `postgres-introspection-vX.Y.Z.zip`, unzip it, and copy the `postgres-introspection/` folder into a supported skill location. Common locations include:

- `.github/skills/`
- `.codex/skills/`
- `.claude/skills/`

Keep `SKILL.md` and its support folders together.

## Codex plugin

Download `postgres-introspection-codex-plugin-vX.Y.Z.zip` from the release and unzip it. The package contains `.codex-plugin/plugin.json` and a `skills/` directory. Install it as a Codex plugin.

## Claude plugin

Download `postgres-introspection-claude-plugin-vX.Y.Z.zip` from the release and unzip it. The package contains `.claude-plugin/plugin.json` and a `skills/` directory. Install it as a Claude Code plugin.

## Removing the skill after setup

This skill can install introspection tooling directly into a repository. Once that tooling exists in the repository and works on its own, you may remove the skill if it was installed locally to that repository. A globally installed copy should stay, because it serves other repositories.
