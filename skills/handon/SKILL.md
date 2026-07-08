---
name: handon
description: Run the `/handon` workflow for the current repository. Use when the user says `/handon`, "handon", "continue from last time", "restore context", or asks to resume work from repo-local handoff files without relying on prior chat history.
---

# Handon

Restore project context from repo-local handoff files. Do not modify code during the first response.

## Read First

Read these files when present:

```text
AGENTS.md
docs/HANDOFF/CURRENT.md
docs/HANDOFF/DECISIONS.md
docs/HANDOFF/TODO.md
README.md
```

Then check:

```bash
git status
git branch --show-current
git log --oneline -5
```

## Missing Handoff

If `docs/HANDOFF/CURRENT.md` is missing, say exactly:

```text
No handoff file found.

Expected:
docs/HANDOFF/CURRENT.md

Handon cannot restore the previous project state from handoff.
```

You may infer context from README, git log, and TODO only after clearly labeling it as inference.

## Branch Or Local Changes

If the current branch differs from the branch recorded in `CURRENT.md`, stop and ask for confirmation before modifying files.

If local uncommitted changes exist, say that local uncommitted changes were detected and summarize first. Do not modify files until the user confirms.

## Response Format

Return:

```md
# Handon Summary

## Current Objective

...

## Last Completed Work

...

## Current Blockers

...

## Key Files

- `path/to/file`: ...

## Risks

...

## Recommended Next Steps

1. ...
2. ...
3. ...

## Validation Plan

1. ...
2. ...

Ready to continue.
```

Wait for explicit confirmation such as "start", "continue", or "go ahead" before modifying code.
