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

## 八、个人开发常见操作合集

### 1. 初始化项目并推送到远程

```bash
# 本地初始化
git init
git add .
git commit -m "chore: initial commit"

# 关联远程仓库
git remote add origin https://github.com/username/project.git
git branch -M main
git push -u origin main
```

### 2. 克隆项目并开始开发

```bash
# 克隆仓库
git clone https://github.com/username/project.git
cd project

# 查看项目状态
git status
git log --oneline --graph --all

# 创建开发分支
git checkout -b dev
```

### 3. 日常开发提交流程

```bash
# 查看修改内容
git status
git diff

# 分阶段提交
git add src/components/
git commit -m "feat: add user component"

git add src/utils/
git commit -m "refactor: optimize utils"

# 推送到远程
git push origin dev
```

### 4. 同步主分支最新代码

```bash
# 方法1：使用 merge（保留完整历史）
git checkout main
git pull origin main
git checkout dev
git merge main

# 方法2：使用 rebase（保持线性历史）
git checkout dev
git fetch origin
git rebase origin/main

# 如遇冲突解决后
git add .
git rebase --continue
```

### 5. 修改最近的提交

```bash
# 场景1：忘记添加文件
git add forgotten-file.js
git commit --amend --no-edit

# 场景2：修改提交信息
git commit --amend -m "feat: add user component with validation"

# 场景3：修改多个提交（交互式变基）
git rebase -i HEAD~3
# 在编辑器中：
# pick -> edit（修改提交）
# pick -> reword（修改消息）
# pick -> squash（合并提交）
```

### 6. 查看和对比历史

```bash
# 查看提交历史
git log --oneline --graph --decorate --all
git log --author="yourname" --since="2 weeks ago"

# 查看某个文件的修改历史
git log -p src/main.js
git blame src/main.js

# 对比差异
git diff HEAD~1 HEAD  # 对比最近两次提交
git diff main dev  # 对比两个分支
git diff --stat  # 查看统计信息
```

### 7. 撤销与回滚操作

```bash
# 撤销工作区修改
git checkout -- file.js  # 旧语法
git restore file.js  # 新语法

# 撤销暂存区文件
git reset HEAD file.js  # 旧语法
git restore --staged file.js  # 新语法

# 回退到某个提交
git reset --soft HEAD~1  # 保留修改在暂存区
git reset --mixed HEAD~1  # 保留修改在工作区（默认）
git reset --hard HEAD~1  # 完全删除修改

# 回退后想恢复
git reflog  # 查找丢失的提交
git reset --hard abc123  # 恢复到指定提交
```

### 8. 紧急保存工作进度

```bash
# 快速保存当前工作
git stash
# 或带描述
git stash save "WIP: 实现用户登录功能"

# 切换分支处理紧急任务
git checkout main
# ...处理紧急问题...

# 回到开发分支恢复工作
git checkout dev
git stash pop  # 恢复并删除stash
# 或
git stash apply  # 恢复但保留stash

# 查看所有stash
git stash list
# 应用特定stash
git stash apply stash@{1}
# 删除stash
git stash drop stash@{0}
git stash clear  # 清空所有
```

### 9. 处理合并冲突

```bash
# 发生冲突后
git status  # 查看冲突文件

# 手动编辑冲突文件，解决冲突标记
# <<<<<<< HEAD
# 当前分支的代码
# =======
# 合并分支的代码
# >>>>>>> branch-name

# 解决后标记为已解决
git add conflict-file.js
git commit -m "merge: resolve conflicts"

# 如果想放弃合并
git merge --abort
git rebase --abort
```

### 10. 清理本地仓库

```bash
# 删除已合并的本地分支
git branch --merged | grep -v "\*" | xargs -n 1 git branch -d

# 清理远程已删除的分支引用
git fetch --prune
git remote prune origin

# 删除未跟踪的文件
git clean -n  # 预览会删除的文件
git clean -f  # 删除文件
git clean -fd  # 删除文件和目录
git clean -fdx  # 包括.gitignore中的文件

# 优化仓库
git gc  # 垃圾回收
git gc --aggressive --prune=now  # 深度清理
```

### 11. 标签管理

```bash
# 创建标签
git tag v1.0.0
git tag -a v1.0.0 -m "Release version 1.0.0"

# 推送标签
git push origin v1.0.0
git push origin --tags  # 推送所有标签

# 查看标签
git tag
git show v1.0.0

# 删除标签
git tag -d v1.0.0  # 删除本地标签
git push origin --delete v1.0.0  # 删除远程标签
```

### 12. 协作开发工作流

```bash
# Fork工作流
# 1. Fork项目到自己账号
# 2. 克隆Fork的仓库
git clone https://github.com/yourname/project.git
cd project

# 3. 添加上游仓库
git remote add upstream https://github.com/original/project.git

# 4. 同步上游更新
git fetch upstream
git checkout main
git merge upstream/main
git push origin main

# 5. 创建功能分支并推送
git checkout -b feat/new-feature
# ...开发...
git push origin feat/new-feature

# 6. 在GitHub/GitLab创建Pull Request
```

### 13. 修改Git配置

```bash
# 查看配置
git config --list
git config user.name
git config user.email

# 设置用户信息
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"

# 设置默认编辑器
git config --global core.editor "code --wait"

# 设置别名
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm commit
git config --global alias.lg "log --oneline --graph --all"

# 使用别名
git st  # 相当于 git status
git lg  # 查看美化的日志
```

### 14. 忽略文件管理

