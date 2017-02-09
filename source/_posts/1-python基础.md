title: 1.python基础
date: 2016-11-18 22:41:28
categories:
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


```
>>> 2 + 3*414>>> (2 + 3) * 4 20
```
在这些示例中，空格不影响Python计算表达式的方式，它们的存在旨在让你阅读代码时，能 迅速确定先执行哪些运算。

### 浮点数
Python将带小数点的数字都称为浮点数。大多数编程语言都使用了这个术语，它指出了这样一个事实:小数点可出现在数字的任何位置。每种编程语言都须细心设计，以妥善地处理浮点数， 确保不管小数点出现在什么位置，数字的行为都是正常的。

```
>>> 0.1 + 0.10.2>>> 0.2 + 0.2
0.4>>>2 * 0.10.2>>>2 * 0.20.4
```

但需要注意的是，结果包含的小数位数可能是不确定的:


```
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

### +

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
## 1.8 集合
  
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

```
 while expression:        suite_to_repeat
```
while 循环的 suite_to_repeat 子句会一直循环执行, 直到 expression 值为布尔假. 这种 类型的循环机制常常用在计数循环中。

```
 count = 0    while (count < 9):        print('the index is:', count)        count += 1
```

#### 无限循环

你必须小心地使用 while 循环, 因为有可能它的条件永远不会为布尔假. 这样一来循环就永远不会结束. 这些"无限"的循环不一定是坏事, 许多通讯服务器的客户端/服务器系统就是通过它来工作的. 这取决于循环是否需要一直执行下去, 如果不是, 那么这个循环是否会结束; 也就是说, 条件表达式会不会计算后得到布尔假?


```
while True:        handle, indata = wait_for_client_connect()        outdata = process_request(indata)        ack_result_to_client(handle, outdata)
```

例如上边的代码就是故意被设置为无限循环的，因为 True 无论如何都不会变成 False. 这是因 为服务器代码是用来等待客户端(可能通过网络)来连接的. 这些客户端向服务器发送请求, 服务器处理请求. 请求被处理后, 服务器将向客户端返回数据, 而此时客户端可能断开连接或是发送另一个请求. 对于服务器而言它已经完成了对这个客户端的任务, 它会返回最外层循环等待下一个连接. 

### for

Python 提供给我们的另一个循环机制就是 for 语句. 它提供了 Python 中最强大的循环结构. 它可以遍历序列成员。

for 循环会访问一个可迭代对象(例如序列或是迭代器)中的所有元素, 并在所有条目都处理过 后结束循环. 它的语法如下:

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
    if c.find("c") != -1 :
        found = True
        print("发现以字母c开头的项")
        break
 
if not found:
    print("没有发现以字母c开头的项")
```

```
s = ["a", "b", "c", "d", "e"]
for c in s:
    if c.find("c") != -1 :
        print("发现以字母c开头的项")
        break
else:
    print("没有发现以字母c开头的项")
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

不管是 Python, C, Java 还是其它任何支持 continue 语句的结构化语言中, 一些初学者有这样 的一个误解: continue 语句"立即启动循环的下一次迭代". 实际上, 当遇到 continue 语句时, 程序会终止当前循环, 并忽略剩余的语句, 然后回到循环的顶端. 在开始下一次迭代前,如果是条件循环, 我们将验证条件表达式. 如果是迭代循环,我们将验证是否还有元素可以迭代. 只有在验证成功的情况下, 我们才会开始下一次迭代.

Python 里的 continue 语句和其他高级语言中的传统 continue 并没有什么不同. 它可以被 用在 while 和 for 循环里. while 循环是条件性的, 而 for 循环是迭代的, 所以 continue 在开 始下一次循环前要满足一些先决条件(前边的核心笔记中强调的), 否则循环会正常结束.


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

### 推导式

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

```
     >>> thing = None     >>> if thing:     ...     print("It's some thing")     ... else:     ...     print("It's no thing")     ...     It's no thing```

为了区分 None 和布尔值 False , 使用 Python 的 is 操作符:

```     >>> if thing is None:     ...     print("It's nothing")     ... else:     ...     print("It's something")     ...     It's nothing
```
这虽然是一个微妙的区别，但是对于 Python 来说是很重要的。你需要把 None 和不含 任何值的空数据结构区分开来。0 值的整型 / 浮点型、空字符串('')、空列表([])、 空元组((,))、空字典({})、空集合(set())都等价于 False，但是不等于 None。现在，快速写一个函数，输出它的参数是否是 None:

```
 >>> def is_none(thing):
...    if thing is None:...        print("It's None")...    elif thing:...        print("It's True")...    else:...        print("It's False")```
现在，运行一些测试函数:

