# Java

[toc]

> [Java 官方在线 API](https://docs.oracle.com/javase/8/docs/api/)

## 第一章 语言概述

### 软件开发

#### 软件

**软件分类：**

1. 系统软件：各种操作系统（Windows、Linux、MacOS、鸿蒙等），主要是跟计算机硬件打交道的
2. 应用软件：影音类软件、编程软件、即时通信类软件等

**定义：**

一系列按照特定顺序组织的计算机数据和指令的集合

#### 软件开发

制作软件的过程，包括：需求阶段、设计阶段（UED、数据库、软硬件架构）、研发阶段、测试阶段、上线阶段、运行维护阶段

### 人机交互方式

1. 卡带式：早期的计算机占地面积大，计算能力弱，早期的程序员将准备好的二进制的计算机程序打在卡带上，然后将卡带插入计算机中，经过漫长的等待，计算机根据卡带上的二进制程序给出最终的结果
2. 命令行（问答式）：典型的黑底白字的界面，程序员输入一个命令，电脑根据输入的命令给出不同的反应：1. 命令输入正确，电脑给出相应的行为响应；2. 命令输入错误，电脑给出错误提示，或者无响应
3. 图形化界面：电脑将常用的命令组装成外设一键式的操作（比如鼠标、键盘等），复杂的命令可以通过简单命令的组合达到同样的效果

> 知识补充：常用的命令

### 发展历史

Java 是由 Sun 公司于 1995 年推出的一门编程语言：

* 1995 ~ 2004 年，Sun 公司先后推出了 JDK 1.2，1.3，1.4
* 2004 年，推出了 JDK 1.5，并改名为 JDK 5.0，这是一个划时代的版本，奠定了 Java 的江湖地位
* 2005 年，推出了 JDK 6.0
* JDK 7.0，8.0 是一年推出一个，9.0，10.0，11.0 更是达到了半年一个版本的速度进行推出
* Sun 公司于 2019 年 3 月份推出了 JDK 最新的版本 12.0

### 与其它语言的对比

* Java 真的不难学
  * 学习简单（相比 C、C++）
  * 面向对象（不支持多继续）
  * 程序健壮（强类型的语言，异常处理机制健全）
  * 程序安全（内存管理机制）
* Java 真的很强大
  * 全世界程序员使用最多的一门语言
  * 具有完备的生态圏
  * 拥有世界范围影响力的框架
  * 语言性能比较高效

### 运行机制

> Java 程序可以跨平台使用

1. 解释型语言：JavaScript，一边读取程序，一边对程序里的内容逐行进行解释，效率比较低，有错误不容易在编码时发现
2. 编译型语言：Java，需要一个解释器来将程序源码编译为电脑可以运行的可执行文件
   1. 写代码源文件
   2. 使用 JavaC.exe 将源文件编译为相应的 class　文件（字节码文件）
   3. 使用 Java.exe 工具解释这个字节码文件，生成直接可以运行的二进制文件，交给 CPU 运行

### JVM

Java Virtual Machine，Java 虚拟机，目的是为了解析 Java 语言

> 它是 Java 语言跨平台的关键

### JDK 和 JRE

* JRE -- Java Runtime Environment，Java 运行时环境，主要包含了 Java 运行时的必要元素（如：JVM 运行时需要的支持）
* JDK -- Java Development Kits，Java 开发工具包，有 Sun 公司免费提供的 Java 开发的工具，是一种 SDK，Software Development Kits，软件开发工具包

> JDK 与 KRE 之间相互依赖，缺一不可

### Java 开发环境安装

1. 获取安装包
2. 安装 Java 开发环境
3. 配置 Java 环境变量

### Java 技术的不同发展方向

* `Java` 标准开发（`J2SE`、`Java SE`）：提供的是底层的支持，实现了桌面程序的开发
* `Java` 嵌入式开发（`J2ME`、`Java ME`）
* `Java` 企业开发（`J2EE`、`Java EE`）：主要是进行企业平台的搭建，现在已经主要的开发是互联网平台；

### PATH 与 CLASSPATH 区别

* `PATH`：操作系统提供的路径配置，定义所有可执行程序的路径
* `CLASSPATH`：是由 `JRE` 提供的，用于定义 `Java` 程序解释时类加载路径，默认的设置为当前所在目录加载，可以通过 `CLASSPATH=路径` 的命令形式来进行定义

> 关系：
>
> JVM → CLASSPATH 定义的路径 → 加载字节码文件

## 第二章 数据类型与运算符

### HelloWorld

```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello World！");
    }
}
```

这一段代码要注意的点：

* 目前我们所接触到的代码都是写在类 class 中的
* 类名与文件名称相同（如果类的访问修饰符不是 `public` ，而是默认——即什么都不写，那么文件名称可以和类名称不一致，但是最终生成的 `.class` 文件会与类的名称保持一致）
* 文件后缀是：`.java`
* main 方法的写法是固定写法
* 语句后面用分号结尾
* 注意代码的缩进和必要的空格，这样可以让代码保持良好的阅读性

编译&运行代码：

* 使用 `> javac Hello.java` 命令将刚刚写的源代码编译为相应的字节码
* 使用 `> java Hello` 命令将上一步生成的字节码文件生成可执行的二进行文件并运行
* 在控制台上，你将看到 `> Hello World!` 的输出内容

### IntelliJ IDEA

使用 `IDEA` 编写 `HelloWorld` ：

* 从 [官网]() 下载 `IntelliJ IDEA`，注意：只下载 `2020.2.3` 这一版本，主要是为了后面的破解
* 点击安装
* 打开 `IDEA` ，选择 `Create Project` ，在 `New Project` 界面的左侧，选择 `Java` ，确保右边的 `Project SDK` 是电脑上已经安装好的 `JDK 1.8`
* 创建项目名称，指定项目存放的位置

#### 快捷键

* 单行注释：<kbd>command</kbd> + <kbd>/</kbd>
* 多行注释：<kbd>ctrl</kbd> + <kbd>shift</kbd> + <kbd>/</kbd>
* 代码格式化：<kbd>option</kbd> + <kbd>command</kbd> + <kbd>L</kbd>

#### 小知识点

* `TODO` ：在 `IntelliJ IDEA` 中，正常的 `TODO` 注释会被自动识别并高亮显示，在 `TODO` 窗口中也会有响应的显示，用 `TODO` 注释来标记自己待开发的任务是一项非常常见的做法

### 标识符

代码中使用的一些名字，例如：

* 变量名
* 方法名
* 接口名
* 类名
* ……

#### 命名规范

* 标识符可以使用的字符范围：a～z，A～Z，0-9，_
* 标识符必须以英文字母开头
* 标识符严格区分大小写
* 标识符需要做到：见名知义
* 标识符需要用到驼峰命名法：
  
  * 大驼峰：所有单词的首字母都要大写；一般适用于 class 类名
  * 小驼峰：首字母小写，之后的每一个单词的首字母大写；一般适用于变量名、方法名
* 已经被 `Java` 或者系统占有的标识符不能使用，关键字和保留字不能使用
  
  > 例如 HelloWorld 程序中，变颜色的单词都不能使用

### 基本数据类型

| 整形  | 占据内存空间大小 |       数据范围        |
| :---: | :--------------: | :-------------------: |
| byte  |  1字节（8bit）   |     $ -127～128 $     |
| short |  2字节（16bit）  |   $ -32767～32768 $   |
|  int  |  4字节（32bit）  | $ -2^{31}～2^{31}-1 $ |
| long  |  8字节（64bit）  | $ -2^{63}～2^{63}-1 $ |

| 浮点型 | 占据内存空间大小 |       数据范围       |
| :----: | :--------------: | :------------------: |
| float  |  4字节（32bit）  | $ \pm3.4 * 10^{38} $ |
| double |  8字节（64bit）  |     $ 10^{308} $     |

| 字符型 | 占据内存空间大小 |   数据范围   |
| :----: | :--------------: | :----------: |
|  char  |  2字节（16bit）  | 可以保存中文 |

| 布尔类型 | 占据内存空间大小 |  数据范围   |
| :------: | :--------------: | :---------: |
| boolean  |    视情况而定    | true  false |

#### 数据类型使用建议（个人）

* 如果要描述数字首选的是：`int`（整数）、`double`（小数）
* 如果要进行数据传输或者是进行文字编码转换使用 `byte` 类型（二进制处理操作）
* 处理中文时最方便的操作是使用 `char` 类型来完成的
* 描述内存或文件大小，描述表的主键列（自动增长）可以使用 `long`

### 变量

变量是计算机内存中的一块存储空间，是存储数据的基本单元

格式：`数据类型 变量名 = 初始化数据;` 

> 变量名里面保存的数据，可以在程序的运行过程中发生改变

数据类型：约束当前变量是什么类型

变量名：方便操作变量的名字

= 赋值号：把赋值号右侧的数据赋值给左侧变量名

初始化数据：给变量赋值相应数据类型的值

```java
class Demo1 {
    public static void main(String[] args) {
        // 定义一个 int 类型的变量
        int nums = 100;
        System.out.println(nums);
    }
}
```

### 数据类型转换

主要是为了满足数据类型一致化的问题，在不同数据类型之间做数据的转换操作的一种方式。

#### 自动类型转换

核心思想就是小数据类型转换为大数据类型。

算数运算的规则：

1. 两个操作数有一个是 double，计算结果提升为 double
2. 两个操作数没有 double，但是有一个 `float`，计算结果提升为 `float`
3. 如果操作数中没有 `float`，有一个为 `long`，计算结果提升为 `long`
4. ……
5. 你看出来什么规律了吗？

> 1. 如果操作数中只有 short 或者 byte，那么最终的结果会被提升为 int
> 2. 任何类型与 String 类型相加时（+），实际为拼接，其结果自动提升为 String

```java
byte num1 = 10;
int num2 = 20;

num2 = num1 + num2;
// 问：最终，num2 是什么数据类型，为什么？
```

#### 强制类型转换

核心思想就是将大数据类型转换为小数据类型

```java
float num1 = 3.14F;
int num2 = 10;

num2 = num1 + num2; // 这里会有编译报错

// 正确的写法是：
num2 = (int) (num1 + num2);

// 问：最终 num2 是什么数据类型，值为多少？
```

* 利：可以满足数据类型的一致性要求
* 弊：原数据类型的强制转换过程中，会导致数据精度丢失，而且这样的丢失是不可逆的

### 运算符

#### 赋值运算符

`=` ：把左边的值赋值给右边的变量

#### 复合赋值运算符

`+=  -=  *=  /=  %=`

#### 算术运算符

`+、-、*、/、%、()` ：加、减、乘、除，求余 

规则：

* 从左到右
* 先乘除，后加减
* 除数不能为0
* 有括号先处理括号里的内容

`%` 针对的是两个整数，获得的结果是不能整除后的余数，如果可以整除，结果为 0 

```java
class Demo {
    public static void main(String[] args) {
        int num1 = 10;
        int num2 = 20;

        num1 = num1 + num2; // num1 = ? num2 = ?
        num1 = num1 - num2; // num1 = ? num2 = ?
        num1 = num1 * num2; // num1 = ? num2 = ?
        num1 = num1 / num2; // num1 = ? num2 = ?
        num1 = num1 % num2; // num1 = ? num2 = ?
    }
}
```

`+=、-=、*=、/=、%=` ：这些是复合运算符，作用是简化书写

```java
int num1 = 1, num2 = 2;

num1 += num2; // => num1 = num1 + num2
```

> 如果在除法中需要得到浮点类型的结果，把参与除法的任一操作数改为 double 类型的就可以了

##### 自增、自减

> 1. 该运算符很好用，但是容易引起阅读者的理解困难，或者引起初学者的困惑，小心使用
> 2. 这两个都是 一元运算符

`++` 、`--` ：

* 放在变量之后，首先执行当前语句，然后再执行自增、自减操作
* 放在变量之前，首先执行自增、自减操作，然后再执行当前语句

```java
int num1 = 1, num2 = 2;
System.out.println(num1++ + ++num2); // 最后结果是什么？为什么？
// 现在 n1 和 n2 的值又变成了什么
System.out.println(num1);
System.out.println(num2);
```

#### 比较运算符

`>  >=  <  <=  !=  ==`    这是 Java 中的写法

$>$   $ \geq $    $ < $    $ \leq $     $ \neq $      $ = $    这是数学中的表示法

关系运算符的结果是 **布尔值**

```java
System.out.println(4 > 3); // 结果是？
System.out.println(5 < 4); // 结果是？
System.out.println(3 >= 3); // 结果是？
System.out.println(6 != 8); // 结果是？
System.out.println(9 == 9); // 结果是？
```

#### 位运算符

`& | ^ ～ << >> >>>`  ：

* 按位与：同1为1，不同为0
* 按位或：有1为1，无1为0
* 按位异或：相同为0，不同为1
* 按位非：0变1，1变0（单目运算符）
* 左移：向左移动X位（在右边补X个0，单目运算符）
* 右移：向右移动X位（在左边补X个0，单目运算符）
* 无符号右移：不管符号位，其余与右移一样

#### 逻辑运算符

`&&` ：逻辑与，同真为真，有假为假

`||` ：逻辑或，有真即真，同假为假

`!` ：取反

```java
System.out.println(4 > 3 && 5 > 4);
System.out.println(4 > 3 || 5 > 6);
System.out.println(!(false));
```

##### 逻辑与的断路原则

```java
int num1 = 1, num2 = 2;
boolean res = num1 > 3 && num2++ > 10;

System.out.println(num1); // 结果？
System.out.println(num2); // 结果？
```

##### 逻辑或断路原则

```java
int num1 = 1, num2 = 2;
boolean res = num1 > 0 || num2++ > 10;

System.out.println(num1); // 结果？
System.out.println(num2); // 结果？
```

#### 三元运算符

`? : ` ：将判断后的结果赋值给变量

```java
boolean res = 3 > 5 ? false : true;
```

### 控制台输入

程序运行以后，在控制台输入一定的数据，然后程序继续运行

1. 导入工具包：`import 包名.类名`
2. 声明变量： `Scanner scanner = new Scanner(System.in);`
3. 使用 `Scanner` 中的方法

```java
import java.util.Scanner

class HaHa {
    public static void main(String[] argss) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("请输入内容：");
        int num = scanner.nextInt();
        System.out.println("你输入的内容是：" + num);
    }
}
```

> Scanner 的三个常用方法：
>
> * nextInt()
> * nextDouble()
> * next()

### 表达式

使用运算符连接的变量或者字面值，并且可以得到一个最终结果

```java
1 + 2;
int a = 3;
d > e;
```

## 第三章 选择结构与分支结构

### 选择结构 If

根据已知条件进行逻辑判断，满足条件后执行相应判断

```java
if (布尔表达式) {
    // 代码块
} else if (布尔表达式) {
    // 代码块
} 
...
else {

}
```

> 1. 以上代码块相互排斥，有一个为 true，其他均不再执行，适用于区间判断
> 2. 嵌套语法正确的情况下，if 语句可以任意嵌套

### 分支结构 switch

对变量或者表达式进行判断，根据判断的结果选择相应的分支

```java
switch (变量 | 表达式) {
        case 值1：
            代码1;
        case 值2：
            代码2;
        case 值n：
            代码n;
        default:
            未满足上述条件时的逻辑运算;
}
```

1. 可以用于判断的类型：`byte、short、int、char、String（JDK7+）`
2. 每个 `case` 中都可以使用 `break` 来中断匹配的继续

> 一定要养成良好的习惯，在每个 case 分支中尽可能把 break 都写上，否则会引发问题

### 循环结构

#### while

```java
while (布尔表达式) {
    // 逻辑代码
}
```

执行流程：

1. 先对布尔表达式进行判断，结果为 `true` 时，才执行逻辑代码
2. 本次执行完成后，会对布尔表达式进行再次判断，判断结果为 `true` 时，再执行逻辑代码
3. 直到布尔表达式的结果为 `false` 时，就会退出循环结构

特点：

* 先判断，再执行：首次判断条件不满足时，一次循环内容都不会执行

#### 循环的主要构成

1. 初始部分：用于判断的变量
2. 循环条件：决定是否继续循环的依据
3. 循环内容：循环的单次执行的代码内容
4. 迭代部分：控制循环变量的改变

#### do while

```java
do {
    // 逻辑代码
} while (布尔表达式)
```

执行流程：

1. 先无条件的执行一次逻辑代码，然后进行条件判断
2. 当结果为 `true`，则再次执行循环体内容
3. 当结果为 `false`，结束循环，执行后续代码

特点：

1. 没有入口条件，先执行，后判断

#### for

```java
for (初始部分；循环条件；迭代部分) {
    // 逻辑代码
}
```

执行流程：

1. 执行初始部分（只有一次）
2. 对循环条件进行判断，如果为 `true`，则执行逻辑代码
3. 逻辑代码执行完成后，进行迭代部分
4. 迭代完成后，再次进行循环条件的判断，如果为 `true`，继续执行逻辑代码
5. 循环条件判断的结果为 `false`，退出循环结构

特点：

1. 先判断，再执行
2. 适用于次数明确的循环

### 流程控制语句

#### break

作用：终止、跳出 `switch`、循环语句

#### continue

作用：结束本次循环，进入下次循环

### 嵌套循环

在一个完整的循环结构中，嵌套另外一个完整的循环结构

## 第四章 方法/函数

### 方法的概念

概念：实现特定功能的一段代码，可以反复使用

### 方法的定义

```java
public static void 方法名称() {
    // 方法主体
}
```

经验：将需要在多个地方重复使用后段代码，定义在方法内部

位置：在类的内部，与 `main` 方法并列

```java
// 位置1
public class {
    // 位置2
    public static void main(String[] args) {
        // 位置3
    }
    // 位置4
}
// 位置5
```

> 1. 一个类中可以定义多个方法，方法之间是平行关系，不能嵌套
> 2. 一个方法只做一件事情

### 方法的调用

```java
public class Test {
    public static void main(String[] args) {
        System.out.println("床前明月光，");
        printStr();
        System.out.println("疑是地上霜。");
        printStr();
        System.out.println("举头望明月，");
        printStr();
        System.out.println("低头思故乡。");
        printStr();
    }
    // 自定义方法，用于打印分隔字符
    public static void printStr() {
        for (int i = 0; i < 10; i++) {
            System.out.print("-");
        }
        System.out.println();
    }
}
```

调用方法时，会优先执行方法内部代码，结束后，返回到方法调用处，继续向下执行。

### 方法的组成

在大多数情况下，方法需要与调用者进行一些数据的交互，通常，数据的交互是由方法的参数和返回值来完成的。

参数：调用方法时，传给方法的数据

#### 形参

```java
public static void 方法名(形参) {
    // 方法体
}
```

形参又等价于局部变量

#### 实参

在调用有形参的方法时，需要传入对应的参数，调用方法时传递的参数被称为实参

#### 方法参数的作用

1. 可以让方法更灵活
2. 可以让方法普遍性、适应性更高
3. 可以让方法易于修改及维护

> 调用有参的方法时，实参的个数与类型必须与形参列表完全一致

根据实际的业务定义方法的参数

#### 返回值与返回类型

方法执行后，一些情况下不需要返回值，有些情况必须得有返回值

```java
public static 返回值类型 方法名称(形参列表) {
    // 方法体
    return value; // 返回
}
```

* 返回值类型规定了返回值的数据类型（基本类，引用类型，`void`）
* `return` 后面跟具体的返回值，也可以应用在没有返回值类型（`void`）的方法中  
* 可以使用变量接收方法的返回值，要求：变量类型与返回值类型必须一致
* 一个方法只能有一个返回值
* 当具有返回值的方法存在分支结构时，必须保证每一个分支都返回合适类型的值

#### continue、break、return 的区别

1. continue：跳出本次循环，继续下一次循环
2. break：跳出循环体，继续执行循环体之外的函数体
3. return：跳出整个函数体，函数体后面的部分不再执行

### 递归

为了解决具备某种规矩的问题时，在方法内部再次调用自身方法的和种编程

#### 使用时机

1. 当需要解决的问题可以被拆解为若干个解决方法相同的问题时，方法中调用方法本身
2. 使用循环解决的常规问题，都可以替换为递归解决

#### 使用方法

* 设置有效的出口条件，可以让方法得以正确返回，避免无穷递归
* 递进：每一次推进，计算都比上一次变得简单，直至简单到无需继续推进，就能获得结果，也叫达到出口
* 回归：基于出口的结果，逐层向上回归，依次计算每一层的结果，直到回归到最顶层

> 所有递归能解决的问题，循环都可以解决，但在解决复杂问题时，递归的实现方式更为简单

## 第五章 数组

概念：一组连续的存储空间，存储多个相同数据类型的值

特点：数据类型相同；数组长度固定

### 创建

先声明，再分配数组空间

```java
数据类型[] 数组名称 = new 数据类型[数组长度]

// 1. 先声明，再分配数组空间
int[] array1;
array1 = new int[4];

// 2. 声明并分配空间
int[] array1 = new int[4];

// 3. 声明并赋值
int[] array1 = new int[]{1, 2, 3};

// 4. 声明并赋值（简化版）
int[] array1 = {1, 2, 3};

// 注意：3、4 两种方式有一些细微的差别
// 3 可以写为两行：
// int[] array1;
// array1 = new int[]{1, 2, 3};
// 但是 4 不可以这样写
```

### 术语

* 数组中的每个数据被称为：**数组元素**
* 对数组中每个元素进行赋值或取值的操作被称为：**元素的访问**
* 访问数组元素时，需要使用下标：**下标从0开始，依次加1，自动生成**

### 数组元素存取

* 获取：`数组名称[下标]`
* 存入：`数组名称[下标] = 值`

### 下标

范围：`0 ~ 数组长度-1`

> 如果访问或者存入一个不存在的下标，会报出 java.lang.ArrayIndexOutOfBoundsException 的异常

### 遍历

从头至尾，逐一对数组的每个元素进行访问

```java
public static void main(String[] args) {
    int[] arr = new int[5];

    for (int i = 0; i < 5; i++) {
        arr[i] = i + 1;
    }

    for (int i = 0; i < 5; i++) {
        System.out.println(arr[i])
}
}
```

**length** ：获取数组的长度

### 数组元素的默认值

数组在没有初始化之前，和数组的类型相关，系统都会对数组的元素做相应的初始化操作。

数组元素默认值：

* 整数：`0`
* 小数：`0.0`
* 字符：`\u0000`
* 布尔：`false`
* 其它：`null`

### 随堂练习

1. 给定一个整数数组，数组中的值自己指定/从控制台中获取，统计数组中所有元素的平均值。
2. 从控制台输入一个数字，在一个已经存在的数组中进行判断，如果该数字在数组中存在，输入数字在数组中的下标，如果不存在，输出 `-1`

### 数组的排序

`java.util.Arrays.sort(数组名)` ：对数组中的元素进行升序排序

## 第六章 面向对象

### 概念

* 一切客观存在的事情都是对象，**万物皆对象**
* 任何对象，一定具有自己的特征和行为

> 特征：也叫做属性，一般为名词，代表对象有什么
>
> 行为：也叫做方法，一般为动词，代码对象能做什么

### 使用对象解决问题

1. 将现实中的对象定义为程序里的对象，用来模拟现实世界
2. 用程序中的对象代表现实中的对象，解决实际的问题

### 如何定义对象

现实中的事物产生，一般都会有个模板，根据模板，再创造出各种事物对象。

程序中也有个模板，用以产生对象，这个模板在程序中被叫做 **类**。由程序中的类所产生的实体被叫做程序中的 **对象**。

### 类

```java
public class Dog {

    String breed; // 定义品种
    int age; // 定义年龄
    String sex; // 定义性别
    String color; // 定义颜色

    // 吃东西的方法
    public void eat() {
        System.out.println("eating...");
    }

    // 睡觉的方法
    public void sleep() {
        System.out.println("sleeping...");
    }
}
```

#### 属性

1. 类的属性通过变量表示，又被称作实例变量
2. 与变量的声明相同
3. 属性的声明位于类的内部，方法的外部

#### 方法

1. 通过函数表示，又被称作实例方法
2. 定义：
  
   ```java
   public 返回值类型 方法名(形参) {
       // 方法
   }
   ```

#### 创建对象

```java
public class JingBa {
    public static void main(String[] args) {
        Dog jingBa = new Dog();

        jingBa.bread = "京巴";
        jingBa.age = 3;
        jingBa.sex = "公";
        jingBa.color = "白";

        jingBa.eat();
        jingBa.sleep();
    }
}
```

> 1. 给对象的属性赋值的方法：对象.属性 = 值;
> 2. 调用对象行为的方法：对象.方法();
> 3. 获取对象属性值的方法：对象.属性

#### 类与对象

* 类定义了对象应具有的属性与行为，类是对象的模板
* 对象拥有多个特征和行为的实体，对象是类的实例

#### 实例变量

|          | 实例变量（field）              | 局部变量（variable）           |
| -------- | ------------------------------ | ------------------------------ |
| 定义位置 | 类的内部，方法的外部           | 方法或方法内的结构当中         |
| 默认值   | 字面值（与数组相同）           | 无默认值                       |
| 使用范围 | 本类有效                       | 从定义行开始到包含其的结构结束 |
| 命名冲突 | 可与局部变量重名，局部变量优先 | 不允许重名                     |

##### 默认值

| 数据类型                   | 默认值   |
| -------------------------- | -------- |
| byte                       | 0        |
| short                      | 0        |
| int                        | 0        |
| long                       | 0L       |
| float                      | 0.0f     |
| double                     | 0.0d     |
| char                       | '\u0000' |
| String(or any Object)<br/> | null     |
| boolean                    | false    |

##### 字面值

基本类型是内置于语言中的特殊数据类型；它们不是从类创建的对象。字面值是固定值的源代码表示；字面值直接在代码中表示，不需要计算。

###### 整形字面值

```java
// 十进制
int num = 10;
// 十六进制
int num = 0xa;
// 二进制
int num = 0b1010;
// 八进制
int num = 012;
```

###### 浮点字面值

```java
// 长整形
long num = 10L;
// 单精度浮点
float num = 10.0f/F;
// 双精度浮点
double num = 10.0d/D;
// 科学计数法
double num = 0.01e3
```

###### 字符、字符串字面值

字符字面值使用单引号包裹 `'` ，字符串字面值使用双引号包裹 `"` ，`Unicode` 转义序列可以使用在程序的任何地方（例如字段名等）。

**ASCII 码表：**
[![6EXbwV.md.png](https://s3.ax1x.com/2021/03/04/6EXbwV.md.png)](https://imgtu.com/i/6EXbwV)

**转义字符：**

[![6EXzl9.md.png](https://s3.ax1x.com/2021/03/04/6EXzl9.md.png)](https://imgtu.com/i/6EXzl9)

###### 在数字字面值中使用下划线 `_` 分隔

在 `Java SE 7` 及以后版本中，数字字面值中可以出现任意数量的下划线字符(`_`)，这样可以提高代码的可读性。

**注意：** 只能在数字字面值中添加下划线，并且在数字字面值的以下情况中也不能添加下划线：

* 数字的开始或结尾
* 浮点数字中，与小数点相邻的位置
* `F` 或者 `L` 后缀的前面
* 在完整的数字串之间

```java
// 错误：在 . 前后出现 _
float pi1 = 3_.1415F;
float pi2 = 3._1415F;
// 错误：在 L 之前出现 _
long socialSecurityNumber1 = 999_99_9999_L;
// 错误：在 0x 之间出现 _ （0x 是完整的数字串）
int x4 = 0_x52;
// 错误：在数字字面值的开始或结尾
int x5 = 0x_52;
int x2 = 52_;

// 正确
int x1 = 5_2;
// 正确
int x3 = 5_______2;
// 正确
int x6 = 0x5_2; 
```

#### 实例方法

##### 方法的声明

`修饰符 返回值类型 方法名(形参列表)`

##### 方法的重载

有些情况下，对象的同一种行为可能存在不同的实现过程。

方法重载（**overload**）：一个类中定义多个相同名称的方法

要求：

* 方法名称相同
* 参数列表不同（类型、个数、顺序）
* 与访问修饰符、返回值类型无关

调用：

* 根据传入的实参找到实际调用的方法

#### 构造方法/构造器

类中的一个特殊方法，主要用于创建对象

特点：

* 名称与类名完全相同
* 没有返回值类型
* 创建对象时，就可以调用构造方法
* 如果类中没有显式定义构造方法，则编译器默认会提供一个无参的构造方法
* 类中如果有其它的构造方法，系统就不会添加无参的构造方法了

#### 创建对象的过程

1. 在内存中开辟一个空间，并赋值属性为默认值
2. 调用构造方法初始化
3. 把对象地址赋值给变量

#### **this** 关键字

类是模板，可以创建很多对象。**this** 是类中的默认引用，代表当前实例，当类服务于某个对象时，**this** 则指向这个对象

用法：

1. 调用实例属性、方法
2. 调用本类中的其它构造方法
  
   1. 构造方法中调用其它构造方法要注意，必须是第一条语句，且只能调用一次

### 三大特性

面向对象的核心

#### 封装

在对象的外部，为对象的属性赋值，可能存在非法数据的录入。

**概念：**

尽可能的隐藏对象的内部实现细节，控制对象的修改及访问的权限。

**实现：**

将对象的属性改为 `private`（私有的），同时添加属性公共的访问方法，在访问方法中对属性的赋值的合理性做控制

**总结：**

`get、set` 方法是外界访问对象私有属性的唯一通道，方法内部可以对数据朝廷检测和过滤

#### 继承

两个类之间的继承关系，必须满足 `is a` 的关系

被继承的类：**父类（超类）**

继承的类：**子类（派生类）**

**父类的抽象：**

可以根据程序需要使用到的多个具体类，进行共性抽取，进而定义父类

##### 语法

`class 子类 extends 父类 {}  // 定义子类时，显式继续父类`

产生继续关系后，子类可以使用父类的属性和方法，也可以定义子类独有的属性和方法

好处：提高代码的复用性，又可以提高代码的可扩展性

`java` 中的继承为单继承，即每个类只能有一个直接父类，但是可以多级继承，属性和方法逐级叠加

**类中不可以被继承的内容**

* 构造方法
* `private` 修饰的属性和方法
* 父子类不在同一个 `package` 中，`default` 修饰的属性和方法

**访问修饰符：**

|               | 本类 | 同包 | 非同包子类 | 其它 |
| ------------- | :--: | :--: | :--------: | :--: |
| **private**   |  ✓   |  ✕   |     ✕      |  ✕   |
| **default**   |  ✓   |  ✓   |     ✕      |  ✕   |
| **protected** |  ✓   |  ✓   |     ✓      |  ✕   |
| **public**    |  ✓   |  ✓   |     ✓      |  ✓   |

问题：

1. 子类中是否可以定义和父类相同的方法？
2. 为什么要在子类中定义和父类相同的方法？
  
   1. 答：当父类提供的方法无法满足子类的需求，可以在父类中定义相同的方法进行覆盖

##### 方法覆盖（`Override`）

**原则：** 

1. 方法名称、参数列表、返回值类型必须与父类相同
2. 访问修饰符不能比父类更严格

**Super 关键字**

在子类中，可以直接访问从父类继承到的属性和方法，如果父类与子类的属性和方法存在重名时，需要加以区分，才可以精准访问

* 可以调用父类的构造方法。注：如果没有显示书写，隐式存在于子类构造方法的首行

##### 继承中对象的创建

* 在具有继承关系的对象中，构建子类对象会构建父类对象
* 由父类的共性内容，叠加子类的独有内容，组合成完整的子类对象

##### this 与 super

* `this` 表示当前对象的引用，调用本类（包括继承）的属性、方法、本类构造方法
* `super` 表示父类对象的引用，调用父类的属性、方法、构造方法

#### 多态

**概念：**

父类引用指向子类对象，从而产生多种形态

这是因为父类和子类之间有直接或间接的继承关系，父类引用可指向子类对象，即形成多态

**使用场景：**

* 使用父类作为方法的形参实现多态，使方法参数的类型更为宽泛
* 使用父类作为方法的返回值实现多态，使方法可以返回不同子类型

**向上转型**

父类引用中保存真实子类对象，称为向上转型（即多态核心概念）

**向下转型**

将父类引用的真实子类对象，强转回子类本身类型，称为向下转型

**instanceof 关键字**

向下转型前，应该判断引用中的真实对象类型，保证类型转换的正确性

`boolean res = 引用 instanceof 类型`

#### 包 —— package

一个包是用来组织一系列相关的类或接口的命名空间。从概念上说，你可以把包当成电脑中各个文件夹，你应该会把网页、图片、脚本、应用放在不同的文件夹中。因为由 `Java` 编写的软件可能由成千上万的类组成，通过将相关的类和接口放入不同的包中来使事情井井有条是很有意义的。

在应用程序中，`Java` 平台提供了大量的类库（一系列的包）以供使用，一般来说，它们被叫做 `Application Programming Interface`，或者简称为 `API`。常用的类库有：包含了字符串状态和行为的 `String` 对象，方便对操作系统上文件进行境、删、改、查、对比等操作的 `File` 对象，创建和使用网络套接字的 `Socket` 对象，与用户界面图形相关的 `GUI` 对象等。实际上，有数千种类可供选择。这些工具类使得程序员专注于设计应用本身，而不是把精力消耗在如何让应用工作的基础框架之上。

##### 命名规则

包名以小写字母开头，包与子包之间使用 `.` 分隔

##### 系统包说明

* `java.lang` 包里面包含了使用语言的基本类
* `java.util` 包里面包含了各种工具类

##### 使用方式

* 在代码中使用全路径限定名称，如：`java.util.Date today = new java.util.Date();`
* 在头部（类定义之外）使用 `import` 语法引入类的包名，在使用时就只需要写类名就可以了，如：
  
  ```java
  import java.util.Date;
  public class DatePrinter {
    public static void main(String[] args) {
      Date today = new Date();
      System.out.println("Today's date is: " + today.toString());
      } 
  }
  ```
  
  如果想要引入某个包中的所有类，使用 `*` 号就可以，例如：`import java.util.*`
* 系统会自动把 `java.lang` 包包含到每个 `Java` 程序中，不用手动添加
* `default package`（默认包）表示文件没有在某个包中

### 抽象

#### 抽象类

##### 概念

具备某种对象的特征，但是不完整

被 `abstract` 修饰的类就是抽象类，抽象类对象无法独立存在，即 **不能 new 对象**

##### 作用

* 可以被子类继承，提供共性的属性和方法
* 可申明为引用，更自然的使用多态

#### 抽象方法

父类提供的方法很难满足子类的不同需求，一般都会被子类覆盖，略显多余（方法声明必要，方法实现多余），这里就可以使用抽象方法。

##### 概念

只有方法的申明，没有方法的实现（即没有 `{}` 及方法体）

**注意：** 

* 抽象方法必须包含在抽象类中
* 子类必须重写父类中的抽象方法（如果子类还是抽象类，重写父类的抽象方法就不是必须的了）

##### 总结

抽象类中不一定有抽象方法，但有抽象方法的类一定是抽象类

### 静态

#### 概念

使用 `static` 修饰的属性或方法，就变成了静态属性（类属性）和静态方法（类方法）

#### 属性

##### 静态 VS 实例

* 实例属性是每个对象各自持有的独立空间（多份），单个对象修改，不会影响其它对象
* 静态属性是整个类共同持有的共享空间（一份），任何对象修改，都会影响其它对象

##### 调用

`类名.静态属性名`

#### 方法

##### 已知的静态方法

`Arrays.sort()、Math.random()`

都是使用类名直接调用

##### 调用

`类名.静态方法名()`

##### 特点

* 静态方法允许直接访问静态成员
* 静态方法不能直接访问非静态成员
* 静态方法中不允许使用 `this` 或 `super` 关键字
* 静态方法可以继承，不能重写、没有多态

#### 代码块

##### 构成

```java
class Test {
    public static String name;
    static {
        name = "初始化";    
    }
}
```

##### 作用

可为静态属性赋值，或进行必要的初始化行为

##### 时机

* 类加载时，触发静态代码块的执行（仅一次）
* `new` 第一个对象时
* 第一次调用静态方法时

> 类加载的过程：
>
> 1. `JVM` 首次使用某个类时，需要通过 `CLASSPATH` 查找该类的 `.class` 文件
> 2. 将 `.class` 文件中对类的描述信息加载到内存中，进行保存
>
>    1. 描述信息有：包名、类名、父类、属性、方法、构造方法……
> 3. 加载时机
>
>    1. 创建对象
>    2. 创建子类对象
>    3. 访问静态属性
>    4. 调用静态方法
>    5. 主动加载：`Class.forName("全限定名")`

##### 加载顺序

静态属性初始化之后

### final

#### 可修饰的内容

* 类
  
  * 使用 `final` 修饰的类不能被继承
* 方法
  
  * 使用 `final` 修饰的方法不能被重写、覆盖
* 变量
  
  * 使用 `final` 修饰的变量值不能被改变（常量）
  * 使用 `final` 修饰了实例变量，系统将不再给其提供默认值，必须手动赋予初始值，可以在显示时，或在构造方法中为其赋值
  * 静态常量
* 对象常量
  
  ```java
  final int[] nums = new int[]{1, 2, 3, 4};
  
  final Student s = new Student();
  
  // 对象常量的引用地址不能再发生变化，但地址里的内容可以变化
  ```

### 接口

接口在 `Java` 开发中，接口是很重要的一个概念，其重要程序不亚于封装、继承、多态等概念

#### 定义

接口是一种能力的定义：

* 接口的定义代表了某种能力
* 方法的定义是能力的具体要求

#### 语法

接口相当于特殊的抽象类，定义方式、组成部分与抽象类类似

```java
interface MyInterface {
    public static final String FIELD = "value";
    public abstract void method();
}
```

* 使用 `interface` 关键字定义接口
* 没有构造方法，不能创建对象
* 只能定义：公开静态常量、公开抽象方法
  
  * 常量前面的 `public static final` 可以省略，系统会自动添加
  * 方法前面的 `public abstract` 可以省略，系统会自动添加

#### 与抽象类的异同

**相同：**

* 可编译成字节码文件
* 不能创建对象
* 可以作为引用类型
* 具备 `Object` 类中所定义的方法

**不同：**

* 所有属性都是公开静态常量，隐式地使用 `public static final` 修饰
* 所有方法都是公开抽象方法，隐式地使用 `public atstract` 修饰
* 没有构造方法、代码块

#### 扩展

`Java` 是一个单继承的语言，当父类的方法无法满足子类的需求时，子类可以通过实现多个接口的方式扩充本身的能力

#### 规范

* 任何类在实现接口时，必须实现接口中所有的抽象方法，除非此类为抽象类
* 实现接口中的抽象方法时，访问修饰符必须是 `public` 的

#### 关系

**类与类：**

* 单继承
* `extends` 父类

**类与接口：**

* 多实现
* `implements` 接口1，接口2，...，接口 `n`

**接口与接口：**

* 多继承
* `extends` 父接口1，父接口2，...，父接口 `n`

#### 常量接口

将多个用于表示状态或固定值的变量，以静态常量的形式定义在接口中统一管理，提高代码可读性

#### 标记接口

没有包含任何成员，仅仅用于标记

* `Serializable`
* `Cloneable`

#### 接口的好处

* 降低程序的耦合度
* 使用多态
* 设计与实现完全分享
* 更容易搭建程序框架
* 更容易更换具体实现

### 内部类

#### 成员内部类

##### 概念

* 在一个类的内部再定义一个完整的类，与实例变量、实例方法同级别
* 外部类的一个实例部分，创建内部类对象时，必须依赖外部类对象

##### 特点

* 编译之后可以生成独立的字节码文件
* 内部类可以直接访问外部类的私有成员，而不破坏封装
* 可为外部类提供必要的内部功能组件

##### 实例化

```java
public class Outer {
    private String name;
    private int age;

    class Inner {
        public void show() {
            System.out.println(name + "\n" + age);
        }
    }
}

public class TestOuter {
    public static void main(String[] args) {
        // 第一种实例化方法
        Outer outer = new Outer();
        Innter inner = outer.new Inner();

        // 第二种实例化方法
        Inner inner = new Outer().new Inner();

        // 调用内部类的方法
        inner.show();
    }
}
```

##### 内部类访问外部类的同名属性

当外部类与内部类存在同名属性时，会优先访问内部属性，要访问同名的外部属性，使用下面的语法：

`外部类名.this.属性名`

##### 注意

成员内部类里面不能定义静态成员，但是可以定义静态常量

#### 静态内部类

不依赖外部类对象，可以直接创建或通过类名访问，可声明静态成员

```java
public class Outer {
    private int age = 10;
    private String name = "哈哈";

    static class Inner {
        private String sex = "男";
        // 静态内部类中可以定义静态变量
        private static String phone = "123234";

        public void show() {
            // 访问外部类的变量
            System.out.println(new Outer().age);

            // 调用静态内部类的变量
            System.out.println(sex);

            // 调用静态内部类的静态变量
            System.out.println(Inner.phone);
        }
    }
}
```

> **只有内部类可以被 static 修饰**，普通类是不能被 `static` 修饰的

#### 局部内部类

定义在外部类的方法当中，作用范围和创建对象范围仅限于当前方法

```java
public class Outer {

    private String name = "haha";
    private int age = 20;

    public void test() {
        String hehe = "hehe";

        class Inner {
            private String phone = "12342349";
            private String sex = "顶起";

            public void show() {
                // 访问外部类成员
                System.out.println(Outer.this.name);
                System.out.println(age);

                // 访问内部类成员
                System.out.println(phone);
                System.out.println(this.sex);

                // 访问方法内的局部变量
                // 注意：局部内部类要访问所在方法中的变量时，要保证该变量是 final 类型的常量
                //      1. JDK 1.7 及以前，需要显式写 final，JDK 1.8 及以后，只要发生这种访问，系统会自动添加
                //      2. 使用常量的原因是：方法该用完成后，方法里的变量立即会消失，但是类不会，因此，需要使用 final 常量。final 常量在内存中记录的不是变量地址，而是变量值
                System.out.println(hehe);
            }
        }

        // 调用局部类对象方法
        Inner inner = new Inner();
        inner.show();
    }

    public static void main(String[] args) {
        Outer outer = new Outer();
        outer.test();
    }
}
```

> 局部内部类访问外部类当前方法中的局部变量时，因无法保障变量的生命周期与自身相同，变量必须修饰为 final

#### 匿名内部类

没有类名的局部内部类（一切特征都与局部内部类相同）

* 必须继承一个父类或者实现一个接口
* 定义类、实现类、创建对象的语法合并，只能创建一个该类的对象
* 优点：减少代码量
* 缺点：可读性差

## 第七章 Object

* 它是所有父类的直接或间接父类，位于继承树的最顶层
* 任何类，如果没有书写 `extends` 显式继承某个类，都默认直接继承 `Object` 类
* `Object` 类中定义的方法，是所有对象都具备的方法
* `Object` 类型可以存储任何对象

### 方法

#### getClass()

* 声明：`public final Class<?> getClass() {}`
* 返回：返回引用中存储的实际类型对象
* 应用：通常用于判断两个引用中实际存储对象类型是否一致

#### hashCode()

* 声明：`public int hashCode() {}`
* 返回：对象的哈希码值
  
  * 哈希值根据对象的地址、或字符串、或数字使用 `hash` 算法算出来的 `int` 类型的数值
* 说明：一般情况下相同对象返回相同哈希码值
* 应用：用来判断两个对象是否为同一个对象

#### toString()

* 声明：`public String toString() {}`
* 返回：对象的字符串表示（表现形式）
* 应用：可以根据程序需求覆盖该方法，如：展示对象各个属性值

#### equals()

* 声明：`public boolean equals(Object obj) {}`
* 返回：两个对象是否相等
* 说明：默认实现为：`this == obj`，比较两个对象地址是否相同
* 注意：可以覆盖，比较两个对象的内容是否相同，很多类都对该方法进行了覆盖，使用时一定要注意

#### finalize()

* 说明：当对象被判定为垃圾对象时，由 `JVM` 自动调用此方法，用以标记垃圾对象，进入回收队列
  
  * 垃圾对象：没有有效引用指向对象时，此对象为垃圾对象
  * 垃圾回收：由 `GC` 销毁垃圾对象，释放数据存储空间
  * 自动回收机制：`JVM` 的内存耗尽，一次性回收所有垃圾对象
  * 手动回收机制：使用 `System.gc()`，通知 `JVM` 执行垃圾回收
    
    > 注意：一般情况下，不会手动进行垃圾回收

## 第八章 包装类

基本数据类型所对应的引用数据类型就是包装类。

| 基本数据类型 | 包装数据类型 |
| ------------ | ------------ |
| **byte**     | **Byte**     |
| **short**    | **Short**    |
| **int**      | **Integer**  |
| **long**     | **Long**     |
| **float**    | **Float**    |
| **double**   | **Double**   |
| **boolean**  | **Boolean**  |
| **char**     | **Char**     |

### 类型转换与装箱、拆箱

`8` 种包装类提供不同类型之间的转换方式

> JDK 1.5 之后，提供了自动装箱和拆箱

### parseXXX() 静态方法

`XXX` 代表一种基本类型。该类静态方法实现了字符串转换为基本类型

### valueOf() 静态方法

实现引用类型转与基本类型之间的转换

> 注意：需要保证转换的类型兼容，否则抛出 NumberFormatException 异常

### 整数缓冲区

`Java` 在运行过程中会创建一个整数缓冲区，会预先创建 `256` 个常用的整数包装类型对象。这是将常用的数据创建的对象进行复用，减少内存开支

```java
public class Boxing {

    public static void main(String[] args) {

        Integer i1 = new Integer(100);
        Integer i2 = new Integer(100);
        System.out.println(i1 == i2);

        Integer i3 = Integer.valueOf(100);
        Integer i4 = Integer.valueOf(100);
        System.out.println(i3 == i4);

        Integer i5 = Integer.valueOf(200);
        Integer i6 = Integer.valueOf(200);
        System.out.println(i5 == i6);
    }
}

// 下面是最终输出的结果
// false
// true
// false
```

## 第九章 String 类

* 字符串是常量，创建以后不可改变
* 字符串字面值存储在 **字符串池中**，可以共享
* 给字符串类型的变量赋值有两种方式：
  
  * `String s = "Hello";` 这种情况下只会在字符串常量池中产生一个对象
  * `String s = new String("Hello");` 这种情况下会在堆、池中各产生一个对象

### 常用方法

* `public int length()` ：返回字符串的长度
* `public Char charAt(int index)` ：根据下标获取字符
* `public boolean contains(String str)` ：判断当前字符串中是否包含 `str`
* `public char[] toCharArray()` ：将字符串转换为字符数组
* `public int indexOf(String str)` ：查找 `str` 首次出现的下标，存在，则返回该下标；不存在，则返回 `-1`
* `public int lastIndexOf(String str)` ：查找 `str` 在字符串中最后一次出现的下标索引，存在，则返回该下标；不存在，则返回 `-1`
* `public String trim(String str)` ：去掉字符串前后的空格
* `public String toUpperCase()` ：将字符串中的小写字母转换为大写
* `public String toLowerCase()` ：将字符串中的大写字母转换为小写
* `public boolean startWith(String str)` ：判断字符串是否以 `str` 开头
* `public boolean endWith(String str)` ：判断字符串是否以 `str` 结尾
* `public String replace(char oldChar, char newChar)` ：将旧字符串替换为新字符串
* `public String[] split(String str)` ：根据 `str` 拆分字符串
* `public boolean equals(String str)` ：比较字符串的内容是否一样
* `public int compareTo(String str)` ：比较两个字符串的内容是否一样，一样返回 `true`，不一样返回正或负值（先比较字符，字符相等时比较长度）

### 综合练习

```java
public static void main(String[] args) {
    /**
     * 要解决的问题：
     *    已知字符串：String str = "this is a text";
     *    1. 将 str 里的单词单独提取出来
     *    2. 将 str 中的 text 替换为 practice
     *    3. 在 text 前面插入一个 easy
     *    4. 将每个单词的首字母改为大写
     */

    String str = "this is a text";
    //----------------1. 将 str 里的单词单独提取出来------------------
    String[] word = str.split(" ");
    for (String w : word) {
        System.out.print(w + "\t");
    }

    //----------------2. 将 str 中的 text 替换为 practice------------
    System.out.println();
    String str1 = str.replace("text", "practice");
    System.out.println(str1);

    //----------------3. 在 text 前面插入一个 easy------------------
    String str2 = str.replace("text", "easy text");
    System.out.println(str2);

    //----------------4. 将每个单词的首字母改为大写------------------
    String res = "";
    for (String w : word) {
        char first = w.charAt(0);
        char newFirst = Character.toUpperCase(first);
        res += newFirst + w.substring(1) + " ";
    }
    System.out.println(res);
}
```

### 可变字符串

#### StringBuffer

可变长字符串，`JDK 1.0` 提供，运行效率慢、线程安全

#### StringBuilder

可变长字符串，`JDK 1.5` 提供，运行效率快、纯种不安全

#### 与 String 的区别

1. 效率比 `String` 高
2. 比 `String` 省内存

#### 常用的方法

1. `public StringBuffer/StringBuilder append(xxx)` ：把参数（转换为字符串后）添加到字符序列之后
2. `public StringBuffer/StringBuilder insert(int offset, xxx c)` ：在字符序列的 `offset` 位置插入 `c`
3. `public StringBuffer/StringBuilder delete(int start, int end)` ：删除位于 `[start, end)` 的子字符序列，如果 `start` 等于 `end`，什么都不会做
4. `public StringBuffer/StringBuilder replace(int start, int end, String str)` ：替换位置在 `[start, end)` 的字符序列

## 第十章 BigDecimal

很多实际应用中需要精确运算，而 `double` 是近似值存储，不符合要求，需要借助 `BigDecimal`

`BigDecimal` 类位于 `java.math` 包中，用于精确计算浮点数。 

### 创建

`BigDecimal bd = new BigDecimal("1.0");`

### 综合示例

```java
public static void main(String[] args) {
    BigDecimal db1 = new BigDecimal("1.0");
    BigDecimal db2 = new BigDecimal("0.9");

    System.out.println(db1.add(db2));
    System.out.println(db1.subtract(db2));
    System.out.println(db1.multiply(db2));
    System.out.println(db1.divide(db2));
}

// 下面是输出
1.9
0.1
0.90
Exception in thread "main" java.lang.ArithmeticException: Non-terminating decimal expansion; no exact representable decimal result.
    at java.math.BigDecimal.divide(BigDecimal.java:1690)
    at com.ch.wchya.fourteen.Course.main(Course.java:20)
```

**报错的原因：**

因为 `1.0` 除以 `0.9` 不能除尽，结果是无限循环小数，因此报错

**正确的做法：**

使用 `divide` 方法的另一个重载：`public BigDecimal devide(BigDecimal divisor, int scale, int roundMode)` ，在做除法时传入保留的小数位（`scale`），和小数位进位原则（`BigDecimal.ROUND_XXX`）

> RoundMode 的常量只需要记住 ROUND__HALF_UP（四舍五入）就可以了，有其它需要的在使用的时候自己测试使用即可

## 第十一章 Date

`Date` 表示特定的瞬间，精确到毫秒

> Date 类中的大部分方法都已经被 Calendar 类中的方法所取代

> 时间单位：
>
> * 1秒     = 1000毫秒
> * 1毫秒 = 1000微秒
> * 1微秒 = 1000纳秒

### 创建

`Date date = new Date()`

> 注意：Date 类在 java.sql 包中和 java.util 包中都存在，请使用 java.util 包中的 Date 类，因为 java.sql 包中的 Date 类是继承自 java.util 包中的 Date 类

```java
public static void main(String[] args) {
    Date date = new Date();
    System.out.println(date.toString());

    Date date1 = new Date(date.getTime() - (1000 * 24 * 60 * 60));
    System.out.println(date1.toString());

    System.out.println(date.toLocaleString());
    System.out.println(date1.toLocaleString());

    System.out.println(date.before(date1));
    System.out.println(date.after(date1));

    System.out.println(date.compareTo(date1));
}

// 以下是输出
Sat Dec 26 19:11:57 CST 2020
Wed Dec 23 19:11:57 CST 2020
2020-12-26 19:11:57
2020-12-23 19:11:57
false
true
1
```

## 第十二章 枚举

枚举类型是 `Java 5` 中新增特性的一部分，它是一种特殊的数据类型，在 `JDK 6` 以后，`switch` 支持枚举类型。

### 创建

```java
public enum Weekdays {
    MON,TUE,WED,THI,FRI,SAT,SUN
}
```

### 使用

```java
public static void main(String[] args) {
    Weekdays day = Weekdays.MON;
}
```

### 常见方法

| 返回类型                      | 方法名称                                         | 方法说明                                                |
| ----------------------------- | ------------------------------------------------ | ------------------------------------------------------- |
| `int`                         | `compareTo(E o)`                                 | 比较此枚举与指定对象的顺序                              |
| `boolean`                     | `equals(Object other)`                           | 当指定对象等于此类型常量时，返回 `true`                 |
| `Class<?>`                    | `getDeclaringClass()`                            | 返回与此枚举常量的枚举类型相对应的 `Class` 对象         |
| `String`                      | `name()`                                         | 返回此枚举常量的名称，在其枚举声明中对其进行声明        |
| `int`                         | `ordinal()`                                      | 返回枚举常量的序数（它在枚举声明中的位置，序数从0开始） |
| `String`                      | `toString()`                                     | 返回枚举常量的名称，它包含在声明中                      |
| `static<T extends Enum<T>> T` | `static valueOf(Class<T> enumType, String name)` | 返回带指定名称的指定枚举类型的枚举常量                  |

**注意：**

枚举声明以后，位置就已经确定，即每个枚举常量所代表的数值就定下了。但是如果后期枚举常量的位置发生变化，使用 `ordinal()` 方法返回的值也就会变化，所以：

1. 要慎用该方法
2. 可以使用带整形参数的构造方法将每个枚举常量的位置进行固定

```java
enum Weekday {
    SUN(7), MON(1), TUES(2), WED(3), THU(4), FRI(5), SAT(6);


    private final int value;

    private Weekday(int value) {
        this.value = value;
    }
}
```

### 与类的区别

没有区别，`enum` 定义的类型就是 `class`

### 特点

* 自定义的 `enum` 类型问题继承自 `java.lang.Enum`，且无法被继承
* 只能定义出 `enum` 的实例，而无法通过 `new` 操作符创建 `enum` 的实例
* 定义的每个类型都是引用类型的唯一实例
* 可以将 `enum` 类型用于 `switch` 语句
* `enum` 的构造方法要声明为 `private`，字段强烈建议声明为 `final`

## 第十三章 Calendar

`Calendar` 提供了设置各种日历字段的方法

> 注意：因为 Calendar 构造方法的修饰符是 protected 的，所以无法直接创建该对象

### 方法

| 方法名                                                       | 说明                                       |
| ------------------------------------------------------------ | ------------------------------------------ |
| `static Calendar getInstance()`                              | 使用默认时区和区域获取日历                 |
| `void set(int year, int month, int date, int hourofday, int minute, int second)` | 设置日历的年、月、日、时、分、秒           |
| `int get(int field)`                                         | 返回给定日历字段的值。字段：年、月、日等   |
| `void setTime(Date date)`                                    | 用给定的 `Date` 设置给日历的时间           |
| `Date getTime()`                                             | 返回一个 `Date`，表示此日历的时间          |
| `void add(int field, int amount)`                            | 按照日历的规则，给指定字段添加或减少时间量 |
| `long getTimeInMillies()`                                    | 毫秒为单位返回该日历的时间值               |

### 示例

```java
public static void main(String[] args) {
    Calendar calendar = Calendar.getInstance();
    System.out.println(calendar.getTime().toLocaleString());

    int year = calendar.get(Calendar.YEAR);
    // 月份从 0 开始，如果要符合人类正常的逻辑，需要手动 + 1
    int month = calendar.get(Calendar.MONTH);
    int day = calendar.get(Calendar.DAY_OF_MONTH);
    // HOUR_OF_DAY 是 24 小时制的，HOUR 是 12 小时制的
    int hour = calendar.get(Calendar.HOUR_OF_DAY);
    int minute = calendar.get(Calendar.MINUTE);
    int second = calendar.get(Calendar.SECOND);
    System.out.println(year + "年" + month + "月" + day + "日" + hour + "时" + minute + "分" + second + "秒");

    Calendar calendar1 = Calendar.getInstance();
    calendar1.add(Calendar.DAY_OF_YEAR, 1);
    System.out.println(calendar1.getTime().toLocaleString());

    int min = calendar.getActualMinimum(Calendar.DAY_OF_MONTH);
    int max = calendar.getActualMaximum(Calendar.DAY_OF_MONTH);
    System.out.println("最小：" + min + "最大：" + max);

    calendar1.add(Calendar.MONTH, -1);
    int min1 = calendar1.getActualMinimum(Calendar.DAY_OF_MONTH);
    int max1 = calendar1.getActualMaximum(Calendar.DAY_OF_MONTH);
    System.out.println("最小：" + min1 + "最大：" + max1);
}

// 以下是输出
2020-12-27 15:30:02
2020年11月27日15时30分2秒
2020-12-28 15:30:02
最小：1最大：31
最小：1最大：30
```

## 第十四章 SimpleDateFormat

`SimplleDateFormat` 是一个以语言环境有关的方式来格式化和解析日期的具体类

### 模式字母

| 字母   | 时间或日期                 | 示例 |
| ------ | -------------------------- | ---- |
| y      | 年                         | 2019 |
| M      | 年中月份                   | 08   |
| d      | 月中天数                   | 07   |
| H      | 1天中小时数（0-23）        | 23   |
| m      | 分钟                       | 23   |
| s      | 秒                         | 23   |
| S<br/> | 毫秒                       | 832  |
| w      | 年中的周数                 | 27   |
| W      | 月中的周数                 | 3    |
| F      | 月份中的星期               | 4    |
| E      | 月份中的天数               | 22   |
| k      | 1天中的小时数（0-24）      | 24   |
| K      | `am/pm` 中的小时数（0-11） | 0    |
| h      | `am/pm` 中的小时数（1-12） | 12   |

### 示例

```java
public static void main(String[] args) throws Exception {
    SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 HH:mm:ss");
    SimpleDateFormat sdf1 = new SimpleDateFormat("yyyy/mm/dd");

    System.out.println(sdf.format(new Date()));
    System.out.println(sdf1.format(new Date()));

    // 注意：sdf1 可以转换的日期时间的字符串格式，与它这个对象在创建时所
    //      传入的格式是一样的，否则是抛出 ParseException 异常
    Date date = sdf1.parse("2020/12/20 12:12:12");
    System.out.println(date);
}
```

## 第十五章 System

`System` 类是系统类，主要用于系统的属性数据和其他操作，构造方法私有

### 方法

| 方法名                            | 说明                                                         |
| --------------------------------- | ------------------------------------------------------------ |
| `static void arrayCopy(...)`      | 复制数组                                                     |
| `static long currentTimeMillos()` | 获取当前系统时间，返回的是毫秒值                             |
| `static void gc()`                | 建议 `JVM` 赶快启动垃圾回收器回收垃圾                        |
| `static void exit(int status)`    | 退出 `JVM`，如果参数是 `0` 表示正常退出 `JVM`，非 `0` 表示异常退出 `JVM` |

> gc() 方法只能建议 `JVM` 进行垃圾回收，具体是否回收，是由 `JVM` 的系统根据内存决定的

### 格式化数字打印输出

在 `java.io` 包中包含了 `PrintStream` 类，该类中有两个格式化的方法，可以使用这两个方法来替代 `print` 和 `pringln` 方法。其实，也可以通过 `System.out` 执行 `PrintStream` 类的方法，因此，你可以在任何能够使用 `print` 和 `println` 的地方使用 `PrintStream` 类的方法

`public PrintStream format(String format, Object... args)`

**作用：** 使用指定的格式和参数，向输出流写入格式化后的字符串

**参数：**

* `format` ：格式化字符串
* `args` ：用于替换 `format` 中的点位符
  
  * 如果 `args` 中的参数个数比在 `format` 中指定的参数多，将会忽略 `args` 中多余的参数
  * `args` 可以是变量，也可以不传
  * `args` 支撑的最大参数数量由数组的最大数量决定

**返回：** 输出流

#### 示例

```java
public static void main(String[] args) {
    long n = 461012;
    System.out.format("%d%n", n);      //  -->  "461012"
    System.out.format("%08d%n", n);    //  -->  "00461012"
    System.out.format("%+8d%n", n);    //  -->  " +461012"
    System.out.format("%,8d%n", n);    // -->  " 461,012"
    System.out.format("%+,8d%n%n", n); //  -->  "+461,012"

    double pi = Math.PI;

    System.out.format("%f%n", pi);       // -->  "3.141593"
    System.out.format("%.3f%n", pi);     // -->  "3.142"
    System.out.format("%10.3f%n", pi);   // -->  "     3.142"
    System.out.format("%-10.3f%n", pi);  // -->  "3.142"
    System.out.format(Locale.FRANCE, "%-10.4f%n%n", pi); // -->  "3,1416"

    Calendar c = Calendar.getInstance();
    System.out.format("%tB %te, %tY%n", c, c, c); // -->  "May 29, 2006"

    System.out.format("%tl:%tM %tp%n", c, c, c);  // -->  "2:34 am"

    System.out.format("%tD%n", c);    // -->  "05/29/06"
}
```

示例中使用到的格式化转换和标识的说明：

| 转换     | 标识 | 说明                                                         |
| -------- | ---- | ------------------------------------------------------------ |
| `d`      |      | 十进制数                                                     |
| `f`      |      | 浮点数                                                       |
| `n`      |      | 表示新的一行，具体的字符依据当前运行应用的平台调整。应该总是使用 `%n`，而不应该使用 `\n` |
| `tB`     |      | 日期时间转换——特定于地区的月份全称                           |
| `td，te` |      | 日期时间转换——两位数字表示月份中的某一天。一位数字时，`td` 有前导 `0`，`te` 没有 |
| `ty，tY` |      | 日期时间转换——`ty`：两位数字表示年份；`tY`：四位数字表示年份 |
| `tl`     |      | 日期时间转换——12小时制的小时表示                             |
| `tM`     |      | 日期时间转换——两位数字的分钟，前导 `0` 一定会存在            |
| `tp`     |      | 日期时间转换——特定于区域的 `am/pm` 时间                      |
| `tm`     |      | 日期时间转换——两位的月份表示，前导 `0` 是必须的              |
| `tD`     |      | 日期时间转换——使用 `%tm%td%ty` 格式显示日期                  |
|          | `08` | `8` 个字符宽度，如果有需要，增加前置 `0`                     |
|          | `+`  | 包含符号，有 `+` 和 `-`                                      |
|          | `,`  | 包含特定于语言的分组字符                                     |
|          | `-`  | 左对齐                                                       |
|          | `.3` | 小数点后保留 `3` 位小数                                      |

#### DecimalFormat 类

可以使用 `java.text.DecimalFormat` 类来控制小数前置 `0` 、尾随 `0` 的显示，小数的前缀和后缀，还有千分位分隔等

```java

import java.text.DecimalFormat;

public class DecimalFormatDemo {

    static public void customFormat(String pattern, double value ) {
        DecimalFormat myFormatter = new DecimalFormat(pattern);
        String output = myFormatter.format(value);
        System.out.println(value + "  " + pattern + "  " + output);
    }

    public static void main(String[] args) {
        customFormat("###,###.###", 123456.789);  // 123456.789  ###,###.###  123,456.789
        customFormat("###.##", 123456.789);       // 123456.789  ###.##  123456.79
        customFormat("000000.000", 123.78);       // 123.78  000000.000  000123.780
        customFormat("$###,###.###", 12345.67);   // 12345.67  $###,###.###  $12,345.67
    }
}
```

下面是每一行输出的解释：

| 值         | 格式                                                         | 输出        | 解释                                                         |
| ---------- | ------------------------------------------------------------ | ----------- | ------------------------------------------------------------ |
| 123456.789 | [![6Ej8fg.png](https://s3.ax1x.com/2021/03/04/6Ej8fg.png)](https://imgtu.com/i/6Ej8fg) | 123,456.789 | # 表示一个数字，逗号是分组分隔符的占位符，句号是小数点分隔符的占位符 |
| 123456.789 | [![6Ejd00.png](https://s3.ax1x.com/2021/03/04/6Ejd00.png)](https://imgtu.com/i/6Ejd00) | 123456.79   | 该值在小数点右边有三位数，但是在格式中只有两位，`format` 通过四舍五入来解决该问题 |
| 123.78     | 000000.000                                                   | 000123.780  | 该模式指定前导零和尾随零，因为使用0字符代替了井号（＃）      |
| 12345.67   | [![6EjBkT.png](https://s3.ax1x.com/2021/03/04/6EjBkT.png)](https://imgtu.com/i/6EjBkT) | $12,345.67  |                                                              |

## 简单 Java 类

在以后进行项目的开发与设计的过程中，简单 `Java` 类都将作为一个重要的组成部分存在，慢慢接触到正规的项目设计之后，简单 `Java` 类无处不在，并且有可能会产生一系列的变化。

所谓的简单 `Java` 类指的是可以描述某一类信息的程序类，例如：描述一个人、描述一本书、描述一个部门、描述一个部员，并且在这个类之后并没有特别复杂的逻辑操作，只作为一种信息存储的媒介存在。

对于简单 `Java` 类而言，其核心的开发结构如下（未完成，后面有补充）：

* 类名一定要有意义，可以明确的描述一类的事物
* 类之中的所有属性都必须使用 `private` 进行封装，同时封装后的属性必须要提供有 `getter`、`setter` 方法
* 类之中可以提供有无数多个构造方法，但是必须要保留有无参构造方法
* 类之中不允许出现任何的输出语句，所有的内容的获取必须返回
* 【非必须】可以提供有一个获取对象详细信息的方法，暂时将此方法名称定义为 `getInfo

## 第十六章 集合框架

### 集合

对象的容器，定义了对多个对象进行操作的常用方法。可实现数组的功能

#### 和数组的区别

* 数组固定长度，集合长度不固定
* 数组可以存储基本类型和引用类型，集合只能存储引用类型

#### 位置

集合相关的类都位于 `java.util` 包下

### Collection体系集合

[![6Ejyp4.md.png](https://s3.ax1x.com/2021/03/04/6Ejyp4.md.png)](https://imgtu.com/i/6Ejyp4)

### Collection 父接口

代表一组任意类型的对象，无序、无下标、元素可重复

#### 方法

* `boolean add(Object obj)` ：添加一个对象
* `boolean addAll(Collection c)` ：将一个集合中的所有对象添加到此集合中
* `void clear()`：清空此集合中的所有对象
* `boolean contains(Object o)` ：检查此集合中是否包含 `o` 对象
* `boolean equals(Object o)` ：比较此集合是否与指定对象相等
* `boolean isEmpty()` ：判断此集合是否为空
* `boolean remove(Object o)` ：在此集合中移除 `o` 对象
* `int size()` ：返回此集合中元素个数
* `Object[] toArray()` ：将此集合转换为数组

#### 示例

```java
public class Course15 {

    public static void main(String[] args) {
        Collection collection = new ArrayList();

        // 1. 新增操作
        System.out.println("============1. 新增操作============");
        collection.add("水煮鱼");
        collection.add("回锅肉");
        collection.add("毛血旺");
        System.out.println("集合里的元素个数：" + collection.size());
        System.out.println(collection);

        // 2. 迭代元素
        System.out.println("===========2. 迭代元素=============");
        // 集合的循环需要用到迭代器 Iterator
        Iterator iterator = collection.iterator();
        // 2.1 第一种循环方式
        for (Object str : collection) {
            System.out.println(str);
        }
        // 2.2 第二种循环方式
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }

        // 3. 判断
        System.out.println("===========3. 判断=============");
        System.out.println(collection.isEmpty());
        System.out.println(collection.contains("毛血旺"));

        // 4. 删除
        System.out.println("===========4. 删除=============");
//        collection.clear();
//        System.out.println("删除后的元素个数：" + collection.size());
        // 4.1 注意：在遍历的时候，不能使用集合本身的删除方法，会报错或者删不干净
        iterator = collection.iterator();
        // 下面是错误的示例
//        while (iterator.hasNext()) {
//            Object next = iterator.next();
//            System.out.println(next);
//            collection.remove(next);
//        }
        // 应该使用迭代器的删除
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
            iterator.remove();
        }
        System.out.println("删除后的元素个数：" + collection.size());
        System.out.println(collection);
    }
}


// 下面是输出
============1. 新增操作============
集合里的元素个数：3
[水煮鱼, 回锅肉, 毛血旺]
===========2. 迭代元素=============
水煮鱼
回锅肉
毛血旺
水煮鱼
回锅肉
毛血旺
===========3. 判断=============
false
true
===========4. 删除=============
水煮鱼
回锅肉
毛血旺
删除后的元素个数：0
[]
```

### List

#### 特点

有序、有下标、元素可重复

#### 方法

* `void add(int index, Object o)` ：在 `index` 位置插入对象 `o`
* `boolean addAll(int index, Collection c)` ：将一个集合中的元素添加到此集合中的 `index` 位置
* `Object get(int index)` ：返回集合中指定位置的元素
* `List subList(int fromIndex, int toIndex)` ：返回 `fromIndex` 到 `toIndex` 之间（`[fromIndex, toIndex)`）的集合元素
* `int indexOf(Object o)` ：返回集合中第一个匹配的元素索引，不存在返回 `-1`

```java
public class Course15 {

    public static void main(String[] args) {
        List<String> list = new ArrayList<>();

        // 1. 新增
        System.out.println("===========1. 新增============");
        list.add("小米");
        list.add("苹果");
        list.add(0, "华为");
        System.out.println("元素个数：" + list.size());
        System.out.println(list);

        // 2. 删除
//        System.out.println("============2. 删除===========");
//        list.remove(1);
//        System.out.println("元素个数：" + list.size());
//        System.out.println(list);

        // 3. 遍历
        System.out.println("==========3. 遍历=============");
        // 3.1 一般 for
        System.out.println("===========3.1 一般 for============");
        for (int i = 0; i < list.size(); i++) {
            System.out.println(i + " : " + list.get(i));
        }
        // 3.2 增加 for
        System.out.println("===========3.2 增加 for============");
        for (String s : list) {
            System.out.println(s);
        }
        // 3.3 iterator
        System.out.println("===========3.3 iterator============");
        Iterator<String> iterator = list.iterator();
        while (iterator.hasNext()) {
            System.out.println(iterator.next());
        }
        // 3.4 listIterator
        System.out.println("===========3.4 listIterator============");
        ListIterator<String> stringListIterator = list.listIterator();
        while (stringListIterator.hasNext()) {
            System.out.println(stringListIterator.nextIndex() + " : " + stringListIterator.next());
        }
        while (stringListIterator.hasPrevious()) {
            System.out.println(stringListIterator.previousIndex() + " : " + stringListIterator.previous());
        }

        // 4. 判断
        System.out.println("===========4. 判断============");
        System.out.println(list.contains("香蕉"));
        System.out.println(list.isEmpty());

        // 5. 获取
        System.out.println("===========5. 获取============");
        System.out.println(list.indexOf("小米"));
    }
}

// 下面是输出
===========1. 新增============
元素个数：3
[华为, 小米, 苹果]
==========3. 遍历=============
===========3.1 一般 for============
0 : 华为
1 : 小米
2 : 苹果
===========3.2 增加 for============
华为
小米
苹果
===========3.3 iterator============
华为
小米
苹果
===========3.4 listIterator============
0 : 华为
1 : 小米
2 : 苹果
2 : 苹果
1 : 小米
0 : 华为
===========4. 判断============
false
false
===========5. 获取============
1
```

```java
public class Course15 {

    public static void main(String[] args) {
        List<Integer> list = new ArrayList<>();

        list.add(200);
        list.add(300);
        list.add(400);
        list.add(500);
        list.add(600);

        System.out.println(list.size());
        System.out.println(list);

//        list.remove(new Integer(200));
        list.remove((Object)200);
        System.out.println(list.size());
        System.out.println(list);

        List<Integer> list1 = list.subList(1, 3);
        System.out.println(list1);
    }
}

// 注意：List 里面只能存储引用类型的数据，所以 list.add(200); 这句话，
// 其实隐藏着一个自动装箱的操作，所以在移除基本数据类型的元素时，需要把
// 基本数据类型转换为对应的包装类型

// 以下是输出
5
[200, 300, 400, 500, 600]
4
[300, 400, 500, 600]
[400, 500]
```

#### 实现类

* `ArrayList`（重点）：
  
  * 数组结构实现，查询快、增删慢
  * `JDK 1.2` 加入，运行效率快、线程不安全
  * 常/变量：
    
    * `DEFAULT_CAPACITY = 10` ：默认容量大小
      
      * 注意：该容量是添加元素后的默认容量，如果一个元素都没有，默认容量为 `0`，添加做生意一个元素之后，容量扩容为 `10`；以后每次的扩容大小为原来大小的 `1.5` 倍
    * `elementData` ：存放列表元素的数组
* `Vector` ：
  
  * 数组结构实现，查询快、增删慢
  * `JDK 1.0` 加入，运行效率慢、线程安全
* `LinkedList` ：
  
  * 链表结构实现，增删快、查询慢

### 集合的问题

1. 集合对元素类型没有任何限制
2. 从集合取出的元素都是 `Object` 类型的，可能在使用时会引发 `ClassCastException` 异常

#### 错误举例

```java
public class Course17 {

    public static void main(String[] args) {
        List list = new ArrayList();
        list.add("123");
        list.add("Hello");
        list.add(5);

        for (Object o : list) {
            // 下面这一句会产生 ClassCastException 异常
            System.out.println(((String)o).length());
        }
    }
}
```

### 泛型

`Java` 的泛型是 `JDK 1.5` 引入的一个新特性，其本质是参数化类型，即把类型当作参数传递，常见的形式有：泛型类、泛型接口、泛型方法

`Java` 增加泛型的支持，在很大程度上都是为了让集合能够记住其它元素的数据类型。

> `Java` 的泛型可以保证：如果在编译时没有发出警告，运行时就不会产生 ClassCastException 异常

#### 语法

`<T,...>`

* `T` 称为类型占位符，表示一种**引用类型**
* `T` 可以换为任意一个大写字母，一般使用的有：
  * `E` —— `Element`，该字母被 `Java` 框架集合广泛使用
  * `K` —— `Key`
  * `N` —— `Number`
  * `T` ——    `Type`
  * `V` —— `Value`
  * `S`、`U`、`V` 等 —— 第2、3、4种类型

#### 好处

* 提高代码的重用性
* 防止类型转换异常，提高代码的安全性

#### 泛型集合

参数化类型、类型安全的集合，强制集合元素的类型必须一致

##### 特点

* 编译期就可以检查，而非运行时抛出异常
* 访问时，不必类型转换（拆箱）
* 不同泛型之间引用不能相互赋值，泛型不存在多态

#### 泛型不能存在的地方

* 静态初始化块
* 静态变量的声明和初始化
* `instanceOf` 运算符之后不能使用泛型类

```java
{
    ArrayList<String> strings = new ArrayList<>();
    strings.add("234");

    Collection<Integer> collection = new ArrayList<>();
    collection.add(234);
}

{
    Car<Person> personCar = new Car<>();
    personCar.oil();
}

{
    ArrayList<String> list1 = new ArrayList<>();
    list1.add("234");
    list1.add("345");


    ArrayList<Integer> list2 = new ArrayList<>();
    list2.add(3);
    list2.add(4);

    for (String s : list1) {
        System.out.println(s);
    }

    for (Integer integer : list2) {
        System.out.println(integer);
    }

}
{
    // 下面的泛型申明是 <? extends Person>
    // P 继承了 Person
    Futer<Person> personFuter = new Futer<>();
    Futer<P> pFuter = new Futer<>();
}
```

### Set 集合

#### 特点

无序、无下标、元素不可重复

`Set` 集合的所有方法全部来自于 `Collection`，自己并没有添加新的方法，所以，适用于 `Collection` 都适用于 `Set`

```java
// Set 系列演示
{
    Set<String> set = new HashSet<>();

    // 1. 增加
    set.add("123");
    set.add("321");
    set.add("456");
    set.add("789");

    // 2. 循环
    /*for (String s : set) {
        System.out.println(s);
    }

    Iterator<String> iterator = set.iterator();
    while (iterator.hasNext())
        System.out.println(iterator.next());*/

    // 3. 删除
    set.remove("123");
    set.add("321");
    /*for (String s : set) {
        System.out.println(s);
    }*/

    // 4. 判断
    System.out.println(set.contains("7892"));
}
```

### HashSet

存储结构：哈希表（数组+链表）

存储过程（重复的判断依据）：

1. 根据 `hashcode` 计算保存的位置，如果此位置为空，则直接保存，如果不为空执行第2步
2. 执行 `equals` 方法，如果 `equals` 方法为 `true`，则认为是重复，否则，形成链表

```java
// HashSet 进阶用法展示
// 根据 Person 的年龄和姓名进行判重的秘诀是：重写 hashCode 和 equals 方法
{
    HashSet<Person> people = new HashSet<>();

    Person zhangsan = new Person("张三", 22);
    Person lisi = new Person("李四", 20);
    Person liuliu = new Person("刘六", 24);

    people.add(zhangsan);
    people.add(lisi);
    people.add(liuliu);
//            people.add(liuliu);

    people.add(new Person("刘六", 24));

    /*for (Person person : people) {
        System.out.println(person);
    }*/
}
```

### TreeSet

* 基于排列顺序实现元素不重复
* 实现了 `SortedSet` 接口，对集合元素自动排序
* 元素对象的类型必须实现 `Comparable` 接口，指定排序规则
* 通过 `CompareTo` 方法确定是否为重复元素

```java
// TreeSet
// TreeSet 使用自定义的排序规则的方法：
//     1. TreeSet 使用的泛型类型实现了 Comparable 接口，在 compareTo 方法中实现自定义的排序方式
//     2. 在实例化 TreeSet 时，使用匿名内部类的方式，实现 Comparator 接口的 compare 方法，实现自定义的排序方式
{
    TreeSet<Person> treeSet = new TreeSet<>(new Comparator<Person>() {
        @Override
        public int compare(Person o1, Person o2) {
            return o1.getAge() - o2.getAge();
        }
    });

    Person zhangsan = new Person("张三", 22);
    Person lisi = new Person("李四", 20);
    Person liuliu = new Person("刘六", 24);

    treeSet.add(zhangsan);
    treeSet.add(lisi);
    treeSet.add(liuliu);

    for (Person person : treeSet) {
        System.out.println(person);
    }
}
```

### Map

[![6Ejf76.png](https://s3.ax1x.com/2021/03/04/6Ejf76.png)](https://imgtu.com/i/6Ejf76)

#### 特点

* 用于存储任意键值对（`key-value`）
* 键：无序、无下标、不允许重复（唯一）
* 值：无序、无下标、允许重复

### Map 父接口

#### 方法

* `V put(K key, V value)` ：将对象存入到集合中，关联键值，`key` 重复则覆盖原值
* `Object get(Object key)` ：根据键获取对应的值
* `Set<K> keySet()` ：返回所有的 `key`
* `Collection<V> values()` : 返回包含所有值的 `Collection` 集合
* `Set<Map.Entry<K,V>> entrySet()` ：返回键值匹配的 `Set` 集合
* `boolean containsKey(Object key)` ：如果包含指定的键，返回 `true`
* `boolean containsValue(Object value)` : 如果包含一个或多个的值，返回 `true`

### HashMap（重点）

`JDK 1.2` 版本引入，线程不安全，运行效率快，允许使用 `null` 作为 `key` 或者 `value`

> `HashMap` 无参的构造器会构造一个具有默认初始容量（16）和默认加载因子（0.75） 的空 `HashMap`

#### 源码分析

```java
static final int DEFAULT_INITIAL_CAPACITY = 1 << 4; // 默认初始化的容量
static final int MAXIMUM_CAPACITY = 1 << 30; // 最大容量
static final float DEFAULT_LOAD_FACTOR = 0.75f； // 加载因子
static final int TREEIFY_THRESHOLD = 8; // 当链表长度大于8时，并且数组元素大于64时，调整成红黑树
static final int MIN_TREEIFY_CAPACITY = 64; // 当链表长度大于8时，并且数组元素大于64时，调整成红黑树
transient Node<K,V>[] table; // 哈希表中的数组
transient int size; // 元素个数
```

##### 总结

1. `HashMap` 刚创建时，`table` 是 `null`，为了节省空间，当添加第一个元素时，`table` 容量调整为 `16`
2. 当元素个数大于阀值 $ 16 * 0.75 = 12 $ 时，会进行扩容，扩容后大小为原来的 `2` 倍，目的是减少调整元素的个数
3. `jdk 1.8` 当每个链表长度大于 `8`，并且数组元素个数大于等于 `64` 时，会调整为红黑树，目的是为了提高执行效率
4. `jdk 1.8` 当链表长度小于 `6` 时，调整为链表
5. `jdk 1.8` 以前，链表从头插入，`jdk 1.8` 以后，链表从尾插入

### HashTable（了解即可）

`jdk 1.0` 版本引入，线程安全，运行效率慢，不允许 `null` 作为 `key` 或者 `value`

### Properties

> 流讲完后，再详细讲解这个类

`HashTable` 的子类，要求 `key` 和 `value` 都是 `String`， 通常用于配置文件的读取

* 存储属性名和属性值
* 属性名和属性值都是字符串类型
* 没有泛型
* 和流有关

### TreeMap

实现了 `SortedMap` 接口（是 `Map` 的子接口），可以对 `key` 自动排序

### Collections 工具类

集合工具类，定义了除了存取以外的集合常用方法

#### 方法

* `public static void reverse(List<?> list)` ：反转集合中元素的顺序
* `public static void shuffle(List<?> list)` ：随机重置集合中元素的顺序
* `public static void sort(List<T> list)` ：升序排序（元素类型必须实现 `Comparable` 接口）

## 第十七章 异常

程序在运行中出现的不正常现象，出现异常不处理将终止程序运行。

### 处理异常的必要性

任何程序都可能存在大量的未知问题、错误，如果不对这些问题进行正确处理，则可能导致程序的中断，造成不必要的损失

### 异常处理

`Java` 编程语言使用异常处理机制为程序提供了异常处理的能力

### Throwable

可抛出的，一切错误或异常的父类，位于 `java.lang` 包中

#### Error

`JVM`、硬件、执行逻辑错误，不能手动处理，例如：`StackOverflowError`、`OutOfMemoryError`

#### Exception

程序在运行和配置中产生的问题，可处理

**分类：**

* `RuntimeException` ：运行时异常，可处理，可不处理
  
  * `NullPointerExceptioin` ：空指针异常
  * `ArrayIndexOutOfBoundsException` ：数组越界异常
  * `ClassCastException` ：类型转换异常
  * `NumberFormatException` ：数字格式化异常
  * `ArithmeticException` ：算术异常
* `CheckedException` ：检查时异常，必须处理

### 异常的传递

按照方法的调用链反向传递，如果始终没有处理异常，最终会由 `JVM` 进行默认异常处理（打印堆栈跟踪信息）

> 出现异常没有处理，程序会在出异常的地方中断

### 异常处理

`Java` 的异常处理是通过 `5` 个关键字来实现的：

* `try` ：执行可能产生异常的代码
* `catch` ：捕获异常并处理
* `finally` ：无论异常是否发生，代码总能执行
* `throw` ：手动抛出异常
* `throws` ：声明方法可能要抛出的各种异常

#### 第一种结构

```java
try {
    // 可能出现异常的代码
} catch(Exception e) {
    // 异常处理的相关代码，如：getMessage()、printStackTrace()
}
```

上面的结构可能会出现以下三种情况：

1. 正常请求
2. 出现异常并处理
3. 异常类型不匹配

#### 第二种结构

```java
try {
    // 可能出现异常的代码
} catch(Exception e) {
    // 异常处理的相关代码，如：getMessage()、printStackTrace()
} finally {
    // 无论出现异常都会执行，可以释放资源等……
}
```

> 1. 无论是否发生异常，finally 块中的代码都可以执行，可以用于释放资源
> 2. finally 块中的代码不执行的唯一情况，就是退出 java 虚拟机
> 3. java 的垃圾回收机制不会回收任何物理资源，垃圾回收机制只能回收堆内存中对象所占用的内存
> 4. 不要在 finally 块中使用如 return、throw 等导致方法终止的语句，如果这样做了，将会导致 try 块、catch 块中的 return、throw 语句失效

#### 第三种结构

```java
try {
    // 可能出现异常的代码
} catch(异常类型1) {
    // 异常处理的相关代码，如：getMessage()、printStackTrace()
} catch(异常类型2) {
    // 异常处理的相关代码，如：getMessage()、printStackTrace()
} catch(异常类型3) {
    // 异常处理的相关代码，如：getMessage()、printStackTrace()
} ...
```

上面的结构注意事项：

1. 子类异常在前，父类异常在后
2. 发生异常时按顺序逐个匹配
3. 只执行第一个与异常类型匹配的 `catch` 语句
4. `finally` 根据需求可写可不写

#### 第四种结构

```java
try {
    // 可能出现异常的代码
} finally {
    // 无论出现异常都会执行，可以释放资源等……
}
```

注意：

1. 该结构不能捕获异常，仅仅用来当发生异常时，用来释放资源
2. 一般用在底层代码，只释放资源不做异常处理，把异常向上抛出

> 1. try、catch、finally 块后的花括号不能省略，即使块里面只有一行代码
> 2. 根据块级代码作用域的原则，try 块中声明的变量，不能在 catch、finally 块中访问

### 多异常捕获

在 `Java 7` 以前，每个 `catch` 块只能捕获一种类型的异常；但从 `Java 7` 开始，一个 `catch` 块可以捕获多个类型的异常：

* 捕获多种类型的异常时，多种异常类型之间用竖线（`|`）隔开
* 捕获多种类型的异常时，异常变量有隐式的 `final` 修饰，因此程序不能对异常变量重新赋值

```java
public class Course19 {

    public static void main(String[] args) {
        try {
            int a = Integer.parseInt(args[0]);
            int b = Integer.parseInt(args[1]);
            System.out.println(a / b);
        } catch (NumberFormatException | ArithmeticException e) {
            e.printStackTrace();
            // 下面会报错
            e = new ArithmeticException("test");
        } catch (Exception ex) {
            System.out.println(ex.getMessage());
            // 下面的正常
            ex = new Exception("test");
        }
    }
}
```

### 异常信息

所有异常对象都包含了如下几个常用方法：

* `getMessage()` ：返回该异常的详细描述字符串
* `printStackTrace()` ：将该异常的跟踪栈信息输出到标准错误输出
* `printStackTrace(PrintStream ps)` ：将该异常的跟踪栈信息输出到指定输出流
* `getStackTrace()` ：返回该异常的跟踪栈信息

### 声明异常

关键字：`throws`，用于底层代码向上抛出或声明异常，最上层一定要处理异常，否则程序中断

### 抛出异常

关键字：`throw` ，除了系统自动抛出异常外，有些问题需要程序员自行抛出异常

语法：`throw 异常对象`

### 自定义异常

自定义异常的类需要继承 `Exception` 或 `Exception` 的子类，常用 `RuntimeException`

必须提供的构造方法：

* 无参构造方法
* `String message` 参数的构造方法

### 带有异常声明的方法覆盖

要求：

1. 方法名、参数列表、返回值类型必须和父类相同
2. 子类的访问修饰符权限与父类相同或是比父类更宽
3. 子类中的方法，不能抛出比父类更多、更宽的检查时异常（主要指检查时异常）

### 自动关闭资源 try 语句

`Java 7` 增加了 `try` 语句的功能——允许在 `try` 关键字后紧跟一对圆括号，圆括号可以声明、初始化一个或多个资源，此处的资源指的是那些必须在程序结束时显式关闭的资源（比如数据库连接，网络连接等），`try` 语句在该语句结束时自动关闭这些资源

自动关闭资源的 `try` 语句相当于包含了隐式的 `finally` 块（该块用于关闭资源），因此这个 `try` 语句可以既没有 `catch` 块，也没有 `finally` 块

### 总结

* 异常处理结构语法中只有 `try` 块是必须的，也就是说，如果没有 `try` 块，则不能有后面的 `catch` 块和 `finally` 块
* `catch` 块和 `finally` 块都是可选的，但 `catch` 块和 `finally` 块至少出现其中之一，也可以同时出现
* 可以有多个 `catch` 块，捕获父类异常的 `catch` 块必须位于捕获子类异常的后面
* 不能只能 `try` 块，既没有 `catch` 块，也没有 `finally` 块
* 多个 `catch` 块必须位于 `try` 块之后，`finally` 块必须位于所有的 `catch` 块之后

## 第十八章 MVC 设计模式

> [原文](https://www.tutorialspoint.com/design_pattern/mvc_pattern.htm)

`MVC` 模式指的是：模型（`Model`）——视图（`View`）——控制器（`Controller`）模式，该模式用于分离应用的关注点：

* `Model`——一个模型代表着用于传递数据的对象（`Object`）或者 `Java POJO`。如果数据发生变化，它可以逻辑更新控制器（`Controller`）
* `View`——视图代表着模型中包含数据的可视化展现
* `Controller`——控制器作用于模型和视图两部分。它控制着数据流向模型，而且当数据发生变化，它还控制着视图的更新。它使得模型与视图分离

### 实现

我们要创建一个学生对象作为一个模型。`StudentView` 是一个视图类，可以在控制台上打印学生信息的细节，`StudentController` 是控制器类，负责把学生信息存储到 `Student` 对象中，并相应地更新 `StudentView` 视图。

`MVCPatternDemo` 是一个演示类，会使用 `StudentController` 类来演示 `MVC` 模式的使用

![](index_files/6c301597-89af-4345-96f5-6428bbca26f0.png)

### 步骤一

创建模型：`Student.java`

```java
public class Student {
    private String rollNo;
    private String name;

    public String getRollNo() {
        return rollNo;
    }

    public void setRollNo(String rollNo) {
        this.rollNo = rollNo;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```

### 步骤二

创建视图：`StudentView.java`

```java
public class StudentView {
   public void printStudentDetails(String studentName, String studentRollNo){
      System.out.println("Student: ");
      System.out.println("Name: " + studentName);
      System.out.println("Roll No: " + studentRollNo);
   }
}
```

### 步骤三

创建控制器：`StudentController.java`

```java
public class StudentController {
    private Student model;
    private StudentView view;

    public StudentController(Student model, StudentView view) {
        this.model = model;
        this.view = view;
    }

    public void setStudentName(String name) {
        model.setName(name);
    }

    public String getStudentName() {
        return model.getName();
    }

    public void setStudentRollNo(String rollNo) {
        model.setRollNo(rollNo);
    }

    public String getStudentRollNo() {
        return model.getRollNo();
    }

    public void updateView(){
        view.printStudentDetails(model.getName(), model.getRollNo());
    }
}
```

### 步骤四

使用控制器的方法演示 `MVC` 设计模式的用法：`MVCPatternDemo.java`

```java
public class MVCPatternDemo {

    public static void main(String[] args) {
        Student student = retriveStudentFromDatabase();

        // 创建视图：用于把学生信息输出到控制台
        StudentView view = new StudentView();

        StudentController controller = new StudentController(student, view);

        controller.updateView();

        // 更新视图
        controller.setStudentName("John");

        controller.updateView();
    }

    public static Student retriveStudentFromDatabase() {
        Student student = new Student();
        student.setName("Robert");
        student.setRollNo("10");
        return student;
    }
}
```

### 步骤五

验证输出

```java
Student: 
Name: Robert
Roll No: 10
Student: 
Name: John
Roll No: 10
```

## 第十九章 IO

### 流

内存与存储设备之间传输数据的通道

### 分类

* 按方向（重点）
  
  * 输入流
    
    * 将 <存储设备> 中的内容读入到 <内存> 中
  * 输出流
    
    * 将 <内存> 中的内容写入到 <存储设备> 中
* 按单位
  
  * 字节流
    
    * 以字节为单位，可以读写所有数据
  * 字符流
    
    * 以字符为单位，只能读写文本数据
* 按功能
  
  * 节点流
    
    * 具有实际传输数据的读写功能
  * 过滤流
    
    * 在节点流的基础之上增强功能

### 字节流

[![6EL4AS.png](https://s3.ax1x.com/2021/03/04/6EL4AS.png)](https://imgtu.com/i/6EL4AS)

#### 父类（抽象类）

* `InputStream` ：字节输入流
  
  * `public int read()`
  * `public int read(byte[] b)`
  * `public int read(byte[] b, int off, int len)`
* `OutputStream` ：字节输出流
  
  * `public void write(int n)`
  * `public void write(byte[] b)`
  * `public void write(byte[] b, int off, int len)`

#### 子类

* `FileInputStream` 
  
  * `public int read(byte[] b)` ：从流中读取多个字节，将读到的内存存入 `b` 数组，返回实际讲到的字节数；如果达到文件的尾部，则返回 `-1`
* `FileOutStream`
  
  * `public void write(byte[] b)` ：一次写多个字节，将 `b` 数组中所有字节，写入输出流

#### 字节缓冲流

`BufferedInputStream/BufferedOutputStream`

* 提高 `IO` 效率，减少访问磁盘的次数
* 数据存储在缓冲区中，`flush` 是将缓冲区的内容写入文件中，也可以直接 `close`

```java
public class DemoBufferedInputStream {

    public static void main(String[] args) throws Exception {
        FileInputStream fis = new FileInputStream("dontlaugh.txt");
        BufferedInputStream bis = new BufferedInputStream(fis);

        long start = System.currentTimeMillis();
        int count;

        // 此方法没有使用缓存，速度比较慢
        /*while ((count = bis.read()) != -1) {
            System.out.print((char)count);
        }*/

        // 此方法使用了缓存，速度比较快
        while ((count = fis.read()) != -1) {
            System.out.print((char)count);
        }
        long end = System.currentTimeMillis();
        System.out.println();
        System.out.println(end - start);

        bis.close();
    }
}
```

```java
public class DemoBufferedOutputStream {

    public static void main(String[] args) throws Exception {
        FileOutputStream fos = new FileOutputStream("output.txt");
        BufferedOutputStream bos = new BufferedOutputStream(fos);

        String lyric = "那是我日夜思念深深爱着的人啊\n到底要我如何表达\n她会接受我吗\n也许永远都不会跟她说出那句话\n而我注定要浪迹天涯\n怎么能有牵挂";

        long start = System.currentTimeMillis();

        // 这时候只是写入了缓冲区，还没有将内容写入文件之中
        bos.write(lyric.getBytes());

        long end = System.currentTimeMillis();
        System.out.println(end - start);

        // close 时会调用 flush，将内容从缓冲区写入到文件之中
        bos.close();
    }
}
```

#### 对象流

`ObjectOutputStream/ObjectInputStream`

* 增强了缓冲区功能
* 增强了读取 `8` 种基本数据类型和字符串功能
* 增强了读取对象的功能
  
  * `readObject()`：从流中读取一个对象
  * `writeObject(Object obj)`：向流中写入一个对象

> 使用流传输对象的过程叫做 **序列化，反序列化**

```java
public class DemoObjectOutputStream {

    public static void main(String[] args) throws Exception {
        FileOutputStream fos = new FileOutputStream("zhangsan.bin");
        ObjectOutputStream oos = new ObjectOutputStream(fos);

        Student stud = new Student("zhangsan", 20);
        // 这里序列化的对象一定要实现 Serializable 接口，要不然会报错
        // 序列化类的注意事项：
        // 1. 必须要实现 Serializable 接口
        // 2. 类中的属性都要求实现 Serializable 接口
        // 3. 序列化的类中，需要添加一个序列化版本号 ID，用于保证序列化的类和反序列化的类是一个类
        // 4. 使用 transient 修改属性，该属性不能被序列化
        // 5. 静态属性不能序列化
        // 6. 序列化多个对象，可以借助集合实现
        oos.writeObject(stud);

        oos.close();
    }
}
```

```java
public class DemoObjectInputStream {

    public static void main(String[] args) throws Exception {
        FileInputStream fis = new FileInputStream("zhangsan.bin");
        ObjectInputStream ois = new ObjectInputStream(fis);

        // 从文件中读取并重构对象，反序列化
        Student stu = (Student) ois.readObject();

        ois.close();

        System.out.println(stu.toString());
    }
}
```

### 字符流

[![6ELX7T.png](https://s3.ax1x.com/2021/03/04/6ELX7T.png)](https://imgtu.com/i/6ELX7T)

#### 字符编码

* `ISO-8859-1`：收录除 `ASCII` 外，还包括西欧、希腊语、泰语、阿拉伯语、希伯来语对应的文字符号
* `UTF-8`：针对 `Unicode` 码表的可变长度字符编码
* `GB2312`：简体中文
* `GBK`：简体中文、扩充
* `BIG5`：台湾，繁体中文

> 编码和解码方式不一致时，会出现乱码

#### 父类（抽象类）

* `Reader`：字符输入流
* `Writer`：字符输出流

#### 子类（文件字符流）

* `FileReader`
  
  * `public int read(char[] c)`：从流中读取多个字符，将讲到内容存入 `c` 数组，返回实际读到的字符数；如果达到文件的尾部，则返回 `-1`
    
    ```java
    public class DemoFileReader {
    
        public static void main(String[] args) throws Exception {
            FileReader file = new FileReader("dontlaugh.txt");
    
            int count = 0;
            // 一次读取一个字符
            while ((count = file.read()) != -1) {
                System.out.println((char)count);
            }
    
            // 一次读取 1024 个字符
            char[] chars = new char[1024];
            while ((count = file.read(chars)) != -1) {
                System.out.println(new String(chars, 0, count));
            }
    
            file.close();
        }
    }
    ```
* `FileWriter`
  
  * `public void write(String str)`：一次写多个字符，将 `b` 数组中所有字符，写入输出流
    
    ```java
    public class DemoFileWriter {
    
        public static void main(String[] args) throws Exception {
            FileWriter file = new FileWriter("right.txt");
    
            file.write(new String("那是我日夜思念深深爱着的人啊\n到底要我如何表达\n它会接受我吗"));
    
            file.close();
        }
    }
    
    ```

#### 字符缓冲流

`BufferedReader/BufferedWriter`

* 高效读写
* 支持输入换行符
* 可一次写一行、读一行

```java
public class FileBufferedReader {

    public static void main(String[] args) throws Exception {
        BufferedReader reader = new BufferedReader(new FileReader("right.txt"));

        int count = 0;

        // 每次读取一个字符
        /*while ((count = reader.read()) != -1) {
            System.out.println((char)count);
        }*/

        // 每次读取 1K 字符到缓冲中
        /*char[] chars = new char[1024];
        while ((count = reader.read(chars)) != -1) {
            System.out.println(new String(chars, 0, count));
        }*/

        // 每次读取一行
        String str = null;
        while ((str = reader.readLine()) != null) {
            System.out.println(str);
        }

        reader.close();
    }
}
```

```java
public class DemoBufferedWriter {

    public static void main(String[] args) throws Exception {
        BufferedWriter writer = new BufferedWriter(new FileWriter("bufferedwriter.txt"));

        for (int i = 0; i < 10; i++) {
            writer.write("好好学习，天天向上！");
            // 根据操作系统不同，自动写入合适的换行符，比如：windows - \r\n，mac - \n
            writer.newLine();
            writer.flush();
        }

        writer.close();
    }
}
```

#### 打印流

`PrinteWriter`

* 封装了 `print()/println()` 方法，支持写入后换行
* 支持数据原样打印

```java
public class DemoPrintWriter {

    public static void main(String[] args) throws Exception {
        PrintWriter printWriter = new PrintWriter("print.txt");

        // 打印流输入文件的内容会原样输出
        printWriter.println(97);
        printWriter.println(true);
        printWriter.println(3.14);
        printWriter.print('a');

        printWriter.close();
    }
}
```

### 转换流（桥转换流）

`InputStreamReader/OutputStreamWriter`

* 可将字节流转换为字符流
* 可设置字符的编码方式

```java
public class DemoInputStreamReader {

    public static void main(String[] args) throws Exception {
        InputStreamReader isr = new InputStreamReader(new FileInputStream("dontlaugh.txt"), "latin1");

        int data = 0;
        while ((data = isr.read()) != -1) {
            System.out.println((char)data);
        }

        isr.close();
    }
}
```

```java
public class DemoOutputStreamWriter {

    public static void main(String[] args) throws Exception {
        OutputStreamWriter osw = new OutputStreamWriter(new FileOutputStream("OnputStreamWriter.txt"), "utf-8");

        int data = 0;
        for (int i = 0; i < 10; i++) {
            osw.write("我爱北京天安门，天安门上太阳升！\n");
            osw.flush();
        }

        osw.close();
    }
}
```

### File 类

代表物理盘符中的一个文件或者文件夹

* `createNewFile()`：创建一个新文件
* `mkdir()`：创建一个新目录
* `delete()`：删除文件或空目录
* `exists()`：判断 `File` 所代表的对象是否存在
* `getAbsolutePath()`：获取文件的绝对路径
* `getName()`：取得名字
* `getParent()`：获取文件/目录所在的目录
* `isDirectory()`：是否是目录
* `ifFile()`：是否是文件
* `length()`：获得文件的长度
* `listFiles()`：列出目录中的所有内容
* `renameTo()`：修改文件名

```java
public class DemoFileEasyCommon {

    public static void main(String[] args) throws Exception {
        seperator();
        fileOper();
        directoryOper();
    }

    /**
     * 分隔符
     */
    private static void seperator() {
        System.out.println("路径分隔符：" + File.pathSeparator);
        System.out.println("名称分隔符：" + File.separator);
    }

    /**
     * 文件常用操作
     */
    public static void fileOper() throws Exception {
        // 1. 创建文件
        File file = new File("file.txt");
        // 下面这句打印的是 file 的路径字符串，这时候，file 所代表的文件，可能存在，也可能不存在
        System.out.println(file.toString());

        // 2. 删除文件

        /*boolean res = file.createNewFile();
        System.out.println("文件创建：" + (res ? "成功" : "失败"));*/

        if (!file.exists()) {
            boolean newFile = file.createNewFile();
            if (!newFile)
                System.out.println("文件创建失败！");
            else
                System.out.println("文件创建成功！");
        } else {
            // 直接删除文件
            // System.out.println("文件删除" + (file.delete() ? "成功" : "失败"));

            // 虚拟机退出时过 5 秒删除
            /*Thread.sleep(5000);
            file.deleteOnExit();*/
        }

        // 3. 获取文件信息
        System.out.println("文件的绝对路径是：" + file.getAbsolutePath());
        System.out.println("获取路径：" + file.getPath());
        System.out.println("文件名称：" + file.getName());
        System.out.println("文件父目录：" + file.getParent());
        System.out.println("文件长度：" + file.length());
        System.out.println("文件创建时间：" + new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(new Date(file.lastModified())));

        // 4. 判断
        System.out.println("文件是否可写：" + file.canWrite());
        System.out.println("是否为文件：" + file.isFile());
        System.out.println("是否为隐藏：" + file.isHidden());
    }

    /**
     * 文件夹操作
     */
    public static void directoryOper() throws Exception {
        // 1. 创建文件夹
        File folder = new File("zero/");

        System.out.println("文件夹路径：" + folder.toString());

        if (!folder.exists()) {
            // boolean mkdirs = folder.mkdir(); // 只能创建单级目录
            boolean mkdirs = folder.mkdirs(); // 可以创建多级目录
            if (mkdirs)
                System.out.println("文件夹创建成功！");
            else
                System.out.println("文件夹创建失败！");
        }

        // 2. 删除文件夹

        // 直接删除文件夹，该文件夹必须是空目录
        /*boolean delete = folder.delete();
        System.out.println("删除文件夹" + (delete ? "成功" : "失败"));*/

        // 使用 JVM 删除
        /*folder.deleteOnExit();
        Thread.sleep(5000);*/

        // 3. 获取文件夹信息
        System.out.println("获取绝对路径：" + folder.getAbsolutePath());
        System.out.println("获取路径：" + folder.getPath());
        System.out.println("文件夹名称：" + folder.getName());
        System.out.println("获取父目录：" + folder.getParent());
        System.out.println("创建时间：" + new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(new Date(folder.lastModified())));

        // 4. 判断
        System.out.println("是否是文件夹：" + folder.isDirectory());
        System.out.println("是否隐藏：" + folder.isHidden());

        // 5. 遍历文件夹
        File directory = new File("/Users/wchya/Pictures");

        // 遍历名称的数组
        /*String[] list = directory.list();
        for (String name : list) {
            System.out.println(name);
        }*/

        // 遍历 File 的数组
        File[] files = directory.listFiles();
        for (File file : files) {
            System.out.println(file.getName() + (file.isDirectory() ? " 是 " : " 不是 ") + "文件夹");
        }
    }
}
```

#### FileFilter

* `public interface FileFilter`
  
  * `boolean accept(File pathName)`

当调用 `File` 类中的 `listFiles()` 方法时，支持传入 `FileFilter` 接口的实现类，对获取文件进行过滤，只有满足条件的文件才可以出现在 `listFiles()` 的返回值中

```java
public class DemoFileFilter {

    public static void main(String[] args) throws Exception {
        File file = new File("/Users/wchya/Pictures");
        File[] files = file.listFiles(new FileFilter() {
            @Override
            public boolean accept(File pathname) {
                if (pathname.getName().endsWith(".jpg") || pathname.getName().endsWith(".png"))
                    return true;
                return false;
            }
        });

        for (File file1 : files) {
            System.out.println(file1.getName());
        }
    }
}
```

```java
public class DemoRecursionTraverseFoldersAndDelFiles {

    public static void main(String[] args) {
        recursionTraverseFolders(new File("/Users/wchya/Downloads/photo"));
        deleteFolder(new File("/Users/wchya/Downloads/photo"));
    }

    /**
     * 递归打印文件夹下的所有文件和文件夹的绝对路径
     * @param root - 要遍历的文件夹
     */
    public static void recursionTraverseFolders(File root) {
        System.out.println(root.getAbsolutePath());
        File[] files = root.listFiles();

        if (files != null && files.length > 0) {
            for (File file : files) {
                if (file.isDirectory()) {
                    recursionTraverseFolders(file);
                } else {
                    System.out.println(file.getAbsolutePath());
                }
            }
        }
    }

    /**
     * 删除文件夹。先递归删除文件夹中子文件夹里的文件，再删除文件夹
     * @param root - 要删除的文件夹
     */
    public static void deleteFolder(File root) {
        File[] files = root.listFiles();

        if (files != null && files.length > 0) {
            for (File file : files) {
                if (file.isDirectory()) {
                    deleteFolder(file);
                } else {
                    System.out.println(file.getAbsolutePath() + " 删除 " + file.delete());
                }
            }
        }

        root.delete();
    }
}
```

## 第二十章 GUI 编程

### 核心技术

`Swing、AWT`

### 不流行的原因

* 界面不美观
* 需要 `JRE` 环境

### 为什么学习

* 可以根据自己的需求，写一些实用的小工具
* 工作的时候，在对原来的项目进行维护时可能会用到
* 了解 `MVC` 架构，了解监听

### AWT

#### 介绍

* `AWT-Abstract Window Tools`，抽象窗口工具集
* 包含了很多的类和接口
* 元素包括：窗口、按钮、文本框

![](index_files/cf672ede-319f-4b3a-a093-976dba8194f7.png)

#### 容器

容器（`container`）是 `Component` 的子类，因此容器对象本身也是一个组件，具有组件的所有性质，可以调用 `Component` 类的所有方法。`Component` 类的常用方法如下：

* `setLocation(int x, int y)` ：设置组件的位置
* `setSize(int width, int height)` ：设置组件的大小
* `setBounds(int x, int y, int width, int height)` ：同时设置组件的大小和位置
* `setVisible(Boolean visible)` ：设置组件的可见性
* `Component add(Component, comp)` ：向容器中添加其它组件（该组件可以是普通组件，也可以是容器）
* `Component getComponentAt(int x, int y)` ：返回指定点的组件
* `int getComponentCount()` ：返回该容器内组件的数量
* `Component[] getComponents()` ：返回该容器内所有的组件

**分类**

* `Window` ：可独立存在的顶级窗口
* `Panel` ：可作为容纳其它组件，但不能独立存在，必须被添加到其它容器中（如 `Window`、`Panel` 或 `Applet` 等）

##### Frame

是 `Window` 的子类，有以下的特点：

* `Frame` 对象有标题，允许通过拖拉来改变窗口的位置、大小
* 初始化时为不可见，可用 `setVisible(true)` 使其显示出来
* 默认使用 `BorderLayout` 作为其布局管理器

```java
public static void main(String[] args) {
    Frame frame = new Frame("第一个 Frame");
    frame.setVisible(true);
    frame.setSize(300, 300);
    frame.setBackground(Color.LIGHT_GRAY);
    frame.setLocation(300, 300);
    frame.setResizable(false);
}
```

**问题**

上面代码可以生成一个窗口，但是点击关闭按钮没有任何作用，只能通过停止程序运行关闭窗口

##### Panel

`Penal` 存在的意义在于为其它组件提供空间，有以下的特点：

* 可作为容器来盛装其它组件，为放置组件提供空间
* 不能单独存在，必须放置到其它容器中
* 默认使用 `FlowLayout` 作为其布局管理器

```java
public static void main(String[] args) {
    Frame frame = new Frame("我的第一个窗口");

    frame.setLayout(null);
    frame.setBounds(100, 100, 300, 300);
    frame.setBackground(Color.lightGray);

    Panel panel = new Panel();

    panel.setBounds(50, 50, 100, 100);
    panel.setBackground(new Color(182, 13, 23));

    frame.add(panel);
    frame.setVisible(true);

    frame.addWindowListener(new WindowAdapter() {

        @Override
        public void windowClosing(WindowEvent e) {
            System.exit(0);
        }
    });
}
```

> 上面的代码给关闭按钮添加了监听事件，所以解决了上节遗留的问题

##### ScrollPane

`ScrollPane` 是一个带滚动条的容器，也不能独立存在，必须被添加到其它容器中，有以下的特点：

* 可作为容器来盛装其它组件，当组件占用空间过大时，`ScrollPane` 自动产生滚动条，当然也可以通过指定的构造器参数来指定默认具有滚动条
* 不能单独存在，必须放置到其它容器中
* 默认使用 `BorderLayout` 作为其布局管理器。`ScrollPane` 通常用于盛装其它容器，所以通常不允许改变 `ScrollPane` 的布局管理器

```java
public static void main(String[] args) {
    Frame frame = new Frame("ScrollPane 容器练习");

    ScrollPane scrollPane = new ScrollPane(ScrollPane.SCROLLBARS_ALWAYS);

    TextField comp = new TextField(30);
    comp.setBackground(Color.blue);
    scrollPane.add(new Label("下面是一个输入框"), BorderLayout.EAST);
    scrollPane.add(comp, BorderLayout.SOUTH);

    frame.add(scrollPane);

    frame.pack();
    frame.setVisible(true);
}
```

#### 布局管理器

所有的 `AWT` 容器都有默认的布局管理器，如果没有为容器指定布局管理器，则该容器使用默认的布局管理器。为容器指定布局管理器的方法：

`c.setLayout(new XxxLayout());`

##### FlowLayout

在 `FlowLayout` 布局管理器中，组件像水流一样向某方向流动（排列），遇到障碍（边界）就折回，重头开始排列。默认情况下，`FlowLayout` 从左到右今次排列所有组件，遇到边界就会折回下一行重新开始。

```java
public static void main(String[] args) {
    Frame frame = new Frame("FlowLayout 容器练习");

    frame.setLayout(new FlowLayout());
    frame.setBounds(100, 100, 200, 300);

    for (int i = 0; i < 10; i++) {
        frame.add(new Button("按钮" + i));
    }

    frame.pack();
    frame.setVisible(true);
}
```

##### BorderLayout

`BorderLayout` 将容器分为 `EAST、WEST、NORTH、SOUTH、CENTER` 五个区域，普通组件可以被放置在这 `5` 个区域中的任意一个中，注意点如下：

* 当改变使用 `BorderLayout` 的容器大小时，`NORTH、SOUTH、CENTER` 区域水平调整，而 `EAST、WEST、CENTER` 区域垂直调整
* 当向使用 `BorderLayout` 布局管理器的容器中添加组件时，需要指定要添加到哪个区域中，如果没有指定添加到哪个区域中，则默认添加到中间区域中
* 如果向同一个区域添加多个组件时，后放入的组件会覆盖先放入的组件

```java
public static void main(String[] args) {
    Frame frame = new Frame("BorderLayout 容器练习");

    frame.setLayout(new BorderLayout());
    frame.setBounds(100, 100, 100, 200);

    frame.add(new Button("North"), BorderLayout.NORTH);
    frame.add(new Button("South"), BorderLayout.SOUTH);
    // 不指定区域，默认添加到中间区域
    frame.add(new Button("Center"));
    frame.add(new Button("West"), BorderLayout.WEST);
    frame.add(new Button("East"), BorderLayout.EAST);

    frame.pack();
    frame.setVisible(true);
}
```

##### GridLayout

`GridLayout` 布局管理器将容器分割成纵横线分隔的风格，每个网格所占的区域大小相同。当向使用 `GridLayout` 布局管理器的容器中添加组件时，默认从左向右、从上到下依次添加到每个网格中。与 `FlowLayout` 不同的是，放置在 `GridLayout` 布局管理器中的各组件的大小由组件所处的区域来决定（**每个组件将自动占满整个区域**）

```java
public static void main(String[] args) {
    Frame frame = new Frame("GridLayout 容器练习");

    frame.setBounds(200, 200, 200, 300);
    frame.add(new TextField(30), BorderLayout.NORTH);

    Panel panel = new Panel();
    panel.setLayout(new GridLayout(3, 5, 5, 5));
    String[] bs = {"1", "2", "3", "4", "5", "6", "7", "8", "9", "0", "+", "-", "*", "/", "="};
    for (int i = 0; i < bs.length; i++) {
        panel.add(new Button(bs[i]));
    }
    frame.add(panel);

    frame.pack();
    frame.setVisible(true);
}
```

##### GridBagLayout

`GridBagLayout` 布局管理器中，一个组件可以跨越 1 个或多个网格，并可以设置各网格的大小互不相同，从而增加了布局的灵活性，当窗口的大小发生变化时，`GridBagLayout` 布局管理器也可以准确地控制窗口各部分的拉伸。

使用步骤如下：

1. 创建 `GridBagLayout` 布局管理器，并指定 `GUI` 容器使用该布局管理器
  
   ```java
   GridBagLayout gbl = new GridBagLayout();
   container.setLayout(gbl);
   ```
2. 创建 `GridBagConstraints`，并设置该对象的关联属性（用于设置受该对象控制的 `GUI` 组件的大小、跨越性等
  
   ```java
   GridBagConstraints gbc = new GridBagConstraints();
   gbc.gridx = 2; // 组件位于网格的横向索引
   gbc.gridy = 1; // 组件位于网格的纵向索引
   gbc.gridwidth = 2; // 组件横向跨越多少网格
   gbc.gridheight = 1; // 组件纵向跨越多少网格
   ```
3. 调用 `GridBagConstraints` 对象的方法来建立 `GridBagConstraints` 对象和受控组件之间的关联
  
   ```java
   gbc.setConstraints(c, gbc);
   ```
4. 添加组件
  
   ```java
   container.add(c);
   ```

> `GridBagConstraints` 对象应该被重用，只需要不断改变它的属性就可以了

```java
public class WindowAndPanel {
    private static Frame frame;
    private static GridBagLayout gbl;
    private static GridBagConstraints gbc;

    public static void main(String[] args) {
        frame = new Frame("GridLayout 容器练习");

        gbl = new GridBagLayout();
        frame.setLayout(gbl);
        frame.setBounds(200, 200, 300, 300);
        Button[] bs = new Button[10];

        for (int i = 0; i < bs.length; i++) {
            bs[i] = new Button("按钮" + i);
        }

        gbc = new GridBagConstraints();

        // 所有组件都可以在横向、纵向上扩大
        gbc.fill = GridBagConstraints.BOTH;
        gbc.weightx = 1;
        addButton(bs[0]);
        addButton(bs[1]);
        addButton(bs[2]);
        // 将会成为横向最后一个组件
        gbc.gridwidth = GridBagConstraints.REMAINDER;
        addButton(bs[3]);
        // 将在横向上不会扩大
        gbc.weightx = 0;
        addButton(bs[4]);
        // 将横跨两个网格
        gbc.gridwidth = 2;
        addButton(bs[5]);
        // 将横跨一个网格
        gbc.gridwidth = 1;
        // 纵向将横跨两个网格
        gbc.gridheight = 2;
        // 将成为横向最后一个组件
        gbc.gridwidth = GridBagConstraints.REMAINDER;
        addButton(bs[6]);
        // 横向跨越一个网格，纵向跨越两个网格
        gbc.gridwidth = 1;
        gbc.gridheight = 2;
        // 纵向扩大的权重是 1
        gbc.weighty = 1;
        addButton(bs[7]);
        // 纵向不会扩大
        gbc.weighty = 0;
        // 成为横向最后一个
        gbc.gridwidth = GridBagConstraints.REMAINDER;
        // 纵向上横跨一个网格
        gbc.gridheight = 1;
        addButton(bs[8]);
        addButton(bs[9]);

        frame.pack();
        frame.setVisible(true);
    }

    private static void addButton(Button b) {
        gbl.setConstraints(b, gbc);
        frame.add(b);
    }
}
```

##### CardLayout

`CardLayout` 布局管理器以时间而非空间来管理它里面的组件，它将加入容器的所有组件看成一叠卡片，每次只有最上面的那个 `Component` 才可见。常用方法：

* `first(Container tgarget)` ：显示 `target` 容器中的第一张卡片
* `last(Container tgarget)`：显示`target` 容器中的最后一张卡片
* `previous(Container tgarget)`：显示`target` 容器中的前一张卡片
* `next(Container tgarget)`：显示`target` 容器中的后一张卡片
* `show(Container target, String name)` ：显示 `target` 容器中指定名字的卡片

```java
public class WindowAndPanel {
    private Frame frame = new Frame("CardLayout 测试");
    private String[] names = {"第一张", "第二张", "第三张", "第四张", "第五张"};
    private Panel panel = new Panel();

    public void init() {
        CardLayout cardLayout = new CardLayout();
        panel.setLayout(cardLayout);

        for (int i = 0; i < names.length; i++) {
            panel.add(names[i], new Button(names[i]));
        }
        Panel p = new Panel();
        ActionListener listener = e -> {
            switch (e.getActionCommand()) {
                case "上一张":
                    cardLayout.previous(panel);
                    break;
                case "下一张":
                    cardLayout.next(panel);
                    break;
                case "最后一张":
                    cardLayout.last(panel);
                    break;
                case "第三张":
                    cardLayout.show(panel, "第三张");
                    break;
            }
        };
        // 控制显示上一张的按钮
        Button previous = new Button("上一张");
        previous.addActionListener(listener);
        Button next = new Button("下一张");
        next.addActionListener(listener);
        Button last = new Button("最后一张");
        last.addActionListener(listener);
        Button third = new Button("第三张");
        third.addActionListener(listener);
        p.add(previous);
        p.add(next);
        p.add(last);
        p.add(third);
        frame.add(panel);
        frame.add(p, BorderLayout.SOUTH);
        frame.pack();
        frame.setVisible(true);
    }

    public static void main(String[] args) {
        new WindowAndPanel().init();
    }
}
```

##### 绝对定位

绝对定位的步骤：

1. 将 `container` 的布局管理器设置为 `null`
2. 向容器中添加组件时，先调用 `setBounds()` 或 `setSize()` 方法来设置组件的大小、位置，或者直接创建 `GUI` 组件时通过构造参数指定组件的大小和位置，然后将组件添加到容器中

```java
public class WindowAndPanel {
    private Frame frame = new Frame("绝对定位 测试");
    private Button btn1 = new Button("第一个按钮");
    private Button btn2 = new Button("第二个按钮");

    public void init() {
        // 设置 null 布局管理器
        frame.setLayout(null);
        // 下面强制设置每个按钮的大小和位置
        btn1.setBounds(20, 30 , 90, 28);
        frame.add(btn1);
        btn2.setBounds(50, 45, 120, 35);
        frame.add(btn2);
        frame.setBounds(50, 50, 200, 100);
        frame.setVisible(true);
    }

    public static void main(String[] args) {
        new WindowAndPanel().init();
    }
}
```

##### BoxLayout

`GridBagLayout` 布局管理器虽然功能强大，但它实在太复杂了，所以 `Swing` 引入了一个新的布局管理器：`BoxLayout`，它可以在垂直和水平两个方向上摆放 `GUI` 组件

```java
public class WindowAndPanel {
    private Frame frame = new Frame("BoxLayout 测试一");

    public void init() {
        frame.setLayout(new BoxLayout(frame, BoxLayout.Y_AXIS));
        frame.add(new Button("第一个按钮"));
        frame.add(new Button("第二个按钮"));
        frame.pack();
        frame.setVisible(true);
    }

    public static void main(String[] args) {
        new WindowAndPanel().init();
    }
}
```

`BoxLayout` 通常和 `Box` 容器结合使用，`Box` 是一个特殊的容器，它有点像 `Panel` 容器，但该容器默认使用 `BoxLayout` 布局管理器，`Box` 提供了两个静态方法来创建`Box` 对象：

* `createHorizontalBox()` ：创建一个水平排列组件的 `Box` 容器
* `createVerticalBox()` ：创建一个垂直排列的 `Box` 容器

```java
public class WindowAndPanel {
    private Frame frame = new Frame("BoxLayout 测试一");

    public void init() {
        Box horizontalBox = Box.createHorizontalBox();
        horizontalBox.add(new Button("水平按钮一"));
        horizontalBox.add(new Button("水平按钮二"));
        Box verticalBox = Box.createVerticalBox();
        verticalBox.add(new Button("垂直按钮一"));
        verticalBox.add(new Button("垂直按钮二"));
        frame.add(horizontalBox, BorderLayout.NORTH);
        frame.add(verticalBox);

        frame.pack();
        frame.setVisible(true);
    }

    public static void main(String[] args) {
        new WindowAndPanel().init();
    }
}
```

`Box` 提供了五个静态方法来创建 `Glue`、`Strut` 和 `RigidArea`，用来控制组件在水平和垂直方向上的间距：

* `createHorizontalGlue()` ：创建一个水平 `Glue`（可在两个方向同时拉伸的间距）
* `createVerticalGlue()` ：创建一个垂直 `Glue`（可在两个方向同时拉伸的间距）
* `createHorizontalStut(int width)` ：创建一条指定宽度的 `Strut`（可在垂直方向拉伸的间距）
* `createVerticalStrut(int height)` ：创建一条指定高度的垂直 `Strut`（可在水平方向拉伸的间距）
* `createRightArea(Dimension d)` ：创建指定宽度、高度的 `RigidArea`（不可拉伸的间距）

```java
public class WindowAndPanel {
    private Frame frame = new Frame("BoxLayout 测试一");

    public void init() {
        Box horizontalBox = Box.createHorizontalBox();
        Box verticalBox = Box.createVerticalBox();

        horizontalBox.add(new Button("水平按钮一"));
        horizontalBox.add(Box.createHorizontalGlue());
        horizontalBox.add(new Button("水平按钮二"));
        // 水平方向不可拉伸距离，其宽度为 10
        horizontalBox.add(Box.createHorizontalStrut(10));
        horizontalBox.add(new Button("水平按钮三"));

        verticalBox.add(new Button("垂直按钮一"));
        verticalBox.add(Box.createVerticalGlue());
        verticalBox.add(new Button("垂直按钮二"));
        // 垂直方向不可拉伸的距离，其高度为 10
        verticalBox.add(Box.createVerticalStrut(10));
        verticalBox.add(new Button("垂直按钮三"));

        frame.add(horizontalBox, BorderLayout.NORTH);
        frame.add(verticalBox);

        frame.pack();
        frame.setVisible(true);
    }

    public static void main(String[] args) {
        new WindowAndPanel().init();
    }
}
```

#### AWT 常用组件

`AWT` 组件需要调用运行平台的图形界面来创建和平台一致的对等体，因此 `AWT` 平台只能使用所有平台都支撑的公共组件，所以 `AWT` 只提供了一些常用的 `GUI` 组件

##### 基本组件

* `Button` ：按钮，可接受单击操作
* `Canvas` ：用于绘图的画布
* `Checkbox` ：复选框组件（也可以变成单选框组件）
* `CheckboxGroup` ：用于将多个  `Checkbox` 组件合成一组，一组 `Checkbox` 组件将只有一个可以被选中，即全部变成单选框组件
* `Choice` ：下拉式选择框组件
* `Frame` ：窗口，在 `GUI` 程序里通过该类创建窗口
* `Label` ：标签类，用于放置提示性文本
* `List` ：列表框组件，可以添加多项条目
* `Panel` ：不能单独存在的基本容器类，必须放到其它容器中
* `ScrollBar` ：滑动条组件，如果需要用户输入位于某个范围的值，就可以使用滑动条组件，比如调色板中设置 `RGB` 三个值所用的滑动条。当创建一个滑动条时，必须指定它的方向、初始值、滑块的大小、最小值和最大值
* `ScrollPane` ：带水平及垂直滚动条的容器组件
* `TextArea` ：多行文本域
* `TextField` ：单行文本域

##### 对话框（Dialog）

`Dialog` 是 `Window` 的子类，是一个容器类，属于特殊组件。对话框是可以独立存在的顶级窗口，因此用法与普通窗口的用法几乎完全一样，但需要注意两点：

* 对话框通常依赖于其它窗口，就是通常有一个 `parent` 窗口
* 对话框有非模式（`non-modal`）和模式（`nodal`）两种，当某个模式对话框被打开后，该模式对话框总是位于它依赖的窗口之上。在模式对话框被关闭之前，它依赖的窗口无法获得焦点

对话框有多个重载的构造器，可能会有如下三个参数：

* `owner` ：指定该对话框所依赖的窗口，既可以是窗口，也可以是对话框
* `title` ：指定该对话框的窗口标题
* `modal` ：指定该对话框是否模式的，`true` 或 `false`

```java
public class WindowAndPanel {
    private Frame frame = new Frame("Dialog 测试");

    public void init() {
        Dialog dialog1 = new Dialog(frame, "模式对话框", true);
        Dialog dialog2 = new Dialog(frame, "非模式对话框", false);

        Button button1 = new Button("打开模式对话框");
        Button button2 = new Button("打开非模式对话框");

        dialog1.setBounds(20, 30 , 300, 400);
        dialog2.setBounds(20, 30 , 300, 400);

        button1.addActionListener(e -> dialog1.setVisible(true));
        button2.addActionListener(e -> dialog2.setVisible(true));

        frame.add(button1);
        frame.add(button2, BorderLayout.SOUTH);

        frame.pack();
        frame.setVisible(true);
    }

    public static void main(String[] args) {
        new WindowAndPanel().init();
    }
}
```

`FileDialog` 是 `Dialog` 的子类，它代表一个对话框文件，用于打开或保存文件，它的构造器可支持：`parent`、`title` 和 `model` 三个参数，其中 `parent`、`title` 指定文件对话框的所属父窗口和标题，而 `mode` 用于指定该窗口用于打开文件或保存文件，该参数支持两个参数值：`FileDialog.LOAD`、`FileDialog.SAVE`。

`FileDialog` 提供了如下两个方法来获取被打开/保存文件的路径：

* `getDirectory()` ：获取被打开/保存文件的绝对路径
* `getFile()` ：获取被打开/保存文件的文件名

```java
public class WindowAndPanel {
    private Frame frame = new Frame("FileDialog 测试");

    public void init() {
        FileDialog openDialog = new FileDialog(frame, "打开文件", FileDialog.LOAD);
        FileDialog saveDialog = new FileDialog(frame, "保存文件", FileDialog.SAVE);

        Button openButton = new Button("打开文件");
        Button saveButton = new Button("保存文件");

        openButton.addActionListener(e -> {
            openDialog.setVisible(true);
            System.out.println(openDialog.getDirectory() + openDialog.getFile());
        });

        saveButton.addActionListener(e -> {
            saveDialog.setVisible(true);
            System.out.println(saveDialog.getDirectory() + saveDialog.getFile());
        });

        frame.add(openButton);
        frame.add(saveButton, BorderLayout.SOUTH);

        frame.pack();
        frame.setVisible(true);
    }

    public static void main(String[] args) {
        new WindowAndPanel().init();
    }
}
```

#### 事件处理

##### Java 事件模型的流程

在事件处理过程中，主要涉及三类对象：

* `Event Source（事件源）` ：事件发生的场所，通常就是各个组件，例如按钮、窗口、菜单等
* `Event（事件）` ：事件封装了 `GUI` 组件上发生的特定事件（通常就是一次用户操作）。如果程序需要获得 `GUI` 组件上所发生事件的相关信息，都通过 `Event` 对象来获取
* `Event Listener（事件监听器）` ：负责监听事件源所发生的事件，并对各种事件做出监听处理

![](index_files/1a41257c-2b28-40e8-bec1-129c905f74f7.png)

实现 `AWT` 事件处理机制的步骤如下：

1. 实现事件监听类，该监听类是一个特殊的 `Java` 类，必须实现一个 `XxxListener` 接口
2. 创建普通组件（事件源），创建事件监听器对象
3. 调用 `addXxxListener()` 方法将事件监听器对象注册给普通组件（事件源）。当事件源上发生指定事件时，`AWT` 会触发事件监听器，由事件监听器调用相应的方法（事件处理器）来处理事件，事件源上所发生的事件会作为参数传入事件处理器

##### AWT 事件分类

* 低级事件
  
  指基于特定动作的事件。比如进入、点击、拖放等动作的鼠标事件，当组件得到焦点、失去焦点触发焦点事件
  
  * `ComponentEvent` ：组件事件，当组件尺寸发生变化、位置发生移动、显示/隐藏状态发生改变时触发该事件
  * `ContainerEvent` ：容器事件，当容器里发生添加组件、删除组件时触发该事件
  * `WindowEvent` ：窗口事件，当窗口状态发生改变（如打开、关闭、最大化、最小化）时触发该事件
  * `FocusEvent` ：焦点事件，当组件得到焦点或失去焦点时触发该事件
  * `KeyEvent` ：键盘事件，当按键被按下、松开、单击时触发该事件
  * `MouseEvent` ：鼠标事件，当进行按下、松开、单击、移动鼠标等动作时触发该事件
  * `PaintEvent` ：组件绘制事件，该事件是一个特殊的事件类型，当 `GUI` 组件调用 `update/paint` 方法来呈现自身时触发该事件，该事件并非专用于事件处理模型
* 高级事件
  
  基于语义的事件，它可以不和特定的动作相关联，而依赖于触发此事件的类。比如，在 `TextField` 中按 `Enter` 键会触发 `ActionEvent` 事件，在滑动条上移动滑块会触发 `AdjustmentEvent` 事件，选中项目列表的某一项就会触发 `ItemEvent` 事件
  
  * `ActionEvent` ：动作事件，当按钮、菜单被单击，在 `TextField` 中按 `Enter` 键时触发该事件
  * `AdjustmentEvent` ：调节事件，在滑动条上移动滑块以调节数值时触发该事件
  * `ItemEvent` ：选项事件，当用户选中某项，或取消选中某项时触发该事件
  * `TextEvent` ：文本事件，当文本框、文本域里的文本发生改变时触发该事件

![](index_files/18736909-528c-4e20-9fae-2a03e0a69a87.png)

| 事件              | 监听器接口           | 处理器及触发时间                                             |
| ----------------- | -------------------- | ------------------------------------------------------------ |
| `ActionEvent`     | `ActionListener`     | `actionPerformed`：按钮、文本框、菜单被单击时触发            |
| `AdjustmentEvent` | `AdjustmentListener` | `adjustmentValueChanged`：滑块位置发生变化时触发             |
| `ContainerEvent`  | `ContainerListener`  | `componentAdded`：向容器中添加组件时触发；`componentRemoved`：从容器中删除组件时触发<br/> |
| 未完待续……        |                      |                                                              |

```java
public class WindowAndPanel {
    private Frame frame = new Frame("事件监听 测试");
    private TextArea textArea = new TextArea(6, 40);
    private Button bu1 = new Button("按钮一");
    private Button bu2 = new Button("按钮二");

    public void init() {
        FirstListener firstListener = new FirstListener();
        bu1.addActionListener(firstListener);
        bu1.addActionListener(new SecondListener());

        bu2.addActionListener(firstListener);

        frame.add(textArea);
        Panel panel = new Panel();
        panel.add(bu1);
        panel.add(bu2);
        frame.add(panel, BorderLayout.SOUTH);
        frame.pack();
        frame.setVisible(true);
    }

    class FirstListener implements ActionListener {

        @Override
        public void actionPerformed(ActionEvent e) {
            textArea.append("第一个事件监听器被触发，事件源是：" + e.getActionCommand() + "\n");
        }
    }

    class SecondListener implements ActionListener {

        @Override
        public void actionPerformed(ActionEvent e) {
            textArea.append("单击了：" + e.getActionCommand() + "按钮\n");
        }
    }

    public static void main(String[] args) {
        new WindowAndPanel().init();
    }
}
```

#### AWT 菜单

`AWT` 中的菜单由如下几个类组成：

* `MenuBar` ：菜单条，菜单的容器
* `Menu` ：菜单组件，菜单项的容器，它也是 `MenuItem` 的子类，所以可作为菜单项使用
* `PopupMenu` ：上下文菜单组件（右键菜单组件）
* `MenuItem` ：菜单项组件
* `CheckboxMenuItem` ：复选框菜单项组件
* `MenuShortcut` ：菜单快捷键组件

![](index_files/80827469-a709-4c3f-9818-135d801bd7fd.png)

从图中可以看出，`MenuBar` 和 `Menu` 都实现了菜单容器接口，所以 `MenuBar` 可以盛装 `Menu`，而 `Menu` 可以盛装 `MenuItem`（包括 `Menu` 和 `CheckboxMenuItem` 两个子类对象）。`Menu` 还有一个子类：`PopupMenu`，代表上下文菜单，上下文菜单无须使用 `MenuBar` 盛装。

## 第二十一章 Swing

### 创建窗口

`JFrame` 代表一个窗口，通过 `JFrame` 相关的 `API` 就可以创建窗口：

```java
JFrame frame = new JFrame("这是窗口的标题内容");
```

### 监听器

监听器 `Listener` 是 `Swing` 里界面事件处理的一种方式，使用步骤如下：

1. 创建监听器对象 `Listener`
2. 将监听器对象交给要监听的组件
3. 当按钮被点击时，`Swing` 框架会自动调用监听器对象里的方法，进行处理

```java
public class ShowCurTime {

    private static Label label;
    private static Button button;

    public static void createGUI() {
        MyFrame frame = new MyFrame("显示当前时间", 400, 300);

        Container contentPane = frame.getContentPane();
        contentPane.setLayout(new FlowLayout());

        button = new Button("显示时间");
        contentPane.add(button);
        label = new Label("00:00:00");
        contentPane.add(label);

        // 当按钮被点击时，Swing 框架会调用监听器的 actionPerformed() 方法
        button.addActionListener(e -> showTime());
    }

    public static void showTime() {
        SimpleDateFormat sdf = new SimpleDateFormat("HH:mm:ss");
        label.setText(sdf.format(new Date()));
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(ShowCurTime::createGUI);
    }
}
```

### 回调

回调，`Callback()`，一个设计上的术语。

* 当我们调用系统的一个方法时，叫 `Call`（调用）
* 当我们写的一个方法被系统调用时，叫 `Callback`（回调）

> Java 中，使用 interface 语法实现回调

### 控件

#### JLabel

用于显示短文本，或者图标

* `setText()` ：设置文本
* `setFont()` ：设置字体
* `setForeground()` ：设置文本颜色
* `setToolTipText()` ：设置工具提示

#### JTextField

用于显示单行文本

* `new JTextField(16)` ：`16` 表示列数，用于计算宽度（并不是字数限制）
* `setText()/getText()` ：设置文本/获取文本
* `setFont()` ：设置字体

```java
public class DemoJTextField {

    public static void createGUI() {
        MyFrame frame = new MyFrame("JTextField 演示", 500, 200);

        Container contentPane = frame.getContentPane();
        contentPane.setLayout(new FlowLayout());

        contentPane.add(new JLabel("请输入你的名字"));
        JTextField textField = new JTextField(16);
        contentPane.add(textField);
        JButton button = new JButton("确定");
        contentPane.add(button);

        button.addActionListener(new AbstractAction() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String text = textField.getText();
                JOptionPane.showMessageDialog(frame, "你输入的名字是：" + text);
            }
        });
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoJTextField::createGUI);
    }
}
```

#### JCheckBox

复选框

* `isSelected()/setSelected()` ：获取/设置选中状态
* `setText()` ：选项文字
* `addActionListener()` ：用户选中/取消时触发

```java
public class DemoJCheckBox {

    public static void createGUI() {
        MyFrame frame = new MyFrame("JCheckBox 练习", 400, 200);

        Container contentPane = frame.getContentPane();
        contentPane.setLayout(new FlowLayout());

        JCheckBox checkBox = new JCheckBox("我想订阅邮件通知");
        contentPane.add(checkBox);
        JTextField textField = new JTextField(16);
        contentPane.add(textField);

        checkBox.setSelected(true);

        checkBox.addActionListener(e -> textField.setEnabled(checkBox.isSelected()));
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoJCheckBox::createGUI);
    }
}
```

#### JComboBox

下拉列表

* `addItem(Object)` ：添加指定的对象成为列表项
* `Object getItemAt(int index)` ：获取第 `index` 个索引
* `Object getSelectedItem()` ：获得被选中的元素
* `int getItemCount()` ：获取列表项的数目

```java
public class DemoJComboBox {

    private static JComboBox<String> colors;
    private static JLabel label;

    public static void createGUI() {
        MyFrame frame = new MyFrame("JComboBox 练习", 400, 300);

        Container contentPane = frame.getContentPane();
        contentPane.setLayout(new FlowLayout());

        colors = new JComboBox<>();
        colors.addItem("红色");
        colors.addItem("绿色");
        colors.addItem("蓝色");

        colors.setSelectedIndex(2);

        colors.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                changeTextColor();
            }
        });

        contentPane.add(colors);
        label = new JLabel("文本样例 This is a sample");
        contentPane.add(label);

        changeTextColor();
    }

    private static void changeTextColor() {
        int index = colors.getSelectedIndex();
        if (index == 0)
            label.setForeground(Color.red);
        else if (index == 1)
            label.setForeground(Color.green);
        else if (index == 2)
            label.setForeground(Color.blue);
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoJComboBox::createGUI);
    }
}
```

#### 综合小练习——彩色标签

```java
public class ColorLabel {

    public static void createGUI() {
        MyFrame frame = new MyFrame("彩色标签实战", 400, 200);

        Container contentPane = frame.getContentPane();
        contentPane.setLayout(new FlowLayout());

        Color[] colors = {Color.yellow, Color.green, Color.gray, new Color(0, 116, 122)};

        // 下面是第一种方式，不完全面向对象
        /*for (int i = 0; i < colors.length; i++) {
            JLabel label = new JLabel((i + 1) + "");
            // 设置背影为不透明，JLabel 背影默认为透明的
            label.setOpaque(true);
            // 设置最佳尺寸
            label.setPreferredSize(new Dimension(60, 30));
            label.setBackground(colors[i]);
            label.setHorizontalAlignment(SwingConstants.CENTER);
            contentPane.add(label);
        }*/

        // 下面是第二种方式，面向对象
        for (int i = 0; i < colors.length; i++) {
            contentPane.add(new ColorLabel().new ColorfulLabel((i + 1) + "", colors[i]));
        }
    }

    private class ColorfulLabel extends JLabel {
        public ColorfulLabel(String text, Color color) {
            super(text);

            setOpaque(true);
            setPreferredSize(new Dimension(60, 30));
            setBackground(color);
            setHorizontalAlignment(SwingConstants.CENTER);
        }
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(ColorLabel::createGUI);
    }
}
```

### 卡片布局器练习

```java
public class DemoCardLayout {

    public static void createGUI() {
        MyFrame frame = new MyFrame("CardLayout 练习", 400, 200);

        Container contentPane = frame.getContentPane();
        contentPane.setLayout(new BorderLayout());

        JComboBox<String> comboBox = new JComboBox<>();
        comboBox.addItem("第一个卡片");
        comboBox.addItem("第二个卡片");
        contentPane.add(comboBox, BorderLayout.PAGE_START);

        JPanel panel = new JPanel();
        panel.setLayout(new CardLayout());
        contentPane.add(panel);

        JPanel panel1 = new JPanel();
        panel1.add(new ColorLabel().new ColorfulLabel("1", Color.yellow));
        panel1.add(new ColorLabel().new ColorfulLabel("2", Color.green));
        panel1.add(new ColorLabel().new ColorfulLabel("3", Color.red));

        JPanel panel2 = new JPanel();
        panel2.add(new JLabel("请输入你的信息："));
        panel2.add(new JTextField(16));

        panel.add(panel1, "first");
        panel.add(panel2, "second");

        comboBox.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                int index = comboBox.getSelectedIndex();
                CardLayout layout = (CardLayout) panel.getLayout();
                if (index == 0)
                    layout.show(panel, "first");
                else if (index == 1)
                    layout.show(panel, "second");
            }
        });
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoCardLayout::createGUI);
    }
}
```

### 窗口布局

* 把上层窗口称为容器（`Container`）
* 容器里可以有多个子窗口或子控件（`Component`）
* 所谓布局，就是决定每一个子控件显示在什么位置
* 在布局时，每个控件占据一个矩形区域（`Rectangle`）
  
  * `Rectangle` 参数：左上角坐标 `(x,y)`、宽度 `width`、高度 `height`

> 1. 取消布局器后（`setLayout(null)`），子控件默认是不显示的
> 2. `Frame` 的窗口大小，包括了标题栏的大小

```java
public class DemoDIYLayout {

