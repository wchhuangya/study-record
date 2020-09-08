## 异常

### 错误

由于逻辑或语法导致一个程序无法正常执行的问题

> 有些错误是未知的

### 定义

1. 程序出错时标识的一种状态
2. 当异常发生时，程序不会再向下执行，而转去调用该函数的地方，等待处理此错误并恢复到正常的状态

### 作用

1. 通知上层调用者有错误产生需要处理
2. 用作信号

### try-except

```python
try:
  可能触发异常的语句
except 错误类型1 [as 变量1]:
  异常处理语句1
except 错误类型2 [as 变量2]:
  异常处理语句2
except 错误类型3 [as 变量3]:
  异常处理语句3
...
except: # 可以捕获任何错误类型
  异常处理语句 other
else:
  未发生异常时执行的语句
finally:
  最终执行语句
```

> 最简单的形式可以没有 else、finally 语句

说明：

1. `as` 语句是用于绑定错误对象的变量，可以省略不写
2. `except` 子句可以有一个或多个，但至少要有一个
3. `else` 子句最多只能有一个，也可以省略不写
4. `finally` 子句最多只能有一个，也可以省略不写

### try-finally

```python
try:
  可能触发异常的语句
finally:
  最终语句
```

> finally 子句不可省略
>
> 一定不存在 except 子句
>
> 该语句不会改变程序的 正常/异常 状态

作用：通常用该语句来做触发异常时必须要处理的事情，无论异常是否发生，`finally` 子句都会被执行

### raise

触发一个错误，让程序进入异常状态

语法：

```python
raise 异常类型
或者
raise 异常对象
```

### assert

断言语句，当真值表达式为 `False` 时，用错误数据创建一个 `AssertionError` 类型的错误，并进入异常状态

```python
assert 真值表达式，错误数据（通常是字符串）
```

它的作用类似于：

```python
if 真值表达式 == False:
  raise AssertionError(错误数据)
```

### 使用异常机制的原因

在程序调用层数较深时，向主调函数传递错误信息需要用 `return` 语句层层传递比较麻烦，用异常机制处理简单

## 迭代器

用 `iter`（可迭代对象）函数返回的对象（实例），迭代器可以用 next(it) 函数获取可迭代对象的数据

### 迭代器函数

`iter(iterable)` 从可迭代对象中返回一个迭代器，`iterable` 必须是一个能提供迭代器的可迭代对象。

`next(iterator)` 从迭代器 `iterator` 中获取下一条记录，如果无法获取下一条记录，则触发 `StopIteration` 异常

### 说明

1. 迭代器是访问可迭代对象的一种方式
2. 迭代器只能向前取值，不能后退
3. 用 `iter` 函数可以返回一个可迭代对象的迭代器

### 用途

迭代器对象能使用 `next` 函数获取下一个元素

### 迭代工具函数

用于生成个性化的可迭代对象

#### zip 函数

`zip(iter1 [, iter2, iter3, ...])`

该函数返回一个 `zip` 对象，此对象用于生成一个元组，此元组的个数由最小的可迭代对象决定

```python
names = ['中国电信', '中国移动', '中国联通']
phones = [10000, 10086, 10010]

for n,p in zip(names, phones):
  print(n, '的客服电话是：', p)
  
# 以下是打印结果
# 中国电信 的客服电话是： 10000
# 中国移动 的客服电话是： 10086
# 中国联通 的客服电话是： 10010
```

#### enumerate 函数

`enumerate(iterable [, start])`

生成带索引的枚举对象，返回迭代类型为：索引-值对（`index, value`）默认索引从 0 开始，也可以使用 `start` 绑定

```python
names = ['中国电信', '中国移动', '中国联通']

for n in enumerate(names):
  print(n)
  
# 以下是打印结果
# (0, '中国电信')
# (1, '中国移动')
# (2, '中国联通')
```

## 生成器

能够动态提供数据的对象，生成器对象也是可迭代对象（实例）

### 生成器函数

含有 `yield` 语句的函数是生成器函数，此函数被调用时将返回一个生成器对象

```python
yield 表达式
```

#### 说明

1. `yield` 用于 `def` 函数中，目的是将此函数作为生成器函数使用
2. `yield` 用来生成数据，供迭代器 `next(it)` 函数使用
3. 生成器函数的调用将返回一个生成器对象，生成器对象是一个可迭代对象
4. 在生成器函数调用 `return` 时会生出一个 `StopIteration` 异常来通知 `next(it)` 函数不能在提供数据

