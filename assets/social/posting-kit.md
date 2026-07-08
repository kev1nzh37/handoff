# WanliTech / Handoff Posting Kit

## Profile

Display name:

```text
Froggo@WanliTech
```

Chinese name:

```text
蛙里酱
```

Bio:

```text
Vibe Coding / Product / Workflows
Work hard uphill, enjoy the ride downhill.
```

Chinese bio:

```text
Vibe Coding / Product / Workflows
上坡要努力，下坡要开心。
```

Avatar:

```text
assets/social/wanlitech-walijiang-avatar.png
```

## X

```text
I made a new Skill for Vibe Coding across machines:

/handoff before leaving work
push docs/HANDOFF/
pull at home
/handon

Now the new Codex/Claude Code session knows what was done, what is left, and where to continue.

No full chat sync. No extra cloud service. Just repo-local markdown.

https://github.com/kev1nzh37/handoff
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
I made /handoff and /handon for Vibe Coding across machines
```

Post:

```text
I kept running into this dumb but real problem:

I would let Codex / Claude Code / Cursor work on something at my desk, leave with the task half-done, then open a new session later and the agent had no idea what happened.

So I made Handoff.

- /handoff writes a compact project state to docs/HANDOFF/
- you commit/push or otherwise sync those files to the next machine
- /handon reads them later and gives a short recap before continuing work

The point is not to save the whole conversation. Most of that is noise. I only want the next session to know:

- what we were trying to do
- what already changed
- what is still unfinished
- which files matter
- what to verify next

It is repo-local and agent-agnostic. I added entry points for Codex, Claude Code, Cursor-compatible layouts, Kimi, OpenCode, Gemini-style agents, and Pi notes.

GitHub: https://github.com/kev1nzh37/handoff

Feedback welcome, especially if you use a different coding agent app and the install flow needs work.
```

## V2EX

Suggested node:

```text
推广
```

Title:

```text
全新 Skill！Codex/Claude Code 多设备共享会话（Sessions）神器！
```

Post:

```text
我做了一个全新的 Skill，叫 Handoff，解决 Vibe Coding 时最烦的一个问题：

下班回到家，本来想接着让 AI 给你干活，结果上下文还在公司电脑里。

新 session 一开，AI 完全不知道上次做到哪，也不知道哪些文件改过、还有什么没做。

典型场景：

- 公司电脑上让 Codex/Claude Code/Cursor 干到一半
- 下班前运行 /handoff
- 它把当前目标、完成了什么、还差什么、风险、关键文件、下一步写进 docs/HANDOFF/
- commit + push
- 回家 git pull
- 运行 /handon
- 新 session 直接知道该从哪里继续干活

它不保存完整聊天记录，也不会自动 commit/push，更不依赖额外云服务。核心就是 repo-local markdown 文件。

GitHub: https://github.com/kev1nzh37/handoff

目前做了 Codex、Claude Code、Cursor-compatible、Kimi、OpenCode、Gemini-style agents 的入口。欢迎试用和提意见。
```
