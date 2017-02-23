title: 1.python基础
date: 2016-11-18 22:41:28
categories: python教程
tags:
  - python教程
---
  
# 1. 内置类型

## 1.1 [变量](http://opslinux.com/2016/11/20/1-1-1-%E5%8F%98%E9%87%8F/)

## 1.2 布尔

表示真假的类型，仅包含 True 和 False 两种取值

数字 0、None，以及元素为空的容器类对象都可视作 bool False，反之为 True。

```
>>> bool(0)
False

>>> bool(None)
False

>>> bool("")
False

>>> bool([])
False

>>> bool({})
False

>>> bool(1)
True

>>> bool([1,2])
True
```

bool类型支持的运算符


```
>>> a and b  # 如果 a 和 b 都是 True，结果就是 Ture ， 否则 False。
>>> a or b   #  a 和 b 至少有一个是 True 时结果是 True， 否则 False。
>>> not b    # 如果 a 是 False, 结果是 True， 如果 a 是 True，结果是 False。
```

## 1.3 数字
python本身支持整数以及浮点数。你可以对这些数字进行下表中的计算。

| 运算符 | 表述 | 示例 | 运算结果 |
| --- | --- | --- | :-- |
| + | 加法 | 1 + 1  | 2  |
| - | 减法 | 4 - 2 | 2 |
| * | 乘法 | 2 * 2 | 4 |
| / | 浮点数除法 | 7 / 2 | 3.5 |
| // | 整数除法 | 7 // 2 | 3 |
| / | 摸（求余） | 7 % 3 | 1 |
| ** | 幂 | 2 ** 2 | 4  |


### 整数

任何仅含数字的序列在 Python 中都被认为是整数：

```
>>> 5
5
```

Python还支持运算次序，因此你可在同一个表达式中使用多种运算。你还可以使用括号来修 改运算次序，让Python按你指定的次序执行运算，如下所示:

```python
>>> 2 + 3*4
14
>>> (2 + 3) * 4 20
```

在这些示例中，空格不影响Python计算表达式的方式，它们的存在旨在让你阅读代码时，能 迅速确定先执行哪些运算。

### 浮点数
Python将带小数点的数字都称为浮点数。大多数编程语言都使用了这个术语，它指出了这样一个事实:小数点可出现在数字的任何位置。每种编程语言都须细心设计，以妥善地处理浮点数， 确保不管小数点出现在什么位置，数字的行为都是正常的。

```python
>>> 0.1 + 0.1
0.2
>>> 0.2 + 0.2
0.4
>>>2 * 0.1
0.2
>>>2 * 0.2
0.4
```

但需要注意的是，结果包含的小数位数可能是不确定的:

```python
>>> 0.2 + 0.1 
0.30000000000000004 
>>> 3 * 0.1 
0.30000000000000004
```

所有语言都存在这种问题，没有什么可担心的。Python会尽力找到一种方式，以尽可能精确地表示结果，但鉴于计算机内部表示数字的方式，这在有些情况下很难。就现在而言，暂时忽略 多余的小数位数即可。







## 1.4 字符串

字符串是由多个字符组成的序列。在Python中，用引号括起的都是字符串，字符串定义简单自由，可以是单引号、双引号或者三引号。但是个人建议使用双引号表示字符串，用单引号表示字符，和其他语言习惯保持一致。字符串是不可变序列（immutable, sequence）类型，默认存储 Unicode 文本。 python3 不再使用 str 处理二进制字节数据，改为使用 bytes 和 bytearray，前者同为不可变类型。


```
>>> s = "abc汉字"
>>> >>> len(s)
5

>>> print(ascii(s))
'abc\u6c49\u5b57'
```

> 内置函数 ascii 将目标转换为可打印 ASCII 字符组成的字符串。

构建字符串字面量很容易，单引号、双引号，以及跨行的三个引号。


```
>> "ab'c"           # 双引号。
"ab'c"

>>> 'ab"c'          # 单引号。
'ab"c'

>>> 'ab\'c'         # 引号转义。
"ab'c"

>>> """             # 多行，也可以用三个单引号。
... a
... b
... c"""
'\na\nb\nc'

>>> "a" "b" 'c'     # 自动合并多个相邻字符串。
'abc'

```

可在字面量前添加特殊指示符。


```
>>> r"abc\nd"       # raw string，禁用转义。
'abc\\nd'

>>> type(b"abc")
<class 'bytes'>

>>> type(u"abc")
<class 'str'>
```

### str() 类型转换

```
>>> str(2.2)
'2.2'
```




### 合并字符串

#### format 

```
>>> "python培训哪家强：{}".format('京峰教育')
'python培训哪家强：京峰教育'
```

```
>>> "python培训哪家强：{}, 京峰教育谁最帅？ {}".format('京峰教育', '斌哥')
'python培训哪家强：京峰教育, 京峰教育谁最帅？ 斌哥'
```

```
>>> "python培训哪家强：{0}, 京峰教育谁最帅？ {1}".format('京峰教育', '斌哥')
'python培训哪家强：京峰教育, 京峰教育谁最帅？ 斌哥'
```

#### +

```
>>> '京峰' +  '教育'
'京峰教育'
```
  

### split() 分割

```
>>> s = 'a,b,c'

>>> s.split(',')
['a', 'b', 'c']
```
### join() 合并

```
>>> l = s.split(',')

>>> l
['a', 'b', 'c']

>>> ','.join(l)
'a,b,c'
```

### find 查找子串

查找到返回该子串在原字符串中的索引位置，如果无法找到，find方法会返回值-1

```
>>> s = "abc"
>>> s.find('a')
0
>>> s.find('d')
-1
>>>
```


## 1.5 [列表](http://opslinux.com/2016/11/20/1-1-2-%E5%88%97%E8%A1%A8/)
## 1.6 元组
与列表类似，元组也是由任意类型元素组成的序列。与列表不同的是，元组是不可改变的，这意味着一但元组被定义，将无法再进行增加、删除或者修改元素等操作。因此元组就像一个常量列表。从行为上看，元组（tuple）像是列表的只读版本。 但在内在实现上有根本不同，元组的只读性使其拥有更好的内存效率和性能。除无法修改外，其普通特征和列表类似。 在需要传递 “不可变” 参数时，应鼓励用元组替代列表。 它是可哈希（hashaable）结构，可用作字典（dict）主键（key）

### 使用()创建元组

可以用()创建一个空元组：

```
>>> empty_tuple = ()
>>> empty_tuple
()
>>> type(empty_tuple)
tuple
```

创建包含一个或多个元素的元组时，没一个元素后面需要跟着一个逗号，即使只包含一个元素也不能忽略：

```
>>> num = '1',
>>> num
('1',)
>>>
```

如果创建的元组所包含的元素数量超过1，最后一个元素后面的逗号可以忽略：


```
>>> num = '1', '2', '3'
>>> num
('1', '2', '3')
```
Python的交互式解释器输出元组时会自动添加一堆圆括号。你并不需要这么做——定义元组真正靠的是每个元素的后缀逗号——但如果你习惯添加一对括号也无可厚非。可以用括号将所有元素包裹起来，这会使得程序更加清晰：

```
>>> num = ('1', '2', '3')
>>> num
('1', '2', '3')
```

可以一口气将元组赋值给多个变量：


``` 
>>> a, b, c = num
>>> a
'1'
>>> b
'2'
>>> c
'3'
>>>       
```

这个过程称为元组解包

可以利用元组在一条语句中对多个变量的值进行交换，而不需借助临时变量：

```
>>> a = 1
>>> b = 2
>>> a, b = b, a
>>> a
2
>>> b
1
>>>
```

tuple() 函数可以用其他类型的数据来创建元组：

```
>>> num = [1, 2, 3]
>>> tuple(num)
(1, 2, 3)
>>>
```

### 元组与列表
在许多地方都可以用元组代替列表，但元组的方法函数与类表相比要少一些——元组没有 append() 、insert()，等等——因为一但创建元组变无法修改。既然列表更加灵活那为什么不在所有地方都是用列表呢？原因如下：

* 元组占用的空间小
* 你不会意外修改元组的值
* 可以将元组用作字典的键（详细的后面会介绍）
* 命名元组可以作为对象的代替
* 函数的参数是以元组形式是传递的

