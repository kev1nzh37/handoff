# Changelog

## 1.0.5 - 2026-07-08

### Changed

- Refined promotion copy to better match Vibe Coding communities and added `docs/HANDOFF/` to `.gitignore`.

## 1.0.4 - 2026-07-08

### Added

- Promotion copy for GitHub, X, Hacker News, Reddit, and Chinese communities.
- Example Codex plugin marketplace metadata.
- README workflow diagrams that explain the cross-machine handoff flow at a glance.

## 1.0.3 - 2026-07-08

### Changed

- Documented the cross-machine workflow: `/handoff` writes repo-local files, so users must commit and push `docs/HANDOFF/` or otherwise sync those files before running `/handon` on another computer.

## 1.0.2 - 2026-07-08

### Changed

- Made `/handon` output shorter: a concise context recap, a few next steps, and a friendly "we can continue" close instead of a full report-style summary.

## 1.0.1 - 2026-07-08

### Added

- Dedicated `handoff` and `handon` skill entry points so Codex can expose `/handoff` and `/handon` as enabled skill slash entries.

### Changed

- Documentation now describes `/handoff` and `/handon` as dedicated skill slash entries instead of relying only on the combined `handoff-handon` skill.

## 1.0.0 - 2026-07-08

First public release.

### Added

- Codex plugin manifest.
- Claude Code, Cursor-compatible, and Kimi plugin metadata.
- Claude, Gemini, OpenCode, and Pi instruction entry points.
- `handoff-handon` skill.
- `/handoff` workflow for updating `docs/HANDOFF/CURRENT.md`.
- `/handon` workflow for restoring context without immediately modifying code.
- Templates for `CURRENT.md`, `DECISIONS.md`, `TODO.md`, AGENTS guidance, and Handon summaries.
- Safety rules for avoiding secrets and sensitive operational data in handoff files.
