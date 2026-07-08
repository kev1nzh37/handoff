# Promotion Kit

Use these drafts to announce Handoff. Adjust tone for the platform before posting.

## One-Liner

Handoff is a tiny repo-local workflow for coding agents: run `/handoff` before leaving work, commit `docs/HANDOFF/`, then run `/handon` at home to continue with the right context.

## Short Pitch

Agentic coding breaks down when context lives only in a chat window. Handoff turns the current project state into small repo-local markdown files, so a fresh session on another machine can continue without replaying the whole conversation.

It does not sync chat history, auto-commit, or depend on a cloud service. It just writes the next useful state into `docs/HANDOFF/`.

## X / Twitter

```text
I built Handoff, a tiny workflow for coding agents:

/handoff at work -> writes docs/HANDOFF/
git push
git pull at home
/handon -> continue with context restored

No chat transcript sync. No extra cloud service. Just repo-local markdown files.

https://github.com/kev1nzh37/handoff
```

## Hacker News

Title:

```text
Show HN: Handoff - repo-local handoff files for coding agents
```

Post:

```text
I built Handoff to solve a small but recurring problem in agentic coding: work context gets trapped in a chat session.

The workflow is intentionally simple:

- run /handoff before stopping work
- it writes docs/HANDOFF/CURRENT.md, TODO.md, and DECISIONS.md
- commit and push those files
- on another machine or in a fresh session, pull and run /handon

It does not sync chat history, auto-commit, auto-push, or use a cloud service. The handoff is just markdown in the repo, so Codex, Claude Code, Cursor, Kimi, OpenCode, Gemini-style agents, or any similar coding agent can read it.

Repo: https://github.com/kev1nzh37/handoff
```

## Reddit

Suggested communities:

- r/ChatGPTCoding
- r/OpenAI
- r/ClaudeAI
- r/cursor
- r/LocalLLaMA, if framed as an agent workflow rather than a Codex-only tool

Title:

```text
I made a repo-local /handoff and /handon workflow for coding agents
```

Post:

```text
I kept running into the same problem: I would work with a coding agent on one machine, then later lose the useful project context when switching machines or starting a fresh session.

So I made Handoff:

- /handoff writes a compact project state to docs/HANDOFF/
- you commit/push or otherwise sync those files
- /handon reads them later and gives a short recap before continuing

The goal is not to save the entire chat transcript. It only keeps the objective, completed work, remaining tasks, risks, key files, and validation plan.

It is designed to be repo-local and agent-agnostic, with entry points for Codex, Claude Code, Cursor-compatible layouts, Kimi, OpenCode, Gemini-style agents, and Pi notes.

GitHub: https://github.com/kev1nzh37/handoff

Feedback welcome, especially on install flows for different agent apps.
```

## Chinese Communities

Suggested communities:

- V2EX
- 即刻
- 知乎
- 掘金
- 少数派 Matrix

Title:

```text
做了一个给 AI 编程用的 /handoff 和 /handon 工作流
```

Post:

```text
我做了一个小工具/工作流，叫 Handoff，解决 AI 编程时上下文断掉的问题。

典型场景：

- 公司电脑上和 Codex/Claude/Cursor 写了一半
- 下班前运行 /handoff
- 它把当前目标、完成了什么、还差什么、风险、关键文件、下一步写进 docs/HANDOFF/
- commit + push
- 回家 git pull
- 运行 /handon
- 新 session 直接知道该从哪里继续

它不保存完整聊天记录，也不会自动 commit/push，更不依赖额外云服务。核心就是 repo-local markdown 文件。

GitHub: https://github.com/kev1nzh37/handoff

目前做了 Codex、Claude Code、Cursor-compatible、Kimi、OpenCode、Gemini-style agents 的入口。欢迎试用和提意见。
```

## GitHub Description

```text
Repo-local handoff workflow for coding agents
```

## GitHub Topics

```text
agent-workflow
claude-code
codex
context
cursor
handoff
kimi
opencode
```

## Product Positioning

Use these points consistently:

- Handoff is a workflow, not a cloud sync service.
- The durable state is stored in repo-local markdown files.
- Cross-machine use requires Git push/pull or another file sync mechanism.
- `/handon` summarizes first and does not modify code until the user confirms.
- The goal is to restore useful working context, not to preserve full chat history.
