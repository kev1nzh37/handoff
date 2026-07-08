# Handoff for Pi

Handoff is a repo-local workflow, so Pi-compatible agents can use the same skill instructions:

```text
skills/handoff-handon/SKILL.md
```

For a local checkout, load this repository as a package or point Pi at this directory according to your Pi setup.

## Expected Behavior

- `/handoff` writes `docs/HANDOFF/CURRENT.md`.
- `/handon` reads handoff files and summarizes before modifying code.
- Secrets and sensitive operational details must not be written into handoff files.