## 文件

### 定义

1. 文件是存储数据的单位
2. 文件通常用来长期存储数据
3. 文件中的数据是以**字节**为单位**顺序存储**的

### 操作流程

#### 打开文件

`open(filepath, mode='rt')`

打开一个文件，返回此文件对应的文件流对象，如果打开失败，则会触发 `OSError` 错误

**mode 说明**

| 字符 | 含义                                                         |
| ---- | ------------------------------------------------------------ |
| 'r'  | 以只读方式打开（默认）                                       |
| 'w'  | 以只写方式打开，删除原有文件内容（如果文件不存在，则创建改文件并以只写方式打开） |
| 'x'  | 创建一个新文件，并以写模式打开这个文件，如果文件存在则会产生 FileExistsError 错误 |
| 'a'  | 以只写方式打开一个文件，如果有原文件则追加到文件末尾         |
| 'b'  | 用二进制模式打开                                             |
| 't'  | 文本文件模式打开（默认）                                     |
| '+'  | 为更新内容打开一个磁盘文件（可读可写）                       |

> 1. 缺省模式是 'rt'
> 2. 'w+b' 可以实现二进制随机读写，当打开文件时，文件内容将被清零
> 3. 'r+b' 以二进制读和更新模式打开文件，打开文件时不会清空文件内容
> 4. 'r+' 以文本模式读和更新模式打开文件，打开文件时不会清空文件内容

#### 读写文件

`python` 文件读写的类型有两种：

1. 文本文件（`text file`）
2. 二进制文件（`binary file`）

##### 文本文件的操作

默认文件中存储的都是字符数据，以行为单位进行分割，在 `python` 内部统一用 `\n` 作为换行符进行分隔

##### 各种操作系统的换行符

1. `Linux` 换行符：`\n`
2. `Windows` 换行符：`\r\n`
3. 旧的 `Macintosh` 换行符：`\r`
4. 新的 `Mac OS` 换行符：`\n`

#### 关闭文件

`File.close()` 

关闭文件，释放系统资源

### 标准输入输出文件

`sys.stdin` ：默认为标准键盘输入设备

`sys.stdout` ：默认为屏幕终端

`sys.stderr` ：默认为屏幕终端

标准输入输出文件不需要打开和关闭就可以使用

### 汉字编码

#### 国标系列

`GB18030` ：二字节或四字节编码（最迟的，2005年，2 万 7 千多个汉字）

`GBK`         ：二字节编码（次早的，1995年，2 万 1 千多个汉字）

`GB2312`   ：二字节编码（最早的，1980年，6000 多个汉字）

> windows 常用

#### 国际标准

`Unicode`    <--->   `UTF-8`

> Linux、Mac OS X、IOS、Android 常用

#### python 编码字符串

`gb2312` 、`gbk` 、`gb18030` 、`utf-8`、`ascii` ……

### 编码注释

在源文件的第一行或第二行写下如下内容为编码注释：

`# -*- coding:utf-8 -\*-`

## 面向对象

### 类

拥有相同属性和行为的对象分为一组，即为一个类。类是用来描述对象的工具，用类可以创建同类对象。

#### 创建

```python
class 类名(继承列表):
  '''类的文档字符串'''
  实例方法定义（类内的行数称为方法 method）
  类变量定义
  类方法定义
  静态方法定义
```

> 类如果没有继承可以不写继承列表

#### 构造函数

创建这个类的实例对象，并返回此实例对象的引用关系。

#### 实例（对象）说明

1. 实例有自己的作用域和命名空间，可以为该实例添加实例变量（属性）
2. 实例可以调用类方法和实例方法
3. 实例可以访问类变量和实例变量

#### 实例方法

```python
class 类名(继承列表):
  def 实例方法名(self, 参数1, 参数2, ...):
    '''实例方法的文档字符串'''
    语句块
```

##### 说明

1. 实例方法实质是函数，是定义在类内的函数
2. 实例方法至少有一个形参，第一个形参代表调用这个方法的实例，一般命名为：`self`

##### 调用语法

`实例.实例方法名(调用传参)` 或者

`类名.实例方法名(实例, 调用传参)`

#### 属性（实例变量）

每个实例都可以有自己的变量，此变量称为实例变量（也叫属性）

##### 赋值规则

