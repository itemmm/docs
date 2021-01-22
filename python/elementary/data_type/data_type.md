## 字符串
字符串是 Python 中最常用的数据类型，可以使用引号('或")来创建字符串。
创建字符串很简单，只要为变量分配一个值即可。例如：
```python
str1 = "hello world!"
str2 = "hello python!"
```

> 字符串拼接
```python
str1 = "hello "
str2 = "world!"
print(str1 + str2)
```
执行结果为
```
>>> hello world!
```

> 字符串截取
可以使用方括号来截取字符串
```python
str1 = "hello world!"
str2 = str1[0]
str3 = str1[1:5]
print(str2)
print(str3)
```
执行结果为
```
>>> h
>>> ello
```

> 转义字符

转义字符|描述
--|:--
\\(在行尾时)|续行符
\\\\|反斜杠符
\\'|单引号
\\"|双引号
\\a|响铃
\\b|退格(Backspace)
\\e|转义
\\000|空
\\n|换行
\\v|纵向制表符
\\t|横向制表符
\\r|回车
\\f|换页
\\oyy|八进制数，y 代表 0~7 的字符，例如：\\012 代表换行。
\\xyy|十六进制数，以 \\x 开头，yy代表的字符，例如：\\x0a代表换行
\\other|其它的字符以普通格式输出

> 运算符

操作符|描述
--|:--
+|字符串连接
*|重复输出字符串
[]|通过索引获取字符串中字符
[:]|截取字符串中的一部分
in|成员运算符 - 如果字符串中包含给定的字符返回 True
not in|成员运算符 - 如果字符串中不包含给定的字符返回 True
r/R|原始字符串 - 原始字符串：所有的字符串都是直接按照字面的意思来使用，没有转义特殊或不能打印的字符。 原始字符串除在字符串的第一个引号前加上字母"r"（可以大小写）以外，与普通字符串有着几乎完全相同的语法。
%|格式字符串


## 列表
创建一个列表，只要把逗号分隔的不同数据项使用方括号括起来即可。例如：
```python
list1 = ["hello", "world"]
list2 = ["hello", "python"]
```
与字符串的索引一样，列表的索引从0开始。列表可以截取和组合等。

> 添加元素

`append()`

在列表最后添加元素

`insert()`

在列表指定位置添加元素

> 删除元素

`del`

根据索引值删除元素

```python
# del 删除列表中的单个元素，index为元素索引
del listname[index]

# del 删除中间一段连续的元素，start为开始索引，end为结束索引，删除的元素中包含start，不包含end
del listname[start:end]
```

`pop()`

根据索引值删除元素

```python
# 删除列表指定索引的元素，如果没有index，默认删除列表中最后一个元素
listname.pop(index)
```

`remove()`

根据元素值删除元素，该方法只会删除第一个和指定值相同的元素，而且必须保证该元素存在，否则会引发 ValueError 错误
```python
list1 = ["hello", "world", "python"]
list1.remove("world")
print(list1)
list1.remove("hello")
print(list1)
```
执行结果为
```
>>> ["hello", "python"]
>>> ["python"]
```

`clear()`

删除列表所有元素
```python
list1 = ["hello", "world", "python"]
list1.clear()
print(list1)
```
执行结果为
```
>>> []
```

## 元组
和列表类似，元组也是由一系列按特定顺序排序的元素组成。
元组和列表的不同之处：
- 列表的元素是可以更改的，包括修改元素值、删除元素和插入元素，所以列表是可变的
- 元组一旦被创建，它的元素就不可更改了，所以元组是不可变的

> 创建元组

需要注意一点，当创建的元组中只有一个字符串类型的元素时，该元素后面必须要追加一个`,`，否则会被视为字符串
```python
tuple1 = ("hello", "world", "python")
```


## 字典
使用键-值（key-value）存储，具有极快的查找速度

字典相当于保存了两组数据，其中一组是关键数据，被称为`key`，另一组数据可以通过`key`来访问，被称为`value`

**由于字典中的`key`是非常关键的数据，而且程序需要通过`key`，来访问`value`，因此字典中的`key`不允许重复**

程序既可使用花括号语法来创建字典，也可使用`dict()`函数来创建字典

在使用花括号语法创建字典时，花括号中应包含多个键值对，`key`与`value`之间用英文冒号隔开，多个键值对之间用英文逗号隔开，例如：

```python
dict1 = {"key1": "value1", "key2": "value2"}
```
**需要指出的是，元组可以作为`dict`的`key`，但列表不能作为`dict`的`key`，这是由于`dict`要求`key`必须是不可变类型，由于列表是可变的，因此列表不能作为`dict`的`key`**

在使用`dict()`函数创建字典时，可以传入多个列表或元组参数作为键值对，每个列表或元组将被当成一个键值对，因此这些列表或元组都只能包含两个元素，例如：

```python
list1 = [("key1", "value1"), ("key2", "value2"), ("key3", "value3")]
dict1 = dict(list1)
print(dict1)

list2 = [["key4", "value4"], ["key5", "value5"], ["key6", "value6"]]
dict2 = dict(list2)
print(dict2)
```
执行结果为
```
>>> {"key1": "value1", "key2": "value2", "key3": "value3"}
>>> {"key4": "value4", "key5": "value5", "key6": "value6"}
```

如果不为`dict()`函数传入任何参数，则代表创建一个空字典，例如：
```python
dict1 = dict()
print(dict1)
```
执行结果为
```
>>> {}
```

还可通过为`dict()`指定关键参数创建字典，此时字典的`key`不允许使用表达式，例如：
```python
dict1 = dict(key1="value1", key2="value2")
print(dict1)
```
执行结果为
```
>>> {"key1": "value1", "key2": "value2"}
```

> 通过`key`访问`value`

使用方括号语法访问不存在的`key`时，字典会引发`KeyError`错误

使用`get()`方法访问不存在的`key`，该方法会简单的返回`None`，不会导致错误

```python
dict1 = {"key1": "value1", "key2": "value2"}
print(dict1["key1"])
print(dict1.get("key1"))
print(dict1.get("key3"))
```
执行结果为
```
>>> value1
>>> value1
>>> None
```

> 通过`key`添加键值对

只需为不存在的`key`赋值即可

```python
dict1 = {"key1": "value1"}
dict1["key2"] = "value2"
print(dict1)
```
执行结果为
```
>>> {"key1": "value1", "key2": "value2"}
```

> 通过`key`删除键值对

可使用`del`

```python
dict1 = {"key1": "value1", "key2": "value2"}
del dict1["key2"]
print(dict1)
```
执行结果为
```
>>> {"key1": "value1"}
```

> 通过`key`修改键值对

只需对字典中存在的`key`赋值，新赋的值会覆盖原有的值
```python
dict1 = {"key1": "value1"}
dict1["key1"] = "value2"
print(dict1)
```
执行结果为
```
>>> {"key1": "value2"}
```

> 通过`key`判断指定键值对是否存在

如果要判断字典是否包含指定的`key`，则可以使用`in`或`not in`运算符，需要指出的是，对于字典而言，`in`或`not in`运算符都是基于`key`来判断的，例如：
```python
dict1 = {"key1": "value1", "key2": "value2"}
print("key1" in dict1)
print("key1" not in dict1)
print("key3" in dict1)
print("key3" not in dict1)
```
执行结果为
```
>>> True
>>> False
>>> False
>>> True
```

## 数据转换