# python 100days study notes

## 数据结构类型

Python 中的基本数据类型主要包括以下几种：

1. 整型（`int`）：Python 中可以处理任意大小的整数，而且支持二进制（如`0b100`，换算成十进制是4）、八进制（如`0o100`，换算成十进制是64）、十进制（`100`）和十六进制（`0x100`，换算成十进制是256）的表示法。运行下面的代码，看看会输出什么。

    ```python
    print(0b100)  # 二进制整数
    print(0o100)  # 八进制整数
    print(100)    # 十进制整数
    print(0x100)  # 十六进制整数
    ```

2. 浮点型（`float`）：浮点数也就是小数，之所以称为浮点数，是因为按照科学记数法表示时，一个浮点数的小数点位置是可变的，浮点数除了数学写法（如`123.456`）之外还支持科学计数法（如`1.23456e2`，表示$\small{1.23456 \times 10^{2}}$）。运行下面的代码，看看会输出什么。

    ```python
    print(123.456)    # 数学写法
    print(1.23456e2)  # 科学计数法
    ```

3. 字符串型（`str`）：字符串是以单引号或双引号包裹起来的任意文本，比如`'hello'`和`"hello"`。

4. 布尔型（`bool`）：布尔型只有`True`、`False`两种值，要么是`True`，要么是`False`，可以用来表示现实世界中的“是”和“否”，命题的“真”和“假”，状况的“好”与“坏”，水平的“高”与“低”等等。如果一个变量的值只有两种状态，我们就可以使用布尔型。

## Python语言中的变量和运算符

| 运算符                                                       | 描述                           |
| ------------------------------------------------------------ | ------------------------------ |
| `[]`、`[:]`                                                 | 索引、切片                  |
| `**`                                                         | 幂                             |
| `~`、`+`、`-`                                              | 按位取反、正号、负号         |
| `*`、`/`、`%`、`//`                                       | 乘、除、模、整除            |
| `+`、`-`                                                    | 加、减                        |
| `>>`、`<<`                                                  | 右移、左移                    |
| `&`                                                          | 按位与                         |
| `^`、``                                                   | 按位异或、按位或              |
| `<=`、`<`、`>`、`>=`                                      | 小于等于、小于、大于、大于等于 |
| `==`、`!=`                                                   | 等于、不等于                  |
| `is`、`is not`                                               | 身份运算符                     |
| `in`、`not in`                                                | 成员运算符                     |
| `not`、`or`、`and`                                             | 逻辑运算符                     |
| `=`、`+=`、`-=`、`*=`、`/=`、`%=`、`//=`、`**=`、`&=`、`\|=`、`^=`、`>>=`、`<<=` | 赋值运算符             |

## 分支结构 (Branching Structures)

分支结构，也称选择结构，它允许程序根据一个或多个条件的真假来决定执行哪一段代码，从而让程序拥有“决策”能力，打破了代码自上而下的顺序执行。

最核心的分支结构由 `if`、`elif` (else if) 和 `else` 关键字构成。

- **`if`**: 必须的，作为分支的入口。如果条件为真，则执行其下的代码块。
- **`elif`**: 可选的，可以有多个。在前一个 `if` 或 `elif` 的条件为假时，检查当前 `elif` 的条件。
- **`else`**: 可选的，最多一个。在所有 `if` 和 `elif` 条件都为假时，执行其下的代码块。

在整个 `if...elif...else` 链条中，只有一个代码块会被执行。

**示例：`if-elif-else`**
下面是一个根据 BMI (身体质量指数) 判断身体状况的多分支示例。

```python
# BMI 计算器
height = float(input('身高(cm)：'))
weight = float(input('体重(kg)：'))
bmi = weight / (height / 100) ** 2
print(f'{bmi = :.1f}')

if bmi < 18.5:
    print('你的体重过轻！')
elif bmi < 24: # 只有在 bmi >= 18.5 时才会判断此条件
    print('你的身材很棒！')
elif bmi < 27: # 只有在 bmi >= 24 时才会判断此条件
    print('你的体重过重！')
else: # 如果以上所有条件都不满足 (即 bmi >= 27)
    print('你已属于肥胖范畴！')
```

