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

Keep the first response brief. Return one compact summary, optional next steps, and a warm continue cue:

```md
I read the handoff. We are currently [one-sentence objective]. Last time, [one-sentence completed work]. The main remaining point is [one-sentence blocker/risk/next task].

Next:
1. ...
2. ...
3. ...

Ready to continue.
```

When responding in Chinese, end with the natural equivalent of "we can continue now."

Mention local uncommitted changes in one short sentence when present. Include key file names only when they are necessary for the next action.

Wait for explicit confirmation such as "start", "continue", or "go ahead" before modifying code.
