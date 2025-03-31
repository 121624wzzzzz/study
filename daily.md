# 学习

## Markdown 语法指南

### 标题分级

```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
```

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

### 列表

#### 无序列表

```markdown
- 项目1
  - 子项目（缩进2空格）
```

#### 有序列表

```markdown
1. 第一项
   1. 子项（缩进3空格）
```

---

### 链接与图片

```markdown
[链接文本](URL)  
访问[GitHub](https://github.com)学习开源项目。
![图片描述](图片URL)
```

示例：

![GitHub Logo](https://github.githubassets.com/images/modules/logos_page/GitHub-Mark.png)

---

### 代码块

#### 行内代码

```markdown
`代码`
```

#### 多行代码

````markdown
```python
print("Hello")
```
````

---

### 引用

```markdown
> 引用内容
>> 嵌套引用
```

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

| 功能 | 语法       |
|------|------------|
| 粗体 | **text**   |

---

## 编程学习

### conda

```bash
conda create --name myenv
conda create --name wz1 python=3.10
# 这将创建一个名为 `myenv` 的环境，并安装 Python 3.10。
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

### 配置镜像源

临时使用镜像源在安装包时，可以通过 -i 参数指定镜像源。例如：

```bash
pip install package_name -i https://pypi.tuna.tsinghua.edu.cn/simple
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip config list  
pip install -r requirements.txt
```

### python库

#### pipreqs

```bash
# 安装 pipreqs
pip install pipreqs
# 在项目根目录下生成 requirements.txt
pipreqs ./
# 强制覆盖现有的 requirements.txt 文件
pipreqs ./ --force
# 忽略某些目录（例如 venv 和 tests）
pipreqs ./ --ignore=venv,tests
# 生成不带版本的依赖列表
pipreqs ./ --no-pin
# 指定编码（例如 utf-8）
pipreqs ./ --encoding=utf-8
```

### Git使用

```bash
# 1. 系统级配置
# 安装 Git 和 LFS（Linux）
sudo apt-get update && sudo apt-get install -y git git-lfs

# 配置全局用户信息（一次设置即可）
git config --global user.name "121624wzzzzz"
git config --global user.email "1216249110@qq.com"
git config --global --add safe.directory /your/project/path  # 解决权限问题

# 生成 SSH 密钥（推荐替代 HTTPS）
ssh-keygen -t rsa -b 4096 -C "your.email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub  # 复制后添加到 GitHub SSH Keys

# ======================
# 2. 项目初始化
# ======================
# 克隆仓库（推荐 SSH）
# 克隆您的仓库（使用 SSH 地址）
git clone git@github.com:121624wzzzzz/teacher-rag.git
cd teacher-rag

# 或初始化新项目后关联远程仓库
git init
git remote add origin git@github.com:121624wzzzzz/teacher-rag.git


# 配置 LFS（大文件支持）
git lfs install
git lfs track "*.bin" "*.h5" "data/**" #指定跟踪的大文件类型
git add .gitattributes  # 必须单独提交 LFS 配置
git commit -m "Configure Git LFS"

# 3. 标准开发流程
# ======================
# 创建功能分支（推荐工作流）
git checkout -b feature-xxx

# 开发后提交
git add .
git commit -m "Add feature-xxx"

# 首次推送分支
git push -u origin feature-xxx  # -u 设置上游分支

# ======================
# 4. 代码合并
# ======================
# 更新本地主分支
git checkout master
git pull origin master

# 合并功能分支（推荐 rebase 避免污染历史）
git rebase master feature-xxx
git checkout master
git merge --no-ff feature-xxx  # --no-ff 保留合并记录
git push origin master

# 删除已合并分支
git branch -d feature-xxx
git push origin --delete feature-xxx

# ======================
# 5. 其他高频命令
# ======================
# 查看状态
git status

# 撤销工作区修改
git restore <file>

# 查看历史
git log --oneline --graph
```

完整流程

```bash
# 初始化本地仓库
git init
# 关联远程仓库（替换为你的仓库地址）
git remote add origin git@github.com:121624wzzzzz/teacher-rag.git
# 添加所有文件到暂存区
git add .
# 提交代码（必须写有意义的描述）
git commit -m "初始化项目：包含核心框架代码"
# 首次推送（默认分支可能是 main 或 master）
git push -u origin main
# 如果报错，尝试：
git push -u origin master
# 后续修改
# 查看当前修改状态（确认要提交的文件）
git status
# 添加修改文件（可指定具体文件）
git add 文件名  # 或 git add .
# 提交修改
git commit -m "修复登录接口的越界问题"
# 推送到远程
git push origin main
# 拉取远程最新代码（自动合并）
git pull origin main
# 如果存在冲突，会提示：
# CONFLICT (content): Merge conflict in 文件名
# 手动解决冲突后执行：
git add 冲突文件
git commit -m "解决合并冲突"

# 从主分支创建功能分支
git checkout -b feature-user-auth

# 开发完成后提交
git add .
git commit -m "实现JWT用户认证功能"

# 推送到远程（首次需要 -u）
git push -u origin feature-user-auth

```

## Linux 常用命令

### 文件和目录操作

```bash
ls
ls -l  # 详细列表
ls -a  # 包括隐藏文件
```

```bash
cd /path/to/directory
cd ..  # 返回上一级目录
cd ~   # 返回用户主目录
```

```bash
pwd
```

```bash
mkdir new_directory
```

```bash
rm file.txt
rm -r directory  # 递归删除目录
```

```bash
cp file.txt /path/to/destination
cp -r directory /path/to/destination  # 递归复制目录
```

```bash
mv file.txt /path/to/destination
mv old_name.txt new_name.txt  # 重命名文件
```

```bash
touch file.txt
```

### 文件查看和编辑

```bash
cat file.txt
```

```bash
less file.txt
```

```bash
head file.txt
head -n 10 file.txt  # 查看前10行
```

```bash
tail file.txt
tail -n 10 file.txt  # 查看最后10行
```

```bash
nano file.txt
```

```bash
vim file.txt
```

### 系统信息和管理

```bash
uname -a
```

```bash
top
```

```bash
ps aux
```

```bash
kill PID  # 终止指定PID的进程
kill -9 PID  # 强制终止
```

```bash
df -h
```

```bash
du -sh /path/to/directory
```

```bash
free -h
```

### 网络操作

```bash
ping google.com
```

```bash
ifconfig
```

```bash
ssh user@hostname
```

```bash
scp file.txt user@hostname:/path/to/destination
```

### 权限管理

```bash
chmod 755 file.txt
```

```bash
chown user:group file.txt
```

### 压缩和解压

```bash
tar -cvf archive.tar /path/to/directory  # 打包
tar -xvf archive.tar  # 解包
```

```bash
gzip file.txt
```

```bash
gunzip file.txt.gz
```

### 查找和搜索

```bash
find /path/to/directory -name "*.txt"
```

```bash
grep "search_term" file.txt
```
