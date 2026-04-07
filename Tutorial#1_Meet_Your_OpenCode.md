# 第一章：打开 OpenCode

> 📖 **CHAPTER #1**: Meet Your OpenCode

---

## 📋 目录

- [什么是 OpenCode](#什么是opencode)
- [安装 OpenCode](#安装opencode)
- [使用 OpenCode 的方式](#使用opencode的方式)
- [启动 OpenCode 并进入项目](#启动-opencode-并进入项目)
- [新手模型选择](#新手模型选择)
- [CLI 常用指令](#cli-常用指令)
- [TUI 常用指令](#tui-常用指令)
- [OpenCode 核心工具](#opencode核心工具)
- [高级功能](#高级功能)

---

## 💡 什么是 OpenCode

OpenCode 是一个免费开源项目，是一个在终端里运行的 **AI 编程助手**，与几乎所有主流大模型都可以搭配使用。

你可以用它进行 **Vibe Coding**，你说一句话，它帮你：

- 📝 分析需求
- ✏️ 修改代码
- ⚡ 执行命令
- 🔄 自动完成多步任务

> 🎯 **目标**：不懂编程的普通人也可以用 OpenCode 写代码，做 App、协助办公，以及更多无限可能。

它被称为 **Claude Code** 的高性价比平替。对于国内用户，在 Anthropic **反花 + 封号 + 需要海外信用卡** 等缺点的情况下，OpenCode 确实是一个不错的选择。

---

## 🚀 安装 OpenCode

> ⚠️ **前置要求**：安装前需确保已安装 Node.js、Python、Git 等前置软件。

网络上安装教程非常多，本文不再重复造车轮。

### Windows 常见安装方式

进入 **管理员权限的 PowerShell**，输入：

```powershell
npm install -g opencode-ai
```

---

## 📌 使用 OpenCode 的方式

### 1. 终端直接使用

> 💡 **推荐**：最常用、稳定

在 cmd 终端 / PowerShell 里直接使用，稳定，但是对于编程新手需要适应终端界面和指令操作（但其实也没那么难）。

### 2. VS Code / Cursor IDE

先安装 OpenCode，再在 VS Code 里安装 OpenCode 插件。

> ✅ **优点**：
> - 适配程序员编程习惯
> - 实时看到文件资源器
> - 可视化 GitHub 管理

### 3. Warp 第三方终端

界面简单，有指令记忆功能，可以看到文件资源器。

> ⚠️ **缺点**：经常卡死，**不推荐**。

---

## ⚡ 启动 OpenCode 并进入项目

在 PowerShell 里输入：

```bash
cd ~/your-project  # 换成你的项目绝对路径
opencode
```

---

## ✅ 新手模型选择

> 💡 **建议**：新手优先使用 OpenCode 自带的免费 Model，不需要配置 API KEY，不折腾，打开即用

> ⚠️ **缺点**：短时间内不能连续使用太多次，有 rate limit（速率限制）

---

## 🔧 CLI 常用指令

> 📖 **说明**：CLI 指令用于没有进入 OpenCode 之前，在终端界面里使用

以 `opencode` 开头，加上下面后缀：

| 标志 | 简写 | 描述 |
|------|------|------|
| `--continue` | `-c` | 继续上一个会话 |
| `--session` | `-s` | 后面加要继续的会话 ID |
| `--fork` | - | 继续时分叉会话（与 `--continue` 或 `--session` 配合使用） |

### 常用命令

```bash
# 列出所有可用的代理
opencode agent list

# 为提供商配置 API 密钥
opencode auth login

# 密钥存储在 ~/.local/share/opencode/auth.json 中

# 列出所有已认证提供商
opencode auth list

# 清除提供商信息（登出）
opencode auth logout

# 列出提供商的所有可用模型
opencode models [provider]

# 刷新模型缓存
opencode models --refresh

# 列出所有 OpenCode 会话（按 q 退出）
opencode session list

# 列出最近 N 个会话
opencode session list -n [number]

# 更新到最新版本
opencode upgrade

# 更新到指定版本
opencode upgrade v0.1.48

# 查看版本号
opencode -v
```

> 💡 **常看常新**：https://opencode.ai/docs/zh-cn/cli/

---

## 🖥️ TUI 常用指令

> 📖 **说明**：TUI 指令用于从终端或者 IDE 进入 OpenCode 之后使用

### 用 `/` 调用斜杠命令

| 命令 | 作用 |
|------|------|
| `/help` | 查看帮助 |
| `/new` | 新建会话 |
| `/models` | 选择模型 |
| `/connect` | 添加 Model Provider |
| `/init` | 创建或更新 AGENTS.md 文件 |
| `/sessions` | 选择对话 |
| `/compact` | 压缩过长的上下文 |
| `/undo` | 撤回上一步操作（需要 Git 配合） |
| `/theme` | 切换主题 |
| `/exit` | 退出（也可用 `/q`） |

> 💡 **常看常新**：https://opencode.ai/docs/zh-cn/tui/

---

### 常用快捷键

| 快捷键 | 作用 |
|--------|------|
| `Tab` | 切换 Plan / Build 模式 |
| `Ctrl + C` | 中断当前操作 |
| `Ctrl + L` | 清屏 |
| `Ctrl + X` | Leader 键（前缀键） |
| `:q` | 退出 OpenCode，返回终端 |
| `Esc` | 取消 / 返回 |

### Leader 键组合

| 快捷键 | 作用 |
|--------|------|
| `Ctrl + X` → `n` | 新建会话 |
| `Ctrl + X` → `l` | 会话列表 |
| `Ctrl + X` → `m` | 模型列表 |

---

### 更多快捷键

| 功能 | 快捷键 | 说明 |
|------|--------|------|
| model_list | `<leader>m` | 模型列表 |
| model_cycle_recent | `F2` | 切换最近模型 |
| model_cycle_recent_reverse | `Shift + F2` | 反向切换 |
| model_cycle_favorite | `none` | 切换收藏模型 |
| agent_list | `<leader>a` | Agent 列表 |
| agent_cycle | `Tab` | 切换 Agent |
| agent_cycle_reverse | `Shift + Tab` | 反向切换 Agent |
| session_new | `<leader>n` | 新建会话 |
| session_list | `<leader>l` | 会话列表 |
| session_rename | `<leader>w` | 重命名会话 |
| sidebar_toggle | `<leader>b` | 切换侧边栏 |
| status_view | `<leader>s` | 状态视图 |
| tips_toggle | `<leader>h` | 切换首页提示 |
| messages_first | `Home` | 跳到第一条 |
| messages_last | `End` | 跳到最后一条 |

> 💡 **备注**：有些快捷键是自定义的，详见 `tui.json`

---

### 用 `@` 引用文件

> 💡 **这是 OpenCode 最强大的功能** —— 让 AI 直接读取你的文件

> ⚠️ **注意**：输入 `@` 后会看到 Agent 列表（如 `@explore`）和文件夹。继续输入文件名的部分内容（如 `@pack`），才会搜索并显示匹配的具体文件，用方向键选择后按 `Enter` 确认。

---

### 用 `!` 开头执行命令

这是一个非常方便的操作，可以直接在 OpenCode 里执行终端命令，减少不确定性，加快执行速度。

> 💡 **提示**：当然，不缺 Token 的话，可以尽量用自然语言让 AI 去执行终端命令。

---

### 待解决问题

> ❓ **待解决**：快捷键冲突
>
> `command_list` 的默认快捷键是 `ctrl+p`，但在 VS Code 里使用时，打开的是 VS Code 的命令搜索界面，和 OpenCode 无关。改了键位之后依然无效。

> ✅ **已解决**
>
> 在 VS Code 有按键冲突。在原生 PowerShell 或 CMD 终端里是可以使用的。

---

## 🛠️ OpenCode 核心工具

| 工具 | 作用 | 类比 |
|------|------|------|
| `read` | 读取文件或目录 | 打开文件看内容 |
| `write` | 创建或覆盖文件 | 另存为 |
| `edit` | 精确替换文件中的文本 | 查找替换 |
| `bash` | 执行 Shell 命令 | 在终端敲命令 |
| `grep` | 按内容搜索文件 | 全局搜索 |
| `glob` | 按文件名搜索文件 | 文件管理器里搜文件名 |
| `Task` | 创建子 Agent 处理复杂任务 | 创建帮手团队执行任务 |
| `WebFetch` | 获取网页内容 | 联网搜索 |
| `TodoWrite` | 任务清单管理（AI 自动使用） | 复杂任务时创建任务清单，防止 AI "忘事"或"走偏" |
| `Skill` | 加载专业知识包 | Skill 系列 |

### 额外说明

> ⚠️ **限制**：grep 和 glob 都最多返回 100 条结果。如果结果被截断，可以：
> - 缩小搜索目录（"只在 src 目录下搜索"）
> - 用更精确的关键词
> - 过滤文件类型（"只搜索 .ts 文件"）

> 💡 **提示**：你不需要手动调用这些工具。你只管用自然语言描述需求，AI 会自动选择合适的工具。

---

### 聪明的 Edit 工具

> 💡 **为什么 edit 是 OpenCode 最聪明的工具**：它不是简单地"改第几行"，而是用字符串匹配来精确定位要修改的位置。

Edit 工具有 **9 层匹配策略**，从严格到宽松逐层尝试：

| 策略 | 说明 | 例子 |
|------|------|------|
| 精确匹配 | 完全一致 | `foo` 匹配 `foo` |
| 行首尾空白忽略 | 忽略每行开头结尾的空格 | `foo` 匹配 `foo` |
| 首尾行锚点 | 用第一行和最后一行定位代码块 | 函数开头和结尾匹配 |
| 空白规范化 | 多个空格当一个 | `a b` 匹配 `a  b` |
| 缩进容错 | 忽略整体缩进差异 | 2 空格缩进匹配 4 空格 |
| 转义字符处理 | 处理 `\n`、`\t` 等 | `a\nb` 匹配实际换行 |
| 边界修剪 | 去掉首尾空白后匹配 | 前后有空行也能匹配 |
| 上下文感知 | 用首尾行 + 中间内容相似度 | 代码块略有变化也能匹配 |
| 多处匹配 | 找到所有精确匹配 | 配合 `replaceAll` 使用 |

> 💡 **简单说**：你给 AI 的代码片段不需要和文件里的完全一致，有点缩进差异、空格差异都没关系。

---

### 多处匹配问题

如果 `oldString` 在文件中出现了多次，edit 会报错：

> ⚠️ **错误提示**：
> ```
> Found multiple matches for oldString.
> Provide more surrounding lines in oldString to identify the correct match.
> ```

**解决方法**：
- 让 AI 提供更多上下文（多包含几行代码），确保唯一匹配
- 或者用 `replaceAll` 参数一次性替换所有匹配

---

## 🚀 高级功能

### Fork 会话

> ❓ **为什么需要**？
> 有时候你想从对话的某个节点"分叉"出去，尝试不同的方向，但又不想丢掉原来的对话。Fork 就是干这个的。

Fork 会复制当前会话的所有历史消息，创建一个新会话。新会话的标题会加上 `(fork #1)` 后缀，再次 Fork 则递增为 `(fork #2)`、`(fork #3)`……

**操作方式**：

在终端界面使用 CLI 指令：

```bash
opencode -c --fork
```

在 TUI 里，Fork 没有默认快捷键，你可以在 `tui.json` 中给它绑一个：

```json
{
  "keybinds": {
    "session_fork": "<leader>f"
  }
}
```

配置后，按 `Ctrl + X` `f` 就能 Fork 当前会话。

> ✅ **预期效果**：新会话出现，标题类似 `原标题 (fork #1)`

---