## 1.7 字典

### 使用 {} 创建字典

```
>>> empty_dict = {}
>>> empty_dict
{}
```

### 使用 dict() 转换为字典
可以用 dict() 将包含双值子序列的序列转换成字典。

```
>>> lol = [ ['a', 'b'], ['c', 'd'], ['e', 'f'] ]
>>> dict(lol)
{'a': 'b', 'c': 'd', 'e': 'f'}
```
> 记住，字典中元素的顺序是无关紧要的，实际存储顺序可能取决于你添加元素的顺序。

双值元组列表：

```
>>> lot = [ ('a', 'b'), ('c', 'd'), ('e', 'f') ]
>>> dict(lot)
{'a': 'b', 'c': 'd', 'e': 'f'}
```

双字符串的字符串组成的列表：

```
>>> los = [ 'ab', 'cd', 'ef' ]
>>> dict(los)
{'a': 'b', 'c': 'd', 'e': 'f'}
```

双字符的字符串组成的元组：

```
>>> tos = ( 'ab', 'cd', 'ef' )
>>> dict(tos)
{'a': 'b', 'c': 'd', 'e': 'f'}
```


### 使用 [key] 添加或修改元素

```
>>> d = {"l1":1, "l2":2, "l3":3}
>>> d["l4"] = 4
>>> d
{'l2': 2, 'l1': 1, 'l3': 3, 'l4': 4}
```

### 使用 update() 合并字典

```
>>> d = {"l1":1, "l2":2, "l3":3}
>>> d.update({"l4":4})
>>> d
{'l2': 2, 'l1': 1, 'l3': 3, 'l4': 4}
```

### 使用 del 删除具有指定键的元素

```
>>> d = {"l1":1, "l2":2, "l3":3}
>>> del d["l1"]
>>> d
{'l2': 2, 'l3': 3}
```

### 使用 clear() 删除所有元素

```
>>> d = {"l1":1, "l2":2, "l3":3}
>>> d.clear()
>>> d
{}
```

### 使用 in 判断是否存在
如果你希望判断某一个键是否存在于一个字典中，可以使用 in 。

```
>>> d = {"l1":1, "l2":2, "l3":3}
>>> d
{'l2': 2, 'l1': 1, 'l3': 3}
>>> 1 in d
False
>>> "l1" in d
True
>>> "l4" in d
False
>>>
```

### 使用 [key] 获取元素

```
>>> d = {"l1":1, "l2":2, "l3":3}
>>> d.keys()
dict_keys(['l2', 'l1', 'l3'])
```

### 使用 values() 获取所有值

```
>>> d = {"l1":1, "l2":2, "l3":3}
>>> list( d.values() )
[2, 1, 3]
```

### 使用 items() 获取所有键值对

```
>>> d = {"l1":1, "l2":2, "l3":3}
>>> list(d.items())
[('l2', 2), ('l1', 1), ('l3', 3)]
```

### 使用=赋值，使用copy()复制
与列表一样，对字典内容进行修改会反应到所有与之相关联的变量名上：

```
>>> d = {"l1":1, "l2":2, "l3":3}
>>> d2 = d
>>> d.update({"l4":4})
>>> d
{'l2': 2, 'l1': 1, 'l3': 3, 'l4': 4}
>>> d2
{'l2': 2, 'l1': 1, 'l3': 3, 'l4': 4}
>>>
```

若想避免这种情况，可以使用 copy() 将字典复制到一个新的字典中：

```
>>> d
{'l2': 2, 'l1': 1, 'l3': 3, 'l4': 4}
>>> d2
{'l2': 2, 'l1': 1, 'l3': 3, 'l4': 4}
>>> d = {"l1":1, "l2":2, "l3":3}
>>> d2 = d.copy()
>>> d.update({"l4":4})
>>> d2
{'l1': 1, 'l2': 2, 'l3': 3}
>>> d
{'l2': 2, 'l1': 1, 'l3': 3, 'l4': 4}
```



### 两个列表转换为字典

```
>>> l1 = [1,2,3]
>>> l2 = ["one", "two", "there"]
>>> zip(l1,l2)
<zip object at 0x1022f1588>
>>> dict(zip(l1,l2))
{1: 'one', 2: 'two', 3: 'there'}
```

## 1.8 集合

集合就像舍弃了值，仅剩下的字典一样。键与键之间也不允许重复。如果你仅仅想知道某一个元素是否存在而不关心其他的，使用集合是个非常好的选择。如果需要为键附加其他信息的话建议使用字典。


### 使用 set() 创建集合

可以使用set()函数创建一个集合，或者用大括号将一系列一都好分开的值包裹起来：

```
>>> empty_set = set()
>>> empty_set
set()
>>> num_set ={1,2,3,4,5}
>>> num_set
{1, 2, 3, 4, 5}
```

与字典一样，集合是无序的。

> {} 创建的是一个空字典，这仅仅是因为字典出现的比较早抢占了花括号。


### 使用set()将其他类型转换为集合

你可以利用已有的列表、字符串、元组或字典的内容来创建集合，其中重复的值会被丢弃。

首先来试着转换一个包含重复字母的字符串：

```
>>> set('letters')
{'l', 'r', 'e', 't', 's'}
```

注意，上面得到的集合中仅含有一个 'e' 和一个 't'，尽管字符串 'letters' 里各自包含两个。

再试试用列表建立集合：

```
>>> set(['one', 'two', 'three'])
{'one', 'two', 'three'}
```

再看下元组：

```
>>> set(('one', 'two', 'three'))
{'one', 'two', 'three'}
```

当字典作为参数传入set()函数时，只有键会被使用：

```
>>> set( {'apple': 'red', 'orange': 'orange', 'cherry': 'red'} )
{'cherry', 'orange', 'apple'}
```

### 使用in测试值是否存在

```
>>> num_set = {'one', 'two', 'three'}
>>> num_set
{'one', 'two', 'three'}
>>> 'one' in num_set
True
>>> 'four' in num_set
False
```

### 添加删除数据

```
>>> num_set = {'one', 'two', 'three'}
>>> num_set.add('four')
>>> num_set
{'one', 'two', 'four', 'three'}
>>> num_set.remove('one')
>>> num_set
{'two', 'four', 'three'}
```

### 交集和并集

set可以看成数学意义上的无序和无重复元素的集合，因此，两个set可以做数学意义上的交集、并集等操作：

```
>>> s1 = set([1, 2, 3])
>>> s2 = set([2, 3, 4])
>>> s1 & s2
set([2, 3])
>>> s1 | s2
set([1, 2, 3, 4])
```
  
## 比较数据结构

列表

元组

字典

集合
  
## 建立大型数据结构

我们从最简单的布尔型、数字、字符串开始学习，到目前为止，学习了列表、元组集合以及字典等数据结构，你可以将这些内置的数据结构自由地组合成更大、更复杂的结构。试着从建立上三个不同的列表开始：

```
>>> num = [1, 2, 3]
>>> name = ["l1", "l2", "l3", "l4", "l5"]
>>> englist = ["one", "two", "three"]
```
可以把上面每一个列表当做一个元素，并建立一个元组：

```
>>> tol = num, name, englist
>>> tol
([1, 2, 3], ['l1', 'l2', 'l3', 'l4', 'l5'], ['one', 'two', 'three'])
>>>
```
同样，可以创建一个包含上面三个列表的列表：

```
>>> lol = [num, name, englist]
>>> lol
[[1, 2, 3], ['l1', 'l2', 'l3', 'l4', 'l5'], ['one', 'two', 'three']]
```
还可以创建以这三个列表为值的字典：

```
>>> dol = {'num': num, 'name':name, 'englist':englist}
>>> dol
{'englist': ['one', 'two', 'three'], 'name': ['l1', 'l2', 'l3', 'l4', 'l5'], 'num': [1, 2, 3]}
>>>
```
在创建自定义数据结构的过程中，唯一的限制来自于这些内置数据本身。比如字典的键必须为不可变对象，因此列表、字典和集合都不能作为字典的键，但元组可以作为字典的键。举个例子，我们可以通过 GPS 坐标（纬度，经度，海拔）定位感兴趣的位置：

```
>>> houses = {
... (44.79, -93.14, 285): 'My House', 
(38.89, -77.03, 13): 'The White House' }
```


  
# 2. 代码格式

