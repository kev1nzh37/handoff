---
name: handoff
description: Run the `/handoff` workflow for the current repository. Use when the user says `/handoff`, "handoff", "prepare a handoff", "save current project state", or indicates they are ending a coding session and want the next session to continue from repo-local handoff files.
---

# Handoff

Create or update a concise repo-local handoff for the current project.

## Output Files

Always update:

```text
docs/HANDOFF/CURRENT.md
```

Update only when clearly needed:

```text
docs/HANDOFF/TODO.md
docs/HANDOFF/DECISIONS.md
```

Use `TODO.md` when the task list changed or new follow-up work was discovered. Use `DECISIONS.md` when a durable project decision was made or confirmed.

## Workflow

1. Inspect repository state:

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
docs/HANDOFF/CURRENT.md
docs/HANDOFF/TODO.md
docs/HANDOFF/DECISIONS.md
```

3. Inspect recently changed important files as needed.
4. Create `docs/HANDOFF/` if missing.
5. Write `docs/HANDOFF/CURRENT.md` with:
   - current objective
   - completed work
   - unfinished work
   - blockers
   - important files
   - validation status
   - next steps
   - constraints and warnings
   - suggested handon prompt
6. Do not copy full chat history or write a chronological transcript.
7. Do not include secrets or sensitive operational details.

## Safety

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

If suspicious sensitive material is encountered, record only an abstract warning.

## Final Response

Keep the final response short:

```text
Handoff completed.

Updated:
docs/HANDOFF/CURRENT.md
```

List `docs/HANDOFF/TODO.md` or `docs/HANDOFF/DECISIONS.md` only if they were actually changed.
