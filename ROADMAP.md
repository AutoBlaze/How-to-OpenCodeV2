# How-to-OpenCodeV2 更新路线图

> 🎯 **目标**：成为 OpenCode V2 最好的中文新手教学指南。
>
> 📌 **定位**：V2 原生、每条结论有证据来源、版本和验证日期标清、附带新手避坑手册。

---

## 现状

| 内容 | 状态 |
|------|------|
| 第 1 章 打开 OpenCode | ✅ 已按 V2 更新 |
| 第 2 章 学习 AI Agent | ✅ 已按 V2 更新 |
| 第 3 章 自建写作 Agent | ✅ 已按 V2 更新 |
| 附赠：Git 操作全流程 | ✅ 与 V2 无关，格式已整理 |
| 配置示例（`opencode_config/`） | ✅ 已更新为 V2 写法 |
| 截图 | ⏸ 暂时保留旧图（v1.3.17 界面），后续统一更新 |

---

## 内容路线图

### P0：V2 必备章节

| 章 | 主题 | 要点 |
|----|------|------|
| 04 | 权限与安全 | `permissions` 有序数组（`bash→shell`、`task→subagent`）；`external_directory` 默认放行；`.env` 读取询问；`--auto` 的风险；`policies`；`session export --sanitize`；密钥的保存方式 |
| 05 | 模型与提供商 | `/connect` 多账号；免费模型与限额；国产模型接入；`#variant`；本地 Ollama / LM Studio；自定义 provider |
| 06 | 上下文与会话 | `/compact` 与 `compaction.buffer`；会话列表与标签页；`/fork`；快照与 `/undo` 的边界；`/btw`；排队提示 |
| 07 | Skills | `SKILL.md`、`@skill-id`、与命令的区别、发现路径 |
| 08 | MCP 与联网 | `mcp.servers`、`opencode mcp add`、`websearch` / `webfetch`、常用 MCP 示例 |

### P1：V2 新体验与场景实战

| 章 | 主题 |
|----|------|
| 09 | V2 新体验：桌面端与网页端（`opencode pair`）、`mini`、后台服务与 `--standalone`、worktree、并行会话、后台子代理、`/goal`、`/review`、`/diff` |
| 10 | 自动化：`opencode run`、`--format json`、`serve`、CI 示例 |
| 11 | 场景实战线：内容创作、办公效率、程序员线 |
| 12 | 插件：V2 插件 API 概览，V1 插件迁移提示 |

### 附录

- **A. 从 V1 迁移速查表**：配置字段、目录、命令、键位的新旧对照
- **B. 命令和快捷键速查**：一页纸
- **C. 排错 FAQ**：Leader 键分步按、`Ctrl+Shift+字母` 在多数终端无效、免费额度 429、环境变量对后台服务不生效、VS Code 插件版本要求、网络问题
- **D. 术语表**

---

## 质量保障

1. **证据标签**：规范见 `workTools/tuitorial_md_improve.md` 的"证据标签"一节。
2. **每章元信息**：章首标明适配版本和最后验证日期。
3. **版本记录**：`VERSION.md` 记录已验证版本、已实测结论和待验证清单。
4. **版本守护**：OpenCode V2 每发布新 minor 版本，对照官方 changelog 的变更逐项核对。
5. **半自动校验脚本**：对比 `opencode --help`、`opencode debug agents`、`GET /api/command`、`GET /openapi.json` 的输出与教程里的命令表，发现差异时提醒。
6. **练习可复现**：每章附 `examples/` 素材与期望输出。

---

## 仓库工程

| 项目 | 状态 |
|------|------|
| `LICENSE` 文件（CC BY-NC-SA 4.0） | ✅ 已添加 |
| 教程迁移到 `docs/` 并使用数字前缀文件名 | ✅ 已完成 |
| README 链接指向 `docs/` | ✅ 已完成 |
| README 首屏改造（横幅、徽章、30 秒上手、学习路线图、章节地图、FAQ） | ✅ 已完成 |
| `CONTRIBUTING.md`、Issue 模板（勘误、版本不符、章节建议）、PR 模板 | ✅ 已完成 |
| Social preview 图（`Assets/Brand/social-preview.png`，1280×640） | ✅ 已制作，需在 GitHub 仓库设置里手动上传 |
| GitHub topics 与仓库描述 | ⬜ 需在 GitHub 仓库设置里手动填写 |
| README 演示 GIF（终端录屏） | ⏸ 随截图一起更新 |
| 在线站点（VitePress + GitHub Pages） | ⏸ 暂不做 |
| 英文 README | ⏸ 暂不做 |
| 仓库改名（`git_test` → `How-to-OpenCodeV2`） | ✅ 已完成 |

---

## 分阶段里程碑

| 阶段 | 目标 | 交付物 | 验收标准 |
|------|------|--------|----------|
| 0 | 打地基 | LICENSE、`docs/` 迁移、证据标签规范、`VERSION.md`、README 改造、治理文件 | 仓库对外看起来可信、有人维护 |
| 1 | P0 核心 | 第 4、5、6 章 | 每章有证据标注，练习可复现 |
| 2 | P0 收尾与附录 | 第 7、8 章，附录 A / B / C | 新手能完整走通 V2 |
| 3 | 工具化 | 校验脚本与定期检查（站点和英文版视情况再定） | 版本差异能被发现 |
| 4 | P1 | 第 9–12 章，场景实战线 | 覆盖新手、创作者、办公、开发者 |
| 5 | 发布与增长 | 重截 V2 截图和 GIF，首发推广，资源列表投稿 | 首发渠道上线 |

---

## 发布与增长

- **投稿**：`awesome-opencode` 资源列表、OpenCode 官方 Discord 的 showcase。
- **中文渠道**：掘金、知乎、V2EX、少数派、公众号、小红书、B 站。标题用"V1 升级 V2 踩坑清单""新手 30 分钟上手"这类容易被搜索的写法。
- **合作而不是对立**：与同类中文教程（如 learn-opencode）互链，定位为"V2 优先的精简版"。
- **节奏**：每章发布时打 Release tag，每次 V2 升级写更新记录。
- **衡量**：星标、Fork、勘误 Issue 数、搜索关键词排名。

---

## 风险

| 风险 | 应对 |
|------|------|
| V2 发布频繁，教程容易过时 | 版本守护、校验脚本、`VERSION.md` |
| 官方文档自相矛盾（如 Windows 的 winget） | 标注矛盾，不替官方裁决，教程只写已验证的方式 |
| 第三方证据质量不一 | 只做补充，不当结论，放入"待验证" |
| 与同类教程内容重叠 | V2 原生、证据标注、排错手册做差异化 |
| 许可证为非商用条款（NC），限制部分转载 | 已决定保留 CC BY-NC-SA 4.0 |
| 密钥、邮箱等个人信息泄露 | 示例和教程中不放真实信息；提交前检查 |