# 2.1. 注释
在大多数编程语言中，注释都是一项很有用的功能。随着程序越来越大、越来越复杂，就应在其中添加说明，对你解决问题的方法进行大致的阐述。注释让你能够使用自然语言在程序中添加说明。注释是程序中会被Python解释器忽略的一段文本。通过使用注释，可以解释和明确Python代码的功能，记录将来要修改的地方，甚至写下你想写的东西。在Python中使用#字符标记注释，从#开始到当前行结束的部分都是注释。你可以把注释作为单独一行：
  
单行注释：

hello.py

```
# 向大家问好
print("Hello Python people!")
```

Python解释器将忽略第一行，只执行第二行.

```
print("Hello Python people!")
```

多行注释：

```
#coding=utf-8

"""这是"nester.py"模块，提供了一个名为print_lol的函数，这个函数的作用是打印列表，其中有可能包含（也可能不包含）嵌套列表。"""
def print_lol(the_list):
    """这个函数取一个位置参数，名为"the_list",这个可以是任何python列表（也可以是包含嵌套列表的列表）。所指定的列表中的每个数据项（递归地）输出到屏幕上，各数据项各占一行。"""
    for each_item in the_list:
        if isinstance(each_item, list):
            print_lol(each_item)
        else:
            print(each_item)
```

**该编写什么样的注释?**
编写注释的主要目的是阐述代码要做什么，以及是如何做的。在开发项目期间，你对各个部分如何协同工作了如指掌，但过段时间后，有些细节你可能不记得了。当然，你总是可以通过研 究代码来确定各个部分的工作原理，但通过编写注释，以清晰的自然语言对解决方案进行概述， 可节省很多时间。要成为专业程序员或与其他程序员合作，就必须编写有意义的注释。当前，大多数软件都是合作编写的，编写者可能是同一家公司的多名员工，也可能是众多致力于同一个开源项目的人员。 训练有素的程序员都希望代码中包含注释，因此你最好从现在开始就在程序中添加描述性注释。 作为新手，最值得养成的习惯之一是，在代码中编写清晰、简洁的注释。如果不确定是否要编写注释，就问问自己，找到合理的解决方案前，是否考虑了多个解决方案。如果答案是肯定的，就编写注释对你的解决方案进行说明吧。相比回过头去再添加注释，删除多余的注释要容易得多。从现在开始，本书的示例都将使用注释来阐述代码的工作原理。
  
## 2.2 python 之禅

## 2.3 pep8

# 3. 表达式

## 3.1 控制流

### if

#### elif

#### 条件表达式(即"三元操作符")

三元运算符可以只需要一行完成条件判断和赋值操作

```
data = x if x < y else y
```

### while
while 是Python中的循环语句. 事实它上是一个条件循环语句. 与 if 声明相比, 如果 if 后的条件为真, 就会执行一次相应的代码块. 而 while 中的代码块会一直循环执行, 直到循环条件不再为真.

语法：

```python
 while expression:
        suite_to_repeat
```

while 循环的 suite_to_repeat 子句会一直循环执行, 直到 expression 值为布尔假. 这种 类型的循环机制常常用在计数循环中。

```python
count = 0
while (count < 9):
    print('the index is:', count)
    count += 1
```

#### 无限循环

你必须小心地使用 while 循环, 因为有可能它的条件永远不会为布尔假. 这样一来循环就永远不会结束. 这些"无限"的循环不一定是坏事, 许多通讯服务器的客户端/服务器系统就是通过它来工作的. 这取决于循环是否需要一直执行下去, 如果不是, 那么这个循环是否会结束; 也就是说, 条件表达式会不会计算后得到布尔假?


```python
while True:
    handle, indata = wait_for_client_connect()
    outdata = process_request(indata)
    ack_result_to_client(handle, outdata)
```

例如上边的代码就是故意被设置为无限循环的，因为 True 无论如何都不会变成 False. 这是因为服务器代码是用来等待客户端(可能通过网络)来连接的. 这些客户端向服务器发送请求, 服务器处理请求. 请求被处理后, 服务器将向客户端返回数据, 而此时客户端可能断开连接或是发送另一个请求. 对于服务器而言它已经完成了对这个客户端的任务, 它会返回最外层循环等待下一个连接. 

#### while使用 else 语句
在 python 中，for … else 表示这样的意思，for 中的语句和普通的没有区别，else 中的语句会在循环正常执行完（即 for 不是通过 break 跳出而中断的）的情况下执行，while … else 也是一样。

```
count = 0
while count < 5:
   print count, " is  less than 5"
   count = count + 1
else:
   print count, " is not less than 5"
```
结果：
```
0 is less than 5
1 is less than 5
2 is less than 5
3 is less than 5
4 is less than 5
5 is not less than 5
```



### for

Python 提供给我们的另一个循环机制就是 for 语句. 它提供了 Python 中最强大的循环结构. 它可以遍历序列成员。

for 循环会访问一个可迭代对象(例如序列或是迭代器)中的所有元素, 并在所有条目都处理过后结束循环. 它的语法如下:

```python
for iter_var in iterable:        suite_to_repeat
```

每次循环, iter_var 迭代变量被设置为可迭代对象(序列, 迭代器, 或者是其他支持迭代的对象)的当前元素, 提供给 suite_to_repeat 语句块使用.

#### else

for 循环也可以有 else 用于循环后处理(post-processing). 它和 while 循环中的 else 处理方式相同. 只要 for 循环是正常结束的(不是通过 break ), else 子句就会执行.


```
s = ["a", "b", "c", "d", "e"]
found = False
for c in s:
    if c.find("c") != -1:
        found = True
        print("发现c项")
        break
 
if not found:
    print("没有发现c项")
```

```
s = ["a", "b", "c", "d", "e"]
for c in s:
    if c.find("c") != -1 :
        print("发现c项")
        break
else:
    print("没有c项")
```

#### enumerate

```
>>> l = ['a', 'b', 'c']
>>> 
>>> for index, item in enumerate(l):
...     print(index, item)
...
0 a
1 b
2 c
```
#### range()

内建函数 range() 可以把类似 foreach 的 for 循环变成你更加熟悉的语句. 例如从 0 到 10 计数, 或者从 10 到 100 一次递增 5 .

```
range(start, end, step=1)
```

```
>>> range(5)
range(0, 5)

>>> list(range(10))
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

>>> list(range(0, 10, 2))
[0, 2, 4, 6, 8]
```

#### zip

定义：zip([iterable, ...])

zip()是Python的一个内建函数，它接受一系列可迭代的对象作为参数，将对象中对应的元素打包成一个个tuple（元组），然后返回由这些tuples组成的list（列表）。若传入参数的长度不等，则返回list的长度和参数中长度最短的对象相同。利用*号操作符，可以将list unzip（解压），看下面的例子就明白了：


```
>>> a = [1,2,3]
>>> b = [4,5,6]
>>> c = [4,5,6,7,8]
>>> zipped = zip(a,b)
[(1, 4), (2, 5), (3, 6)]
>>> zip(a,c)
[(1, 4), (2, 5), (3, 6)]
>>> zip(*zipped)
[(1, 2, 3), (4, 5, 6)]
```

### pass

空语句。

如果你在需要子语句块的地方不写任何语句, 解释器会提示你 语法错误. 因此, Python 提供了 pass 语句, 它不做任何事情 - 即 NOP , ( No OPeration , 无操作) 我们从汇编语言中借用这个概念. pass 同样也可作为开发中的小技巧, 标记你后来要完成的代码

### break

Python 中的 break 语句可以结束当前循环然后跳转到下条语句, 类似 C 中的传统 break . 常用在当某个外部条件被触发(一般通过 if 语句检查), 需要立即从循环中退出时. break 语句可以用在 while 和 for 循环中.

### continue

不管是 Python, C, Java 还是其它任何支持 continue 语句的结构化语言中, 一些初学者有这样的一个误解: continue 语句"立即启动循环的下一次迭代". 实际上, 当遇到 continue 语句时, 程序会终止当前循环, 并忽略剩余的语句, 然后回到循环的顶端. 在开始下一次迭代前, 如果是条件循环, 我们将验证条件表达式. 如果是迭代循环, 我们将验证是否还有元素可以迭代. 只有在验证成功的情况下, 我们才会开始下一次迭代.

