<!-- markdownlint-disable MD033 -->
# 学习

## vscode常用插件

## ***Markdown*** 语法指南

### 标题分级

```markdown
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
```

---

### html操作

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

### 空格需求

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

| 标题1 | 标题2 | 标题3 |
|-------|-------|-------|
| 内容1 | 内容2 | 内容3 |
| 内容4 | 内容5 | 内容6 |

| 左对齐 | 居中对齐 | 右对齐 |
|:-------|:-------:|-------:|
| 数据1  |  数据2  |  数据3 |
| 数据4  |  数据5  |  数据6 |

---