    public static void createGUI() {
        MyFrame frame = new MyFrame("自定义布局器 练习", 500, 400);

        Container contentPane = frame.getContentPane();
        contentPane.setLayout(null);

        ColorLabel.ColorfulLabel label1 = new ColorLabel().new ColorfulLabel("彩色标签一", Color.yellow);
        ColorLabel.ColorfulLabel label2 = new ColorLabel().new ColorfulLabel("彩色标签二", Color.red);

        label1.setBounds(new Rectangle(0, 0, 200, 200));
        label2.setBounds(new Rectangle(150, 150, 100, 150));

        contentPane.add(label1);
        contentPane.add(label2);
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoDIYLayout::createGUI);
    }
}
```

### 布局管理器

负责对子控件的布局，当窗口变化的时候，动态调整子控件的位置和大小

#### 布局器运行机制

1. 给容器设置一个布局器：`root.setLayout(layoutMgr)`
2. 当容器大小改变时，自动调用布局器重新布局：`layoutMgr.layoutContainer(...)` （这是`Swing`自动调用的）

#### 手动布局

手工定义每个控件的位置，只需要重写 `LayoutManager` 类的 `layoutContainer` 这个方法即可

```java
public class DemoLayoutManager {

    private static ColorLabel.ColorfulLabel label1 = new ColorLabel().new ColorfulLabel("Hello World!", Color.yellow);
    private static ColorLabel.ColorfulLabel label2 = new ColorLabel().new ColorfulLabel("样例文本", new Color(202, 255, 112));

