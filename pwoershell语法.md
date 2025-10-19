# PowerShell 常用命令速查表

### **文件和目录操作 (File & Directory)**

| 功能 | PowerShell 命令 | 常用别名 |
| :--- | :--- | :--- |
| 列出文件和目录 | `Get-ChildItem` | `ls`, `gci`, `dir` |
| 切换目录 | `Set-Location` | `cd`, `sl` |
| 获取当前路径 | `Get-Location` | `pwd`, `gl` |
| 创建新目录 | `New-Item -ItemType Directory` | `mkdir`, `md` |
| 创建新文件 | `New-Item -ItemType File` | `ni` |
| 获取文件内容 | `Get-Content` | `cat`, `gc`, `type` |
| 设置/覆盖文件内容 | `Set-Content` | `sc` |
| 追加内容到文件 | `Add-Content` | `ac` |
| 复制项目 | `Copy-Item` | `cp`, `cpi`, `copy` |
| 移动项目 | `Move-Item` | `mv`, `mi`, `move` |
| 删除项目 | `Remove-Item` | `rm`, `ri`, `del` |
| 重命名项目 | `Rename-Item` | `ren`, `rni` |
| 解析路径 | `Resolve-Path` | `rvpa` |
| 清理屏幕 | `Clear-Host` | `cls`, `clear` |

### **命令与帮助 (Command & Help)**

| 功能 | PowerShell 命令 | 常用别名 |
| :--- | :--- | :--- |
| 查找命令 | `Get-Command` | `gcm` |
| 获取命令帮助 | `Get-Help <命令>` | `help`, `man` |
| 查看命令示例 | `Get-Help <命令> -Examples` | |
| 在线查看帮助 | `Get-Help <命令> -Online` | |
| 查找别名 | `Get-Alias` | `gal` |
| 查找命令位置(类似which) | `(Get-Command <命令>).Source` | |

### **进程和服务 (Process & Service)**

| 功能 | PowerShell 命令 | 常用别名 |
| :--- | :--- | :--- |
| 列出进程 | `Get-Process` | `ps`, `gps` |
| 停止进程 | `Stop-Process` | `kill`, `spps` |
| 启动进程/程序 | `Start-Process` | `start`, `saps` |
| 获取服务 | `Get-Service` | `gsv` |
| 启动服务 | `Start-Service` | `sasv` |
| 停止服务 | `Stop-Service` | `spsv` |
| 重启服务 | `Restart-Service` | `rs` |

### **管道与对象操作 (Pipeline & Object)**

| 功能 | PowerShell 命令 | 常用别名 |
| :--- | :--- | :--- |
| 筛选对象 (过滤) | `Where-Object` | `where`, `?` |
| 选择对象属性 | `Select-Object` | `select` |
| 排序对象 | `Sort-Object` | `sort` |
| 遍历对象 | `ForEach-Object` | `foreach`, `%` |
| 分组对象 | `Group-Object` | `group` |
| 测量对象(计数/求和) | `Measure-Object` | `measure` |
| 导出为CSV | `Export-Csv` | `epcsv` |
| 导入CSV | `Import-Csv` | `ipcsv` |

### **网络 (Networking)**

| 功能 | PowerShell 命令 | 常用别名 |
| :--- | :--- | :--- |
| 测试网络连接 | `Test-Connection` | `ping`, `tcm` |
| 测试网络端口 | `Test-NetConnection` | `tnc` |
| 下载网页或文件 | `Invoke-WebRequest` | `iwr`, `curl`, `wget` |
| 调用REST API | `Invoke-RestMethod` | `irm` |

### **系统与历史 (System & History)**

| 功能 | PowerShell 命令 | 常用别名 |
| :--- | :--- | :--- |
| 获取日期 | `Get-Date` | `date` |
| 获取历史命令 | `Get-History` | `h`, `history` |
| 执行历史命令 | `Invoke-History` | `r` |
| 获取环境变量 | `Get-ChildItem Env:` | `ls env:` |
| 获取特定环境变量 | `$env:<变量名>` | |
| 获取Windows事件日志 | `Get-WinEvent` | |

---
**小提示:** 你可以使用 `Get-Alias <别名>` 来查找一个别名对应的原始 PowerShell 命令，例如 `Get-Alias ls`。
 nvidia-smi