Python 3.10 引入了 `match-case` 结构

- **`match`**: 指定要匹配的变量。
- **`case`**: 提供一个或多个匹配模式。
- **`|`**: 用于在一个 `case` 中合并多个值。
- **`_`**: 通配符，相当于 `else`，匹配任何其他情况。

**示例：`match-case`**
下面是使用 `match-case` 识别 HTTP 状态码的例子。

```python
# HTTP 状态码识别 (Python 3.10+)
status_code = 404

match status_code:
    case 200:
        description = 'OK'
    case 401 | 403 | 404: # 合并多个匹配项
        description = 'Not Allowed or Not Found'
    case 500:
        description = 'Server Error'
    case _: # 通配符，匹配所有其他情况
        description = 'Unknown Status Code'

print(f'{status_code}: {description}')
# 输出: 404: Not Allowed or Not Found
```

### 循环结构 (Looping Structures)

循环结构用于重复执行某段代码，直到满足某个退出条件。这极大地减少了代码的重复编写，让程序能处理重复性任务。Python 主要有两种循环结构：`for` 循环和 `while` 循环。

#### `for` 循环

`for` 循环通常用于**遍历一个可迭代对象**（如列表、字符串、元组）或**已知循环次数**的场景。它常与 `range()` 函数结合使用。

**示例：`for` 循环**
计算 1 到 100 之间所有偶数的和。

```python
# 计算 1-100 的偶数和
total = 0
# range(2, 101, 2) 生成从 2 开始，到 100 结束，步长为 2 的序列
for num in range(2, 101, 2):
    total += num

print(f'1到100的偶数和为: {total}') # 输出: 2550
```

#### `while` 循环

`while` 循环用于**当某个条件持续为真时**重复执行代码块，适用于循环次数不确定的场景。循环体内部必须有逻辑能改变循环条件，否则会陷入“死循环”。

**示例：`while` 循环**
猜数字游戏，用户不断猜测，直到猜对为止。

```python
import random

answer = random.randint(1, 100)
counter = 0

while True: # 这是一个“死循环”，需要内部 break 来退出
    counter += 1
    num = int(input('猜一个1到100的数字: '))
    
    if num < answer:
        print('猜小了，再大一点！')
    elif num > answer:
        print('猜大了，再小一点！')
    else:
        print('恭喜你，猜对了！')
        break # 猜对后，使用 break 退出循环

print(f'你一共猜了 {counter} 次。')
```

#### 循环控制 (`break` 和 `continue`)

- **`break`**: 立即**完全终止**当前所在的循环，执行循环之后的代码。
- **`continue`**: **跳过**本次循环中余下的代码，直接开始下一次循环迭代。

**示例：`break` 和 `continue`**

```python
# 打印1到10的数字，但跳过5，并且到8时提前停止
for i in range(1, 11):
    if i == 5:
        continue # 当 i 是 5 时，跳过本次循环的 print 语句
    if i == 8:
        break # 当 i 是 8 时，完全退出循环
    print(i, end=' ')

# 输出: 1 2 3 4 6 7 
```

#### 嵌套循环 (Nested Loops)

一个循环结构内部可以包含另一个循环结构。外层循环每执行一次，内层循环会完整地执行一遍。

**示例：嵌套循环**
打印一个 9x9 的乘法口诀表。

```python
# 打印九九乘法表
for i in range(1, 10):      # 外层循环控制行 (从1到9)
    for j in range(1, i + 1): # 内层循环控制列 (从1到当前行数i)
        print(f'{j}×{i}={i*j}', end='\t')
    print() # 每行结束后换行
```

---

## 数据结构

