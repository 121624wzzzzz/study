以下是整理好的命令块，每个命令块后都有注释说明其作用，使用 Markdown 格式呈现：

---

### **1. `pipreqs` 命令**
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

---

### **2. Git 连接 GitHub 命令**
```bash
# 安装 Git（Linux）
sudo apt-get install git

# 安装 Git（macOS，使用 Homebrew）
brew install git

# 配置 Git 用户名
git config --global user.name "Your Name"

# 配置 Git 邮箱
git config --global user.email "your.email@example.com"

# 生成 SSH 密钥
ssh-keygen -t rsa -b 4096 -C "your.email@example.com"

# 将 SSH 密钥添加到 SSH 代理
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa

# 复制 SSH 公钥（添加到 GitHub）
cat ~/.ssh/id_rsa.pub

# 克隆仓库（使用 HTTPS）
git clone https://github.com/username/repository.git

# 克隆仓库（使用 SSH）
git clone git@github.com:username/repository.git

# 查看 Git 状态
git status

# 添加文件到暂存区
git add filename

# 添加所有文件到暂存区
git add .

# 提交更改
git commit -m "Your commit message"

# 推送更改到远程仓库
git push origin branch-name

# 拉取远程仓库的更改
git pull origin branch-name

# 创建新分支
git branch new-branch

# 切换分支
git checkout branch-name

# 合并分支
git merge branch-name
```

---

### **3. 下载和安装依赖的命令**
```bash
# 使用 pip 安装 requirements.txt 中的依赖
pip install -r requirements.txt

# 下载依赖包到本地目录（不安装）
pip download -r requirements.txt

# 下载并构建依赖包为 .whl 文件
pip wheel -r requirements.txt

# 离线安装本地目录中的依赖包
pip install --no-index --find-links=. -r requirements.txt
```

---

### **4. Conda 相关命令**
```bash
# 创建新的 Conda 环境
conda create --name myenv python=3.x

# 激活 Conda 环境
conda activate myenv

# 导出 Conda 环境配置
conda env export > environment.yml

# 从 environment.yml 创建环境
conda env create -f environment.yml

# 清理 Conda 缓存
conda clean --all
```

---

### **5. Poetry 相关命令**
```bash
# 安装 Poetry
pip install poetry

# 初始化 Poetry 项目
poetry init

# 添加依赖
poetry add package_name

# 安装依赖
poetry install

# 导出 requirements.txt
poetry export -f requirements.txt --output requirements.txt
```

---

### **6. Pipenv 相关命令**
```bash
# 安装 Pipenv
pip install pipenv

# 初始化 Pipenv 项目
pipenv install

# 添加依赖
pipenv install package_name

# 生成 requirements.txt
pipenv lock -r > requirements.txt
```

---

###