Python 里的 continue 语句和其他高级语言中的传统 continue 并没有什么不同. 它可以被用在 while 和 for 循环里. while 循环是条件性的, 而 for 循环是迭代的, 所以 continue 在开始下一次循环前要满足一些先决条件, 否则循环会正常结束.


```
>>> for s in 'hello':
...  if s == 'l':
...     continue
...  print(s)
... 
h
e
o
```

## 推导式
推导式是从一个或者多个迭代器快速简洁地创建数据结构的一种方法。他可以讲循环和条件判断结合，从而避免语法冗长的代码。会使用推导式有时可以说明你已经超过 Python初学者的水平。也就是说，使用推导式更像 Python 风格


### 列表推导式

你可以从1到5创建一个整数列表，每次增加一项：

```
>>> number_list = []
>>> number_list.append(1)
>>> number_list.append(2)
>>> number_list.append(3)
>>> number_list.append(4)
>>> number_list.append(5)
>>> number_list
[1, 2, 3, 4, 5]
```

或者，可以结合 range() 函数使用一个迭代器：

```
>>> number_list = []
>>> for number in range(1, 6):
...     number_list.append(number)
...
>>> number_list
[1, 2, 3, 4, 5]
```
上面这些方法都是可行的Python代码，会得到相同的结果。然而，更像 Python 风格的创建列表方法是列表推导。语法如下：

```
[ expression for item in iterable ]
```

将通过列表推导创建一个整数列表：

```
>>> number_list = [number for number in range(1,6)]
>>> number_list
[1, 2, 3, 4, 5]
```
在第一行中，第一个 number 变量为列表生成值，也就是说，把循环的结果放在列表 number_list 中。 第二个 number 可以为表达式， 看下下面的例子：

```
>>> number_list = [number-1 for number in range(1,6)]
>>> number_list
[0, 1, 2, 3, 4]
```

列表推到把循环放在方括号内部。这种例子和之前碰到的不大一样，但却是更为常见的方式。同样，列表推导也可以像下面的例子加上条件表达式：

```
[expression for item in iterable if condition]
```
现在，通过推导创建一个在1到5之间的偶数列表（当 number % 2 为真时，代表奇数；为假时代表偶数）：

```
>>> a_list = [number for number in range(1,6) if number % 2 == 1]
>>> a_list
[1, 3, 5]
```

正如很多嵌套循环一样，在对应的推导中会有多个for语句，我们先来看一个简单的嵌套循环例子：

```
>>> rows = range(1,4)
>>> cols = range(1,3)
... for row in rows:
...     for col in cols:
...         print(row, col)
...
1 1
1 2
2 1
2 2
3 1
3 2
```
使用一次推导，将结果赋值给变量 cells，使 row，col 成为元组：

```
>>> rows = range(1,4)
>>> cols = range(1,3)
>>> cells = [(row, col) for row in rows for col in cols]
>>> for cell in cells:
...     print(cell)
...
(1, 1)
(1, 2)
(2, 1)
(2, 2)
(3, 1)
(3, 2)
>>>
```
另外，在对 cells 列表进行迭代时可以通过元组拆封将变量 row 和 col 的值分别取出：

```
>>> for row, col in cells:
...     print(row, col)
...
1 1
1 2
2 1
2 2
3 1
3 2
```
其中，列表推导中 for row ...和 for col ...都可以有自己单独的 if 条件判断。


```
>>> rows = range(1,4)
>>> cols = range(1,3)
>>> cells = [(row, col) for row in rows if row % 2 == 1  for col in cols if col % 2 == 1]
>>> cells
[(1, 1), (3, 1)]
>>>
```


# 3.2  id is ==
Python中的对象包含三要素：id、type、value
其中id返回一个对象的唯一标识，type标识对象的类型，value是对象的值
is判断的是a对象是否就是b对象，是通过id来判断的
==判断的是a对象的值是否和b对象的值相等，是通过value来判断的
如下代码或许可以帮助你理解。


```
>>> a = 1
>>> b = 1.0
>>> a is b
False
>>> a == b
True
>>> id(a)
12777000
>>> id(b)
14986000
>>> a = 1
>>> b = 1
>>> a is b
True
>>> a == b
True
>>> id(a)
12777000
>>> id(b)
12777000
```

> 就 CPython 而言，id 返回的就是运行期内存地址。因此这个标识属阶段性的，不能保证不被重复使用。 但对于其他实现来说，id 返回的未必就是内存地址。

### 字典推导式

### 集合推导式

集合也不例外，同样有推导式。最简单的版本和之前的列表、字典推导类似：

```
{expression for expression in iterable }
```

也可以使用条件判断：

```python
>>> a_set = {number for number in range(1,6) if number % 3 == 1}
>>> a_set
{1, 4}
```


# 4. 函数

代码复用的第一步是使用函数，它是命名的用于区分的代码段。函数可以接受任何数字或者其他类型的输入作为参数，并且返回数字或者其他类型的结果。

你可以使用函数做一下两件事情：

* 定义函数
* 调用函数

## 定义：
语句 def 在运行期创建函数对象，并与指定名字关联。

```
def func_name():
    pass  # 写入你的逻辑
```

## 参数
传入到函数的值称为参数。当调用含参数的函数时，这些参数的值会被复制给函数中的对应参数。

```
>>> def get_name(num):
...     if num == 1:
...         return '老大'
...     elif num == 2:
...         return '老二'
...
...
>>> name = get_name(1)
>>> name
'老大'
```
这个函数做了如下事情：

* 把 1 赋值给函数的内部参数 num
* 运行 if-elif 的逻辑链
* 返回一个字符串
* 将该字符串赋值给变量 name

一个函数可以接受任何数量（包括0）的任何类型的值作为输入变量，并且返回任何数量（包括0）的任何类型的结果。如果函数不显示调用 return 函数，那么会默认返回 None。

```
>>> def func_name():
...     pass
...
>>> print(func_name())
None
>>>
```

**None**

None 是 Python 中一个特殊的值，虽然它不表示任何数据，但仍然具有重要的作用。 虽然 None 作为布尔值和 False 是一样的，但是它和 False 有很多差别。下面是一个例子:

```python
>>> thing = None
>>> if thing:
...     print("It's some thing")
... else:
...     print("It's no thing")
...
It's no thing
```

为了区分 None 和布尔值 False , 使用 Python 的 is 操作符:

```python
>>> if thing is None:
...     print("It's nothing")
... else:
...     print("It's something")
...
It's nothing
```
这虽然是一个微妙的区别，但是对于 Python 来说是很重要的。你需要把 None 和不含 任何值的空数据结构区分开来。0 值的整型 / 浮点型、空字符串('')、空列表([])、 空元组((,))、空字典({})、空集合(set())都等价于 False，但是不等于 None。现在，快速写一个函数，输出它的参数是否是 None:

```python
>>> def is_none(thing):
...    if thing is None:
...        print("It's None")
...    elif thing:
...        print("It's True")
...    else:
...        print("It's False")
```
现在，运行一些测试函数:

```python
>>> is_none(None)
It's None
>>> is_none(True)
It's True
>>> is_none(False)
It's False
>>> is_none(0)
It's False
>>> is_none(0.0)
It's False
>>> is_none(())
It's False
>>> is_none([])
It's False
>>> is_none({})
It's False
>>> is_none(set())
It's False
```

## 位置参数
Python 处理参数的方式要比其他语言更加灵活。其中，最熟悉的参数类型是位置参数，传入参数的值是按照顺序依次复制过去的。

```
>>> def name (n1, n2, n3):
...     print('1', n1)
...     print('2', n2)
...     print('3', n3)
...
>>> name('老大', '老二', '老三')
1 老大
2 老二
3 老三
>>>
```

尽管这种方式很常见，但是位置参数的一个弊端是必须熟记没个位置的参数的含义。在调用函数name() 时误把最后一个参数当做第一个参数，会得到完全不同的结果：

```
>>> name('老二', '老大', '老三')
1 老二
2 老大
3 老三
>>>
```
## 关键字参数
为了避免位置参数带来的混乱，调用参数时可以指定对应的名字，甚至可以采用与函数定义不同的顺序调用：

