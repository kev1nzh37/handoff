# Handoff for OpenCode

OpenCode uses its own plugin configuration. Install Handoff separately even if you already use it in another harness.

## Quick Install

Add Handoff to the `plugin` array in your global or project-level `opencode.json`:

```json
{
  "plugin": ["handoff@git+https://github.com/kev1nzh37/handoff.git"]
}
```

Restart OpenCode after editing the config.

## Manual Use

If your OpenCode setup does not load this repository as a plugin yet, point OpenCode at:

```text
skills/handoff-handon/SKILL.md
```

Then ask it to follow the `/handoff` or `/handon` workflow.

## Verify

In a project repository, ask:

```text
/handon
```

If `docs/HANDOFF/CURRENT.md` does not exist, the agent should report that no handoff file was found and should not modify code.
