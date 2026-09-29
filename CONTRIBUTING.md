# 团队作品集协作与提交指南 (CONTRIBUTING.md)

欢迎加入项目！我们的 GitHub 仓库 `team-portfolio` 不仅是文件存储，更是老师中期检查和最终评分的**核心证据库**。

为了保证大家不出现 Git 冲突、不影响自动化主页（`index.html`）生成，并且**稳稳拿满老师的评分点**，请所有队友严格遵守以下规则和操作流程。

---

## 🚨 第一部分：三条绝对红线（禁止触碰）

### 1. 绝对不要直接修改 `main` 分支
`main` 是老师查看的正式版本。所有人都不允许直接在 `main` 上修改或直接 push。**每次干活必须新建分支。**

### 2. 绝对不要手动修改 `index.html`
根目录的 `index.html` 是由机器人（GitHub Actions）自动生成的。**一旦你手动修改它，会导致团队推送发生严重冲突，且你的修改会被机器人覆盖。** 如果你不小心改了，请立即在 Git Bash 执行 `git checkout -- index.html` 放弃本地修改。

### 3. 绝对不要两个人同时修改同一个文件
Git 无法合并 Word 文档或多个人同时编辑的 Markdown。**必须一人一文件。** Logbook 各写各的，提案按章节分工，绝不允许多人共用一个 `.md` 文件。

### 🚨 特别提醒（外方课要求）：必须使用英文
*   **Logbook 内容**：必须用英文写，不要写中文。
*   **Git 提交信息（commit message）**：**必须用英文**，不要写中文。比如写成 `git commit -m "log: update weekly log"`。
*   **提案内容**：最终交给老师的提案必须是全英文。

---

## 🚀 第二部分：全员标准工作流程（含专属命令）

**（首次准备工作）**：第一次使用需要克隆仓库并配置身份。`"Your Name"` 填你自己姓名全小写，如 `xuhancheng`，邮箱填你注册 GitHub 时用的邮箱地址：

```bash
git clone https://github.com/Henry-Xu-0929/team-portfolio.git
cd team-portfolio
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

**（每天工作流程）**：请**只复制运行自己名字对应的命令块**，不要运行别人的。

### 🔴 队长 xuhancheng 专属命令：
```bash
# 1. 同步最新代码
git checkout main
git pull origin main

# 2. 新建自己的分支
git checkout -b log/xuhancheng-2026-09

# 3. 在电脑上修改 logbook/members/xuhancheng/2026-09.md（内容必须用英文写，日期请改成现在的年、月）

# 4. 提交并推送（提交信息必须是英文）
git add .
git commit -m "log: xuhancheng weekly update"
git push -u origin log/xuhancheng-2026-09
```

### 🟢 队友 chizijun 专属命令：
```bash
# 1. 同步最新代码
git checkout main
git pull origin main

# 2. 新建自己的分支
git checkout -b log/chizijun-2026-09

# 3. 在电脑上修改 logbook/members/chizijun/2026-09.md（内容必须用英文写，日期请改成现在的年、月）

# 4. 提交并推送（提交信息必须是英文）
git add .
git commit -m "log: chizijun weekly update"
git push -u origin log/chizijun-2026-09
```

### 🔵 队友 yeborui 专属命令：
```bash
# 1. 同步最新代码
git checkout main
git pull origin main

# 2. 新建自己的分支
git checkout -b log/yeborui-2026-09

# 3. 在电脑上修改 logbook/members/yeborui/2026-09.md（内容必须用英文写，日期请改成现在的年、月）

# 4. 提交并推送（提交信息必须是英文）
git add .
git commit -m "log: yeborui weekly update"
git push -u origin log/yeborui-2026-09
```

### 🟣 队友 wuruiyang 专属命令：
```bash
# 1. 同步最新代码
git checkout main
git pull origin main

# 2. 新建自己的分支
git checkout -b log/wuruiyang-2026-09

# 3. 在电脑上修改 logbook/members/wuruiyang/2026-09.md（内容必须用英文写，日期请改成现在的年、月）