```
>>> name(n2='老二', n1='老大', n3='老三')
1 老大
2 老二
3 老三
>>>
```
你也可以把位置参数和关键字参数混合起来。

```
>>> name('老大', n2='老二', n3='老三')
1 老大
2 老二
3 老三
```

如果同时出现两种参数形式，首先应该考虑的是位置参数。


```
>>> name(n2='老二', '老大', n3='老三')
  File "<ipython-input-60-2a320a67eb2a>", line 1
    name(n2='老二', '老大', n3='老三')
                     ^
SyntaxError: positional argument follows keyword argument
```
## 指定默认参数
当调用方没有提供对应的参数值时，你可以指定默认参数值。


```
>>> def name (n2, n3, n1='老大'):
...     print('1', n1)
...     print('2', n2)
...     print('3', n3)
...
...
>>> name('老二', '老三')
1 老大
2 老二
3 老三
>>>
```
> 默认参数值在函数被定义时已经计算出来，而不是在程序运行时。Python程序员经常犯的一个错误是把可变的数据类型（例如列表或者字典）当做默认参数值。

在函数 box() 在每次调用时，添加参数 arg 到一个空的列表 result, 然后打印输出一个单值列表。但存在一个问题：只有在第一次调用时列表是空的，第二次调用时就会存在之前调用的返回值：

```
>>> def box(arg, result=[]):
...     result.append(arg)
...     print(result)
...
>>> box('a')
['a']
>>> box('b')
['a', 'b']
```

如果写成下面的样子就会解决刚才的问题：

```
>>> def box(arg):
...     result = []
...     result.append(arg)
...     return result
...
>>> box('a')
['a']
>>> box('b')
['b']
```
这样的修改也是为了表明第一次调用跳过一些操作：

```
>>> def box(arg, result=None):
...     if result is None:
...         result = []
...     result.append(arg)
...     print(result)
...
>>> box('a')
['a']
>>> box('b')
['b']
```

# 生成器

# 装饰器

# 命名空间和作用域

# 5. 类

Python里的所有数据都是以对象形式存在的，无论是的简单的数字类型还是复杂的代码模块。然而，Python特殊的语法形式巧妙地将实现对象机制的大量细节隐藏起来。输入 num = 1 就可以创建一个值为 1 的整数对象，并且将这个对象值赋值给变量num。事实上，在Python中，只有当你想要创建属于自己的对象或者需要修改已有的对象的行为时，才需要关注对象的内部实现细节。

对象既包含数据（变量，更习惯称之为特性，attribute），也包含代码（函数，也成为方法）。它是某一类具体事务的特殊实例。例如，整数 7 就是一个包含了加法、乘法之类方法的对象。整数 8 则是另一个对象。这意味着在 Python 里，7和8都属于一个公共的类，我们称之为整数类。(字符串、list、dict)

当你想要创建一个别人从来没有创建过的新对象时，首先必须定义一个类，用以指明该类的对象所包含的内容（特性和方法）。

可以把对象想象成名词，那么方法就是动词。对象代表着一个独立的事物，它的方法则定义了它是如何与其他事物互相作用的。

与模块不同，你可以同时创建许多同类的对象，他们的特性值可能各不相同。对象就是像是包含了代码的超级数据结构。

## 术语

property   属性 
attribute   特性 

## 使用 class 定义类
想要在Python中创建属于自己的类使用关键字 class 来定义，我们先看个例子。

假设你想要定义一些对象用于记录联系人，每个对象对应一个人。首先需要定义 Person 类作为生产对象的模具。在接下来的几个例子中，我们会不停更新这个类的内容，从最简单的开始，知道它成为一个可实际使用的类。

首先创建的是最简单的类，即一个没有任何内容的空类：

```
>>> class Person():
...     pass
```

同函数一样，用 pass 表示这个类是一个空类。上面这种定义类的方法已经是最简形式，无法再忽略。你可以通过类名来创建对象，同调用函数一样：

```
>>> someone = Person()
```

在这个例子中，Person()创建了一个Person类的对象，并给它赋值 someone 这个名字。但是，由于我们的Person类是空的，所以由它创建的对象 someone 实际上什么也做不了。实际编程中，你永远也不会创建这样一个没用的类，我在这里只是为了从零开始引出后面每一步的内容。

我们来试着重新定义一下 Person 类。这一次，将 Python 中特殊的对象初始化方法放入其中：

```
>>> class Person():
...     def __init__(self):
...         pass
```

我承认 __init__() 和 self 看起来很奇怪，但这就是实际的Python类的定义形式。__init__() 是 Python 中一个特殊的函数名，用于根据类的定义创建实例对象。self参数指向了这个正在被创建的对象本身。

当你在类生命定义 __init__() 方法时，第一个参数必须为 self。尽管 self 并不是一个 Python 保留字，但它很常用。

尽管我们添加了初始化方法，但用这个 Person 类创建的对象仍然什么也做不了。接着我们在初始化方法中添加 name 参数：

```
>>> class Person():
...     def __init__(self, name):
...         self.name = name
...
```
用 Person 类创建一个对象，为 name 特性传递一个字符串参数：

```
>>> hunter = Person("Elmer Fudd")
```
> python执行：
> Person.__init__(huter, "Elmer Fudd")
> self 其实就是代表要实例化的对象，这个例子里是 huter。

上面这短短的一行代码实际做了以下工作：

* 查看 Person 类的定义；
* 在内存中实例化（创建）一个新的对象
* 调用对象的 __init__ 方法， 将这个新创建的对象作为 self 传入，并将另一个参数（'Elemer-Fudd'）作为 name 传入；
* 将 name 的值存入对象；
* 返回这个新的对象；
* 将名字 hunter 与这个对象关联。

这个新对象与任何其他的python对象一样。 你可以把它当作列表、元组、字典或集合中的元素，也可以把它当作参数传递给函数，或者把它作为函数的返回结果。

我们传入的 name 参数 作为对象的特性存储在了对象里。可以直接对它进行读写操作：

```
>>> print('The mighty hunter: ', hunter.name)
The mighty hunter:  Elmer Fudd
```
记住，在 Person 类定义的内部， 你可以直接通过 self.name 访问 name 特性。 而当创建了一个实际的对象后，例如这里的 hunter，需要通过 hunter.name 来访问他。

在类的定义中， __init__ 并不是必需的。只有当需要区分由该类创建的不同对象时，才需要指定 __init__ 方法。

## 继承
在你编写代码解决实际问题时，经常能找到一些已有的类，它们能够实现你所需的大部分功能，但不是全部。这时该怎么办？当然，你可以对这个已有的类进行修改，但这么做很容易让代码变得更加复杂，一不留神就可能会破坏原来可以正常工作的功能。

当然，也可以另起炉灶重新编写一个类：复制粘贴原来的代码再融入自己的新代码。但这意味着你需要维护更多的代码。同时，新类和旧类中实现同样功能的代码被分隔在了不同的地方（日后修改时需要改动多处）。

更好的解决方法是利用类的继承：从已有类中衍生出新的类，添加和修改部分功能。这是代码复用的一个绝佳的例子。使用继承得到的新类会自动获得旧类中的多有方法，而不需要进行任何复制。

你只需要在新类里面定义自己额外需要的方法，或者按照需求对继承的方法进行修改即可。修改得到的新方法会覆盖原有的方法。我们习惯将原始的类称为父类、超类或基类，将新的类称作孩子类、子类或衍生类。这些术语在面向对象的编程中不加以区分。

现在，我们来试试继承。首先，定义一个空类 Car。然后，定义一个 Car 的子类 Yugo。定义子类使用的也是 class 关键字，不过需要把父类的名字放在子类名字后面的括号里：

```python
>>> class Car():
...     pass
... 
>>> class Yugo(Car):
...     pass
... 
```

接着，为每个类创建一个实力对象：

```python
>>> give_me_a_car = Car()
>>> give_me_a_yugo = Yugo()
```

子类是父类的一种特殊情况，它属于父类。在面向对象的术语里，我们经常成 Yugo 是一个 Car。 对象 give_me_a_yugo 是 Yugo 类的一个实例，但它同事集成了 Car 能做到的所有事情。当然，上面的例子中 Car 和 Yugo 就像潜艇上的甲板水手一样起不到任何实际作用。我们来更新一下类的定义，让它们发挥点儿作用：