    public static void createGUI() {
        MyFrame frame = new MyFrame("布局管理器 练习", 300, 200);

        Container contentPane = frame.getContentPane();
        // 设置自定义的布局管理器
        contentPane.setLayout(new DemoLayoutManager().new MyLayout());

        contentPane.add(label1);
        contentPane.add(label2);
    }

    public class MyLayout extends LayoutManagerAdapter {
        @Override
        public void layoutContainer(Container parent) {
            super.layoutContainer(parent);

            int width = parent.getWidth();
            int height = parent.getHeight();

            if (label1.isVisible()) {
                int width1 = label1.getPreferredSize().width;
                int height1 = label1.getPreferredSize().height;

                label1.setBounds((width - width1) / 2, (height - height1) / 2, width1, height1);
            }

            if (label2.isVisible()) {
                int width2 = label2.getPreferredSize().width;
                int height2 = label2.getPreferredSize().height;

                label2.setBounds(width - width2, 0, width2, height2);
            }
        }
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoLayoutManager::createGUI);
    }
}
```

#### 线性布局器

包含 **水平布局** 和 **垂直布局** 两种

```java
// 该类中，使用了阿发提供的 AfXLayout 工具类
public class DemoLinearLayout {

    public static void createGUI() {
        MyFrame frame = new MyFrame("线性布局 练习", 300, 150);

        Container contentPane = frame.getContentPane();
        contentPane.setLayout(new AfXLayout(8));

        ColorLabel.ColorfulLabel label1 = new ColorLabel().new ColorfulLabel("Hello World!", Color.yellow);
        ColorLabel.ColorfulLabel label2 = new ColorLabel().new ColorfulLabel("样例文本", Color.green);
        ColorLabel.ColorfulLabel label3 = new ColorLabel().new ColorfulLabel("Good Boy", Color.cyan);
        ColorLabel.ColorfulLabel label4 = new ColorLabel().new ColorfulLabel("占满剩余", Color.red);

        contentPane.add(label1, "100px");
        contentPane.add(label2, "30%");
        contentPane.add(label3, "auto");
        contentPane.add(label4, "1w");
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoLinearLayout::createGUI);
    }
}
```

#### 任意布局

一种不规则的布局，比规则布局使用频率低

```java
// 该类中，使用了阿发提供的 AfAnyWhere 工具类
public class DemoAnywhereLayout {

