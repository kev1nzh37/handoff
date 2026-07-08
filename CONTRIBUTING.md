# Contributing

Thanks for helping improve Handoff.

## Principles

- Keep the workflow small and repo-local.
- Preserve `/handoff` as a compact state summary, not a chat transcript.
- Preserve `/handon` as read-and-summarize first; do not make it modify code before user confirmation.
- Avoid adding network services, automatic commits, automatic pushes, or automatic branch switching to the core MVP.
- Do not introduce examples that contain secrets, private hostnames, or real credentials.

## Development

The main skill lives in:

```text
skills/handoff-handon/SKILL.md
```

Long templates live in:

```text
skills/handoff-handon/references/templates.md
```

After changing the plugin or skill, run the validators documented in `README.md`.

## Pull Requests

Good pull requests usually include:

- A clear description of the behavior change.
- Any template updates needed to support the behavior.
- Notes about manual validation with `/handoff` or `/handon`.

Small, focused changes are easiest to review.
