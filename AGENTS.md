# 项目规则

## 项目目标
这是一个在GitHub上开源的OpenCode学习项目，目的是生成一个user-friendly和简洁高效的线上学习教材。

## 项目结构
- `docs/NN-xxx.md` - OpenCode 教程章节（`01-meet-opencode.md` 等，文件名使用数字前缀）
- `docs/bonus-git-push-to-github.md` - Git 操作全流程教程（附赠）
- `Assets/Pictures/` - 教程截图（章节里用 `../Assets/Pictures/xxx.png` 引用）
- `Assets/Brand/` - README 横幅和 GitHub social preview 图
- `.github/` - Issue 模板和 PR 模板
- `CONTRIBUTING.md` - 贡献指南
- `opencode_config/` - OpenCode V2 配置示例
- `workTools/` - 写作规范
- `ROADMAP.md` - 后续更新计划
- `VERSION.md` - 已验证的 OpenCode 版本记录

## 技术栈
- 文档格式：Markdown
- 托管平台：GitHub
- 核心内容：OpenCode AI 编程助手教程

## 代码规范
- 使用简体中文
- 合理美化md格式的教程，包括标题、字体、颜色，可以添加少量商务风格emoji
- 代码块注明语言类型
- 有序号的章节使用数字前缀（如 01-, 02-）
- 教程以 OpenCode V2 为准；关键结论按 `workTools/tuitorial_md_improve.md` 里的"证据标签"规范标注来源
- 教程和示例文件里不得出现真实 API Key、邮箱等个人信息

## 敏感文件（已忽略）
- `备份backup/` 目录（包含 API Key，已在 .gitignore 中）
- 任何包含 `sk-` 开头的密钥文件

## 快速启动
1. 阅读 docs/01-meet-opencode.md 了解 OpenCode 基础
2. 查看 docs/bonus-git-push-to-github.md 学习 Git 操作
3. 参考 opencode_config/ 下的示例配置文件
4. 更详细的教学，可参考 https://learnopencode.com/ 学习完整课程