1. 首次为属性赋值则创建此属性
2. 再次为属性赋值则改变属性的绑定关系

##### 作用

用来记录对象自身的数据

##### 删除属性

`del 对象.实例变量名`

使用 `del` 语句可以删除一个对象的实例变量

#### 初始化方法

对新创建的对象添加实例变量（属性）或相应的资源

```python
class 类名(继承列表):
  def __init__(self [, 形参列表]):
    语句块
```

> 1. 初始化方法必须为 `__init__ `，不可改变
> 2. 初始化方法会在构造函数创建实例后自动调用，且此实例自身通过第一个参数 `self` 传入 `__init__` 方法中
> 3. 构造函数的实参将通过 `__init__` 方法的形参列表传入 `__init__` 方法中
> 4. 初始化方法内部如果需要返回则只能返回 None

#### 析构方法

```python
class 类名(继承列表):
  def __del__(self):
    语句块
```

1. 析构方法不需要手动调用，在对象销毁时自动调用
2. 用于清理此对象所占用的资源

> 不建议在析构方法内做任何事情，因为对象销毁的时间难以确定

#### 预置实例属性

##### \_\_dict\_\_ 属性

此属性绑定一个存储此实例自身变量的字典，也就是说，实例的该属性里面，存放的是属于该实例的所有属性的字典

##### \_\_class\_\_ 属性

用于绑定创建此实例的类，可以借助此属性来访问创建此实例的类

#### 属性管理函数

`getattr(obj, name[, default])` ：

1. 从一个对象得到对象的属性；`getattr(x, 'y')` 等同于 `x.y`

2. 当对象的属性不存在时，如果给出 `default` 参数，则返回 `default`；如果没有给出 `default` 参数，则产生一个 `AttributeError` 错误

`hasattr(obj, name)` ：

1. 用给定的 `name` 返回对象 `obj` 是否有此属性
2. 这种做法可以避免在 `getattr(obj, name)` 时引发错误

`setattr(obj, name, value)` ：

1. 给对象 `obj` 的名为 `name` 的属性设置相应的值 `value`；`setattr(x, 'y', v)` 相当于 `x.y = v`

`delattr(obj, name)` ：

1. 删除对象 `obj` 中的 `name` 属性，`delattr(x, 'y')` 等同于 `del x.y`

#### 类变量

类变量是类的属性，此属性属于类，

##### 作用

用来记录类相关的数据

##### 说明

1. 类变量可以通过类直接访问
2. 类变量可以通过类的实例直接访问
3. 类变量可以通过此类实例的 `__class__` 属性间接访问

#### 文档字符串

类内第一个没有赋值给任何变量的字符串是类的文档字符串

类的文档字符串可以使用 `help()` 函数查看

#### \_\_slots\_\_ 列表

限定一个类的实例只能有固定的属性（实例变量），通常为防止错写属性名而发生运行时错误

```python
class Student:
  __slots__ = ['name', 'score']
  def __init__(self, name, score):
    self.name = name
    self.score = score
    
stu1 = Student('zhangsan', '90')
stu1.socre = 98  # 编译时会报错
```

> 含有 `__slots__` 列表的类创建的实例对象没有 `__dict__` 属性，即此类实例的变量不用字典来保存对象的属性（实例变量）

#### 类方法

`@classmethod`

类方法是描述类的行为的方法，类方法属于类

> 1. 类方法需要使用 `@classmethod` 装饰器定义
> 2. 类方法至少有一个形参，第一个形参用于绑定类，约定写为 `cls`
> 3. 类和该类的实例都可以调用类方法
> 4. 类方法不能访问此类创建的实例的属性，只能访问类变量

#### 静态方法

`@staticmethod`

静态方法不属于类，也不属于类的实例，它相当于定义在类内的普通函数，只是它的作用域属于类

#### 继承 / 派生

##### 定义

1. 继承是指从已有的类衍生出新类，新类具有原类的行为，并能扩展新的行为
2. 派生就是从一个已有类中衍生（创建）新类，在新类上可以添加新的属性和行为

##### 目的

1. 继承是延续旧类的功能
2. 派生是为了在旧类的基础上添加新的功能

##### 名词

基类：`base class`

超类：`super class`

父类：`father class`

派生类：`derived class`

子类：`child class`

##### 作用

1. 用继承派生机制，可以将一些共有功能加载基类中，实现代码的共享
2. 在不改变基类的基础上改变原有功能

