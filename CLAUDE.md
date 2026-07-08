# Handoff

Use the Handoff workflows in `skills/handoff/SKILL.md`, `skills/handon/SKILL.md`, and `skills/handoff-handon/SKILL.md`.

When the user says `/handoff`, "handoff", "prepare a handoff", or indicates they are ending a work session:

1. Read `skills/handoff-handon/SKILL.md`.
2. Follow the Handoff workflow.
3. Always update `docs/HANDOFF/CURRENT.md`.
4. Update `docs/HANDOFF/TODO.md` only when the task list changed or new follow-up work was discovered.
5. Update `docs/HANDOFF/DECISIONS.md` only when a durable project decision was made or confirmed.

When the user says `/handon`, "handon", "continue from last time", or asks to restore context:

1. Read `skills/handoff-handon/SKILL.md`.
2. Follow the Handon workflow.
3. Summarize the restored context first.
4. Do not modify code until the user explicitly confirms.

Never write secrets, credentials, `.env` values, private keys, or production configuration into handoff files.