### 列表 (List)

列表 (list) 是 Python 中最基本和最常用的数据结构之一。它是一个**有序**、**可变**的数据序列，可以用来存储多个任意类型的元素。由于其可变性，我们可以随时向列表中添加、删除或修改元素。

#### 创建列表

创建列表主要有两种方式：

1.**使用 `[]` 字面量语法** (最常用)

```python
# 列表中可以包含不同类型的元素，也可以有重复元素
items1 = [35, 12, 99, 68, 55, 35, 87]
items2 = ['Python', 'Java', 'Go', 'Kotlin']
items3 = [100, 12.3, 'Python', True]
```

2.**使用 `list()` 构造器** 将其他可迭代对象转换为列表

```python
# 将 range 对象转换为列表
items4 = list(range(1, 10))  # [1, 2, 3, 4, 5, 6, 7, 8, 9]

# 将字符串转换为列表
items5 = list('hello')      # ['h', 'e', 'l', 'l', 'o']
```

#### 访问和切片

通过索引和切片可以访问列表中的一个或多个元素。

- **索引 (Indexing)**: 访问单个元素，索引从 0 开始。负数索引从 -1 开始，表示从末尾访问。
  ```python
  languages = ['Python', 'Java', 'Go', 'Kotlin']
  print(languages[0])   # 输出: Python
  print(languages[-1])  # 输出: Kotlin
  
  # 修改元素
  languages[2] = 'C++'
  print(languages)      # 输出: ['Python', 'Java', 'C++', 'Kotlin']
  ```
- **切片 (Slicing)**: 访问一个子列表，语法为 `[start:end:stride]`。
  ```python
  items = ['a', 'b', 'c', 'd', 'e', 'f']
  print(items[1:4])     # 输出: ['b', 'c', 'd'] (不包含索引4)
  print(items[:3])      # 输出: ['a', 'b', 'c'] (从头开始)
  print(items[3:])      # 输出: ['d', 'e', 'f'] (到末尾结束)
  print(items[::2])     # 输出: ['a', 'c', 'e'] (步长为2，即每隔一个取一个)
  print(items[::-1])    # 输出: ['f', 'e', 'd', 'c', 'b', 'a'] (反转列表)
  ```

#### 遍历列表

使用 `for` 循环可以逐个访问列表中的所有元素。

```python
languages = ['Python', 'Java', 'C++', 'Kotlin']
for lang in languages:
    print(lang)
```

#### 列表的常用方法

##### 1. **添加元素**
- **`append(element)`**: 在列表末尾添加一个元素。
- **`insert(index, element)`**: 在指定索引位置插入一个元素。

```python
languages = ['Python', 'Java']
languages.append('Go')      # ['Python', 'Java', 'Go']
languages.insert(1, 'SQL')  # ['Python', 'SQL', 'Java', 'Go']
```

##### 2. 删除元素
- **`remove(element)`**: 删除列表中第一个匹配的元素。如果元素不存在，会引发 `ValueError`。
- **`pop(index=-1)`**: 移除并返回指定索引的元素。如果未指定索引，则默认移除并返回最后一个元素。
- **`clear()`**: 清空列表中的所有元素。
- **`del` 关键字**: `del a_list[index]`，直接删除指定索引的元素。

```python
languages = ['Python', 'SQL', 'Java', 'Go', 'Java']
languages.remove('Java')  # 只删除第一个Java -> ['Python', 'SQL', 'Go', 'Java']
popped_item = languages.pop(1) # 移除'SQL'并返回 -> popped_item is 'SQL'
del languages[0] # 删除'Python'
languages.clear() # 列表变为空 []
```

##### 3. 查找与统计
- **`index(element)`**: 返回元素在列表中首次出现的索引。如果不存在，会引发 `ValueError`。
- **`count(element)`**: 返回指定元素在列表中出现的次数。