```python
>>> class Car():
...     def exclaim(self):
...         print("I'm a Car!")
...
>>> class Yugo(Car):
...     pass
...
>>>
```

最后，为每一个类各创建一个对象，并调用刚刚声明的 exclaim 方法：

```
>>> give_me_a_car = Car()
>>> give_me_a_yugo = Yugo()
>>> give_me_a_car.exclaim()
I'm a Car!
>>> give_me_a_yugo.exclaim()
I'm a Car!
```

我们不需要进行任何特殊的操作，Yugo 就自动从 Car 那里继承了 exclaim() 方法。但事实上，我们并不希望 Yugo 在 exclaim() 方法里面宣称它是一个 Car，这可能会造成无法区分 Car 和 Yugo。让我们来看看怎么解决这个问题。

## 覆盖方法

新创建的子类会自动继承父类的所有信息。接下来我们来看子类如何替代——覆盖（override）父类的方法。

```
>>> class Car():
...     def exclaim(self):
...         print("I'm a Car!")
...
>>> class Yugo(Car):
...     def exclaim(self):
...         print("I'm a Yugo! Much like a Car, but more Yugo-ish.")
...
```

为每个类创建一个对象：
```
>>> give_me_a_car = Car()
>>> give_me_a_yugo = Yugo()
```

执行看下结果：

```
>>> give_me_a_car.exclaim()
I'm a Car!
>>> give_me_a_yugo.exclaim()
I'm a Yugo! Much like a Car, but more Yugo-ish.
```
我们覆盖了父类的 exclaim() 方法。 在子类中，可以覆盖任何父类的方法，包括 __init__()。下面我们使用之前的 Person 类。我们来创建两个子类，分别代表医生(MDPerson)和（JDPerson）

```
>>> class Person():
...     def __init__(self, name):
...         self.name = name
...
>>> class MDPerson(Person):
...     def __init__(self, name):
...         self.name = "Doctor " + name
...
>>> class JDPerson(Person):
...     def __init__(self, name):
...         self.name = name + ", Esquire"
...
>>>
```
在上面的例子中，子类的初始化方法 __init__() 接受的参数和父类  Person 一样，但存储到对象内部 name 特性的值却不尽相同：

```
>>>  person = Person('Fudd')
>>> doctor = MDPerson('Fudd')
>>> lawyer = JDPerson('Fudd')
>>> print(person.name)
Fudd
>>> print(doctor.name)
Doctor Fudd
>>> print(lawyer.name)
Fudd, Esquire
>>>
```

## 添加新方法

子类还可以添加父类中没有的方法。回到 Car 类 和 Yugo 类，我们给 Yugo 类添加一个新的方法 need_a_push():

```
>>> class Car():
...     def exclaim(self):
...         print("I'm a Car!")
...
>>> class Yugo(Car):
...     def exclaim(self):
...         print("I'm a Yugo! Much like a Car, but more Yugo-ish.")
...     def need_a_push(self):
...         print("A little help here?")
...
```

接着创建一个 Car 和一个 Yugo 对象：

```
>>> give_me_a_car = Car()
>>> give_me_a_yugo = Yugo()
```
Yugo 类的对象可以响应 need_a_push()方法：

```
>>> give_me_a_yugo.need_a_push()
A little help here?
```

但父类 Car 无法使用该方法：

```
>>> give_me_a_car.need_a_push()
Traceback (most recent call last):
  File "<ipython-input-98-61aca925ea27>", line 1, in <module>
    give_me_a_car.need_a_push()
AttributeError: 'Car' object has no attribute 'need_a_push'
```
至此，Yugo终于可以做一些 Car 做不到的事情了。它的与众不同的特征开始体现了出来。

## super
我们已经知道如何在子类中覆盖父类的方法，但如果想要调用父类的方法就要使用 super()。下面的例子将新定义一个新的类 EmailPerson，用于表示有电子邮箱的 Person。首先，来定义熟悉的Person类：

```
>>> class Person():
...     def __init__(self, name):
...         self.name = name
...
```

下面是子类的定义。注意，子类的初始化方法 __init__() 中添加了一个额外的 email 参数：

```
>>> class EmailPerson(Person):
...     def __init__(self, name, email):
...         super().__init__(name)
...         self.email = email
...
```
在子类中定义 __init__() 方法时，父类的 __init__() 方法会被覆盖。因此在子类中父类的初始化方法并不会被自动调用，我们必须显式调用它。以上代码实际上做了这样几件事情：

* 通过 super() 方法获取了父类 Person 的定义。
* 子类的 __init__() 调用了 Person.__init__() 方法。它会自动将 self 参数传递给父类。因此，你只需传入其余参数即可。在上面的例子中，Person() 能接受的其余参数指的是 name。
* self.email = email 这行新的代码才真正起到了将 EmailPerson 与 Person 区分开的作用。

接下来，创建一个 EmailPerson 类的对象：

```
>>> bob = EmailPerson('Bob Frapples', 'bob@frapples.com')
```
我们既可以访问 name 特性，也可访问 email 特性：

```
>>> bob.name
'Bob Frapples'
>>> bob.email
'bob@frapples.com'
```
为什么不像下面这样定义 EmailPerson 类呢？

```python
>>> class EmailPerson(Person):
...     def __init__(self, name, email):
...         self.name = name
...         self.email = email
...
```

确实可以这么做，但这有悖我么使用继承的初衷。我们应该使用 super() 来让 Person 完成他应该做的事情，就像任何一个单纯的 Person 对象一样。除此之外，不这么写还有另一个好处，如果 Person 类的定义在未来发生改变，使用 super() 可以保证这些改变会自动体现在 EmailPersion类上，而不需要手动修改。

子类可以按照自己的方式处理问题，但如果人需要借助父类的帮助，使用 super() 是最佳的选择。


## self

Python 中经常被争议的一点（除了使用空格外）就是必须把 self 设置为实例方法的第一个参数。Python 使用 self 参数来找到正确的对象所包含的特性和方法。通过下面的例子，我会告诉你调用对象方法背后 Python 实际做的工作。

```
>>> car = Car()
>>> car.exclaim()
I'm a Car!
```
Python 在背后做了一下两件事：

* 查找 car 对象所属的类（Car）；
* 把 car 对象作为 self 参数传给 Car 类所包含的 exclaim() 方法。

了解调用机制后，为了好玩，我们甚至可以像下面这样进行调用，这与普通的调用语法(car.exclaim())效果完全一致：

```
>>>  Car.exclaim(car)
I'm a Car!
```
当然，我们没有理由使用这种臃肿的语法。

## 使用属性对特性进行访问和设置

property   属性 
attribute   特性 

有一些面向对象的语言支持私有特性。这些特性无法从对象外部直接访问，我们需要编写 getter 和 setter 方法对这些私有特征进行读写操作。

Python 不需要 getter 和 setter 方法，因为 Python 里所有特性都是公开的，使用时全凭自觉。如果你不放心直接访问对象的特性，可以为对象编写 setter 和 getter 方法。 但更具Python 风格的解决方案是使用属性(property)。

下面例子中，首先定义一个 Duck 类，他仅包含一个 hidden_name 特性。我们不希望别人能够直接访问这个特性，因此需要定义两个方法：getter 方法（get_name()）和 setter方法（set_name()）。我们在没个方法中都添加一个 print() 函数，这样就能方便地知道它们何时被调用。最后，把这些方法设置为 name 属性：

```
>>> class Duck():
...     def __init__(self, input_name):
...         self.hidden_name = input_name
...     def get_name(self):
...         print('inside the getter')
...         return self.hidden_name
...     def set_name(self, input_name):
...         print('inside the setter')
...         self.hidden_name = input_name
...     name = property(get_name, set_name)
...
```

这两个新方法在最后一行之前都与普通的 getter 和 setter 方法没有任何区别，最后一行则把这两个方法定义为了 name 属性。 property() 的第一个参数是 getter 方法，第二个参数是 setter 方法。现在，当你尝试访问 Duck 类对象的 name 特性时，get_name()会被自动调用：

```
>>> fowl = Duck('Howard')
>>> fowl.name
inside the getter
'Howard'
```
当然，也可以显式调用 get_name() 方法，它就像普通的 getter 方法一样：