```python
class 类名(基类名):
  语句块
  
# 单继承是指派生类有一个基类衍生出来的类
```

##### 说明

1. 任何类都直接或间接的继承自 `object` 类

2. `object` 类是一切类的超类（祖类）

3. 子类如果重写了 `__init__` 方法，父类的初始化方法就不会再被调用了，如果还想调用，这样写：

   ```python
   class MyList(list):
     def __init__(self, *args):
       self.__init__(*args) # 保证父类的初始化方法被正确的调用
       # 下面就可以写子类自己初始化方法中的一些操作了
   ```

#### 覆盖

在有继承关系的类中，子类实现了与基类同名的方法，在子类实例调用该方法时，实例调用的是子类中覆盖版本的方法，这种现象叫做覆盖

##### 调用父类的方法

`super(type, obj)` 返回绑定超类的实例

#### 常用函数

##### `issubclass(cls, clas_or_tuple)`

判断一个类是否继承自其他的类，如果此 `cls` 是 `class` 或 `tuple` 中的一个派生子类则返回 `True`，否则返回 `False`

##### 查看 python 中内建类的继承关系

`help(_builtins__)`

#### 封装

封装指隐藏类的实现细节，让使用者不用关心这些细节；

封装的目的是让这些使用者尽可能少的进行实例变量（属性）的操作

#### 私有属性

`python` 类中，以双下划线 `__` 开头，不以双下划线结尾的标识符为私有成员，在类的外部无法直接访问

##### 扩展

1. `_xxx` ：不能用于 `from import *`；表示的是 `protected` 类型的变量，即该变量只能本身与子类访问
2. `__xxx` ：表示私有类型的变量或方法，只能允许这个类本身访问，连子类也不可以
3. `__xxx__` ：系统的特殊方法，不建议使用这样的命名方式

#### 多态

只在继承、派生关系的类中，调用基类对象的方法，实际能调用子类的覆盖版本方法的现象叫多态

##### 说明

1. 多态调用的方法与对象相关，不与类型相关
2. `python` 的全部对象都只有”运行时状态（动态）“，没有 `C++/Java` 里的编译时状态（静态）

#### 多继承

指一个子类继承自两个或两个以上的基类

```python
class 类名(基类名1, 基类名2, ...):
  语句块
```

##### 说明

1. 一个子类同时继承自多个父类，父类中的方法可以被同时继承下来
2. 如果两个父类中有同名的方法，而在子类中有没有覆盖此方法时，调用结果难以确定

> 使用多继承可能会出现标识符（名字空间冲突）的问题，要谨慎使用；
>
> 一般来说，继承列表中先写哪个类，先使用哪个类的方法

#### 继承的 MRO（Method Resolution Order）问题

类里面用 `__mro__` 属性来记录继承方法的查找顺序

> 在多继承里面，super() 的调用，不是按照继承关系调用的，而是按照 `__mro__` 里面的顺序调用的

#### 重写

在自定义的类内添加相应的方法，让自定义的类生成的对象（实例）像内建对象一样进行内建的函数操作

##### 对象转字符串函数重写

`repr(obj)` ：返回一个能代表此对象的**表达式**字符串，通常：`eval(repr(obj)) == obj`

```python
def __repr__(self):
  return 能够表达 self 内容的字符串
```

`str(obj) ` ：使给定的对象返回一个字符串（这个字符串通常是给人看的）

```python
def __str__(self):
  return 人能看懂的字符串
```

> 1. str(obj) 函数有限调用 `obj.__str__()` 方法返回字符串
> 2. 如果 obj 没有 `__str__()` 方法，则调用 `obj.__repr__()` 方法返回的字符串
> 3. 如果 obj 没有 `__repr__()` 方法，则调用 object 类的 `__repr__()` 实例方法显示 `<xxxx>` 格式的字符串

### with 语句

```python
with 表达式1 [as 变量1], 表达式2 [as 变量2]:
  语句块
```

#### 作用

使用与对资源进行访问的场合，确保使用过程中不管是否发生异常，都会执行必须的清理操作，并释放资源

适用的场景：

1. 文件使用后自动关闭
2. 线程中锁的自动获取和释放

> 能够用 with 语句管理的对象必须是环境管理器

### 环境管理器

