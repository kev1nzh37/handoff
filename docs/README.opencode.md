# Handoff for OpenCode

OpenCode users should follow:

```text
.opencode/INSTALL.md
```

The short version is to add this repository to the `plugin` array in `opencode.json`:

```json
{
  "plugin": ["handoff@git+https://github.com/kev1nzh37/handoff.git"]
}
```

Then restart OpenCode.

## Verify

Run `/handon` in a project. If no handoff exists yet, the agent should report:

```text
No handoff file found.

Expected:
docs/HANDOFF/CURRENT.md

Handon cannot restore the previous project state from handoff.
```
