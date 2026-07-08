# Handoff

[English](README.md) | [简体中文](README.zh-CN.md)

Handoff is a Codex plugin for restoring coding context across machines, agent sessions, and context resets.

It gives coding agents a small workflow pair:

- `/handoff`: compress the current repository state into `docs/HANDOFF/CURRENT.md`.
- `/handon`: restore context from the handoff files before changing code.

Handoff does not save full chat history. It keeps only the state another session needs to continue the work: the current objective, completed work, unfinished work, risks, key files, next steps, and validation plan.

## Why

Agentic coding often breaks down when work moves between a laptop and desktop, or when a long chat is lost. The useful state is usually not the whole conversation. It is a compact project handoff that lives in the repo and can be read by any future session.

Handoff standardizes that handoff.

## Status

Version: `1.0.0`

This is the first public release. The workflow contract is stable, and the implementation is intentionally small:

- No chat transcript sync.
- No automatic commits or pushes.
- No automatic branch switching.
- No remote host management.
- No external service dependency.

## Supported Agents

The workflow is intentionally repo-local and agent-agnostic. Any coding agent that can read project files and follow markdown instructions can use the handoff files.

Packaged entry points in this repository:

- Codex: `.codex-plugin/plugin.json`
- Claude Code: `.claude-plugin/plugin.json` and `CLAUDE.md`
- Cursor-compatible plugin layout: `.cursor-plugin/plugin.json`
- Gemini-style instruction pointer: `GEMINI.md`
- Kimi Code: `.kimi-plugin/plugin.json`
- OpenCode: `.opencode/INSTALL.md`
- Pi-compatible package notes: `docs/README.pi.md`

Install support differs by app. Like Superpowers, each harness may need its own installation path.

## Installation

Install this repository as a local Codex plugin using the plugin installation flow available in your Codex environment.

For local development, clone the repository:

```bash
git clone https://github.com/kev1nzh37/handoff.git
```

Then point Codex at the cloned plugin folder or install it through your configured local plugin marketplace.

Platform-specific notes:

- Codex: install this repository as a local Codex plugin.
- Claude Code: install this repository as a Claude plugin, then use `/handoff` or `/handon`.
- Cursor: use the Cursor-compatible plugin metadata in `.cursor-plugin/`.
- Gemini: point the agent at `GEMINI.md`.
- Kimi Code: install from this repository with Kimi's plugin manager.
- OpenCode: follow `.opencode/INSTALL.md`.
- Pi: see `docs/README.pi.md`.

## Usage

In a repository where you are working with Codex:

```text
/handoff
```

Codex inspects the repo and updates:

```text
docs/HANDOFF/CURRENT.md
```

`CURRENT.md` is always the primary output. `docs/HANDOFF/TODO.md` and `docs/HANDOFF/DECISIONS.md` are updated only when there is a clear reason:

- update `TODO.md` when the task list changed or new follow-up work was discovered;
- update `DECISIONS.md` when a durable project decision was made or confirmed.

When returning in a fresh session:

```text
/handon
```

Codex reads the handoff files, summarizes the current state, and waits for confirmation before modifying code.

## Project Handoff Files

Handoff expects projects to use:

```text
AGENTS.md
docs/
  HANDOFF/
    CURRENT.md
    DECISIONS.md
    TODO.md
```

File roles:

- `AGENTS.md`: project rules, conventions, commands, and constraints.
- `docs/HANDOFF/CURRENT.md`: current handoff state, updated often.
- `docs/HANDOFF/DECISIONS.md`: durable decisions, updated rarely.
- `docs/HANDOFF/TODO.md`: task pool.

## Safety

Handoff instructs Codex not to write secrets or sensitive operational details into handoff files, including:

- API keys
- tokens
- cookies
- passwords
- private keys
- `.env` values
- database credentials
- production configuration

If sensitive material is detected, the handoff should only record an abstract warning.

## Examples

- [`examples/current.md`](examples/current.md): example `docs/HANDOFF/CURRENT.md`
- [`examples/handon-summary.md`](examples/handon-summary.md): example `/handon` response

## Plugin Structure

```text
.codex-plugin/plugin.json
.claude-plugin/plugin.json
.cursor-plugin/plugin.json
.kimi-plugin/plugin.json
.opencode/INSTALL.md
CLAUDE.md
GEMINI.md
docs/
  README.kimi.md
  README.opencode.md
  README.pi.md
skills/
  handoff-handon/
    SKILL.md
    agents/openai.yaml
    references/templates.md
```

## Development

If you are developing this plugin with Codex's plugin and skill creator tooling, run the relevant validators from your local Codex tools checkout.

Validate the plugin manifest:

```bash
python /path/to/plugin-creator/scripts/validate_plugin.py .
```

Validate the skill:

```bash
python /path/to/skill-creator/scripts/quick_validate.py skills/handoff-handon
```

## License

MIT