1. 类里面有 `__enter__` 和 `__exit__` 实例方法的类被称为环境管理器
2. 能够用 `with` 语句管理的对象必须是环境管理器
3. `__enter__` 方法将在进入 `with` 语句时被调用，并返回有 `as` 变量管理的对象
4. `__exit__` 将在离开 `with` 语句时被调用，且可以用参数来判断在离开 `with` 语句时是否有异常发生并作出相应的处理

```python
class A:
  def __enter__(self):
    print('已经进入 with 语句')
    return self # 返回的对象将有 as 绑定
  
  def __exit__(self, exc_type, exc_val, exc_tb):
    '''
    exc_type：在没有异常时为 None，在出现异常时为异常类型
    exc_val：在没有异常时为 None，在出现异常时绑定错误对象
    exc_tb：在没有异常时为 None，在出现异常时绑定 traceback 对象
    '''
    print('已经离开 with 语句')
```

## 网络编程

### 面向连接的传输服务

#### 传输特征

提供可靠的数据传输，可靠性指数据传输过程中无丢失，无失序，无差错，无重复

#### 实现手段

数据传输断开前都需要进行传输和断开的确认

#### 三次握手

`tcp` 传输在数据传输前建立连接的过程

1. 客户端向服务器发送连接请求
2. 服务器收到请求后，回复确认消息，表示允许连接
3. 客户端收到服务器回复，进行最终标志发送确认连接

![image-20200321151656393](/Users/wchya/own/markdown/imgs/image-20200321151656393.png)

#### 四次挥手

`tcp` 传输在连接断开前进行断开确认的过程

1. 主动方发送报文告知被动方要断开连接
2. 被动方接收到请求后立即返回报文告知已经准备断开
3. 被动方准备就绪后再次发送报文告知可以断开
4. 主动方发送消息，确认最终断开

#### 应用情况

适用于传输较大的文件，网络情况良好，需要保证传输可靠性的情况。比如：网页的获取，文件下载，邮件传输，登录注册等

![image-20200321151857676](/Users/wchya/own/markdown/imgs/image-20200321151857676.png)

### 面向无连接的传输服务

基于 `udp` 协议的传输

#### 传输特点

不保证传输的可靠性，传输过程没有连接和断开的流程，数据收发自由

#### 应用情况

网络情况较差，对传输可靠性要求不高，需要提升传输效率，需要灵活收发消息。比如：网络视频，群聊，广播发送等。

### socket 套接字编程

#### 目标

根据 `socket` 接口提供的接口函数，经过组合使用，完成基于 `tcp` 或 `udp` 的网络编程

#### 套接字

完成网络编程的一种手段，编程方案

#### 流式套接字（SOCK_STREAM）

传输层基于 `tcp` 协议的套接字编程方案

##### 1. 创建套接字

```python
sockfd = socket.socket(socket_family = AF_INET, socket_type = SOCKET_STREAM, proto = 0)
# 参数说明：
# socket_family ：选择地址族类型
# socket_type ：套接字类型 （SOCK_STREAM ：流式套接字，SOCK_DGRAM ：数据报套接字）
# proto ：选择子协议类型，通常为 0，默认值为 0
# 返回值说明：返回套接字对象
# 注意：创建流式套接字时，三个参数都可以不写，使用默认
```

##### 2. 绑定服务端地址

```python
sockfd.bind(addr)
# 功能：绑定 IP地址
# 参数：元组 （ip，port）
# 注意：
#			1. 作为服务端的套接字需要绑定地址和端口，方便客户端寻找定位
#			2. 作为客户端的套接字不需要该方法，也可以绑定，但是意义不大
```

##### 3. 设置监听套接字（服务端）

```python
sockfd.listen(n)
# 功能：将套接字设置为监听套接字，创建监听队列
# 参数：正整数，表示监听队列大小
# 注意：1. 只有监听套接字（服务端）才需要这一步
#			 2. 一个监听套接字可以连接多个客户端套接字
```

##### 3. 建立连接（客户端）

```python
sockfd.connect(serv_addr)
# 功能：建立连接
# 参数：元组，服务端地址与端口
```

##### 4. 等待处理客户端的连接请求

```python
connfd, addr = sockfd.accept()
# 功能：阻塞等待处理客户端连接
# 返回值：
#				connfd ：客户端连接套接字
#				addr ：连接的客户端地址
```

##### 5. 消息收发

