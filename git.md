# Git 核心指令分类

<https://www.runoob.com/git/git-create-repository.html>

<!-- markdownlint-disable MD033 -->
> 本文档整理了常用的 Git 操作命令，按照数据流向与功能分类，方便快速查找与使用。

## 一、工作区与暂存区操作

### 1. 添加文件 (`git add`)

| 命令 | 方向 | 作用 | 场景示例 |
|------|------|------|----------|
| `git add <file>` | 正向 | 添加文件到暂存区 | `git add README.md` |
| `git add -p` | 正向 | 交互式选择代码块暂存 | 只提交部分修改 |
| `git add .` | 正向 | 添加当前目录所有变更 | 提交所有更改 |

### 2. 撤销操作

| 命令 | 方向 | 作用 | 场景示例 |
|------|------|------|----------|
| `git restore --staged <file>` | 反向 | **从暂存区撤出**（不删除工作区文件） | `git restore --staged config.yml` |
| `git rm --cached <file>` | 反向 | 从暂存区删除并**停止跟踪**（保留工作区文件） | `git rm --cached .env.local` |
| `git restore <file>` | 反向 | 丢弃工作区修改 | `git restore src/main.js` |

## 二、本地仓库操作

### 1. 提交更改 (`git commit`)

| 命令 | 方向 | 作用 | 场景示例 |
|------|------|------|----------|
| `git commit -m "msg"` | 正向 | 提交到本地仓库 | `git commit -m "feat: add login"` |
| `git commit -a -m "msg"` | 正向 | **跳过暂存**，直接提交所有已跟踪文件 | `git commit -am "fix: typo"` |
| `git commit --amend` | 正向 | 修改最近一次提交 | 补漏文件或改提交消息 |

### 2. 撤销提交

| 命令 | 方向 | 作用 | 场景示例 |
|------|------|------|----------|
| `git revert <commit>` | 反向 | **撤销指定提交**（生成反向提交，保留历史） | `git revert abc123` |
| `git reset --soft HEAD~1` | 反向 | 撤销提交但保留修改到暂存区 | 重写提交消息或拆分提交 |
| `git reset --hard HEAD~1` | 反向 | **彻底删除提交**（慎用！丢失修改） | 放弃最近一次提交的所有改动 |

## 三、分支管理

### 1. 分支基本操作

| 命令 | 方向 | 作用 | 场景示例 |
|------|------|------|----------|
| `git branch` | 查看 | 查看本地分支 | `git branch` |
| `git checkout -b <branch>` | 正向 | 创建并切换分支 | `git checkout -b feat/login` |
| `git switch -c <branch>` | 正向 | 创建并切换分支（新语法） | `git switch -c fix/header` |
| `git branch -d <branch>` | 反向 | 安全删除已合并分支 | `git branch -d old-feature` |

### 2. 分支合并

| 命令 | 方向 | 作用 | 场景示例 |
|------|------|------|----------|
| `git merge <branch>` | 正向 | **合并分支**到当前分支 | `git merge feat/search` |
| `git rebase <branch>` | 正向 | **变基分支**（重写提交历史） | `git rebase main` |
| `git cherry-pick <commit>` | 正向 | **复制提交**到当前分支 | `git cherry-pick abc123` |
| `git merge --abort` | 反向 | **中止合并操作** | 解决冲突时放弃操作 |
| `git rebase --abort` | 反向 | **中止变基操作** | 变基遇到问题时中止 |

## 四、远程仓库交互

### 1. 推送与拉取

| 命令 | 方向 | 作用 | 场景示例 |
|------|------|------|----------|
| `git push -u origin <branch>` | 正向 | 首次推送并关联分支 | `git push -u origin feat/chat` |
| `git push` | 正向 | 推送当前分支到远程 | `git push` |
| `git pull` | 正向 | **拉取并合并远程更新** | `git pull origin main` |
| `git fetch` | 正向 | 仅下载远程更新（不合并） | `git fetch` |

### 2. 远程分支管理

| 命令 | 方向 | 作用 | 场景示例 |
|------|------|------|----------|
| `git push --force-with-lease` | 反向 | 安全强制推送（覆盖远程提交） | `git push --force-with-lease` |
| `git push origin --delete <branch>` | 反向 | 删除远程分支 | `git push origin --delete old-branch` |
| `git branch -r` | 查看 | 查看远程分支 | `git branch -r` |

## 五、临时操作与代码恢复

### 1. 工作区暂存

| 命令 | 方向 | 作用 | 场景示例 |
|------|------|------|----------|
| `git stash` | 正向 | **临时保存未提交的修改** | `git stash` |
| `git stash save "WIP"` | 正向 | 临时保存并添加描述 | `git stash save "登录页面开发中"` |
| `git stash pop` | 正向 | 恢复最近一次暂存修改 | `git stash pop` |
| `git stash list` | 查看 | 查看所有暂存记录 | `git stash list` |
| `git stash drop` | 反向 | 删除指定暂存记录 | `git stash drop stash@{0}` |

### 2. 代码恢复

| 命令 | 方向 | 作用 | 场景示例 |
|------|------|------|----------|
| `git checkout HEAD~1 <file>` | 反向 | 从历史提交恢复文件 | `git checkout HEAD~1 src/styles.css` |
| `git reflog` | 查看 | 查看引用日志（可用于恢复删除的分支） | `git reflog` |

## 六、常见工作流程示例

### 1. 功能开发流程

```bash
# 1. 开发新功能（正向）
git checkout -b feat/search
git add -p  # 选择暂存
git commit -m "feat: add search UI"
git push -u origin feat/search

# 2. 创建合并请求(PR)并完成代码审查
# (在GitHub/GitLab等平台操作)

# 3. 合并完成后清理分支
git checkout main
git pull  # 获取最新主分支
git branch -d feat/search  # 删除本地分支
git push origin --delete feat/search  # 删除远程分支
```

### 2. 紧急修复流程

```bash
# 1. 暂存当前工作
git stash save "保存搜索功能开发进度"

# 2. 创建修复分支
git checkout main
git pull
git checkout -b hotfix/login

# 3. 修复、提交并推送
git commit -am "fix: login error"
git push -u origin hotfix/login

# 4. 创建PR并合并修复

# 5. 恢复之前的开发
git checkout feat/search
git stash pop  # 恢复暂存的代码
```

## 七、反向操作速查表

| 想撤销的操作 | 对应命令 | 危险等级 |
|--------------|----------|----------|
| **误暂存文件** | `git restore --staged <file>` | ⭐️ |
| **误提交（需修改）** | `git reset --soft HEAD~1` | ⭐️ |
| **误提交（需彻底删除）** | `git reset --hard HEAD~1` | ⭐️⭐️⭐️ |
| **误推送提交** | `git push --force-with-lease` | ⭐️⭐️ |
| **误合并/变基操作** | `git merge --abort` / `git rebase --abort` | ⭐️⭐️ |
| **误删分支** | `git reflog` + `git checkout -b <branch> <commit-hash>` | ⭐️⭐️ |

---
