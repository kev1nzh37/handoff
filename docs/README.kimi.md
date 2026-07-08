# Handoff for Kimi Code

Handoff includes Kimi-compatible plugin metadata at:

```text
.kimi-plugin/plugin.json
```

## Installation

Use Kimi Code's plugin manager to install this repository:

```text
/plugins install https://github.com/kev1nzh37/handoff
```

Then use:

```text
/handoff
```

or:

```text
/handon
```

## Behavior

- `/handoff` updates `docs/HANDOFF/CURRENT.md`.
- `TODO.md` is updated only when the task list changed or follow-up work was discovered.
- `DECISIONS.md` is updated only when a durable project decision was made or confirmed.
- `/handon` summarizes context first and does not modify code until you confirm.