```     >>> is_none(None)     It's None     >>> is_none(True)     It's True     >>> is_none(False)     It's False     >>> is_none(0)     It's False     >>> is_none(0.0)     It's False     >>> is_none(())     It's False
>>> is_none([])It's False>>> is_none({})It's False>>> is_none(set())It's False
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

# 5. 类
  
# 6. 文件异常

## 文件
数据持久化最简单的类型是普通文件，有时也叫平面文件（flat file）。它仅仅是在一个文件名下的字节流，把数据从一个文件读入内存，然后从内存写入文件。Python很容易实现这些文件操作，它模仿熟悉和流行的 unix 系统的操作。

读写一个文件之前需要打开它：


```python
data = open(filename, mode)
```

下面是对该 open() 调用的简单解释：

* data 是 open() 返回的文件对象；
* filename 是该文件的字符串名；
* mode 是指明文件类型和操作的字符串。

mode 的第一个字母表明对其的操作。

* r 表示读模式。
* w 表示写模式。若果文件不存在则新创建，如果存在则重写新内容。
* x 表示在文件不存在的情况下新创建并写文件。
* a 表示如果文件存在，在文件末尾追写内容。

mode 的第二本字母是文件类型：

* t（或者省略） 代表文本类型。
* b 代表二进制文件。

打开文件之后就可以调用函数来读写数据，最后需要关闭文件。

### 使用 write() 写文本文件

```
>>> poem = "日照香炉生紫烟，遥看瀑布挂前川。飞流直下三千尺，疑是银河落九天。"
>>> len(poem)
32
```

将整首诗写到libai.txt中：

```
>>> fout = open('libai.txt', 'wt')
>>> fout.write(poem)
32
fout.close()
```

函数 write() 返回写入文件的字节数。和 print() 一样， 他没有增加空格或者换行符。同样，你也可以在一个文本文件中使用 print()


```
>>> fout = open('libai.txt', 'w')
>>> print(poem, file=fout)
>>> fout.close()
```

这就产生了一个问题：到底是用是 write() 还是 print()？ print() 默认会在每个参数后面添加空格，在每行结束处添加换行。在之前的例子中， libai.txt 中默认添加了一个换行。为了使 print() 与 write() 有同样的输出，传入下面两个参数：

* sep 分隔符：默认是一个空格 ' '
* end 结束字符：默认是一个换行符 '\n'

除非自定义参数，否则 print() 会使用默认参数。在这里，我们通过空字符串替换 print() 添加的所有多余输出：

```python
>>> fout = open('libai.txt', 'w')
>>> print(poem, file=fout, sep='', end='')
>>> fout.close()
```

如果字符串非常大，可以将数据分块，知道所有字符被写入：


```python
>>> fout = open('libai.txt', 'w')
>>> size = len(poem)
>>> size
32
>>> offset = 0
>>> chunk = 10
>>> while True:
...     if offset > size:
...         break
...     fout.write(poem[offset:offset+chunk])
...     offset += chunk
...
>>> fout.close()
```

第一次写 10 个字符，4次写完，32个字符。

如果 libai.txt 文件已经存在，使用模式 x 可以避免重写文件：

```python
>>> font = open('libai.txt', 'xt')
Traceback (most recent call last):
  File "<ipython-input-108-c2dbf65c7612>", line 1, in <module>
    font = open('libai.txt', 'xt')
