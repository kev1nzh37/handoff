# Handoff Plugin Development

This repository contains a Codex plugin that provides the `handoff-handon` skill.

## Project Shape

- `.codex-plugin/plugin.json`: Codex plugin manifest.
- `.claude-plugin/plugin.json`: Claude Code plugin metadata.
- `.cursor-plugin/plugin.json`: Cursor-compatible plugin metadata.
- `.kimi-plugin/plugin.json`: Kimi Code plugin metadata.
- `.opencode/INSTALL.md`: OpenCode installation entry point.
- `CLAUDE.md` and `GEMINI.md`: agent-specific instruction entry points.
- `docs/README.*.md`: platform-specific installation notes.
- `skills/handoff/SKILL.md`: dedicated handoff entry point.
- `skills/handon/SKILL.md`: dedicated handon entry point.
- `skills/handoff-handon/SKILL.md`: combined compatibility skill instructions.
- `skills/handoff-handon/references/templates.md`: reusable handoff and handon templates.
- `skills/handoff-handon/agents/openai.yaml`: Codex UI metadata for the skill.

## Development Rules

- Keep the skill concise; move long templates or examples into `references/`.
- Do not store secrets, private machine details, or full chat transcripts in generated handoff content.
- Preserve `/handon` as a read-and-summarize workflow until the user explicitly confirms implementation should continue.
- Validate both the plugin manifest and the skill before calling the work complete.

## Validation

```bash
python /path/to/plugin-creator/scripts/validate_plugin.py .
python /path/to/skill-creator/scripts/quick_validate.py skills/handoff-handon
```
