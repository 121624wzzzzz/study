### 多行代码块详解

多行代码块是 Markdown 中用于展示**多行代码**的语法结构，与单行代码片段形成对比。以下是完整说明：

---

#### 一、基础语法
````markdown
```语言名称
第一行代码
第二行代码
...
```
````
• 必须用 **三个反引号** ``` 包裹
- 首行指定语言（如 `python`/`bash`/`javascript`）
- 代码块独立成段，前后需空行（部分解析器要求）

---

#### 二、对比单行代码
| 类型       | 语法                | 用途               | 示例                  |
|------------|---------------------|--------------------|-----------------------|
| 单行代码   | `` `代码` ``        | 文中短代码         | 调用`print()`函数     |
| 多行代码块 | ```语言\n代码\n```  | 完整代码段         | 函数/类/脚本的展示    |

---

#### 三、使用示例
##### 1. Python 代码块
````markdown
```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)
```
````
效果：
```python
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)
```

##### 2. Shell 命令块
````markdown
```bash
#!/bin/bash
echo "当前目录："
pwd
```
````
效果：
```bash
#!/bin/bash
echo "当前目录："
pwd
```

---

#### 四、高级特性
1. **显示行号**（GitHub/VSCode 支持）
   ````markdown
   ```python linenums="1"
   def hello():
       print("Hello")  # 第2行
   ```
   ````
   ```python 
   def hello():
       print("Hello")  # 第2行
   ```
2. **代码高亮行**（GitHub 支持）
   ````markdown
   ```python hl_lines="2 3"
   def test():
       x = 1
       y = 2
       return x + y
   ```
   ````

   ```python 
   def test():
       x = 1
       y = 2
       return x + y
       
3. **混合其他语法**
   ````markdown
   > 使用示例：
   > ```javascript
   > console.log('Markdown 代码块');
   > ```
   ````

---

#### 五、注意事项
1. **语言标识大小写敏感**
   - ✅ 正确：```python
   • ❌ 错误：```Python

2. **闭合标记独立成行**
   ```markdown
   <!-- 错误示例 -->
   ```python print("错误") ```

   <!-- 正确示例 -->
   ```python
   print("正确")
   ```
   ```

3. **嵌套代码块需转义**
   ````markdown
   ````
   ```text
   这是外层代码块
   ```
   ````

---

#### 六、主流平台支持
| 平台       | 行号支持 | 高亮行 | 语言数量 |
|------------|----------|--------|----------|
| GitHub     | ✅        | ✅      | 300+     |
| GitLab     | ✅        | ❌      | 200+     |
| VS Code    | ✅        | ✅      | 150+     |
| 微信公众号 | ❌        | ❌      | 10+      |

---

> **最佳实践建议**：  
> 1. 始终指定语言以获得最佳高亮效果  
> 2. 复杂代码建议添加行号便于讨论  
> 3. 在文档中用注释说明关键代码段