    public static void createGUI() {
        MyFrame frame = new MyFrame("任意位置布局器 练习", 500, 300);

        Container contentPane = frame.getContentPane();
        contentPane.setLayout(new AfAnyWhere());

        ColorLabel.ColorfulLabel label1 = new ColorLabel().new ColorfulLabel("Hello World！", Color.yellow);
        contentPane.add(label1, AfMargin.TOP_LEFT);
        label1.setPreferredSize(new Dimension(90, 30));

        contentPane.add(new ColorLabel().new ColorfulLabel("样例文本", Color.green), AfMargin.TOP_RIGHT);

        ColorLabel.ColorfulLabel label = new ColorLabel().new ColorfulLabel("Good Boy", Color.red);
        contentPane.add(label, AfMargin.CENTER);
        label.setPreferredSize(new Dimension(260, 150));

        ColorLabel.ColorfulLabel label2 = new ColorLabel().new ColorfulLabel("占据剩余", Color.cyan);
        contentPane.add(label2, new AfMargin(-1, 15, 10, 15)); // -1 表示自动计算
        label2.setPreferredSize(new Dimension(0, 40));
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoAnywhereLayout::createGUI);
    }
}
```

#### 综合布局

这是一个综合布局练习，请享用

```java
// 该类使用了阿发提供的 AfXLayout 工具类
public class DemoComprehensiveLayout {

