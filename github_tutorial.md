# Git 操作全流程解析（新手版）

## 整体流程概览

```
本地创建文件 → 初始化 Git → 配置身份 → 创建 .gitignore → 添加到暂存区 → 提交到本地仓库 → 连接远程 → 推送到 GitHub
```

---

## 每一步详细解释

### 1. 配置 Git 身份信息
```bash
git config --global user.name "zhisheng2200"
git config --global user.email "zhishengpsu@gmail.com"
```
**作用：** 告诉 Git "你是谁"。每次提交代码时，Git 会记录提交者的名字和邮箱，就像在文件上签名一样。`--global` 表示这台电脑上所有项目都用这个身份。

---

### 2. 初始化 Git 仓库
```bash
git init
```
**作用：** 在项目文件夹里创建一个 `.git` 隐藏文件夹，相当于给这个文件夹"装上 Git 监控"。之后 Git 会开始跟踪这里的所有文件变化。

---

### 3. 查看当前状态
```bash
git status
```
**作用：** 查看哪些文件被 Git 跟踪了，哪些还没有。执行后显示：
- `.gitignore` 和 `AGENTS.md` 是未跟踪的文件
- 其他文件（如 `hello.txt`、`*.docx`）已被 `.gitignore` 忽略

---

### 4. 创建 .gitignore 文件
```
（通过 AI 助手 OpenCode 创建 .gitignore 文件）
```
**作用：** 用户向 OpenCode 发送指令，要求分析项目文件并创建 `.gitignore`。OpenCode 会：
1. 先运行 `git status` 查看当前文件状态
2. 分析哪些文件是临时的、测试的、或不需要版本控制的
3. 自动创建 `.gitignore` 文件，写入需要忽略的文件规则
4. 向用户解释每条规则的作用

**用户当时的 prompt：**
```
帮我检查哪些文件不必要提交，添加到 .gitignore。
要求：
1) 先运行并参考 git status / git diff（只看，不要直接提交/推送）
2) 只修改/创建 .gitignore，改完后把 .gitignore 的内容贴出来并解释每一条为什么要忽略
3) 如果发现 .env、密钥、token 之类的敏感文件，先停下提醒我
```

---

### 5. 添加到暂存区
```bash
git add .
```
**作用：** 把当前目录下所有**未被忽略**的文件放进"暂存区"。`.` 表示"当前目录所有文件"。暂存区就像一个"打包准备区"，告诉 Git "这些文件我准备要提交了"。

> ⚠️ 出现了警告 `LF will be replaced by CRLF`，这是 Windows 和 Linux 换行符不同导致的，不影响使用。

---

### 6. 提交到本地仓库
```bash
git commit -m "init"
```
**作用：** 把暂存区里的文件正式"存档"到本地 Git 仓库。`-m "init"` 是提交说明，相当于给这次存档写个备注。执行后显示：
- `2 files changed`：2 个文件被提交
- `create mode 100644`：文件权限模式

---

### 7. 重命名分支
```bash
git branch -M main
```
**作用：** 把默认分支名从 `master` 改成 `main`。这是 GitHub 推荐的命名规范，`-M` 表示强制重命名。

---

### 8. 添加远程仓库地址
```bash
git remote add origin https://github.com/AutoBlaze/git_test.git
```
**作用：** 告诉本地 Git "云端仓库在哪里"。`origin` 是给远程仓库起的别名（默认叫这个），后面是 GitHub 仓库的 URL。

---

### 9. 推送到 GitHub
```bash
git push -u origin main
```
**作用：** 把本地 `main` 分支的所有提交上传到远程 `origin` 仓库。`-u` 表示"建立跟踪关系"，之后只需输入 `git push` 即可，不用再指定分支。

执行结果：
```
* [new branch]      main -> main
```
表示本地 `main` 分支成功推送到了 GitHub。

---

## 总结流程图

```
本地电脑                          GitHub 云端
┌─────────────┐                  ┌─────────────┐
│ 工作区       │                  │             │
│ (你的文件)   │                  │             │
│      ↓       │                  │             │
│ git add .    │                  │             │
│      ↓       │                  │             │
│ 暂存区       │                  │             │
│ (准备打包)   │                  │             │
│      ↓       │                  │             │
│ git commit   │                  │             │
│      ↓       │                  │             │
│ 本地仓库     │ ── git push ──→ │ 远程仓库    │
│ (已存档)     │                  │ (GitHub)    │
└─────────────┘                  └─────────────┘
```

## 核心概念

| 命令 | 比喻 |
|---|---|
| `git add` | 放进购物车 |
| `git commit` | 结账打包 |
| `git push` | 快递寄到云端 |

---

# 日常更新 GitHub 教程

## 最简单的三步流程

每次修改完项目文件后，只需运行这三条命令：

```bash
git add .
git commit -m "描述你做了什么"
git push
```

---

## 详细步骤

### 1. 查看修改了哪些文件
```bash
git status
```
**作用：** 查看哪些文件被修改了、新增了、或删除了。

---

### 2. 添加到暂存区
```bash
git add .
```
**作用：** 把所有修改过的文件放进"准备区"。`.` 表示当前目录所有变更。

> 如果只想提交某个文件，可以用 `git add 文件名`

---

### 3. 提交到本地仓库
```bash
git commit -m "修复了登录页面的样式问题"
```
**作用：** 把暂存区的文件正式存档。`-m` 后面写提交说明，要简洁明了地描述这次改了什么。

---

### 4. 推送到 GitHub
```bash
git push
```
**作用：** 把本地存档上传到云端。因为之前已经用 `-u` 建立了跟踪关系，现在只需输入 `git push` 即可。

---

## 完整示例

假设你修改了 `AGENTS.md` 文件：

```bash
# 查看状态
git status

# 添加到暂存区
git add .

# 提交并写说明
git commit -m "更新项目规则，添加代码规范"

# 推送到 GitHub
git push
```

---

## 常用场景

| 场景 | 操作 |
|---|---|
| 日常更新 | `git add .` → `git commit -m "说明"` → `git push` |
| 只想看改了啥 | `git status` |
| 查看具体修改内容 | `git diff` |
| 查看提交历史 | `git log --oneline` |
| 拉取云端最新代码 | `git pull` |

---

## 注意事项

- **频繁提交**：建议每次完成一个小功能就提交一次，不要攒太多
- **说明要清晰**：`-m` 后面的说明要让人一看就知道这次改了什么
- **先 pull 再 push**：如果多人协作，push 前先 `git pull` 拉取最新代码，避免冲突