```
>>> fowl.get_name()
inside the getter
'Howard'
```
当对 name 特性执行赋值操作时，set_name() 方法会被调用：

```
>>> fowl.name = 'Daffy'
inside the setter
>>> fowl.name
inside the getter
'Daffy'
```
也可以显式调用 set_name() 方法：

```
>>> fowl.set_name('Daffy')
inside the setter
>>> fowl.name
inside the getter
'Daffy'
>>>
```
另一种定义属性的方式是使用装饰器（decorator）。下一个例子会定义两个不同的方法，它们都叫 name()，担保函不同的装饰器：

* @property, 用于指示 getter 方法
* @name.setter, 用于指示 setter 方法

```
>>> class Duck():
...     def __init__(self, input_name):
...         self.hidden_name = input_name
...     @property
...     def name(self):
...         print('inside the getter')
...         return self.hidden_name
...     @name.setter
...     def name(self, input_name):
...         print('inside the setter')
...         self.hidden_name = input_name
...
```

你仍然可以像之前访问特性一样访问 name, 但这里没有显式的 get_name() 和 set_name() 方法：

```
>>> fowl = Duck('Howard')
>>> fowl.name
inside the getter
'Howard'
>>> fowl.name = 'Donald'
inside the setter
>>> fowl.name
inside the getter
'Donald'
>>>
```
> 实际上，如果有人能猜到我们在类的内部用的特性名是 hidden_name，他仍然可以直接通过 fowl.hidden_name 进行读写操作。

在前面几个例子中，我们都使用 name 属性指向类中存储的某一特性（在我们的例子中是 hidden_name）。除此之外，属性还可以指向一个计算结果值。我们来定义一个 Circle （圆）类，它包含 radius（半径） 特性以及一个计算属性 diameter（直径）:

```
>>> class Circle():
...     def __init__(self, radius):
...         self.radius = radius
...     @property
...     def diameter(self):
...         return 2 * self.radius
...
```
创建一个 Circle 对象，并给 radius 赋予一个初值：

```
>>> c = Circle(5)
>>> c.radius
5
```
可以像访问特性（例如 radius）一样访问属性 diameter：

```
>>> c.diameter
10
```
真正有趣的还在后面。我们可以随时改变 radius 特性的值，计算属性 diameter 会自动根据新的值更新自己：

```
>>> c.radius = 7
>>> c.diameter
14
```
如果你没有指定某一特性的 setter 属性（@diameter.setter），那么将无法从类的外部对它的值进行设置。这对于那些只读的特性非常有用：

```
>>> c.diameter = 20
Traceback (most recent call last):
  File "<ipython-input-22-dd5da562ba9f>", line 1, in <module>
    c.diameter = 20
AttributeError: can't set attribute
```
与直接访问特性相比，使用 property 还有一个巨大的优势，如果你改变了某个特性的定义，只需要在类定义里修改相关代码即可，不需要再每一处调用修改。



## 使用名称重整保护私有特性
前面的 Duck 列子中， 为了隐藏内部特性，我们曾将其命名为 hidden_name 。 其实，Python 对那些需要刻意隐藏在类内部的特性有自己的命名规范：
由连续的两个下划线开头（__）。

我们来把 hidden_name 改名为 __name，如下所示：

```

>>> class Duck():
...     def __init__(self, input_name):
...         self.__name = input_name
...     @property
...     def name(self):
...         print('inside the getter')
...     @name.setter
...     def name(self, input_name):
...         print('inside the setter')
...         self.__name = input_name
...
```
看看代码是否还能正常工作：

```
>>> fowl = Duck('Howard')
>>> fowl.name
inside the getter
'Howard'
>>> fowl.name = 'Donald'
inside the setter
>>> fowl.name
inside the getter
'Donald'
```
看起来没问题，现在，你无法在外部访问 __name 特性了：

```
>>> fowl.__name
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
AttributeError: 'Duck' object has no attribute '__name'
```

这种命名规范本质上并没有把特性变成私有，但Python确实将它的名字重整了。让外部的代码无法使用。如果你是在好奇名称重整是怎么实现的。我可以偷偷告诉你其中的奥秘：

```
>>> fowl._Duck__name
'Donald'
```

发现了么？我们并没有得到 inside the getter，成功绕过了 getter 方法。尽管如我们所见，这种保护特性的方式并不完美，但它确实能在一定程度上避免我们无意或有意地对特性进行直接访问。

## 方法的类型
有些数据（特性）和函数（方法）是类本身的一部分，还有一些是由类创建的实例的一部分。

在类的定义中，以 self 作为第一个参数的方法都是实例方法（instance method）。它们在创建自定义类时最常用。实例方法的首个参数是 self，当它被调用时，Python 会把调用该方法的对象作为 self 参数传入。

与之相对，类方法（class method）会作用于整个类，对类作出的任何改变会对它的所有实例对象产生影响。在类定义内部，用前缀修饰符 @classmethod 指定的方法都是类方法。与实例方法相似，类方法的第一个参数是类本身。在Python中，这个采纳数常被写作 cls，因为全称 class 是保留字，在这里我们无法使用。下面的例子中，我们为A定义一个类方法来记录一共有多少个类A的对象被创建：

```
>>> class A():
...     count = 0
...     def __init__(self):
...         A.count += 1
...     def exclaim(self):
...         print("I'm an A!")
...     @classmethod
...     def kids(cls):
...         print("A has", cls.count, "little objects.")
...
>>> easy_a = A()
>>> breezy_a = A()
>>> wheezy_a = A()
>>> A.kids()
A has 3 little objects.
```

注意，上面的代码中，我们使用的是 A.count（类特性），而不是 self.count （可能是对象的特性）。在 kids() 方法中，我们使用的是 cls.count，它与 A.count 的作用一样。

类定义中的方法还存在着第三种类型，它既不会影响类也不会影响类的对象。他们出现在类的定义中仅仅是为了方便，否则他们只能孤零零地出现在代码的其他地方，这会影响代码的逻辑性。这种类型的方法被称作静态方法（static method），用 @staticmethod 修饰， 它既不需要 self 参数 也不需要 class 参数。 下面列子中的静态方法是一则 CoyoteWeapon的广告：

```
>>> class CoyoteWeapon():
...     @staticmethod
...     def commercial():
...         print('This CoyoteWeapon has been brought to you by Acme')
...
>>> CoyoteWeapon.commercial()
This CoyoteWeapon has been brought to you by Acme
>>>
```

注意，在这个例子中，我们甚至都不用创建任何 CoyoteWeapon 类的对象就可以调用这个方法，语法优雅不失风格！

## 鸭子类型

Python 对实现多态（polymorphism）要求得十分宽松，这意味着我们可以对不同对象调用同名的操作，甚至与用管这些对象的类型是什么。

我们来为上那个 Quote 类设定同样的初始化方法 __init__()，然后再添加两个新函数：

* who() 返回保存的 person 字符串的值
* says() 返回保存的 words 字符串的内容，并添上指定的表点符号。

它们的具体实现如下所示：

```
>>> class Quote():
...     def __init__(self, person, words):
...         self.person = person
...         self.words = words
...     def who(self):
...         return self.person
...     def says(self):
...         return self.words + '.'
...
>>> class QuestionQuote(Quote):
...     def says(self):
...         return self.words + '?'
...
>>> class ExclamationQuote(Quote):
...     def says(self):
...         return self.words + '!'
...
>>>
```

我们不需要改变 QuestionQuote 或者 ExclamQuote 的初始化方式，因此没有覆盖它们的 __init__()方法。Python 会自动调用父类 Quote 的初始化函数 __init__() 来存储实例变量 person 和 words，这就是我们可以在子类 QuestionQuote 和 ExclamationQuote 的对象里访问 self.words 的原因。

接下来创建一些对象：