FileExistsError: [Errno 17] File exists: 'libai.txt'
>>>
```

### 使用 read()、readline() 或者 readlines() 读取文本文件

你可以按照下面的示例那样，使用不带参数的 read() 函数一次读入文件的所有内容。但在读入文件时要格外注意，1GB的文件会用到相同大小的内存。

```python
>>> fin = open('libai.txt', 'rt')
>>> poem = fin.read()
>>> poem
'日照香炉生紫烟，遥看瀑布挂前川。飞流直下三千尺，疑是银河落九天。'
>>> fin.close()
>>> len(poem)
32
```

同样也可以设置最大的读入字符数限制 read() 函数一次返回的大小。下面一次读入10个字符，然后把每一快拼接成原来的字符串 poem


```python
>>> poem = ''
>>> fin = open('libai.txt', 'rt')
>>> chunk = 10
>>> while True:
...     fragment = fin.read(chunk)
...     if not fragment:
...         break
...     poem += fragment
...
>>> fin.close()
>>> len(poem)
32
>>> poem
'日照香炉生紫烟，遥看瀑布挂前川。飞流直下三千尺，疑是银河落九天。'
```

读到结尾之后，再次调用 read() 会返回空字符串('')， if not fragment 条件呗判断为 False。此时会跳出 while True 的循环。 当然， 你也能使用 readline() 每次读入文件的一行。 在下面的例子中，通过追加每一行拼接成原来的字符串 poem:

```python
>>> poem = ''
>>> fin = open('libai.txt', 'rt')
>>> while True:
...     line = fin.readline()
...     if not line:
...         break
...     poem += line
...
>>> fin.close()
>>> len(poem)
32
>>> poem
'日照香炉生紫烟，遥看瀑布挂前川。飞流直下三千尺，疑是银河落九天。'
```

对于一个文本文件，即使空行也有1字符长度（换行符'\n'），自然会返回 True。当文件读取结束后，readline() （类似 read() ） 同样会返回空字符串，也被 while True 判断为 False。

读取文本文件最简单的方式是使用一个迭代器（iterator），它会每次返回一行。这和之前的例子类似，但代码会更短：

```
>>> poem = ''
>>> fin = open('libai.txt', 'rt')
>>> for line in fin:
...     poem += line
...
>>> fin.close()
>>> len(poem)
32
>>> poem
'日照香炉生紫烟，遥看瀑布挂前川。飞流直下三千尺，疑是银河落九天。'
```

前面所有的示例最终都返回单个字符串 poem。 函数 readlines() 调用时每次读取一行，并返回单行字符串的列表：


```
>>> poem = '''日照香炉生紫烟,
... 遥看瀑布挂前川。
... 飞流直下三千尺，
... 疑是银河落九天。
... '''
>>> fin = open('libai.txt', 'wt')
>>> fin.write(poem)
36
>>> fin.close()

