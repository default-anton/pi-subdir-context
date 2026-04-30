# Changelog

All notable changes to `pi-subdir-context` are documented here.

## Format

- Keep `## [Unreleased]` at the top.
- Use release headers as `## [X.Y.Z] - YYYY-MM-DD`.
- Group entries under `### Added`, `### Changed`, `### Fixed` (optionally `### Removed` / `### Security`).
- Keep entries short and operator/user-facing.

## [Unreleased]

### Added

- Added support for loading `CLAUDE.md` as the lowest-priority subdirectory context fallback after `AGENTS.override.md` and `AGENTS.md`.

### Changed

- None.

### Fixed

- None.

## [1.1.5] - 2026-04-22

### Added

- None.

### Changed

- Updated `@mariozechner/pi-coding-agent` in peer and dev dependencies to `^0.69.0` for pi 0.69.0 compatibility. No source changes were needed because this extension does not use TypeBox or session-replacement APIs.

### Fixed

- None.

## [1.1.4] - 2026-04-21

### Added

- None.

### Changed

- Upgraded the GitHub Actions release workflow to `actions/checkout@v6` and `actions/setup-node@v6`.

### Fixed

- None.

## [1.1.3] - 2026-04-21

### Added

- None.

### Changed

- Updated `@mariozechner/pi-coding-agent` in peer and dev dependencies to `^0.68.0` for pi 0.68.0 compatibility.

### Fixed

- None.

## [1.1.2] - 2026-04-03

### Added

- None.

### Changed

- Updated `@mariozechner/pi-coding-agent` in peer and dev dependencies to `^0.65.0`.

### Fixed

- Removed the deprecated `session_switch` listener and now rely on `session_start` for pi 0.65.0 compatibility.

## [1.1.1] - 2026-03-27

### Added

- None.

### Changed

- Updated `@mariozechner/pi-coding-agent` in peer and dev dependencies to `^0.63.1`.

### Fixed

- None.

## [1.1.0] - 2026-03-05

### Added

- None.

### Changed

- AGENTS file discovery now treats `AGENTS.override.md` as `AGENTS.md` with higher precedence when both exist in the same directory.

### Fixed

- None.

## [1.0.5] - 2026-02-17

### Added

- None.

### Changed

- Updated `@mariozechner/pi-coding-agent` in peer and dev dependencies to `^0.53.0`.

### Fixed

- None.

## [1.0.4] - 2026-02-13

### Added

- None.

### Changed

- Updated `@mariozechner/pi-coding-agent` in peer and dev dependencies to `^0.52.12`.

### Fixed

- None.

## [1.0.3] - 2026-02-12

### Added

- Added automated GitHub Actions release workflow (`.github/workflows/release.yml`) triggered by stable `vX.Y.Z` tags.
- Added release validation and notes extraction scripts: `scripts/verify-release-tag.mjs` and `scripts/changelog-release-notes.mjs`.

### Changed

- Updated release process to use trusted publishing (`npm publish --provenance --access public`) from CI instead of manual local publishing.
- Added canonical npm release scripts (`release:verify-tag`, `release:notes`, `release:gate`) to `package.json`.

### Fixed

- None.
