# 贡献指南

感谢你愿意帮助 How-to-OpenCodeV2 变得更好。这是一份面向新手的 OpenCode V2 中文教程，我们最看重两件事：**准确**和**简洁**。

## 你可以怎么参与

| 方式 | 说明 |
|------|------|
| 🐛 勘误 | 发现错别字、错误命令、过时内容 |
| 🔄 版本不符 | 你的 OpenCode 版本行为和教程不一致 |
| 💡 章节建议 | 希望增加的主题（可参考 [路线图](ROADMAP.md)） |
| 🔀 Pull Request | 直接修改文档或补充章节 |

提交前请先在 [Issues](https://github.com/AutoBlaze/How-to-OpenCodeV2/issues) 里搜索，避免重复。

## 提交 Issue

请使用对应的 Issue 模板，并尽量写清：

- 你的 **OpenCode 版本**（运行 `opencode -v`）
- 你的**操作系统**和使用的**终端**（PowerShell、Windows Terminal、macOS Terminal 等）
- 出问题的**章节和位置**
- 你实际看到的现象，以及教程里写的预期

> ⚠️ **不要贴出 API Key、邮箱等隐私信息。** 如果日志或配置里有密钥，请先删除或打码。

## 提交 Pull Request

1. Fork 本仓库，新建分支
2. 修改文档或示例，保持改动**最小且聚焦**
3. 对照下面的写作规范自查
4. 发起 Pull Request，按模板说明改了什么、依据是什么

### 写作规范

完整规范见 [`workTools/tuitorial_md_improve.md`](workTools/tuitorial_md_improve.md)，要点如下：

- 使用简体中文；英文术语首次出现时加中文解释
- 代码块标注语言类型；命令和代码保持英文原样
- 章节文件放在 `docs/`，使用数字前缀、英文小写加连字符命名（如 `04-permissions.md`）
- 标题带 emoji 时，用 `<a id="xxx"></a>` 自定义锚点，保证目录跳转有效
- 图片放在 `Assets/Pictures/`，在 `docs/` 里用相对路径 `../Assets/Pictures/xxx.png` 引用

### 证据标签

教程里的**命令、快捷键、配置字段、默认行为、版本差异**等关键结论，需要有可靠来源：

| 标签 | 含义 |
|------|------|
| 官方文档 | 来自 [opencode.ai/v2/docs](https://opencode.ai/v2/docs/) |
| 实测 | 在 OpenCode V2 上实际运行验证过 |
| 第三方 | 来自 GitHub issue 或第三方文章，仅作补充，不写成定论 |
| 待验证 | 暂无可靠证据，不写进正文，记录到 [`VERSION.md`](VERSION.md) |

- 在句末或引用块里标注来源，例如"（实测）"
- 没有证据的内容，宁可不写，也不要写成定论
- 你验证过的新结论，请同步更新 [`VERSION.md`](VERSION.md)

### 提交前检查清单

- [ ] 命令和配置在 OpenCode V2 上能正常运行
- [ ] 关键结论有来源，不确定的没有写成定论
- [ ] 文中没有真实 API Key、邮箱、个人路径等隐私信息
- [ ] 链接和图片路径都能打开
- [ ] 目录跳转（锚点）正常

## 行为准则

请保持友善、尊重和就事论事。我们欢迎各种水平的学习者提问和纠错。对人身攻击、歧视性言论和刷屏广告，维护者有权删除内容并限制参与。

## 许可

提交内容即表示你同意以 [CC BY-NC-SA 4.0](LICENSE) 协议发布你的贡献。