    public static void createGUI() {
        MyFrame frame = new MyFrame("综合布局 练习", 500, 300);

        Container contentPane = frame.getContentPane();

        JPanel panel1 = new JPanel();
        panel1.setLayout(new AfXLayout());
        JLabel label = new ColorLabel().new ColorfulLabel(">>>", Color.green);
        label.setBackground(Color.yellow);
        label.setHorizontalAlignment(SwingConstants.CENTER);
        panel1.add(label, "1w");
        JButton button = new JButton("发送");
        panel1.add(button, "80px");
        contentPane.add(panel1, BorderLayout.PAGE_START);

        contentPane.add(new ColorLabel().new ColorfulLabel("...", Color.green), BorderLayout.CENTER);
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoComprehensiveLayout::createGUI);
    }
}
```

### Border

每个 `JComponent` 都可以有一个或多个边框。边界是非常有用的对象，虽然它们本身不是组件，但知道如何绘制 `Swing` 组件的边缘。边框不仅用于绘制线条和漂亮的边缘，还用于提供标题和组件周围的空白。

> 尽管从技术上讲，可以在继承自 `JComponent` 的任何对象上设置边框，但许多标准 `Swing` 组件的外观实现与用户设置的边框不能很好地整合在一起工作。通常，当你想在除 `JPanel` 或 `JLabel` 之外的标准 `Swing` 组件上设置边框时，建议将组件放在 `JPanel` 中，并在 `JPanel` 上设置边框。

```java
public class DemoBorderEasy {

