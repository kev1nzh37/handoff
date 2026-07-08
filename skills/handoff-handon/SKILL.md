---
name: handoff-handon
description: Create and restore repo-local coding handoffs for Codex, GPT, Claude, or other agentic development sessions. Use when the user says `/handoff`, `handoff`, "prepare a handoff", "ready to leave work", `/handon`, `handon`, "continue from last time", "restore context", or asks to preserve or resume project state across machines, sessions, or chat history loss.
---

# Handoff / Handon

## Overview

Use repo-local markdown files to preserve only the information needed to continue work in a fresh session. Do not save full chat history, secrets, or a chronological transcript.

Default project files:

```text
AGENTS.md
docs/HANDOFF/CURRENT.md
docs/HANDOFF/DECISIONS.md
docs/HANDOFF/TODO.md
```

`CURRENT.md` is the core handoff artifact. It should let a new machine, new agent, or new context window recover the current objective, recent work, risks, next steps, and validation plan in about three minutes.

## Workflow Decision

- If the user asks for `/handoff` or is ending a work session, run the Handoff workflow.
- If the user asks for `/handon` or wants to continue from a previous handoff, run the Handon workflow.
- If the repo does not yet contain the handoff files and the user asks to set up the workflow, create the structure using `references/templates.md`.
- If the request is ambiguous, infer from intent: leaving/saving state means handoff; returning/restoring state means handon.

## Handoff Workflow

When creating or updating a handoff:

1. Inspect project state before writing:

```bash
git status
git diff --stat
git diff
git log --oneline -5
```

2. Read existing context when present:

```text
README.md
AGENTS.md
docs/HANDOFF/TODO.md
docs/HANDOFF/DECISIONS.md
docs/HANDOFF/CURRENT.md
```

3. Inspect recently changed core files as needed to understand the actual implementation state.
4. Create `docs/HANDOFF/` if missing.
5. Update `docs/HANDOFF/CURRENT.md` using the Current Handoff template in `references/templates.md`.
6. Update `docs/HANDOFF/TODO.md` or `docs/HANDOFF/DECISIONS.md` only when the user request or discovered project state clearly requires it.
7. Keep the final response short. Do not paste the full handoff unless the user asks.

Required final response shape:

```text
Handoff completed.

Updated:
docs/HANDOFF/CURRENT.md
```

List additional updated handoff files only if they were actually changed.

## Handon Workflow

When restoring context:

1. Read:

```text
AGENTS.md
docs/HANDOFF/CURRENT.md
docs/HANDOFF/DECISIONS.md
docs/HANDOFF/TODO.md
README.md
```

2. Check:

```bash
git status
git branch --show-current
git log --oneline -5
```

3. If `docs/HANDOFF/CURRENT.md` is missing, say exactly:

```text
No handoff file found.

Expected:
docs/HANDOFF/CURRENT.md

Handon cannot restore the previous project state from handoff.
```

You may infer context from README, git log, and TODO only after clearly labeling it as inference.

4. If the current branch differs from the branch recorded in `CURRENT.md`, stop and ask for branch confirmation before modifying files.
5. If local uncommitted changes exist, state that handon will summarize first and will not modify files until confirmed.
6. Output a short handon recap using the concise format in `references/templates.md`.
7. Do not modify code or project files during the first handon response. Wait until the user explicitly confirms with words such as "start", "continue", "go ahead", or equivalent non-English confirmation phrases.

## Safety Rules

Never write these into handoff files:

```text
API keys
tokens
cookies
passwords
private keys
.env actual values
auth.json contents
database credentials
company-sensitive information
```

If suspicious sensitive material is encountered, describe it abstractly:

```md
- Sensitive credentials were detected during the session, but they were not written into this handoff.
- Check local environment files before sharing or committing.
```

Avoid recording sensitive usernames, internal account names, production hostnames, or private filesystem paths when a generic description is enough.

## References

- Read `references/templates.md` when creating missing handoff files or formatting `CURRENT.md`, `DECISIONS.md`, `TODO.md`, AGENTS guidance, or the Handon summary.