```
>>> hunter = Quote('Elmer Fudd', "I'm hunting wabbits")
>>> print(hunter.who(), 'says:', hunter.says())
Elmer Fudd says: I'm hunting wabbits.

>>> hunted1 = QuestionQuote('Bugs Bunny', "What's up, doc")
>>> print(hunted1.who(), 'says:', hunted1.says())
Bugs Bunny says: What's up, doc?

>>> hunted2 = ExclamationQuote('Daffy Duck', "It's rabbit season")
>>> print(hunted2.who(), 'says:', hunted2.says())
Daffy Duck says: It's rabbit season!
```
三个不同版本的 says() 为上面三种类型提供了不同的相应方式，这是面向对象的语言中多态的传统形式。Python 在这方面走的更远一些，无论对象的种类是什么，只要包含 who() 和 says()，你便可以调用它。我们再来定义一个 BabblingBrook 类，他与我们之前的猎人猎物（Quote 类的后代）什么的没有任何关系：

```
>>> class BabblingBrook():
...     def who(self):
...         return 'Brook'
...     def says(self):
...         return 'Babble'
...
>>> brook = BabblingBrook()
```
现在，对不同对象执行 who() 和 says() 方法，其中有一个（brook） 与其他类型的对象毫无关联：

```
>>> def who_says(obj):
...     print(obj.who(), 'says', obj.says())
...
>>> who_says(hunter)
Elmer Fudd says I'm hunting wabbits.
>>> who_says(hunted1)
Bugs Bunny says What's up, doc?
>>> who_says(hunted2)
Daffy Duck says It's rabbit season!
>>> who_says(brook)
Brook says Babble
```

这种方式有事被称作鸭子类型（duck typing），这个命名源自一句名言：

```
  如果它想鸭子一样走路，像样子一样叫，那么它就是一直鸭子。
                                                   ———— 以为智者
```

## 特殊方法
到目前为止，你已经能创建并使用基本对象了。现在再往深钻研一些。

当我们输入像 a = 3 + 8 这样的表达式时，整数 3 和 8 怎么知道如何实现 + 的？ 同样， a 又是怎么知道如何使用 = 来获取计算结果的？ 你可以使用 Python 的特殊方法（special method），有时魔术方法（magic method）， 来实现这些操作符的功能。别担心，它们一点也不复杂。

这些特殊的方法的名称以双下划线(__)开头和结束。没错，你已经见过其中一个：
__init__，它根据类的定义以及传入的参数对新创建的对象进行初始化。

假设你有一个简单的 Word 类，现在想要添加一个 equals() 方法来比较两个词是否一致，忽略大小写。也就是说，一个包含值 'ha' 的 Word 对象与包含 'HA' 的是相同的。

下面的代码是第一次尝试，创建一个普通方法 equals()。self.text 是当前 Word 对象所包含的字符串文本，equals() 方法将该字符串与 words （另一个 Word 对象）所包含的字符串做比较：

```
>>> class Word():
...     def __init__(self, text):
...         self.text = text
...
...     def equals(self, word2):
...         return self.text.lower() == word2.text.lower()
...
```

接着创建三个包含不通字符串的 Word 对象：

```
>>> first = Word('ha')
>>> second = Word('HA')
>>> third = Word('eh')
```
当字符串 'ha' 和 'HA' 被转换为小写形式再进行比较时（我们就是这么做的），他们应该是相等的：

```
>>> first.equals(second)
True
```
但字符串 'eh' 无论如何与 'ha'也不会相等：

```
>>> first.equals(third)
False
```

我们成功定义了 equals() 方法进行小写转换并比较。但试想一下，如果能通过 if first == second 进行比较的话岂不更妙？这样类会更自然，表现得更像一个 Python 内置的类。 好的，我们来试一下，把前面例子中的 equals() 方法的名称改为 __eq__() ：

```
>>> class Word():
...     def __init__(self, text):
...         self.text = text
...     def __eq__(self, word2):
...         return self.text.lower() == word2.text.lower()
...
```

修改就此结束，来看看新的版本能否正常工作：

```
>>> first = Word('ha')
>>> second = Word('HA')
>>> third = Word('eh')
>>> first == second
True
>>> first == third
False
```
太神奇了！是不是如同魔术一般？仅需将方法名改为 Python 里进行相等比较的特殊方法名 __eq__() 即可。下面列出一些常用的魔术方法：

和比较相关的魔术方法
![](/media/14878335329824.jpg)

和数学相关的魔术方法
![](/media/14878335686210.jpg)

不仅数字类型可以使用像 + （魔术方法 __add__()）和 - （魔术方法 __sub__()）的数学运算符，一些其他的类型也可以使用。例如，Python 的字符类型使用 + 进行拼接，使用 * 进行复制。字符串常见的魔术方法如下：
![](/media/14878341886394.jpg)

除了 __init__() 外，你会发现在编写类方法时最常用到的是 __str__()，他用于定义如何打印对象信息。print() 方法，str() 方法以及一些字符串格式化的相关方法都会用到 __str__()。交互式解释器则用 __repr__() 方法输出变量。如果在你的类既没有定义 __str__() 也没有定义 __repr__(), Python会输出类似下面这样的默认字符串：

```
>>> first = Word('ha')
>>> first
<__main__.Word object at 0x10a70b908>
>>> print(first)
<__main__.Word object at 0x10a70b908>
```

我们将 __str__() 和 __repr__() 方法都添加到 Word 类里，让输出的对象信息变得更好看些：

```
>>> class Word():
...     def __init__(self, text):
...         self.text = text
...     def __eq__(self, word2):
...         return self.text.lower() == word2.text.lower()
...     def __str__(self):
...         return self.text
...     def __repr__(self):
...         return 'Word(' + self.text + ')'
...
...
>>> first = Word('ha')
>>> first
Word(ha)
>>> print(first)
ha
>>>
```

更多关于魔术方法的内容请查看 Python 文档 [https://docs.python.org/3/reference/datamodel.html#special-method-names](https://docs.python.org/3/reference/datamodel.html#special-method-names)

## 组合
如果你想要创建的子类在大多数情况下的行为都和父类相似的话，使用继承是非常不错的选择，建立复杂的继承关系确实很吸引人，但有些时候使用组合（composition）或者聚合（aggregation）更加符合现实的逻辑。一只鸭子是鸟的一种，它有一条尾巴。尾巴并不是鸭子的一种，它是鸭子的组成部分。

```
>>> class Tail():
...     def __init__(self, length):
...         self.length = length

>>> class Bill():
...     def __init__(self, description):
...         self.description = description

>>> class Duck():
...     def __init__(self, bill, tail):
...         self.bill = bill
...         self.tail = tail
...     def about(self):
...         print('This duck has a', bill.description, 'bill and a',
... tail.length, 'tail')
...
>>> tail = Tail('long')
>>> bill = Bill('wide orange')
>>> duck = Duck(bill, tail)
>>> duck.about()
This duck has a wide orange bill and a long tail
>>>
```

## 何时使用类和对象而不是模块
有一些方法可以帮助你决定是把你的代码封装到类里还是模块里。

* 当你需要许多具有相似行为（方法）但不同状态（特性）的实例时，使用对象是最好的选择。
* 类支持继承，但模块不支持。
* 如果你想要保证实例的唯一性，使用模块是最好的选择。不管模块在程序中被引用多少次，始终只有一个实例被加载（单例）。
* 如果你有一系列包含多个值的变量，并且它们能作为参数传入不同的函数，那么最好将它们封装到类里面。举个例子，你可能会使用以 size 和 color 为键的字典代表一张彩色图片。你可以在程序中为每张图片创建不同的字典，并把它们作为参数传递给像 scale() 或者 transform() 之类的函数。但这么做的话，一但你想要添加其他的键或者函数会变得非常麻烦。为了确保统一性，应该定义一个 Image 类，把 size 和 color 作为特性，把 scale() 和 transform 定义为方法。这么一来，关于一张图片的所有数据和可执行的操作都存储在了统一的位置。
* 用最简单的方式解决问题。使用字典、列表和元组往往要比使用模块更加简单、简洁且快速。而使用类则更为复杂。

创始人 Guido 的建议：

```
不要过度构建数据结构。尽量使用元组（以及命名元组）而不是对象。尽量使用简单的属性域儿不
是 getter/setter 函数…… 内置数据类型是你最好的朋友。尽可能多地使用数字、字符串、元
组、列表、集合以及字典。多看看容器库提供的类型，尤其是双端队列。

                     		                                          —— Guid van Rossum
```





# 6. [文件异常](http://opslinux.com/2017/02/15/6-%E6%96%87%E4%BB%B6%E4%B8%8E%E5%BC%82%E5%B8%B8/)



# 7. 模块