```python
connfd.recv(buffersize)
# 功能：接收对应客户端消息
# 参数：一次最多接收多少字节
# 返回值：接收到的内容
# 注意：如果没有消息则会阻塞

connfd.send(data)
# 功能：发送消息给对应客户端
# 参数：要发送的内容，必须是 bytes 格式（python3 中规定，只要是网络消息的发送，必须是 bytes 格式）
# 返回值：实际发送消息的大小（字节）

# 注意：消息收发需要客户端和服务端之间的配合，避免两边都出现 recv 阻塞
```

##### 6. 关闭套接字

```python
sockfd.close()
connfd.close()
# 功能：关闭套接字
```

> 套接字传输注意事项：
>
> 1. 监听套接字只要存在客户端即可发送消息，但是最终连接的处理需要 accept 进行处理
> 2. 如果连接的另外一端退出，则 recv 会立即返回空字符串，不再阻塞
> 3. 连接的两端中有一端退出后，存在的一端再试图使用 send 发送消息时就会出现 BrokenPipeError
> 4. 服务端流程：socket() ---> bind() ---> listen() ---> accept() ---> recv()/send() ---> close()
> 5. 客户端流程：socket() ---> connect() ---> recv()/send() ---> close()

#### 网络收发缓冲区

##### 缓冲区作用

1. 协调数据收发（处理）速度
2. 减少交互次数

`send` 和  `recv` 实际上是和缓冲区进行交互，发送缓冲区满时就无法发送，接收缓冲区满时 `recv` 才阻塞

#### TCP 粘包

##### 产生原因

`tcp` 套接字以字节流方式传输，没有消息边界。发送和接受并不能保证每次发送都能及时的被接收

##### 影响

如果每次发送内容表达一个独立的含义，此时可能需要处理粘包，防止产生歧义

##### 处理方法

1. 每次发送的消息添加结尾标志（认为增加消息边界）
2. 发送数据结构体
3. 协调收发速度，每次发送后都预留接收时间

#### http 协议

超文本传输协议，是一个应用层协议

##### 用途

1. 网页数据的传输
2. 数据传输的方法

##### 特点

1. 应用层协议，传输层使用 `tcp` 服务
2. 简单，灵活，多种语言都有 `http` 相关操作接口
3. 无状态的协议，即不记录用户传输的状态
4. `http 1.1`，支持持久连接

##### 一次数据交互过程

一端通过 `http` 请求的格式发送具体请求内容，另一端接受 `http` 请求，按照协议格式解析，获取真实请求后按照 `http` 协议响应格式组织回复内容，会发给请求方，完成一次数据交互。

##### http 请求（request）

```
请求行：表明了具体的请求类别和请求内容
		格式： 	GET		  /		    HTTP/1.1
				 请求类别 请求内容    协议版本
				 请求类别：表示请求的种类
				 				GET			获取网络资源
				 				POST		提交一定的附加信息，得到返回结果
				 				DELETE	删除服务器资源
				 				HEAD		获取相应头
				 				PUT			更新服务器资源
				 				CONNECT	预留
				 				TRACE		用于测试
				 				OPTIONS	获取服务器性能信息
请求头：对请求内容的具体描述信息，以键值对进行描述，每一个键值对占一行
空行
请求体：请求参数或者是提交内容
```

##### http 相应（response）

```
响应行：反馈相应的情况
		格式：		HTTP/1.1			200				OK
						协议版本			响应码			附加信息
				响应码：相应的具体情况
							1xx：提示信息，表示请求成功
							2xx：相应成功
							3xx：相应需要重定向
							4xx：客户端错误
							5xx：服务端错误
				常见响应码：
							200：成功
							404：请求内容不存在
							401：没有访问权限
							500：服务器发生未知错误
							503：暂时无法执行
响应头：对相应内容具体描述，键值对，键由协议规定
空行
响应体：返回给请求端的具体内容
```



#### 数据报套接字（SOCK_DGRAM）

传输层基于 `udp` 协议的套接字编程方案

##### 1. 创建数据报套接字

```python
sockfd = socket(AF_INET, SOCK_DGRAM)
```

##### 2. 绑定地址

```python
sockfd.bind(addr)
```

##### 3. 消息的收发

