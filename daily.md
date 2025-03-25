### 创建 Conda 环境

1. **创建新的 Conda 环境**：
   ```bash
   conda create --name myenv
   ```
   这将创建一个名为 `myenv` 的新环境。

2. **创建指定 Python 版本的环境**：
   ```bash
   conda create --name wz1 python=3.10
   ```
   这将创建一个名为 `myenv` 的环境，并安装 Python 3.8。

3. **激活环境**：
   ```bash
   conda activate myenv
   ```
   激活名为 `myenv` 的环境。

4. **安装包到指定环境**：
   ```bash
   conda install -n myenv numpy
   ```
   在 `myenv` 环境中安装 `numpy` 包。

5. **列出所有环境**：
   ```bash
   conda env list
   ```
   列出所有已创建的 Conda 环境。

6. **删除环境**：
   ```bash
   conda remove --name myenv --all
   ```
   删除名为 `myenv` 的环境及其所有包。

7. **导出环境配置**：
   ```bash
   conda env export > environment.yml
   ```
   将当前环境的配置导出到 `environment.yml` 文件中。

8. **从文件创建环境**：
   ```bash
   conda env create -f environment.yml
   ```
   根据 `environment.yml` 文件创建环境。
9. **从文件创建环境**：
   临时使用镜像源
在安装包时，可以通过 -i 参数指定镜像源。例如：
   ```bash
   pip install package_name -i https://pypi.tuna.tsinghua.edu.cn/simple
   pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
   pip config list
   pip install -r requirements.txt
   ```
10. **python命令**:
    ```bash
    安装 pipreqs
    pip install pipreqs

    在项目根目录下生成 requirements.txt
    pipreqs ./

    强制覆盖现有的 requirements.txt 文件
        pipreqs ./ --force

        忽略某些目录（例如 venv 和 tests）
        pipreqs ./ --ignore=venv,tests

        生成不带版本的依赖列表
        pipreqs ./ --no-pin

        指定编码（例如 utf-8）
        pipreqs ./ --encoding=utf-8
    ```
11. **Git 连接 GitHub 命令**:
    ```bash
    
    安装 Git（Linux）
    sudo apt-get install git

    安装 Git（macOS，使用 Homebrew）
    brew install git
    
    git init
    git config user.name "121624wzzzzz"
    git config user.email "1216249110@qq.com"
    git remote add origin https://github.com/121624wzzzzz/study.git
    配置 Git 用户名
    git config --global user.name "Your Name"

    配置 Git 邮箱
    git config --global user.email "your.email@example.com"

    生成 SSH 密钥
    ssh-keygen -t rsa -b 4096 -C "your.email@example.com"

    将 SSH 密钥添加到 SSH 代理
    eval "$(ssh-agent -s)"
    ssh-add ~/.ssh/id_rsa

    复制 SSH 公钥（添加到 GitHub）
    cat ~/.ssh/id_rsa.pub

    克隆仓库（使用 HTTPS）
    git clone https://github.com/username/repository.git

    克隆仓库（使用 SSH）
    git clone git@github.com:username/repository.git

    查看 Git 状态
    git status

    添加文件到暂存区
    git add filename

    添加所有文件到暂存区
    git add .

    提交更改
    git commit -m "Your commit message"

    推送更改到远程仓库
    git push origin branch-name

    拉取远程仓库的更改
    git pull origin branch-name

    # 创建新分支
    git branch new-branch

    切换分支
    git checkout branch-name

    合并分支
    git merge branch-name
    ```


### Linux 常用命令

1. **文件和目录操作**：
   • `ls`：列出目录内容
     ```bash
     ls
     ls -l  # 详细列表
     ls -a  # 包括隐藏文件
     ```
   • `cd`：切换目录
     ```bash
     cd /path/to/directory
     cd ..  # 返回上一级目录
     cd ~   # 返回用户主目录
     ```
   • `pwd`：显示当前目录
     ```bash
     pwd
     ```
   • `mkdir`：创建目录
     ```bash
     mkdir new_directory
     ```
   • `rm`：删除文件或目录
     ```bash
     rm file.txt
     rm -r directory  # 递归删除目录
     ```
   • `cp`：复制文件或目录
     ```bash
     cp file.txt /path/to/destination
     cp -r directory /path/to/destination  # 递归复制目录
     ```
   • `mv`：移动或重命名文件或目录
     ```bash
     mv file.txt /path/to/destination
     mv old_name.txt new_name.txt  # 重命名文件
     ```
   • `touch`：创建空文件或更新文件时间戳
     ```bash
     touch file.txt
     ```

2. **文件查看和编辑**：
   • `cat`：查看文件内容
     ```bash
     cat file.txt
     ```
   • `less`：分页查看文件内容
     ```bash
     less file.txt
     ```
   • `head`：查看文件开头部分
     ```bash
     head file.txt
     head -n 10 file.txt  # 查看前10行
     ```
   • `tail`：查看文件末尾部分
     ```bash
     tail file.txt
     tail -n 10 file.txt  # 查看最后10行
     ```
   • `nano`：简单的文本编辑器
     ```bash
     nano file.txt
     ```
   • `vim`：强大的文本编辑器
     ```bash
     vim file.txt
     ```

3. **系统信息和管理**：
   • `uname`：显示系统信息
     ```bash
     uname -a
     ```
   • `top`：实时显示系统进程
     ```bash
     top
     ```
   • `ps`：显示当前进程
     ```bash
     ps aux
     ```
   • `kill`：终止进程
     ```bash
     kill PID  # 终止指定PID的进程
     kill -9 PID  # 强制终止
     ```
   • `df`：显示磁盘使用情况
     ```bash
     df -h
     ```
   • `du`：显示目录或文件大小
     ```bash
     du -sh /path/to/directory
     ```
   • `free`：显示内存使用情况
     ```bash
     free -h
     ```

4. **网络操作**：
   • `ping`：测试网络连接
     ```bash
     ping google.com
     ```
   • `ifconfig`：显示网络接口信息
     ```bash
     ifconfig
     ```
   • `ssh`：远程登录
     ```bash
     ssh user@hostname
     ```
   • `scp`：安全复制文件
     ```bash
     scp file.txt user@hostname:/path/to/destination
     ```

5. **权限管理**：
   • `chmod`：修改文件权限
     ```bash
     chmod 755 file.txt
     ```
   • `chown`：修改文件所有者
     ```bash
     chown user:group file.txt
     ```

6. **压缩和解压**：
   • `tar`：打包和解包文件
     ```bash
     tar -cvf archive.tar /path/to/directory  # 打包
     tar -xvf archive.tar  # 解包
     ```
   • `gzip`：压缩文件
     ```bash
     gzip file.txt
     ```
   • `gunzip`：解压缩文件
     ```bash
     gunzip file.txt.gz
     ```

7. **查找和搜索**：
   • `find`：查找文件
     ```bash
     find /path/to/directory -name "*.txt"
     ```
   • `grep`：在文件中搜索文本
     ```bash
     grep "search_term" file.txt
     ```

这些命令涵盖了 Linux 系统中常用的操作，可以帮助你高效地管理文件、目录、进程和网络等。