```python
items = ['Python', 'Java', 'Java', 'C++']
print(items.index('Java'))  # 输出: 1
print(items.count('Java'))  # 输出: 2
```

##### 4. 排序和反转
- **`sort(reverse=False)`**: 对列表进行**原地排序** (会修改原列表)。
- **`reverse()`**: 对列表进行**原地反转** (会修改原列表)。

```python
items = [3, 1, 4, 1, 5, 9, 2]
items.sort()           # items 变为 [1, 1, 2, 3, 4, 5, 9]
items.sort(reverse=True) # items 变为 [9, 5, 4, 3, 2, 1, 1]
items.reverse()        # items 变为 [1, 1, 2, 3, 4, 5, 9]
```

#### 列表生成式 (List Comprehension)

列表生成式提供了一种简洁、高效的方式来创建列表。它通常比传统的 `for` 循环加 `append` 方法性能更好。

**语法**: `[expression for item in iterable if condition]`

```python
# 创建 1-10 中所有偶数的平方列表
squares_of_evens = [x**2 for x in range(1, 11) if x % 2 == 0]
print(squares_of_evens)  # 输出: [4, 16, 36, 64, 100]
```

#### 嵌套列表

列表的元素也可以是列表，形成嵌套列表，常用于表示二维数据，如矩阵或表格。

```python
# 3x3 矩阵
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

# 访问元素
print(matrix[1][2]) # 输出: 6 (第2行第3列的元素)
```

好的，没问题。这是为你整理的关于 Python 字符串核心知识的 Markdown 笔记。

---

### 元组（Tuple）

元组（tuple）是 Python 中的另一种内置数据结构，它与列表类似，但有以下几个关键区别：

1. **不可变性**: 一旦创建，元组中的元素不能被修改、添加或删除。这使得元组在需要保护数据不被意外修改时非常有用。
2. **语法**: 元组使用圆括号 `()` 来定义，而列表使用方括号 `[]`。
3. **性能**: 由于元组是不可变的，它们通常比列表更快，尤其是在需要频繁访问元素时。
4. **哈希性**: 元组可以作为字典的键，而列表不能。
5. **存储效率**: 元组的内存占用通常比列表更小。
6. **语义**: 元组通常用于存储一组相关但不需要修改的数据，而列表则用于需要频繁修改的数据。
7. **单元素元组**: 创建单元素元组时，必须在元素后加逗号 `,`，否则会被解释为普通括号。

### 字符串 (String)

字符串 (string) 是由零个或多个字符组成的**有序**且**不可变**的序列。在 Python 中，它被广泛用于处理文本信息。由于其不可变性，对字符串的所有操作（如替换、拼接）都会返回一个**新的字符串对象**，而不会改变原始字符串。

#### 创建与表示

1.  **基本创建**: 使用单引号 `' '`、双引号 `" "` 或三引号 `''' '''` / `""" """` 包裹字符序列。三引号支持多行字符串。
    ```python
    s1 = 'hello, world!'
    s2 = "你好，世界！"
    s3 = '''这是一个
    多行字符串。'''
    ```
2.  **转义字符**: 使用反斜杠 `\` 来表示特殊含义的字符，如 `\n` (换行)、`\t` (制表符)、`\'` (单引号)、`\\` (反斜杠本身)。
    ```python
    print('it\'s a \\new\\ line.\nHello!')
    # 输出:
    # it's a \new\ line.
    # Hello!
    ```
3.  **原始字符串 (Raw String)**: 在字符串前加 `r` 或 `R`，字符串内的所有字符都按其字面意思解释，没有转义。常用于文件路径和正则表达式。
    ```python
    path = r'C:\Users\new'
    print(path) # 输出: C:\Users\new
    ```

#### 运算与操作

1.  **拼接与重复**: 使用 `+` 进行拼接，`*` 进行重复。
    ```python
    s1 = 'hello' + ' ' + 'world' # "hello world"
    s2 = 'go!' * 3               # "go!go!go!"
    ```