>>> fin = open('libai.txt', 'rt')
>>> lines = fin.readlines()
>>> fin.close()
>>> lines
['日照香炉生紫烟,\n', '遥看瀑布挂前川。\n', '飞流直下三千尺，\n', '疑是银河落九天。\n']
>>> print(len(lines), 'lines read')
4 lines read
>>> for line in lines:
...     print(line, end='')
...
日照香炉生紫烟,
遥看瀑布挂前川。
飞流直下三千尺，
疑是银河落九天。
```

### 使用 write() 写二进制文件

如果文件模式字符串中包含 'b', 那么文件会议二进制模式打开，这种情况下，读写的是字节而不是字符串。

我们手边没有二进制格式的诗，所以直接在 0~255 产生 256 字节的值：

```python
>>> bdata = bytes(range(0, 256))
>>> len(bdata)
256
```

以二进制模式打开文件，并且一次写入所有的数据：


```python
>>> fout = open('bfile', 'wb')
>>> fout.write(bdata)
256
>>> fout.close()
>>>
```

再次，write() 返回到写入的字节数。

对于文本，也可以分块写二进制数据：

```python
>>> fout = open('bfile', 'wb')
>>> size = len(bdata)>>> offset = 0>>> chunk = 100>>> while True:...     if offset > size:...         break...     fout.write(bdata[offset:offset+chunk])...     offset += chunk...10010056>>> fout.close()
```

### 使用 read() 读取二进制文件

```python
>>> fin = open('bfile', 'rb')
>>> bdata = fin.read()>>> len(bdata)256>>> fin.close()
```

### 使用 with 自动关闭文件

如果你旺季关闭已经打开的一个文件，在该文件对象不再被引用之后 Python 会关掉此文件。这也意味着在一个函数中打开文件，并没有及时关闭它，但是在函数结束时会被关掉。然而你可能会在一直运行中的函数或者程序的主要部分打开一个文件，应该强制剩下的所有写操作完成后再关闭文件。

Python的上下文管理器（context manager）会清理一些资源，例如打开的文件。它的形式为 with expression as variable：

```python
>>> with open('libai.txt', 'wt') as fout:
>>> ... fout.write(poem)...
```

完成上下文管理器的代码后，文件会自动关闭。

### 使用 seek() 改变位置

无论是读或者写文件，Python都会跟踪文件中的位置。函数 tell() 返回距离文件开始处的字节偏移量。函数 seek() 允许跳转到文件其他字节偏移量的位置。这意味着可以不用从头读取文件的没一个字节，直接跳转到最后位置并制度一个字节也是可行的。

对于这个例子，使用之前写过的 256 字节的二进制文件 'bfile':

```python
>>> fin = open('bfile', 'rb')
>>> fin.tell()0
```
使用 seek() 读取文件结束前最后一个字节:

```python
>>> fin.seek(255)255
```

一直读到文件结束:

```python
>>> bdata = fin.read()>>> len(bdata)1>>> bdata[0]255
```

seek() 同样返回当前的偏移量。

用第二个参数调用函数 seek()： seek(offset, origin)

* 如果 origin 等于0 （默认为0），从头便宜 offset 个字节；
* 如果 origin 等于1，从当前位置处偏移 offset 个字节；
* 如果 origin 等于2，距离最后结尾处偏移 offset 个字节。

这些值也在标准库 os 模块中被定义：

```python
>>> import os
>>> os.SEEK_SET
0
>>> os.SEEK_CUR
1
>>> os.SEEK_END
2
```

所以，我们可以用不通的方法读取最后一个字节：

```python
>>> fin = open('bfile', 'rb')
```

文件结尾前的一个字节：

```
>>> fin.seek(-1, 2)255>>> fin.tell()255
```

一直读到文件结尾：

```python
>>> bdata = fin.read()>>> len(bdata)1>>> bdata[0]255
```

> 在调用 seek() 函数时不需要额外调用 tell()。前面的例子只是想说明两个函数都可以返回同样的偏移量。

下面是从文件的当前位置寻找：

```python>>> fin = open('bfile', 'rb') 
```

接下来的例子返回最后两个字节：

```python
>>> fin.seek(254, 0)254>>> fin.tell()254
```

在此基础上前进一个字节：

```python
>>> fin.seek(1, 1)255>>> fin.tell()255
```

这些函数对于二进制文件都是极其重要的。当文件是 ASCII 编码（每个字符一个字节）时，也可以使用它们，但是计算偏移量会是一个麻烦事。其实，这些都取决于文件的编码格式，最流行的编码格式（例如 UTF-8）每个字符的字节数都不尽相同。




## 异常
Python使用被称为异常的特殊对象来管理程序执行期间发生的错误。每当发生让Python不知 所措的错误时，它都会创建一个异常对象。如果你编写了处理该异常的代码，程序将继续运行; 如果你未对异常进行处理，程序将停止，并显示一个traceback，其中包含有关异常的报告。异常是使用try-except代码块处理的。try-except代码块让Python执行指定的操作，同时告 诉Python发生异常时怎么办。使用了try-except代码块时，即便出现异常，程序也将继续运行: 显示你编写的友好的错误消息，而不是令用户迷惑的traceback。

### 使用 try-except 代码块

当你认为可能发生了错误时，可编写一个try-except代码来处理可能引发的异常。你让 Python尝试运行一些代码，并告诉它如果这些代码引发了指定的异常，该怎么办。

try 语句有两种主要形式: try-except 和 try-finally . 这两个语句是互斥的, 也就是说你 只能使用其中的一种. 一个 try 语句可以对应一个或多个 except 子句, 但只能对应一个 finally 子句, 或是一个 try-except-finally 复合语句.处理ZeroDivisionError异常的try-except代码 类似于下面这样：
   
```python
>>> try:
...     print(5/0)
... except ZeroDivisionError:
...     print("You can't divide by zero!")
...
You can't divide by zero!
```

我们将导致错误的代码行print(5/0)放在了一个try代码中。如果try代码中的代码运行起来没有问题，Python将跳过except代码; 如果try代码中的代码导致了错误，Python将查找这样的except代码块，并运行其中的代码，即其中指定的错误与引发的错误相同。 在这个示例中，try代码中的代码引发了ZeroDivisionError异常，因此Python指出了该如何解决问题的except代码块，并运行其中的代码。这样，用户看到的是一条 好的错误消息，而不是traceback:

```
You can't divide by zero!
```

如果try-except代码后面还有其他代码，程序将接着运行，因为已经告诉了Python如何处理这种错误。

### 使用异常避免崩溃

发生错误时，如果程序还有工作没有完成，妥善地处理错误就尤其重要。这种情况经常会出现在要求用户提供输入的程序中;如果程序能够妥善地处理无效输入，就能再提示用户提供有效输入，而不至于崩溃。

下面来创建一个只执行除法运算的简单计算器:

```python
 1 # coding=utf-8
 2 print("Give me two numbers, and I'll divide them.")
 3 print("Enter 'q' to quit.")
 4
 5 while True:
 6     first_number = input("\nFirst number: ")
 7     if first_number == 'q':
 8         break
 9     second_number = input("Second number: ")
10     if second_number == 'q':
11         break
12     answer = int(first_number) / int(second_number)
13     print(answer)
```

在第6行，这个程序提示用户输入一个数字，并将其存储到变量first_number中; 如果用户输入的不是表示退出的q，就再提示用户输入一个数字，并将其存储到变量second_number中(见第9行 )。 接下来，我们计算这两个数字的商 (即answer，见12行)。这个程序没有采取任何处理错误的措施，因此让它执行除数为0的除法运算时，它将崩溃:


```
Give me two numbers, and I'll divide them.
Enter 'q' to quit.

