# Python 常用数据结构与函数详解

## 一、基本数据结构

### 1. 列表（List） - 有序可变序列
```python
my_list = [1, 2, 3, 4, 5]

# 常用方法
my_list.append(6)      # 在末尾添加元素: [1,2,3,4,5,6]
my_list.insert(0, 0)   # 在索引0处插入0: [0,1,2,3,4,5,6]
my_list.extend([7,8])  # 扩展多个元素: [0,1,2,3,4,5,6,7,8]
my_list.pop(2)         # 移除并返回索引2的元素 (3)
my_list.remove(0)      # 移除第一个值为0的元素
my_list.index(4)       # 返回4的索引 (3)
my_list.count(5)       # 统计5出现的次数 (1)
my_list.sort()         # 原地排序（升序）
my_list.reverse()      # 原地反转列表
my_list.clear()        # 清空列表
copy_list = my_list.copy()  # 浅拷贝
```

### 2. 元组（Tuple） - 有序不可变序列
```python
my_tuple = (1, 2, 3, 'a')

# 常用方法
my_tuple.index(2)      # 返回2的索引 (1)
my_tuple.count('a')    # 统计'a'出现的次数 (1)
# 不能修改元素
```

### 3. 字典（Dict） - 键值对映射
```python
my_dict = {'a': 1, 'b': 2, 'c': 3}

# 常用方法
my_dict['d'] = 4        # 添加新键值对
value = my_dict.get('b', 0)  # 获取键'b'的值，不存在返回0 (2)
keys = my_dict.keys()   # 返回键的视图: dict_keys(['a','b','c','d'])
values = my_dict.values() # 返回值的视图: dict_values([1,2,3,4])
items = my_dict.items() # 返回键值对的视图: dict_items([('a',1),('b',2)...])
my_dict.pop('a')        # 移除键'a'并返回值 (1)
my_dict.update({'e':5}) # 更新字典
'c' in my_dict          # 检查键是否存在 (True)
new_dict = my_dict.copy() # 浅拷贝
my_dict.clear()         # 清空字典
```

### 4. 集合（Set） - 唯一元素的无序集合
```python
my_set = {1, 2, 3, 4, 5}

# 常用方法
my_set.add(6)          # 添加元素: {1,2,3,4,5,6}
my_set.remove(3)       # 移除元素: {1,2,4,5,6} (不存在时报错)
my_set.discard(10)     # 移除元素 (不存在时无操作)
popped = my_set.pop()  # 随机移除并返回一个元素
my_set.update({7,8})   # 更新集合
set1 | set2            # 并集 (| 或 union())
set1 & set2            # 交集 (& 或 intersection())
set1 - set2            # 差集 (- 或 difference())
set1 ^ set2            # 对称差集 (^ 或 symmetric_difference())
```

### 5. 字符串（String） - 不可变字符序列
```python
s = " Hello, World! "

# 常用方法
s.lower()              # 转小写: " hello, world! "
s.upper()              # 转大写: " HELLO, WORLD! "
s.strip()              # 移除两侧空白: "Hello, World!"
s.split(',')           # 分割字符串: [' Hello', ' World! ']
s.replace('H', 'J')    # 替换字符: " Jello, World! "
s.startswith(' ')      # 判断开头: True
s.endswith('! ')       # 判断结尾: True
s.find('World')        # 查找子串索引: 7
s.count('l')           # 统计出现次数: 3
s.join(['a', 'b', 'c']) # 连接字符串: "a Hello, World! b Hello, World! c"
```

## 二、常用内置函数

### 1. enumerate() - 枚举迭代器
为可迭代对象添加索引计数器
```python
fruits = ['apple', 'banana', 'cherry']

for index, fruit in enumerate(fruits):
    print(f"{index}: {fruit}")
    
# 输出:
# 0: apple
# 1: banana
# 2: cherry

# 从指定索引开始
for i, fruit in enumerate(fruits, start=10):
    print(f"{i}: {fruit}")
```