    public static void createGUI() {
        MyFrame frame = new MyFrame("简单边框 练习", 500, 400);

        Container contentPane = frame.getContentPane();
        contentPane.setLayout(new AfYLayout(3));

        ColorLabel.ColorfulLabel label1 = new ColorLabel().new ColorfulLabel("1", new Color(0xceeb5f));
        ColorLabel.ColorfulLabel label2 = new ColorLabel().new ColorfulLabel("2", new Color(0xefe149));
        LineBorder lineBorder = new LineBorder(Color.blue, 4, true);
        label2.setBorder(lineBorder);
        ColorLabel.ColorfulLabel label3 = new ColorLabel().new ColorfulLabel("3", new Color(0xb1e8a6));
        label3.setBorder(BorderFactory.createLineBorder(Color.blue, 4));
        ColorLabel.ColorfulLabel label4 = new ColorLabel().new ColorfulLabel("4", new Color(0xf0f0f0));
        label4.setBorder(BorderFactory.createTitledBorder("边框标题"));

        contentPane.add(label1, "25%");
        contentPane.add(label2, "25%");
        contentPane.add(label3, "25%");
        contentPane.add(label4, "25%");
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoBorderEasy::createGUI);
    }
}
```

根据边框的样式分类，大概可以分为 `4` 种：

* 简单边框：`Simple`
* 特种边框：`Matte`（上、下、左、右边框不一样的）
* 带标题边框：`Titled`
* 复合边框：`Compound`

```java
public class DemoBorderAllKinds {

    public static void createGUI() {
        MyFrame frame = new MyFrame("四各类型的边框 练习", 400, 300);

        JPanel panel = new JPanel();
        panel.setLayout(new AfYLayout(3));
        // 给窗口设置空边框（用于占位）
        panel.setBorder(BorderFactory.createEmptyBorder(10, 15, 15, 20));
        frame.setContentPane(panel);

        // 简单类型边框（Simple）
        ColorLabel.ColorfulLabel label1 = new ColorLabel().new ColorfulLabel("1", new Color(0xfcfcfc));
        label1.setBorder(BorderFactory.createRaisedBevelBorder());

        // 特种边框（Matte）
        ColorLabel.ColorfulLabel label2 = new ColorLabel().new ColorfulLabel("2", new Color(0xfcfcfc));
        label2.setBorder(BorderFactory.createMatteBorder(1, 5, 1, 1, Color.red));

        // 带标题边框（Titled）
        ColorLabel.ColorfulLabel label3 = new ColorLabel().new ColorfulLabel("3", new Color(0xfcfcfc));
        TitledBorder title = BorderFactory.createTitledBorder(BorderFactory.createLineBorder(Color.black), "title");
        title.setTitleJustification(TitledBorder.RIGHT);
        label3.setBorder(title);

        // 复合边框（Compound）
        ColorLabel.ColorfulLabel label4 = new ColorLabel().new ColorfulLabel("4", new Color(0xfcfcfc));
        Border outer = BorderFactory.createLineBorder(Color.blue, 4);
        Border inner = BorderFactory.createLineBorder(Color.red, 4);
        CompoundBorder compound = BorderFactory.createCompoundBorder(outer, inner);
        label4.setBorder(compound);

        panel.add(label1, "25%");
        panel.add(label2, "25%");
        panel.add(label3, "25%");
        panel.add(label4, "25%");
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoBorderAllKinds::createGUI);
    }
}
```

#### 边距与填充

在 `Swing` 里，边距和填充也是由 `Border` 来实现的。

```java
// 所谓的 EmptyBorder，就可以用来实现空白填充效果
Border padding = BorderFactory.createEmptyBorder(8, 8, 8, 8);
```

> 具体代码实现见上一个示例代码

* `padding`：边框线与内容之间的边距
* `margin`：边框外的空白间距

```java
// 本类使用了阿发提供的 AfLayout、AfBorder 工具类
public class DemoMarginUtil {

    public static void createGUI() {

        MyFrame frame = new MyFrame("四各类型的边框 练习", 400, 300);

        JPanel panel = new JPanel();
        panel.setLayout(new AfYLayout(3));
        // 给窗口添加内边距
        // AfBorder.addPadding(panel, 8);
        AfBorder.addPadding(panel, 3, 6, 12, 24);
        frame.setContentPane(panel);

        ColorLabel.ColorfulLabel label1 = new ColorLabel().new ColorfulLabel("1", new Color(0xfcfcfc));
        ColorLabel.ColorfulLabel label2 = new ColorLabel().new ColorfulLabel("2", new Color(0xfcfcfc));
        ColorLabel.ColorfulLabel label3 = new ColorLabel().new ColorfulLabel("3", new Color(0xfcfcfc));
        ColorLabel.ColorfulLabel label4 = new ColorLabel().new ColorfulLabel("4", new Color(0xfcfcfc));

        panel.add(label1, "25%");
        panel.add(label2, "25%");
        panel.add(label3, "25%");
        panel.add(label4, "25%");
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoMarginUtil::createGUI);
    }
}
```

### 使用图标

* 接口：`Icon`
* 实现类：`ImageIcon`

默认情况下，`JLabel、JButton` 都可以显示图标，支持 `jpg/jepg/png` 格式的静态图片

```java
public class DemoIconLoad {

    public static void createGUI() throws Exception {
        MyFrame frame = new MyFrame("图片加载 练习", 300, 200);

        JPanel panel = new JPanel();
        JLabel label = new JLabel();
        frame.setContentPane(panel);

        Icon camera = new ImageIcon(DemoIconLoad.class.getResource("/images/camera.png"));
        label.setIcon(camera);
        label.setText("这是一个图标");
        panel.add(label);
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(() -> {
            try {
                createGUI();
            } catch (Exception e) {
                e.printStackTrace();
            }
        });
    }
}
```

#### 资源文件

随 `class` 文件一同打包的文件，称为资源文件

资源文件的加载：内部由 `ClassLoader` 负责加载，加载时，须指定资源文件的路径（包路径

```java
public class DemoImageIconShow {

    public static void createGUI() {
        MyFrame frame = new MyFrame("图标按钮 练习", 500, 400);

        JPanel panel = new JPanel();
        frame.setContentPane(panel);

        panel.setLayout(new BorderLayout());

        JButton button1 = createButton("/images/view.png");
        JButton button2 = createButton("/images/save.png");
        JButton button3 = createButton("/images/print.png");

        Box box = Box.createHorizontalBox();
        panel.add(box, BorderLayout.PAGE_START);

        box.add(button1);
        box.add(button2);
        box.add(button3);

        JTextArea content = new JTextArea();
        panel.add(content, BorderLayout.CENTER);
        content.setBorder(BorderFactory.createLineBorder(Color.lightGray));
    }

    public static JButton createButton(String path) {
        URL url;
        Icon icon = new ImageIcon(DemoImageIconShow.class.getResource(path));

        JButton button = new JButton();
        button.setIcon(icon);

        button.setContentAreaFilled(false);
        button.setFocusPainted(false);

        return button;
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoImageIconShow::createGUI);
    }
}
```

### 自定义控件

* 自己写个类，继承某个系统的类
* 重写 `paintComponent(Graphics g)` 方法，决定自定义控件的显示

```java
public class DemoDIYComponentRedSquare {

    public static void createGUI() {
        MyFrame frame = new MyFrame("自定义控件-红色方框 练习", 300, 300);

        frame.setLayout(new FlowLayout());

        frame.setContentPane(new DemoDIYComponentRedSquare().new MyPanel());
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoDIYComponentRedSquare::createGUI);
    }

    private class MyPanel extends JPanel {
        @Override
        protected void paintComponent(Graphics g) {
            int width = this.getWidth();
            int height = this.getHeight();

            g.clearRect(0, 0, width, height);

            g.setColor(Color.red);
            g.fillRect(0, 0, width, height);
        }
    }
}
```

#### 颜色

在 `Swing` 里，用 `Color` 类来代表颜色

```java
Color color = Color.red;
Color color = new Color(255, 0, 0);
Color color = new Color(0xFF0000);
```

#### 控件的绘制

在控件里可以绘制的内容：

* 几何图形
* 文本
* 图片

绘制几何图形时，使用 `Graphics` 和 `Graphics2D` 下的方法

* `Line` ：直线
* `Rect` ：矩形（含正方形）
* `Oval` ：椭圆（含圆）
* `Polygon` ：多边形（含三角形）
* `Arc` ：圆弧 / 扇形

几何图形的绘制方法分为两种

* `drawXXX()` ：表示只画线条
* `fillXXX()` ：表示只填充

**自定义绘制正弦曲线示例**

```java
public class DemoDIYSinLine {
    static MyClass contentPane = null;
    static JSpinner grainSpinner = new JSpinner(new SpinnerNumberModel(1, 1, 10, 1));
    static JSpinner rangeSpinner = new JSpinner(new SpinnerNumberModel(50, 20, 80, 5));
    static JSpinner periodSpinner = new JSpinner(new SpinnerNumberModel(100, 50, 150, 10));

    public static void createGUI() {

        MyFrame frame = new MyFrame("自定义绘制正弦曲线 练习", 500, 500);

        Container pane = frame.getContentPane();
        pane.setLayout(new BorderLayout());
        DemoDIYSinLine.contentPane = new DemoDIYSinLine().new MyClass();

        Box box = Box.createHorizontalBox();
        pane.add(box, BorderLayout.PAGE_START);
        box.add(new JLabel("粒度"));
        box.add(grainSpinner);
        box.add(new JLabel("高度"));
        box.add(rangeSpinner);
        box.add(new JLabel("周期"));
        box.add(periodSpinner);
        box.add(Box.createHorizontalGlue());

        grainSpinner.setValue(DemoDIYSinLine.contentPane.grain);
        rangeSpinner.setValue(DemoDIYSinLine.contentPane.range);
        periodSpinner.setValue(DemoDIYSinLine.contentPane.period);

        ChangeListener listener = new ChangeListener() {
            @Override
            public void stateChanged(ChangeEvent e) {
                changeUI(e);
            }
        };

        grainSpinner.addChangeListener(listener);
        rangeSpinner.addChangeListener(listener);
        periodSpinner.addChangeListener(listener);
        pane.add(box, BorderLayout.PAGE_START);
        pane.add(DemoDIYSinLine.contentPane, BorderLayout.CENTER);
    }

    public static void changeUI(ChangeEvent e) {
        contentPane.grain = (int) grainSpinner.getValue();
        contentPane.range = (int) rangeSpinner.getValue();
        contentPane.period = (int) periodSpinner.getValue();

        contentPane.repaint();
    }

    public static void main(String[] args) {
        javax.swing.SwingUtilities.invokeLater(DemoDIYSinLine::createGUI);
    }

    private class MyClass extends JPanel {

        int grain = 1; // 线条的精细度（粒度）
        int range = 50; // 高度（振幅半径）
        int period = 100; // x 轴，第 100 像素表示一个周期（2PI）

        @Override
        protected void paintComponent(Graphics g) {
            int width = getWidth();
            int height = getHeight();

            g.clearRect(0, 0, width, height);
            g.setColor(Color.white);
            g.fillRect(0, 0, width, height);

            int center = height / 2;
            g.setColor(Color.blue);
            g.drawLine(0, center, width, center);

            int x1 = 0, y1 = 0;
            for (int i = 0; i < width; i += grain) {
                // 每 100 像素表示 2PI
                int x2 = i;
                int y2 = (int) (range * Math.sin( 2 * Math.PI * i / period));
                g.drawLine(x1, center + y1, x2, center + y2);

                x1 = x2;
                y1 = y2;
            }
        }
    }
}
```

#### 绘制图片

位于 `java.awt.Image`，描述一个图像数据

`drawImage(Image img, int x, int y, int width, int height, ImageObserver observer)` ：用于绘制图片的方法，`x, y, width, height` 为目标区域，`observer` 为通知接收者

* 图片的准备
  
  * 支持 `jpg/jpeg/png` 格式
  * 可以是资源文件或本地文件
* 加载图片
  
  * 使用 `ImageIO` 类来加载图片，得到 `Image` 对象
    
    `ImageIO.read(URL/File)`

## 第二十二章 MySQL 数据库

### 现有的数据存储方式有哪些

* `Java` 程序存储数据（变量、对象、数组、集合），数据保存在内存中，属于瞬时状态存储
* 文件（`File`）存储数据，保存在硬盘上，属于持久状态存储

#### 以上存储方式的缺点

* 没有数据类型的区分
* 存储数据量级较小
* 没有访问安全限制
* 没有备份、恢复机制

### 数据库

数据库是按照数据结构来组织、存储和管理数据的仓库，是一个长期存储在计算机内的、有组织的、有共享的、统一管理的数据集合

#### 分类

* 网状结构数据库：美国通用电气公司 `IDS`（`Integrated Data Store`），以节点形式存储和访问
* 层次结构数据库：`IBM` 公司 `IMS`（`Information Management System`）定向有序的树状结构实现存储和访问
* 关系结构数据库：`Oracle、DB2、MySQL、SQL Server`，以表格存储，多表间建立关联关系，通过分类、合并、连接、选取等运算实现访问
* 非关系型数据库：`ElasterSearch、MongoDB、Redis`，多数使用哈希表，表中以键值对的方式实现特定的键和一个指针指向的特定数据

### 数据库管理系统

`DataBase Management System，DBMS`：指一种操作和管理数据库的大型软件，用于建立、使用和维护数据库，对数据库进行统一管理和控制，以保证数据库的安全性和完整性。用户通过数据库管理系统访问数据库中的数据

#### 常用的数据库管理系统

* `Oracle`：被认为是业界目前比较成功的关系型数据库管理系统。`Oracle` 数据库可以运行在 `Unix、Windows` 等主流操作系统平台，完全支持所有的工业标准，并获得最高级别的 `ISO` 标准安全性认证
* `DB2`：`IBM` 公司的产品，`DB2` 数据库系统采用多进程多线索体系结构，其功能足以满足大中公司的需要，并可灵活地服务于中小型电子商务解决方案
* `SQL Server`：`Microsoft` 公司推出的关系型数据库管理系统，具有使用方便可伸缩性好与相关软件集成程度高等优点
* `SQLite`：应用在手机端的数据库

### MySQL

#### 简介

`MySQL` 是一个 **关系型数据库管理系统**，由瑞典 `MySQL AB` 公司开发，属于 `Oracle` 旗下产品。`MySQL` 是最流行的关系型数据库管理系统之一，在 `Web` 应用方面，`MySQL` 是最好的 `RDBMS（Relational Database Management System）` 应用软件之一。

#### 访问与下载

[官网地址](https://www.mysql.com)

[下载地址](https://dev.mysql.com/downloads/mysql/)

 #### 配置环境变量

* `Windows`
  * 创建 `MYSQL_HOME: C:\Program Files\MySQL Server x.x`
  * 追加 `PATH: %MYSQL_HOME%\bin`
* `MacOS/Linux`
  * 终端中输入 `cd ~` 进入目录，并检查 `.bash_profile` 是否存在，有则追加，无则创建
  * 创建文件：`touch .bash_profile`
  * 打开文件：`open .bash_profile`
  * 输入：`export PATH=${PATH}/user/local/mysql/bin` 保存并退出终端

##### 验证

* 打开命令行工具
* 输入命令：`mysql -u 用户名 -p 密码`
* 如果控制台出现：`mysql>` 则表示成功

#### 目录结构

> 只介绍核心文件

| 文件夹名称 |        内容        |
| :--------: | :----------------: |
|    bin     |      命令文件      |
|    lib     |       库文件       |
|  include   |       头文件       |
|    hare    | 字符集、语言等信息 |

以上文件所在路径：`/usr/local/mysql-x.x.x-macosx.x-x86_64/`

#### 配置文件

所在路径：`/etc/my.cnf`

> 在配置文件中可以修改客户端和本地的字符集、服务端口等内容

| 参数                   | 描述                      |
| ---------------------- | ------------------------- |
| default-charset-set    | 客户端默认字符集          |
| character-set-server   | 服务端默认字符集          |
| port                   | 客户端和服务端的端口号    |
| default-storage-engine | MySQL 默认存储引擎 INNODB |

### SQL 语言

#### 概念

`SQL（Structed Query Language）`：结构化查询语言，用于存取数据、更新、查询和管理关系数据库系统的程序设计语言

> 通常对数据库执行的 “增删改查” 操作，简称：`C（Create）R（Read）U（Update）D（Delete）`

#### MySQL 上的应用

想对数据库操作，需要在命令行下进入 `MySQL` 环境进行指令的输入，并在一句指令的末尾使用 `;` 结尾

#### 基本命令

##### 查看 MySQL 中所有数据库

`mysql > show databases;`

| 数据库名称           | 描述                                                         |
| -------------------- | ------------------------------------------------------------ |
| `information_schema` | 信息数据库，其中保存着关于所有数据库的信息（元数据）<br />元数据是关于数据的数据，如数据库名或表名，列的数据类型，或访问权限等 |
| `mysql`              | 核心数据库，主要负责存储数据库的用户、权限设置、关键字等，以及需要使用的控制和管理信息，不可以删除 |
| `performance_schema` | 性能优化的数据库，`MySQL 5.5` 版本中新增的一个性能优化的引擎 |
| `sys`                | 系统数据库，`MySQL 5.7` 版本中新增的可以快速的了解元数据信息的系统库，便于发现数据库的多样信息，解决性能瓶颈问题 |

##### 创建数据库

```sql
mysql> create database mydb1; # 创建 mydb 数据库
mysql> create database mydb2 character set gbk; # 创建数据库并设置编码
mysql> create database if not exists mydb3; # 如果 mydb4 数据库不存在，就创建
```

##### 查看数据库创建信息

```sql
mysql> show create database mydb2; # 查看创建数据库时的基本
```

##### 修改数据库

```sql
mysql> alter database mydb2 character set gbk;
```

##### 删除数据库

```sql
mysql> drop database mydb2;
```

##### 查看当前所使用的数据库

```sql
mysql> select database();
```

##### 使用数据库

```sql
mysql> use mydb1;
```

### 客户端工具

#### Navicate

`Navicate` 是一套快速、可靠并价格便宜的数据库管理工具，专为简化数据库的管理及降低系统管理成本而设。它的设计符合数据库管理员、开发人员及中小企业的需要。`Navicate` 是以直觉化的图形用户界面而建的，让你可以以安全并简单的方式创建、组织、访问并共用信息。

#### SQLyog

`MySQL` 可能是世界上最流行的开源数据库引擎，但是使用基于文本的工具和配置文件可能很难进行管理。`SQLyog` 提供了完整的图形界面，即使初学者也可以轻松使用 `MySQL` 的强大功能，其拥有广泛的预定义工具和查询、友好的视觉界面、类似 `Excel` 的查询结果编辑界面等优点

### 数据查询（DQL）【重点】

#### 数据库表的基本结构

关系结构数据库是以表格进行数据存储，表格由 “行” 和 “列” 组成

> 执行查询语句返回的结果集是一张虚拟表

#### 基本查询

`select 列名 from 表名;`

| 关键字   | 描述           |
| -------- | -------------- |
| `select` | 指定要查询的列 |
| `from`   | 指定要查询的表 |

##### 查询部分列

```sql
# 查询员工表中所有员工的编号、姓名、邮箱
select employee_id, first_name, email
from t_employees;
```

##### 查询所有列

```sql
# 查询员工表中所有员工的所有信息
select 所有的列名 from t_employees;
select * from t_employees;
```

> 注意：生产环境下，优先使用列名查询。这是因为在执行时，* 的方式需要转换为全列名，效率低，可读性差

##### 对列中的数据进行运算

```sql
# 查询员工表中所有员工的编码、名字、年薪
select employee_id, first_name, salary * 12 
from t_employees;
```

| 算术运算符 | 描述           |
| ---------- | -------------- |
| +          | 两列做加法运算 |
| -          | 两列做减法运算 |
| *          | 两列做乘法运算 |
| /          | 两列做除法运算 |

> 注意：% 是点位符，而非模运算符

##### 列的别名

`列 as '别名'`

```sql
# 查询员工表中所有员工的编号、名字、年薪（列名均为中文）
select employee_id as '编号', first_name as '名字', salary * 12 as '年薪' 
from t_employees;
```

##### 查询结果去重

`distinct 列名`

```sql
# 查询员工表中所有经理的 ID
select distinct manager_id 
from t_employees;
```

#### 排序查询

语法：`select 列名 from 表名 order by 排序列[ 排序规则]`

| 排序规则 | 描述                   |
| -------- | ---------------------- |
| asc      | 对前面排序列做升序排序 |
| desc     | 对前面排序列做降序排序 |

##### 依据单列排序

```sql
# 查询员工的编号、名字、薪资。按照工资高低进行升序排序
select employee_id, first_name, salary 
from t_employees 
order by salary desc;
```

##### 依据多列排序

```sql
# 查询员工的编号、名字、薪资。按照工资高低进行升序排序（薪资相同时，按照编号进行升序排序）
select employee_id, first_name, salary
from t_employees
order by salary desc, employee_id asc;
```

#### 条件查询

语法：`select 列名 from 表名 where 条件`

| 关键字 | 描述                                                   |
| ------ | ------------------------------------------------------ |
| where  | 在查询结果中，筛选复合条件的查询结果，条件为布尔表达式 |

##### 等值判断（=）

```sql
# 查询薪资是 11000 的员工信息（编号、名字、薪资）
select employee_id, first_name, salary
from t_employees
where salary = 11000;
```

> 与 Java 中（==）不同的是，mysql 中使用 = 进行等值判断

##### 逻辑判断（or、and、not）

```sql
# 查询薪资薪资是 11000 并且提成是 0.30 的员工信息（编号、姓名、薪资）
select employee_id, first_name, salary
from t_employees
where salary = 11000 and commission_pct = 0.30;
```

##### 不等值判断（>、<、>=、<=、!=、<>）

```sql
# 查询员工的薪资在 6000~10000 之间的员工信息（编号、姓名、薪资）
select employee_id, first_name, salary
from t_employees
where salary >= 6000 and salary <= 10000;
```

##### 区间判断（between and）

```sql
# 查询员工的薪资在 6000~10000 之间的员工信息（编号、名字、薪资）
select employee_id, first_name, salary
from t_employees
where salary between 6000 and 10000; # 闭合区间，包含区间边界的两个值
```

> 注意：在敬意判断语法中，小值在前，大值在后，反之，得不到正确结果

##### NULL 值判断（is null、is not null）

`列名 is null`

`列名 is not null`

```sql
# 查询没有提成的员工信息（编号、名字、薪资、提成）
select employee_id, first_name, salary, commission_pct
from t_employees
where commission_pct is null;
```

##### 枚举查询（in（值1，值2，值3））

```sql
# 查询部门编号为70、80、90的员工信息（编号、名字、薪资、部门编号）
select employee_id, first_name, salary, department_id
from t_employees
where department_id in(70, 80, 90);
```

> 注意：in 的查询效率较低，可通过多条件拼接

##### 模糊查询

* 单个字符：`列名 like '张_' `
* 任意长度字符：`列名 like '张%'`

```sql
# 查询名字以 L 开头的员工信息（编号、名字、薪资、部门编号）
select employee_id, first_name, salary, department_id
from t_employees
where first_name like 'L%'

# 查询名字以 L 开头且长度为 4 的员工信息（编号、名字、薪资、部门编号）
select employee_id, first_name, salary, department_id
from t_employees
where first_name like 'L____'
```

> 注意：模糊查询只能和 like 关键字结合使用

##### 分支结构查询

```sql
case
	when 条件1 then 结果1
	when 条件2 then 结果2
	when 条件3 then 结果3
	else 结果
end
```

> 1. 类似于 java 中的 switch
> 2. 通过使用 case end 进行条件判断，每条数据对应生成一个值

```sql
# 查询员工信息（编号、名字、薪资、薪资级别<对应条件表达式生成>）
select employee_id, first_name, salary, 
	case
		when salary>=10000 then 'A'
		when salary>=8000 and salary<10000 then 'B'
		when salary>=6000 and salary<8000 then 'C'
		when salary>=4000 and salary<6000 then 'D'
		else 'E'
	end as 'level'
from t_employees;
```

#### 时间查询

语法：`select [时间函数([参数列表])]()`

> 执行时间函数查询，会自动生成一张虚表（一行一列）

| 时间函数                 | 描述                                   |
| ------------------------ | -------------------------------------- |
| `sysdate()`              | 当前系统时间（日、月、年、时、分、秒） |
| `curdate()`              | 获取当前日期                           |
| `curtime()`              | 获取当前时间                           |
| `week(date)`             | 获取当前日期为一年中的第几周           |
| `year(date)`             | 获取日期的年份                         |
| `hour(time)`             | 获取指定时间的小时值                   |
| `minute(time)`           | 获取时间的分钟数                       |
| `datediff(date1, date2)` | 获取 date1 和 date2 之间相隔的天数     |
| `adddate(date, n)`       | 计算 `date` 加上 `n` 天以后的日期      |

#### 字符串查询

语法：`select 字符串函数([参数列表])`

| 字符串函数                      | 说明                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| `concat(str1, str2, str...)`    | 将多个字符串连接                                             |
| `insert(str, pos, len, newstr)` | 将 `str` 中指定 `pos` 位置开始 `len` 长度的内容替换为 `newstr` |
| `lower(str)`                    | 将指定字符串转换为小写                                       |
| `upper(str)`                    | 将指定字符串转换为大写                                       |
| `substring(str, num, len)`      | 将 `str` 字符串指定 `num` 位置开始截取 `len` 个内容          |

##### 字符串应用

```sql
# 拼接内容
select concat('My', 'S', 'QL');
# 字符串替换，注意：字符串下标从零开始
select insert('这是一个数据库', 3, 2, 'MySQL'); 
# 指定内容转换为小写
select lower('MYSQL');
# 指定内容转换为大写
select upper('mysql');
```

#### 聚合函数

语法：`select 聚合函数(列名) from 表名;`

| 聚合函数  | 说明                     |
| --------- | ------------------------ |
| `sum()`   | 求所有行中单列结果的总和 |
| `avg()`   | 平均值                   |
| `max()`   | 最大值                   |
| `min()`   | 最小值                   |
| `count()` | 求总行数                 |

> 聚合函数
>
> 1. 对多条数据的单列进行统计，返回统计后的一行结果
> 2. 会自动忽略 null 值，不进行统计

#### 分组查询

语法：`select 列名 from 表名 where 条件 group by 分组依据（列）`

| 关键字   | 说明                            |
| -------- | ------------------------------- |
| group by | 分组依据，必须在 where 之后生效 |

##### 查询各部门人数的总和

```sql
# 思路
# 1. 按照部门编号进行分组（分组依据是 employee_id)
# 2. 再针对各部门的人数进行统计（count）
select department_id, count(employee_id)
from t_employees
group by department_id;
```

##### 查询各部门的总人数

```sql
# 思路
# 1. 按照部门编号进行分组（分组依据是 employee_id)
# 2. 再针对各部门进行平均工资统计（avg）
select department_id, count(salary)
from t_employees
group by department_id;
```

##### 查询各个部门、各个岗位的人数

```sql
# 思路
# 1. 按照部门编号进行分组（分组依据是 employee_id)
# 2. 按照岗位名称进行分组（分组依据是 job_id）
# 3. 针对每个部门中的各个岗位进行人数统计（count）
select department_id, job_id, count(employee_id)
from t_employees
group by department_id, job_id
```

##### 常见问题

```sql
# 查询各个部门 id、总人数、first_name
select department_id, count(*), first_name
from t_employees
group by department_id;
# 注意：执行上面这一句会出现 error
```

> 分组查询中，`select` 显示的列只能是分组依据列，或者聚合函数列，不能出现其它列

#### 分组过滤查询

语法：`select 列名 from 表名 where 条件 group by 分组列 having 过滤规则`

| 关键字          | 说明                               |
| --------------- | ---------------------------------- |
| having 过滤规则 | 过滤规则定义对分组后的数据进行过滤 |

##### 统计部门的最高工资

```sql
# 统计 60、70、90 号部门的最高工资
# 1. 确定分组依据（department_id）
# 2. 对分组后的数据，过滤出部门号是 60、70、90 的部门
# 3. 使用 max 函数
select department_id, max(salary)
from t_employees
group by department_id
having departmennt_id in (60, 70, 90);
```

#### 限定查询

语法：`select 列名 from 表名 limit 起始行，查询行数`

| 关键字                          | 说明                           |
| ------------------------------- | ------------------------------ |
| `limit offset_start, row_count` | 限定查询结果的起始行数和总行数 |

> 注意：起始行从 0 开始，代表了第 1 行，第 2 个参数代表的是从指定行开始查询几行

##### 查询前 5 行记录

```sql
select * from t_employees limit 0, 5;
```

##### 查询范围记录

```sql
# 表中从第 4 行开始，查询 10 行
select * from t_employees limit 3, 10;
```

##### limit 典型应用

分页查询：一页显示 10 条，一共查询 3 页

```sql
# 思路：第 1 页从 0 开始，显示 10 条
select * from limit 0, 10;