2.  **索引与切片**: 与列表类似，通过索引访问单个字符，通过切片获取子字符串。
    ```python
    s = 'python'
    print(s[0])    # 'p'
    print(s[-1])   # 'n'
    print(s[2:5])  # 'tho'
    print(s[::-1]) # 'nohtyp' (反转字符串)
    ```
3.  **成员运算**: 使用 `in` 和 `not in` 检查子字符串是否存在。
    ```python
    print('py' in 'python') # True
    ```
4.  **长度**: 使用 `len()` 函数获取字符串的字符数。
    ```python
    print(len('python')) # 6
    ```

#### 常用方法

字符串提供了大量内置方法来处理文本。

##### 1. 大小写转换
- `upper()`: 全部转为大写。
- `lower()`: 全部转为小写。
- `capitalize()`: 首字母大写，其余小写。
- `title()`: 每个单词的首字母大写。
```python
s = 'hello world'
print(s.upper())  # 'HELLO WORLD'
print(s.title())  # 'Hello World'
```

##### 2. 查找与定位
- `find(sub)`: 查找子串 `sub`，返回其首次出现的索引，未找到则返回 `-1`。
- `index(sub)`: 功能与 `find` 类似，但未找到时会引发 `ValueError`。
- `startswith(prefix)`: 检查字符串是否以 `prefix` 开头。
- `endswith(suffix)`: 检查字符串是否以 `suffix` 结尾。

```python
s = 'hello.world.txt'
print(s.find('world'))        # 6
print(s.startswith('hello'))  # True
print(s.endswith('.txt'))     # True
```

##### 3. 修剪与替换
- `strip()`: 去除字符串两端的空白字符（或指定字符）。`lstrip()` 和 `rstrip()` 分别处理左侧和右侧。
- `replace(old, new, count=-1)`: 将字符串中的 `old` 子串替换为 `new`。可选 `count` 参数指定最大替换次数。

```python
s1 = '  hello  '
print(s1.strip()) # 'hello'

s2 = 'hello, world'
print(s2.replace('l', 'L', 2)) # 'heLLo, world'
```

##### 4. 拆分与合并
- `split(sep=None)`: 将字符串按指定分隔符 `sep` 拆分成一个**列表**。若不指定 `sep`，则默认按所有空白字符拆分。
- `'sep'.join(iterable)`: 使用指定的字符串 `sep` 将一个可迭代对象（如列表）中的元素连接成一个新字符串。

```python
s = 'I-love-python'
word_list = s.split('-')  # ['I', 'love', 'python']
new_s = ' '.join(word_list) # 'I love python'
```

##### 5. 格式化字符串
创建包含变量的字符串有多种方式，f-string 是目前最推荐的方式。

- **f-string (格式化字符串字面量)**: 在字符串前加 `f`，用花括号 `{}` 包裹变量或表达式。
  ```python
  name = 'Alice'
  age = 30
  print(f'My name is {name} and I am {age} years old.')
  
  # 高级格式化
  pi = 3.14159
  print(f'The value of pi is approximately {pi:.2f}.') # '3.14'
  ```
- **`format()` 方法**:
  ```python
  print('My name is {} and I am {} years old.'.format(name, age))
  ```

##### 6. 编码与解码
计算机内部使用字节存储数据。字符串与字节串之间的转换通过编码和解码完成。

- **`encode(encoding='utf-8')`**: 将字符串编码为字节串 (`bytes`)。
- **`decode(encoding='utf-8')`**: 将字节串解码为字符串 (`str`)。

```python
s = '你好'
encoded_s = s.encode('utf-8') # b'\xe4\xbd\xa0\xe5\xa5\xbd'
decoded_s = encoded_s.decode('utf-8') # '你好'
```
> **注意**: 编码和解码时必须使用相同的编码格式（如 `utf-8`），否则会导致乱码或错误。

