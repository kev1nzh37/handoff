# Handoff

[English](README.md) | [简体中文](README.zh-CN.md)

Handoff 是一个面向 coding agent 的交接工作流插件，用来在多台电脑、多个 agent session、上下文重置之间恢复开发状态。

它给 coding agent 提供一组很小的工作流：

- `/handoff`: 把当前仓库状态压缩成 `docs/HANDOFF/CURRENT.md`。
- `/handon`: 从 handoff 文件恢复上下文，在修改代码前先总结当前状态。

Handoff 不保存完整聊天记录。它只保存下一次继续工作真正需要的状态：当前目标、已经完成的工作、未完成的工作、风险、关键文件、下一步和验证计划。

## 为什么需要它

使用 agent 写代码时，最容易断的不是代码本身，而是上下文：从公司电脑切到家里电脑、长对话丢失、session 重开、模型窗口被压缩，都会让下一次继续工作变慢。

真正有用的信息通常不是完整聊天记录，而是一份放在 repo 里的、结构化的项目交接文档。

Handoff 就是把这件事标准化。

## 当前状态

版本：`1.0.1`

这是第一个公开版本。工作流契约已经稳定，实现范围刻意保持很小：

- 不同步完整聊天记录。
- 不自动 commit 或 push。
- 不自动切换分支。
- 不管理远程主机。
- 不依赖外部服务。

## 支持的 Agent

这个工作流刻意设计成 repo-local 和 agent-agnostic。只要某个 coding agent 能读取项目文件并遵守 markdown 指令，就可以使用这些 handoff 文件。

当前仓库提供的入口：

- Codex: `.codex-plugin/plugin.json`
- Claude Code: `.claude-plugin/plugin.json` 和 `CLAUDE.md`
- Cursor-compatible plugin layout: `.cursor-plugin/plugin.json`
- Gemini-style instruction pointer: `GEMINI.md`
- Kimi Code: `.kimi-plugin/plugin.json`
- OpenCode: `.opencode/INSTALL.md`
- Pi-compatible package notes: `docs/README.pi.md`

不同 app 的安装方式会不同。和 Superpowers 类似，每个 harness 可能都需要单独安装或配置。

## 安装

使用你的 Codex 环境支持的插件安装流程，把这个仓库作为本地 Codex 插件安装。

本地开发时可以先克隆仓库：

```bash
git clone https://github.com/kev1nzh37/handoff.git
```

然后让 Codex 指向这个插件目录，或者通过你配置好的本地插件 marketplace 安装。

不同平台的入口：

- Codex: 把这个仓库作为本地 Codex 插件安装。
- Claude Code: 把这个仓库作为 Claude plugin 安装，然后使用 `/handoff` 或 `/handon`。
- Cursor: 使用 `.cursor-plugin/` 下的 Cursor-compatible metadata。
- Gemini: 让 agent 读取 `GEMINI.md`。
- Kimi Code: 通过 Kimi 的 plugin manager 从这个仓库安装。
- OpenCode: 按 `.opencode/INSTALL.md` 操作。
- Pi: 查看 `docs/README.pi.md`。

## 使用方式

在你正在开发的仓库里输入：

```text
/handoff
```

Codex 应该会把 `handoff` 显示为可用的 skill slash entry。选择或发送 `/handoff` 会运行专门的 handoff skill，检查仓库状态并更新：

```text
docs/HANDOFF/CURRENT.md
```

`CURRENT.md` 永远是主要输出。`docs/HANDOFF/TODO.md` 和 `docs/HANDOFF/DECISIONS.md` 只在有明确理由时更新：

- 当任务列表变化，或发现新的后续工作时，更新 `TODO.md`；
- 当产生或确认了长期项目决策时，更新 `DECISIONS.md`。

当你在新的 session 回来继续工作时输入：

```text
/handon
```

Codex 应该会把 `handon` 显示为可用的 skill slash entry。选择或发送 `/handon` 会读取 handoff 文件，总结当前状态，并在你确认前不修改代码。

## 项目交接文件

Handoff 期望项目使用下面的结构：

```text
AGENTS.md
docs/
  HANDOFF/
    CURRENT.md
    DECISIONS.md
    TODO.md
```

文件含义：

- `AGENTS.md`: 项目规则、约定、命令和限制。
- `docs/HANDOFF/CURRENT.md`: 当前交接状态，频繁更新。
- `docs/HANDOFF/DECISIONS.md`: 长期决策，低频更新。
- `docs/HANDOFF/TODO.md`: 任务池。

## 安全边界

Handoff 会要求 Codex 不要把密钥或敏感运行信息写入 handoff 文件，包括：

- API keys
- tokens
- cookies
- passwords
- private keys
- `.env` 实际值
- 数据库凭据
- 生产环境配置

如果发现疑似敏感信息，handoff 只应该记录抽象提醒，而不是记录真实值。

## 示例

- [`examples/current.md`](examples/current.md): `docs/HANDOFF/CURRENT.md` 示例
- [`examples/handon-summary.md`](examples/handon-summary.md): `/handon` 输出示例

## 插件结构

```text
.codex-plugin/plugin.json
.claude-plugin/plugin.json
.cursor-plugin/plugin.json
.kimi-plugin/plugin.json
.opencode/INSTALL.md
CLAUDE.md
GEMINI.md
docs/
  README.kimi.md
  README.opencode.md
  README.pi.md
skills/
  handoff/
    SKILL.md
    agents/openai.yaml
  handon/
    SKILL.md
    agents/openai.yaml
  handoff-handon/
    SKILL.md
    agents/openai.yaml
    references/templates.md
```

## 开发

如果你在用 Codex 的 plugin creator / skill creator 工具开发这个插件，请使用你本机工具目录里的 validator。

验证插件 manifest：

```bash
python /path/to/plugin-creator/scripts/validate_plugin.py .
```

验证 skill：

```bash
python /path/to/skill-creator/scripts/quick_validate.py skills/handoff-handon
```

## License

MIT
