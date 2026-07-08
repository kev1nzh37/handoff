# Handoff / Handon Templates

Use these templates verbatim where practical. Keep generated content concise and specific to the project.

## CURRENT.md

```md
# Current Handoff

## Updated At

YYYY-MM-DD HH:mm

## Project

Project name:

## Branch

Branch:

## Current Objective

Describe the current objective in one or two sentences.

## Completed In This Session

- What was completed.
- Which files were changed.
- What behavior or feature is now working.

## Not Completed Yet

- What is still unfinished.
- What is partially implemented.
- What still needs review or validation.

## Current Blockers

- What is blocking progress.
- What has already been tried.
- What should not be retried unless new information appears.

## Important Files

- `path/to/file`: Why this file matters.
- `path/to/file`: What changed here.
- `path/to/file`: What to inspect next.

## Validation Status

### Verified

- Commands, tests, builds, or manual checks that passed.

### Not Yet Verified

- Checks that still need to be run.

### Known Issues

- Known bugs, risks, regressions, or suspicious behavior.

## Next Steps

1. First recommended next action.
2. Second recommended next action.
3. How to verify the result.

## Constraints And Warnings

- Things that should not be changed.
- Architecture or style constraints.
- Risky areas.
- Environment-specific notes.

## Suggested Handon Prompt

Read `AGENTS.md`, `docs/HANDOFF/CURRENT.md`, `docs/HANDOFF/DECISIONS.md`, and `docs/HANDOFF/TODO.md`.

Do not modify code yet.

First summarize:
1. The current objective.
2. What was completed last time.
3. The current blockers.
4. The key files.
5. The next recommended steps.
6. The validation plan.
```

## Handon Summary

```md
I read the handoff. We are currently [one-sentence objective]. Last time, [one-sentence completed work]. The main remaining point is [one-sentence blocker/risk/next task].

Next:
1. ...
2. ...
3. ...

我们继续吧。
```

## Cross-Machine Note

Use this note only when relevant:

```text
Handoff writes repo-local files only. To continue on another machine, commit and push `docs/HANDOFF/` or sync those files before running `/handon`.
```

## DECISIONS.md

```md
# Decisions

## YYYY-MM-DD - Decision Title

### Decision

What was decided.

### Reason

Why this decision was made.

### Impact

What future work should follow this decision.

### Do Not Revisit Unless

When this decision should be reconsidered.
```

## TODO.md

```md
# TODO

## Now

- [ ] Highest priority task.
- [ ] Next task.

## Later

- [ ] Lower priority task.
- [ ] Nice-to-have improvement.

## Backlog

- [ ] Idea or unresolved issue.
```

## AGENTS.md Workflow Block

````md
# Handoff / Handon Workflow

This project uses a structured handoff workflow.

## Files

- `docs/HANDOFF/CURRENT.md`: current project handoff state.
- `docs/HANDOFF/DECISIONS.md`: long-term project decisions.
- `docs/HANDOFF/TODO.md`: task list.

## /handoff

When the user says `/handoff`, update `docs/HANDOFF/CURRENT.md`.

Do not copy the full conversation.
Do not write a changelog.
Do not include secrets.
Only keep information that helps the next session continue the work.

After finishing, only say:

```text
Handoff completed.

Updated:
docs/HANDOFF/CURRENT.md
```

## /handon

When the user says `/handon`, read:

- `AGENTS.md`
- `docs/HANDOFF/CURRENT.md`
- `docs/HANDOFF/DECISIONS.md`
- `docs/HANDOFF/TODO.md`
- `README.md`

Do not modify code immediately.

First give a concise context recap, the most relevant next steps, and say that we can continue.
````