### 字典 (Dictionary)

字典 (dict) 是 Python 中极其重要和强大的数据结构。它是一个**无序**的、由**键-值 (key-value) 对**组成的**可变**集合。与列表和元组通过索引访问元素不同，字典通过唯一的**键 (key)** 来查找、添加或修改对应的**值 (value)**，这使得它在数据检索方面非常高效。

字典非常适合用来为真实世界的事物建模，将相关联的信息组织在一起。

#### 创建字典

1.  **使用 `{}` 字面量语法** (最常用)
    键和值用冒号 `:` 分隔，键值对之间用逗号 `,` 分隔。
    ```python
    # 用字典存储个人信息，键清晰地描述了值的含义
    person = {
        'name': '王大锤',
        'age': 55,
        'height': 168,
        'is_male': True,
        'address': '成都市武侯区科华北路62号'
    }
    ```
    > **注意**: 字典的**键**必须是**不可变类型**（如字符串、数字、元组），而**值**可以是**任意类型**（包括列表、甚至其他字典）。

2.  **使用 `dict()` 构造器**
    ```python
    # 方式一：使用关键字参数
    person = dict(name='王大锤', age=55, height=168)
    
    # 方式二：使用 zip() 函数压缩两个序列
    keys = ['A', 'B', 'C']
    values = [1, 2, 3]
    items = dict(zip(keys, values)) # {'A': 1, 'B': 2, 'C': 3}
    ```

3.  **使用字典生成式 (Dictionary Comprehension)**
    这是一种从可迭代对象快速创建字典的简洁语法。
    ```python
    # 创建一个数字及其平方的字典
    squares = {x: x**2 for x in range(1, 6)}
    # 输出: {1: 1, 2: 4, 3: 9, 4: 16, 5: 25}
    ```
4. **创建空字典**
    ```python
    empty_dict = {}
    ```

#### 访问、修改和添加

字典的操作核心是通过键来进行。

- **索引 (Indexing)**: 使用方括号 `[]` 和键来访问、修改或添加键值对。
  - **访问**: `dictionary[key]`。如果键不存在，会引发 `KeyError`。
  - **修改**: `dictionary[key] = new_value`。如果键已存在，其值会被更新。
  - **添加**: `dictionary[new_key] = value`。如果键不存在，会添加新的键值对。

```python
person = {'name': '王大锤', 'age': 55}

# 访问
print(person['name']) # 输出: 王大锤

# 修改
person['age'] = 25
print(person) # 输出: {'name': '王大锤', 'age': 25}

# 添加
person['tel'] = '13122334455'
print(person) # 输出: {'name': '王大锤', 'age': 25, 'tel': '13122334455'}

# 尝试访问不存在的键会报错
# print(person['gender']) # KeyError: 'gender'
```

#### 遍历字典

有多种方式可以遍历字典中的所有元素。

1. **遍历键 (Keys)**: 这是默认的遍历方式。

```python
for key in person:
    print(f'{key}: {person[key]}')
```

2. **遍历值 (Values)**: 使用 `.values()` 方法

```python
for value in person.values():
    print(value)
```

3. **遍历键值对 (Items)**: 使用 `.items()` 方法，这是最高效、最常用的方式。

```python
for key, value in person.items():
    print(f'{key}: {value}')
```

#### 字典的常用方法

##### 1. 安全获取

- **`get(key, default=None)`**: 安全地获取键对应的值。如果键不存在，返回 `default` 值（默认为 `None`），而不会报错。

```python
person = {'name': '王大锤', 'age': 25}
print(person.get('name'))    # '王大锤'
print(person.get('gender'))  # None (不会报错)
print(person.get('gender', '未知')) # '未知' (提供了默认值)
```

##### 2.删除元素