```bash
# 创建.gitignore文件
cat > .gitignore << EOF
# 依赖目录
node_modules/
__pycache__/
venv/

# 环境变量
.env
.env.local

# IDE配置
.vscode/
.idea/

# 构建产物
dist/
build/
*.pyc

# 日志
*.log
logs/

# 系统文件
.DS_Store
Thumbs.db
EOF

# 已跟踪的文件需要取消跟踪
git rm -r --cached node_modules/
git commit -m "chore: remove node_modules from tracking"

# 全局忽略文件
git config --global core.excludesfile ~/.gitignore_global
```

### 15. 子模块管理

```bash
# 添加子模块
git submodule add https://github.com/user/lib.git libs/lib

# 克隆包含子模块的项目
git clone --recursive https://github.com/user/project.git
# 或
git clone https://github.com/user/project.git
cd project
git submodule init
git submodule update

# 更新子模块
git submodule update --remote

# 删除子模块
git submodule deinit libs/lib
git rm libs/lib
rm -rf .git/modules/libs/lib
```

## 九、常见问题解决方案

### 1. 推送被拒绝

```bash
# 场景：远程有新提交
# 解决方案1：先拉取再推送
git pull --rebase origin main
git push

# 解决方案2：强制推送（慎用）
git push --force-with-lease
```

### 2. 误提交敏感信息

```bash
# 从历史中彻底删除文件
git filter-branch --force --index-filter \
  "git rm --cached --ignore-unmatch path/to/secret.txt" \
  --prune-empty --tag-name-filter cat -- --all

# 或使用BFG工具
bfg --delete-files secret.txt
git reflog expire --expire=now --all
git gc --prune=now --aggressive

# 强制推送
git push origin --force --all
```

### 3. 分支名写错了

```bash
# 重命名当前分支
git branch -m old-name new-name

# 重命名其他分支
git branch -m old-branch-name new-branch-name

# 删除远程旧分支，推送新分支
git push origin --delete old-name
git push origin -u new-name
```

### 4. 合并代码后想撤销

```bash
# 如果还没推送
git reset --hard HEAD~1

# 如果已经推送，使用revert
git revert -m 1 <merge-commit-hash>
git push
```

---

## 十、Git命令速记卡

| 操作类型 | 常用命令 |
|---------|---------|
| **初始化** | `git init` / `git clone <url>` |
| **状态查看** | `git status` / `git log --oneline --graph` |
| **添加暂存** | `git add .` / `git add -p` |
| **提交** | `git commit -m "msg"` / `git commit -am "msg"` |
| **分支** | `git checkout -b <branch>` / `git merge <branch>` |
| **远程** | `git push` / `git pull` / `git fetch` |
| **撤销** | `git restore <file>` / `git reset HEAD~1` |
| **暂存** | `git stash` / `git stash pop` |
| **查看差异** | `git diff` / `git diff --staged` |
| **清理** | `git clean -fd` / `git branch -d <branch>` |

---

## 十一、个人开发一页速查（Cheatsheet）

下面是一份可直接复制使用的个人开发速查，适合放在编辑器侧边或打印为纸质卡片：

### 常用状态 & 快速查看

git status                     # 查看当前状态
git lg                         # 美化日志（需 alias 配置，见下）
git log --oneline --graph --decorate --all
git diff                       # 查看未暂存差异
git diff --staged              # 查看已暂存差异

### 提交流程（常规）

git add -A                     # 添加所有改动
git add -p                     # 交互式选择改动
git commit -m "type: 描述"   # 提交
git commit --amend             # 修改最近一次提交（本地未推送）

### 推拉与同步

git fetch origin               # 获取远端更新
git pull --rebase origin main  # 拉取并变基（推荐保持线性历史）
git push -u origin <branch>    # 首次推送并设置上游
git push                       # 后续推送
git push --force-with-lease    # 当确实需要覆写远端时（慎用）

### 分支与代码合并

git switch -c feat/name        # 新建并切换（推荐）
git switch main
git merge feat/name            # 合并（保留历史）
git rebase origin/main         # 在当前分支上变基最新主分支
git cherry-pick <commit>      # 拷贝提交

### 撤销与救援

git restore <file>             # 丢弃工作区文件修改
git restore --staged <file>    # 从暂存区撤出
git reset --soft HEAD~1        # 撤销最近提交，保留到暂存
git reset --hard <commit>      # 强制回退（危险）
git reflog                      # 找回丢失的提交或分支

### 暂存（WIP）与切换任务

git stash save "WIP: 描述"   # 保存当前工作
git stash list                 # 列表
git stash pop                  # 恢复并删除stash
git stash apply stash@{1}      # 应用特定stash

### 合并冲突快速处理

git status                     # 找到冲突文件
// 手动编辑冲突后：
git add <file>
git rebase --continue          # 如果在变基时
git commit -m "merge: resolve conflicts"  # 如果在合并时
git merge --abort              # 放弃合并
git rebase --abort             # 放弃变基

### 清理与优化

git fetch --prune              # 删除已被删除的远程引用
git branch --merged            # 查看已合并的本地分支
git branch -d <branch>         # 删除本地分支（已合并）
git clean -nd                  # 预览将要删除的未跟踪文件
git clean -fd                  # 强制删除未跟踪文件/目录

### 常用 Git 别名（添加到 ~/.gitconfig 或 全局配置）

[alias]
  st = status
  co = checkout
  br = branch
  cm = commit
  lg = log --oneline --graph --decorate --all
  unstage = restore --staged
  last = log -1 --stat

示例（设置别名）:
git config --global alias.lg "log --oneline --graph --decorate --all"

### .gitignore 常见片段

# Python
__pycache__/
*.py[cod]
venv/

# Node
node_modules/

# 系统 / IDE
.DS_Store
.vscode/

---

## 完成说明

已将一页速查追加到文档底部，可按需修改命令风格（merge vs rebase）以匹配你和团队的偏好。
