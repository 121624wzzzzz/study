<!-- markdownlint-disable MD033 -->
# 学习

## ***Markdown*** 语法指南

### 标题分级

```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
```

---

### html报错允许

| 命令格式| 作用范围 | 示例 |
|-|-|-|
| `<!-- markdownlint-disable-next-line MD033 -->` | 仅下一行生效 | 临时允许某行使用 HTML|
| `<!-- markdownlint-disable MD033 -->` | 从当前位置到文件末尾   | 整个代码块允许使用 HTML |
| `<!-- markdownlint-enable MD033 -->`  | 恢复规则检查           | 在 `disable` 后重新启用规则  |

---

### 段落与换行

- 段落间用空行分隔
- 换行：行尾加两个空格或 `<br>`

---

### 文字样式

```markdown
*斜体*  
**粗体**  
***粗斜体***  
~~删除线~~
`行内代码`
```

示例：这是 `print("Hello")` 行内代码。

---

### 有序列表和无序列表

- 项目1
  - 子项目（缩进2空格）

1. 第一项
   1. 子项（缩进3空格）

两者区别在于缩进

---

### 链接与图片

```markdown
[显示文本](实际URL "悬浮提示")  
示例：  
```

[GitHub官网](https://github.com "点击访问GitHub")  

```markdown
访问[GitHub](https://github.com)学习开源项目。
![图片描述](图片URL)
```
<!-- 1. 直接显示URL -->
`<https://github.com>`  
→ 效果： <https://github.com>

<!-- 2. 引用式链接（长链接优化） -->
[GitHub][1] 和 [GitLab][2]

[1]: https://github.com "GitHub官网"
[2]: https://gitlab.com "GitLab官网"

示例：

![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png "GitHub官网")
<!-- markdownlint-disable MD033 -->
<img
  src="https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png"
  alt="GitHub Logo"  
  title="GitHub官网"  
  width="100"  
  style="display: block; margin: 0 auto;" />

---

### 代码块

#### 多行代码

````markdown
```python
print("Hello")
```
````

---

### 引用

> 爱因斯坦理论：
> E=mc² 是质能方程的经典表述。
>> 霍金补充：
>> 该方程在黑洞研究中需考虑量子效应。
>>> 现代物理学家质疑：
>>> 但在量子引力领域可能存在修正。
---

### 代码块缩进

- 缩进 **4空格** 或 **1 Tab**  
- 或使用 ```` ``` ```` 包裹（无需缩进）

---

### 空格要求

- `#`、`-`、`1.` 等符号后必须加空格  
- 表格竖线 `|` 两侧建议加空格

---

### 转义字符

特殊符号用 `\` 转义，如 `\*`、`\#`

---

### 兼容性

不同编辑器对空行、缩进解析可能不同。

---

### 示例文档

#### 代码

```python
def hello():
    print("Markdown")
```

#### 表格

```markdown
| 功能 | 语法       |
|------|------------|
| 粗体 | `**text**` |
```

| 标题1 | 标题2 | 标题3 |
|-------|-------|-------|
| 内容1 | 内容2 | 内容3 |
| 内容4 | 内容5 | 内容6 |

| 左对齐 | 居中对齐 | 右对齐 |
|:-------|:-------:|-------:|
| 数据1  |  数据2  |  数据3 |
| 数据4  |  数据5  |  数据6 |

---

## 编程相关工具学习

### conda

```bash
conda create --name myenv
conda create -n myenv python=3.8
conda create -n wz1 python=3.10
# 这将创建一个名为 `myenv` 的环境，并安装 Python 3.10。
#-n 和 --name 是 Conda 中定义环境名称的参数，功能完全相同**。
conda activate myenv
# 激活名为 `myenv` 的环境。
conda env list
# 列出所有已创建的 Conda 环境。
conda remove --name myenv --all
# 删除名为 `myenv` 的环境及其所有包。
conda env export > environment.yml
# 将当前环境的配置导出到 `environment.yml` 文件中。
conda env create -f environment.yml
# 根据 `environment.yml` 文件创建环境。
```

### ***python***配置镜像源

临时使用镜像源在安装包时，可以通过 -i 参数指定镜像源。例如：

```bash
pip install package_name -i https://pypi.tuna.tsinghua.edu.cn/simple # 临时使用清华源
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple # 设置全局镜像源
pip config list  # 查看配置
pip config unset global.index-url  # 删除配置
pip install -r requirements.txt#  # 安装依赖包
```

### python外部库

#### 依赖管理工具***pipreqs***

```bash
# 安装 pipreqs
pip install pipreqs  # 在项目根目录下生成 requirements.txt
pipreqs ./
 # 强制覆盖现有的 requirements.txt 文件
pipreqs ./ --force
# 忽略某些目录（例如 venv 和 tests）
pipreqs ./ --ignore=venv,tests
# 生成不带版本的依赖列表
pipreqs ./ --no-pin
# 指定编码（例如 utf-8）
pipreqs ./ --encoding=utf-8
# 忽略指定目录（多个目录用逗号分隔）
pipreqs ./ --ignore=venv,tests  # 完整写法
pipreqs ./ -i venv,tests        # 简写形式
# - venv/.venv/env：虚拟环境  - tests/test：测试目录
```

### Git使用

1. 系统配置与初始化

    ```bash
    # 1. 安装Git和LFS
    sudo apt-get update && sudo apt-get install -y git git-lfs
    # 2. 全局配置（首次使用）
    git config --global user.name "121624wzzzzz"
    git config --global user.email "1216249110@qq.com"
    git config --global core.editor "code --wait"
    # 设置局部用户名/邮箱（覆盖全局配置）
    cd /path/to/your/project
    git config user.name "project-specific-name"
    git config user.email "project@example.com"
    # 3. SSH密钥配置
    ssh-keygen -t rsa -b 4096 -C "1216249110@qq.com"
    eval "$(ssh-agent -s)" && ssh-add ~/.ssh/id_rsa
    cat ~/.ssh/id_rsa.pub | xclip -sel clip  # 复制公钥
    # 替换为您的仓库地址
    git clone git@github.com:username/repository.git
    ```

2. 项目初始化与管理

    ```bash
    # 1. 克隆仓库
    git clone git@github.com:121624wzzzzz/teacher-rag.git
    cd teacher-rag

    # 2. LFS大文件管理
    git lfs install
    git lfs track "*.bin" "*.h5" "data/**" "models/*.pt"
    git add .gitattributes && git commit -m "chore: 配置LFS规则"
    ```

3. 分支策略与开发流程

    | **类型**       | **格式**                     | **示例**                     | **适用场景**                                                                 |
    |----------------|-----------------------------|-----------------------------|-----------------------------------------------------------------------------|
    | **功能开发**   | `feat/<功能描述>`           | `feat/user-auth`            | 新功能开发（如登录模块、支付接口）                                           |
    | **问题修复**   | `fix/<问题描述>`            | `fix/login-error`           | 修复 Bug（如接口报错、样式问题）                                             |
    | **文档更新**   | `docs/<修改范围>`           | `docs/quick-start`          | 更新 README、API 文档、注释等                                                |
    | **代码重构**   | `refactor/<模块名>`         | `refactor/payment-service`  | 代码重构（不改变功能逻辑）                                                   |
    | **测试相关**   | `test/<测试目标>`           | `test/user-regression`      | 添加单元测试、E2E 测试                                                       |
    | **样式调整**   | `style/<修改范围>`          | `style/dark-mode`           | CSS/UI 样式调整（不涉及功能逻辑）                                            |
    | **依赖更新**   | `chore/<依赖名>`            | `chore/update-react`        | 升级依赖版本、修改构建配置（如 webpack、CI）                                  |
    | **性能优化**   | `perf/<优化目标>`           | `perf/api-response`         | 性能优化（如缓存数据库查询优化）                                       |
    | **实验性功能** | `experiment/<功能名>`       | `experiment/ai-chat`        | 临时性实验分支（可能不会合并到主分支）                                       |
    | **发布准备**   | `release/<版本号>`          | `release/v1.2.0`            | 发布前的最终测试和准备（禁止直接开发代码）                                    |
    | **紧急热修复** | `hotfix/<问题描述>`         | `hotfix/security-patch`     | 生产环境紧急修复（从 `main` 分支创建，修复后直接合并回 `main` 和 `develop`） |

#### 标准操作流程

```bash
# 1. 基于最新main创建功能分支
git checkout main && git pull
git checkout -b feat/payment

# 2. 开发并提交
git add -p src/payment.js  # 选择性暂存
git commit -m "feat(payment): 增加支付宝支付"

# 3. 推送到远程
git push -u origin feat/payment

# 4. 代码审查后合并到main
git checkout main
git pull --rebase
git merge --no-ff feat/payment
git push origin main

# 5. 清理分支
git branch -d feat/payment
git push origin --delete feat/payment
```

#### 四、Git 全流程开发指南（优化版）

1. 系统初始化
  
  ```bash
  # ====================== 系统初始化 
  # 1. 安装Git和LFS（Linux）
  sudo apt-get update && sudo apt-get install -y git git-lfs

  # 2. 全局配置（首次使用必做）
  git config --global user.name "YourName"
  git config --global user.email "your@email.com"
  git config --global core.editor "code --wait"
  git config --global pull.rebase true  # 设置pull时自动rebase

  # 3. SSH密钥配置（免密推送）
  ssh-keygen -t rsa -b 4096 -C "your@email.com"
  ssh-keygen -t ed25519 -f ~/.ssh/id_ed25519
  eval "$(ssh-agent -s)" && ssh-add ~/.ssh/id_rsa #&&如果前一条命令成功（返回 0）
  #则执行下一条/默认私钥（id_rsa）添加到 SSH 代理，后续无需重复输入密码
  cat ~/.ssh/id_rsa.pub | clip  # Windows复制公钥,|管道接受前一条输出，clip复制
  # 将公钥添加到GitHub/GitLab的SSH Keys设置中

  # ====================== 项目初始化 ======================
  # 1. 克隆仓库（两种方式）
  git clone https://github.com/user/repo.git  # HTTPS方式
  git clone git@github.com:user/repo.git     # SSH方式（推荐）

  # 2. 初始化新项目（如果是全新项目）
  mkdir project && cd project
  git init
  git remote add origin git@github.com:user/repo.git

  # 3. 大文件管理（超过100MB的文件）
  git lfs install
  git lfs track "*.psd" "*.zip" "data/​**​"
  git add .gitattributes && git commit -m "chore: 配置LFS规则"


  # ====================== 分支管理 ======================
  # 1. 创建功能分支（带分类文件夹）
  git checkout -b feat/a  # 功能开发
  git checkout -b fix/login-error # Bug修复
  git checkout -b docs/api-update # 文档更新
  git push -u origin feat/a
  # 2. 查看分支信息
  git branch -avv  # 查看本地+远程分支及关联关系
  git log --oneline --graph --all  # 图形化查看提交历史

  # 3. 分支同步与清理
  git fetch --all -p  # 获取所有远程分支并清理已删除的
  git branch -d old-branch  # 删除已合并的分支
  git branch -D force-delete  # 强制删除未合并分支
  git push origin --delete remote-branch  # 删除远程分支


  # ====================== 日常开发流程 ======================
  # 1. 开发前同步（重要！）
  git checkout main
  git pull --rebase  # 使用rebase保持历史线性

  # 2. 提交代码（推荐交互式）
  git add -p  # 选择性暂存修改
  git commit -m "描述"  # 语义化提交

  # 3. 解决冲突（当pull/push时报错时）
  git mergetool  # 使用配置的比对工具解决
  git rebase --continue  # 解决后继续rebase

  # 4. 代码推送（首次需要-u参数）
  git push -u origin feat/user-auth  # 首次推送
  git push  # 后续推送（已建立关联）


  # ====================== 合并与发布 ======================
  # 1. 合并到主分支（推荐rebase方式）
  git checkout main
  git pull --rebase
  git checkout feat/user-auth
  git rebase main  # 变基到main最新提交
  git checkout main
  git merge --no-ff feat/user-auth  # 显式生成合并节点

  # 2. 打标签发布
  git tag -a v1.2.0 -m "Release version 1.2.0"
  git push origin --tags


  # ====================== 实用技巧 ======================
  # 1. 临时保存修改（当需要切换分支时）
  git stash save "WIP: 登录功能开发中"
  git stash pop  # 恢复最近暂存
  ```

##### 配置***gitgnore***文件

| 符号 | 作用           | 示例          | 说明                      |
|------|----------------|---------------|---------------------------|
| `/`  | 路径分隔符     | `dir/file`    | 明确目录层级关系           |
| `#`  | 注释           | `# 忽略日志`  | 解释规则用途               |
| `*`  | 匹配0-N个字符  | `*.tmp`       | 忽略所有`.tmp`文件         |
| `?`  | 匹配1个字符    | `?.log`       | 匹配`a.log`不匹配`ab.log`  |
| `[]` | 字符范围       | `temp[0-9]`   | 匹配`temp0`到`temp9`       |

- 目录忽略

    ```gitignore
    /build/          # 仅忽略根目录build文件夹（匹配/build/file.txt，不匹配/src/build/）
    build/           # 忽略所有build目录（匹配/build/、/src/build/、/a/b/build/）
    src/*/temp/      # 忽略src下二级temp目录（匹配/src/a/temp/，不匹配/src/temp/）
    data/*           # 忽略data目录内容
    !data/.gitkeep      # 保留空目录标记文件
    ```

- 文件匹配

    ```gitignore
    *.bak            # 递归忽略所有.bak文件
    /README.md       # 仅忽略根目录README.md
    temp?.*          # 忽略temp1.txt等单字符文件名
    temp*.*        # 忽略tempabc.txt等任意字符文件名
    ```

- 特殊场景处理

    ```gitignore
    /vendor/*        # 忽略vendor目录内容
    !/vendor/important.txt  # 但保留指定文件

    logs/*           # 忽略logs内容
    !logs/important/  # 但保留子目录

    **/cache         # 全局匹配所有cache目录/文件
    ```

| 规则写法      | 匹配目标                     | 递归子目录 | 匹配类型       | 典型应用场景               | 注意事项                     |
|---------------|-----------------------------|------------|----------------|--------------------------|-----------------------------|
| `cache`       | 仅当前目录的 `cache`         | ❌ 否       | 文件或目录      | 临时忽略当前目录的缓存      | ​**​不会递归​**​匹配子目录        |
| `​**​/cache`    | 所有层级的 `cache`           | ✅ 是       | 文件或目录      | 彻底清除项目所有缓存        | 需要显式使用 `​**​/` 前缀       |
| `cache/`      | 所有层级的 `cache` ​**​目录​**​   | ✅ 是       | 仅目录          | 忽略缓存目录但保留同名文件  | 斜杠 `/` 后缀强制仅匹配目录    |

> 💡 ​**​使用提示​**​：  
>
> 1. 需要递归匹配时必须用 `​**​/` 前缀（纯名称不会自动递归）  
> 2. 目录匹配推荐用 `cache/` 写法（比 `​**​/cache/` 更简洁）  
> 3. 用 `git check-ignore -v` 验证实际匹配效果  

- 优先级与调试

1. 规则从上到下匹配，后写规则可覆盖前规则
2. 范围小的规则优先级更高（如`/build/` > `build/`）
3. 调试命令：

```bash
git check-ignore -v path/to/file  # 检查忽略原因
git status --ignored             # 查看所有被忽略
```

## Linux 常用命令

### 一、文件和目录操作（核心命令）

#### 1. `ls` - 列出目录内容

```bash
ls          # 简单列表
ls -l       # 详细列表（显示权限/所有者/大小/时间）
ls -a       # 显示隐藏文件（以.开头的文件）
ls -lh      # 人类可读的文件大小（KB/MB/GB）
ls -lt      # 按修改时间排序（最新在前）
ls -R       # 递归列出子目录内容
```

#### 2. `cd` - 切换目录

```bash
cd /path/to/dir  # 绝对路径切换
cd ..            # 返回上级目录
cd ~             # 返回用户主目录
cd -             # 返回上一个工作目录/后退
```

#### 3. `mkdir` - 创建目录

```bash
mkdir dirname              # 创建单个目录
mkdir -p parent/child      # 创建多级目录（自动创建父目录）
mkdir {dir1,dir2,dir3}     # 批量创建目录
```

#### 4. `rm` - 删除文件/目录

```bash
rm file.txt                # 删除文件
rm -i file.txt             # 交互式删除（确认提示）
rm -r dirname              # 递归删除目录
rm -rf dirname             # 强制删除（无确认，慎用！）
```

#### 5. `cp/mv` - 复制/移动文件

```bash
cp file.txt /backup/       # 复制文件
cp -r dir /backup/         # 递归复制目录
mv file.txt newname.txt    # 重命名
mv file.txt /target/       # 移动文件
```

---

### 二、文件查看与编辑

#### 1. 查看文件内容

```bash
cat file.txt        # 显示全部内容
less file.txt       # 分页查看（支持搜索：/keyword）
head -n 20 file.txt # 显示前20行
tail -f log.txt     # 实时追踪日志文件
```

#### 2. 文件编辑

```bash
nano file.txt       # 简单文本编辑器（Ctrl+O保存，Ctrl+X退出）
vim file.txt        # 高级编辑器（需掌握基本命令）
```

#### 3. 文件属性

```bash
stat file.txt       # 显示详细属性（大小/权限/时间戳）
file unknown.bin    # 检测文件类型
```

---

### 三、系统监控与管理

#### 1. 进程管理

```bash
top                 # 动态进程监控（按q退出）
htop                # 增强版top（需安装）
ps aux | grep nginx # 查找特定进程
kill -9 PID         # 强制终止进程
pkill -f "pattern"  # 按名称终止进程
```

#### 2. 磁盘与内存

```bash
df -h               # 查看磁盘使用情况（人类可读）
du -sh *            # 统计当前目录各文件/目录大小
free -h             # 查看内存使用情况
```

#### 3. 系统信息

```bash
uname -a            # 显示系统内核信息
uptime              # 系统运行时间与负载
lscpu               # CPU详细信息
lsblk               # 块设备信息（磁盘分区）
```

---

### 四、网络操作

#### 1. 网络诊断

```bash
ping google.com      # 测试网络连通性
traceroute google.com # 追踪网络路径
netstat -tulnp      # 查看开放端口
ss -tulnp           # 更现代的netstat替代
```

#### 2. 远程操作

```bash
ssh user@host -p 2222  # 指定端口连接
scp file.txt user@host:/path  # 安全复制文件
rsync -avz dir/ user@host:backup/ # 增量同步
```

---

### 五、权限管理

#### 1. 权限修改

```bash
chmod 755 script.sh  # 设置权限（所有者rwx，其他rx）
chmod +x script.sh   # 添加执行权限
chown user:group file.txt # 修改所有者/组
```

#### 2. 特殊权限

```bash
sudo command         # 以root权限执行
sudo su -            # 切换root用户（需谨慎）
visudo               # 安全编辑sudo配置
```

---

### 六、压缩与归档

#### **1. 基础压缩解压**

```bash
# 创建 .tar.gz 压缩包（最常用）
tar -czvf 压缩包名.tar.gz 要压缩的目录/

# 解压 .tar.gz 文件
tar -xzvf 压缩包名.tar.gz

# 创建 .zip 压缩包（兼容Windows）
zip -r 压缩包名.zip 要压缩的目录/

# 解压 .zip 文件
unzip 压缩包名.zip
```

#### **2. 实用进阶指令**

```bash
# 创建高压缩率的 .tar.bz2 包
tar -cjvf 压缩包名.tar.bz2 要压缩的目录/

# 查看压缩包内容（不解压）
tar -tzvf 压缩包名.tar.gz
unzip -l 压缩包名.zip

# 解压到指定目录
tar -xzvf 压缩包名.tar.gz -C 目标目录/
unzip 压缩包名.zip -d 目标目录/
```

#### **3. 参数速记表**

| 参数 | 作用                  | 记忆口诀       |
|------|-----------------------|---------------|
| `c`  | 创建压缩包            | **C**reate    |
| `x`  | 解压文件              | e**X**tract   |
| `z`  | 处理gzip格式          | **Z**ip       |
| `j`  | 处理bz2格式           | **J**umbo压缩 |
| `v`  | 显示操作过程          | **V**erbose   |
| `f`  | 指定文件名            | **F**ile      |

---

### 七、查找与过滤

#### 1. 文件查找

```bash
find / -name "*.log" -mtime +30 # 查找30天前的日志
find . -size +100M             # 查找大于100MB的文件
```

#### 2. 内容搜索

```bash
grep "error" *.log             # 在当前目录日志中搜索
grep -r "pattern" /path/       # 递归搜索目录
ack -i "keyword"               # 更友好的grep替代（需安装）
```

#### 3. 组合使用

```bash
ls -l | grep "Aug"             # 过滤8月修改的文件
ps aux | sort -nk4 | tail -5   # 显示内存使用最高的5个进程
```

---

### 八、实用技巧

#### 1. 命令组合

```bash
command1 && command2      # 前一个成功才执行后一个
command1 || command2      # 前一个失败才执行后一个
command1 ; command2       # 顺序执行
```

#### 2. 历史命令

```bash
history | grep "apt"      # 搜索历史命令
!42                       # 执行历史记录中第42条命令
Ctrl+R                    # 反向搜索历史命令
```

#### 3. 输出重定向

```bash
command > output.txt      # 标准输出重定向（覆盖）
command >> output.txt     # 追加输出
command 2> error.log      # 错误输出重定向
command &> all.log        # 所有输出重定向
```
