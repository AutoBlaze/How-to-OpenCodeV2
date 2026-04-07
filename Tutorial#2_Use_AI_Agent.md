# 第二章：学习 AI Agent

> 📖 **CHAPTER #2**: Use AI Agent

---

## 📋 目录

- [什么是 Primary Agent 和 Subagent](#什么是-primary-agent-和-subagent)
- [OpenCode 内置 Agent 速览](#opencode-内置-agent-速览)
- [练习调用 Explore Agent](#练习调用-explore-agent)
- [练习调用 General Agent](#练习调用-general-agent)
- [实战练习](#实战练习)
- [查看 Agent 列表](#查看-agent-列表)
- [撤销操作](#撤销操作)
- [TODO 跟踪进度](#todo-跟踪进度)
- [项目初始化](#项目初始化)
- [规则文件](#规则文件)
- [进阶技巧](#进阶技巧)
- [环境变量配置](#环境变量配置)

---

## 💡 什么是 Primary Agent 和 Subagent

**Plan** 和 **Build** 是 OpenCode 内置的两个 **Primary Agents**（主要助手）：

| 类型 | 说明 | 切换方式 |
|------|------|----------|
| **Primary Agent** | 你可以直接对话的主助手 | 用 `Tab` 切换 |
| **Subagent** | 由 Primary Agent 调用的专家助手 | 用 `@agent名` 调用 |

> 💡 **提示**：用 `Tab` 切换 Primary Agent，用 `@agent名` 调用 Subagent

---

## 🚀 OpenCode 内置 Agent 速览

| Agent | 类型 | 擅长 | 默认权限 |
|-------|------|------|----------|
| `Build` | Primary | 全能开发（默认主 Agent） | 全能（可读写文件、执行命令） |
| `Plan` | Primary | 分析代码、规划方案、审查建议 | 受限（默认禁止编辑，仅 `.opencode/plans/*.md` 允许写入） |
| `Explore` | Subagent | 快速找到文件、搜索代码、回答代码库问题 | 只读（可搜索、浏览代码） |
| `General` | Subagent | 复杂研究、多步骤任务、不确定能否快速找到答案时 | 多任务执行（可用 Todo 工具） |

---

## 🔍 练习调用 Explore Agent

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

你可以用 `<leader>→` 进入子会话，用 `<leader>←` 返回父会话。

> 💡 **备注**：默认 leader 是 `Ctrl+X`

---

## 📚 练习调用 General Agent

> 📖 **为什么**：General Agent 擅长复杂研究和多步骤任务。

输入：

```bash
@general 帮我研究 Node.js 和 Python 的性能对比，并输出总结报告
```

---

## 💪 实战练习

在 **Build Agent** 模式下输入：

```bash
帮我分析这个项目的代码结构，然后添加一个 README.md
```

---

## 📋 查看 Agent 列表

> 📖 **了解当前有哪些 Agent 可用**。

按 `<leader>a` 列出所有 Agent（默认 leader 是 `Ctrl+X`，即 `Ctrl+X` + `a`）

按 `Esc` 退出列表

---

## ↩️ 撤销操作

如果不满意，可以撤销。

```bash
/undo
```

---

## ✅ TODO 跟踪进度

> 📖 **复杂任务时，可以明确告诉 AI 用 TODO 跟踪进度**：

| 你说的话 | AI 会做什么 |
|---------|-------------|
| "用 TODO 跟踪进度" | 创建任务列表，逐步更新状态 |
| "分步骤完成" | 自动拆分任务，边做边更新 |
| "当前进度怎么样？" | 汇报已完成 / 进行中 / 待处理 |

---

## 🚀 项目初始化

### 为什么需要初始化

没有初始化时，你每次对话都要告诉 AI：

- 这是什么项目
- 用什么技术栈
- 代码风格是什么
- 有什么特殊规范

> 💡 **提示**：初始化后，这些信息会保存在 `AGENTS.md` 文件里，AI 每次都会自动读取。

---

## 📄 规则文件

> 📖 **OpenCode 会按以下顺序查找规则文件**：

| 位置 | 作用范围 |
|------|----------|
| 项目根目录 `/AGENTS.md` | 当前项目 |
| 项目根目录 `/CLAUDE.md` | 兼容 Claude Code |
| `~/.config/opencode/AGENTS.md` | 全局（所有项目） |
| `~/.claude/CLAUDE.md` | 全局（兼容 Claude Code） |
| `$OPENCODE_CONFIG_DIR/AGENTS.md` | 全局（通过环境变量指定） |

---

### 查找机制

> 💡 **提示**：OpenCode 会从当前目录开始向上遍历，直到工作目录（worktree）的根目录，找到的第一个规则文件会被使用。全局规则会与项目规则合并。

---

### 规则文件的加载和合并

> 📖 **加载顺序**：

1. **项目规则**：从当前目录向上遍历到工作目录根，查找 `AGENTS.md` 或 `CLAUDE.md`
2. **全局规则**：加载 `~/.config/opencode/AGENTS.md` 或 `~/.claude/CLAUDE.md`
3. **自定义配置目录**：如果设置了 `OPENCODE_CONFIG_DIR` 环境变量，加载其中的 `AGENTS.md`
4. **配置规则**：加载 `opencode.json` 中 `instructions` 指定的所有文件

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
/init 特别关注 TypeScript 类型安全和错误处理
```

---

### /init 命令会：

- 扫描项目文件和目录结构
- 检测构建、测试、lint 命令
- 分析代码风格和命名规范
- 如果发现 Cursor 规则（`.cursor/rules/`、`.cursorrules`）或 Copilot 规则（`.github/copilot-instructions.md`），会自动整合
- 如果 `AGENTS.md` 已存在，会**改进而非覆盖**
- 生成约 150 行的规则文件，确保内容精炼实用

---

### 第 3 步：审核生成的规则

> 📖 **为什么**：AI 生成的规则可能不完全准确，需要人工审核。

检查这些内容是否正确。

> 💡 **参考**：完整的 AGENTS.md 示例可以参考官方文档：https://github.com/anomalyco/opencode/blob/dev/packages/web/src/content/docs/rules.mdx

---

## 🛠️ 进阶技巧

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
| 相对路径 | 从项目目录向工作目录根查找，支持 glob 模式 |
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

虽然 OpenCode 不会自动解析文件引用，但你可以在 `AGENTS.md` 中显式指示 AI 读取外部文件，以下是示范：

```markdown
【# 项目规则

## 外部文件引用
当遇到文件引用（如 `@docs/xxx.md`）时，使用 Read 工具按需加载：
- 不要预先加载所有引用，按实际需要懒加载
- 加载后的内容作为必须遵守的指令
- 必要时递归加载引用

## 技术规范
TypeScript 风格：@docs/typescript-guidelines.md
React 组件模式：@docs/react-patterns.md
REST API 设计：@docs/api-standards.md
测试策略：@test/testing-guidelines.md】
```

---

## ⚙️ 环境变量配置

### 通过系统设置（永久生效）

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

```bash
echo $env:SILICONFLOW_API_KEY
```

---

> 💡 **提示**：建议把 `opencode.json` 中的硬编码 API Key 替换为：
> ```json
> "apiKey": "{env:SILICONFLOW_API_KEY}"
> ```

---