### 2. sorted() - 排序函数
返回排序后的新列表（不改变原序列）
```python
numbers = [5, 2, 8, 1, 9]

# 基本排序
asc = sorted(numbers)   # 升序: [1, 2, 5, 8, 9]
desc = sorted(numbers, reverse=True)  # 降序: [9, 8, 5, 2, 1]

# 自定义排序
words = ["apple", "Banana", "cherry"]
sort_ignore_case = sorted(words, key=lambda x: x.lower())  # ['apple', 'Banana', 'cherry']
sort_by_length = sorted(words, key=len)  # 按长度排序: ['apple', 'cherry', 'Banana']
```

### 3. range() - 生成数字序列
```python
range(5)          # 0,1,2,3,4
range(1, 6)       # 1,2,3,4,5
range(0, 10, 2)   # 0,2,4,6,8

list(range(3))     # [0, 1, 2]
```

### 4. zip() - 并行迭代多个序列
```python
names = ['Alice', 'Bob', 'Charlie']
ages = [25, 30, 35]

# 并行迭代
for name, age in zip(names, ages):
    print(f"{name} is {age} years old")

# 创建字典
person_dict = dict(zip(names, ages))  # {'Alice': 25, 'Bob': 30, 'Charlie': 35}

# 解压缩
zipped = [('a', 1), ('b', 2), ('c', 3)]
letters, numbers = zip(*zipped)  # letters = ('a','b','c'), numbers = (1,2,3)
```

### 5. map() - 对序列应用函数
```python
numbers = [1, 2, 3, 4]

# 基本使用
squares = map(lambda x: x**2, numbers)  # [1, 4, 9, 16]

# 多个序列
result = map(lambda a, b: a + b, [1,2,3], [4,5,6])  # [5, 7, 9]
```

### 6. filter() - 过滤序列元素
```python
numbers = range(10)

# 过滤奇数
even_numbers = filter(lambda x: x % 2 == 0, numbers)  # [0, 2, 4, 6, 8]

# 过滤非数字字符
chars = ['a', '1', 'b', '2', 'c', '3']
digits = filter(str.isdigit, chars)  # ['1', '2', '3']
```

## 三、高级特性

### 1. 推导式（创建序列的简洁方法）
```python
# 列表推导式
squares = [x**2 for x in range(10)]  # [0,1,4,9,16,25,36,49,64,81]

# 字典推导式
square_dict = {x: x**2 for x in range(5)}  # {0:0, 1:1, 2:4, 3:9, 4:16}

# 集合推导式
unique_lengths = {len(word) for word in ['hello', 'world', 'python']}  # {5, 6}

# 条件过滤
even_squares = [x**2 for x in range(10) if x % 2 == 0]  # [0,4,16,36,64]
```

### 2. 切片操作（访问序列的子集）
```python
numbers = [0,1,2,3,4,5,6,7,8,9]

numbers[2:5]    # [2,3,4]（起始:结束索引）
numbers[:3]     # [0,1,2]（从头开始）
numbers[7:]     # [7,8,9]（到结尾）
numbers[::2]    # [0,2,4,6,8]（步长为2）
numbers[::-1]   # [9,8,7,6,5,4,3,2,1,0]（反转序列）
```

### 3. 运算符in - 成员检测
```python
3 in [1,2,3,4,5]   # True（检测列表中是否存在）
'a' in {'a':1}      # True（检测字典键是否存在）
```

### 4. 解包操作 - 解包序列元素
```python
first, *middle, last = [1,2,3,4,5]  # first=1, middle=[2,3,4], last=5
```

## 四、使用场景建议

| 需求                     | 推荐数据结构        |
|--------------------------|--------------------|
| 需要修改的序列           | 列表 (list)        |
| 不需要修改的序列         | 元组 (tuple)       |
| 键值对映射               | 字典 (dict)        |
| 唯一元素集合             | 集合 (set)         |
| 文本处理                 | 字符串 (str)       |
| 带索引的遍历             | enumerate()       |
| 创建排序副本             | sorted()          |
| 合并多个序列             | zip()             |
| 函数式编程（映射）       | map()             |
| 函数式编程（过滤）       | filter()          |
| 高效成员检测             | 集合/字典的in操作 |

掌握这些核心数据结构和方法能大大提高Python编程效率！实际开发中，建议根据具体场景灵活选择合适的数据结构和工具。