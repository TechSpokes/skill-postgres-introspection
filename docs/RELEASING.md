# Releasing

This document describes how to release the `postgres-introspection` skill.

## Release goal

Release assets should contain only what an agent host needs to install and use the skill. The process protects skill portability by packaging the runtime skill cleanly, and maintainer confidence by requiring a changelog entry and release notes.

## Release checklist

- Update `src/SKILL.md` and the relevant files in `src/references/` and `src/scripts/`.
- Update `README.md` and the files in `docs/`.
- Add a `## [vX.Y.Z]` section to `CHANGELOG.md`.
- Add `docs/releases/vX.Y.Z.md`.
- Update the version in `package.json` and both `packaging/*/plugin.json`.
- Run `npm run validate`.
- Tag the release with `vX.Y.Z`.

Each item keeps repository state, package metadata, and release history synchronized.

## Local packaging

Run:

```bash
npm run package -- v1.0.0
```

Use the intended tag. Assets are written to `dist/assets/`.

## GitHub release

Pushing a `vX.Y.Z` tag runs `.github/workflows/release-draft.yml`. The workflow validates the skill, packages assets, creates or updates a draft release from `docs/releases/vX.Y.Z.md`, and uploads the ZIP assets. It requires a matching `## [vX.Y.Z]` section in `CHANGELOG.md`.