# 4. 提交并推送（提交信息必须是英文）
git add .
git commit -m "log: wuruiyang weekly update"
git push -u origin log/wuruiyang-2026-09
```

**（全员推送后的动作）**：推送成功后，立刻去 GitHub 网页端：
1. 点页面顶部的黄色提示条 **Compare & pull request**。
2. 确认 `base` 是 `main`，`compare` 是你刚推的分支。
3. 点击 **Create pull request**。
4. 在群里 @ 队长（xuhancheng），告诉他你提交了 PR，等待他合并。

---

## 👑 第三部分：队长合并 PR 的标准步骤

队友提交了 PR 后，队长打开 GitHub 的 **Pull requests** 标签：

1. 点进队友的 PR。
2. 点击 **Files changed**，检查他是不是只改了自己 `logbook/members/名字/` 下的文件。
   * ⚠️ **如果发现他动了 `index.html` 或别人的文件，立刻在 PR 里留言让他改，不要点合并！**
3. 确认无误，点击页面底部的 **Squash and merge**。
4. 在弹出的框中点击 **Confirm squash and merge**。
5. 合并成功后，点击 **Delete branch** 删掉这个临时分支。
6. 此时，队友的修改正式进入 `main` 分支，GitHub Actions 会自动重新生成 `index.html`。

**队长每天合并完队友的 PR 后，在自己电脑上执行：**
```bash
git checkout main
git pull origin main
```

---

## ⚠️ 第四部分：常见报错与解决

### 1. `git push` 被拒绝（rejected - fetch first）？
**原因**：你在本地工作的时候，机器人（或者队友）已经更新了远程仓库，你的本地版本落后了。
**解决**：直接在 Git Bash 执行：
```bash
git pull --rebase origin main
git push origin main  # 或者你的分支名
```
*   `--rebase` 会把你的修改“垫”在最新代码之上，避免产生多余的合并记录。

### 2. 遇到文件冲突（CONFLICT）？
如果 `git pull` 之后提示冲突，通常是因为你手动改了 `index.html`。直接执行：
```bash
git checkout --theirs index.html
git add index.html
git rebase --continue
```
*   `--theirs` 表示放弃你的修改，直接使用远程版本。如果是你负责的 `.md` 文件冲突了，立刻在群里求助队长，不要乱删代码。

### 3. 误操作把文件删了或者改坏了？
不要慌，只要还没 `git commit`，执行：
```bash
git checkout -- 文件名
```
即可恢复到修改前的状态。

---

## 📝 第五部分：格式转换（如何把 MD 变成 Word/PDF）

Markdown (`.md`) 适合协作和版本控制，但最终提交给老师可能需要 Word 或 PDF。

*   **方法一（最推荐，VS Code 插件）**：安装 `Markdown PDF` 插件，打开 `.md` 文件，按 `Ctrl+Shift+P`，输入 `Markdown PDF: Export (pdf)`。
*   **方法二（在线转换，最快）**：打开 [CloudConvert](https://cloudconvert.com/md-to-docx) 或 [Dillinger](https://dillinger.io/)，上传 `.md`，选择输出为 `.docx` 或 `.pdf`。
*   **方法三（Pandoc，最强大）**：安装 Pandoc 后，在终端运行 `pandoc proposal.md -o proposal.docx` 生成 Word。
*   **最佳团队操作流程**：
    1. 队友各自写 `.md` 草稿。
    2. 由一名负责人汇总到 Word 里统一排版。
    3. 导出为 `proposal-v1.0.pdf`，放入 `project-proposal/exports/` 目录。
    4. 把最终 PDF 提交到 Canvas。

**⚠️ 注意**：如果要把 Word/PPT 上传到 GitHub，去修改 `scripts/generate_index.py` 里的 `SHOW_EXTS`，加上 `".docx", ".pptx"`，机器人才能把链接显示在主页上。

---

## ✅ 第六部分：每日开工前检查清单
- [ ] 执行过 `git checkout main && git pull origin main`
- [ ] 创建了自己的独立分支（不是 main）
- [ ] 没有手动修改 `index.html`
- [ ] 没有和队友同时在改同一个文件
- [ ] Logbook 内容是用英文写的，且记录了产出物链接
- [ ] Commit message 是用英文写的
- [ ] 如果开了会，48小时内提交了会议纪要
- [ ] 提案章节按时提交 PR，等待队长合并

**我们是一个团队，共同维护这个仓库就是保护我们的最终分数。有任何 Git 问题，随时在群里问，不要瞎操作。祝大家项目顺利！**