- **`pop(key, default)`**: 移除指定键及其值，并返回该值。如果键不存在，若提供了 `default` 则返回 `default`，否则引发 `KeyError`。
- **`popitem()`**: (自Python 3.7起) 移除并返回最后一个插入的键值对（作为元组）。对于旧版本，则是随机移除。
- **`clear()`**: 清空字典中所有元素。
- **`del` 关键字**: `del dictionary[key]`，删除指定键值对。

```python
person = {'name': '王大锤', 'age': 25, 'tel': '13122334455'}
age = person.pop('age')  # age is 25
last_item = person.popitem() # last_item is ('tel', '13122334455')
del person['name']
person.clear() # person 变为 {}
```

##### 3.更新与合并

- **`update(other_dict)`**: 将 `other_dict` 中的键值对合并到当前字典。如果存在相同的键，则 `other_dict` 中的值会覆盖原有的值。
- **`|` 运算符** (Python 3.9+): `dict1 | dict2` 返回一个包含两者合并内容的新字典。`dict1 |= dict2` 会原地更新 `dict1`。

```python
d1 = {'a': 1, 'b': 2}
d2 = {'b': 3, 'c': 4}
d1.update(d2) # d1 变为 {'a': 1, 'b': 3, 'c': 4}

# 使用 | 运算符 (Python 3.9+)
d1 = {'a': 1, 'b': 2}
d3 = d1 | d2  # d3 is {'a': 1, 'b': 3, 'c': 4}, d1 不变
```

##### 4.视图对象 (Views)

- **`keys()`**: 返回一个包含所有键的视图对象。
- **`values()`**: 返回一个包含所有值的视图对象。
- **`items()`**: 返回一个包含所有键值对（元组）的视图对象

> 视图对象是动态的，当字典发生变化时，视图也会相应更新。

```python
person = {'name': '王大锤', 'age': 25}
print(person.keys())   # dict_keys(['name', 'age'])
print(person.values()) # dict_values(['王大锤', 25])
print(person.items())  # dict_items([('name', '王大锤'), ('age', 25)])
```

---

#### 常用函数

| `abs`   | 返回一个数的绝对值，例如：`abs(-1.3)`会返回`1.3`。           |
| `bin`   | 把一个整数转换成以`'0b'`开头的二进制字符串，例如：`bin(123)`会返回`'0b1111011'`。 |
| `chr`   | 将Unicode编码转换成对应的字符，例如：`chr(8364)`会返回`'€'`。 |
| `hex`   | 将一个整数转换成以`'0x'`开头的十六进制字符串，例如：`hex(123)`会返回`'0x7b'`。 |
| `input` | 从输入中读取一行，返回读到的字符串。                         |
| `len`   | 获取字符串、列表等的长度。                                   |
| `max`   | 返回多个参数或一个可迭代对象中的最大值，例如：`max(12, 95, 37)`会返回`95`。 |
| `min`   | 返回多个参数或一个可迭代对象中的最小值，例如：`min(12, 95, 37)`会返回`12`。 |
| `oct`   | 把一个整数转换成以`'0o'`开头的八进制字符串，例如：`oct(123)`会返回`'0o173'`。 |
| `open`  | 打开一个文件并返回文件对象。                                 |
| `ord`   | 将字符转换成对应的Unicode编码，例如：`ord('€')`会返回`8364`。 |
| `pow`   | 求幂运算，例如：`pow(2, 3)`会返回`8`；`pow(2, 0.5)`会返回`1.4142135623730951`。 |
| `print` | 打印输出。                                                   |
| `range` | 构造一个范围序列，例如：`range(100)`会产生`0`到`99`的整数序列。 |
| `round` | 按照指定的精度对数值进行四舍五入，例如：`round(1.23456, 4)`会返回`1.2346`。 |
| `sum`   | 对一个序列中的项从左到右进行求和运算，例如：`sum(range(1, 101))`会返回`5050`。 |
| `type`  | 返回对象的类型，例如：`type(10)`会返回`int`；而` type('hello')`会返回`str`。 |