First number: 5
Second number: 0
Traceback (most recent call last):
  File "<ipython-input-208-1e61f850d337>", line 11, in <module>
    answer = int(first_number) / int(second_number)
ZeroDivisionError: division by zero
>>>
```
程序崩溃可不好，但让用户看到 traceback 也不是好主意。不懂技术的用户会被它们搞糊涂， 而且如果用户 怀有恶意，他会通过traceback获悉你不希望他知道的信息。例如，他将知道你的程序文件的名称，还将看到部分不能正确运行的代码。有时候，训练有素的攻击者可根据这些信息判断出可对你的代码发起什么样的攻击。

### else 代码块

通过将可能引发错误的代码放在try-except代码中，可提高这个程序抵御错误的能力。错误是执行除法运算的代码行导致的，因此我们需要将它放到try-except代码块中。这个示例还包含一个else代码块; 依赖于try代码块成功执行的代码都应放到else代码中:


```python
  1 # coding=utf-8
  2 print("Give me two numbers, and I'll divide them.")
  3 print("Enter 'q' to quit.")
  4
  5 while True:
  6     first_number = input("\nFirst number: ")
  7     if first_number == 'q':
  8         break
  9     second_number = input("Second number: ")
 10     if second_number == 'q':
 11         break
 12     try:
 13         answer = int(first_number) / int(second_number)
 14     except ZeroDivisionError:
 15         print("You can't divide by 0!")
 16     else:
 17         print(answer)
```

我们让Python尝试执行try代码块中的除法运算(见12行)，这个代码块只包含可能导致错误的代码。依赖于try代码块成功执行的代码都放在else代码中; 在这个示例中，如果除法运算成功，我们就使用else代码块来打印结果(见16行)。 except代码块告诉Python，出现ZeroDivisionError异常时该怎么办(见14行 )。如果try代码因除零错误而失败，我们就打印一条友好的消息，告诉用户如何避免这种错误。程序将继续运行，用户根本看不到traceback:

```
Give me two numbers, and I'll divide them.
Enter 'q' to quit.

First number: 5
Second number: 0
You can't divide by 0!

First number: 5
Second number: 2
2.5

First number: q
>>>
```
try-except-else代码块的工作原理大致如下: Python尝试执行try代码块中的代码; 只有可能引发异常的代码才需要放在try语句中。有时候，有一些仅在try代码块成功执行时才需要运行的的代码; 这些代码应放在else代码中。except代码块告诉Python，如果它尝试运行try代码块中的代码时引发了指定的异常，该怎么办。 通过预测可能发生错误的代码，可编写健壮的程序，它们即便面临无效数据或缺少资源，也能继续运行，从而能够抵御无意的用户错误和恶意的攻击。

### 失败时不提示

使用 pass

### 决定报告那些错误

在什么情况下该向用户报告错误? 在什么情况下又应该在失败时不提示呢? 如果用户知道要分析哪些文件，他们可能希望在有文件没有分析时出现一条消息，将其中的原因告诉他们。 如果用户只想看到结果，而并不知道要分析哪些文件，可能就无需在有些文件不存在时告知他们。 向用户显示他不想看到的信息可能会降低程序的可用性。Python的错误处理结构让你能够细致地控制与用户分享错误信息的程度，要分享多少信息由你决定。 
编写得很好且经过详尽测试的代码不容易出现内部错误，如语法或逻辑错误，但只要程序依赖于外部因素，如用户输入、存在指定的文件、有网络连接，就有可能出现异常。凭借经验可判断该在程序的什么地方包含异常处理 ，以及出现错误时该向用户提供多少相关的信息。


### finally子句finally 子句是无论异常是否发生,是否捕捉都会执行的一段代码. 你可以将 finally 仅仅配合 try 一起使用,也可以和 try-except(else 也是可选的)一起使用. 你可以用 finally 子句 与 try-except 或 try-except-else 一起使用.
下面是 try-except-else-finally 语法的示例:

```python
try: 
    Aexcept MyException:
    Belse: 
    Cfinally: 
    D
```

当然,无论如何,你都可以有不止一个的 except 子句,但最少有一个 except 语句,而 else 和 finally 都是可选的.A,B,C 和 D 是程序(代码块).程序会按预期的顺序执行.(注意:可能的顺序是 A-C-D[正常]或 A-B-D[异常]).无论异常发生在 A,B,和/或 C 都将执行 finally 块.

# 7. 模块