```python
data, addr = sockfd.recvfrom(buffersize)
# 功能：接收 UDP 消息
# 参数：每次最多接收多大的消息
# 返回值：
#				data 接收到的数据
#				addr 消息发送端的地址
# 注意：一次接受一个数据包，如果数据大小大于 recvfrom 方法指定的消息，那么大于的部分将会丢失

sockfd.sendto(data, addr)
# 功能：发送 UDP 消息
# 参数：
#				data 发送的消息，bytesize 格式
#				addr 目标地址
# 返回值：发送的字节数
```

##### 4. 关闭套接字

```python
sockfd.close()
```

##### 广播

###### 地址

一个网段内有一个指定的广播地址，是该网段的最大地址：`x.x.x.255`

###### 广播风暴

一个网络中有大量的广播就会产生广播风暴占用大量带宽，影响正常的访问速度

#### 文件描述符：

1. 每一个 IO 事件操作系统都会分配一个不同的正整数作为编号，该正整数则为这个 IO 的文件操作符
2. 文件描述符是操作系统识别 IO 的唯一标识
3. python中，标准输入、输出、错误流的文件操作符分别是：0，1，2，即：system.stdin，system.stdout，system.err

#### IO

##### IO 密集型程序

在程序执行过程中存在大量 `IO` 操作，而 `CPU` 运算操作较少。消耗 `CPU` 少，运行效率低

##### 计算密集型程序（cpu 密集型程序）

在程序执行中 `CPU` 运算较多，`IO` 操作相对较少。消耗 `CPU` 大，运行速度快

##### 阻塞 IO

是 `IO` 的默认形态，是效率较低的一种 `IO` 情形

阻塞情况分为：

1. 因为某种条件没有达成造成的阻塞，例如：`accept，input，recv`
2. 处理 `IO` 数据传输时间较长形成的阻塞，例如：`网络传输过程，文件读写过程`

##### 非阻塞 IO

通过修改 `IO` 时间的属性，使其变成非阻塞状态（让一些条件阻塞函数不再阻塞）

> 非阻塞 IO 往往和循环判断一起使用

##### 超时检测

将原本阻塞的函数设置一个最长阻塞时间。若时间内条件达成则正常运行，如果任然阻塞则视为超时，继续向下运行或产生异常。

##### IO 多路复用

同时监控多个 `IO` 事件，当那个`IO` 事件准备就绪就执行那个 `IO` 事件，以此形成可以同时操作多个 `IO` 的并发行为，避免一个 `IO` 阻塞，造成所有的 `IO` 都无法执行。

`IO` 准备就绪：是一种 `IO` 必然要发生的临界状态

##### 步骤

1. 将 IO 设置为关注 IO
2. 将关注 IO 提交给内核监测
3. 处理内核给我们反馈的准备就绪的 IO

方案有：

1. `select ---> windows, linux, unix`
2. `poll ---> linux, unix`
3. `epoll ---> linux, unix`

```python
import select

rs, ws, xs = select(rlist, wlist, xlist[, timeout])
# 功能：监控 IO 事件，阻塞等待 IO 时间发生
# 参数：rlist		列表，存放我们监控等待处理的 IO 事件
#			 wlist		列表，存放我们要主动操作的 IO 事件
#			 xlist		列表，我们要关注出错处理的 IO 事件
# 		 timeout	超时时间
# 返回值：rs		列表，rlist 准备就绪的 IO
#		 		 ws		列表，wlist 准备就绪的 IO
#				xs		列表，xlist 准备就绪的 IO

# 注意：
#			1. wlist 中如果有 IO 事件则 select 立即回返回
#			2. 在处理 IO 过程中不要处理一个客户端长期占有服务端使服务端无法运行到 select 的情况
#			3. IO 多路复用占用计算机资源少，计算机效率高
```



```python
from select import select
# 1. 创建 poll 对象
p = select.poll()

# 2. 添加注册事件
p.register(s, POLLIN) # 将某个时间添加到关注事件中
# 常用的特定事件：
#			POLLIN		相当于 r 事件
#			POLLOUT		相当于 w 事件
#			POLLERR		相当于 x 事件
#			POLLHUP		断开事件
#			POLLNVAL	无效数据
p.unregister(s) # 将事件从关注事件中移除

# 3. 阻塞等待 IO 事件发生
events = p.poll()
# 功能：阻塞等待 IO 发生
# 返回值：events 是一个列表，列表中给出的每一个元素都是一个元组，代表一个发生的 IO 事件：
#						[(fileno,          event),(),()...]
#					就绪IO的文件描述符    具体就绪事件
# 注意：需要自己维护一个关注的 IO 事件字典：{s.fileno() : s}

# 4. 处理具体的 IO
```