# 第 2 页是从 10 开始，显示 10 条
select * from limit 10, 10;

# 第 3 页是从 20 开始，显示 10 条
select * from limit 20, 10;
```

> 在分页应用场景中，起始行是变化的，但是一页显示的数据是不变的

#### 查询总结

##### sql 语句编写顺序

`select 列名 from 表名 where 条件 group by 分组 having 过滤条件 order by 排序列（asc|desc） limit 起始行，总行数；`

##### sql 语句执行顺序

```sql
1. from：指定数据来源表
2. where：对查询数据做第一次过滤
3. group by：分组
4. having：对分组后的数据第二次过滤
5. select：查询各字段的值
6. order by：排序
7. limit：限定查询结果
```

#### 子查询（作为条件判断）

`select 列名  from 表名 where 条件（子查询结果）`

##### 查询工资大于 Bruce 的员工

```sql
# 1. 先查询到 Bruce 的工资，一行一列
select salary from t_employees where first_name = 'Bruce'; # 查询结果是 6000

# 2. 查询工资大于 Bruce 的员工信息
select * from t_employees where salary > 6000;

# 3. 将 1、2 句整合为一句
select * from t_employees where salary > (select salary from t_employees where first_name = 'Bruce');
```

> 注意：将子查询 “一行一列” 的结果作为第二次查询的条件

#### 子查询（作为枚举查询条件）

`select 列名 from 表名 where 列名 in(子查询结果);`

##### 查询与名为 king 同一部门的员工信息

```sql
# 1. 先查询 King 所在的部门编号(多行单列)
select department_id
from t_employees
where first_name = 'King'; # 部门编号：80，90

# 2. 再查询 80、90 号部门的员工信息
select * from t_employees
where department_id in(80, 90);

# 3. 合并
select * from t_employees
where department_id in(
  select department_id
  from t_employees
  where first_name = 'King'
);
```

##### 工资高于 60 部门所有人的信息

```sql
# 1. 查询 60 部门所有人的工资（多行多列）
select salary from t_employees
where department_id = 60;

# 2. 查询高于 60 部门所有人的工资的员工信息（高于所有）
select * from t_employees
where salary > all(select salary from t_employees where depaprtment_id=60);

# 查询高于 60 部门所有人的工资的员工信息（高于部分）
select * from t_employees
where salary > any(select salary from t_employees where depaprtment_id=60);
```

> 注意：当子查询结果集形成为多行单列时可以使用 any 或 all 关键字

#### 子查询（作为一张表）

语法：`select 列名 from (子查询的结果集) where 条件;`

##### 查询员工表中工资排名前 5 名的员工信息

```sql
# 1. 先对所有员工的薪资进行排序（排序后形成临时表）
select employee_id, first_name, salary
from t_employees
order by salary desc;

# 2. 再查临时表中前 5 行的员工信息
select employee_id, first_name, salary
from 临时表
limit 0, 5;

# 3. 合并
select employee_id, first_name, salary
from 
(
  select employee_id, first_name, salary
  from t_employees
  order by salary desc
) as temp
limit 0, 5;
```

> 注意：
>
> 1. 将子查询 “多行多列” 的结果作为外部查询的第一张表，做第二次查询
> 2. 子查询作为临时表，为其赋予一个临时表名

#### 合并查询（了解）

```sql
select * from 表名1 union select * from 表名2;
select * from 表象1 union all select * from 表名2;
```

##### 合并两张表的结果（去除重复记录）

```sql
select * from t1 union select * fromm t2;
```

> 注意：
>
> 1. 合并结果的两张表，列数必须相同，列的数据类型可以不同
> 2. 使用 union 合并结果集，会去除掉两张表中的重复数据

##### 合并两张表的结果（保留重复记录）

```sql
select * from t1 union all select * fromm t2;
```

#### 表连接查询

语法：`select 列名 from 表1 连接方式 表2 on 连接条件`

##### 内链接查询

```sql
# 1. 查询所有有部门的员工信息（sql标准做法）
select * from t_employees inner_join t_jobs on t_employees.job_id = t_jobs.job_id;

# 2. 查询所有有部门的员工信息（mysql不标准做法）
select * from t_employees, t_jobs where t_employees.job_id = t_jobs.job_id;
```

> 1. 在 Mysql 中，第 2 种做法也可以作为内连接查询，但是不符合 sql 标准
> 2. 第一种属于 sql 标准，在其它关系型数据库中通用

##### 三表连接查询

```sql
# 查询所有员工号、名字、部门名称、部门所在国家 ID
select * from t_employees e
inner join t_employees d
on e.employee_id = d.employee_id
inner join t_location l
on d.location_id = t.location_id;
```

##### 左外连接（left join）

```sql
# 查询所有员工信息，以及对应的部门名称（没有部门的员工，也在查询结果中，部门名称以 null 填充）
select e.employee_id, e.first_name, e.salary, d.department_name from t_employees e
left join t_departments d
on e.department_id = d.department_id;
```

>注意：左外连接，是以左表为主，今次向右匹配，匹配到，返回结果；匹配不到，则返回 null 值填充

##### 右外连接（right join）

```sql
查询所有部门信息，以及此部门中所有员工信息（没有员工的部门，也在查询结果中，员工信息以 null 填充）
select e.employee_id, e.first_name, e.salary, d.department_name from t_employees e
right join t_departments d
on e.department_id = d.department_id;
```

> 注意：右外连接，是以右表为主，今次向左匹配，匹配到，返回结果；匹配不到，则返回 null 值填充

### DML 操作【重点】

#### 新增（insert）

语法：`insert into 表名(列1, 列2, 列3...) values(值1, 值2, 值3...);`

##### 添加一条信息

```sql
insert into t_jobs(job_id, job_title, min_salary, max_salary)
values('Java_Le', 'Java_Lecturer', 2500, 9000);
```

```sql
# 添加一条员工信息
insert into t_employees(employee_id, first_name, last_name, email, phone_number, hire_date, job_id, salary, commission_pct, man_ager_id, department_id)
values('194', 'Samuel', 'McCain', 'SMCCAIN', '650.510.3876', '1998-07-01', 'SH_CLERK', '3200', NULL, '123', '50');
```

> 注意：表名后的列名和 values 里的值要一一对应（个数、顺序、类型）

#### 修改（update）

语法：`update 表名 set 列名1=新值1, 列名2=新值2, ... where 条件;`

##### 修改一条信息

```sql
update t_employees set salary = 25000 where employee_id = '100';

update t_employees set job_id = 'st_man', salary = 3500 where employee_id = '135';
```

> 注意：set 后多个 列名=值，绝大多数情况下都要加 where 条件，指定修改，否则为整表更新

#### 删除（Delete）

语法：`delete from 表名 where 条件;`

```sql
delete from t_employees where employee_id = '135';

delete from t_employees where first_name = 'Peter' and last_name = 'Hail';
```

> 注意：删除时，如若不加 where 条件，删除的则是整张表的数据

#### 清空整表数据（truncate）

语法：`truncate table 表名;`

##### 清空整张表

```sql
truncate table t_countries;
```

> 注意：与 delete 不加 where 删除整表数据不同，truncate 是把表销毁，再按照原表的格式创建一张新表

### 数据表操作

#### 数据类型

`MySQL` 支持多种类型，大致可以分为三类：数值、日期/时间、字符串（字符）类型，对于我们约束数据的类型有很大的帮助。

##### 数值类型

| 类型         | 大小                            | 范围（有符号）            | 范围（无符号）            | 用途           |
| ------------ | ------------------------------- | ------------------------- | ------------------------- | -------------- |
| int          | 4字节                           | $-2^{31}$~$2^{31}-1$      | 0~$2^{32}-1$              | 大整数值       |
| double       | 8字节                           | (-1.797E+308,-2.22E-308)  | (0,2.22E-308,1.797E+308)  | 双精度浮点数值 |
| double(m, d) | 8字节，m表示长度，d表示小数位数 | 同上，受m和d的约束        | 同上，受m和d的约束        | 双精度浮点数值 |
| decimal(m,d) |                                 | 依赖于m和d的值，m最大值65 | 依赖于m和d的值，m最大值65 | 小数数值       |

##### 日期类型

| 类型      | 大小 | 范围                                                         | 格式                 | 用途                   |
| --------- | ---- | ------------------------------------------------------------ | -------------------- | ---------------------- |
| date      | 3    | 1000-01-01/9999-12-31                                        | YYYY-MM-DD           | 日期值                 |
| time      | 3    | '-838:59:59'/'838:59:59'                                     | HH:MM:SS             | 时间值或持续时间       |
| year      | 1    | 1901/2155                                                    | YYYY                 | 年份值                 |
| datetime  | 8    | 1000-01-01 00:00:00/9999-12-31 23:59:59                      | YYYY-MM-DD HH:MM:SS  | 混合日期和时间值       |
| timestamp | 4    | 1970-01-01 00:00:00/2038 结束时间是第2147483647秒（北京时间）格林尼治时间2038年1月19日凌晨03:14:07 | YYYYMM<br />DDHHMMSS | 混合日期、时间、时间戮 |

##### 字符串类型

| 类型    | 大小        | 用途                   |
| ------- | ----------- | ---------------------- |
| char    | 0~255字符   | 定长字符串             |
| varchar | 0~65535字节 | 变长字符串             |
| blob    | 0~65535字节 | 二进制形式的长文本数据 |
| text    | 0~65535字节 | 长文本数据             |

> 注意：
>
> 1. char 和 varchar 类型类似，但它们保存和检索的方式不同，它们的最大长度和是否尾部空格被保留等方面也不同，在存储和检索过程中不进行大小写转换
> 2. blob 是一个二进制大对象，可以容纳可变数量的数据，有 4 种 blob 类型：tinyblob，blob，mediumblob 和 longblob，它们只是可容纳值的最大长度不同

#### 数据表创建（create）

```sql
create table 表名 (
	列名 数据类型 [约束],
	列名 数据类型 [约束],
	.......
	列名 数据类型 [约束]   # 最后一列的末尾不加逗号
) [charset=utf8]  		# 可根据需要指定表的字符集编码
```

##### 创建表

| 列名         | 数据类型    | 说明     |
| ------------ | ----------- | -------- |
| subjectId    | int         | 课程编号 |
| subjectName  | varchar(20) | 课程名称 |
| subjectHours | int         | 课程时长 |

```sql
create table `subject` (
	subjectId int,
  subjectName varchar(20),
  subjectHours int
) charset=utf8;
# 注意：subject 是关键字，如果想规避关键字，使用 tab 上面、1 左面的键 '`' 将字符包裹即可

insert into subject(subjectId, subjectName, subjectHours) values(1, 'Java', 40);
insert into subject(subjectId, subjectName, subjectHours) values(2, 'MySQL', 30);
insert into subject(subjectId, subjectName, subjectHours) values(3, 'JavaScript', 20);
```

####  修改表（alter）

语法：`alter table 表名 操作`

##### 向现有表中添加列

```sql
alter table `subject` add gradeId int;
```

##### 修改表中的列

```sql
alter table `subject` modify subjectName varchar(10);
```

> 注意：修改表中的某列时，也要写全列的名字，数据类型，约束

##### 删除表中的列

```sql
alter table `subject` drop gradeId;
```

> 注意：删除列时，每次只能删除一列

##### 修改列名

```sql
alter table `subject` change subjectHours classHours int;
```

#####  修改表名

```sql
alter table `subject` rename sub;
```

#### 删除表

语法：`drop table 表名`

```sql
drop table `subject`;
```

### 约束

* 问题：在往已创建的表中新增数据时，可不可以新增两行列值相同的数据？
* 如果可行，会有什么弊端？

#### 实体完整性约束

表中的一行数据代表一行实体（`entity`），实体完整性的作用即是标识每一行数据不重复、实体唯一

##### 主键约束

`primary key`：唯一，标识表中的一行数据，此列的值不可重复，且不能为 `null`

```sql
# 为表中适用主键的列添加主键约束
create table `subject` (
	subjectId int primary key, # 标识每一个课程编号唯一，且不能为null
  subjectName varchar(20),
  subjectHours int
) charset=utf8;

insert into subject(subjectId, subjectName, subjectHours) values(1, 'Java', 40);
insert into subject(subjectId, subjectName, subjectHours) values(1, 'Java', 40); # error 主键 1 已经存在
```

##### 唯一约束

`unique`，唯一，标识表中的一行数据，不可以重复，可以为 `null`

```sql
# 为表中列值不允许重复的列添加唯一约束
create table `subject` (
	subjectId int primary key,
  subjectName varchar(20) unique, # 课程名称唯一
  subjectHours int
) charset=utf8;

insert into subject(subjectId, subjectName, subjectHours) values(1, 'Java', 40);
insert into subject(subjectId, subjectName, subjectHours) values(2, 'Java', 40); # error 课程名称已存在
```

##### 自动增长列

`auto_increment`：自动增长，给主键数值列添加自动增长，从 1 开始，每次加 1，**不能单独使用，和主键配合**

```sql
# 为表中主键列添加自动增长，避免忘记 ID 主键序号
create table `subject` (
	subjectId int primary key auto_increment, # 课程编号主键自动增长，会从 1 开始根据添加数据的顺序依次加 1
  subjectName varchar(20) unique, 
  subjectHours int
) charset=utf8;

insert into subject(subjectName, subjectHours) values('Java', 40);
insert into subject(subjectName, subjectHours) values('JavaScript', 40); 
```

#### 域完整性约束

用来限制列的单元格的数据正确性

##### 非空约束

`not null`：非空，此列必须有值

```sql
# 课程名称虽然添加了唯一约束，但是有 null 值存在的可能，要避免课程名称为 null
create table `subject` (
	subjectId int primary key auto_increment, # 课程编号主键自动增长，会从 1 开始根据添加数据的顺序依次加 1
  subjectName varchar(20) unique not null, 
  subjectHours int
) charset=utf8;

insert into subject(subjectName, subjectHours) values(null, 40); # error，课程名称约束了非空
```

##### 默认值约束

`default值`：为列赋予默认值，当新增数据不指定值时，书写 default，以指定的默认值进行填充

```sql
# 当存储课程信息时，如果课程时长没有指定，则以默认课时 20 填充
create table `subject` (
	subjectId int primary key auto_increment, # 课程编号主键自动增长，会从 1 开始根据添加数据的顺序依次加 1
  subjectName varchar(20) unique, 
  subjectHours int default 20
) charset=utf8;

insert into subject(subjectName, subjectHours) values('Java', default); # 课程时长默认以 20 填充
```

##### 引用完整性约束

* 语法：`constraint 引用名 foreign key(列名) references 被引用表名(列名)`
* 详解：`foreign key` 引用外部表的某个列的值，新增数据时，约束此列的值必须是引用表中存在的值

```sql
# 创建专业表
create table speciality (
	id int primary key auto_increment,
  specialName varchar(20) unique not null
) charset=utf8;

# 创建课程表（课程表的 specialId 引用专业表的 id）
create table `subject` (
	subjectId int primary key auto_increment, # 课程编号主键自动增长，会从 1 开始根据添加数据的顺序依次加 1
  subjectName varchar(20) unique, 
  subjectHours int default 20,
  specialId int not null
  constraint fk_subject_specialID foreign key(specialId) references speciality(id)  # 引用专业表里的 id 作为外键，新增课程信息时，约束课程所属的专业
) charset=utf8;

# 专业表新增数据
insert into speciality(specialName) values('Java');
insert into speciality(specialName) values('C#');

# 课程信息表添加数据
insert into subject(subjectName, subjectHours, specialId) values('Java', 30, 1); # 专业 id 为 1，引用的是专业表的 Java
insert into subject(subjectName, subjectHours, specialId) values('C#MVC', 10， 2); # 专业 id 为 2，引用的是专业表的 C#
```

#### 约束创建整合

##### 创建表

| 列名      | 数据类型    | 约束           | 说明     |
| --------- | ----------- | -------------- | -------- |
| gradeId   | int         | 主键，自动增长 | 班级编号 |
| gradeName | varchar(20) | 唯一、非空     | 班级名称 |

```sql
create table grade (
	gradeId int primary key auto_increment,
  gradeName varchar(20) unique not null
) charset=utf8;
```

| 列名         | 数据类型    | 约束                           | 说明     |
| ------------ | ----------- | ------------------------------ | -------- |
| student_id   | varchar(20) | 主键                           | 学号     |
| student_name | varchar(50) | 非空                           | 姓名     |
| sex          | char(1)     | 默认填充男                     | 性别     |
| borndate     | date        | 非空                           | 生日     |
| phone        | varchar(11) | 无                             | 电话     |
| gradeId      | int         | 非空，外键约束，引用班级表的id | 班级编号 |

```sql
create table student (
	student_id varchar(20) primary key,
  student_name varchar(50) not null,
  sex char(1) default '男',
  borndate date not null,
  phone varchar(11),
  gradeId int,
  constraint fk_student_gradeId foreign key(gradeId) references grade(gradeId)
) charset=utf8;
```

> 1. 创建关系表时，一定要先创建主表，再创建从表
> 2. 删除关系表时，先删除从表，再删除主表

### 事务【重点】

#### 模拟转账

生活当中转账是转账方账户扣钱，几账方账户加钱，可以使用数据库来模拟现实转账

##### 模拟转账

```sql
# A 账户转账给 B 账户 1000 元
# A 账户减 1000 元
update account set money = money - 1000 where id = 1;

# B 账户加 1000 元
update account set money = money + 1000 where id = 2;
```

> 以上代码就完成了两个账户之间的转账操作

##### 模拟转账错误

```sql
# A 账户转账给 B 账户 1000 元
# A 账户减 1000 元
update account set money = money - 1000 where id = 1;

# 断电、异常、出错...

# B 账户加 1000 元
update account set money = money + 1000 where id = 2;
```

> 上述代码在减操作之后的过程中出现了异常或者加钱语句出错，会发现，减钱仍然是成功了，而加钱失败了
>
> 注意：每条 sql 语句都是一个独立的操作，一个操作执行完对数据库是永久性的影响

#### 事务的概念

事务是一个原子操作，是一个最小执行单元，可以由一个或多个 sql 语句组成，在同一个事务当中，所有的 sql 语句都成功执行时，整个事务成功，有一条 sql 语句执行失败，整个事务都执行失败

#### 事务的边界

* 开始
  * 连接到数据库，执行一条 `DML` 语句。上一个事务结束后，又输入了一条 `DML` 语句，即事务的开始
* 结束
  * 提交
    * 显示提交：`commit`
    * 隐式提交：一条创建、删除的语句，正常退出（客户端退出连接）
  * 回滚
    * 显式回滚：`rollback`
    * 隐式回滚：非正常退出（断电，宕机），执行了创建、删除的语句，但是失败了，会为这个无效的语句执行回滚

#### 事务的原理

数据库会为每一个客户都维护一个空间独立的缓存区（回滚段），一个事务中所有的增删改语句的执行结果都会缓存在回滚段里，只有当事务中所有 `sql` 语句均正常结束（`commit`)，才会将回滚段中的数据同步到数据库。否则无论因为哪种原因失败，整个事务都将回滚（`rollback`）

#### 事务的特性

* `Atomicity`（原子性）
  * 表示一个事务内所有的操作是一个整体，要么全部成功，要么全部失败
* `Consistency`（一致性）
  * 表示一个事务内有一个操作失败时，所有更改过的数据必须回滚到更改前的状态
* `Isolation`（隔离性）
  * 事务查看数据操作时数据所处的状态，要么是另一并发事务修改它之前的状态，要么是另一事务修改它之后的状态，事务不会查看中间状态的数据
* `Durability`（持久性）
  * 持久性事务完成之后，它对于系统的影响是永久性的

#### 事务应用

应用环境：基于增删改语句的操作结果（均返回操作后受影响的行数），可通过程序逻辑手动控制事务提交或回滚

##### 事务完成转账

```sql
# A 账户给 B 账户转账
# 1. 开启事务
start transaction; # setAutoCommit=0; 禁止自动提交
# 2. 事务内数据操作语句
update account set money = money - 1000 where id = 1;
update account set money = money + 1000 where id = 2;
# 3. 事务内语句都成功了，执行 commit
commit;
# 4. 事务内语句如果出现错误，执行 rollback
rollback;
```

> 注意：开启事务后，执行的语句均属于当前事务，成功再执行 commit，失败要进行 rollback

### 权限管理

#### 创建用户

语法：`create user 用户名 identified by 密码;`

```sql
create user `zhangsan` identified by '123';
```

#### 授权

语法：`grant all on 数据库.表 to 用户名;`

```sql
grant all on companyDB.* to `zhangsan`;
```

#### 撤销授权

语法：`revoke all on 数据库.表 from 用户名;`

```sql
revoke all on companyDB.* from `zhangsan`;
```

> 注意：撤销权限后，账户要重新连接客户端才会生效

#### 删除用户

语法：`drop user 用户名;`

```sql
drop user `zhangsan`;
```

### 视图

#### 概念

视图，虚拟表，从一个表或多个表中查询出来的表，作用和真实表一样，包含一系列带有行和列的数据。视图中，用户可以使用 `select` 语句查询数据，也可以使用 `insert, update, delete` 修改记录，视图可以使用户操作方便，并保障数据库系统安全。

#### 视图特点

* 优点
  * 简单化，数据所见即所得
  * 安全性，用户只能查询或修改他们所能见得到的数据
  * 逻辑独立性，可以屏蔽真实表结构变化带来的影响
* 缺点
  * 性能相对较差，简单的查询也会变得稍显复杂
  * 修改不方便，特别是复杂的聚合视图基本无法修改

#### 视图的创建

语法：`create view 视图名 as 查询数据源表语句;`

##### 创建视图

```sql
# 创建 t_empInfo 的视图，其视图从 t_employees 表中查询到员工编号、员工姓名、员工邮箱、工资
create view t_empInfo
as
select employee_id, first_name, last_name, email, salary from t_employees;
```

##### 使用视图

```sql
# 查询 t_empInfo 视图中编号为 101 的员工信息
select * from t_empInfo where employee_id = '101';
```

#### 视图的修改

* 方式一：`create or replace view 视图名 as 查询语句`
* 方式二：`alter view 视图名 as 查询语句`

```sql
# 方式 1：如果视图存在则进行修改，反之，进行创建
create or replace view t_empInfo
as
select employee_id, first_name, last_name, email, salary, department_id from t_employees;

# 方式 2：直接对已存在的社稷进行修改
alter view t_empInfo
as
select employee_id, first_name, last_name, email, salary, department_id from t_employees;
```

#### 视图的删除

语法：`drop view 视图名`

```sql
drop view t_empInfo;
```

> 注意：删除视图不会影响原表

#### 视图注意事项

* 视图不会独立存储数据，万年青发生改变，视图也发生改变，没有优化任何查询性能
* 如果视图包含以下结构中的一种，则视图不可更新
  * 聚合函数的结果
  * `dintinct` 去重后的结果
  * `group by` 分组后的结果
  * `having` 筛选过后的结果
  * `union、union all` 联合后的结果

### SQL 语言分类

* 数据查询语言 `DQL（Data Query Language）：select、where、order by、group by、having`
* 数据定义语言 `DDL（Data Definition Language）：create、alter、drop`
* 数据操作语言 `DML（Data Mainipulation Language）：insert、update、delete`
* 事务处理语言 `TPL（Transaction Process Language）：commit、rollback`
* 数据控制语言 `DCL（Data Control Language）：grant、revoke`

### 综合练习

某商城数据库表结构如下：

```sql
# 创建用户表
create table user(
	userId int primary key auto_increment,
  username varchar(20) not null,
  password varchar(18) not null,
  address varchar(100),
  phone varchar(11)
);

# 创建分类表
create table category(
	cid varchar(32) primary key,
  cname varchar(100) not null				# 分类名称
);

# 商品表
create table `products`(
	`pid` varchar(32) primary key,
  `name` varchar(40),
  `price` double(7,2),
  category_id varchar(32),
  constraint fk_products_category_id foreign key(category_id) references category(cid)
);

# 订单表
create table `orders`(
	`oid` varchar(32) primary key,
  `totalprice` double(12,2),
  `userId` int,
  constraint fk_orders_userId foreign key(userId) references user(userId)
);

# 订单项表
create table orderitem(
	oid varchar(32),	# 订单 id
  pid varchar(32),	# 商品 id
  num int,					# 购买商品数量
  primary key(oid, pid), 		# 主键
  constraint fk_orderitem_oid foreign key(oid) references orders(oid),
  constraint fk_orderitem_pid foreign key(pid) references products(pid)
);

# 初始化数据

# 用户表添加数据
insert into user(username, password, address, phone) values('张三', '123', '北京昌平沙河', '13812345678');
insert into user(username, password, address, phone) values('王五', '5678', '北京海滨', '13812345141');
insert into user(username, password, address, phone) values('赵六', '123', '北京朝阳', '13812348987');
insert into user(username, password, address, phone) values('田七', '123', '北京大兴', '13812345687');

# 商品表初始化值
insert into products(pid, name, price, category_id) values('p001', '联想', 5000, 'c001');
insert into products(pid, name, price, category_id) values('p002', '海尔', 3000, 'c001');
insert into products(pid, name, price, category_id) values('p003', '雷神', 5000, 'c001');
insert into products(pid, name, price, category_id) values('p004', 'JACK JONES', 800, 'c002');
insert into products(pid, name, price, category_id) values('p005', '真维斯', 200, 'c002');
insert into products(pid, name, price, category_id) values('p006', '花花公子', 440, 'c002');
insert into products(pid, name, price, category_id) values('p007', '劲霸', 2000, 'c002');
insert into products(pid, name, price, category_id) values('p008', '香奈儿', 800, 'c003');
insert into products(pid, name, price, category_id) values('p009', '相宜本草', 200, 'c003');
insert into products(pid, name, price, category_id) values('p010', '梅明子', 200, null);

# 添加分类
insert into category values('c001', '电器');
insert into category values('c002', '服饰');
insert into category values('c003', '化妆品');
insert into category values('c004', '书籍');

# 添加订单
insert into orders values('o6100', 18000.50, 1);
insert into orders values('o6101', 7200.35, 1);
insert into orders values('o6102', 600.00, 2);
insert into orders values('o6103', 13000.26, 4);

# 订单详情表
insert into orderitem values('o6100', 'p001', 1),('o6100', 'p002', 1),('o6101', 'p003', 1);
```



















## 第二十三章 JDBC

`JDBC(Java Database Conectivity)` ，`Java` 连接数据库，可以使用 `Java` 语言连接数据库完成 `CRUD` 的操作。

### 核心思想

`Java` 中定义了访问数据库的接口，可以为多种关系型数据库提供统一的访问方式，由数据库厂商提供驱动实现类（`Driver` 数据库驱动）

[![6ma7cR.md.png](https://s3.ax1x.com/2021/03/05/6ma7cR.md.png)](https://imgtu.com/i/6ma7cR)

### 常用类

| 类型        | 完全限定名               | 简介                                                         |
| ----------- | ------------------------ | ------------------------------------------------------------ |
| `class`     | `java.sql.DriverManager` | 管理多个数据库驱动类，提供了获取数据库连接的方法             |
| `interface` | `java.sql.Connection`    | 代表一个数据库连接（当 `Connection` 不是 `null` 时，表示已连接数据库 |
| `interface` | `java.sql.Statement`     | 发送 `SQL` 语句到数据库工具                                  |
| `interface` | `java.sql.ResultSet`     | 保存 `SQL` 查询语句的结果数据（结果集）                      |
| `class`     | `java.sql.SQLException`  | 处理数据库应用程序时所发生的异常                             |

### 环境搭建

> 以 mysql 为例，驱动如下：
>
> mysql-connector-java-5.1.x ：适用于 5.x 版本
>
> mysql-connector-java-8.0.x ：适用于 8.x 版本

* 在 `Java` 项目下，创建 `lib` 包，将下载好的驱动文件放入该文件夹，在文件夹上点击右键，选择 `Add as Library（Project）`
* 在 `Maven` 项目下，打开项目的  `POM` 文件，添加相应的依赖即可

### 开发步骤

#### 1. 注册驱动

手动加载字节码文件到 `JVM` 中：

`Class.forName("com.jdbc.mysql.Driver"); // 加载驱动`

> 上面的数据库驱动字符串已经过期，下面是最新的：
>
> `com.mysql.cj.jdbc.Driver`

#### 2. 连接数据库

```java
Connection connection = DriverManager.getConnection(
    "jdbc:mysql://localhost:3306/database?useUnicode=true&characterEncoding=utf-8", // 数据库连接字符串
    username, // 数据库用户名
    password  // 数据库密码 
)
```

#### 3. 获取发送 SQL 的 Statement 对象

`Statement statement = connection.createStatement();`

#### 4. 执行 SQL 语句

```java
String sql = "INSERT INTO STUDENT_INFO(NAME, AGE) VALUES('zhangsan', 20);";
int res = statement.executeUpdate(sql); // 执行 sql 语句并接收结果
```

> 注意：在编写 `DML` 语句时，一定要注意字符串参数的符号是用单引号包裹的
>
> `DML` 语句：增删改使用，返回受影响的行数（`int`）
>
> `DQL` 语句：查询使用，返回结果数据（`ResultSet` 结果集）

#### 5. 处理结果

