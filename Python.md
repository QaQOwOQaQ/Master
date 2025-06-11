## Reference

[python tutor code visualize](https://pythontutor.com/render.html#mode=edit)

[JSON](https://www.json.org/json-zh.html)

[python core 50 courses](https://github.com/jackfrued/Python-Core-50-Courses)

[翻译的文章](https://github.com/MrKiven/PyZh/tree/master/docs)

[Python3 CookBook](https://python3-cookbook.readthedocs.io/zh-cn/latest/index.html)

[Python Docs-en](https://docs.python.org/3/index.html)

[Python Docs：设计和历史常见问题](https://docs.python.org/zh-cn/3.6/faq/design.html)

[Python Docs：built-in function](https://docs.python.org/zh-cn/3.12/library/functions.html)

[Python Docs：tutorial](https://docs.python.org/zh-cn/3/tutorial/index.html)

[Python 设计哲学](https://docs.python.org/3.12/faq/design.html)

[Python Why-do?](https://github.com/chinesehuazhou/python-whydo)

## English

* leeches: 伸手党，（吸血，蚂蝗的延伸）
* docstrings：文档字符串，用于解释文档程序，帮助你的程序文档更加简单易懂，我们可以在函数体的第一行使用一对三个单引号 **'''** 或者一对三个双引号 **"""** 来定义文档字符串。你可以使用 **__doc__**（注意双下划线）调用函数中的文档字符串属性。

* indent：缩进
* intersection：十字路口，交点，交汇
* disjoint：不连贯的；（两个集合）不相交的
* paradigm：范式
* encapsulation：封装，隐藏一切可以隐藏的实现细节，只向外界暴漏简单的调用接口
* inheritance
* polymorphism
* dunder：Python中双下划线的读法
* built-in：内置
* json
* csv
* excel
* pdf
* crop：剪短；剪裁（照片）
* thumbnail：缩略图
* flip：翻转
* encrypt：加密
* watermark：水印
* wildcard：通配符，百搭牌
* purge：净化，清除，肃清
* sibling：同胞
* descendant：后代
* axes：轴线
* daemon：守护进程，后台进程
* reentrant：可重入
* coroutine：协程
* pip：Package Installer for Python

## 1. 初识Python

1991年2月：第一个Python解释器诞生，它是用C语言实现的，可以调用C语言的库函数。

**说明**：大多数软件的版本号一般分为三段，形如A.B.C，其中A表示大版本号，当软件整体重写升级或出现不向后兼容的改变时，才会增加A；B表示功能更新，出现新功能时增加B；C表示小的改动（例如：修复了某个Bug），只要有修改就增加C。

Python最主要的缺点是执行效率低，但是当我们更看重产品的开发效率而不是执行效率的时候，Python就是很好的选择。

目前Python在Web服务器应用开发、云基础设施开发、**网络数据采集**（爬虫）、**数据分析**、量化交易、**机器学习**、**深度学习**、自动化测试、自动化运维等领域都有用武之地。当然，Python语言还可以用来粘合其他语言开发的系统，所以也经常被戏称为“**胶水语言**”。

## 2. 第一个Python程序

* vscode：文本编辑器
* Pycharm：集成开发环境

**提醒**：我们也可以在任意位置打开“命令提示符”，然后将需要执行的Python代码通过拖拽的方式拖入到“命令提示符”中，这样相当于指定了文件的绝对路径来运行该文件中的Python代码。再次提醒，macOS系统要通过`python3`命令来运行该程序。

我们用Python写程序，最好每一行代码中只有一条语句。虽然使用`;`分隔符可以将多个语句写在一行代码中，但是最好不要这样做，因为代码会变得非常难看。我们用Python写程序，最好每一行代码中只有一条语句。虽然使用`;`分隔符可以将多个语句写在一行代码中，但是最好不要这样做，因为代码会变得非常难看。

Python中有两种形式的注释：

1. 单行注释：以`#`和空格开头，可以注释掉从`#`开始后面一整行的内容。
2. 多行注释：三个引号(`‘`，`“`)开头，三个引号结尾，通常用于添加多行说明性内容。

python中并没有对多行注释的内置支持，所谓通过三个引号实现多行注释的方法其实是使用了docstrings，需要注意的是，在使用docstrings进行注释时，缩进仍然很重要，不过，一般来说，应该坚持使用python的单行注释，即便是应对多行，这是因为docstrings是用来编写文档的，而不是用来注释代码的。（这一点在集成环境对这两种注释的处理也可以看出，单行注释是灰色的，docstrings注释是绿色的）

cpu：现代cpu一般由运算器和控制器构成，负责执行各种运算和控制指令

冯诺伊曼体系结构：（1）存储设备和中央处理器分开（2）将数据以二进制方式编码

需要说明的是，不同于C++、Java等编程语言，Python中没有用花括号来构造代码块而是**使用了缩进的方式来表示代码的层次结构**，换句话说**连续的代码如果又保持了相同的缩进那么它们属于同一个代码块**，相当于是一个执行的整体。**缩进**可以使用任意数量的空格，但**通常使用4个空格**

## 3. 变量

与C++不同：

- 整型（`int`）：Python中可以处理任意大小的整数，而且支持二进制（如`0b100`，换算成十进制是4）、八进制（如`0o100`，换算成十进制是64）、十进制（`100`）和十六进制（`0x100`，换算成十进制是256）的表示法。
- 布尔型（`bool`）：布尔值只有`True`、`False`两种值，要么是`True`，要么是`False`。

Python 整数的取值范围是无限的，不管多大或者多小的数字，Python 都能轻松处理。当所用数值超过计算机自身的计算能力时，Python 会自动转用高精度计算（大数计算）。

python的字符串是不可变类型，无法直接修改。通过间接方式对原字符串的修改，其实就是创建了一个新字符串代替原字符串。

变量命名规则：

- 硬性规则：
  - 规则1：变量名由**字母**、数字和**下划线**构成，数字不能开头。需要说明的是，这里说的字母指的是Unicode字符，Unicode称为万国码，囊括了世界上大部分的文字系统，这也就意味着中文、日文、希腊字母等都可以作为变量名中的字符，但是像`!`、`@`、`#`这些特殊字符是不能出现在变量名中的，而且我们强烈建议大家**尽可能使用英文字母**。
- 非硬性规则：
  - 规则1：变量名通常使用小写英文字母，多个单词用下划线进行连接。
  - 规则2：受保护的变量用单个下划线开头。
  - 规则3：私有的变量用两个下划线开头。

非硬性规则的规则2和规则3最大的作用就是做到“见名知意”

Python无需声明变量的类型，并且Python类型可以动态变化

常用函数：

* `type()`

* `bool`

* `int()`：将一个数值或字符串转换成整数，可以指定进制。

* `float()`：将一个字符串转换成浮点数。

* `str()`：将指定的对象转换成字符串形式，可以指定编码。

* `chr()`：将整数转换成该编码对应的字符串（一个字符）。

* `ord()`：将字符串（一个字符）转换成对应的编码（整数）。

  

## 4. 运算符

* 切片：``[:]`` ，假设对象的长度为n，那么正向索引`s[idx]`对应的负向索引为`s[n-idx]`，对于`[i:j:k]`，所取区间为`[i,j)`，k决定了索引的方向
* 指数：`**`
* 整除：``//``
* 身份运算符：`is`, `is not`，它比较的对象的内存的地址（可以通过``id()``查看）
* 成员运算符：`in`, `not in`
* 逻辑运算符：`not`, `or`, `and`，注意Python不使用`&&.||,!`
* 用于copy对象的`*`

留意 `or` 和 `and` 的**短路处理**特性。

赋值运算符的优先级最低。

`print(*objects, sep=' ', end='\n', file=sys.stdout, flush=False)`

- objects -- 复数，表示可以一次输出多个对象。输出多个对象时，需要用 , 分隔。
- sep -- 用来间隔多个对象，默认值是一个空格。
- end -- 用来设定以什么结尾。默认值是换行符 \n，我们可以换成其他字符串。
- file -- 要写入的文件对象。
- flush -- 输出是否被缓存通常决定于 file，但如果 flush 关键字参数为 True，流会被强制刷新。

针对objects有两种写法：`f` 和 `%`

``` python
a = 1234
b = 3.1415926
c = "hello"

print("%d, %.2f, %s!" % (a, b, c), a, b, c)
print(f'{a}, {b:.2f}, {c}!', a, b, c)
```

## 5. 分支和循环结构

### 5.1 分支

注意 `if` 后面的条件判断不需要加括号 

``` python
if something:
    dosomething
else if something:
    dosomething
else:
    dosomething
```

case:

``` python
year = int(input("pls input year: "))
if year % 400 == 0 or (year % 4 == 0 and year % 100 != 0):
    print("Yes")
else:
    print("No")
```

### 5.2 循环

* `for in`
* `while`
* `break`
* `continue`

在Python中，对元素的遍历也是有两种方法，类似于C++的普通`for`和`range-for`，以string为例：

``` python
s = "hello"
# way1
for ch in s:
    print(ch, end='')
print()
# way2
for i in range(len(s)):
    print(s[i], end='')
print()
```

## 6. 关键字

### 6.1 pass

pass 是空语句，是为了保持程序结构的完整性，它不做任何事情，一般用做占位语句。主要是为了解决Python不允许空函数、空循环的问题。

### 6.2 with

对于正确的处理涉及到异常的资源管理时，需要使用 `try/finally` 代码结构，这样的结构一多会导致整体代码结构 **很臃肿繁琐，不易读、不美观**，因此在 **Python2.6** 版本推出 `with` 关键字。

`with as` 语句是 `Pyhton` 提供的一种简化语法，适用于对资源进行访问的场合，确保不管使用过程中是否发生异常都会执行必要的**清理操作**（系统会自动调用`f.close()`），释放资源。

但并不是所有的对象都可以放在`with`上下文语法中，只有符合**上下文管理器协议**（有`__enter__`和`__exit__`魔术方法）的对象才能使用这种语法。

> 在文件对象中定义了 `__enter__` 和 `__exit__` 方法，即文件对象也实现了上下文管理器，首先调用 `__enter__` 方法，然后执行 with 语句中的代码，最后调用 `__exit__`  方法。 即使出现错误，也会调用 `__exit__`  方法，也就是会关闭文件流。

### 6.3 None

讨论：https://stackoverflow.com/questions/19473185/what-is-a-none-value

总结来看，None有一下作用：

1. 声明一个变量。由于Python中变量不需要指定类型，因此他并不想C那样可以声明一个变量而不赋值，例如`int a;`在C中是合法的，但是在Python中我们只能这样：`a`，这是Python解释器会报错：`NameError: name 'a' is not defined`，但如果我们 `a=None`，此时a就声明出来了。
2. 简化函数的行为。Python中规定，函数一定有一个返回值，如果我们不显式return，这个返回值就是None。

### 6.4 global

我们先来看一个例子：

``` python
x = 10
def func():
    x = x + 2
    print(x)
func()
'''
    x = x + 2
        ^
UnboundLocalError: cannot access local variable 'x' where it is not associated with a value
'''
```

在上面的例子中，我们想在函数体当中修改全局变量`x`的值，但是`x=x+2`会报错，这是因为**Python会默认函数体内的变量为局部变量**，因此在函数`func()`中会认为`x`是局部变量，但是在该函数中，`x`并未声明。

如果我们想在函数体内直接访问全局变量，需要先进行声明，声明方法就是global关键字：

``` PYTHON
x = 10 # 声明一个全局变量

def func():
    global x # 声明x是全局变量
    x = x + 2
    print("func:", x)

print("before func: ", x) # 10
func()					  # 12
print("main: ", x)        # 12
```

> 注意，如果我们`global x`时，`x`并未在函数外部声明，会报错！也就是说`x`必须存在

最后，总结以下global的使用场景：

1. **在函数内部修改全局变量的值**： 如果不使用 `global`，Python 会将函数内部的变量视为局部变量，导致无法修改全局变量。
2. **多个函数共享全局变量**： `global` 可以帮助多个函数访问和修改同一个变量。

### 6.4 nolocal

nolocal的思想和global一样，global是因为无法直接在函数内部直接修改全局变量，而nolocal是因为无法直接在函数内部修改局部变量（嵌套函数的情况）。

### 6.6 [yield](https://www.runoob.com/w3cnote/python-yield-used-analysis.html)

yield功能：

* **返回可迭代对象**：当生成器函数执行到 `yield` 语句时，它会暂停并返回一个值。这使得生成器可以在迭代时逐步产生结果，而不是一次性生成所有值。
* **接受值**：生成器可以通过 `yield` 接收外部发送的值。当使用 `send(value)` 方法调用生成器时，`yield` 语句会接收到这个值，并可以在生成器内部进行处理。

----

在详细介绍yield之前，先介绍一下range和xrange：

**返回值类型**：

* `range(start, stop)` 会返回一个**列表**，包含从 `start` 到 `stop-1` 的所有整数。
* `xrange(start, stop)` 返回一个**生成器对象**，这个对象在迭代时按需生成值，而不是一次性创建一个完整的列表。

**内存使用**：

* 由于 `range` 返回一个完整的列表，当你生成一个很大的范围时，它会占用大量内存。
* `xrange` 只在需要的时候生成数值，因此更加节省内存。

> ⚠注意！上面的分析基于Python2，实际上，在Python3中，range做的就是和xrange一样的事情。

---

而我们通过yield做的事，就是希望将一个返回“一大堆东西”的普通函数改造为一个只返回“很小一个东西”（生成器）的生成器函数，就相当于把range改造为xrange。从而减少内存消耗。

关键点：

1. **生成器函数**：当一个函数包含 `yield` 关键字时，它会被视为生成器函数。调用这个函数不会立即执行函数体，而是返回一个生成器对象。
2. **逐步生成值**：每次调用生成器的 `__next__()` 方法（通常通过 `next()` 函数或在循环中自动调用）时，函数会执行到下一个 `yield` 语句，然后返回 `yield` 后面的值。下一次调用时，会从上次 `yield` 的位置继续执行。
3. **节省内存**：因为生成器可以逐步生成数据，而不需要一次性把所有数据加载到内存中，所以在处理大数据集时非常高效。

例如，我们将求1~n的Fibonacci数列的函数改造为生成器函数：

``` python
def fib(n):
    a, b = 0, 1
    for _ in range(n):
        yield a
        a, b = b, a + b


f = fib(5)     # 创建一个生成器对象（可迭代对象）
print(type(f)) # <class 'generator'>

for i in range(5):
    print(f'[{i}] {next(f)}')
```

> 注意不要傻傻的将 `a, b = b, a + b` 写为下面的形式了：
>
> ``` python
> c = a + b
> a = b
> b = c
> ```

当生成器创建的可迭代对象迭代到终点时，在迭代会抛出`StopIteration`异常，表示迭代完成。

----

下面是一个通过`yield`接受`send()`方法发送的值的例子：

``` python
def get_average():
    total, count = 0, 0
    average = None
    while True:
        current = yield average# 接受send发送的值
        total += current
        count += 1
        average = total / count


def main():
    gen = get_average() # 创建生成器对象
    print('start: ', gen.send(None))    # 启动生成器
    while True:
        # 注意input默认读入str，需要进行type convert
        print('avg: ', gen.send(float(input('pls input a number: '))))



if __name__ == '__main__':
    main()
```



## 7. 正则表达式

### 7.1 reference

[正则表达式30分钟入门教程](https://deerchao.cn/tutorials/regex/regex.htm)

[正则表达式在线测试工具](https://www.jyshare.com/front-end/854/)

### 7.2 常用元字符

量词，断言，管道等都是元字符，不过是根据作用不同划分。

| 代码 | 说明                                             |
| ---- | ------------------------------------------------ |
| .    | 匹配除换行以外的任意字符                         |
| \w   | 匹配字母、数字、下划线或汉字等                   |
| \s   | 匹配任意的空白符                                 |
| \d   | 匹配数字                                         |
| \b   | 匹配单词的开始或结束（左右两次一个是\w一个不是） |
| ^    | 匹配字符串的开始                                 |
| &    | 匹配字符串的结束                                 |

> 在英文语境下，`\w` 就等价于 `[a-z0-9A-Z]`
>
> `^`，`&`和`\b`有分类为（零宽）断言字符（满足一定条件的字符）

当然，正则表达式中的元字符数量很庞大，用到时查询即可！

### 7.3 转义字符`\`

常见的，windows下文件的目录为：`C:\\Windows`，Linux目录为：`/root`

### 7.4 量词

| 代码  | 说明            |
| ----- | --------------- |
| *     | 重复0次或者多次 |
| +     | 重复1次或者多次 |
| ?     | 重复0次或1次    |
| {n}   | 重复n次         |
| {n,m} | 重复[n,m]次     |
| {n,}  | 等价于{n,∞}     |

### 7.5 字符类

| 代码     | 说明                  |
| -------- | --------------------- |
| [a-z]    | 匹配任意小写字母      |
| [aeiou]  | 匹配aeiou中的任意一个 |
| [a-zA-Z] | 匹配任意英文字母      |
|          |                       |

### 7.6 管道`|`

管道可以理解为分支，通过分支我们可以选择不同的匹配模式。

分支时要格外注意分支的顺序，例如我们相匹配5个数字或者5个数字后面跟连字符和4个数字的情况，那么`\d{5}|\d{5}-\d{4}`是错误的，因为对于`\d{5}-\d{4}`，它永远会被前面的`\d{5}`匹配掉。

### 7.7 分组

通过`()`来指定子表达式，称为分组，通过分组可以实现多个字符的重复。

默认情况下，每个分组都会有一个组号，分组0代表整个正则表达式，组号分配规则一般如下：

1. 从左向右扫描，给未命名分组分配组号，如果是嵌套分组，由内而外分配
2. 从左向右扫描，给命名分组分配组号

常用分组语法：

| 分类         | 代码/语法    | 说明                                                         |
| ------------ | ------------ | ------------------------------------------------------------ |
| **捕获**     | (exp)        | 匹配exp,并捕获文本到自动命名的组里                           |
|              | (?<name>exp) | 匹配exp,并捕获文本到名称为name的组里，也可以写成(?'name'exp) |
|              | (?:exp)      | 匹配exp,不捕获匹配的文本，也不给此分组分配组号               |
| **零宽断言** | (?=exp)      | 匹配exp前面的位置                                            |
|              | (?<=exp)     | 匹配exp后面的位置                                            |
|              | (?!exp)      | 匹配后面跟的不是exp的位置                                    |
|              | (?<!exp)     | 匹配前面不是exp的位置                                        |
| **注释**     | (?#comment)  | 这种类型的分组不对正则表达式的处理产生任何影响，用于提供注释让人阅读 |

> 非捕获组(?:exp)的作用是节省内存空间，因为被捕获的内容都是放到内存当中的。

### 7.8 反义

注意这里的反义不是反义字符的反义，而是“意思相反”的意思。

| 代码     | 说明                                       |
| -------- | ------------------------------------------ |
| \W       | 匹配任意不是字母，数字，下划线，汉字的字符 |
| \S       | 匹配任意不是空白符的字符                   |
| \D       | 匹配任意不是数字的字符                     |
| \B       | 匹配不是单词开头或结束的位置               |
| [^x]     | 匹配除了x意外的任意字符                    |
| [^aeiou] | 匹配除了“aeiou”这几个字母以外的任意字符    |

例如：`\S+`匹配不包含空白符的字符串，`<a[^>]+>`匹配用尖括号括起来的以a开头的字符串。

### 7.9 后向引用

当一个匹配模式（正则表达式）的全部或者部分内容由一对括号分组时，正则引擎就会对内容进行捕获并临时存储于内存中。可以通过后向引用引用捕获的内容，形式为`\n`引用的是第n个捕获的分组。



### 7.10 零宽断言

零宽断言：见名知义，零宽断言是一种零宽度的匹配，它匹配到的内容不会保存到匹配结果中去，最终匹配结果只是一个位置。

作用是给指定位置添加一个限定条件， 用来规定此位置之前或者之后的字符必须满足限定条件才能使用正则中的子表达式匹配成功。

(?=exp)也叫**零宽度正预测先行断言**，它断言自身出现的位置的后面能匹配表达式exp。比如\b\w+(?=ing\b)，匹配以ing结尾的单词的前面部分(除了ing以外的部分)，如查找*I'm singing while you're dancing.*时，它会匹配sing和danc。

(?<=exp)也叫**零宽度正回顾后发断言**，它断言自身出现的位置的前面能匹配表达式exp。比如(?<=\bre)\w+\b会匹配以re开头的单词的后半部分(除了re以外的部分)，例如在查找*reading a book*时，它匹配ading。

假如你想要给一个很长的数字中每三位间加一个逗号(当然是从右边加起了)，你可以这样查找需要在前面和里面添加逗号的部分：((?<=\d)\d{3})+\b，用它对*1234567890*进行查找时结果是234567890。

下面这个例子同时使用了这两种断言：(?<=\s)\d+(?=\s)匹配以空白符间隔的数字(再次强调，不包括这些空白符)。

### 7.11 负向零宽断言

前面我们提到过怎么查找**不是某个字符或不在某个字符类里**的字符的方法(反义)。但是如果我们只是想要**确保某个字符没有出现，但并不想去匹配它**时怎么办？例如，如果我们想查找这样的单词--它里面出现了字母q,但是q后面跟的不是字母u,我们可以尝试这样：

`\b\w*q[^u]\w*\b`匹配包含**后面不是字母u的字母q**的单词。但是如果多做测试(或者你思维足够敏锐，直接就观察出来了)，你会发现，如果q出现在单词的结尾的话，像**Iraq**,**Benq**，这个表达式就会出错。这是因为``[^u]``总要匹配一个字符，所以如果q是单词的最后一个字符的话，后面的``[^u]``将会匹配q后面的单词分隔符(可能是空格，或者是句号或其它的什么)，后面的`\w*\b`将会匹配下一个单词，于是`\b\w*q[^u]\w*\b`就能匹配整个**Iraq fighting**。**负向零宽断言**能解决这样的问题，因为它只匹配一个位置，并不**消费**任何字符。现在，我们可以这样来解决这个问题：``\b\w*q(?!u)\w*\b`。

> 这样，如果q后面是一个`,`的话。`(?!u)`不会匹配掉（消耗掉）这个逗号，接下来`\w*`仍然会尝试去匹配这个逗号。

**零宽度负预测先行断言**(?!exp)，断言此位置的后面不能匹配表达式exp。例如：\d{3}(?!\d)匹配三位数字，而且这三位数字的后面不能是数字；\b((?!abc)\w)+\b匹配不包含连续字符串abc的单词。

同理，我们可以用(?<!exp),**零宽度负回顾后发断言**来断言此位置的前面不能匹配表达式exp：(?<![a-z])\d{7}匹配前面不是小写字母的七位数字。

一个更复杂的例子：``(?<=<(\w+)>).*(?=<\/\1>)``匹配不包含属性的简单HTML标签内里的内容。``(?<=<(\w+)>)``指定了这样的**前缀**：被尖括号括起来的单词(比如可能是``<b>``)，然后是``.*``(任意的字符串),最后是一个**后缀**``(?=<\/\1>)``。注意后缀里的``\/``，它用到了前面提过的字符转义；`\1`则是一个反向引用，引用的正是捕获的第一组，前面的``(\w+)``匹配的内容，这样如果前缀实际上是<b>的话，后缀就是</b>了。整个表达式匹配的是<b>和</b>之间的内容(再次提醒，不包括前缀和后缀本身)。

> `(?<=<(\w+)>)`是一个零宽度正回顾后发断言，它匹配以`<(\w+)>`开头的后半部分
>
> `.*`匹配任意字符
>
> `(?=<\/\1>)`是一个零宽度正预测先行断言，它匹配以`<\/\1>`结尾的前半部分，其中`\/`是转义字符，`\1`是一个反向引用，引用的是`(\w)`里面的内容
>
> 例如：
>
> `<div>hello</span>` 匹配失败，因为属性标签div和span不一致
>
> `<div>hello</div>`会匹配`hello`

### 7.12 注释

小括号的另一种用途是通过语法``(?#comment)``来包含注释。例如：``2[0-4]\d(?#200-249)|25[0-5](?#250-255)|[01]?\d\d?(?#0-199)``。

要包含注释的话，最好是启用“忽略模式里的空白符”选项，这样在编写表达式时能任意的添加空格，Tab，换行，而实际使用时这些都将被忽略。启用这个选项后，在#后面到这一行结束的所有文本都将被当成注释忽略掉。例如，我们可以前面的一个表达式写成这样：

``` 
  (?<=    # 断言要匹配的文本的前缀
  <(\w+)> # 查找尖括号括起来的内容
  		  		# (即HTML/XML标签)
  )       # 前缀结束
  .*      # 匹配任意文本
  (?=     # 断言要匹配的文本的后缀
  <\/\1>  # 查找尖括号括起来的内容
  )       # 后缀结束
```

### 7.13 贪婪与懒惰

当正则表达式中包含能接受重复的限定符时，通常的行为是（在使整个表达式能得到匹配的前提下）匹配**尽可能多**的字符。以这个表达式为例：``a.*b`，它将会匹配最长的以`a`开始，以`b`结束的字符串。如果用它来搜索*aabab*的话，它会匹配整个字符串*aabab*。这被称为**贪婪**匹配。

有时，我们更需要**懒惰**匹配，也就是匹配**尽可能少**的字符。前面给出的限定符都可以被转化为懒惰匹配模式，只要在它后面加上一个问号`?`。这样`.*?`就意味着匹配任意数量的重复，但是在能使整个匹配成功的前提下使用最少的重复。现在看看懒惰版的例子吧：

`a.*?b`匹配最短的，以`a`开始，以`b`结束的字符串。如果把它应用于*aabab*的话，它会匹配*aab*（第一到第三个字符）和*ab*（第四到第五个字符）。

> 可以发现，由贪婪匹配改为懒惰匹配之后，匹配成功的字符串个数由1变为2。
>
> 另外注意，对于`aaaab`，它会成功匹配`aaaab`而不是`ab`

| 代码   | 说明                        |
| ------ | --------------------------- |
| *?     | 重复任意次，但尽可能少      |
| +?     | 重复1次或更多次，但尽可能少 |
| ??     | 重复0次或1次，但尽可能少    |
| {n,m}? | 重复[n,m]次，但尽可能少     |
| {n,}?  | 重复[n,∞)次，但尽可能少     |

### 7.14 处理选项

下面是.Net中常用的正则表达式选项：

| 名称                              | 说明                                                         |
| --------------------------------- | ------------------------------------------------------------ |
| IgnoreCase(忽略大小写)            | 匹配时不区分大小写。                                         |
| Multiline(多行模式)               | 更改^和$的含义，使它们分别在任意一行的行首和行尾匹配，而不仅仅在整个字符串的开头和结尾匹配。(在此模式下,$的精确含意是:匹配\n之前的位置以及字符串结束前的位置.) |
| Singleline(单行模式)              | 更改.的含义，使它与每一个字符匹配（包括换行符\n）。          |
| IgnorePatternWhitespace(忽略空白) | 忽略表达式中的非转义空白并启用由#标记的注释。                |
| ExplicitCapture(显式捕获)         | 仅捕获已被显式命名的组。                                     |

一个经常被问到的问题是：是不是只能同时使用多行模式和单行模式中的一种？答案是：不是。这两个选项之间没有任何关系，除了它们的名字比较相似（以至于让人感到疑惑）以外。事实上，为了避免混淆，在最新的 JavaScript 中，单行模式其实名叫 dotAll，意为点可以匹配所有字符，然而在指定该选项时，用的还是 Singleline 的首字母 s.

### 7.15 平衡组/递归匹配`[*]`

有时我们需要匹配像``(100*(50+15))``这样的可嵌套的层次性结构，这时简单地使用``\(.+\)``则只会匹配到最左边的左括号和最右边的右括号之间的内容(这里我们讨论的是贪婪模式，懒惰模式也有下面的问题)。假如原来的字符串里的左括号和右括号出现的次数不相等，比如``*(5/(3+2)))*``，那我们的匹配结果里两者的个数也不会相等。有没有办法在这样的字符串里匹配到最长的，配对的括号之间的内容呢？

这里需要用到以下的语法构造：

* `(?'group')` 把捕获的内容命名为group,并压入**堆栈(Stack)**
* `(?'-group')` 从堆栈上弹出最后压入堆栈的名为group的捕获内容，如果堆栈本来为空，则本分组的匹配失败
* `(?(group)yes|no)` 如果堆栈上存在以名为group的捕获内容的话，继续匹配yes部分的表达式，否则继续匹配no部分
* `(?!)` 零宽负向先行断言，由于没有后缀表达式，试图匹配总是失败

我们需要做的是每碰到了左括号，就在压入一个"Open",每碰到一个右括号，就弹出一个，到了最后就看看堆栈是否为空－－如果不为空那就证明左括号比右括号多，那匹配就应该失败。正则表达式引擎会进行回溯(放弃最前面或最后面的一些字符)，尽量使整个表达式得到匹配。

> 为了避免与组的括号混淆，将圆括号改为尖括号

``` JAVASCRIPT
<                   #最外层的左括号
  [^<>]*            #它后面非括号的内容
  (
      (
        (?'Open'<)  #左括号，压入"Open"
        [^<>]*      #左括号后面的内容
      )+
      (
        (?'-Open'>) #右括号，弹出一个"Open"
        [^<>]*      #右括号后面的内容
      )+
  )*
  (?(Open)(?!))     #最外层的右括号前检查
                    #若还有未弹出的"Open"
                    #则匹配失败
>                #最外层的右括号
```

平衡组的一个最常见的应用就是匹配HTML,下面这个例子可以匹配嵌套的``<div>``标签：

``` JAVASCRIPT
<div[^>]*>[^<>]*(((?'Open'<div[^>]*>)[^<>]*)+((?'-Open'</div>)[^<>]*)+)*(?(Open)(?!))</div>.
```

### 7.16 捕获组

正则表达式的捕获组（Capture Group）是一种用于提取和操作匹配文本的机制。它允许你将特定部分的匹配结果单独捕获并进行后续处理。

**定义**：捕获组是用括号 `()` 包围的部分。在正则表达式中，括号中的内容会被“捕获”，可以在匹配后单独提取。

**作用**：捕获组用于提取特定部分的字符串、分隔文本、或在后续处理（如替换或重构字符串）中引用捕获的内容。

例如：

``` python
# 指定了捕获组，all_matchs的返回结果为href和title的值
pattern = re.compile(
    r'<a.*?href="(.*?)".*?title="(.*?)".*?>'
)

# 没有指定捕获组，all_matchs的返回结果为所有的<a>标签内容
pattern = re.compile(
    r'<a.*?href=".*?".*?title=".*?".*?>'
)

all_matchs = pattern.findall(resp.text)
```

### 7.17 Python对正则表达式的支持

Python通过`re`模块来支持正则表达式相关操作，下面是`re`模块中的核心函数：

| 函数                                              | 说明                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| `compile(pattern, flags=0)`                       | 编译正则表达式并返回正则表达式对象                           |
| `match(pattern, string, flags=0)`                 | 用正则表达式匹配字符串，成功返回匹配对象，否则返回`None`（只要求字符串的开头部分匹配） |
| `search(pattern, string, flags=0)`                | 搜索字符串中第一次出现正则表达式的模块，成功返回匹配对象，否则返回`None` |
| `split(pattern, string, maxsplit=0, flags=0)`     | 用正则表达式指定的模式分隔符拆分字符串，返回列表             |
| `sub(pattern, replace, string, count=0, flags=0)` | 用指定的字符串替换源字符串中与正则表达式匹配的模式，可以使用count指定替换次数 |
| `fullmatch(pattern, string, flags=0)`             | 要求整个字符串都匹配                                         |
| `findall(pattern, string, flags=0)`               | 查找字符串所有与正则表达式匹配的模式，返回一个迭代器         |
| `purge()`                                         | 清楚隐式编译的正则表达式的缓存                               |
| `re.I`/`re.IGNORECASE`                            | 忽略大小写                                                   |
| `re.M`/`re.MULTILINE`                             | 多行匹配标记                                                 |
|                                                   |                                                              |

> 忽略大小写和多行匹配是通过flags参数指定的
>
> 如果某个正则表达式需要重复使用，那么先通过`compile`函数编译正则表达式并创建出正则表达式对象无疑是更为明智的选择。

在Python中指定pattern时，由于正则表达式的元字符很有很多转义符号，因此我们需要对转义字符进行转移，例如`\d`要写为`\\d`，就很冗杂，因此我们一般是通过**raw string**来指定pattern，无需转义。

例如：

``` python
import re

"""
要求：
用户名必须由字母、数字或下划线构成且长度在6~20个字符之间
QQ号是5~12的数字且首位不能为0
"""

def func1():
    username = input('pls input you name:')
    qq = input('pls input you qq:')

    # 别忘了加上零宽断言
    pattern_username = r'^[a-zA-Z0-9_]{6,20}$'
    pattern_qq = r'[1-9]\d{4,11}'

    match_username = re.compile(pattern_username)
    match_qq = re.compile(pattern_qq)

    m1 = re.match(pattern_username, username)
    m2 = re.match(pattern_qq, qq)

    if not m1:
        print('pls input valid username.')

    if not m2:
        print('pls input valid qq')

"""
要求：
替换字符串中的不良内容
"""

def func2():
    comment = 'oh, shit, fuck you! Son of a bitch!'
    purfied = re.sub('fuck|shit|bitch', '*', comment, flags=re.I)
    print('purfied comment: ', purfied)


"""
要求：
拆分长字符串
"""
def func3():
    poem = '窗前明月光，疑是地上霜。举头望明月，低头思故乡'
    poem_list = re.split(r'[，。？！]', poem)
    print(poem_list)

"""
要求：
从一串文字当中提取手机号码
"""
def func4():
    pattern = re.compile(r'(?<!\d)1[345678]\d{9}(?!\d)')
    sentence = ('重要的事情说8130123456789遍，我的手机号是13512346789这个靓号，'
                '不是15600998765，也是110或119，王大锤的手机号才是15600998765。')
    phone_list = re.findall(pattern, sentence)
    print(phone_list)

##### main ####
func4()
```

## 8. list[]

链表是可变数据类型，字符串是不可变数据类型，其区别在于，当我们针对字符串增删时，是创建了一个新的字符串，原字符串没有发生变化。注意这里说的字符串是不可变数据类型指的是不可以修改字符串的某个元素，例如`str[0]='1'`，但是我们可以这样修改：`str='1'+str[1:]`来实现同样的效果，其本质相当于重新创建了一个字符串，也就是说Python的字符串只是不支持原地修改，关于官方Docs的解释：

> 一个是性能：知道字符串是不可变的，意味着我们可以在创建时为它分配空间，并且存储需求是固定不变的。这也是元组和列表之间区别的原因之一。
>
> 另一个优点是，Python 中的字符串被视为与数字一样“基本”。 任何动作都不会将值 8 更改为其他值，在 Python 中，任何动作都不会将字符串 “8” 更改为其他值。

Python中的列表底层是一个可以动态扩容的数组（类似vector），可以随机访问，可以保存各种类型的数据

下标范围为 `[0,n-1]`，`[-n,-1]`

通过生成式创建列表，【强烈建议使用生成式语法来创建列表】，这是因为Python解释器的字节码指令中有专门针对生成式的指令（`LIST_APPEND`指令）；而`for`循环是通过方法调用（`LOAD_METHOD`,`CALL_METHOD`指令）的方式为列表添加元素，方法调用本身就是一个相对耗时的操作。

一种错误的创建的嵌套列表的方法：

``` python
matrix = [[0] * 3] * 5
print(matrix) 
# [[0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0], [0, 0, 0]]
matrix[0][0] = 3 
print(matrix)
# [[3, 0, 0], [3, 0, 0], [3, 0, 0], [3, 0, 0], [3, 0, 0]]
```

正确方法：

``` python
matrix = [[0] * 3 for _ in range(5)]
matrix[0][0] = 3
print(matrix)
```

错误的原因很简单，就是指针，先看下面例子：

``` python
list1 = [[0]]
list2 = list1 * 3
list1[0][0] = 1
print(list2)
# [[1], [1], [1]]
print(id(list1[0]))
print(id(list2[0]))
print(id(list2[1]))
print(id(list2[2]))
```

在这里我们明明修改的是list1，怎么list2变了？并且变的是所有元素

一句话解释清楚：**针对list的`*`操作符在实现上是复制了值的引用，而不是创建了一个新的对象，所以在上面例子中，list2是4个指向同一个list1对象的引用**

> 理解为指针就行了

所以，`*`操作符对于不可变对象很安全，但是对于可变对象，可能就不是你期望的结果了。

这里结合[这个可视化网站](https://pythontutor.com/visualize.html#mode=edit)会更清晰，最后，我们也可以通过``id()``打印对象的地址来进一步确认，毫无疑问，他们的地址是相同的。

那你可能会问，为什么下面的修改不行呢？

``` python
list1 = [0, "fuck"]
list2 = list1 * 3
list1[0] = 1
print(list2)
# [0, 'fuck', 0, 'fuck', 0, 'fuck']
```

这是因为，数字和字符串在list中就是以值的形式存在的，而嵌套list是作为指针指过去的，因此在复制嵌套list时，复制的是指针，在复制数字，字符串时，复制的就是值。

## 9.tuple()

tuple不同于list，它是不可变类型，这意味着tuple的变量一旦定义，其中的元素不可以再添加或删除，元素的值也不可以修改。定义tuple通常使用`()`字面量语法。

`()`表示空tuple，但如果tuple中只有一个元素，需要加上一个`,`，否则`()`就不是代表元组的字面量语法，而是改变算数优先级的圆括号。

tuple的应用场景：

1. 打包和解包:当我们把多个用逗号分隔的值赋给一个变量时，多个值会打包成一个元组类型；当我们把一个元组赋值给多个变量时，元组会解包成多个值然后分别赋给对应的变量。可以使用星号表达式来接受多个值，其类型为list，不过注意其职能出现一次。打包的元素也可以是一个字符串，``range()``等。
2. 交换多个变量的值：本质上也是通过打包操作进行的，但是对于两个和三个元素的交换，Python有专门的字节码指令`ROT_TWO`和`ROT_THREE`进行优化。

从功能上看，tuple就像是list的子集，那么tuple有什么list无法替代的好处呢？（其实主要是针对其不可变类型的特性）

1. 不可变类型更适合多线程环境，因为它降低了并发访问变量的同步化开销
2. 不可变类型在创建时间和占用空间上面都优于对应的可变类型

> 我们可以使用`sys`模块的`getsizeof()`来检查保存相同元素的tuple和list各自占用了多少内存空间。
>
> 可以使用`timeit`模块的`timeit`函数来检查创建保存相同元素的tuple和list各自花费的时间。
>
> ``` python
> from sys import getsizeof
> from timeit import timeit
> 
> n = 100000
> a = list(range(n))
> b = tuple(range(n))
> 
> print(getsizeof(a), getsizeof(b)) 
> # 800056 800040
> print(timeit('[1, 2, 3, 4, 5, 6, 7, 8, 9]')) 
> # 0.034143834
> print(timeit('(1, 2, 3, 4, 5, 6, 7, 8, 9)')) 
> # 0.0043259999999999965
> ```



最后，python中的list和tuple是可以相互转换的

## 10. string

计算机被设计之初是用来处理数值计算的，但发展至今，我们还需要处理文本数据，这就需要字符串了。

以三个引号开头的字符串可以拆行：

``` python
print("start--->")
s = '''
hello,
world!
fuck,you!
'''
print(s)
print("done---->")

# start--->
#
# hello,
# world!
# fuck,you!
#
# done---->
```

``` python
print("start--->")
s = '''hello,
world!
fuck,you!'''
print(s)
print("done---->")

# start--->
# hello,
# world!
# fuck,you!
# done---->
```

Python的字符串可以以`R`或`r`开头(raw)，这种字符串被称为原始字符串，意思是字符串中的每个字符都是它原本的含义，没有所谓的转义字符。

Python还允许在转义字符`\`后面跟一个八进制或者十六进制数来表示字符。例如`\141`和`\x61`都代表小写字母`a`，前者是八进制的表示法，后者是十六进制的表示法。另外一种表示字符的方式是在`\u`后面跟Unicode字符编码，例如`\u9a86\u660a`代表的是中文“骆昊”。

字符串常用方法：

* string.capitalize()：字符串首字母大写
* string.title()：每个单词首字母大写
* string.upper()
* string.lower()
* string.find(substring[, start, end])：找到返回下标，找不到返回-1
* string.index(substring[, start, end])：找到返回下标，找不到引发异常
* string.rfind()
* string.rindex()
* string.startwith()
* string.endwith()
* string.isdigit()：字符串是否由数字构成
* string.isalpha()：字符串是否由字母构成
* string.isalnum()：字符串是由由字母和数字构成
* string.center(width[, fillchar])：居中对齐
* string.ljust(width[, fillchar])：居左对齐
* string.rjust(width[, fillchar])：居右对齐
* string.zfill(width)：左侧补0，直到字符串长度为width
* string.encode(encoding=‘utf-8’,errors=‘strict’)：将字符串编码为字节串(bytes)
* string.decode(encoding=‘utf-8’,errors=‘strict’)：将bytes解码为string
* string.split(separator=‘ ’, maxsplit)：依据separator将字符串拆分为一个list，可以规定最大拆分次数
* string.join(iterable)：The `join()` method takes all items in an iterable and joins them into one string.
* string.replace(old, new, count)
* string.strip()：修剪，用来去掉string左右两端的空格
* string.lstrip()
* string.rstrip()

字符串格式化：

* `%`

* `f`

* `format`

  ``` python
  a = 123
  b = 3
  c = 3.1415926
  d = "hello"
  
  print('%d * %d = %d' % (a, b, a * b))
  print('{0} * {1} = {2}'.format(a, b, a * b))
  print(f'{a} * {b} = {a * b}')
  
  print('%d, %.2f, %s' % (a, c, d))
  print('{0:d}, {1:.2f}, {2:s}'.format(a, c, d))
  print(f'{a:d}, {c:.2f}, {d:s}')
  ```

## 11. set{}

注意与C++的set进行区分，C++的set使用红黑树实现，有序，但是在Python中，集合元素之间是无序的，Python的集合更像是C++的`unordered_set`，因此Python中的集合底层存储是哈希存储，故其取元素的时间复杂度为常数。也因此，集合中的元素必须是`hashable`类型（e.g.整数、浮点数、字符串、元组），通常不可变类型都是`hashable`类型，可变类型都不是`hashable`类型。

通过`{}`创建集合时，要确保集合中至少有一个元素，否则创建的是空字典而不是空集合，如果想要创建空集合，可以使用构造器`set()`，另外也可以通过生成式创建集合对象：

``` python
s1 = {"hello"}  # 1
print(s1) # {'hello'}
s1 = set("hello") # 2
print(s1) # {'e', 'h', 'l', 'o'}
s1 = set([1, 2, 2, 3, 4, 4]) # 3
print(s1) # {1, 2, 3, 4}
s1 = {num for num in range(20) if num % 3 == 0 or num % 5 == 0} # 4
print(s1) # {0, 3, 5, 6, 9, 10, 12, 15, 18}
```

>  注意第一种方式和第二种方式的不同

集合运算：

* `set1 & set2`，`set1.intersection(set2)`：交集
* `se1 | set2`，`set1.union(set2)`：并集
* `set1 - set2`，`set1.difference(set2)`：差集
* `set1 ^ set2`，`set1.symmetric_difference(set2)`：对称差，等价于：`(set1 | set2) - (set1 & set2)`



比较运算：

* `==`，`!=`：两个集合中的元素是否完全相同
* `set1 <= set2`，`set1.issubset(set2)`：set1 是否是 set2 的子集
* `set1 < set2`：set1 是否是 set2 的真子集
* `set1 >= set2`，`set1.isupperset(set2)`：set1 是否是 set2 的超集

其他方法：

* set.add(element)：添加一个元素
* set.update(set2)：添加一个集合中的所有元素
* set.discard(element)：删除指定元素，不存在不会报错
* set.remove(element)：不存在会抛出KeyError异常
* set.pop()：从集合中随机删除一个元素并返回该元素
* set.clear()
* set1.isdisjoint(set2)：判断两个集合是否存在相同元素，若不存在返回True

frozenset：不可变set，由于frozenset是不可变类型，能够计算出hash code，因此它可以作为set中的元素。它跟set的区别就像tuple和list的区别。

## 12. dict{:}

如何创建字典：

``` python
# 通过{}创建dict
person = {
    'name': 'Fiona', 'age': 20,
    'sex': 'women', 'country': 'USA'
}
print(person)

# 通过构造器创建dict
person = dict(name='Steve', age=23, sex='man', country='China')
print(person)

# 通过Python内置函数zip压缩两个序列并创建dict
items = dict(zip('ABCDE', '12345'))
print(items)
list1 = ('name', 'age', 'sex')
list2 = ('Fiona', 23, 'woman')
items = dict(zip(list1, list2))
print(items)

# 通过生成式语法创建dict
items = {x: x ** 3 for x in range(1, 6)}
print(items)
```

需要注意的是，`for-in`循环只是获取到了字典的key

字典的key必须是不可变类型

字典的方法：

* dict.get(key)：get value，return none if not exist
* dict.keys()：获取所有key
* dict.values()：获取所有value
* dict.items：获取所有键值对
* `for key, value in dict.items()`
* dict.pop(key)：若key不存在返回KeyError
* dict.popitems()：删除最后一个键值对并返回该值（添加顺序？）
* dict.setdefault(key，value)：若key存在，返回其值，不做修改；若key不存在，返回value，并添加直dict
* dict.update(dict)：有则修改，无则添加
* del dict[key]：key不存在抛出KeyError异常

## 13. 函数

### 13.1 一等公民

在 Python 中，函数是一等公民（first-class citizen），也就是地位非常高的意思，也即它具有和其他实体（变量、对象等）同样的地位和权力。体现在：函数可以作为参数传递、作为返回值返回、赋值给变量或存储在数据结构中。这样的特性提供了大量的灵活性和动态性，特别是在更高阶的函数编程中。

[closure，currying，](https://py.qizhen.xyz/first_class_func)



### 13.2 位置参数和命名关键字参数

在没有特殊处理的情况下，函数的参数都是位置参数，如果我们希望调用函数时调用者必须以`参数名=参数值`的方式传递参数，可以使用命名关键字参数（必须以命名的形式给我）。所谓命名关键字参数，就是写为`*`之后的参数，即，以`*`为分隔符（`*args`也可以），左侧是位置参数，右侧是命名关键字参数：

``` python
def func(x, y, z, *, a, b, c):
    print(f'keyword-only arguments: a = {a}, b = {b}, c = {c}')
    print(f'positional arguments: x = {x}, y = {y}, z = {z}')

func(11, 22, 33, a = 1, b = 2, c = 3)
```

位置参数必须出现在关键字参数之前，通过可变参数我们也能理解这样规定的意义

### 13.3 [可变参数和关键字参数](https://www.cnblogs.com/xiaojianliu/articles/10022029.html)

位置参数和命名关键字参数分别有其可变参数形式，其中称`*args`为可变参数，`**ksargs`为关键字参数

```PYTHON
def func(*args, **kwargs):
    print(type(args))   # tuple
    for arg in args:
        print(arg)
    print(type(kwargs)) # dict
    for key, value in kwargs.items():
        print(f'{key}:{value}')

func(1, 2, 3, a = 1, b = 2, c = 3)
```

> 上面这种写法可以接受任意多个，任意形式的参数，特别适用于在你不知道参数签名时

其中可变参数被处理为tuple，关键字参数被处理为dict。

注意我们上面提到的，`*`是位置参数和关键字参数的分隔符，因此当出现`*args`之后，它后面的参数都必须是以命名关键字参数形式传递：

``` python
def calc(*args, init_value, op, **kwargs):
    result = init_value
    for arg in args:
        if type(arg) in (int, float):
            result = op(result, arg)
    for value in kwargs.values():
        if type(value) in (int, float):
            result = op(result, value)
    return result

def add(a, b):
    return a + b

res = calc(1, 2, 3, init_value = 0, op = add, a = 1, b = 2, c = 3)
print(res)

# 如果我们写为以下形式：
res = calc(1, 2, 3, 0, add, a = 1, b = 2, c = 3)
# TypeError: calc() missing 2 required keyword-only arguments: 'init_value' and 'op'
```

注意，位置参数要出现在命名关键字参数和关键字参数之后，而命名关键字参数和关键字参数的位置并不重要，毕竟他们的形式是一样的。

> 位置参数：`func(a)`
>
> 命名关键字参数：`func(*, a)`
>
> 可变参数：`func(*args)`
>
> 关键字参数：`func(**kwargs)`

### 13.4 lambda

Python中的lambda函数只能有一行代码，其格式大致为：`lambda arguments: expression`，函数体通常是一个表达式，其结果就是返回值，不需要写`return`，例如：

``` python
nums = [1, 2, 3, 4, 5, 6, 7, 8]
# 去除所有偶数并求剩下元素的平方
new_nums = list(map(lambda x : x ** 2, filter(lambda x : x % 2 != 0, nums)))
print(new_nums)  # [1, 9, 25, 49]
```

### 13.5 装饰器

装饰器是Python中用一个函数装饰另外一个函数或类并为其提供额外功能的语法现象。装饰器本身是一个函数，它的参数是被装饰的函数或类，它的返回值是一个带有装饰功能的函数。

``` python
import random
import time

def download(filename):
    print(f'开始下载{filename}')
    time.sleep(random.randint(2, 3))
    print(f'{filename}下载完成')

# 装饰器函数
def record_time(func):
    # 定义一个带装饰功能的函数
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f'{func.__name__}执行时间：{end - start:.3f}s')
    # 返回带装饰功能的warpper函数
    return wrapper

# 手动得到装饰后的函数
download = record_time(download)
download('C++ Prime')
```

在Python中，使用装饰器有更为便捷的语法糖， 可以用`@装饰器函数`将装饰器直接放在被装饰的函数上，效果相同。

``` python
import random
import time


def record_time(func):
    # 定义一个带装饰功能的函数
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f'{func.__name__}执行时间：{end - start:.3f}s')
    # 返回带装饰功能的warpper函数
    return wrapper

@record_time # 自动装饰
def download(filename):
    print(f'开始下载{filename}')
    time.sleep(random.randint(2, 3))
    print(f'{filename}下载完成')


download('C++ Prime')
```

如果希望取消装饰器的作用，那么在定义装饰器函数的时候，需要做一些额外的工作。Python标准库`functools`模块的`wraps`函数也是一个装饰器，我们将它放在`wrapper`函数上，这个装饰器可以帮我们保留被装饰之前的函数，这样在需要取消装饰器时，可以通过被装饰函数的`__wrapped__`属性获得被装饰之前的函数。

``` python
import random
import time

from functools import wraps

def record_time(func):
    # 定义一个带装饰功能的函数
    @wraps(func)  # 该装饰器可以保留被装饰之前的函数
    def wrapper(*args, **kwargs):
        start = time.time()
        result = func(*args, **kwargs)
        end = time.time()
        print(f'{func.__name__}执行时间：{end - start:.3f}s')
    # 返回带装饰功能的warpper函数
    return wrapper

@record_time # 自动装饰
def download(filename):
    print(f'开始下载{filename}')
    time.sleep(random.randint(2, 3))
    print(f'{filename}下载完成')


download('C++ Prime')

# 取消装饰
download.__wrapped__('insight Java')
download = download.__wrapped__
download('Mysql')
```

最后就是，装饰器本身也可以参数化（层层装饰）。

## 14. module

​	 可以理解为C++的namespace，为了避免团队协作开发时命名冲突。Python中的每个模块就是一个文件，例如模块math所处文件就是`math.py`，当我们希望引入某个模块或者模块中的某个函数时，如下：

``` python
import math
from math import sqrt
import module as m1

math.sqrt()
sqrt()
m1.sqrt()
```

但是，如果我们从两个不同的模块中引入了同名的函数，则后引入的函数会覆盖掉先前的引入，为了解决这个问题，可以使用别名进行区分。

## 15. Standard Library

### 15.1 module

* random
* time
* math
* functools
* base64
* collections
* hashlib
* heapq
* itertools
* uuid
* os.path

### 15.2 function

* `abs`：整数和浮点数都可用

* `bin`：将整数转换成`0b`开头的二进制字符串

* `oct`：将整数转换成`0o`开头的二进制字符串

* `hex`：将整数转换成`0x`开头的十六进制字符串

* `chr`：将Unicode编码转换成对应的字符

* `ord`：将字符转换成对用的Unicode编码

* `input`：读取一行

* `open`：打开一个文件并返回文件对象

* `round`：返回指定精度的四舍五入值

* `id`：CPython中id()用于获取对象的内存地址，它是该对象的唯一标识符

* `map(function, iterable1, iterable2…)`：每次从所有iterable中取一个元素放入function得到结果，`Python3.x`中返回结果集迭代器，一般通过list的构造器构造为list，并不修改iterable本身

* `filter(function, iterable)``：用于过滤序列，过滤掉不符合条件的元素，返回由符合条件（function）元素组成的新列表，`Python3.x`中返回结果集迭代器，并不修改iterable本身

* `reduce(function, iterable…)`：有点像C++的accumulate，可以传入自定义的累计函数

* `all()`：传入的序列中所有布尔值都是True则返回True，否则返回False
* `enumerate(sequence, [start=0])`：用于将一个可遍历的数据对象(如列表、元组或字符串)组合为一个索引序列，这个索引序列的每个元素为一个tuple(idx, sequence[idx])
* `random`模块的`sample`和`choices`函数都可以实现随机抽样，`sample`实现无放回抽样，这意味着抽样取出的字符是不重复的；`choices`实现有放回抽样，这意味着可能会重复选中某些字符。这两个函数的第一个参数代表抽样的总体，而参数`k`代表抽样的数量。

## 16. 内置对象

我们可以通过`dir(__builtins__)`来查看Python的所有内置变量和内置函数：

``` python
obj = dir(__builtins__)
print(len(obj))
for item in obj:
    print(item)
```

### 16.1 常用魔法方法

（1）`__name__`：这个变量用于表示当前模块的名字。如果该模块被直接运行，`__name__`的值将是`__main__`；如果是被导入，值是该模块的名字。

（2）`__doc__`：存储了模块的文档字符串（三引号），如果没有文档字符串，则为`None`。如果有多个三引号，`__doc__`只会存储第一次出现的三引号内容。

（3）`__file__`：包含了当前文件的路径

（4）`__package__`：包含了当前模块所在的包

（5）`__builtins__`：提供了对所有内置函数和变量的访问，例如`print()`，`len()`等

（6）`__class__`：指向对象所属类的指针。对于类实例，`__class__`指向该实例所属的类；在class内部，`__class__`指向该类本身。

（7）`__bases__`：获取一个类的所有父类（注意不是祖先类），返回一个元组。

（8）`__slots__`：用来限制类的实例只能由固定的属性，从而不允许类对象在运行时添加类成员变量

（9）`__weakref__`：创建弱引用

（10）`__module__`：包含了该类或函数所在的模块名



## 17. 面对对象编程

> 面向对象编程：把一组数据和处理数据的方法组成**对象**，把行为相同的对象归纳为**类**，通过**封装**隐藏对象的内部细节，通过**继承**实现类的特化和泛化，通过**多态**实现基于对象类型的动态分配。
>
> 类是对象的蓝图，对象是类的实例，是可以接收消息的实体，对象的属性是对象的静态特征，对象的行为是对象的动态特征。

### 17.1 初始化

Python中成员变量无需单独声明，它直接在`__init__`方法中声明并定义，当我们通过构造器方法创建对象时，首先会在内存中获得该对象所需的内存空间，然后自动调用`__init_`方法，完成对内存的初始化操作，也就是把数据放到内存中。因此该方法又称为初始化方法：

``` python
class Student:
    # 声明了两个属性name和age
    def __init__(self, name, age):
        self.name = name
        self.age = age
        self.id = self.name + '2024'
```

> 注意属性并不需要出现在参数列表中，例如`self.id`

### 17.2 方法调用

Python的对象没有隐式的this指针，但类方法的第一个参数通常都是`self`，相当于this指针。不同于C++，在Python中，给对象发送消息（调用成员函数）有两种方法（这可能得益于Python中this指针`self`是显式指定的：

``` PYTHON
class Student:
    def study(self, course_name):
        print(f'学生正在学习{course_name}')
    def play(self):
        print(f'学生正在玩游戏')

stu1 = Student()
print(stu1)
print(type(stu1))

# （1）类.方法(对象,arguments)
Student.study(stu1, 'csapp')

# （2）对象.方法(arguments)
stu1.study('java')
```

> 注意不同于C++，如果我们要在一个方法属性中调用另外一个方法属性`func`，形式为`self.func()`而不是直接`func()`

### 17.3 魔术方法/魔法方法

Python中，以两个下划线`__`开头和结尾的方法通常都是由特殊用途和意义的方法，我们一般称之为**魔术方法**或**魔法方法**。

例如初始化对象的`__init__`，以及更改打印对象显示的内容的`__repr__`方法（初始时显示对象的地址），例如：

``` PYTHON
class Student:
    # 声明了两个属性name和age
    def __init__(self, name, age):
        self.name = name
        self.age = age
    def study(self, course_name):
        print(f'学生正在学习{course_name}')
    def play(self):
        print(f'学生正在玩游戏')
    # 修改print打印的内容
    def __repr__(self):
        return f'{self.name}: {self.age}'

stu = Student('Fiona', 23)
print(stu) # Fiona: 23
```

### 17.4 访问可见性

在Python中，说明属性的可见性的方法是在属性名前面添加下划线，不加下划线表示`public`，一个下划线表示`protected`，两个下划线表示`private`（魔方方法除外），下划线作为属性名的一部分。

``` PYTHON
class Student:
    # 声明了两个属性name和age
    def __init__(self, name, _sex, __age):
        self.name = name
        self._sex = _sex
        self.__age = __age
    def study(self, course_name):
        print(f'{self.name}正在学习{course_name}')

stu = Student('Fiona', 'woman' ,23)
print(stu.name) # Fiona
print(stu._sex) # woman
print(stu.__age) # AttributeError: 'Student' object has no attribute '__age'
```

虽然Python提供了说明属性的可见性的方法，但这只是一个**“君子约定”**，而不是语言层面上的机制，你总是有办法绕过这些不具备强制性的约定，典型的防君子不防小人。Python中有一句名言：“**We are all consenting adults here**”（大家都是成年人）。Python语言的设计者认为程序员要为自己的行为负责，而不是由Python语言本身来严格限制访问可见性，而大多数的程序员都认为**开放比封闭要好**，把对象的属性私有化并不是编程语言必须的东西，所以Python并没有从语法上做出最严格的限定。

以protected可见性为例，你可以在class外面直接访问和修改受保护的属性而不会报错。这样看来，python的protected属性和方法似乎很鸡肋，但我认为，这样很符合python一贯坚持的风格。以单下划线做前缀的属性和方法，被视为受保护的，python没有从解释器层面上做出强制性检查，它只是作为一个约定而存在，他们都应被视为API或任何Python代码的非公开部分，无论它是函数，方法还是数据成员。你可以选择遵守这个约定，也可以不遵守，由于不遵守此约定所造成的负面后果自然也需要你来承担。**因此，简而言之，protected成员是受保护的，你不应该直接去修改它**。

再例如private方法，虽然在class外直接访问private属性会报错，但Python并没有从语法上严格保证私有成员的私密性，它只是给米有成员换了一个名字来阻挠对他们的访问，即：`instance._class__variable`，例如：

``` PYTHON
class Student:
    # 声明了两个属性name和age
    def __init__(self, name, _sex, __age):
        self.name = name
        self._sex = _sex
        self.__age = __age
    def study(self, course_name):
        print(f'{self.name}正在学习{course_name}')
    def __talk(self):
        print(f'{self.name} is {self.__age} years old')

stu = Student('Fiona', 'woman' ,23)
stu._Student__talk()  # 访问私有方法
print(stu._Student__age) # 访问私有成员
```

### 17.5 属性装饰器

Python中可以通过属性装饰器为“私有”属性提供读取和修改的方法，之前我们提到过，装饰器通常会放在类、函数或方法的声明之前，通过一个`@`符号表示将装饰器应用于类、函数或方法。通过添加属性访问器和属性修改器，我们可以像访问普通属性一样访问私有成员。

``` python
class Student:
    def __init__(self, __name):
        self.__name = __name

    # 属性访问器
    @property
    def name(self):
        return self.__name

    # 属性修改器
    @name.setter
    def name(self, name):
        self.__name = name

# 访问时无需加上下划线
stu = Student('Alice')
print(stu.name)
stu.name = 'Bob'
print(stu.name)
```

### 17.6 动态属性

Python是一门动态语言，维基百科对动态语言的解释是：“**在运行时可以改变其结构的语言**，例如新的函数、对象、甚至代码可以被引进，已有的函数可以被删除或是其他结构上的变化。动态语言非常灵活，目前流行的Python和JavaScript都是动态语言，除此之外如PHP、Ruby等也都属于动态语言，而C、C++等语言则不属于动态语言”。

在Python中，我们可以动态为对象添加属性，这是Python作为动态类型语言的一项特权，代码如下所示。需要提醒大家的是，对象的方法其实本质上也是对象的属性，如果给对象发送一个无法接收的消息，引发的异常仍然是`AttributeError`。

``` PYTHON
class Student:
    def __init__(self, __name):
        self.__name = __name

    def study(self, course_name):
        print(f'{self.__name} is learning {course_name}')

stu = Student('Alice')
stu.sex = 'woman'
print(stu.sex) # woman

stu2 = Student('Bob')
print(stu2.sex) # AttributeError: 'Student' object has no attribute 'sex'
```

> 需要注意的是，动态添加的属性仅仅属于该对象，而不是属于该class

如果不希望在使用对象时动态的为对象添加属性，可以使用Python的`__slots__`魔法。对于`Student`类来说，可以在类中指定`__slots__ = ('name', 'age')`，这样`Student`类的对象只能有`name`和`age`属性，如果想动态添加其他属性将会引发异常，代码如下所示：

``` PYTHON
class Student:
    def __init__(self, __name):
        self.__name = __name

    def study(self, course_name):
        print(f'{self.__name} is learning {course_name}')

    __slots__ = ('__name')

stu = Student('Alice')
stu.sex = 'woman' # AttributeError: 'Student' object has no attribute 'sex'
```

### 17.7 静态方法和类方法

之前我们在类中定义的方法都是**对象方法**，换句话说这些方法都是对象可以接收的消息。除了对象方法之外，类中还可以有**静态方法**和**类方法**，这两类方法是发给类的消息，二者并没有实质性的区别。在面向对象的世界里，一切皆为对象，我们定义的每一个类其实也是一个对象，而静态方法和类方法就是发送给类对象的消息。

可以直接使用`类名.方法名`的方式来调用静态方法和类方法，二者的区别在于，类方法的第一个参数是类对象本身，而静态方法则没有这个参数（这点和C++一样）。

简单的总结一下，**对象方法、类方法、静态方法都可以通过`类名.方法名`的方式来调用，区别在于方法的第一个参数到底是普通对象还是类对象，还是没有接受消息的对象**。静态方法通常也可以直接写成一个独立的函数，因为它并没有跟特定的对象绑定。

``` PYTHON
class Triangle:
    def __init__(self, a, b, c):
        self.a = a
        self.b = b
        self.c = c

    def perimeter(self):
        return self.a + self.b + self.c

    def area(self):
        p = self.perimeter() / 2
        return (p * (p - self.a) * (p - self.b) * (p - self.c)) ** 0.5

    @classmethod
    def is_valid(self, a, b, c):
        return a + b > c and a + c > b and b + c > a

    @staticmethod
    def is_valid(a, b, c):
        return a + b > c and a + c > b and b + c > a

a, b, c = 1, 1, 100
if Triangle.is_valid(a, b, c) == False:
    print('Not valid triangle')
else:
    t = Triangle(a, b, c)
    print(t.area())
    print(t.perimeter())
```

### 17.8 继承和多态

继承的语法是在定义类的时候，在类名后的圆括号中指定当前类的父类。如果定义一个类的时候没有指定它的父类是谁，那么默认的父类是`object`类。`object`类是Python中的顶级类，这也就意味着所有的类都是它的子类，要么直接继承它，要么间接继承它。Python语言允许多重继承，也就是说一个类可以有一个或多个父类。在子类的初始化方法中，我们可以通过`super().__init__()`来调用父类初始化方法，`super`函数是Python内置函数中专门为获取当前对象的父类对象而设计的。

子类继承父类的方法后，还可以对方法进行重写（重新实现该方法），不同的子类可以对父类的同一个方法给出不同的实现版本，这样的方法在程序运行时就会表现出多态行为（调用相同的方法，做了不同的事情）。

``` python
class Person(object):
    def __init__(self, name):
        self.name = name
    def eat(self):
        print(f'person is eating')
    def sleep(self):
        print(f'person is sleeping')

class Student(Person):
    def __init__(self, name, id):
        super().__init__(name)
        self.id = id
    def eat(self):
        print(f'student is eating')
    def sleep(self):
        print(f'student is sleeping')
    def study(self):
        print(f'student is studiing')

p = Person('John')
p.eat()
p.sleep()

s = Student('Alice', "2024")
s.eat()
s.sleep()
s.study()
```

### 17.9 实例

``` PYTHON
from enum import Enum
import random

# 扑克牌花色
class Suit(Enum):
    SPADE, HEART, CLUB, DIAMOND = range(4)

class Card():
    def __init__(self, suit, face):
        self.suit = suit
        self.face = face

    def __repr__(self):
        suits = '♠♥♣♦'
        faces = ['', 'A', '2', '3', '4', '5', '6', '7', '8', '9', '10', 'J', 'Q', 'K']
        return f'{suits[self.suit.value]}{faces[self.face]}'

    def __lt__(self, other):
        if(self.face == other.face):
            return self.suit.value < other.suit.value
        return self.face < other.face

class Poker():
    def __init__(self):
        self.cards = [Card(suit, face) for suit in Suit for face in range(1, 14)]
        self.current = -1

    def shuffle(self):
        random.shuffle(self.cards)

    def has_next(self):
        return self.current < len(self.cards)

    def deal(self):
        if(self.has_next()):
            self.current += 1
            return self.cards[self.current]
        else:
            print('no card can be gotten!')

class Player():
    def __init__(self, name):
        self.name = name
        self.cards = []

    def get_one(self, card):
        self.cards.append(card)

    def arrange(self):
        self.cards.sort()


poker = Poker()
poker.shuffle()

players = [Player('Bob'), Player('Alice'), Player('Fiona'), Player('Steve')]

for _ in range(13):
    for player in players:
        card = poker.deal()
        print(card, poker.current)
        player.get_one(card)

for player in players:
    player.arrange()
    print(f'{player.name}', end=':')
    print(player.cards)
```

## 18 Python中变量的作用域

在函数内部，无法对与函数外部定义的变量直接进行修改，需要在当前函数内部再次声明：

* 如果该变量是全局变量，需要加`global`
* 如果该变量是局部变量，需要加`nolocal`

### 18.1 Local Scope

变量定义在函数内部，它们只能在该函数内部访问。这些变量称为局部变量，作用域仅限于定义它们的函数中。一旦函数执行完毕，局部变量就会被销毁。

这也解释了，为什么在class内部的函数中，调用成员函数需要用`self.arg`而不能像C一样直接使用`arg`，因为直接使用`arg`的话，CPython会把`arg`视为Local Argument。

### 18.2 Enclosing Scope

这是嵌套函数中的作用域，内部函数可以访问其外部函数的变量，但不能修改它们（除非使用 `nonlocal` 关键字）。外部函数的变量对内部函数是可见的，称为闭包作用域。

```python
def outer_function():
    x = 10  # 外部函数中的变量

    def inner_function():
        print(x)  # 可以访问外部函数的变量

    inner_function()

outer_function()
```

> 即，此时`outer_function（）`的作用域不是局部作用域了，而是闭包作用域。

### 18.3 Global Scope

变量定义在函数或类之外的代码块中，它们可以在整个程序中被访问。全局变量可以在任意位置使用，但如果在函数内部修改它们，需要使用 `global` 关键字。

### 18.4 Built-in Scope

Python 有一组内置的函数和变量，它们在所有作用域中都可以直接使用，比如 `print()`、`len()` 等。这些变量存储在 `builtins` 模块中。

```python
print("Hello, World!")  # print 是一个内置函数
```

### 18.5 LEGB规则

Python 的作用域查找顺序遵循 LEGB 规则：

1. **Local**：局部作用域
2. **Enclosing**：闭包函数的外层作用域
3. **Global**：全局作用域
4. **Built-in**：内置作用域

查找变量时，Python 按照这个顺序依次查找，直到找到为止。

你可以使用 `globals()` 和 `locals()` 函数来查看当前作用域内的变量。

### 18.6 非局部变量

非局部变量既不是global变量，也不是local变量。

它通常在外层函数的作用域当中被定义，但可以在内层函数中访问和修改。

下面是一个使用非局部变量的示例：

```PYTHON
def outer_function():
    x = 10  # 外层函数的变量
    
    def inner_function():
        nonlocal x  # 指定 x 是非局部变量
        x += 5  # 修改外层函数的变量
        print("Inner function:", x) 

    inner_function()  # 调用内部函数
    print("Outer function:", x)  # 输出修改后的变量

outer_function()
```

```SHELL
Inner function: 15
Outer function: 15
```

非局部变量常用于实现闭包（closure），允许内部函数在其外部环境中“记住”某些状态。

## 19. I/O

### 19.1 File System

**file system**使用文件和树形目录的抽象逻辑概念替代了硬盘、光盘、闪存等物理设备的数据块概念，用户使用file system来保存数据时，不辞关心数据实际保存在硬盘的那个数据块上，只需要记住这个文件的路径和文件名。再写入新数据之前，用户不必关心硬盘上的那个数据块没有被使用，硬盘上的存储空间管理（分配和释放）功能由file system自动完成，用户只需要记住数据被写入到那个文件中。

### 19.2 IO Type

* Text IO：produce `str` object
* Binary IO(Buffered IO)：produce `bytes` object
* Raw IO(unBuffered IO)：

``` python
f = open("myfile.txt", "r", encoding="utf-8")
f = open("myfile.jpg", "rb")
f = open("myfile.jpg", "rb", buffering=0)
```

也可以使用 [`str`](https://docs.python.org/zh-cn/3.7/library/stdtypes.html#str) 或 [bytes-like object](https://docs.python.org/zh-cn/3.7/glossary.html#term-bytes-like-object) 作为文件进行读取和写入。对于字符串， [`StringIO`](https://docs.python.org/zh-cn/3.7/library/io.html#io.StringIO) 可以像在文本模式下打开的文件一样使用。 [`BytesIO`](https://docs.python.org/zh-cn/3.7/library/io.html#io.BytesIO) 可以像以二进制模式打开的文件一样使用。两者都提供完整的随机读写功能。

### 19.3 API

`fileObject = open(file, mode='r', buffering=-1, encoding=None, errors=None, newline=None, closefd=True, opener=None)`

> **mode select:**
>
> * reading: `r`
> * writing –> truncate?
>   * yes: `w`
>   * no: `a`
> * reading and writing -> truncate?
>   * yes: `w+`
>   * no -> initial position?
>     * begin: `r+`
>     * end: `a+`

`close()`：该方法可以被多次调用，但只有第一次生效

`closed`：注意这是一个属性而不是一个方法

`fileno()`：返回流的fd（正数），如果存在

`flush()`：刷新流的写入缓冲区，这对只读和非阻塞流不起作用

`readline(size=-1)`：包括`\n`，可以通过size指定最大读取字节

`readlines(hint=-1)`读取所有行直到EOF，使用`for-in`也可以实现循环按行读取

> If given an optional parameter sizehint, it reads that many bytes from the file and enough more to complete a line, and returns the lines from that. 
>
> 关于换行符：
>
> 对于文本文件：
>
> 1. 指定字符数中间包含\n，则\n算做字符；
> 2. 如果\n在指定内容末尾，则**不计入字符**，算作换行符。
>
> 在二进制模式下，字符数量是以ASCII码对应的单字节为单位来计算的，不剔除换行符，字符‘\n’占用一个字节长度
>
> **并不推荐一下子读取文件的所有行（即读取整个文件），因为如果内容太大，可能会造成非常大的内存开销**

`write(str)`

`writelines(lines)`：将行列表写入流

`writable()`

`readable()`

`seek(offset, whence=SEEK_SET)`: 将流位置修改到给定的字节 *offset*,返回新的绝对位置。

> * `SEEK_SET` 或 `0` -- 流的开头（默认值）；*offset* 应为零或正值
> * `SEEK_CUR` or `1` -- 当前流位置；*offset* 可以为负值
> * `SEEK_END` or `2` -- 流的末尾；*offset* 通常为负值

`seekable()`

`truncate(size=none)`：将流的大小调整为给定的 *size* 个字节（如果未指定 *size* 则调整至当前位置）。当前的流位置不变。

`tell()`：返回文件当前位置

## 20. Exception

Python中的错误至少可以被分为两类：语法错误（解析错误）和异常

### 20.1 关键字

Python中于异常有关的关键词有5个，分别是：

* try：放置可能会出错的代码，异常处理程序不仅会处理在 *try 子句* 中立刻发生的异常，还会处理在 *try 子句* 中调用（包括间接调用）的函数
* except：捕获异常，基类异常对象会被其派生类异常捕获
* else：如果没有异常被捕获时执行
* finally：无论程序是否异常都会执行，甚至是调用了`sys`模块的`exit`函数终止Python程序，`finally`块中的代码仍然会被执行（因为`exit`函数的本质是引发了`SystemExit`异常），因此我们把`finally`代码块称为“总是执行代码块”，它最适合用来做释放外部资源的操作。
* raise：抛出异常对象，引发异常

### 20.2 异常的继承结构

``` python
BaseException
 +-- SystemExit
 +-- KeyboardInterrupt
 +-- GeneratorExit
 +-- Exception
      +-- StopIteration
      +-- StopAsyncIteration
      +-- ArithmeticError
      |    +-- FloatingPointError
      |    +-- OverflowError
      |    +-- ZeroDivisionError
      +-- AssertionError
      +-- AttributeError
      +-- BufferError
      +-- EOFError
      +-- ImportError
      |    +-- ModuleNotFoundError
      +-- LookupError
      |    +-- IndexError
      |    +-- KeyError
      +-- MemoryError
      +-- NameError
      |    +-- UnboundLocalError
      +-- OSError
      |    +-- BlockingIOError
      |    +-- ChildProcessError
      |    +-- ConnectionError
      |    |    +-- BrokenPipeError
      |    |    +-- ConnectionAbortedError
      |    |    +-- ConnectionRefusedError
      |    |    +-- ConnectionResetError
      |    +-- FileExistsError
      |    +-- FileNotFoundError
      |    +-- InterruptedError
      |    +-- IsADirectoryError
      |    +-- NotADirectoryError
      |    +-- PermissionError
      |    +-- ProcessLookupError
      |    +-- TimeoutError
      +-- ReferenceError
      +-- RuntimeError
      |    +-- NotImplementedError
      |    +-- RecursionError
      +-- SyntaxError
      |    +-- IndentationError
      |         +-- TabError
      +-- SystemError
      +-- TypeError
      +-- ValueError
      |    +-- UnicodeError
      |         +-- UnicodeDecodeError
      |         +-- UnicodeEncodeError
      |         +-- UnicodeTranslateError
      +-- Warning
           +-- DeprecationWarning
           +-- PendingDeprecationWarning
           +-- RuntimeWarning
           +-- SyntaxWarning
           +-- UserWarning
           +-- FutureWarning
           +-- ImportWarning
           +-- UnicodeWarning
           +-- BytesWarning
           +-- ResourceWarning
```

从上面的继承结构可以看出，Python中所有的异常都是`BaseException`的子类型，它有四个直接的子类，分别是：

* `SystemExit`：解释器请求退出
* `KeyboardInterrupt`：用户中断程序执行(`CTRL+C`)
* `GeneratorExit`：生成器发生异常通知退出
* `Exception`：常规异常类型，我们自定义的异常类型也因该直接或者间接继承自`Exception`类，并且应当以`Error`结尾，类似标准异常的命名。

> 异常类可以被定义成能做其他类所能做的任何事，但通常应当保持简单，它往往只提供一些属性，允许相应的异常处理程序提取有关错误的信息。

例如：

``` python
class InputError(Exception):
    '''自定义异常类型'''
    pass

def fac(num):
    if num < 0:
        raise InputError('只能计算非负整数的阶乘!')
    if num in (0, 1):
        return 1
    return num * fac(num - 1)

flag = True
while flag:
    n = int(input('n = '))
    try:
        print(f'{n}! = {fac(n)}')
    except InputError as e:
        print(str(e))
        flag = False
```

### 20.3 输出异常信息

通过 `str(error)` 打印异常的错误信息：

``` python
try:
    # 可能引发异常的代码
    a = 10 / 0
except Exception as e:
    # 打印异常信息
    print("发生异常：", str(e))
```

通过` traceback.print_exc()` 打印完整异常信息（异常类型，错误消息，堆栈跟踪信息）：

``` python
import traceback

try:
    # 可能引发异常的代码
    a = 10 / 0
except Exception as e:
    # 打印完整的异常信息
    traceback.print_exc()
```

### 20.4 异常链

如果一个未处理的异常发生在 [`except`](https://docs.python.org/zh-cn/3/reference/compound_stmts.html#except) 部分内，它将会有被处理的异常附加到它上面，并包括在错误信息中:

```python
>>> try:
...     open("database.sqlite")
... except OSError:
...     raise RuntimeError("unable to handle error")
...
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
FileNotFoundError: [Errno 2] No such file or directory: 'database.sqlite'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "<stdin>", line 4, in <module>
RuntimeError: unable to handle error
```

为了表明一个异常是另一个异常的直接后果， [`raise`](https://docs.python.org/zh-cn/3/reference/simple_stmts.html#raise) 语句允许一个可选的 [`from`](https://docs.python.org/zh-cn/3/reference/simple_stmts.html#raise) 子句:

```python
# exc must be exception instance or None.
raise RuntimeError from exc
```

转换异常时，这种方式很有用。例如：

\>>>

```python
>>> def func():
...     raise ConnectionError
...
>>> try:
...     func()
... except ConnectionError as exc:
...     raise RuntimeError('Failed to open database') from exc
...
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
  File "<stdin>", line 2, in func
ConnectionError

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File "<stdin>", line 4, in <module>
RuntimeError: Failed to open database
```

它还允许使用 `from None` 表达禁用自动异常链:

```python
>>> try:
...     open('database.sqlite')
... except OSError:
...     raise RuntimeError from None
...
Traceback (most recent call last):
  File "<stdin>", line 4, in <module>
RuntimeError
```

异常链机制详见 [内置异常](https://docs.python.org/zh-cn/3/library/exceptions.html#bltin-exceptions)。

### 20.5 Finally

如果存在 [`finally`](https://docs.python.org/zh-cn/3/reference/compound_stmts.html#finally) 子句，则 `finally` 子句是 [`try`](https://docs.python.org/zh-cn/3/reference/compound_stmts.html#try) 语句结束前执行的最后一项任务。不论 `try` 语句是否触发异常，都会执行 `finally` 子句。以下内容介绍了几种比较复杂的触发异常情景：

* 如果执行 `try` 子句期间触发了某个异常，则某个 [`except`](https://docs.python.org/zh-cn/3/reference/compound_stmts.html#except) 子句应处理该异常。如果该异常没有 `except` 子句处理，在 `finally` 子句执行后会被重新触发。
* `except` 或 `else` 子句执行期间也会触发异常。 同样，该异常会在 `finally` 子句执行之后被重新触发。
* 如果 `finally` 子句中包含 [`break`](https://docs.python.org/zh-cn/3/reference/simple_stmts.html#break)、[`continue`](https://docs.python.org/zh-cn/3/reference/simple_stmts.html#continue) 或 [`return`](https://docs.python.org/zh-cn/3/reference/simple_stmts.html#return) 等语句，异常将不会被重新引发。
* 如果执行 `try` 语句时遇到 [`break`](https://docs.python.org/zh-cn/3/reference/simple_stmts.html#break),、[`continue`](https://docs.python.org/zh-cn/3/reference/simple_stmts.html#continue) 或 [`return`](https://docs.python.org/zh-cn/3/reference/simple_stmts.html#return) 语句，则 `finally` 子句在执行 `break`、`continue` 或 `return` 语句之前执行。
* 如果 `finally` 子句中包含 `return` 语句，则返回值来自 `finally` 子句的某个 `return` 语句的返回值，而不是来自 `try` 子句的 `return` 语句的返回值。

### 20.6 用注释细化异常情况

当一个异常被创建以引发时，它通常被初始化为描述所发生错误的信息。在有些情况下，在异常被捕获后添加信息是很有用的。为了这个目的，异常有一个 `add_note(note)` 方法接受一个字符串，并将其添加到异常的注释列表。标准的回溯在异常之后按照它们被添加的顺序呈现包括所有的注释。

```python
try:
...     raise TypeError('bad type')
... except Exception as e:
...     e.add_note('Add some information')
...     e.add_note('Add some more information')
...     raise
...
Traceback (most recent call last):
  File "<stdin>", line 2, in <module>
TypeError: bad type
Add some information
Add some more information
>>>
```

### 20.7 引发并处理多个不相关的异常

在有些情况下，有必要报告几个已经发生的异常。这通常是在并发框架中当几个任务并行失败时的情况，但也有其他的用例，有时需要是继续执行并收集多个错误而不是引发第一个异常。

内置的 [`ExceptionGroup`](https://docs.python.org/zh-cn/3/library/exceptions.html#ExceptionGroup) 打包了一个异常实例的列表，这样它们就可以一起被引发。它本身就是一个异常，所以它可以像其他异常一样被捕获。

> `` Exception BaseExceptionGroup(msg, excs)``

```python
def f():
...     excs = [OSError('error 1'), SystemError('error 2')]
...     raise ExceptionGroup('there were problems', excs)
...
>>> f()
  + Exception Group Traceback (most recent call last):
  |   File "<stdin>", line 1, in <module>
  |   File "<stdin>", line 3, in f
  | ExceptionGroup: there were problems
  +-+---------------- 1 ----------------
    | OSError: error 1
    +---------------- 2 ----------------
    | SystemError: error 2
    +------------------------------------
>>> try:
...     f()
... except Exception as e:
...     print(f'caught {type(e)}: e')
...
caught <class 'ExceptionGroup'>: e
```

通过使用 `except*` 代替 `except` ，我们可以有选择地只处理组中符合某种类型的异常。在下面的例子中，显示了一个嵌套的异常组，每个 `except*` 子句都从组中提取了某种类型的异常，而让所有其他的异常传播到其他子句，并最终被重新引发。

```python
def f():
...     raise ExceptionGroup(
...         "group1",
...         [
...             OSError(1),
...             SystemError(2),
...             ExceptionGroup(
...                 "group2",
...                 [
...                     OSError(3),
...                     RecursionError(4)
...                 ]
...             )
...         ]
...     )
...
>>> try:
...     f()
... except* OSError as e:
...     print("There were OSErrors")
... except* SystemError as e:
...     print("There were SystemErrors")
...
There were OSErrors
There were SystemErrors
  + Exception Group Traceback (most recent call last):
  |   File "<stdin>", line 2, in <module>
  |   File "<stdin>", line 2, in f
  | ExceptionGroup: group1
  +-+---------------- 1 ----------------
    | ExceptionGroup: group2
    +-+---------------- 1 ----------------
      | RecursionError: 4
      +------------------------------------
```

注意，嵌套在一个异常组中的异常必须是实例，而不是类型。这是因为在实践中，这些异常通常是那些已经被程序提出并捕获的异常，而不是你自己凭空raise出来的异常。

### 20.8 异常使用规范

* `try`后面的`except`语句不是必须的，`finally`语句也不是必须的，但是二者必须要有一个；
* `except`语句可以有一个或多个，多个`except`会按照书写的顺序依次匹配指定的异常，如果异常已经处理就不会再进入后续的`except`语句；
* `except`语句中还可以通过元组同时指定多个异常类型进行捕获；`except`语句后面如果不指定异常类型，则默认捕获所有异常；
* 捕获异常后可以使用`raise`要再次抛出，但是不建议捕获并抛出同一个异常；
* 不建议在不清楚逻辑的情况下捕获所有异常，这可能会掩盖程序中严重的问题；
* **不要使用异常机制来处理正常业务逻辑或控制程序流程**，简单的说就是不要滥用异常机制，这是初学者常犯的错误。

## 21. Python读写JSON文件

### 21.1 JSON

通过上面的讲解，我们已经知道如何将文本数据和二进制数据保存到文件中，那么这里还有一个问题，如果希望把一个列表或者一个字典中的数据保存到文件中又该怎么做呢？在Python中，我们可以将程序中的数据以JSON格式进行保存。

JSON是“JavaScript Object Notation”的缩写，它本来是JavaScript语言中创建对象的一种字面量语法，现在已经被广泛的应用于==跨语言跨平台的数据交换==。

使用JSON的原因非常简单，因为它结构紧凑而且是纯文本，任何操作系统和编程语言都能处理纯文本，这就是**实现跨语言跨平台数据交换**的前提条件。目前JSON基本上已经取代了XML（可扩展标记语言）作为**异构系统间交换数据的事实标准。可以在[JSON的官方网站](https://www.json.org/json-zh.html)找到更多关于JSON的知识，这个网站还提供了每种语言处理JSON数据格式可以使用的工具或三方库。**

> 通过F12打开的浏览器控制台就是Javascritpt交互环境

### 21.2 序列化和反序列化

[维基百科](https://zh.wikipedia.org/)上的解释是：“序列化（serialization）在计算机科学的数据处理中，是指将数据结构或对象状态转换为**可以存储或传输的形式**，这样在需要的时候能够恢复到原先的状态，而且通过序列化的数据重新获取字节时，可以利用这些字节来产生原始对象的副本（拷贝）。与这个过程相反的动作，即从一系列字节中提取数据结构的操作，就是反序列化（deserialization）”。

### 21.3 数据转换

从格式上看，JavaScript的对象和Python的dict格式很相似，它们通过键获取值的方式都是一样的：`obj['name']`，而Python中也通过名为`json`的模块提供了dict与JSON双向转换的支持。

`json`模块有四个比较重要的函数，分别是：

* `dump` - 将Python对象按照JSON格式序列化到文件中
* `load` - 将文件中的JSON数据反序列化成对象
* `dumps` - 将Python对象处理成JSON格式的字符串
* `loads` - 将字符串的内容反序列化成Python对象

> dump会把dict中的中文转换为 Unicode编码

Python标准库中的`json`模块在数据序列化和反序列化时性能并不是非常理想，为了解决这个问题，可以使用三方库`ujson`来替换`json`。

### 21.4 通过网络API获取数据

如果想在我们自己的程序中显示天气、路况、航班等信息，这些信息我们自己没有能力提供，所以必须使用网络数据服务。目前绝大多数的网络数据服务（或称之为网络API）都是基于[HTTP](https://zh.wikipedia.org/wiki/超文本传输协议)或HTTPS提供JSON格式的数据，我们可以通过Python程序发送HTTP请求给指定的URL（统一资源定位符），这个URL就是所谓的网络API，如果请求成功，它会返回HTTP响应，而HTTP响应的消息体中就有我们需要的JSON格式的数据。关于HTTP的相关知识，可以看看阮一峰的[《HTTP协议入门》](http://www.ruanyifeng.com/blog/2016/08/http.html)一文。

## 22. Python读写CSV文件

### 22.1 CSV

CSV（Comma Separate Values），全称逗号分隔值，是一种简单通用的格式，被广泛的应用于应用程序（数据库、电子表格等）数据的导入和导出以及异构系统之间的数据交换。因为CSV是纯文本文件，不管是什么操作系统和编程语言都是可以处理纯文本的，而且很多编程语言中都提供了对读写CSV文件的支持，因此CSV格式在数据处理和数据科学中被广泛应用。

CSV文件有以下特点：

1. 纯文本，使用某种字符集（如[ASCII](https://zh.wikipedia.org/wiki/ASCII)、[Unicode](https://zh.wikipedia.org/wiki/Unicode)、[GB2312](https://zh.wikipedia.org/wiki/GB2312)）等）；
2. 由一条条的记录组成（典型的是每行一条记录）；
3. 每条记录被分隔符（如逗号、分号、制表符等）分隔为字段（列）；
4. 每条记录都有同样的字段序列。

CSV文件可以使用文本编辑器或类似于Excel电子表格这类工具打开和编辑，当使用Excel这类电子表格打开CSV文件时，你甚至感觉不到CSV和Excel文件的区别。很多数据库系统都支持将数据导出到CSV文件中，当然也支持从CSV文件中读入数据保存到数据库中，这些内容并不是现在要讨论的重点。

### 22.2 读写CSV文件

[官方文档](https://docs.python.org/zh-cn/3.8/library/csv.html)

如果我们使用 `csv` 模块读写CSV文件，那么Python对CSV文件的读写要通过**可迭代对象**进行，这个可迭代对象就是 `csv` 模块中函数 `reader()`返回的`csvreader`或者函数`writer()`返回的``csvwriter``。通过可迭代对象`csvwriter`的`writerow`和`writerows`便可以实现单行或者多行的写入操作。

> `csv.reader(csvfile, dialect='excel', fmtparams)`
>
> `csv.writer(csvfile, dialect='excel', fmtparams)`
>
> `dialect`参数表示CSV文件的方言，默认是`excel`
>
> 还可以通过`delimiter`、`quotechar`、`quoting`参数来指定分隔符（默认是逗号）、包围值的字符（默认是双引号）以及包围的方式。

从CSV文件中读取数据：

``` python
import csv

with open('scores.csv', 'r') as file:
    # 创建可迭代对象reader
    reader = csv.reader(file, delimiter=',')
    # 遍历每一行
    for data_list in reader:
        # 添加行号
        print(reader.line_num, end='\t')
        for elem in data_list:
            print(elem, end='\t')
        print()
```

往CSV文件中写入数据：

``` python
import csv
import random

# 如果不添加 newline=''
# 往csv文件写入时会有多余的空行
# 该属性指定了文件的换行符格式
with open('scores.csv', 'w', newline='') as file:
    writer = csv.writer(file)
    writer.writerow(['姓名','语文','数学','英语'])
    names = ['李白','杜甫','李清照','王安石']
    for name in names:
        scores = [random.randrange(50, 101) for _ in range(3)]
        scores.insert(0, name)
        writer.writerow(scores)

```

> 为什么Python在不指定 `newline=''` 的情况下往 csv 文件写入数据会有多余的空行？
>
> **没有指定 `newline=''` 的情况**：
>
> * `csv.writer` 在写入时加了一个换行符（例如 `\n`）。
> * `open()` 又在每个写入操作后添加另一个换行符（在 Windows 上是 `\r\n`），因此最终每一行后面有两个换行符，导致了文件中每行之间多一个空行。
>
> **指定 `newline=''` 后的情况**：
>
> * `open()` 不再自动添加换行符，`csv.writer` 处理的换行符成为唯一的换行符，因此文件格式正确，没有多余的空行。

### 22.3 Pandas Library

将来如果大家使用Python做数据分析，很有可能会用到名为`pandas`的三方库，它是Python数据分析的神器之一。`pandas`中封装了名为`read_csv`和`to_csv`的函数用来读写CSV文件，其中`read_CSV`会将读取到的数据变成一个`DataFrame`对象，而`DataFrame`就是`pandas`库中最重要的类型，它封装了一系列用于数据处理的方法（清洗、转换、聚合等）；而`to_csv`会将`DataFrame`对象中的数据写入CSV文件，完成数据的持久化。`read_csv`函数和`to_csv`函数远远比原生的`csvreader`和`csvwriter`强大。

关于Excel的结构，一个Excel文件（工作簿）里面会有多个sheet表（工作表）。

## 23. Python读写Excel文件

Python操作Excel需要三方库的支持，如果要兼容Excel 2007以前的版本，也就是`xls`格式的Excel文件，可以使用三方库`xlrd`（excel_read）和`xlwt`（excel_write），前者用于读Excel文件，后者用于写Excel文件。如果使用较新版本的Excel，即操作`xlsx`格式的Excel文件，可以使用`openpyxl`库，当然这个库不仅仅可以操作Excel，还可以操作其他基于Office Open XML的电子表格文件。

### 23.1 openpyxl

`openpyxl`的优点在于，当我们打开一个Excel文件后，既可以对它进行读操作，又可以对它进行写操作，而且在操作的便捷性上是优于`xlwt`和`xlrd`的。此外，如果要进行样式编辑和公式计算，使用`openpyxl`也更为简单，而且`openpyxl`还支持数据透视和插入图表等操作，功能非常强大。有一点需要再次强调，**`openpyxl`并不支持操作Office 2007以前版本的Excel文件**。

读Excel文件：

``` python
import openpyxl

# 加载一个工作簿(WorkBook)，即Excel文件
wb = openpyxl.load_workbook('njust.xlsx')
# 获取工作簿的名字：注意这个名字并不是Excel文件名，而是Excel文件中表的名字
    # 而由于一个Excel文件可能包含多个表，因此是names
print('sheetnames:', wb.sheetnames)
# 获取工作表
sheet = wb.worksheets[1]
# 获取单元格的范围
    # 返回的结果是 左上坐标:右下坐标
print(sheet.dimensions)
# 获取行数和列数
print(sheet.max_row, sheet.max_column)
# 获取指定单元格的值
print(sheet.cell(2, 3).value)
print(sheet['A2'].value)
print(sheet['C3'].value)
# 获取多个单元格（嵌套元组）
print(sheet['A1:G1'])
# 读取所有单元格的数据
	# 注意下标从1开始
    # 一般从第2行开始读取数据，因为第一行一般都是标题部分
for row in range(2, sheet.max_row + 1):
    for col in range(2, sheet.max_column + 1):
        value = sheet.cell(row, col).value
        print(value, end='\t')
    print()
```

需要提醒大家一点，`openpyxl`获取指定的单元格有两种方式，一种是通过`cell`方法，需要注意，该方法的行索引和列索引都是从`1`开始的，这是为了照顾用惯了Excel的人的习惯；另一种是通过索引运算，通过指定单元格的坐标，例如`C3`、`G255`，也可以取得对应的单元格，再通过单元格对象的`value`属性，就可以获取到单元格的值。通过上面的代码，相信大家还注意到了，可以通过类似`sheet['A2:C5']`或`sheet['A2':'C5']`这样的切片操作获取多个单元格，该操作将返回嵌套的元组，相当于获取到了多行多列。

写Excel文件：

``` python
import random
import openpyxl

# 创建工作簿
wb = openpyxl.Workbook()

# 添加工作表
sheet = wb.active
sheet.title = 'scores'

# 写入标题行
titles = ('Name', 'Chinese', 'Math', 'English')
for col_index, title in enumerate(titles):
    # cell() 既可以读取数据也可以设置数据
    sheet.cell(1, col_index + 1, title)

# 写入数据
names = ('Bob', 'Lip', 'Alice')
for row_index, name in enumerate(names):
    sheet.cell(row_index + 2, 1, name)
    for col_index in range(2, len(titles) + 1):
        sheet.cell(row_index + 2, col_index, random.randrange(50, 101))

# 保存工作簿
wb.save('tmp.xlsx')

########################################################

import openpyxl

# load工作簿
wb = openpyxl.load_workbook('tmp.xlsx')

# 添加新sheet
sheet = wb.create_sheet('new_sheet')

# 保存工作簿
wb.save('new_tmp.xlsx')

# 关闭工作簿
wb.close()
```

另外还可以调整单元格的样式，进行公式计算，生成统计图表等，这里不再介绍，具体请参考[官方文档](https://openpyxl.readthedocs.io/en/stable/index.html)

### 23.2 Pandas

掌握了Python程序操作Excel的方法，可以解决日常办公中很多繁琐的处理Excel电子表格工作，最常见就是将多个数据格式相同的Excel文件合并到一个文件以及从多个Excel文件或表单中提取指定的数据。如果数据体量较大或者处理数据的方式比较复杂，我们还是推荐大家使用Python数据分析神器之一的`pandas`库。

## 24. Python操作Word和PPT文件

在日常工作中，有很多简单重复的劳动其实完全可以交给Python程序，比如根据样板文件（模板文件）批量的生成很多个Word文件或PowerPoint文件。在Python中，可以使用名为`python-docx` 的三方库来操作Word，可以使用名为`python-pptx`的三方库来生成PowerPoint。

### 24.1 批量制作Word文件

[官方文档](https://python-docx.readthedocs.io/en/latest/)

.docx 文件结构在 python-docx 中的三种类型：

* Document 对象表示整个文档；
* Paragrapha 对象标识段落（在输入文档，每一次回车产生新段落）；
* Run 对象标识相同样式的文本延续。（可以理解为一个paragrpha由多个run构成）

Document 对象包含一个 Paragrapha 对象的列表，Paragraph 对象包含一个 Run 对象的列表。

现在假设我们现在要为一万个学生制作奖状，每个学生有{名字，班级，n等奖}这三项不同的信息，我们可以设计Word模板如下，通过占位符`{key}`表示未确定值，然后在Python当中替换占位符即可。

模板如下：

``` shell
奖状
亲爱的小学{class}班{name}同学，为了祝贺你在本次考试中的优异成绩，特此颁发{level}等奖状予你，以资奖励！
此致！
敬礼！
```

批量修改模板的代码：

``` python
from docx import Document
from docx.document import Document as Doc

from docx import Document
from docx.shared import Cm, Pt
from docx.document import Document as Doc

# 将学生信息以字典的形式保存在列表中
students = [
    {
        'name': '李白',
        'class': '4',
        'level': '三'
     },
    {
        'name': '杜甫',
        'class': '4',
        'level': '二'
    },
    {
        'name': '刘备',
        'class': '3',
        'level': '一'
    },
]

doc = Document('certify_template.docx')
for no, paragraph in enumerate(doc.paragraphs):
    print(no, ":", end='\t')
    for p in paragraph.runs:
        print(p.text, '*')

# 对列表进行循环，批量制作word文件
for student in students:
    doc = Document('certify_template.docx')
    # 遍历所有段落寻找占位符
    for p in doc.paragraphs:
        if '{' not in p.text:
            continue
        # 不能直接修改段落内容，否则会丢失样式
        for run in p.runs:
            # 一个run里面可能有多个占位符
            while '{' in run.text:
                # 将占位符替换为实际内容
                start, end = run.text.find('{'), run.text.find('}')
                key, place_holder = run.text[start + 1:end], run.text[start:end + 1]
                print("key: ", key)
                run.text = run.text.replace(place_holder, student[key])
    # 每个人对应保存一份word文件
    doc.save(f'student{student['name']}.docx')

```

### 24.2 生成PowerPoint

[官方文档](https://python-pptx.readthedocs.io/en/latest/)

## 25. Python操作PDF文件

>  PDF：Portable Document Format（便携式文件格式）

在日常开发工作中，最容易遇到的就是从PDF中读取文本内容以及用已有的内容生成PDF文档这两个任务。

### 25.1 读取PDF

在Python中，可以使用名为`PyPDF2`的三方库来读取PDF文件，`PyPDF2`没有办法从PDF文档中提取图像、图表或其他媒体，但它可以提取文本，并将其返回为Python字符串。

``` python
import PyPDF2

reader = PyPDF2.PdfReader('test.pdf')
for page in reader.pages:
    print(page.extract_text())
```

当然，`PyPDF2`并不是什么样的PDF文档都能提取出文字来，这个问题就我所知并没有什么特别好的解决方法，尤其是在提取中文的时候。网上也有很多讲解从PDF中提取文字的文章，推荐大家自行阅读[《三大神器助力Python提取pdf文档信息》](https://cloud.tencent.com/developer/article/1395339)一文进行了解。

### 25.2 加密PDF

使用`PyPDF2`中的`PdfFileWrite`对象可以为PDF文档加密，如果需要给一系列的PDF文档设置统一的访问口令，使用Python程序来处理就会非常的方便。

```python
import PyPDF2

reader = PyPDF2.PdfReader('certify.pdf')
writer = PyPDF2.PdfWriter()

# 将原pdf的所有页写入writer
for page in reader.pages:
    writer.add_page(page)

# 加密
writer.encrypt('root')

# 将writer中的所有页写入一个新pdf文件
with open('tmp.pdf', 'wb') as f:
    writer.write(f)
```

### 25.3 添加水印

pdf文件添加水印的思路就是合并两个页，原pdf页和水印页

``` python
import PyPDF2

reader = PyPDF2.PdfReader('certify.pdf')
writer = PyPDF2.PdfWriter()

watermark  = PyPDF2.PdfReader('vimqrc.pdf')
watermark_page = watermark.pages[0]

# 添加水印
for page in reader.pages:
    page.merge_page(watermark_page)
    writer.add_page(page)

with open('tmp2.pdf', 'wb') as f:
    writer.write(f)
```

### 25.4 旋转和叠加页面

``` python
import PyPDF2

reader = PyPDF2.PdfReader('certify.pdf')
writer = PyPDF2.PdfWriter()

for no, page in enumerate(reader.pages):
    if no % 2 == 0:
        new_page = page.rotate(90)
    else:
        new_page = page.rotate(-90)
    writer.add_page(new_page)

with open('tmp3.pdf', 'wb') as f:
    writer.write(f)
```

### 25.5 创建PDF文件

创建PDF文档需要三方库`reportlab`的支持

## 26. Python处理图像

### 26.1 图像的基本概念

* 颜色：在计算机系统中，我们通常会将一个元素表示为一个RGB值或RGBA值，其中A表示Alpha通道，它决定了透过这个颜色的像素，也就是透明度。
* 像素：图像的最小单位，不可分割，像素是一个相对单位，不同设备上1px(pixel)可能不同

### 26.2 Pillow

Pillow(Python Image Library)是由从著名的Python图像处理库PIL发展出来的一个分支，通过Pillow可以实现图像压缩和图像处理等各种操作。

Pillow中最为重要的是`Image`类，可以通过`Image`模块的`open`函数来读取图像并获得`Image`类型的对象。

主要功能有：

* 创建图像
* 读取和显示图像
* 裁剪和缩放图像
* 粘贴图像
* 旋转和反转
* 操作像素
* 滤镜效果
* 绘图

Pillow中还有一个名为`ImageDraw`的模块，该模块的`Draw`函数会返回一个`ImageDraw`对象，通过`ImageDraw`对象的方法便可以在图像上绘制出圆弧、线条、矩形、椭圆、多边形等形状，以及添加文字。

### 26.3 OpenCV

使用Python语言做开发，除了可以用Pillow来处理图像外，还可以使用更为强大的OpenCV库来完成图形图像的处理，OpenCV（**Open** Source **C**omputer **V**ision Library）是一个跨平台的计算机视觉库，可以用来开发实时图像处理、计算机视觉和模式识别程序。在我们的日常工作中，有很多繁琐乏味的任务其实都可以通过Python程序来处理，编程的目的就是让计算机帮助我们解决问题，减少重复乏味的劳动。通过本章节的学习，相信大家已经感受到了使用Python程序绘图P图的乐趣，其实Python能做的事情还远不止这些，继续你的学习吧。

 ## 27. 数据采集概述

### 27.1 item

* crawler：爬虫，又称为网络蜘蛛（spider）
* ICP：Internet Content Provider
* HTTP：HyperText Transfer Protocol
* HTML：HyperText Mark Language

### 27.2 Robots协议

网络爬虫排除协议，大多数网站都会定义`robots.txt`文件，这是一个君子协议，并不是所有爬虫都必须遵守的游戏规则。

### 27.3 HTTP

#### 27.3.1 reference

* [《HTTP 协议入门》](http://www.ruanyifeng.com/blog/2016/08/http.html)
* [《互联网协议入门》](http://www.ruanyifeng.com/blog/2012/05/internet_protocol_suite_part_i.html)
* [《图解 HTTPS 协议》](http://www.ruanyifeng.com/blog/2014/09/illustration-ssl.html)

#### 27.3.2 HTTP请求

HTTP REQUEST 的协议头通常是由以下四部分组成：

* 请求行
  * 方法
  * URL
  * HTTP版本
* 请求头：若干键值对，包含了客户端环境信息，客户端支持的压缩类型等
* 空行：请求头和消息体之间的分隔符，表示请求头的结束
* 消息体（可选）：包含要发送给服务器的数据，通常为JSON格式

例如：

```HTTP
GET /index.html HTTP/1.1
Host: www.example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:91.0) Gecko/20100101 Firefox/91.0
Accept:text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,*/*;q=0.8
Accept-Encoding: gzip, deflate
Connection: keep-alive
```

HTTP协议的八种请求类型：

*  **OPTIONS**：返回服务器针对特定资源所支持的HTTP请求方法。也可以利用向Web服务器发送'*'的请求来测试服务器的功能性。
*  **HEAD**：向服务器索要与GET请求相一致的响应，只不过响应体将不会被返回。这一方法可以在不必传输整个响应内容的情况下，就可以获取包含在响应消息头中的元信息。
*  **GET**：向特定的资源发出请求。
*  **POST**：向指定资源提交数据进行处理请求（例如提交表单或者上传文件）。数据被包含在请求体中。POST请求可能会导致新的资源的创建和/或已有资源的修改。
*  **PUT**：向指定资源位置上传其最新内容。数据被包含在请求体中。
*  **DELETE**：请求服务器删除 Request-URI 所标识的资源。
*  **TRACE**：回显服务器收到的请求，主要用于测试或诊断。
*  **CONNECT**：HTTP/1.1 协议中预留给能够将连接改为管道方式的代理服务器。

虽然 HTTP 的请求方式有 8 种，但是我们在实际应用中常用的也就是 **get** 和 **post**，其他请求方式也都可以通过这两种方式间接的来实现。

> HTTP 方法 `GET` 和 `HEAD` 都用于请求资源，但它们有一个关键的区别：`GET` 会请求整个资源的数据，而 `HEAD` 只请求资源的元数据（头部信息）
>
> `GET`**适用场景**: 当需要访问或下载网页、API 返回的具体数据时使用。例如，浏览器访问网页、爬虫抓取数据时通常使用 `GET`。
>
> `HEAD`**适用场景**:
>
> * 检查资源是否存在（通过状态码 `200`、`404` 等）。
> * 获取资源的元数据（如文件大小）而不下载资源内容。
> * 验证缓存：在执行 `GET` 请求前，用 `HEAD` 检查是否需要更新缓存的副本。
>
> ----
>
> ### **`POST` 方法**
>
> * **用途**: `POST` 方法用于向服务器提交数据，通常是创建一个新的资源或触发服务器执行某个操作。它常用于提交表单、上传文件、或进行 API 请求。
>
> ### **`PUT` 方法**
>
> * **用途**: `PUT` 方法用于**更新资源**，或者在指定的 URL 下创建一个资源。它的语义是：如果资源在指定位置已经存在，服务器应该更新它；如果资源不存在，服务器可以创建一个新的资源。

#### 27.3.3 HTTP响应

HTTP RESPONSE 的协议头是由以下四部分组成的：

* 状态行
  * HTTP版本：与请求消息中的版本相匹配
  * 状态码：三位数
  * 状态信息：状态码的简短描述
* 响应头：若干键值对，包含了服务器环境信息、服务器支持的压缩类型等
* 空行：响应头和响应体之间的分隔符
* 响应正文（可选）：包含服务器返回的数据，如请求的网页内容、图片、JSON数据等

例如：

```HTTP
HTTP/1.1 200 OK
Date: Wed, 18 Apr 2024 12:00:00 GMT
Server: Apache/2.4.1 (Unix)
Last-Modified: Wed, 18 Apr 2024 11:00:00 GMT
Content-Length: 12345
Content-Type: text/html; charset=UTF-8

<!DOCTYPE html>
<html>
<head>
    <title>Example Page</title>
</head>
<body>
    <h1>Hello, World!</h1>
    <!-- The rest of the HTML content -->
</body>
</html>
```

![img](https://github.com/jackfrued/mypic/raw/master/20210825002802.PNG)



### 27.4 URL

URL（Uniform Resource Locator，统一资源定位符）：俗称网页地址，简称网址，是因特网上标准的资源的地址。

URL的完整格式如下：

`[(传送)协议类型]://[访问资源需要的凭证信息]@[服务器地址]:[端口号]/[资源层级UNIX文件路径][文件名]?[查询]#[片段ID]`

其中，[访问凭证信息]，[端口号]，[查询]，[片段ID]都属于选填项

[超文本传输协议](https://zh.wikipedia.org/wiki/超文本传输协议)的统一资源定位符将从[因特网](https://zh.wikipedia.org/wiki/因特网)获取信息的五个基本元素包括在一个简单的地址中：

1. [传送协议](https://zh.wikipedia.org/wiki/統一資源標誌符方案)
2. 层级URL标记符号（为“//”，固定不变）
3. 访问资源需要的凭证信息（可省略）
4. [服务器](https://zh.wikipedia.org/wiki/服务器)（通常为[域名](https://zh.wikipedia.org/wiki/域名)，有时为[IP地址](https://zh.wikipedia.org/wiki/IP地址)）
5. [端口](https://zh.wikipedia.org/wiki/通訊埠)号（以[数字](https://zh.wikipedia.org/wiki/數字)方式表示，若为默认值可省略）
6. 路径（以“/”字符区别路径中的每一个目录名称）
7. 查询（[GET模式](https://zh.wikipedia.org/wiki/超文本传输协议#请求方法)的[窗体](https://zh.wikipedia.org/wiki/表單)参数，以“?”字符为起点，每个参数以“&”隔开，再以“=”分开参数名称与资料，通常以[UTF-8](https://zh.wikipedia.org/wiki/UTF-8)的URL编码，避开字符冲突的问题）
8. 片段（以“#”字符为起点[[2\]](https://zh.wikipedia.org/wiki/统一资源定位符#cite_note-2)[[3\]](https://zh.wikipedia.org/wiki/统一资源定位符#cite_note-3)）

相对Protocol links (PRL，又称为相对protocol URLs (PRURL), 是没有指定协议的URL。例如，//example.om 将使用当前页面的协议，通常是 HTTP 或 HTTPS。

### 27.5 相关辅助工具

1.Chrome Developer Tools：谷歌浏览器内置的开发者工具。该工具最常用的几个功能模块是：

* 元素（ELements）：用于查看或修改 HTML 元素的属性、CSS 属性、监听事件等。CSS 可以即时修改，即时显示，大大方便了开发者调试页面。
* 控制台（Console）：用于执行一次性代码，查看 JavaScript 对象，查看调试日志信息或异常信息。控制台其实就是一个执行 JavaScript 代码的交互式环境。
* 源代码（Sources）：用于查看页面的 HTML 文件源代码、JavaScript 源代码、CSS 源代码，此外最重要的是可以调试 JavaScript 源代码，可以给代码添加断点和单步执行。
* 网络（Network）：用于 HTTP 请求、HTTP 响应以及与网络连接相关的信息。
* 应用（Application）：用于查看浏览器本地存储、后台任务等内容，本地存储主要包括Cookie、Local Storage、Session Storage等。

2.Postman：功能强大的网页调试与 RESTful 请求工具。Postman可以帮助我们模拟请求，非常方便的定制我们的请求以及查看服务器的响应。

3.`httpie`：命令行http工具

```
http --header https://movie.douban.com/

HTTP/1.1 200 OK
Connection: keep-alive
Content-Encoding: gzip
Content-Type: text/html; charset=utf-8
Date: Tue, 24 Aug 2021 16:48:00 GMT
Keep-Alive: timeout=30
Server: dae
Set-Cookie: bid=58h4BdKC9lM; Expires=Wed, 24-Aug-22 16:48:00 GMT; Domain=.douban.com; Path=/
Strict-Transport-Security: max-age=15552000
Transfer-Encoding: chunked
X-Content-Type-Options: nosniff
X-DOUBAN-NEWBID: 58h4BdKC9lM
```

4.`builtwith`库：识别网站所用技术的工具

``` python
import ssl
import builtwith

ssl._create_default_https_context = ssl._create_unverified_context
print(builtwith.parse('http://www.bootcss.com/'))
```

5.`python-whois`库：查询网站所有者的工具

``` python
import whois

print(whois.whois('https://www.bootcss.com'))
```

### 27.6 爬虫的基本工作流程

1. 发起请求（数据采集）
2. 获取响应内容
3. 解析响应内容（数据处理，正则表达式）
4. 保存数据
5. 分析数据

当然更为高级的爬虫在数据采集和处理时会使用并发编程或分布式技术，这就需要有调度器（安排线程或进程执行对应的任务）、后台管理程序（监控爬虫的工作状态以及检查数据抓取的结果）等的参与。

另外，在数据采集时：

* 当服务器无法访问时，按照指定的重试次数尝试重新下载页面。
* 在需要的时候设置用户代理或隐藏真实IP，否则可能无法访问页面。

## 28. 用Python获取网络资源

### 28.1 Requests Library

`requests`是基于Python标准库进行了封装，简化了通过HTTP或HTTPS访问网络资源的操作。

> 当我们在浏览器输入了正确的URL并按下Enter时，我们就向网络上的Web服务器发送了一个HTTP请求，服务器在收到请求后会给我们一个HTTP响应。
>
> 浏览器呈现给我们的网页是通过HTML编写的，浏览器相当于是HTML的解释器环境，因此访问网页时，服务器返回给我们的数据就是HTML。

``` PYTHON
import requests
import re
import random
import time

# 获取网页中的特定信息 -- re
def func1():
    resp = requests.get('https://www.huya.com')
    if resp.status_code == 200:
        print(resp.text)
        pattern = re.compile(r'<a.*?href="(.*?)".*?title="(.*?)".*?>')
        all_matchs = pattern.findall(resp.text)
        for href, title in all_matchs:
            print(href, title)


# 获取二进制资源
def func2():
    resp = requests.get('https://www.baidu.com/img/PCtm_d9c8750bed0b3c7d089fa7d55720d6cf.png')
    with open('./data/baidu.png', "wb") as file:
        file.write(resp.content)

# 从豆瓣电影获取排名前250命的电影的名称
    # 通过观察url和网页内容可以发现，一个网页只能显示25个电影信息
    # 通过改变url的start可以实现页面的切换，因此我们总共需要爬取10个网页的信息
    # 但为了爬取的太过频繁，可以在每次爬取之后sleep一段随机时间
def func3():
    pattern1 = re.compile(r'<span class="title">([^&].*?)</span>')
    pattern2 = re.compile(r'<span class="rating_num" property="v:average">(.*?)</span>')
    for i in range(0, 10):
        cur_url = "https://movie.douban.com/top250?start=" + str(i * 25)
        resp = requests.get(
            url=cur_url,
            headers={
                # 如果不设置HTTP请求头中的User-Agent，豆瓣会检测出不是浏览器而阻止我们的请求。
                # 通过get函数的headers参数设置User-Agent的值，具体的值可以在浏览器的开发者工具查看到。
                # 用爬虫访问大部分网站时，将爬虫伪装成来自浏览器的请求都是非常重要的一步。
                'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.0.0 Safari/537.36'
            }
        )
        if resp.status_code == 200:
            titles = pattern1.findall(resp.text)
            ranks = pattern2.findall(resp.text)
            for idx, item in enumerate(zip(titles, ranks)):
                print(f'[{idx + i * 25 + 1}]', item[0], item[1])

        time.sleep(2 + random.randint(2, 3))


func3()
```

### 28.2 使用IP代理

让爬虫程序隐匿自己的身份对编写爬虫程序来说是比较重要的，很多网站对爬虫都比较反感的，因为爬虫会耗费掉它们很多的网络带宽并制造很多无效的流量。要隐匿身份通常需要使用**商业 IP 代理**（如蘑菇代理、芝麻代理、快代理等），让被爬取的网站无法获取爬虫程序来源的真实 IP 地址，也就无法简单的通过 IP 地址对爬虫程序进行封禁。

## 29. 用Python解析HTML页面

在前面我们解析HTML页面是通过正则表达式进行的，但是正则表达式的编写复杂，并且正确性也不容易保障，不过好在，解析HTML页面不止正则表达式一种方式。

> 一个页面的构成
>
> * html : 承载页面要显示的内容
> * css : 页面渲染
> * javascript : 控制页面的交互式行为

### 29.1 XPath

XPath语法原本是XML（Extensive Markup Language）的一种查询语言，可以根据HTML标签的层次结构提取标签中的内容或标签属性；具体来说，我们可以把HTML的标签结构看成一棵树，XPath使用路径表达式在这棵树当中选择节点或者节点集；此外，也可以使用CSS选择器来定位页面元素。

实现 XPath 解析需要三方库`lxml` 的支持，可以使用下面的命令安装`lxml`。

```shell
pip install lxml
```

下面我们用 XPath 解析方式改写之前获取豆瓣电影 Top250的代码，如下所示。

```python
from lxml import etree
import requests

for page in range(1, 11):
    resp = requests.get(
        url=f'https://movie.douban.com/top250?start={(page - 1) * 25}',
        headers={'User-Agent': 'BaiduSpider'}
    )
    tree = etree.HTML(resp.text)
    # 通过XPath语法从页面中提取电影标题
    title_spans = tree.xpath('//*[@id="content"]/div/div[1]/ol/li/div/div[2]/div[1]/a/span[1]')
    # 通过XPath语法从页面中提取电影评分
    rank_spans = tree.xpath('//*[@id="content"]/div/div[1]/ol/li[1]/div/div[2]/div[2]/div/span[2]')
    for title_span, rank_span in zip(title_spans, rank_spans):
        print(title_span.text, rank_span.text)
```

### 29.2 CSS选择器

浏览器中运行的JavaScript本身就可以通过`document`对象的`querySelector()`和`querySelectorAll()`方法基于CSS选择器获取页面元素（HTML），在Python中，我们可以利用第三方库`beautifulsoup4`或`pquery`来做相同的事情，

Beautiful Soup 可以用来解析 HTML 和 XML 文档，修复含有未闭合标签等错误的文档，通过**为待解析的页面在内存中创建一棵树结构**，实现对从页面中提取数据操作的封装。可以用下面的命令来安装 Beautiful Soup。

下面是使用`bs4`改写的获取豆瓣电影Top250电影名称的代码。

```python
import bs4
import requests

for page in range(1, 11):
    resp = requests.get(
        url=f'https://movie.douban.com/top250?start={(page - 1) * 25}',
        headers={'User-Agent': 'BaiduSpider'}
    )
    # 创建BeautifulSoup对象
    soup = bs4.BeautifulSoup(resp.text, 'lxml')
    # 通过CSS选择器从页面中提取包含电影标题的span标签
    title_spans = soup.select('div.info > div.hd > a > span:nth-child(1)')
    # 通过CSS选择器从页面中提取包含电影评分的span标签
    rank_spans = soup.select('div.info > div.bd > div > span.rating_num')
    for title_span, rank_span in zip(title_spans, rank_spans):
        print(title_span.text, rank_span.text)
```

关于 BeautifulSoup 更多的知识，可以参考它的[官方文档](https://www.crummy.com/software/BeautifulSoup/bs4/doc.zh/)。



## 30. XPath

XPath（XML Path Language）：是一种用来在XML文档中查询信息的语言，它使用路径表达式来获取XML文档中的节点或者节点集。XPath将XML文档看作节点树。

### 30.1 XPath Node

在XPath中，有七种类型的节点：

* 文档（根）节点
* 元素
* 属性
* 文本
* 注释
* 命名空间
* 处理指令

例如：

``` html
<?xml version="1.0" encoding="UTF-8"?>

<bookstore>
  <book>
    <title lang="en">Harry Potter</title>
    <author>J K. Rowling</author>
    <year>2005</year>
    <price>29.99</price>
  </book>
</bookstore>
```

其中，`<bookstore>`是文档节点（根节点），`<year>2005</year>`是元素节点，`lang="en"`是属性节点。

其中无父无子的节点成为**基本值**或**原子值**，例如`Harry Potter`和`en`都是基本值。

**项目**是节点或者基本值。

### 30.2 XPath Expression

**（1） 常用路径表达式：**

| 表达式   | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| nodename | 选取此节点的所有子节点                                       |
| /        | 从根节点选取（子节点）                                       |
| //       | 从匹配选择的当前节点选择文档中的节点，而不考虑它们的位置（取子孙节点）。 |
| .        | 选取当前节点                                                 |
| ..       | 选取当前节点的父节点                                         |
| @        | 选取属性                                                     |

例如：

| 路径表达式      | 结果                                                         |
| :-------------- | :----------------------------------------------------------- |
| bookstore       | 选取所有名为 bookstore 的节点。                              |
| /bookstore      | 选取根元素 bookstore。注释：假如路径起始于正斜杠( / )，则此路径始终代表到某元素的绝对路径！ |
| bookstore/book  | 选取属于 bookstore 的子元素的所有 book 元素。                |
| //book          | 选取所有 book 子元素，而不管它们在文档中的位置。             |
| bookstore//book | 选择属于 bookstore 元素的后代的所有 book 元素，而不管它们位于 bookstore 之下的什么位置。 |
| //@lang         | 选取名为 lang 的所有属性。                                   |

**（2）谓语(Predicates)**

通过方括号包围起来，用来查找某个特定的节点或者包含某个指定的值的节点：**（注意XPath的下标从1开始）**

| 路径表达式                          | 结果                                                         |
| :---------------------------------- | :----------------------------------------------------------- |
| /bookstore/book[1]                  | 选取属于 bookstore 子元素的第一个 book 元素。                |
| /bookstore/book[last()]             | 选取属于 bookstore 子元素的最后一个 book 元素。              |
| /bookstore/book[last()-1]           | 选取属于 bookstore 子元素的倒数第二个 book 元素。            |
| /bookstore/book[position()<3]       | 选取最前面的两个属于 bookstore 元素的子元素的 book 元素。    |
| //title[@lang]                      | 选取所有拥有名为 lang 的属性的 title 元素。                  |
| //title[@lang='eng']                | 选取所有 title 元素，且这些元素拥有值为 eng 的 lang 属性。   |
| /bookstore/book[price>35.00]        | 选取 bookstore 元素的所有 book 元素，且其中的 price 元素的值须大于 35.00。 |
| /bookstore/book[price>35.00]//title | 选取 bookstore 元素中的 book 元素的所有 title 元素，且其中的 price 元素的值须大于 35.00。 |

**（3）选取未知节点**

XPath通配符可用来选取未知节点：

| 通配符 | 描述                 |
| :----- | :------------------- |
| *      | 匹配任何元素节点。   |
| @*     | 匹配任何属性节点。   |
| node() | 匹配任何类型的节点。 |

在下面的表格中，我们列出了一些路径表达式，以及这些表达式的结果：

| 路径表达式   | 结果                              |
| :----------- | :-------------------------------- |
| /bookstore/* | 选取 bookstore 元素的所有子元素。 |
| //*          | 选取文档中的所有元素。            |
| //title[@*]  | 选取所有带有属性的 title 元素。   |

**（4）选取若干路径**

| 路径表达式                       | 结果                                                         |
| :------------------------------- | :----------------------------------------------------------- |
| //book/title \| //book/price     | 选取 book 元素的所有 title 和 price 元素。                   |
| //title \| //price               | 选取文档中的所有 title 和 price 元素。                       |
| /bookstore/book/title \| //price | 选取属于 bookstore 元素的 book 元素的所有 title 元素，以及文档中所有的 price 元素。 |

### 30.3 XPath Axes

XPath Axes可定义XML树上相当于当前节点的节点集：

| 轴名称             | 结果                                                     |
| :----------------- | :------------------------------------------------------- |
| ancestor           | 选取当前节点的所有先辈（父、祖父等）。                   |
| ancestor-or-self   | 选取当前节点的所有先辈（父、祖父等）以及当前节点本身。   |
| attribute          | 选取当前节点的所有属性。                                 |
| child              | 选取当前节点的所有子元素。                               |
| descendant         | 选取当前节点的所有后代元素（子、孙等）。                 |
| descendant-or-self | 选取当前节点的所有后代元素（子、孙等）以及当前节点本身。 |
| following          | 选取文档中当前节点的结束标签之后的所有节点。             |
| following-sibling  | 选取当前节点之后的所有兄弟节点                           |
| namespace          | 选取当前节点的所有命名空间节点。                         |
| parent             | 选取当前节点的父节点。                                   |
| preceding          | 选取文档中当前节点的开始标签之前的所有节点。             |
| preceding-sibling  | 选取当前节点之前的所有同级节点。                         |
| self               | 选取当前节点。                                           |

### 30.4 XPath Operator

XPath表达式可以返回节点集、字符串、逻辑值以及数字：

| 运算符 | 描述           | 实例                      | 返回值                                                       |
| :----- | :------------- | :------------------------ | :----------------------------------------------------------- |
| \|     | 计算两个节点集 | //book \| //cd            | 返回所有拥有 book 和 cd 元素的节点集                         |
| +      | 加法           | 6 + 4                     | 10                                                           |
| -      | 减法           | 6 - 4                     | 2                                                            |
| *      | 乘法           | 6 * 4                     | 24                                                           |
| div    | 除法           | 8 div 4                   | 2（注意除法不是`/`，原因显而易见）                           |
| =      | 等于           | price=9.80                | 如果 price 是 9.80，则返回 true。如果 price 是 9.90，则返回 false。 |
| !=     | 不等于         | price!=9.80               | 如果 price 是 9.90，则返回 true。如果 price 是 9.80，则返回 false。 |
| <      | 小于           | price<9.80                | 如果 price 是 9.00，则返回 true。如果 price 是 9.90，则返回 false。 |
| <=     | 小于或等于     | price<=9.80               | 如果 price 是 9.00，则返回 true。如果 price 是 9.90，则返回 false。 |
| >      | 大于           | price>9.80                | 如果 price 是 9.90，则返回 true。如果 price 是 9.80，则返回 false。 |
| >=     | 大于或等于     | price>=9.80               | 如果 price 是 9.90，则返回 true。如果 price 是 9.70，则返回 false。 |
| or     | 或             | price=9.80 or price=9.70  | 如果 price 是 9.80，则返回 true。如果 price 是 9.50，则返回 false。 |
| and    | 与             | price>9.00 and price<9.90 | 如果 price 是 9.80，则返回 true。如果 price 是 8.50，则返回 false。 |
| mod    | 计算除法的余数 | 5 mod 2                   | 1                                                            |

## 31. 并发编程概述

现如今，我们使用的计算机早已是**多 CPU** 或**多核**的计算机，而我们使用的操作系统基本都支持**“多任务”**，这使得我们可以同时运行多个程序，也可以将一个程序分解为若干个相对独立的子任务，让**多个子任务**“并行”或“并发”的执行，从而缩短程序的执行时间，同时也让用户获得更好的体验。

很多时候，我们并不用严格区分并发和并行两个词，所以我们有时候也把 Python 中的多线程、多进程以及异步 I/O 都视为实现并发编程的手段，但实际上前面两者也可以实现并行编程。

### 31.1 daemon

> java中的守护进程

Java程序入口就是由JVM启动`main`线程，`main`线程又可以启动其他线程。当所有线程都运行结束时，JVM退出，进程结束。如果有一个线程没有退出，JVM进程就不会退出。所以，必须保证所有线程都能及时结束。

但是有一种线程的目的就是无限循环，例如，一个定时触发任务的线程。如果这个线程不结束，JVM进程就无法结束。问题是，由谁负责结束这个线程？

然而这类线程经常没有负责人来负责结束它们。但是，当其他线程结束时，JVM进程又必须要结束，怎么办？

答案是使用守护线程（Daemon Thread）。

守护线程是指为其他线程服务的线程。在JVM中，所有非守护线程都执行完毕后，无论有没有守护线程，虚拟机都会自动退出。（也可以理解为守护进程此时强制结束了）最典型的守护进程有GC（垃圾收集器）。

在守护线程中，编写代码要注意：守护线程不能持有任何需要关闭的资源，例如打开文件等，因为虚拟机退出时，守护线程没有任何机会来关闭文件，这会导致数据丢失。

----

另外，对于join函数来说（join会阻塞主线程），如果线程daemon属性为True，则join里的timeout参数无效，主线程会一直等待子线程结束；如果线程daemon属性为False，则join里的timeout参数是有效的，主线程会等待timeout时间后，结束子线程。例如：

``` Python
import threading
import time

def func():
    print("start", flush=True)
    time.sleep(4)
    print("end")


thread = threading.Thread(target=func)
# 如果加上下面一行，"end"不会输出
thread.daemon = True
thread.start()
thread.join(timeout=2)

print('main done')
```

###  31.2 GIL锁

#### 31.2.1 GIL定义

GIL（Global Interpreter Lock）：全局解释器锁，他并不是Python独有的特性，他只是在实现CPython（Python解释器）时引入的一个概念：

> In CPython, the global interpreter lock, or GIL, is a mutex that prevents multiple native threads from executing Python bytecodes at once. This lock is necessary mainly because CPython’s memory management is not thread-safe. (However, since the GIL exists, other features have grown to depend on the guarantees that it enforces.)

由定义可知，GIL是一个`互斥锁(mutex)`。它阻止了多个线程同时执行Python字节码，毫无疑问，这降低了执行效率，使得Python同时最多只能有一个线程在执行。要理解GIL的必要性，需要先了解CPython对于线程安全的内存管理机制。

#### 31.2.2 CPython的内存管理机制

Python使用引用计数来管理内存空间，在Python中创建的对象都会有引用计数，例如我们可以通过`sys`的`getrefcount()`验证：

``` python
import sys

a = [1, 2, 3, 4]
c = a
print(sys.getrefcoutn(a), getrefcoutn(c)) # 3 3
# 显示为3是因为getrefcount也引用了a/c
```

#### 31.2.3 GIL锁的产生和历史局限

如果多个线程同时对数据进行操作，会引发数据不一致（例如reference counting不一致），导致`内存泄漏`，我们可以对其进行加锁。但是既然有了锁，一个对象就需要一把锁，那么多个对象就会有多个锁，这又会带来新问题：

1. 死锁
2. 反复获取和释放锁导致性能降低

为了确保单线程情况下Python的执行执行和效率，GIL锁（单一锁）产生了，它规定任何Python字节码的执行都需要先获取解释器锁，这样可以防止死锁，并且不会带来太多的性能开销。

通过引入GIL简化了在多线程情况下对Python内存对象的管理和实现，但因为历史原因，GIL是在Python的早期版本中引入的，当时Python并没有专门设计为一个高性能的多线程语言。随着多核处理器的普及，多线程并行处理变的越来越重要，但CPython依然保持了GIL的存在。

#### 31.2.4 GIL锁的底层原理

每一个线程在开始执行时，都会锁住 GIL，以阻止别的线程执行；同样的，每一个线程执行完一段后，会释放 GIL，以允许别的线程开始利用资源。

线程释放GIL锁有两种情况，一是遇到`IO操作`，二是`Time Tick`到期。IO操作很好理解，比如发出一个http请求，等待响应。那么`Time Tick`到期是什么呢？Time Tick规定了线程的最长执行时间，超过时间后自动释放GIL锁。Python 3 以后，间隔时间大致为`15毫秒`。

虽然都是释放GIL锁，但这两种情况是不一样的。比如，Thread1遇到`IO操作`释放GIL，由Thread2和Thread3来竞争这个GIL锁，Thread1`不再参与这次竞争`。如果是Thread1因为`Time Tick`到期释放GIL(多数是CPU密集型任务)，那么三个线程可以同时竞争这把GIL锁，可能出现Thread1在竞争中胜出，再次执行的情况。单核CPU下，这种情况不算特别糟糕。因为只有1个CPU，所以CPU的利用率是很高的。

为了避免同一线程霸占CPU，在`python3.2`版本之后，线程会自动的调整自己的优先级，使得多线程任务执行效率更高。

既然GIL降低了多核的效率，那保留它的目的是什么呢？这就和线程执行的安全有关。

#### 31.2.5 CPython GIL不能绝对保证线程安全

``` python
def add():
    global n
    for i in range(10**1000):
        n = n +1
def sub():
    global n
    for i in range(10**1000):
        n = n - 1
n = 0
import threading
a = threading.Thread(target=add,)
b = threading.Thread(target=sub,)
a.start()
b.start()
a.join()
b.join()
print n
```

上面的程序对n做了同样数量的加法和减法，那么n理论上是0。但运行程序，打印n，发现它不是0。问题出在哪里呢，问题在于python的每行代码不是原子化的操作。比如n = n+1这步，不是一次性执行的。如果去查看python编译后的字节码执行过程，可以看到如下结果。

``` assembly
19 LOAD_GLOBAL              1 (n) # 加载全局变量n
22 LOAD_CONST               3 (1) # 加载常量1
25 BINARY_ADD                     # 执行二进制加法运算
26 STORE_GLOBAL             1 (n) # 将运算结果保存到n
```

从过程可以看出，`n=n+1`操作分成了四步完成。因此，`n=n+1`不是一个原子化操作。

根据前面的线程释放GIL锁原则，线程a执行这四步的过程中，有可能会让出GIL。如果这样，n=n+1的运算过程就被打乱了。最后的结果中，得到一个非零的n也就不足为奇。

#### 31.2.6 解决方案

（1）**IO密集型应用**，多线程的应用和多进程应用区别不大。即便有GIL存在，由于IO操作会导致GIL释放，其他线程能够获得执行权限。由于多线程的通讯成本低于多进程，因此偏向使用多线程。

> 在I/O密集型任务中，Python的多线程和多进程的区别不大，主要是由于任务的瓶颈不在于CPU的计算能力，而在于等待I/O操作的完成（如网络请求、文件读取等）。在这类任务中，线程和进程的切换和调度对于整体性能的影响相对较小。
>
> 例如多线程环境下执行I/O密集型任务。当一个线程因为I/O操作（如等待网络响应）阻塞时，GIL会被释放，允许其他线程执行。因此，多个线程可以在I/O操作的等待时间内高效切换，执行其他任务，从而提升效率。

（2）**计算密集型应用**，由于CPU一直处于被占用状态，GIL锁直到规定时间才会释放，然后才会切换状态，导致多线程处于绝对的劣势，此时可以采用多进程+协程。

**多进程**：使用多个进程代替线程。每个进程都有自己的Python解释器和GIL，因此可以充分利用多核CPU。

（3）**其他Python解释器**：一些其他的Python解释器，例如Jython（Java实现）和IronPython（.NET实现），没有GIL的限制，因为它们使用的是Java或.NET的线程管理系统。

（4）**释放GIL**：在某些扩展模块中（如NumPy），在执行计算密集型操作时可以临时释放GIL，允许其他线程并行执行。

（5）**C拓展技术：**由于Python是解释执行的，如果你将那些性能瓶颈代码移到一个C语言扩展模块中， 速度也会提升的很快。例如将计算密集型任务转移给C，跟Python独立，在工作的时候在C代码中释放GIL。 这可以通过在C代码中插入下面这样的特殊宏来完成：

```C
#include "Python.h"
...

PyObject *pyfunc(PyObject *self, PyObject *args) {
   ...
   Py_BEGIN_ALLOW_THREADS
   // Threaded C code
   ...
   Py_END_ALLOW_THREADS
   ...
}
```

如果你使用其他工具访问C语言，比如对于Cython的ctypes库，你不需要做任何事。 例如，ctypes在调用C时会自动释放GIL。

> C扩展最重要的特征是它们和Python解释器是保持独立的。 也就是说，如果你准备将Python中的任务分配到C中去执行， 你需要确保C代码的操作跟Python保持独立， 这就意味着不要使用Python数据结构以及不要调用Python的C API。 另外一个就是你要确保C扩展所做的工作是足够的，值得你这样做。 也就是说C扩展担负起了大量的计算任务，而不是少数几个计算。

### 31.3 Python中的库

#### （1）threadings

#### （2）multiprocessing

#### （3）concurrent





## 32. 多线程编程

Python的标准库提供了两个模块：`_thread`和`threading`，`_thread`是低级模块，`threading`是高级模块，对`_thread`进行了封装。绝大多数情况下，我们只需要使用`threading`这个高级模块。

``` python
threading.Thread(group=None, target=None, name=None, args=None, kwargs=None, deamon=None)
```

* group：该参数为将来扩展线程组功能而保留，当前必须始终为 `None`，否则会引发 `RuntimeError`。目前没有实际用途。
* target：线程启动时执行的目标函数，传递一个可调用对象（函数或方法）。当线程通过 `start()` 方法启动时，它会调用 `target` 指定的函数。如果 `target` 为 `None`，则线程不执行任何任务，除非你重载了 `Thread` 类并实现了 `run()` 方法。
* name：用于指定线程的名称，主要用于调试和日志记录。如果未指定，Python 将自动为线程生成一个唯一的名称，如 `"Thread-1"`、`"Thread-2"` 等。
* args：传递给 `target` 函数的位置参数，必须以元组形式传递。如果目标函数需要多个参数，它们可以按顺序放在 `args` 中。（注意若只有一个元素，需为`(arg1,)`而不是``(arg1)``）
* kwargs：传递给 `target` 函数的关键字参数，以字典形式传递。与 `args` 参数类似，允许传递命名参数给目标函数。
* deamon：指定线程是否为守护线程。守护线程在主线程终止后会自动结束，而非守护线程需要在程序退出前完成所有任务。默认情况下，`daemon` 属性继承自创建线程的父线程。

### 32.1 自定义线程

通过继承Thread类并重载

``` python
import random
import time
import threading
from threading import Thread

# 重载Thread的run方法
class DownloadThread(Thread):
    def __init__(self, filename, name=None, daemon=None):
        # 1. 必须先调用super的init才能初始化当前的init
            # 确保父类 Thread 的初始化首先完成。
            # 父类的 __init__() 方法会初始化内部的线程机制
            # 例如 self._initialized
            # 这样可以避免在子类中调用线程相关属性时出错。
        # 2. 要以关键字的形式传递参数
        super().__init__(name=name, daemon=daemon)
        self.filename = filename
        self.name = filename
    def run(self):
        print(f'[thread name]: {threading.current_thread().name}')  # 使用 current_thread
        start = time.time()
        print(f'start installing {self.filename}')
        time.sleep(random.randint(2, 4))
        print(f'{self.filename} installed successfully')
        end = time.time()
        print(f'time used: {end - start:.3f}s')


def main():
    threads = [
        DownloadThread('C++ Prime'),
        DownloadThread('Insight Java'),
        DownloadThread('Unix Kernel'),
    ]
    start = time.time()
    for thread in threads:
        thread.start()
    for thread in threads:
        thread.join()

    end = time.time()
    print(f'all time used: {end - start:.3f}s')


if __name__ == '__main__':
    main()
```

### 32.2 线程池

线程的创建和释放都会带来较大的开销，频繁的创建和释放线程通常都不是很好的选择。利用线程池，可以提前准备好若干个线程，在使用的过程中不需要再通过自定义的代码创建和释放线程，而是直接复用线程池中的线程。Python 内置的`concurrent.futures`模块提供了对线程池的支持，代码如下所示。

``` python
import random
import time
from threading import Thread
from concurrent.futures import ThreadPoolExecutor

def download(*, filename):
    start = time.time()
    print(f'开始下载 {filename}.')
    time.sleep(random.randint(3, 6))
    print(f'{filename} 下载完成.')
    end = time.time()
    print(f'下载耗时: {end - start:.3f}秒.')

def main():
    start = time.time()
    with ThreadPoolExecutor(max_workers=4) as pool:
        filenames = ['C++', 'Java', 'Go']
        for filename in filenames:
            # 注意filename要以关键字形式传递
            pool.submit(download, filename=filename)
    end = time.time()
    print(f'总耗时: {end - start:.3f}秒.')


if __name__ == '__main__':
    main()
```

### 32.3 死锁

CPython自带的GIL并不能完全避免资源竞争，由于python的一个操作实际上会分解为多个原子操作，因此我们并不能保证这其中的线程安全。因此我们也需要自己手动加锁。

Python的threading模块提供了`Lock`和`RLock` （Reentrant Lock）类支持锁机制。

`Lock` 是 Python 中最基本的锁类型，又称为 **互斥锁（mutex）**。它有两个状态：**“锁定”**`acquire()` 和 **“解锁”**`release()`。

``` PYTHON
import threading

lock = threading.Lock()

def task():
    print(f'{threading.current_thread().name} trying to acquire lock')
    lock.acquire()
    print(f'{threading.current_thread().name} acquired lock')
    # Critical section
    lock.release()
    print(f'{threading.current_thread().name} released lock')

t1 = threading.Thread(target=task)
t2 = threading.Thread(target=task)

t1.start()
t2.start()
t1.join()
t2.join()
```

`RLock` 是 **可重入锁（reentrant lock）**，它允许**同一个线程**在不释放锁的情况下多次获得该锁。这是 `Lock` 无法做到的。

``` python
import threading
from threading import Thread
from threading import RLock

rlock = RLock()

def task():
    thread_name = threading.current_thread().name
    print(f'{thread_name} first acquire rlock...')
    rlock.acquire()
    print(f'{thread_name} second acquire rlock...')
    rlock.acquire()
    print(f'{thread_name} first release rlock')
    rlock.release()
    print(f'{thread_name} second release rlock')
    rlock.release()


t1 = Thread(target=task)
t2 = Thread(target=task)
t1.start()
t2.start()
t1.join()
t2.join()
```

在这个例子中，`RLock` 允许同一个线程多次进入临界区，并要求每次调用 `acquire()` 都对应一次 `release()`。

`RLock`适用于递归调用或者需要多次进入临界区的场景，需要处理“递归计数”；而`Lock`则适用于简单的互斥场景，是一个轻量锁，不需要处理互斥场景。

> `RLock`是`Lock`的超集，因此更推荐使用`RLock`。

当然，我们也可以通过上下文语法来获取锁，从而避免了忘记释放锁以及释放锁的时机不合理的问题：

``` python
import threading
from threading import Thread
from threading import RLock
from concurrent.futures import ThreadPoolExecutor
import time

class Account:
    def __init__(self):
        self.balance = 0
        self.rlock = RLock()

    def deposit(self, money):
        with self.rlock:
            new_balance = self.balance + money
            time.sleep(0.1)
            self.balance = new_balance

def main():
    account = Account()
    with ThreadPoolExecutor(max_workers=16) as pool:
        for _ in range(100):
            pool.submit(account.deposit, 1)
    print(account.balance)


if __name__ == '__main__':
    main()
```

## 33. 多进程编程

在 Python 中可以基于`Process`类来创建进程，虽然进程和线程有着本质的差别，但是`Process`类和`Thread`类的用法却非常类似

``` python
class multiprocessing.Process(group=None, target=None, name=None, args=(), kwargs={}, daemon=None)
```

和多线程一样，多进程的使用方法也一般为三种：

1. 直接使用`Process`类
2. 继承`Process`类
3. 使用进程池`ProcessPoolExecutor`

下面我们以上面三种方法为例，分别比较一下多线程和多进程在执行IO密集型任务或者cpu密集型任务时的执行效率：

> case1：直接使用`Thread`和`Process`类

``` python
import os
import time
import random
from threading import Thread
from multiprocessing import Process


def task(bookname, sleep_time):
    print(f'{bookname} install start')
    time.sleep(sleep_time)
    print(f'{bookname} install finished')

def test_thread():
    start = time.time()
    threads = [
        Thread(target=task, args=('Java', 1)),
        Thread(target=task, args=('CPP', 2)),
        Thread(target=task, args=('Python', 3)),
    ]
    for thread in threads:
        thread.start()
    for thread in threads:
        thread.join()
    end = time.time()
    print(f'multi thread all time uses: {end - start:.3f}')

def test_process():
    start = time.time()
    processes = [
        Process(target=task, args=('Java', 1)),
        Process(target=task, args=('CPP', 2)),
        Process(target=task, args=('Python', 3)),
    ]
    for thread in processes:
        thread.start()
    for thread in processes:
        thread.join()
    end = time.time()
    print(f'multi process all time uses: {end - start:.3f}')

def main():
    test_thread()   # 3.002
    test_process()  # 3.115


if __name__ == '__main__':
    main()
```

> case3：使用`ThreadPoolExecutor`和`ProcessPoolExecutor`

``` python
import os
import time
import math
import random
from threading import Thread
from multiprocessing import Process
from concurrent.futures import ThreadPoolExecutor
from concurrent.futures import ProcessPoolExecutor


def task(n):
    count = 0
    for i in range(2, n + 1):
        count += 1
        for j in range(2, int(math.sqrt(i) + 1)):
            if i % j == 0:
                count -= 1
                continue
    # print(f'from 1 to {n} have {count} prime numbers')

def test_thread(count, max_workers):
    start = time.time()
    with ThreadPoolExecutor(max_workers=max_workers) as pool:
        for _ in range(count):
            pool.submit(task, 10000)
    end = time.time()
    print(f'[multi thread] all time uses: {end - start:.3f}')

def test_process(count, max_workers):
    start = time.time()
    with ProcessPoolExecutor(max_workers=max_workers) as pool:
        for _ in range(count):
            pool.submit(task, 10000)
    end = time.time()
    print(f'[multi process] all time uses: {end - start:.3f}')


def main():
    count, max_workers = 5, 2
    test_thread(count, max_workers)   # 0.073
    test_process(count, max_workers)  # 0.165


if __name__ == '__main__':
    main()
```

## 34 进程间通信

### 34.1 引入

``` python
from multiprocessing import Process
from time import sleep
import os

counter = 0

def sub_task():
    global counter
    print('son pid: ', os.getpid(), "counter: ", counter)
    counter += 50
    print('pid: ', os.getpid(), ", counter add 50，counter: ", counter)


def main():
    global counter
    counter += 10
    print('main begin,  pid: ', os.getpid(), 'counter: ', counter) # 主进程，40
    Process(target=sub_task).start()                    # 主进程看不到子进程1对counter的修改
    print('after add 10, main, counter: ', counter)     # 40
    Process(target=sub_task).start()                    # 主进程看不到子进程2对counter的修改
    print('main done, main, counter: ', counter)     # 40


if __name__ == '__main__':
    print('global pid: ', os.getpid())      # 主进程
    print('before main, counter', counter)  # 30
    main()
    print('after main, counter', counter)   # 40
```

注意在上面的例子中，我们有三个进程，分别是主进程，和在主进程的main函数当中创建的两个进程，这三个进程都拥有独立的内存空间。这意味着所有在主进程中定义的变量（包括全局变量）都会被复制到子进程中。

> 也就是说，这里的`counter=0`会被复制到三个进程当中，他们的初始`counter`都为`0`，并且对它的修改于其他进程不可见。

因此说，主进程对counter的修改对两个子进程不可见，而子进程对counter的修改同样对另一个子进程和主进程不可见。

> 注意这里的main函数只是一个普通函数，而不是像C++那样作为程序的入口函数！

### 34.2 Queue

`multiprocessing.Queue` 提供了一个线程和进程安全的 FIFO 队列，允许进程间传递消息。

``` python
from multiprocessing import Process, Queue

def worker(q):
    q.put("Hello from worker")

if __name__ == '__main__':
    q = Queue()
    p = Process(target=worker, args=(q,))
    p.start()
    message = q.get()  # 从队列中获取消息
    p.join()
    print(message)
```

### 34.3 Pipe

`multiprocessing.Pipe` 提供了一个双向通信管道（任意时刻只能单向通信），允许两个进程之间发送和接收数据。

``` python
from multiprocessing import Process, Pipe

def worker(conn):
    conn.send("Hello from worker")
    conn.close()

if __name__ == '__main__':
    # Pipe()返回了包含两个连接的元组
    parent_conn, child_conn = Pipe()
    p = Process(target=worker, args=(child_conn,))
    p.start()
    message = parent_conn.recv()  # 接收消息
    p.join()
    print(message)
```

### 34.4 Socket

对于分布在不同主机上的进程，网络套接字`socket`也是一种有效的通信方式。

### 34.5 Value和Array

`multiprocessing.Value` 和 `multiprocessing.Array` 允许共享简单的数据结构，如整数、浮点数和数组。

``` python
from multiprocessing import Process, Value

def worker(val):
    val.value = 42

if __name__ == '__main__':
    shared_value = Value('i', 0)  # 创建共享整数
    p = Process(target=worker, args=(shared_value,))
    p.start()
    p.join()
    print(shared_value.value)  # 输出 42
```

### 34.6 Manager

`multiprocessing.Manager` 提供了一个可用于创建共享对象（如字典、列表等）的管理器，支持多进程之间的共享。

``` python
def worker(d):
    d['key'] = 'value'

if __name__ == '__main__':
    with Manager() as manager:
        shared_dict = manager.dict()  # 创建共享字典
        p = Process(target=worker, args=(shared_dict,))
        p.start()
        p.join()
        print(shared_dict)  # 输出 {'key': 'value'}
```

## 35. 协作式并发（异步I/O）

爬虫是典型的 I/O 密集型任务，I/O 密集型任务的特点就是程序会经常性的因为 I/O 操作而进入阻塞状态，比如我们之前使用`requests`获取页面代码或二进制内容，发出一个请求之后，程序必须要等待网站返回响应之后才能继续运行，如果目标网站不是很给力或者网络状况不是很理想，那么等待响应的时间可能会很久，而在这个过程中整个程序是一直阻塞在那里，没有做任何的事情。通过前面的课程，我们已经知道了可以通过多线程的方式为爬虫提速，使用多线程的本质就是，当一个线程阻塞的时候，程序还有其他的线程可以继续运转，因此整个程序就不会在阻塞和等待中浪费了大量的时间。

事实上，还有一种非常适合 I/O 密集型任务的并发编程方式，我们称之为**异步编程**，你也可以将它称为**异步 I/O**。这种方式并不需要启动多个线程或多个进程来实现并发，它是通过多个子程序相互协作的方式来提升 CPU 的利用率，解决了 I/O 密集型任务 CPU 利用率很低的问题，我一般将这种方式称为**“协作式并发”**。

异步I/O在思想上和多线程类似，都是当线程因为I/O等操作而阻塞时，去执行其他任务，但是异步I/O相较于多线程有以下优点：

1. 执行效率更高：异步I/O在阻塞时切换的是子程序，多线程在阻塞时切换的是线程，因此开销更小，执行效率更高。
2. 不需要多线程锁的机制：这一点很好理解，因为异步I/O只需要一个线程。

那么，既然异步I/O是单线程，该如何利用多核CPU呢？最简单的办法就是**多进程+协程**，既充分利用多核，又充分发挥协程的高效率，可获得极高的性能。

### 35.1 基本概念

#### （1）阻塞

**阻塞状态指程序未得到所需计算资源时被挂起的状态**。程序在等待某个操作完成期间，自身无法继续处理其他的事情，则称该程序在该操作上是阻塞的。阻塞随时都可能发生，最典型的就是 I/O 中断（包括网络 I/O 、磁盘 I/O 、用户输入等）、休眠操作、等待某个线程执行结束，甚至包括在 CPU 切换上下文时，程序都无法真正的执行，这就是所谓的阻塞。

#### （2）非阻塞

**程序在等待某操作过程中，自身不被阻塞，可以继续处理其他的事情，则称该程序在该操作上是非阻塞的。**非阻塞并不是在任何程序级别、任何情况下都可以存在的。仅当程序封装的级别可以囊括独立的子程序单元时，它才可能存在非阻塞状态。显然，某个操作的阻塞可能会导程序耗时以及效率低下，所以我们会希望把它变成非阻塞的。

#### （3）同步

**不同程序单元为了完成某个任务，在执行过程中需靠某种通信方式以协调一致，我们称这些程序单元是同步执行的。**例如前面讲过的给银行账户存钱的操作，我们在代码中使用了“锁”作为通信信号，让多个存钱操作强制排队顺序执行，这就是所谓的同步。

#### （4）异步

**不同程序单元在执行过程中无需通信协调，也能够完成一个任务，这种方式我们就称之为异步。**例如，使用爬虫下载页面时，调度程序调用下载程序后，即可调度其他任务，而无需与该下载任务保持通信以协调行为。不同网页的下载、保存等操作都是不相关的，也无需相互通知协调。很显然，异步操作的完成时刻和先后顺序并不能确定。

### 35.2 生成器和协程

前面我们说过，异步编程是一种**“协作式并发”**，即通过多个子程序相互协作的方式提升 CPU 的利用率，从而减少程序在阻塞和等待中浪费的时间，最终达到并发的效果。我们可以将多个相互协作的子程序称为***“协程”***，它是实现异步编程的关键。

如何理解相互协作？看下面的例子：

``` python
def A():
    print 1
    print 2
    print 3
def B():
    print 'a'
    print 'b'
    print 'c'
A()
B()
```

调用结果毫无疑问为：

``` shell
1
2
3
a
b
c
```

但如果我们将这两个普通函数`A`和`B`修改为协程，他就有可能实现下面的输出：

``` shell
1
2
a
b
3
c
```

在执行`A`的过程中，随时可以中断，去执行`B`；同理在执行`B`时也可以中断，再去执行`A`；但是在`A`中，我们并没有调用`B`。

----

生成器对象是由生成器函数创建的特殊对象，生成器函数就是包含yield的函数。我们可以通过内置函数`next`从生成器对象中获取值或者通过`for-in`循环对生成器提供的值进行遍历。

生成器经过预激活，就是一个**协程**，它可以跟其他子程序合作。

``` python
def calc_average():
    total, counter = 0, 0
    avg_value = 0.0
    while True:
        current_value = yield avg_value
        counter += 1
        total += current_value
        avg_value = total / counter


def main():
    obj = calc_average()
    print(type(obj), obj)
    obj.send(None)
    for _ in range(5):
        print(obj.send(int(input('pls input a number: '))))


if __name__ == '__main__':
    main()
```

上面的`main`函数首先通过生成器对象的`send`方法发送一个`None`值来将其激活为协程，也可以通过`next(obj)`达到同样的效果。接下来，协程对象会接收`main`函数发送的数据并产出（`yield`）数据的平均值。

> 我们可以理解为上面的例子就是main函数和calc_average函数的相互协作。

---

传统的生产者-消费者模型是一个线程写消息，一个线程取消息，通过锁机制控制队列和等待，但一不小心就可能死锁。

如果改用协程，生产者生产消息后，直接通过`yield`跳转到消费者开始执行，待消费者执行完毕后，切换回生产者继续生产，效率极高：

``` python
def consumer():
    r = ''
    while True:
        n = yield r
        if not n:
            return
        print('[CONSUMER] Consuming %s...' % n)
        r = '200 OK'

def produce(c):
    c.send(None)
    n = 0
    while n < 5:
        n = n + 1
        print('[PRODUCER] Producing %s...' % n)
        r = c.send(n)
        print('[PRODUCER] Consumer return: %s' % r)
    c.close()

c = consumer()
produce(c)
```

注意到`consumer`函数是一个`generator`，把一个`consumer`传入`produce`后：

1. 首先调用`c.send(None)`启动生成器；
2. 然后，一旦生产了东西，通过`c.send(n)`切换到`consumer`执行；
3. `consumer`通过`yield`拿到消息，处理，又通过`yield`把结果传回；
4. `produce`拿到`consumer`处理的结果，继续生产下一条消息；
5. `produce`决定不生产了，通过`c.close()`关闭`consumer`，整个过程结束。

整个流程无锁，由一个线程执行，`produce`和`consumer`协作完成任务，所以称为“协程”，而非线程的抢占式多任务。

最后套用Donald Knuth的一句话总结协程的特点：

> **“子程序就是协程的一种特例。”**

### 35.3 异步代码

在`Python3.7`版本中，引入了两个关键字：

* `async`：用于定义异步函数。异步函数可能包含异步操作，异步操作的执行不会阻塞主线程。
* `await`：用于等待异步操作完成。`await`必须在`async`函数内部，他会暂停`async`函数的执行，直到`await`的表达式（通常是一个协程）执行完成。

通过这两个关键字，可以简化协程代码的编写，用更简单的方式让多个子程序很好的协作起来。

看下面的例子：

``` python
import asyncio
import time

async def task(num):
    await asyncio.sleep(num)
    print(num)

async def main():
    objs = [task(i) for i in range(0, 5)]
    await asyncio.gather(*objs)


if __name__ == '__main__':
    start = time.time()
    asyncio.run(main())
    end = time.time()
    print(f'All time uses: {end - start:.3f}')
```

 ### 35.4 底层原理

`async`和`await`的底层实现和“事件循环”以及“任务队列”相关。可以将“事件循环”理解为一个“调度器”，“任务队列”就是被“事件循环”调度的数据结构。

首先我们需要注册事件循环，并添加任务。然后调度器会从任务队列中取出一个任务，如果执行到`await`，该任务就会让出控制权，将任务挂起（从任务队列中pop掉），并存储其上下文，然后执行其它任务。一旦挂起的任务的事件完成，它会被重新放入任务队列中等待执行。

因此总下下来，`事件循环`这个调度器主要做四件事：

1. 调度任务
2. 执行任务
3. 挂起任务
4. 重新激活任务

### 35.5 aiohttp库

我们之前使用的`requests`三方库并不支持异步 I/O，如果希望使用异步 I/O 的方式来加速爬虫代码的执行，我们可以安装和使用名为`aiohttp`的三方库。

``` PYTHON
import asyncio
import re

import aiohttp
from aiohttp import ClientSession

TITLE_PATTERN = re.compile(r'<title.*?>(.*?)</title>', re.DOTALL)


async def fetch_page_title(url):
    async with aiohttp.ClientSession(headers={
        'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/95.0.4638.69 Safari/537.36',
    }) as session:  # type: ClientSession
        async with session.get(url, ssl=False) as resp:
            if resp.status == 200:
                html_code = await resp.text()
                matcher = TITLE_PATTERN.search(html_code)
                title = matcher.group(1).strip()
                print(title)


async def main():
    urls = [
        'https://www.python.org/',
        'https://www.jd.com/',
        'https://www.baidu.com/',
        'https://www.taobao.com/',
        'https://git-scm.com/',
        'https://www.sohu.com/',
        'https://gitee.com/',
        'https://www.amazon.com/',
        'https://www.usa.gov/',
        'https://www.nasa.gov/'
    ]
    objs = [fetch_page_title(url) for url in urls]
    await asyncio.gather(*objs)


if __name__ == '__main__':
    asyncio.run(main())
```

``` SHELL
淘宝
搜狐
Git
百度一下，你就知道
京东(JD.COM)-正品低价、品质保障、配送及时、轻松购物！
NASA
Welcome to Python.org
Making government services easier to find | USAGov
Amazon.com. Spend less. Smile more.
Gitee - 基于 Git 的代码托管和研发协作平台
```

从输出可以看出，网站首页标题的输出顺序跟它们的 URL 在列表中的顺序没有关系。代码的第11行到第13行创建了`ClientSession`对象，通过它的`get`方法可以向指定的 URL 发起请求，如第14行所示，跟`requests`中的`Session`对象并没有本质区别，唯一的区别是这里使用了异步上下文。代码第16行的`await`会让因为 I/O 操作阻塞的子程序放弃对 CPU 的占用，这使得其他的子程序可以运转起来去抓取页面。代码的第17行和第18行使用了正则表达式捕获组操作解析网页标题。`fetch_page_title`是一个被`async`关键字修饰的异步函数，调用该函数会获得协程对象，如代码第35行所示。

## 36. 并发编程在爬虫中的应用

单线程版本：

``` python
"""
example04.py - 单线程版本爬虫
"""
import os

import requests


def download_picture(url):
    filename = url[url.rfind('/') + 1:]
    resp = requests.get(url)
    if resp.status_code == 200:
        with open(f'images/beauty/{filename}', 'wb') as file:
            file.write(resp.content)


def main():
    if not os.path.exists('images/beauty'):
        os.makedirs('images/beauty')
    for page in range(3):
        resp = requests.get(f'https://image.so.com/zjl?ch=beauty&sn={page * 30}')
        if resp.status_code == 200:
            pic_dict_list = resp.json()['list']
            for pic_dict in pic_dict_list:
                download_picture(pic_dict['qhimg_url'])

if __name__ == '__main__':
    main()
```

多线程版本：

``` python
"""
example05.py - 多线程版本爬虫
"""
import os
from concurrent.futures import ThreadPoolExecutor

import requests


def download_picture(url):
    filename = url[url.rfind('/') + 1:]
    resp = requests.get(url)
    if resp.status_code == 200:
        with open(f'images/beauty/{filename}', 'wb') as file:
            file.write(resp.content)


def main():
    if not os.path.exists('images/beauty'):
        os.makedirs('images/beauty')
    with ThreadPoolExecutor(max_workers=16) as pool:
        for page in range(3):
            resp = requests.get(f'https://image.so.com/zjl?ch=beauty&sn={page * 30}')
            if resp.status_code == 200:
                pic_dict_list = resp.json()['list']
                for pic_dict in pic_dict_list:
                    pool.submit(download_picture, pic_dict['qhimg_url'])


if __name__ == '__main__':
    main()
```

异步IO版本：

``` python
"""
example06.py - 异步I/O版本爬虫
"""
import asyncio
import json
import os

import aiofile
import aiohttp


async def download_picture(session, url):
    filename = url[url.rfind('/') + 1:]
    async with session.get(url, ssl=False) as resp:
        if resp.status == 200:
            data = await resp.read()
            async with aiofile.async_open(f'images/beauty/{filename}', 'wb') as file:
                await file.write(data)


async def fetch_json():
    async with aiohttp.ClientSession() as session:
        for page in range(3):
            async with session.get(
                url=f'https://image.so.com/zjl?ch=beauty&sn={page * 30}',
                ssl=False
            ) as resp:
                if resp.status == 200:
                    json_str = await resp.text()
                    result = json.loads(json_str)
                    for pic_dict in result['list']:
                        await download_picture(session, pic_dict['qhimg_url'])


def main():
    if not os.path.exists('images/beauty'):
        os.makedirs('images/beauty')
    loop = asyncio.get_event_loop()
    loop.run_until_complete(fetch_json())
    loop.close()


if __name__ == '__main__':
    main()
```

## 38. [爬虫框架Scrapy简介](https://github.com/jackfrued/Python-Core-50-Courses/blob/master/%E7%AC%AC39%E8%AF%BE%EF%BC%9A%E7%88%AC%E8%99%AB%E6%A1%86%E6%9E%B6Scrapy%E7%AE%80%E4%BB%8B.md)

[Docs](https://scrapy-16.readthedocs.io/zh-cn/1.6/index.html)

[菜鸟教程](https://www.runoob.com/w3cnote/scrapy-detail.html)

![scrapt](https://s3.bmp.ovh/imgs/2024/09/26/4060f555f43d2183.png)

如果我们想把爬虫爬取到的数据写入文件，需要注意编码格式的转换：

``` python
    def parse(self, response):
        filename = 'teacher.html'
        with open(filename, 'w', encoding='utf-8') as f:
            f.write(response.body.decode('utf-8'))
```

`response.body`返回的是bytes，需要将其decode为utf-8格式。

## 39. Python接入Mysql数据库

### 39.1 cursor

cursor（游标），他还可以翻译成指针，通过指针这层意思，我们可以更好地理解游标的含义和作用。

试想我们通过SELECT操作在数据库中得到了大量的数据，如果我们要读取或者修改这些数据，就要将这些数据加载到内存当中，但是数据规模可能非常大，一次性加载到内存当中，占用大量内存不说，一下子也用不到这么多数据啊！

游标就是用来解决这个问题的，通过游标，我们可以一条一条或者按批次读取这些数据，而不是一股脑全加载到内存中。其作用，不就相当于一个指针么，这也和C++传递对象的指针而不是原对象本身以节约空间是一样的思想。

游标的类型根据数据库的不同实现略有差异，常见的游标类型有以下几种：

1. **静态游标（Static Cursor）**： 静态游标是在查询时，将所有数据一次性加载到客户端的内存中。数据不会随数据库的改变而更新，适合处理查询结果后不再关心数据变化的情况。
2. **动态游标（Dynamic Cursor）**： 动态游标实时反映数据库的变化。在游标打开期间，如果底层数据发生变化（如插入或删除记录），游标返回的数据也会更新。
3. **前向游标（Forward-Only Cursor）**： 只能从结果集中逐条向前移动（遍历），不能向后移动。这是最常见且效率最高的游标，因为它对内存占用较少。
4. **滚动游标（Scrollable Cursor）**： 允许在结果集中前后移动，甚至可以随机访问记录。这种游标更灵活，但相对消耗资源较多。

### 39.2 pymysql库

在 Python3 中，我们可以使用`mysqlclient`或者`pymysql`三方库来接入 MySQL 数据库并实现数据持久化操作。二者的用法完全相同，只是导入的模块名不一样。我们推荐大家使用纯 Python 的三方库`pymysql`，因为它更容易安装成功。

使用`pymysql`操作Mysql的步骤如下所示：

1. 创建连接
2. 获取游标：sql语句的执行是建立在cursor基础之上的。
3. 执行SQL
4. 事务管理：如果执行增删改操作，需要根据实际情况提交或者回滚事务，因为在创建mysql连接时，默认开启了事务环境。在操作完成后，需要使用连接对象的`commit`或`rollback`方法，实现事务的提交或回滚，`rollback`方法通常会放在异常捕获代码块`except`中。
5. 关闭连接：释放外部资源。我们通常会在`finally`代码块中使用连接对象的`close`方法来关闭连接。

下面是一个将`SELECT`的数据保存到`EXCEL`的示例：

``` python
import pymysql
import openpyxl

# 创建工作簿对象
workbook = openpyxl.Workbook()
# 获取默认的工作表
sheet = workbook.active
# 修改工作表的标题
sheet.title = 'python-sql-test'

# 1. 创建连接
try:
    conn = pymysql.connect(host='127.0.0.1',
                           port=3306,
                           user='jyx',
                           password='XUSHUYU1',
                           database='shop',
                           charset='utf8mb4')
    print("连接成功！")
except pymysql.MySQLError as e:
    print(f"连接失败，错误信息：{e}")


# 2. 获取游标
try:
    with conn.cursor() as cursor:
        # 3. 通过游标对象向数据库服务器发出sql语句
        cursor.execute(
            'SELECT `vend_id`, `prod_id`, `prod_price` FROM products WHERE `prod_price` <= %s'
            , (5, )
        )
        # 4. 通过游标对象抓取数据
        row = cursor.fetchone()
        while row:
            sheet.append(row)
            row = cursor.fetchone()
        # 保存工作簿
        workbook.save('test.xlsx')

except pymysql.MySQLError as e:
    print(type(e), e)

finally:
    # 5. 释放资源
    conn.close()
```

## 附1：Const

在 Python 中，没有专门的关键字来定义“常量”变量（`const`）。不过，开发者通常会通过约定来标识常量。为了表明一个变量是常量，变量名通常用全大写字母书写，并且在使用时避免更改它的值。例如：

```python
PI = 3.14159
MAX_CONNECTIONS = 100
```

在上面的例子中，`PI` 和 `MAX_CONNECTIONS` 被视为常量。虽然 Python 本身不会阻止你修改这些变量的值，但按照约定，开发者不会在程序中修改它们。

如果你希望严格控制常量的行为，可以使用某些类和技术来**模拟常量的不可变性**，例如使用 `property` 或 `namedtuple`。也可以借助第三方库，例如 `enum`。

### 方法一：enum

Python 的 `enum` 模块提供了一种创建常量集的方式。`Enum` 成员是不可变的。

```PYTHON
from enum import Enum

class Constants(Enum):
    PI = 3.14159
    MAX_CONNECTIONS = 100

print(Constants.PI.value)  # 输出 3.14159
# Constants.PI = 3.14  # 会报错：AttributeError: can't reassign members.
```

`Enum` 可以确保其成员是只读的，无法被修改。

> 这里的`Constants`也可以实现C++的枚举类效果。

### 方法二：property

```python
class Constants:
    @property
    def PI(self):
        return 3.14159

constants = Constants()
print(constants.PI)  # 输出 3.14159
# constants.PI = 3.14  # 会报错：AttributeError: can't set attribute
```

> 既要保护类的封装特性，又要让开发者可以使用“对象.属性”的方式操作操作类属性，除了使用 property() 函数，[Python](https://docs.oldtimes.me/c.biancheng.net/python/index.html) 还提供了 @property 装饰器。通过 @property 装饰器，可以直接通过方法名来访问方法，不需要在方法名后添加一对“（）”小括号。
>
> 使用 ＠property 修饰了 PI() 方法，这样就使得该方法变成了 PI属性的 **getter** 方法。需要注意的是，如果类中只包含该方法，那么 PI属性将是一个**只读属性**。
>
> 而要想实现修改 PI属性的值，还需要为 PI属性添加 setter 方法，就需要用到 PI装饰器
>
> 它的语法格式如下：
>
> ``` python
> @方法名.setter
> def 方法名(self, value):
> 代码块
> ```

### 方法三：fronzen

对于字典或集合类型，可以使用 `frozenset` 或者实现不可变的 `frozendict`，使其内容不可更改。

```python
# 模拟不可变集合
constants_set = frozenset(['PI', 'MAX_CONNECTIONS'])
print(constants_set)
# constants_set.add('NEW_CONST')  # 会报错：AttributeError: 'frozenset' object has no attribute 'add'

# 模拟不可变字典 (需要第三方库 frozendict)
from types import MappingProxyType

constants_dict = MappingProxyType({'PI': 3.14159, 'MAX_CONNECTIONS': 100})
print(constants_dict['PI'])  # 输出 3.14159
# constants_dict['PI'] = 3.14  # 会报错：TypeError: 'mappingproxy' object does not support item assignment
```

## 附2：Generator

生成器对象是由生成器函数（包含 `yield` 语句的函数）创建的特殊对象。它是一种**可迭代对象**，用于**逐步生成值**，而不是一次性生成所有值。生成器对象具有以下特点：

1. **惰性求值**：生成器对象不会立即计算所有值，而是每次请求时动态生成下一个值。这种方式可以节省内存，尤其在处理大型数据集时。
2. **状态保持**：每次调用生成器的 `__next__()` 方法时，执行会从上一个 `yield` 语句暂停的地方继续，保留当前状态和局部变量的值。
3. **可迭代性**：生成器对象可以用于 `for` 循环或其他需要可迭代对象的场合。

----

我们还可以通过`send()`方法向生成器发送一个值，并使生成器继续执行，直到遇到下一个`yield`语句。这个方法可以使生成器接受外部输入，从而实现更复杂的协议或状态管理。

基本用法：

1. **发送值**：`send(value)` 将 `value` 传递给生成器，并返回下一个 `yield` 语句的值。
2. **初始启动**（预激活）：在第一次调用 `send()` 之前，生成器必须先被启动，通常是通过调用 `next()`或者`send(None)`。



## 附3：Closure`[*]`

https://www.cnblogs.com/skynet/archive/2011/05/03/2035105.html

## 附4：Ajax技术`[*]`

AJAX（Asynchronous Javascript And XML）是一种用于快速创建动态网页的技术，它允许网页在不重新加载整个页面的情况下与服务器进行异步数据交换。

AJAX 的核心概念

1. **异步请求**： AJAX 允许浏览器在后台与服务器进行通信，而不会干扰用户当前的操作。用户可以在数据加载时继续与页面交互。
2. **数据格式**： 虽然 AJAX 最初设计时使用 XML 格式进行数据传输，但现在 JSON（JavaScript Object Notation）已成为更常用的数据格式，因为它更轻便且易于解析。
3. **JavaScript 和 DOM**： AJAX 使用 JavaScript 来发起请求和处理响应。它可以通过操作 DOM（文档对象模型）来更新网页内容，而无需重新加载页面。



## 附5：Programming Paradise

所谓编程范式就是**程序设计的方法论**，简单的说就是程序员对程序的认知和理解以及他们编写代码的方式。

常见的编程范式有：

* 过程式
* 对象式
* 指令式
* C++模板元
* C++ STL

## 附6：Zen of Python

Python之禅：

* Beautiful is better than ugly. （优美比丑陋好）
* Explicit is better than implicit.（清晰比晦涩好）
* Simple is better than complex.（简单比复杂好）
* Complex is better than complicated.（复杂比错综复杂好）
* Flat is better than nested.（扁平比嵌套好）
* Sparse is better than dense.（稀疏比密集好）
* Readability counts.（可读性很重要）
* Special cases aren't special enough to break the rules.（特殊情况也不应该违反这些规则）
* Although practicality beats purity.（但现实往往并不那么完美）
* Errors should never pass silently.（异常不应该被静默处理）
* Unless explicitly silenced.（除非你希望如此）
* In the face of ambiguity, refuse the temptation to guess.（遇到模棱两可的地方，不要胡乱猜测）
* There should be one-- and preferably only one --obvious way to do it.（肯定有一种通常也是唯一一种最佳的解决方案）
* Although that way may not be obvious at first unless you're Dutch.（虽然这种方案并不是显而易见的，因为你不是那个荷兰人[这里指的是Python之父Guido]）
* Now is better than never.（现在开始做比不做好）
* Although never is often better than *right* now.（不做比盲目去做好[极限编程中的YAGNI原则]）
* If the implementation is hard to explain, it's a bad idea.（如果一个实现方案难于理解，它就不是一个好的方案）
* If the implementation is easy to explain, it may be a good idea.（如果一个实现方案易于理解，它很有可能是一个好的方案）
* Namespaces are one honking great idea -- let's do more of those!（命名空间非常有用，我们应当多加利用）

## 附7：[为什么Python没有自增自减运算符](https://zhuanlan.zhihu.com/p/149878104)

### 1. Python的内存管理机制

Python的整数是不可变类型，对于变量`i`的内存管理在底层是通过引用计数实现的，如果我们执行了`i=100;`，Python不会直接修改`100`这个数所处内存的值，而是重新创建一个变量`101`并分配内存。

### 2. Python有可迭代对象

对于`i++或者++i`，其设计之初的主要目的是实现三段式的`for`循环，但是Python中没有三段式`for`循环的语法，取而代之的是其更为优雅的`for-in`循环。即使是我们想要获取迭代的下标，也可以通过`enumrate`实现，对于字典更是有`keys()`和`values()`这种方法。

> ### 1. `__add__()`
>
> * **定义**：`__add__(self, other)` 方法用于实现加法运算符 `+` 的行为。
> * **用法**：当你使用 `a + b` 时，Python 会自动调用 `a.__add__(b)`。
> * **返回值**：这个方法应该返回一个新的对象，而不是修改原来的对象。
>
> ``` python
> class MyNumber:
>     def __init__(self, value):
>         self.value = value
> 
>     def __add__(self, other):
>         return MyNumber(self.value + other.value)
> 
> num1 = MyNumber(10)
> num2 = MyNumber(20)
> result = num1 + num2  # 实际上调用 num1.__add__(num2)
> print(result.value)  # 输出: 30
> 
> ```
>
> ### 2. `__iadd__()`
>
> * **定义**：`__iadd__(self, other)` 方法用于实现加法赋值运算符 `+=` 的行为。
> * **用法**：当你使用 `a += b` 时，Python 会调用 `a.__iadd__(b)`。
> * **返回值**：这个方法通常应该修改自身的状态，并返回自身，允许连锁赋值。
>
> ``` python
> class MyNumber:
>     def __init__(self, value):
>         self.value = value
> 
>     def __iadd__(self, other):
>         self.value += other.value
>         return self  # 返回自身以支持链式操作
> 
> num1 = MyNumber(10)
> num2 = MyNumber(20)
> num1 += num2  # 实际上调用 num1.__iadd__(num2)
> print(num1.value)  # 输出: 30
> ```
>
> ### 3. 主要区别
>
> * `__add__()` 通常用于返回一个新对象，而 `__iadd__()` 是用于在原地修改对象并返回自身。
> * 使用 `__add__()` 的对象通常是不可变的（immutable），而 `__iadd__()` 则通常用于可变对象（mutable）。
>
> ### 4. 注意事项
>
> * 如果你的类实现了 `__iadd__()`，通常也应该实现 `__add__()`，以确保在使用不同的加法运算时行为的一致性。
> * 你也可以在 `__add__()` 中调用 `__iadd__()`，以减少代码重复，但要确保处理不可变对象的情况。

## 附8：关于id()的思考和延伸

### （1）`id()`究竟表示什么

> Python id() function returns the “identity” of the object. The identity of an object is an integer, which is guaranteed to be unique and constant for this object during its lifetime. Two objects with non-overlapping lifetimes may have the same id() value. **In CPython implementation, this is the address of the object in memory.**

因此说，`id()` 在 CPython 中就表示对象object的地址。

例如 `a=24`，`b=24`，`a` 和 `b` 指向一个相同的对象 `24`，而 `a` 和 `b` 都是对 `24` 这个对象的引用，也即，`a`，`b`，`24` 的地址是一样的。

> <font color=blue>Python中变量名都是对所指向object的引用。</font>

### （2）`is` 和 `==`

字符串的比较运算比较的是字符串的内容，Python中还有一个`is`运算符（身份运算符），如果用`is`来比较两个字符串，它比较的是两个变量对应的字符串对象的内存地址，简单的说就是两个变量是否对应内存中的同一个字符串。

换言之，`a is b` 就相当于 `id(a) == id(b)`。

``` c++
s1 = 'hello world'
s2 = 'hello world'
s3 = s2

# 比较字符串的内容
print(s1 == s2, s2 == s3)    # True True
# 比较字符串的内存地址
print(s1 is s2, s2 is s3, s1 is s3)    # True True True

s2 = "Python"
print(s1, s2, s3)
# 比较字符串的内容
print(s1 == s2, s2 == s3)    # False False
# 比较字符串的内存地址
print(s1 is s2, s2 is s3, s1 is s3)    # False False True
```

在上面的例子当中，我们修改`s2`的值为`Pyhton`，此时`s3`所指向对象的地址依然和`s1`相同。

另外， Python 中会实现创建一个**小型的整形池**，范围为 [-5,256]，为这些整形开辟好内存空间，当代码中定义该范围内的整形时，不会再重新分配内存地址。不过处于性能的考虑，但凡是不可变对象，在同一个代码块中的对象，只有是值相同的对象，就不会重复创建，而是直接引用已经存在的对象。

### （3）特殊案例：切片

但是对于下面的例子，有一些特殊：

``` python
a = [1, 2, 3]
b = a[:]
c = a
print(a == b, b == c, a == c) # True True True
print(a is b, b is c, a is c) # False False True
```

这是因为在 Python 中，切片操作（如 `my_list[:]`）返回的是序列的 **浅拷贝**。这意味着返回的新对象是原始对象的一个独立副本，但对于包含可变对象的容器类型（如列表或字典）**，新对象中的元素仍然引用原始对象中的元素**。

``` C++
s1, s2, s3 = "hello", "world", "python"
a = [s1, s2, s3]
b = a[:]
print(a is b) # False
for e1, e2 in zip(a, b):
    print(e1 is e2, end=', ') # True, True, True
```

### （4）数据类型的可变性

首先，Python3 中有六个标准的数据类型：

1. Number
2. String
3. List
4. Tuple
5. Set
6. Dictionary

其中，Number，String 和 Tuple是值不可变的，List，Set 和 Dictionary 是值可变的。注意这里的值的可变性，需要与内存地址联系起来，例如对于 Number 来说，我们可以这样 `a=1; a=a+2;`，看起来我们修改了 `a`，但实际上我们只是创建了一个新对象并修改 `a` 的引用罢了，本质上我们没有修改任何值。

因此说，对于**可变数据类型**的严格定义应该为：

> 当该数据类型的对应变量的值发生了改变，那么它对应的内存地址不发生改变，对于这种数据类型，就称可变数据类型。



## 附9： `__str__`和`__repr__`

一言以蔽之，`__repr__` 适用于程序员调试，因此它的返回结果应该更准确； `__str__` 适用于最终用户，因此它的返回结果可读性应该更强。

当直接查看对象的时候调用的是`__repr__`方法，对象需要转字符串的时候调用的是`__str__`方法。

``` PYTHON
import datetime
today = datetime.datetime.today()
print(str(today))
>>> 2019-10-20 20:59:47.003003
print(repr(today))
>>> datetime.datetime(2019, 10, 20, 20, 59, 47, 3003)
```

 **为什么每个类都最好有一个` __repr__ `方法**，**`__str__`的默认实现就是调用`__repr__`方法。**

## 附10：缺失的Char类型

在Python中，确实没有单独的`char`类型，只有`str`类型。这是因为Python的设计理念追求简洁和一致性。以下是一些原因：

1. **字符串是不可变的**：在Python中，字符串是不可变的对象，意味着一旦创建，字符串的内容不能被更改。由于字符通常是字符串的基本构成单元，Python选择将字符和字符串视为同一类型，即`str`。
2. **简化数据模型**：通过仅使用`str`类型，Python简化了数据模型，减少了开发者需要记住的数据类型数量。这样可以减少混淆，特别是对于新手来说。
3. **灵活性**：`str`类型支持任意长度的文本，因此可以用一个长度为1的字符串表示一个字符。这种设计让字符和字符串的处理更加一致和灵活。
4. **Unicode支持**：Python中的字符串是Unicode字符串，可以表示多种语言的字符。使用`str`类型使得处理不同字符集变得更加简单。

总的来说，Python通过将字符作为单字符字符串来处理，保持了语言的简洁性和一致性。

## 附11：Hello,World的由来

按照行业惯例，我们学习任何一门编程语言写的第一个程序都是输出`hello, world`，因为这段代码是伟大的丹尼斯·里奇（C语言之父，和肯·汤普森一起开发了Unix操作系统）和布莱恩·柯尼汉（awk语言的发明者）在他们的不朽著作*The C Programming Language*中写的第一段代码。

## 附12：分隔符

我们用Python写程序，最好每一行代码中只有一条语句。虽然使用`;`分隔符可以将多个语句写在一行代码中，但是最好不要这样做，因为代码会变得非常难看。

## 附13：冯·诺依曼机器

计算机的硬件系统通常由五大部件构成，包括：**运算器**、**控制器**、**存储器**、**输入设备**和**输出设备**。其中，运算器和控制器放在一起就是我们常说的**中央处理器**，它的功能是执行各种运算和控制指令。刚才我们提到过程序是指令的集合，写程序就是将一系列的指令按照某种方式组织到一起，然后通过这些指令去控制计算机做我们想让它做的事情。目前，我们使用的计算机基本都是“冯·诺依曼体系结构”的计算机，这种计算机有两个关键点：一是要将**存储设备与中央处理器分开**；二是将**数据以二进制方式编码**。

## 附14：开箱即用

在很多场景下，面向对象编程其实就是一个三步走的问题。第一步定义类，第二步创建对象，第三步给对象发消息。当然，有的时候我们是不需要第一步的，因为我们想用的类可能已经存在了。之前我们说过，Python内置的`list`、`set`、`dict`其实都不是函数而是类，如果要创建列表、集合、字典对象，我们就不用自定义类了。当然，有的类并不是Python标准库中直接提供的，它可能来自于第三方的代码。在某些特殊的场景中，我们会用到名为“内置对象”的对象，所谓“内置对象”就是说上面三步走的第一步和第二步都不需要了，因为类已经存在而且对象已然创建过了，直接向对象发消息就可以了，这也就是我们常说的“开箱即用”。

## 附15：编码解码

编码是根据一种编码规则，将我所要表达的信息用代码去表示出来；解码是根据解码规则（如果是对称加密的话，编码规则和解码规则是同一个规则），将代码解读出来。简而言之就是同一信息在两种不同的规则下的转换。Python中字符的默认编码格式为Unicode

## 附16: 上下文

上下文在不同的地方表示不同的含义，要感性理解。在编程中 `context` 上下文其实说白了就是环境。

例如 一个 **APP** 应用，在切换界面的时候，要保存你是在哪个屏幕跳过来的等等信息，以便你点击返回的时候能正确跳回，如果不存肯定就无法正确跳回了。

再比如线程、协程进行任务切换时，程序怎么能知道切换到另一个任务，是从头开始执行还是从中间呢？其上下文就起到作用，就是任务本身会对其环境进行保存，做到哪里了，做了多少，各种状态都会标识记录，从而形成了上下文环境，因此在切换时根据每个任务的上下文环境，继续执行，从而达到多任务。

## 附17: 三方库

一方：（一方包，一方库），一般指的是本项目或者本工程中的类和方法、接口等。

二方：（二方包，二方库），一般指的是公司内部的依赖库，公司内部其他项目发布的jar包，如公司项目平台的核心依赖包。

三方：（三方包，三方库），一般指的是外部的开源库或开源项目贡献的jar， 比如apache、google、Ali等发布的依赖

## 附18：命名规范

在Python中，首推蛇形命名法，特殊的对于类名使用驼峰式命名法。下面是一些对于具体情况的规范：

<left>1. 常量</left>

* 常量使用 **全大写字母**，并用 **下划线** 分隔单词。
* 常量通常放在模块的开头。

<left>2. 变量和函数</left>

* 使用 **小写字母** 和 **下划线** 分隔单词（snake_case）。
* 避免使用缩写，除非缩写是公认的或自解释的。
* 名称应当简短且有描述性，清晰传达变量或函数的用途。

<left>3. 类名</left>

* 使用 **首字母大写的驼峰式命名法（PascalCase）**。
* 类名应尽量是名词，因为类通常表示某种事物或实体。

<left>4. 模块名和包名</left>

* 使用 **全小写字母**，可以用 **下划线** 分隔单词（不过推荐用短小的单词）。

<left>5. 文档注释</left>

* 使用清晰的文档字符串 (`"""docstring"""`) 为模块、类和函数提供简要的描述，帮助解释代码的作用。
* 使用注释来解释复杂逻辑或非自明的代码段。

<left>6. 类方法</left>

* 私有成员两个下划线包围
* 受保护的成员一个下划线包围

## 附19：三目运算符

Python 是一种极简主义的编程语言，它没有引入`?:`这个新的运算符，而是使用已有的 `if else` 关键字来实现相同的功能。`maxn = a if a > b else b`，即 `exp1 if condition else exp2`

## 附20：标量、矢量和向量

在数学和物理学中，标量（scalar）、矢量（vector）和向量（vector）是基本的概念，它们在描述物理量和数学量时起着重要作用。尽管“矢量”和“向量”在中文中可以通用，但它们的使用情境稍有不同。以下是它们的定义和区别：

* 标量** 和 **矢量/向量** 的主要区别在于是否具有方向：标量没有方向，只有大小（例如温度，体积）；矢量/向量既有大小又有方向（例如速度，力）。
* **矢量** 和 **向量** 本质相同，只是用法上略有不同。在数学领域，通常使用“向量”一词，而在物理学中，更常使用“矢量”来描述具有方向的物理量。

## 附21：Serialization

维基百科上的解释是：“序列化（serialization）在计算机科学的数据处理中，是指将数据结构或对象状态转换为可以存储或传输的形式，这样在需要的时候能够恢复到原先的状态，而且通过序列化的数据重新获取字节时，可以利用这些字节来产生原始对象的副本（拷贝）。与这个过程相反的动作，即从一系列字节中提取数据结构的操作，就是反序列化（deserialization）”。





