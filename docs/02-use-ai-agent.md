# 第二章：学习 AI Agent

> 📖 **CHAPTER #2**: Use AI Agent

> 📌 **版本说明**：本章已按 **OpenCode V2**（实测版本 v2.2.5）更新。

---

## 📋 目录

- [什么是 Primary Agent 和 Subagent](#primary-subagent)
- [OpenCode 内置 Agent 速览](#agent-overview)
- [练习调用 Explore Agent](#explore-agent)
- [练习调用 General Agent](#general-agent)
- [Build Agent实战练习](#practice)
- [查看 Agent 列表](#agent-list)
- [撤销操作](#undo)
- [TODO 跟踪进度](#todo-tracking)
- [项目初始化](#project-init)
- [规则文件](#rules)
- [进阶技巧](#advanced-tips)
- [其他：环境变量配置](#env-config)

---

## 💡 什么是 Primary Agent 和 Subagent <a id="primary-subagent"></a>

**Plan** 和 **Build** 是 OpenCode 内置的两个 **Primary Agents**（主要助手）：

| 类型 | 说明 | 切换方式 |
|------|------|----------|
| **Primary Agent** | 你可以直接对话的主助手 | 用 `Shift + Tab` 切换 |
| **Subagent** | 由 Primary Agent 调用的专家助手 | 用 `@agent名` 调用 |

> 💡 **提示**：用 `Shift + Tab` 切换 Primary Agent，用 `@agent名` 调用 Subagent。如果你是从 V1 升级的用户，旧配置可能让 `Tab` 也能切换，详见第一章"关于 Tab 键"。

---

## 🚀 OpenCode 内置 Agent 速览 <a id="agent-overview"></a>

| Agent | 类型 | 擅长 | 默认权限 |
|-------|------|------|----------|
| `Build` | Primary | 全能开发（默认主 Agent） | 全能（可读写文件、执行命令；读取 `.env` 文件会先询问） |
| `Plan` | Primary | 分析代码、规划方案、审查建议 | 受限（默认禁止编辑项目文件，仅允许写入 OpenCode 的计划文件目录 `~/.opencode/plan/`） |
| `Explore` | Subagent | 快速找到文件、搜索代码、回答代码库问题 | 只读（不能编辑文件，可搜索、读网页；shell 命令由系统提示约束为只读） |
| `General` | Subagent | 复杂研究、多步骤任务、不确定能否快速找到答案时 | 广泛（可读写文件、执行命令，但不能再启动子代理） |

> 💡 **备注**：V2 里还有 `compaction`、`title`、`summary` 三个隐藏 Agent，负责压缩上下文、生成标题和摘要，你不能直接选择它们。

---

## 🔍 练习调用 Explore Agent <a id="explore-agent"></a>

> 📖 **为什么**：让专业的代码探索 Agent 帮你理解项目。

输入：

```bash
@explore 帮我梳理这个项目的整体结构
```

---

### Explore 的三种探索深度

> 💡 **提示**：调用 Explore 时，AI 会根据你的任务描述自动选择探索深度。你也可以在提示词中指定。

| 深度 | 说明 | 适合场景 |
|------|------|----------|
| `quick` | 基本搜索，快速定位 | "找一下 config 文件在哪" |
| `medium` | 中等探索，平衡速度和覆盖面 | "帮我梳理项目结构" |
| `very thorough` | 全面分析，跨多个位置和命名约定进行搜索 | "找出所有安全相关的代码" |

### 示例

```bash
@explore 彻底分析这个项目的认证和鉴权实现，要非常全面
```

> 💡 **提示**：AI 看到"彻底""非常全面"这类描述，会自动采用 `very thorough` 级别。

---

### 进入子会话

调用子代理后，会创建一个子会话。

你可以按 `↓` 打开子代理选择并进入子会话，用 `→` / `←` 在多个子会话之间切换，按 `↑` 返回父会话。

> 💡 **备注**：以上是 V2 的默认键位，不需要 Leader 键。V1 的默认键位是 `<leader>↓`、`<leader>→`、`<leader>←`、`<leader>↑`（默认 leader 是 `Ctrl+X`）。从 V1 升级的用户，旧键位可能被迁移进 `cli.json`，导致三个操作的按法不一致，还可能和 V2 的终端面板键位冲突。删掉 `cli.json` 里的 `session.child.*`、`session.parent` 条目即可恢复默认，详见第一章"迁移用户注意"。

---

## 📚 练习调用 General Agent <a id="general-agent"></a>

> 📖 **为什么**：General Agent 擅长复杂研究和多步骤任务。

输入：

```bash
@general 帮我研究 Node.js 和 Python 的性能对比，并输出总结报告
```

---

## 💪 Build Agent实战练习 <a id="practice"></a>

在 **Build Agent** 模式下输入：

```bash
帮我分析这个项目的代码结构，然后添加一个 README.md
```

---

## 📋 查看 Agent 列表 <a id="agent-list"></a>

> 📖 **了解当前有哪些 Agent 可用**。

按 `<leader>a` 列出所有 Agent（默认 leader 是 `Ctrl+X`，即先按 `Ctrl+X` 并松开，再单独按 `a`，分步按法详见第一章"Leader 键组合"），或者输入 `/agents`。

按 `Esc` 退出列表

---

## ↩️ 撤销操作 <a id="undo"></a>

如果不满意，可以撤销。

```bash
/undo
```

`/undo` 会撤回上一条消息以及 AI 随后的所有工作，被撤回的提示词会回到输入框，方便你修改后重新发送。

后悔了？在发送新提示词之前输入 `/redo`，可以恢复被撤回的对话和文件。

> ⚠️ **注意**：还原文件需要项目是 Git 仓库。不在 Git 仓库里，`/undo` 只能撤回对话，不能还原文件。另外，`/undo` 还原不了 shell 命令造成的影响（如提交、安装依赖、数据库变更）。重要的修改请先用 Git 提交。

---

## ✅ TODO 跟踪进度 <a id="todo-tracking"></a>

> ⚠️ **前提**：V2 里 TODO 功能**默认关闭**。使用前需要在 `opencode.json` 里开启实验功能：
>
> ```json
> {
>   "experimental": {
>     "todo": true
>   }
> }
> ```

> 📖 **开启后，复杂任务时可以明确告诉 AI 用 TODO 跟踪进度**：

| 你说的话 | AI 会做什么 |
|---------|-------------|
| "用 TODO 跟踪进度" | 创建任务列表，逐步更新状态 |
| "分步骤完成" | 自动拆分任务，边做边更新 |
| "当前进度怎么样？" | 汇报已完成 / 进行中 / 待处理 |

---

## 🚀 项目初始化 <a id="project-init"></a>

### 为什么需要初始化

没有初始化时，你每次对话都要告诉 AI：

- 这是什么项目
- 用什么技术栈
- 代码风格是什么
- 有什么特殊规范

> 💡 **提示**：初始化后，这些信息会保存在 `AGENTS.md` 文件里，AI 每次都会自动读取。

---

## 📄 规则文件 <a id="rules"></a>

> 📖 **OpenCode V2 只识别名为 `AGENTS.md` 的规则文件**：

| 位置 | 作用范围 |
|------|----------|
| `~/.config/opencode/AGENTS.md` | 全局（所有项目） |
| 项目根目录 `/AGENTS.md` | 当前项目 |
| 子目录 `/packages/web/AGENTS.md` 等 | 该子目录（AI 读取该区域时才加载） |

> ⚠️ **注意**：V2 **不再兼容 `CLAUDE.md`**（包括 `~/.claude/CLAUDE.md`）。如果你的项目原来靠 `CLAUDE.md` 提供规则，请把内容迁移到 `AGENTS.md` 里。

---

### 查找机制

> 💡 **提示**：OpenCode 会加载全局文件，再加载从当前工作目录一路向上直到 home 目录的每一个 `AGENTS.md`（工作目录在 home 之外时，到项目根目录为止）。它们会**全部合并**，而不是只用第一个，冲突时 OpenCode 不会替你裁决。

例如在 `~/code/my-project/packages/web` 下启动，下面三个文件会全部生效：

```text
~/.config/opencode/AGENTS.md
~/code/my-project/packages/web/AGENTS.md
~/code/my-project/AGENTS.md
```

> 💡 **小技巧**：规则文件改动后无需重启，OpenCode 会在下一次请求前自动检测变化并通知 AI。

---

### 规则文件的加载和合并

> 📖 **加载顺序**：

1. **全局规则**：加载 `~/.config/opencode/AGENTS.md`
2. **项目规则**：从当前工作目录向上，加载每一层的 `AGENTS.md`
3. **配置规则**：加载 `opencode.json` 中 `instructions` 指定的所有文件（在 `AGENTS.md` 之后，按列出的顺序）

> ⚠️ **注意**：URL 超时 — instructions 支持从远程 URL 加载规则文件，但会使用 **5 秒超时限制**。

---

## 👨‍🏫 跟我做

### 第 1 步：进入项目目录

> 📖 **为什么**：在项目根目录下初始化，生成的规则才是针对这个项目的。

```bash
cd ~/your-project
opencode
```

---

### 第 2 步：执行初始化

> 📖 **为什么**：让 AI 分析项目并生成规则文件。

输入：

```bash
/init
```

> ✅ **预期效果**：AI 开始分析项目结构、技术栈、代码风格

也可以带参数执行：

```bash
/init 这是一个XXX项目，需要特别关注XXXX问题
```

> ✅ **实测**：`/init` 后面可以附带大段文字说明。

---

### /init 命令会：

- 引导式地创建或更新项目的 `AGENTS.md`
- 分析项目文件、目录结构和技术栈
- 检测构建、测试、lint 命令和代码风格
- 把结果写进 `AGENTS.md`，并确保内容精炼实用

---

### 第 3 步：审核生成的规则

> 📖 **为什么**：AI 生成的规则可能不完全准确，需要人工审核。

检查这些内容是否正确。

> 💡 **参考**：完整的 AGENTS.md 示例可以参考官方文档：https://opencode.ai/v2/docs/instructions

---

## 🛠️ 进阶技巧 <a id="advanced-tips"></a>

### 1. 进阶：使用 opencode.json 加载更多规则

除了 `AGENTS.md`，你还可以在配置中指定额外的规则文件：

```json
{
  "$schema": "https://opencode.ai/config.json",
  "instructions": [
    "CONTRIBUTING.md",
    "docs/guidelines.md",
    "packages/*/AGENTS.md"
  ]
}
```

`instructions` 支持的特性：

| 特性 | 说明 |
|------|------|
| 相对路径 | 从工作目录向上逐级查找到项目根，支持 glob 模式 |
| Glob 模式 | 如 `packages/*/AGENTS.md` 匹配多个文件 |
| 绝对路径 | 直接指定完整路径 |
| URL | 支持 `https://` 或 `http://` 加载远程规则（5 秒超时） |
| Home 目录 | 以 `~/` 开头自动展开 |

**示例**：

```json
{
  "instructions": [
    "~/team-rules/typescript.md",
    "https://example.com/company-coding-standards.md",
    "docs/**/*.md"
  ]
}
```

> 💡 **提示**：所有通过 `instructions` 指定的文件会与 `AGENTS.md` 合并。

---

### 2. 进阶：在 AGENTS.md 中引用外部文件

`AGENTS.md` 里的 `@文件名` 不会被自动展开，但你可以显式指示 AI 读取外部文件，以下是示范：

```markdown
# 项目规则

## 外部文件引用
当遇到文件引用（如 `@docs/xxx.md`）时，使用 read 工具按需加载：
- 不要预先加载所有引用，按实际需要懒加载
- 加载后的内容作为必须遵守的指令
- 必要时递归加载引用

## 技术规范
TypeScript 风格：@docs/typescript-guidelines.md
React 组件模式：@docs/react-patterns.md
REST API 设计：@docs/api-standards.md
测试策略：@test/testing-guidelines.md
```

---

## ⚙️ 其他：环境变量配置 <a id="env-config"></a>

> 💡 **新手首选**：直接在 TUI 里输入 `/connect`，选择提供商并粘贴 API Key 即可，密钥会保存在本地数据库里，**不需要配置环境变量**。下面的两种方式适合想把 Key 放进环境变量、或者要在配置文件里引用 Key 的用户。

> 📌 **V2 的变化**：V2 默认由一个**后台共享服务**统一发出模型请求，所以环境变量要设置在这个**服务进程**上，只在当前终端里设置不一定对它生效。

### 方式一：写入后台服务（官方文档推荐）

```powershell
opencode service set env SILICONFLOW_API_KEY sk-your-api-key
```

执行后会停止正在运行的后台服务，下次运行任何 `opencode` 命令时，服务会带着新的变量重新启动。验证：

```powershell
opencode auth list
```

支持的变量会以 `environment` 类型出现在列表中。想取消，执行：

```powershell
opencode service unset env SILICONFLOW_API_KEY
```

> ⚠️ **注意**：这个值保存在你本机的服务配置里，请不要把它提交到 Git。

---

### 方式二：通过系统设置（永久生效）

#### 1. 打开环境变量设置

- 按 `Win + R`，输入 `sysdm.cpl`，回车
- 点击 **高级** 标签 → **环境变量**

#### 2. 添加新变量

在"用户变量"或"系统变量"区域点击 **新建**：

| 变量名 |
|--------|
| `SILICONFLOW_API_KEY` |
| `OPENAI_API_KEY` |

#### 3. 验证

重启终端后运行：

```powershell
echo $env:SILICONFLOW_API_KEY
```

> ⚠️ **注意**：官方文档只明确了方式一。用方式二时，如果 OpenCode 没读到变量，先执行 `opencode service restart` 重启后台服务；仍不行就改用方式一。

---

> 💡 **提示**：建议把 `opencode.json` 中的硬编码 API Key 替换成环境变量引用。V2 里 API Key 写在 `providers.<提供商ID>.settings.apiKey`：
> ```json
> {
>   "providers": {
>     "siliconflow-cn": {
>       "settings": {
>         "apiKey": "{env:SILICONFLOW_API_KEY}"
>       }
>     }
>   }
> }
> ```

> 💡 **接入目录里没有的服务**：如果要使用目录里没有的 OpenAI 兼容服务，可以参考 `opencode_config/example_opencode.json`：在 `providers` 里定义提供商 ID、`package`、`settings.baseURL` 和模型，`env` 指定存放 Key 的环境变量名（Key 本身不写进配置文件）。SiliconFlow 这类内置提供商不需要这样配置，直接 `/connect` 即可。

---