* 受影响行数：逻辑判断，方法返回
* 查询结果集：迭代、依次获取

#### 6. 释放资源

遵循 **先开后关** 的原则，释放所使用到的资源对象

```java
statement.close();
conn.close();
```

#### 7. 综合示例

```java
public class FirstTest {

    @Test
    public void testConnectDB() throws Exception {
        // 注册驱动
        Class.forName("com.mysql.cj.jdbc.Driver");

        // 获取连接
        Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/useful?useUnicode=true&characterEncoding=utf-8",
                "******", "******");

        // 判断连接是否可用
        if (conn != null) {
            System.out.println("数据库连接成功！");

            Statement statement = conn.createStatement();
            int res = statement.executeUpdate("delete from common_md5 where id=5110001");
            System.out.println("影响了 " + res + " 行数据！");

            statement.close();
            conn.close();
        } else {
            System.out.println("数据加连接失败！");
        }
    }
}
```

### ResultSet

在执行完查询 `SQL` 语句后，`ResultSet` 用来存放查询到的结果数据

#### 1. 接收结果集

```java
ResultSet rs = statement.executeQuery("select * from stu_info;");
```

#### 2. 遍历

`ResultSet` 以表的结构进行临时数据的存储，需要通过 `JDBC API` 将其中数据进行依次获取

* 数据行指针：初始位置在第一行数据前，每调用一次 `next()` 方法，`RestltSet` 的指针向下移动一行， 结果为 `true` 时，代表当前行有数据
* `rs.getXxx(整数)` ：根据列的编号顺序获得，从 `1` 开始
* `rs.getXxx(列名)` ：根据列名获得

##### 遍历时常用的方法

```java
int getInt(int columnIndex); // 获得当前行第 n 列的 int 值
int getInt(String columnLabel); // 获得当前行 column 列的 int 值

int getDouble(int columnIndex); // 获得当前行第 n 列的 double 值
int getDouble(String columnLabel); // 获得当前行 column 列的 double 值

int getString(int columnIndex); // 获得当前行第 n 列的 String 值
int getString(String columnLabel); // 获得当前行 column 列的 String 值

......
```

> 注意：列的编号从 1 开始

**综合练习**

```java
public class ExecuteQuery {

    @Test
    public void testExecuteQuery() {
        Connection conn = null;
        Statement statement = null;
        ResultSet rs = null;
        try {
            // 注册驱动
            Class.forName("com.mysql.cj.jdbc.Driver");

            // 获取数据库连接
            conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/useful?useUnicode=true&characterEncoding=utf-8", "******", "******");

            // 获取 Statement，用于执行 SQL 语句
            statement = conn.createStatement();

            // 执行查询语句，获取 ResultSet
            rs = statement.executeQuery("select * from salary_igyj");

            // 遍历 Result
            while (rs.next()) {
                int id = rs.getInt(1);
                int money = rs.getInt(2);
                String text = rs.getString("text");

                System.out.printf("%-4d%8d.00%16s\n", id, money, text);
            }

        } catch (Exception e) {
            System.out.println(e.getMessage());
        } finally {
            try {
                if (rs != null)
                    rs.close();
                if (statement != null)
                    statement.close();
                if (conn != null)
                    conn.close();
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
}
```

### 常见错误

* `java.lang.classNotFoundException` ：找不到类（类名书写错误，或没有导入`jar` 包）
* `java.sql.SQLExceptionn` ：与 `sql` 语句相关的错误（约束错误、表名列名书写错误等），**建议**：在客户端工具中测试 `sql` 语句之后再粘贴在代码中
* `com.mysql.jdbc.exceptions.jdbc4.MySQLSyntaxErrorException:Unknown column` ：列名 `String` 类型没有加单引号
* `Duplicate entry '1' for key 'PRIMARY'` ：主键值已经存在或混乱，可以采用更改主键值或清空表的方式解决该问题
* `com.mysql.jdbc.exception.jdbc4.MySQLSyntaxErrorException:Unknown column 'password' in` ：可以输入值的类型不对，确认是否插入的元素对应的值类型是否正确

### SQL 注入

#### 什么是 SQL 注入

用户输入的数据中有 `SQL` 关键字或语法并且参与了 `SQL` 语句的编译，导致 `SQL` 语句编译后的条件含义为 `true`，一直得到正确的结果。这种现象称为 `SQL` 注入 。

#### 如何避免 `SQL` 注入

由于编写的 `SQL` 语句是在用户输入数据，整合后再进行编译。所以为了避免 `SQL` 注入问题，我们要使 `SQL` 语句在用户输入之前就已经编译成完整的 `SQL` 语句，再进行填充数据。

### PreparedStatement【重点】

> `PreparedStatement` 继承了 `Statement` 接口，执行 `SQL` 语句的方法无异

#### 应用

* 预编译 `SQL` 语句，效率高
* 安全，避免 `SQL` 注入
* 可以动态的填充数据，执行多个同构的 `SQL` 语句

#### 参数标记

```java
// 预编译 SQL 语句
PreparedStatement pStatement = conn.preparedStatement(
        "select * from user where name=?");
```

> `JDBC` 中的所有参数都由 ？ 点位，这被称为参数标记，在执行 `SQL` 语句之前，必须为每个参数提供值

#### 动态参数绑定

`pstm.setXxx(下标, 值)`：为指定下标的参数绑定值

```java
// 预编译 SQL 
PreparedStatement pStatement = conn.preparedStatement(
        "select * from user where name=?");
// 根据参数下标赋值
pStatement.setString(1, username);
pStatement.setString(2, password)；
```

### 封装工具类

* 在实际的 `JDBC` 的使用中，存在着大量的重复代码，例如：连接数据库、关闭数据库等这些操作
* 我们需要把传统的 `JDBC`  代码进行重构，抽取出通用的 `JDBC` 工具类。以后连接任何数据库、释放资源都可以使用这个工具类

```java
/**
 * @program: study
 * @description: JDBC 工具类。注意：使用这个类时，需要在类路径的根路径下创建一个 jdbc.properties 文件，用于存放数据库连接的相关信息
 * @create: 2021-02-28 21:58
 **/
public class JDBCUtil {
    private static final Properties PROPERTIES = new Properties();

    static { // 类加载，只执行一次
        try (InputStream is = JDBCUtil.class.getResourceAsStream("/jdbc.properties")) {
            PROPERTIES.load(is);
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException | IOException e) {
            e.printStackTrace();
        }
    }

    private JDBCUtil() {}

    /**
     * 获取数据库连接对象
     * @return - 数据库连接对象
     * @throws SQLException - 数据库连接失败等异常
     */
    public static Connection getConnection() throws SQLException {
        return DriverManager.getConnection(PROPERTIES.getProperty("url"), PROPERTIES.getProperty("username"), PROPERTIES.getProperty("password"));
    }

    /**
     * 关闭 JDBC 数据库操作中可能用到的资源
     * @param rs - ResultSet
     * @param sm - Statement
     * @param conn - Connection
     * @throws SQLException - 数据库操作相关异常
     */
    public static void closeAll(ResultSet rs, Statement sm, Connection conn) throws SQLException {
        if (rs != null)
            rs.close();
        if (sm != null)
            sm.close();
        if (conn != null)
            conn.close();
    }
}
```

### ORM

`ORM(Object Relational Mapping)`：对象关系映射。从数据库查询到的结果集（`ResultSet`）在进行遍历时，逐行遍历，取出的都是零散的数据。在实际应用开发中，需要将零散的数据进行封装整理

#### 实体类（`entity`）：零散数据的载体

* 一行数据中，多个零散的数据进行整理
* 通过 `entity` 的规则，对表中的数据进行对象的封装
* **表名=类名；列名=属性名；提供各个属性的 get、set 方法**
* 提供无参构造方法（视情况添加有参构造）

### DAO（数据访问层）

数据访问对象（`Data Access Object`），实现了业务逻辑与数据库访问分离：

* 对同一张表的所有操作封装在 `XxxDaoImpl` 对象中
* 根据增删改查的不同功能实现具体的方法（`insert、update、delete、select、selectAll`）

### Date 工具类

数据库存储的数据类型为 `java.sql.Date`，而我们 `Java` 应用层存储日期数据的类型为 `java.util.Date`，当我们用 `Java` 应用程序插入带有日期的数据到数据库中时，需要进行转换。

#### java.util.Date

* `Java` 语言常规应用层面的日期类型，可能通过寡不敌众串创建对应的时间对象
* 无法直接通过 `JDBC` 插入到数据库

#### java.sql.Date

* 不可以通过字符串创建对应的时间对象，只能通过毫秒创建对象（毫秒：`1970` 年至今的毫秒值）
* 可以直接通过 `JDBC` 插入到数据库

#### SimpleDateFormat

用于格式化和解析日期的具体类，允许进行格式化（日期 `->` 文本）、解析（文本 `->` 日期）和规范化。

##### 使用

```java
SimpleDateFormat sdf = SimpleDateFormat("yyyy-MM-dd"); // 指定日期格式
java.util.Date date = sdf.parse(String dateStr); // 将字符串解析成日期类型（java.util.Date)
String dates = sdf.format(date); // 将日期格式化成字符串
```

### Service（业务逻辑层）

业务，代表用户完成的一个业务功能，可以由一个或多个 `Dao` 的调用组成（软件所提供的一个功能都叫业务）。

[![6FYh7t.md.png](https://s3.ax1x.com/2021/03/02/6FYh7t.md.png)](https://imgtu.com/i/6FYh7t)

### 综合实例——银行转账

#### 创建数据库表

```sql
CREATE TABLE bank_card (
	card_no VARCHAR(4) NOT NULL PRIMARY KEY,
	password INT NOT NULL,
	name VARCHAR(32) NOT NULL,
	balance INT
) charset=utf8
```

#### 创建实体类

```java
@Data
public class BankCard {
    private String cardNo;
    private int password;
    private String name;
    private int balance;

    public BankCard() {
    }

    public BankCard(String cardNo, int password, String name, int balance) {
        this.cardNo = cardNo;
        this.password = password;
        this.name = name;
        this.balance = balance;
    }
}
```

#### 创建数据访问层

```java
public class BankCardDao extends AbstractDao<BankCard> {

    private Connection conn;
    private PreparedStatement pstm;
    private ResultSet rs;

    @Override
    public int add(BankCard bankCard) {
        return 0;
    }

    @Override
    public int delete(int key) {
        return 0;
    }

    @Override
    public int delete(String key) {
        return 0;
    }

    @Override
    public int update(BankCard bankCard) {
        int res = 0;

        try {
            init();

            pstm = conn.prepareStatement("update bank_card set password=?, name=?, balance=? where card_no=?");
            pstm.setInt(1, bankCard.getPassword());
            pstm.setString(2, bankCard.getName());
            pstm.setInt(3, bankCard.getBalance());
            pstm.setString(4, bankCard.getCardNo());
            res = pstm.executeUpdate();

        } catch (Exception e) {
            e.printStackTrace();
        }

        return res;
    }

    @Override
    public BankCard findOne(String key) {
        BankCard bankCard = null;

        try {
            init();

            pstm = conn.prepareStatement("select * from bank_card where card_no=?");
            pstm.setString(1, key);
            rs = pstm.executeQuery();

            if (rs.next()) {
                bankCard = new BankCard(key, rs.getInt("password"), rs.getString("name"), rs.getInt("balance"));
            }

        } catch (Exception e) {
            e.printStackTrace();
        }

        return bankCard;
    }

    @Override
    public BankCard findOne(int key) {
        return null;
    }

    @Override
    public List<BankCard> findAll() {
        return null;
    }

    private void init() throws Exception {
        conn = JDBCUtil.getConnection();
    }
}
```

#### 创建业务逻辑层

```java
public class BankCardServiceImpl {

    private BankCardDao bankCardDao = new BankCardDao();

    public void transferMoney(String from, int password, int balance, String to) {
        try {
            BankCard fromAccount = bankCardDao.findOne(from);

            JDBCUtil.setAutoCommit(false);

            // 1. 判断 from 账号是否存在
            if (fromAccount == null)
                throw new RuntimeException("账户不存在！");

            // 2. 判断 from 账号密码是否正确
            if (password != fromAccount.getPassword())
                throw new RuntimeException("密码不正确！");

            // 3. 判断 from 账号余额是否充足
            if (fromAccount.getBalance() < balance)
                throw new RuntimeException("余额不足！");

            // 4. 判断 to 账号是否存在
            BankCard toAccount = bankCardDao.findOne(to);
            if (toAccount == null)
                throw new RuntimeException("对方账号不存在!");

            // 5. 从 from 账号的余额中减去要转的钱
            fromAccount.setBalance(fromAccount.getBalance() - balance);
            bankCardDao.update(fromAccount);

            // 6. 给 to 账号的余额增加转来的钱
            toAccount.setBalance(toAccount.getBalance() + balance);
            bankCardDao.update(toAccount);

            JDBCUtil.commit();
            System.out.println("转账成功！");
        } catch (Exception e) {
            System.out.println("转账失败！");
            try {
                if (JDBCUtil.getConnection() != null)
                    JDBCUtil.rollback();
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
            e.printStackTrace();
        }
    }
}
```

#### 单元测试

```java
public class BankCardTest {

    @Test
    public void testTransferMoney() {
        BankCardServiceImpl bankCardService = new BankCardServiceImpl();
        bankCardService.transferMoney("1234", 1234, 1000, "22343");
    }
}
```

#### 附：JDBCUtil.java

```java
public class JDBCUtil {
    private static final Properties PROPERTIES = new Properties();

    private static ThreadLocal<Connection> threadLocal = new ThreadLocal<>();

    static { // 类加载，只执行一次
        try (InputStream is = JDBCUtil.class.getResourceAsStream("/jdbc.properties")) {
            PROPERTIES.load(is);
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException | IOException e) {
            e.printStackTrace();
        }
    }

    private JDBCUtil() {}

    /**
     * 获取数据库连接对象
     * @return - 数据库连接对象
     * @throws SQLException - 数据库连接失败等异常
     */
    public static Connection getConnection() throws SQLException {
        Connection conn = threadLocal.get();
        if (conn == null) {
            conn = DriverManager.getConnection(PROPERTIES.getProperty("url"), PROPERTIES.getProperty("username"), PROPERTIES.getProperty("password"));
            threadLocal.set(conn);
        }
        return conn;
    }

    /**
     * 设置 Connection 的自动提交为 false
     * @throws SQLException - SQL 操作失败
     */
    public static void setAutoCommit(boolean sign) throws SQLException {
        getConnection().setAutoCommit(sign);
    }

    /**
     * Connection 提交更改
     * @throws SQLException - SQL 操作失败
     */
    public static void commit() throws SQLException {
        getConnection().commit();
        closeAll(null, null, getConnection());
        threadLocal.remove();
    }

    /**
     * 设置 Connection 进行事务的回滚
     * @throws SQLException - SQL 操作失败
     */
    public static void rollback() throws SQLException {
        getConnection().rollback();
        closeAll(null, null, getConnection());
        threadLocal.remove();
    }

    /**
     * 关闭 JDBC 数据库操作中可能用到的资源
     * @param rs - ResultSet
     * @param sm - Statement
     * @param conn - Connection
     * @throws SQLException - 数据库操作相关异常
     */
    public static void closeAll(ResultSet rs, Statement sm, Connection conn) throws SQLException {
        if (rs != null)
            rs.close();
        if (sm != null)
            sm.close();
        if (conn != null)
            conn.close();
    }
}
```

### 三层架构

#### 表示层

* 命名：`XxxView`
* 职责：收集用户的数据和需求、展示数据

#### 业务逻辑层

* 命名：`XxxServiceImpl`
* 职责：数据加工处理、调用 `Dao` 完成业务实现、控制事务

#### 数据访问层

* 命名：`XxxDao`
* 职责：向业务层提供数据，将业务层加工后的数据同步到数据库

[![6ka9zT.png](https://s3.ax1x.com/2021/03/02/6ka9zT.png)](https://imgtu.com/i/6ka9zT)

#### 三层架构项目搭建

* `utils` 存放工具类（`JDBCUtil`）
* `entity` 存放实体类（`BankCard`）
* `dao` 存放 `Dao` 接口（`BankCardDao`）
  * `impl` 存放 `Dao` 接口实现类（ `BankCardDaoImpl`）
* `service` 存放 `service` 接口（`BankCardService`）
  * `impl` 存放 `service` 接口实现类（`BankCardServiceImpl`）

> 程序设计时，考虑易修改、易扩展，为 `service` 层和 `Dao` 层设计接口，便于来更换实现类

### DaoUtil

> 在 Dao 层中，对数据库表的增、删、改、查操作存在代码冗余，可对其进行抽取封装为 DaoUtil 工具类实现复用

```java
/**
 * @文件名: DaoUtil
 * @项目名 study
 * @描述: Dao 工具类，里面是能用的更新方法和查询方法
 * @作者 wchya
 * @日期 2021-03-02 21:37
 */
public class DaoUtil<T> {

    /**
     * jdbc 增、删、改 的通用操作方法
     * @param sql - 要执行的 sql 语句
     * @param args - 可变参数，用于 sql 中占位符的实际值
     * @return - 受影响的行数
     * @throws Exception - SQL 相关的异常
     */
    public static int commonUpdates(String sql, Object... args) throws SQLException {
        Connection conn = null;
        PreparedStatement pstm = null;
        try {
            conn = JDBCUtil.getConnection();

            JDBCUtil.setAutoCommit(false);
            pstm = conn.prepareStatement(sql);

            for (int i = 0; i < args.length; i++) {
                pstm.setObject(i + 1, args[i]);
            }

            int res = pstm.executeUpdate();
            JDBCUtil.commit();
            return res;
        } finally {
            JDBCUtil.closeAll(null, pstm, conn);
        }
    }

    /**
     * jdbc 查询的通用方法，查询出来的数据可以对应任何类
     * @param sql - 要查询的 sql 语句
     * @param rowMapper - 一个回调接口，用于调用者使用该接口的 getRow() 方法将查询的数据封装到具体的对象中
     * @param args - 可变参数，用于传入预编译 Statement 的具体值
     * @return - 结果集合
     * @throws SQLException - sql 相关异常
     */
    public List<T> commonSelect(String sql, RowMapper<T> rowMapper, Object... args) throws SQLException {
        Connection conn = null;
        PreparedStatement pstm = null;
        ResultSet rs = null;
        List<T> list = new ArrayList<>();

        conn = JDBCUtil.getConnection();
        pstm = conn.prepareStatement(sql);
        for (int i = 0; i < args.length; i++) {
            pstm.setObject(i + 1, args[i]);
        }

        rs = pstm.executeQuery();

        while (rs.next()) {
            list.add((T) rowMapper.getRow(rs));
        }

        return list;
    }

    @Test
    public void testTest() throws SQLException {
        int res = commonUpdates("update bank_card set name=? where card_no=?", "third", "2234");
        System.out.println("受影响的行数为：" + res);
    }

    @Test
    public void testSelect() throws SQLException {
        RowMapper<BankCard> mapper = rs -> {
            BankCard bankCard = null;
            try {
                bankCard = new BankCard(rs.getString("card_no"), rs.getInt("password"), rs.getString("name"), rs.getInt("balance"));
                return bankCard;
            } catch (SQLException throwables) {
                throwables.printStackTrace();
            }
            return bankCard;
        };

        List<BankCard> list = new DaoUtil<BankCard>().commonSelect("select * from bank_card where card_no=?", mapper, "2234");

        if (!list.isEmpty()) {
            BankCard bankCard = (BankCard) list.get(0);
            System.out.println(bankCard);
        }
    }
}

public interface RowMapper<T> {
    T getRow(ResultSet rs);
}
```

### Druid 连接池

在程序初始化时，预先创建指定数量的数据库连接对象存储在池中，当需要连接数据库时，从连接池中取出现有连接；使用完毕后，也不会进行关闭，而是放回池中，实现复用，节省资源

#### 连接池使用步骤

1. 创建 `database.properties` 配置文件
2. 引入 `druid-1.1.5.jar` 文件

#### 配置文件

```properties
# 连接设置
# 下面四个键名不能改变，这些都是 Druid 的实现类里面规定的名称，改变后会抛出异常
driverClassName=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://localhost:3306/school?useUnicode=true&characterEncoding=utf-8
username=root
password=root
# 初始化连接
initialSize=10
# 最大连接数量
maxActive=50
# 最小空闲数量（如果初始化的10个连接一直没有用，系统会自动释放一部分，这里的数量设置的就是释放后剩余的连接数）
minIdle=5
# 超时等待时间，以毫秒为单位
maxWait=5000
```

#### 连接池工具类

```java
public class DataSourceUtil {
    // 声明连接池对象
    private static DruidDataSource ds;

    static {
        try (InputStream is = DataSourceUtil.class.getResourceAsStream("/jdbc.properties")) {
            Properties properties = new Properties();
            properties.load(is);

            // 创建连接池
            ds = (DruidDataSource) DruidDataSourceFactory.createDataSource(properties);
        } catch (IOException e) {
            e.printStackTrace();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    /**
     * 获取连接
     * @return - 数据库连接
     */
    public static Connection getConnection() {
        try {
            return ds.getConnection(); // 通过连接池获得连接对象
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return null;
    }
}
```

### DbUtils 使用（Apache）

`Commons DbUtils` 是 `Apache` 组织提供的一个对 `JDBC` 进行简单封装的开源工具类库，使用它能够简化 `JDBC` 应用程序的开发！同时，不会影响程序的性能。

#### 简介

`DbUtils` 是 `Java` 编程中数据库操作的实用小工具，小巧、简单、实用：

* 对于数据表的查询操作，可以把结果转换为 `List、Array、Set` 等集合，便于操作
* 对于数据表的 `DML` 操作，也变得很简单（只需要写 `SQL` 语句）

#### 主要包含

* `ResultSetHandler` 接口：转换类型接口
  * `BeanHandler`：实现类，把一条记录转换成对象
  * `BeanListHandler`：实现类，把多条记录转换成 `List` 集合
  * `ScalarHandler`：实现类，适合获取一行一列的数据
* `QueryRunner`：执行 `sql` 语句的类
  * 增、删、改：`update()`
  * 查询：`query()`

> 注意：
>
> 1. 使用 QueryRunner 时写的 sql 中，查找出来的列的名称要和泛型中传递实体的属性名称一致，例如：实体中属性名称是：userName，在查找的 sql 中，必须有这个列名才行

#### 使用步骤

* 导入 `jar` 包
  * `mysql` 连接驱动的 `jar` 包
  * `Druid` 的 `jar` 包
  * `commons-dbutils` 的 `jar` 包
* `db.properties` 配置文件

#### 实例

```java
// Dao 层
public class DboperUser2Dao extends AbstractDao<DboperUser> {

    private QueryRunner queryRunner = new QueryRunner(DataSourceUtil.getDataSource());

    @Override
    public int add(DboperUser dboperUser) {
        try {
            Object[] objects = {dboperUser.getName(), dboperUser.getAge(), dboperUser.getBirthday()};
            return queryRunner.update("insert into dboper_user(name, age, birthday) values(?,?,?)", objects);
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return 0;
    }

    @Override
    public int delete(int key) {
        try {
            return queryRunner.update("delete from dboper_user where id=?", key);
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return 0;
    }

    @Override
    public int delete(String key) {
        return 0;
    }

    @Override
    public int update(DboperUser dboperUser) {
        try {
            Object[] objects = {dboperUser.getName(), dboperUser.getAge(), dboperUser.getBirthday(), dboperUser.getId()};
            return queryRunner.update("update dboper_user set name=?, age=?, birthday=? where id=?", objects);
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return 0;
    }

    @Override
    public DboperUser findOne(String key) {

        return null;
    }

    @Override
    public DboperUser findOne(int key) {
        try {
            return queryRunner.query("select * from dboper_user where id=?", new BeanHandler<DboperUser>(DboperUser.class), key);
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return null;
    }

    @Override
    public List<DboperUser> findAll() {
        try {
            return queryRunner.query("select * from dboper_user", new BeanListHandler<DboperUser>(DboperUser.class));
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return null;
    }

    public long getUserCounts() {
        try {
            return queryRunner.query("select count(id) from dboper_user", new ScalarHandler<>());
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return -1;
    }
}
```

```java
// 测试类
public class CommonsDbutilsTest {

    private DboperUser2Dao userDao;

    @BeforeTest
    public void init() {
        userDao = new DboperUser2Dao();
    }

    @Test
    public void testAdd() {
        int res = userDao.add(new DboperUser("dbutils", 22, DateTimeUtil.utilDateToSqlDate(new Date())));
        System.out.println("插入 " + res + " 条数据！");
    }

    @Test
    public void testUpdate() {
        int res = 0;
        try {
            res = userDao.update(new DboperUser(4, "dbutils", 20, DateTimeUtil.utilDateToSqlDate(DateTimeUtil.strToUtilDate("1985-03-03"))));
        } catch (ParseException e) {
            e.printStackTrace();
        }
        System.out.println("修改 " + res + " 条数据！");
    }

    @Test
    public void testDelete() {
        int res = 0;
        res = userDao.delete(5);
        System.out.println("删除 " + res + " 条数据！");
    }

    @Test
    public void testFindOne() {
        DboperUser user = userDao.findOne(4);
        System.out.println(user);
    }

    @Test
    public void testFindAll() {
        List<DboperUser> lists = userDao.findAll();
        lists.forEach(System.out::println);
    }

    @Test
    public void testGetUserCounts() {
        long userCounts = userDao.getUserCounts();
        System.out.println(userCounts);
    }
}
```



## 第XX章 多线程

### 进程与线程

**进程**：正在进行的程序，是系统进行资源分配的基本单位。目前，操作系统都是多进程的，可以同时执行多个进程，通过进程 `ID` 进行区分

**线程**：又称轻量级进程，进程中的一条执行路径，也是 `CPU` 的基本调度单位

**关系**：一个进程由一个或多个线程组成，彼此间完成不同的工作，同时执行，称为多线程

**区别**：

1. 进程是操作系统资源分配的基本单位，而线程是 `CPU` 的基本调度单位
2. 一个程序运行后至少有一个进程
3. 一个进程可以包含多个线程，但是至少需要有一个线程，否则这个进程没有意义
4. 进程之间不能共享数据段地址，但同进程的线程之间可以

### 线程的组成

* `CPU` 时间片：操作系统（`OS`）会为每个线程分配执行时间
* 运行数据
  
  * 堆空间：存储线程需使用的对象，多个线程可以共享堆中的对象
  * 栈空间：存储线程需使用的局部变量，每个线程都拥有独立的栈
* 线程的逻辑代码

### 线程的特点

1. 线程抢占式执行
  
   1. 效率高
   2. 可以防止单一线程长时间独占 `CPU`
2. 在单核 `CPU` 中，宏观上同时执行，微观上顺序执行

### 创建线程的三种方式

#### 继承 Thread 类，重写 run 方法

#### 实现 Runnable 接口

1. 实现 `Runnable` 接口
2. 覆盖 `run` 方法
3. 创建实现类对象
4. 创建线程对象
5. 调用 `start` 方法

> 注意：Runnable 是线程可运行的功能，不是直接可以运行的线程，需要当作参数传递到 Thread 中使用

#### 实现 Callable 接口

### 线程名称

#### 获取

* 在 `Thread` 的子类中调用 `this.getId()` （获取线程 `ID`）或 `this.getName()` （获取线程名称）
  
  > 该方法只适合继承了 Thread 的子类中使用
* 使用 `Thread.currentThread().getId()` 和 `Thread.currentThread().getName()`

#### 修改

* 调用线程对象的 `setName()` 方法
* 使用线程子类的构造方法赋值

### 线程状态（基本）

```flow
st=>start: 开始
ed=>end: 结束
op1=>operation: 初始状态
op2=>operation: 就绪状态
op3=>operation: 运行状态
op4=>operation: 终止状态
cd1=>condition: 创建对象
cd2=>condition: 调用 start()
cd3=>condition: 抢占时间片
cd4=>condition: 时间片到期
cd5=>condition: run() 方法结束

st(right)->cd1
cd1(yes,right)->op1(right)->cd2
cd2(yes,right)->op2(right)->cd3
cd3(yes,right)->op3(right)->cd4
cd3(no,right)->op2
cd4(yes)->op2
cd4(no)->op3
op3->cd5(yes)->op4(right)->ed
cd5(no)->op3
```

#### 初始状态

线程对象被创建，即为初始状态。只在堆中开辟内存，与常规对象无异

#### 就绪状态

调用 `start()` 之后，进入就绪状态。等待 `0S` 选中，并分配时间片

#### 运行状态

获取时间片之后，进入运行状态，如果时间片到期，就回到就绪状态

#### 终止状态

`run()` 方法执行完成后，就到达终止状态

### 常见方法

* `public static void sleep(long millis)` ：当前线程主动休眠 `millis` 毫秒
* `public static void yield()` ：当前线程主动放弃时间片，回到就绪状态，竞争下一次时间片
* `public final void join()` ：加入到当前线程中（会阻塞当前线程，直到加入线程执行完毕）

### 优先级

线程优先级为 `1-10`，默认为 `5`，优先级越高，表示获取 `CPU` 机会越多

`线程对象.setPriority()`

### 类别

* 用户线程（前台线程）
* 守护线程（后台线程）

如果程序中所有前台线程都执行完毕了，后台线程会自动结束

> 垃圾回收器线程属于守护线程

### 线程安全问题

#### 多线程安全问题

* 当多线程迸发访问临界资源时，如果破坏原子操作，可能会造成数据不一致
* 临界资源：共享资源（同一对象），一次仅允许同一个线程使用，才可保证其正确性
* 原子操作：不可分割的多步操作被视作一个整体，其顺序和步骤不可打乱或缺省