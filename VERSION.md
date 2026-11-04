# 版本验证记录

> 📌 本文件记录教程已验证的 OpenCode 版本，以及哪些结论是实测的、哪些仍待验证。每次 OpenCode V2 发布新的 minor 版本后，对照官方 [changelog](https://opencode.ai/changelog) 重新核对。

## 当前适配版本

| 项目 | 内容 |
|------|------|
| OpenCode 版本 | v2.2.5 |
| 验证日期 | 2026-11-04 |
| 验证平台 | Windows 11 + PowerShell |
| 安装方式 | `npm install -g @opencode/cli` |

## 已实测的结论

| 结论 | 涉及章节 |
|------|----------|
| edit 工具只做精确匹配；失败时报错会列出文件里最接近的行 | 第 1 章 |
| `/init` 后面可以附带大段文字说明 | 第 2 章 |
| Explore Agent 的描述里仍有 quick / medium / very thorough 三档 | 第 2 章 |
| Plan Agent 的可写路径是 `~/.opencode/plan/*`（`opencode debug agents` 输出） | 第 2 章 |
| 命令文件新建、修改、删除后无需重启，立即生效 | 第 3 章 |
| 命令模板里的 `@文件名` 不会展开，AI 收到的是原样文字 | 第 3 章 |
| `.opencode/commands/`（复数）目录被识别 | 第 3 章 |
| Leader 组合键必须分两步按：先按 `Ctrl+X` 并松开，再单独按后面的键；按下后输入框变灰，`Esc` 可取消；默认等待 2000 毫秒 | 第 1 章 |
| 输入 `/` 会列出教程中的斜杠命令；输入 `@` 会列出 `@explore`、`@general` | 第 1 章 |
| `session list -n` 仍可用 | 第 1 章 |
| `Ctrl+Shift+P` 在 PowerShell 终端里无效，`Ctrl+P` 可打开命令面板 | 第 1 章 |

## 来自官方文档、尚未自行实测

- 全新安装的 V2 默认用 `Shift+Tab` 切换 Agent（本机配置从 V1 迁移，保留了 `Tab`）
- 子会话默认键位 `↓`、`→`、`←`、`↑`（本机迁移配置曾覆盖过，现已恢复默认）
- `todowrite` 默认关闭，需 `experimental.todo: true`
- Agent 文件里的 `temperature` 等采样参数不会发送给模型
- V2 只识别 `AGENTS.md`，不再回退到 `CLAUDE.md`
- `providers.<ID>.settings.apiKey` 的新写法，以及 `example_opencode.json` 的自定义 provider 配置
- 环境变量要设置在后台服务进程上（`opencode service set env`）

## 待验证

| 内容 | 说明 |
|------|------|
| Windows 上通过 winget 安装 | 官方文档首页说不支持 Windows 包管理器，但 changelog 2.0.28 提到了 winget，二者矛盾；教程只写 npm |
| 顶层 `opencode --fork` 是否报错 | `opencode --help` 的 flag 列表里没有它，未直接运行验证 |
| 系统环境变量（方式二）是否会被后台服务读到 | 官方文档只明确了 `opencode service set env` |
| VS Code 插件 `sst-dev.opencode` v1.0.0 与 V2 的兼容性 | 依据是 GitHub issue 里维护者的回复，未自行安装验证 |
| `/themes`、`/fork` 等命令的精确名称 | 已在 TUI 里看到命令列表，但个别命令的别名未逐个测试 |
| `learnopencode.com` 当前对应 V1 还是 V2 | 未核实 |
| `Ctrl+Shift+P` 在 Windows Terminal 中被终端自身占用 | 仅为推测，未在 Windows Terminal 设置里核对 |