```python
# epoll 
# 使用方法：基本与 poll 方法相同
# 1. 将生产对象 poll() 改为 epoll()
# 2. 将所有 poll 对象事件改为 epoll 对象事件（前面加 E）

# 区别
# epoll 的效率要比 poll 和 select 高
# epoll 的事件触发方式更多
```

### 本地套接字

#### linux 文件

`b（块设备文件）c（字符设备文件）d（目录）-（普通文件）l（链接）s（套接字）p（管道）`

#### 作用

用于本地不同的程序间进行通信

#### 创建流程

##### 1. 创建本地套接字

```python
sockfd = socket(AF_UNIX, SOCK_STREAM)
```

##### 2. 绑定本地套接字文件

```python
import os
# 先判断目录下是否存在同名文件
os.path.exists(path)
# 如果存在，将源文件先移除
os.remove(path)
# 选定文件位置和名称
sockfd.bind(path)
```

##### 3. 监听

```python
sockfd.listen()
```

##### 4. 消息收发

```python
recv, send
```

### 多任务编程

#### 意义

充分利用计算机的资源提高程序的运行效率

#### 定义

通过应用程序利用计算机的多个核心达到同时执行多个任务的目的，一次提高计算机运行效率

#### 实施方案

多进程，多线程

#### 并行

多个计算机核心在同时处理多个任务，这时，多个任务间是并行关系

#### 并发

同事处理多个任务，内核在多个任务间不断的切换，达到好像都在运行处理的效果。但实际一个时间点内核只能处理其中一个任务。

#### 程序

是一个可执行的文件，是静态的占有磁盘空间，不占有计算机的运行资源

#### 进程

程序在计算机中的一次运行过程。进程是一个动态过程的描述，占有计算机的资源，有一定的生命周期。

> 同一个程序的不同运行过程是不同的进程，占用资源和生命周期都不一样

##### 创建流程

1. 用户空间通过运行程序或者调用接口发起创建进程
2. 操作系统接受用户请求开始创建进程
3. 操作系统分配计算机资源确定进程状态，开辟进程空间等工作
4. 操作系统将创建好的进程提供给应用程序使用

#### CPU 时间片

如果进程占有计算机核心，我们成为该进程 `cpu` 时间片

> 1. 多个任务是争夺 cpu 的关系
> 2. 谁占有 cpu 最终是操作系统决定

#### PCB（进程控制块）

在内存中开辟的一块空间，用来记录进程的信息

> 进程控制块是操作系统查找识别进程的标识

操作系统进程信息查看：`ps -aux`

```
PID(process Id)：在操作系统中每个进程都有一个唯一的 ID 号用来区别与其他进程。ID 号由操作系统自动分配，是一个大于 0 的整数
```

#### 父子进程

在系统中除了初始化进程，每一个进程都有一个父进程，可能有 0 个或多个子进程，由此形成了父子进程关系

> 查看进程树：`pstree` ，需要通过 `brew install pstree` 进行安装
>
> 查看父进程 PID：`ps -ajx`

#### 进程的状态

##### 三态

1. 就绪态：进程具备执行条件，等待系统分配资源
2. 运行态：进程占有 `CPU` 出于运行状态
3. 等待态：进程暂时不具备执行条件，阻塞等待满足条件后再执行

##### 五态（三态的基础上增加新建态、终止态）

1. 新建态：创建一个新的进程，获取资源的过程
2. 终止态：进程执行结束，资源释放回收的过程

#### 进程优先级

决定了一个进程的执行权限和占有资源的优先程度

> top 命令动态查看系统中的进程信息，用 <> 翻页

#### 进程特征

1. 进程之间运行互不影响，各自独立运行
2. 进程是操作系统资源分配的最小单元
3. 每个进程空间独立，各自占有一定的虚拟内存

## 小细节

### 空格的使用

1. 各种右括号前不用加空格
2. 逗号、冒号、分号前不要加空格
3. 函数的左括号前不要加空格
4. 序列的左括号前不要加空格
5. 操作符左右各加一个空格，不要为了对齐增加空格
6. 函数默认参数使用的赋值符左右省略空格
7. 不要讲多余语句写在同一行，尽管使用 ; 允许
8. `if/for/while` 语句中，即使执行语句只有一句，也必须另起一行