以下是对 Linux 常用命令的详细解析，包含使用场景、参数说明和实用技巧：

---

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
cd -             # 返回上一个工作目录
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

#### 1. 常用压缩
```bash
tar -czvf archive.tar.gz dir/  # 创建gzip压缩包
tar -xzvf archive.tar.gz       # 解压gzip包
zip -r archive.zip dir/        # 创建zip压缩包
unzip archive.zip              # 解压zip包
```

#### 2. 高级用法
```bash
tar -cjvf archive.tar.bz2 dir/  # 使用bzip2压缩
pigz -k file.tar               # 多线程压缩（需安装）
```

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

---

### 九、危险命令警示 ⚠️
```bash
rm -rf /                 # 强制删除根目录（系统毁灭！）
dd if=/dev/zero of=/dev/sda # 清空整个磁盘
:(){ :|:& };:            # fork炸弹（会导致系统崩溃）
```

> **最佳实践建议**：
> 1. 使用`-i`参数进行危险操作前确认
> 2. 重要文件先备份再操作
> 3. 生产环境慎用`sudo`和通配符（如`rm *`）

掌握这些命令后，您将能高效完成90%的Linux系统操作任务。建议在实际操作前，先在不重要的文件或测试环境中练习。