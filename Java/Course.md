Java

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

[![6BBkYn.md.png](https://s3.ax1x.com/2021/03/15/6BBkYn.md.png)](https://imgtu.com/i/6BBkYn)

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

* * 

## 第二十章 MySQL 数据库

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

##### 查询各部门的平均工资

```sql
# 思路
# 1. 按照部门编号进行分组（分组依据是 employee_id)
# 2. 再针对各部门进行平均工资统计（avg）
select department_id, avg(salary)
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
  specialId int not null,
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

* 视图不会独立存储数据，源数据发生改变，视图也发生改变，没有优化任何查询性能
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

#### 综合练习1 - 【多表查询】

##### 查询所有用户的订单

```sql
select o.oid, o.totalprice, u.userId, u.userName, u.phone
from orders o inner join user u on o.userId = u.userId;
```

##### 查询用户 id 为 1 的所有订单详情

```sql
select o.oid, o.totalprice, u.userId, u.username, u.phone, oi,pid
from orders o inner join user u on o.userId = u.userId
inner join orderitem oi on o.oid = oi.oid
where u.userid = 1;
```

#### 综合练习2 - 【子查询】

##### 查看用户为张三的订单

```sql
select * from orders where userId = (select userid from user where username='张三');
```

##### 查询出订单的价格大于 800 的所有用户信息

```sql
select * from user where userId in (select distinct userId from where totalprice > 800);
```

#### 综合练习3 - 【分页查询】

##### 查询所有订单信息，每页显示 5 条数据

```sql
# 查询第一页
select * from orders limit 0,5;
```

## 第二十一章 JDBC

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

* 对同一张表的所有操作封装在 `XxxDaoImpl` 类中
* 根据增删改查的不同功能实现具体的方法（`insert、update、delete、select、selectAll`）

### Date 工具类

数据库存储的数据类型为 `java.sql.Date`，而我们 `Java` 应用层存储日期数据的类型为 `java.util.Date`，当我们用 `Java` 应用程序插入带有日期的数据到数据库中时，需要进行转换。

#### java.util.Date

* `Java` 语言常规应用层面的日期类型，可以通过字符串创建对应的时间对象
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
) charset=utf8;
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
    private static final ThreadLocal<Connection> THREAD_LOCAL = new ThreadLocal<>();

    static { // 类加载，只执行一次
        try (InputStream is = JDBCUtil.class.getResourceAsStream("/jdbc.properties")) {
            PROPERTIES.load(is);
            Class.forName(PROPERTIES.getProperty("driverClassName"));
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
    public static Connection getConnection() {
        Connection conn = THREAD_LOCAL.get();
        try {
            if (conn == null) {
                conn = DriverManager.getConnection(PROPERTIES.getProperty("url"), PROPERTIES.getProperty("username"), PROPERTIES.getProperty("password"));
                THREAD_LOCAL.set(conn);
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return conn;
    }

    /**
     * 设置 Connection 的自动提交为 false
     * @throws SQLException - SQL 操作失败
     */
    public static void beginTransaction() {
        try {
            Connection conn = getConnection();
            conn.setAutoCommit(false);
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    /**
     * Connection 提交更改
     * @throws SQLException - SQL 操作失败
     */
    public static void commit() {
        try {
            Connection conn = getConnection();
            conn.commit();
            close(conn, null, null);
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    /**
     * 设置 Connection 进行事务的回滚
     */
    public static void rollback() {
        try {
            Connection conn = getConnection();
            conn.rollback();
            close(conn, null, null);
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    /**
     * 关闭 JDBC 数据库操作中可能用到的资源
     * @param rs - ResultSet
     * @param sm - Statement
     * @param conn - Connection
     */
    public static void close(Connection conn, Statement statement, ResultSet rs) {
        try {
            if (rs != null)
                rs.close();

            if (statement != null)
                statement.close();

            if (conn != null) {
                conn.close();
                THREAD_LOCAL.remove();
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
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

* 命名：`XxxDaoImpl`
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
2. 引入 `druid-x.x.x.jar` 文件

#### 配置文件

```properties
# 连接设置
# 下面四个键名不能改变，这些都是 Druid 的实现类里面规定的名称，改变后会抛出异常
driverClassName=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://localhost:3306/school?useUnicode=true&characterEncoding=utf-8
username=****
password=****
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

[![6DWFeI.md.png](https://s3.ax1x.com/2021/03/15/6DWFeI.md.png)](https://imgtu.com/i/6DWFeI)

## 第二十二章 HTML

### 引言

网页，是网站中的一个页面，通常来说，网页是构成网站的基本元素，是承载各种网站应用的平台。通俗的说，网站就是由网页组成的。通常我们看到的网页都是以 `html` 或者 `htm` 后缀结尾的文件，俗称 `HTML` 文件。

### 什么是 HTML

`HTML` 全称：`Hyper Text Markup Language`（超文本标记语言）

* 超文本：页面可以包含图片、链接，甚至是音乐、程序等非文本元素
* 标记：标签，不同的标签实现不同的功能
* 语言：人与计算机的交互工具

### 能做什么

使用标记标签来描述网页，展示信息给用户

### 书写规范

* `HTML` 标签是以**尖括号**包围的**关键字**
* `HTML` 标签通常是成对出现的，有开始就有结束
* `HTML` 标签通常都有属性，格式：属性="属性值"（多个属性之间用空格隔开）
* `HTML` 标签不区分大小写，建议全部小写

### 标签

在网页中具有特殊功能的符号，`HTML` 中所有的标签都以 `<>` 为区分，区分普通文本。

#### 分类

1. 双标签：成对出现，有开始有结束。`<开始标签>标签内容</结束标签>`
2. 单标签：只有开始标签，没有结束标签，可以手动添加 `/` 表示结束。`<标签名> 或者 <标签名/>`

#### 嵌套

1. 在成对的标签中出现其他标签；
2. 嵌套结构中，外层元素称为父元素，内层元素成为子元素

#### 文档结构

1. 新建文档，保存为 `.html/.htm` 格式
2. 书写一对 `html` 标签 `<html></html>`
3. 在 `html` 标签中嵌套一对 `head` 标签
4. 在 `html` 标签中嵌套一对 `body` 标签
5. 为 `body` 标签增加文本内容，内容不限

#### 属性

用来修饰标签的显示效果

##### 语法

1. 属性由属性名和属性值组成：`属性名="属性值"`
2. 属性的申明必须写在开始标签中：`<开始标签 属性名="属性值">...</结束标签>`
3. 每个标签都可以设置多个属性，属性之间使用空格隔开：`<开始标签 属性名="属性值" 属性名="属性值" ...>...</结束标签>`

### 注释

`<!-- 注释内容 -->`

> 1. 注释不能写在标签里面
> 2. 注释不能嵌套

### 换行与空格

`html` 文档会忽略掉多余的空格，只显示为一个空格。如果需要显示多个空格或者 `< >` 等，都需要使用特殊符号代替

### 基本标签

#### 结构标签

```html
<html>:根标签
  <head>:网页头标签
    <title></title>:页面的标题
  </head>
  <body></body>:网页正文
</html>
```

| 属性         | 代码                                   | 描述                         |
| ------------ | -------------------------------------- | ---------------------------- |
| `text`       | &lt;body text="0xf00"></body&gt;       | 设置网页下方中所有文字的颜色 |
| `bgcolor`    | &lt;body bgcolor="#00f"></body&gt;     | 设置网页的背影色             |
| `background` | &lt;body background="1.png"></body&gt; | 设置网页的背影图             |

> 颜色的表示方式：
>
> * 用表示颜色的英文单词，例：`red、blue、green`
> * 用 16 进制表示颜色，例：`#000000， #ffffff`

>注意：背影色和背影图片只能单独出现

#### 排版标签

可用于实现简单的页面布局

##### 注释标签

`<!--注释-->`

##### 换行标签

`<br>`

##### 段落标签

`<p>文本文字</p>`：突出显示一段文本，每一段的文本都独占一行或一块，不与其他元素同行，并且具备垂直的空白距离

* 特点：段与段之间有空行
* 属性
  * `align`：对齐方式，值有：`left、right、center`

##### 水平标签

`<hr/>`

* 属性
  * `width`：水平线的长度，两种表示方式
    * 像素表示
    * 百分比表示
  * `size`：水平线的粗细，使用像素表示，例如：`10px`
  * `color`：水平线的颜色
  * `align`：水平线的对齐方式

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body text="#d2691e" bgcolor="#faebd7">
    <!--换行-->
    换<br>行
    <!--段落-->
    <p>段落一</p>
    <p align="center">段落二</p>
    <p align="right">段落三</p>
    <!--水平线-->
    <hr align="center" width="50%" color="red" size="3">
</body>
</html>
```

#### 块标签

> 使用 css + div 是现下流行的一种布局方式

| 标签   | 代码            | 描述                         |
| ------ | --------------- | ---------------------------- |
| `div`  | `<div></div>`   | 行级块标签，独占一行，换行   |
| `span` | `<span></span>` | 行内块标签，所有内容都在一行 |

#### 基本文字标签（已过时）

<del>`<font></font>`</del>：处理网页中文字的显示方式

| 属性名  | 代码                         | 描述                                 |
| ------- | ---------------------------- | ------------------------------------ |
| `size`  | `<font size="7"></font>`     | 用于设置字体的大小，最小1号，最大7号 |
| `color` | `<font color="#f00"></font>` | 用于设置字体的颜色                   |
| `face`  | `<font face="宋体"></font>`  | 用于设置字体的样式                   |

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>块标签和基本文字标签</title>
</head>
<body>
    <div>div标签1div标签1div标签1<font color="red" size="7">div标签1</font>div标签1div标签1</div>
    <div>div标签2</div>
    <div>div标签3</div>
    <span>span标签1</span>
    <span>span标签2</span>
    <span>span标签3</span>
</body>
</html>
```

> 注意：font 标签是一个闭合标签，如果不写后面的结束标签，那么 font 的样式会从开始标签一直应用到文档的末尾

#### 文本格式化标签

使用标签实现文本的样式处理

| 标签                       | 代码                | 描述     |
| -------------------------- | ------------------- | -------- |
| `b`                        | `<b></b>`           | 粗体标签 |
| `strong`                   | `<strong></strong>` | 加粗     |
| `em`                       | `<em></em>`         | 强调     |
| `i`                        | `<i></i>`           | 斜体     |
| `small`                    | `<small></small>`   | 小号字体 |
| <del>`big`（已过时）</del> | `<big></big>`       | 大号字体 |
| `sub`                      | `<sub></sub>`       | 上标标签 |
| `sup`                      | `<sup></sup>`       | 下标标签 |
| `del`                      | `<del></del>`       | 删除线   |

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>文本格式化标签</title>
</head>
<body>
    <b>粗体</b><strong>粗体</strong>
    <br>
    <em>斜体</em><i>斜体</i>
    <br>
    <big>大号</big><small>小号</small>
    <br>
    上标：5m<sup>2</sup>，下标：H<sub>2</sub>O
    <br>
    <del>删除线</del>
</body>
</html>
```

#### 字符实体

具有实际意义的符号。

| 字符实体 | 表示意义   |
| -------- | ---------- |
| `&nbsp;` | 空格       |
| `&lt;`   | 小于号 `<` |
| `&gt;`   | 大于号 `>` |
| `&copy;` | 版权符号   |
| `&yen;`  | 人民币符号 |

#### 标题标签

可以不同的文字大小和加粗方式显示文本：`<hn></hn>` ，n 取值 1 ~ 6，字体大小依次递减

> 1. 会改变文字的大小并具有加粗效果
> 2. 每个标题都会具备垂直的空白距离
> 3. 每个标题都独占一行，不与其他元素共行显示
> 4. 每个标题都可以添加属性 align，取值：left, right, center，用于设置文本的水平显示位置，默认居左

| 标签 | 代码        | 描述              |
| ---- | ----------- | ----------------- |
| `h1` | `<h1></h1>` | 1号标题，最大字号 |
| `h2` | `<h2></h2>` | 2号标题           |
| `h3` | `<h3></h3>` | 3号标题           |
| `h4` | `<h4></h4>` | 4号标题           |
| `h5` | `<h5></h5>` | 5号标题           |
| `h6` | `<h6></h6>` | 6号标题，最小字号 |

#### 列表标签（清单标签）

##### 无序列表

使用一组无序的符号定义：

```html
<ul>
  <li></li>
  ...
</ul>
```

重要属性：`type`

| 属性值             | 描述     | 用法举例                  |
| ------------------ | -------- | ------------------------- |
| `circle`（默认值） | 空心圆   | `<ul type="circle"></ul>` |
| `disc`             | 实心圆   | `<ul type="disc"></ul>`   |
| `square`           | 黑色广场 | `<ul type="square"></ul>` |

##### 有序列表

使用一组有序的符号定义：

```html
<ol type="a" start="1">
  <li></li>
  ...
</ol>
```

重要属性：`type`

| 属性值        | 描述             | 用法举例                       |
| ------------- | ---------------- | ------------------------------ |
| `1`（默认值） | 数字类型         | `<ol type="1" start="2"></ol>` |
| `A`           | 大写字母类型     | `<ol type="A" start="2"></ol>` |
| `a`           | 小写字母类型     | `<ol type="a" start="2"></ol>` |
| `i`           | 小写罗马字母类型 | `<ol type="i" start="2"></ol>` |
| `I`           | 大写罗马字母类型 | `<ol type="I" start="2"></ol>` |

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>列表</title>
</head>
<body>
    无序列表：<br>
    <ul type="square">
        <li>做真实的自己</li>
        <li>用良心做自己</li>
    </ul>
    有序列表：<br>
    <ol type="i" start="4">
        <li>人生的风景</li>
        <li>就像大海的风景</li>
        <li>有时涌</li>
        <li>有时急</li>
        <li>亲爱朋友你就小心</li>
    </ol>
    嵌套列表：<br>
    <ul type="square">
        <li>做真实的自己
            <ol type="i" start="4">
                <li>人生的风景</li>
                <li>就像大海的风景</li>
                <li>有时涌</li>
                <li>有时急</li>
                <li>亲爱朋友你就小心</li>
            </ol>
        </li>
        <li>用良心做自己</li>
    </ul>
</body>
</html>
```

#### 图形标签

`<img/>`：在页面指定位置处引入一幅图片

| 属性名   | 描述               |
| -------- | ------------------ |
| `src`    | 引入图片的地址     |
| `width`  | 图片的宽度         |
| `height` | 图片的高度         |
| `bordre` | 图片的边框         |
| `align`  | 与图片对齐显示方式 |
| `alt`    | 提示信息           |
| `hspace` | 在图片左右设定空白 |
| `vspace` | 在图片上下设定空白 |

> 注意：width 和 height 只设置一个属性值时，另外一个属性值会按照原始比例进行缩放

```java
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>图片</title>
</head>
<body>
    <p align="center">
        前一行 <br>
        前面的文字<img src="tiger.png" alt="十二生肖--虎" width="500px" align="center" border="5" hspace="50px" vspace="100px">后面的文字
        <br>
        后一行
    </p>
</body>
</html>
```

#### 超链接标签

`<a href=""></a>`：在页面中使用链接标签会跳转到另外一页面

**属性：**

* `href`
  * 跳转页面的地址
  * **跳转到外网时需要添加协议**
* `target`
  * 跳转页面时页面的打开方式
  * 值：
    * `_blank`：在新窗口打开
    * `_self`：在原窗口打开
    * `_parent`：在父窗口打开
    * `_top`：在顶层窗口打开
  * 同一页面中跳转
    * 定义位置：`<a name="名称"></a>`
    * 指向：`<a href="#名称"></a>`

```html
<!doctype html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>链接</title>
</head>
<body>
    <a name="top"></a><p></p> 首页 <a href="demo1.html" target="_blank">跳转另外一个页面</a>
    <br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br>
    <a href="#top">回到顶部</a>
</body>
</html>
```

#### 表格标签

##### 定义表格

* 标签：`table`
* 属性：
  * `width`：表格宽度
  * `border`：表格边框。==table 上的边框设置只能给表格增加边框，不能给单元格添加==
  * `cellpadding`：内容和单元格的距离
  * `cellspacing`：单元格之间的距离。如果指定为0，则单元格的线合为一条
  * `bgcolor`：背影色
  * `align`：对齐方式

##### 定义行

* 标签：`tr`
* 属性：
  * `bgcolor`：背影色
  * `align`：对齐方式

##### 定义单元格

* 标签：`td`
* 属性：
  * `rowspan`：合并行。==在同一列合并多行==
  * `colspan`：合并列。==在同一行合并多列==

##### 其它标签

* `th`：定义表头单元格，内容会有加粗和居中效果
* `caption`：表格标题

行分组

允许将表格中的一行或若干行分为一组，便于管理

1. `<thead>` 表头行分组
2. `<tfoot>` 表尾行分组
3. `<tbody>` 表主体行分组

> 以上这三个标签可以省略，默认情况下，所有的行都会被添加到 tbody 中
>
> 如果需要手动添加分组，建议按照 thead tbody tfoot 的顺序书写

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表格</title>
</head>
<body>
    <table width="500px" height="200px" border="1" align="center" cellspacing="0">
        <caption>学生成绩表</caption>
        <tr>
            <th>编号</th>
            <th>姓名</th>
            <th>性别</th>
            <th>成绩</th>
        </tr>
        <tr>
            <td align="center">1</td>
            <td align="center">杨过</td>
            <td align="center">男</td>
            <td align="center">100</td>
        </tr>
        <tr>
            <td align="center">2</td>
            <td align="center">小龙女</td>
            <td align="center">女</td>
            <td align="center" rowspan="2">90</td>
        </tr>
        <tr>
            <td align="center">3</td>
            <td align="center">金轮法王</td>
            <td align="center">男</td>
        </tr>
        <tr>
            <td align="center">总成绩</td>
            <td align="center" colspan="3">190</td>
        </tr>
    </table>
</body>
</html>
```

### 表单标签

`html` 表单用于收集不同类型的用户输入数据

#### form 元素

本身不可见，但不能省略，因为数据的提交功能要由 `form` 元素完成

```html
<form>
  表单元素
</form>
```

##### 属性

1. `action` ：指定数据提交的目的地址
2. `method` ：数据请求方式 `get/post` 
   1. `get` ：默认值，通常用于向服务器获取数据
      1. 提交的数据会以参数的形式拼接在 `URL` 的后面
      2. 安全性较低
      3. 提交数据最大为 `2kb`
   2. `post` ：将数据提交给服务器处理
      1. 隐式提交，看不到数据提交
      2. 安全性较高
      3. 没有数据大小限制
3. `enctype` ：表示是表单提交的类型
   1. 默认值：`application/x-www-form-unlencoded`，普通表单
   2. `multipart/form-data`：多部分表单（一般用于文件上传）

#### 表单控件 - input

提供与用户交互的可视化组件

> 只有放在表单元素中的表单控件才允许被提交

##### 文本框和密码框

`<input type="text/password">`

1. `name` ：定义当前控件的名称，缺少的话无法提交，提交数据时被当做 `key` 值
2. `value` ：要提交给服务器的值，也是默认显示在控件上的值
3. `maxlength` ：限制用户输入的最大字符数
4. `placeholder` ：用户输入之前显示在框中的提示文本

##### 单选框和复选框

`<input type="radio">` 单选 `<input type="checkbox">` 复选

1. `name` ：定义控件名称，还起到分组的作用，一组中的按钮必须保持一致
2. `value` ：设置当前控件的值，最终提交给服务器
3. `checked` ：设置预选中状态，可以省略属性值，也可以使用 `"checked"` 作为值

##### 日期框

`<input type="date">`

##### 时间框

`<input type="time">`

##### 时间日期框

`<input type="datetime">`

##### 隐藏域

需要提交给服务器但是却不需要呈现给用户的数据，都可以放在隐藏域中 `<input type="hidden">`

1. `name` ：控件的名称
2. `value` ：控件的值

##### 电子邮件

`<input type="email">`

##### 数字输入

`<input type="number">`

##### 电话号码

`<input type="tel">`

##### 取值范围

`<input type="range">`

##### 取色按钮

`<input type="color">`

##### 文件选择

`<input type="file">`

1. `name` ：控件的名称

##### 文本域

`<textarea></textarea>` 支持用户输入多行文本

1. `name` ：控件名称
2. `cols` ：指定文本域默认显示的列数，一行中能显示的英文字符量，中文减半
3. `rows` ：指定文本域能够显示的行数

> 文本域可以由用户调整大小

##### 提交按钮

`<input type="submit">` 将表单数据发送给服务器，不写 `value` 属性，默认显示：提交

##### 重置按钮

`<input type="reser">` 重置表单，将表单内容恢复到初始化状态，不写 `value` 属性，默认显示：重置

##### 普通按钮

`<input type="button" valu="显示本文">` 可以绑定自定义的事件

`<button>按钮显示文本</button>`  该标签可以在任何地方使用；**该标签如果使用在表单中，默认具有提交功能，等同于 `<input type="submit">` **；可以添加 `type` 属性，取值：`submit / reset / button` 进行区分；

##### 图片提交按钮

`<input type="image" src="">`

##### 特殊用法

`<label for="要关联的控件id">男</label><input type="radio" id="male" name="gender" value="male>"` 

#### 表单控件 - select

##### 下拉选择框

```html
<select name="op">
  <option value="o1" selected="selected">选项一</option>
  <option value="o2">选项二</option>
  ...
</select>
```

假设用户选择选项一，在使用 `get` 方式提交数据时，`URL` 拼接后的数据应为：`op=o1`

**多选列表：**`<select multiple="multiple"></select>`

#### 表单控件 - textarea

**多行文本域**

```html
<textarea cols="列" rows="行">
  内容
</textarea>
```

#### 表单综合练习

[![6HEdRs.png](https://z3.ax1x.com/2021/03/23/6HEdRs.png)](https://imgtu.com/i/6HEdRs)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>表单练习</title>
</head>
<body>
    <form action="result.html" method="get">
        <p>
            姓名：<input type="text" name="name" width="120px">
        </p>
        <p>
            密码：<input type="password" name="password" width="120px">
        </p>
        <p>
            重复密码：<input type="password" name="repassword" width="120px">
        </p>
        <p>
            性别：<input type="radio" name="sex" value="male" checked>男<input type="radio" name="sex" value="femal">女
        </p>
        <p>
            兴趣：<input type="checkbox" name="hobby" value="study" checked>学习<input type="checkbox" name="hobby" value="program">编程<input type="checkbox" name="hobby" value="work">工作
        </p>
        <p>
            生日：<input type="date" name="birthday">
        </p>
        <p>
            薪水：<input type="number">
        </p>
        <p>
            学历：
            <select multiple="multiple" name="profession">
                <option value="1">大专</option>
                <option value="2">本科</option>
                <option value="3">硕士</option>
                <option value="4">博士</option>
            </select>
        </p>
        <p>
            简介：<textarea name="info" id="info" cols="30" rows="10">这个家伙很懒，什么都没有留下...</textarea>
        </p>
        <p>
            <input type="submit" value="提交">
        </p>
    </form>
</body>
</html>
```

### 框架标签

通过使用框架，你可以在同一个浏览器窗口中显示不止一个页面。每份 `HTML` 文档称为一个框架，并且每个框架都独立于其他的框架

使用框架的缺点：

* 开发人员必须同时跟踪更多的 `HTML` 文档
* 很难打印整张页面

#### 框架结构标签 - frameset

* 框架结构标签：`<frameset></frameset>`，用于定义如何将窗口分割为框架
* 每个 `frameset` 标签定义了一系列行或列
* `rows/columns` 的值规定了每行或每列占据屏幕的面积
  * `<frameset rows="" cols=""></frameset>`

#### 框架标签 - frame

每个 `frame` 引入一个 `html` 页面

```html
<frameset clos="*,*">
  <frame src="info1.html" />
  <frmae src="info2.html" />
</frameset>
```

#### 基本的注意事项

* 不能将 `<body></body>` 标签与 `<frameset></frameset>` 标签同时使用
* 假如一个框架有可见边框，用户可以手动边框来改变它的大小。为了避免这种情况发生，可以在 `<frame>` 标签中加入：`noresize="noresize"`

## 第二十三章 CSS

### 1. 简介

#### 1.1 什么是 CSS

* `CSS（Cascading Style Sheets）`：层叠样式表，定义如何显示 `HTML` 元素
* 多个样式可以层层覆盖叠加，如果不同的 `css` 样式对同一 `html` 标签进行修饰，样式有冲突的，应用优先级高的，不冲突的共同作用

#### 1.2 CSS 能干什么

* 修饰美化 `html` 网页
* 外部样式表可以提高代码利用性从而提高工作效率
* `html` 内容与样式表现分离，便于后期维护

#### 1.3 CSS 书写规范

`CSS` 规则由两个主要的部分构造：选择器，以及一条或多条声明：

* 选择器通常是需要改变样式的 `HTML` 元素

* 每条声明由一个属性和一个值组成

#### 1.4 基础语法：选择器：{属性: 值, 属性: 值, ...}

[![cpid1K.md.png](https://z3.ax1x.com/2021/03/28/cpid1K.md.png)](https://imgtu.com/i/cpid1K)

注意事项：

* 请使用花括号来包围声明
* 如果值为若干单词，则要给值加引号
* 多个声明之间使用分号隔开
* `css` 对大小写不敏感，如果涉及到与 `html` 文档一起使用时，`class` 与 `id` 名称对大小写敏感

### 2. 导入方式

#### 2.1 内嵌方式（内联方式）

把 `css` 样式嵌入到 `html` 标签中，类似属性的用法：

```html
<div style="color: blue; font-size: 50px;">这是一个内容</div>
```

#### 2.2 内部方式

在 `head` 标签中使用 `style` 标签引入 `css` 样式：

```html
<style type="text/css"> <!--告诉浏览器使用 CSS 解析器去解析-->
  div {color: red; fonnt-size: 50px;}
</style>
```

#### 2.3 外部方式

将 `css` 样式抽成一个单独文件，使用者直接引用：

```html
创建单独文件：div.css
内容：div{color: green; font-size: 50px;}
引用语句写在 head 内部：
	<link rel="stylesheet" type="text/css" href="div.css"/>
	rel：代表当前页面与 href 所指定文档的关系
	type: 文件类型，告诉浏览器使用 css 解析器去解析
	href: css 文件地址
```

#### 2.4 @import 方式

在页面中引入一个独立的单独文件：

```html
<style type="text/css">
  @import url("div.css")
</style>
```

> link 与 @import 方式的区别：
>
> * link 所有浏览器都支持，@import 某些版本低的 IE 浏览器不支持
> * @import 是等待 html 加载完成才加载
> * @import 是不支持 js 动态修改

### 3. CSS选择器

主要用于选择待添加样式的 `html` 元素

#### 3.1 基本选择器

##### 元素选择器

在 `head` 中使用 `style` 标签，在其中声明元素选择器，语法：`html标签名 {属性: 属性值;...}`

```html
<style type="text/css">
  span {color: red; font-size: 20px;}
</style>
```

##### id 选择器

给需要修改样式的 `html` 元素添加 `id` 属性标识，在 `head` 中使用 `style` 标签，在其中声明 `id` 选择器，语法：`#id值 {属性: 属性值;...}`

```html
<!-- 创建 id 选择器 -->
<div id="d1">这是第一段</div>
<div id="d2">这是第二段</div>
<div id="d3">这是第三段</div>
<!-- 根据 id 选择器进行 html 文件修饰 -->
<style type="text/css">
  #d1 {color: red;}
  #d2 {color: green;}
  #d3 {color: blue;}
</style>
```

##### class 选择器

给需要修改样式的 `html` 元素添加 `class` 属性标识，在 `head` 中使用 `style` 标签，在其中声明 `class` 选择器：`.class名 {属性: 属性值;...}`

```html
<!--创建 class 选择器-->
<div class="d1">这是第一段</div>
<div class="d2">这是第二段</div>
<div class="d3">这是第三段</div>
<!--根据 class 选择器进行 html 文件修饰-->
<style type="text/css">
  .d1 {color: red;}
  .d2 {color: green;}
  .d3 {color: blue;}
</style>
```

> [以上基本选择器的优先级从高到低分别是：id 选择器，class 选择器，元素选择器]()

#### 3.2 属性选择器

* 根据元素的属性及属性的值来选择元素，在 `head` 中使用 `style` 标签引入在其中声明
* 格式为：
  * `html标签名[属性='属性值']{css属性: css属性值}`
  * `html标签名[属性]{css属性：css属性值}`

```html
<!--body 内容-->
<form action="#" name="login" method="get">
  <font size="3">用户名：</font>
  <input type="text" name="username" value="张三">
  <font size="3">密码：</font>
  <input type="password" name="password" value="123456">
  <input type="submit" value="登录">
</form>
<!--head 中书写-->
<style type="text/css">
  input[type='text'] {background-color: pink;}
  input[type='password'] {background-color: yellow;}
  font[size] {color: green;}
  a[href] {color: blue;}
</style>
```

#### 3.3 伪元素选择器

* 主要针对 `a` 标签
* 语法
  * 静止状态：`a:link {css属性：css属性值}`
  * 悬浮状态：`a:hover {css属性：css属性值}`
  * 触发状态：`a:active {css属性：css属性值}`
  * 完成状态：`a:visited {css属性：css属性值}`

```html
<!--代码-->
<a href="http://www.baidu.com">百度</a>
<!--样式-->
<style>
  /*静止状态*/
  a:link {color: red;}
  /*悬浮状态*/
  a:hover {color: green;}
  /*触发状态*/
  a:active {color: yellow;}
  /*完成状态*/
  a:visited {color: blue;}
</style>
```

#### 3.4 层级选择器

父级选择器 子级选择器 ……

```html
<div id="div1">
  <div class="div11">
    <span>span1-1</span>
  </div>
  <div class="div12">
    <span>span1-2</span>
  </div>
</div>
<div class="div2">
  <div id="div21">
    <span>span2-1</span>
  </div>
  <div id="div22">
    <span>span2-2</span>
  </div>
</div>
<style>
  #div1 .div11 {color: red;}
  #div1 .div12 {color: purple;}
  .div2 #div21 {color: green;}
  .div2 #div22 {color: blue;}
</style>
```

### 4. 属性

#### 4.1 文字属性

| 属性名        | 取值                              | 描述     |
| ------------- | --------------------------------- | -------- |
| `font-size`   | 数值                              | 字体大小 |
| `font-family` | 默认、宋体、楷体等                | 字体样式 |
| `font-style`  | `normal` 正常；`italic` 斜体      | 斜体样式 |
| `font-weight` | `100-900`数值；`bold`；`bolder`； | 粗体样式 |

#### 4.2 文本属性

| 属性名            | 取值                                                 | 描述                 |
| ----------------- | ---------------------------------------------------- | -------------------- |
| `color`           | 十六进制；表示颜色的英文单词                         | 设置文本颜色         |
| `text-indent`     | 像素：缩进 x像素；百分比：缩进父容器宽度的 x%        | 缩进元素中文本的首行 |
| `text-decoration` | `none；underline；overline；blink；`                 | 文本的装饰线         |
| `text-align`      | `left；righht；center`                               | 文本水平对齐方式     |
| `word-spacing`    | `normal`；固定值                                     | 单词之间的间隔       |
| `line-height`     | `normal`；固定值                                     | 设置文本的行高       |
| `text-shadow`     | 四个取值依次是：水平偏移；垂直偏移；模糊值；阴影颜色 | 阴影及模糊效果       |

#### 4.3 背影属性

| 属性名                | 取值                                 | 描述               |
| --------------------- | ------------------------------------ | ------------------ |
| `background-color`    | 16进制；用于表示颜色的英语单词       | 背景色             |
| `background-image`    | `url('图片路径')`                    | 背景图片           |
| `background-repeat`   | `repeat-y;repeat-x;repeat;no-repeat` | 背景图的平铺方向   |
| `background-position` | `top;bottom;left;right;center`       | 图像在背景中的位置 |

#### 4.4 列表属性

| 属性名                | 取值               | 描述                             |
| --------------------- | ------------------ | -------------------------------- |
| `list-style-type`     | `disc` 等          | 列表的标识类型                   |
| `list-style-image`    | `url('图片地址')`  | 用图像表示标识                   |
| `list-style-position` | `inside；outsidee` | 标识出现在列表项内容之外还是内部 |

#### 4.5 尺寸属性

* `width`：设置元素的宽度
* `height`：设置元素的高度

#### 4.6 显示属性

`display`：

* `none`：不显示
* `block`：块级显示
* `inline`：行级显示

#### 4.7 轮廓属性

绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用

| 属性名          | 取值                                     | 描述       |
| --------------- | ---------------------------------------- | ---------- |
| `outline-style` | `solid-实线；dotted-虚线；dashed-破折线` | 轮廓的样式 |
| `outline-color` | 16进制；用于表示颜色的英文单词           | 轮廓的颜色 |
| `outline-width` | 数值                                     | 轮廓的宽度 |

#### 4.8 浮动属性

`float`

* 浮动的元素可以向左或者向右移动，直到它的外边缘碰到包含框或者另一个浮动框的边框为止。由于浮动框不在文档的普通流中，所以文档的普通流中的块框表现的就像浮动框不存在一样

[![cpUg10.md.png](https://z3.ax1x.com/2021/03/28/cpUg10.md.png)](https://imgtu.com/i/cpUg10)

下图中：

* 当框1向左浮动时，它脱离文档流并且向左移动，直到它的边缘碰到包含框的左边缘，因为它不再处于文档流中，所以它不占据空间，实际上覆盖住了框2，使框2从视图中消失
* 如果把3个框都向左移动，那么框1向左浮动直到碰到包含框，另外两个框向左浮动直到碰到前一个浮动框

[![cpaVHg.md.png](https://z3.ax1x.com/2021/03/28/cpaVHg.md.png)](https://imgtu.com/i/cpaVHg)



下图中：

* 如果包含框太窄，无法容纳水平排列的三个浮动元素，那么其它浮动块向下移动，直到有足够的空间
* 如果浮动元素的高度不同，那么当它们向下移动时，可能被其它浮动元素 “卡住”

[![cpaxMV.md.png](https://z3.ax1x.com/2021/03/28/cpaxMV.md.png)](https://imgtu.com/i/cpaxMV)

##### clear 属性

规定元素的哪一侧不允许其他浮动元素

| 取值      | 描述                                  |
| --------- | ------------------------------------- |
| `left`    | 在左侧不允许浮动元素                  |
| `right`   | 在右侧不允许浮动元素                  |
| `both`    | 在左右两侧均不允许浮动元素            |
| `none`    | 默认值。允许浮动元素出现在两侧        |
| `inherit` | 规定应该从父元素继承 `clear` 属性的值 |

#### 4.9 定位属性

**相对定位（relative）：**元素框偏移某个距离，元素仍保持其未定位前的形状，它原本所占有的空间仍保留

```html
<head>
    <meta charset="UTF-8">
    <title>相对定位</title>
    <style>
        h2.post-left {position: relative; left: -20px;}
        h2.post-right {position: relative; left: 20px;}
    </style>
</head>
<body>
    <h2>这是位于正常位置的标题</h2>
    <h2 class="post-left">这个标题相对于其正常位置向左移动</h2>
    <h2 class="post-right">这个标题相对于其正常位置向右移动</h2>
    <p>相对定位会按照元素的原始位置对该元素进行移动</p>
    <p>样式 "left: -20px" 从元素的原始左侧位置减去 20px</p>
    <p>样式 "left: 20px" 向元素的原始左侧位置增加 20px</p>
</body>
```

**绝对定位（absolute）：** **元素框从文档流完全删除**，并相对于其包含块进行定位。包含块可能是文档中的另一个元素或者是初始包含块。元素碑在正常文档流中所占有的空间会关闭，就好像元素原来不存在一样。元素定位后生成一个**块级框**

```html
<head>
    <meta charset="UTF-8">
    <title>绝对定位</title>
    <style>
        h2.pos-abs {position: absolute; left: 100px; top: 150px;}
    </style>
</head>
<body>
    <h2 class="pos-abs">这是带有绝对定位的标题</h2>
    <p>通过绝对定位，元素可以放置到页面上的任何位置。下面的标题距离页面左侧 100px，距离页面顶部 150px</p>
</body>
```

**固定定位（fixed）：**元素框的表现类似于将 `position` 设置为 `absolute`，不过其包含块是视窗本身

```html
<head>
    <meta charset="UTF-8">
    <title>固定定位</title>
    <style>
        h2 {position: fixed; left: 0px; top: 0px;}
    </style>
</head>
<body>
    <h2>本段落内容的位置不会随着滚动条的滚动而改变，会始终位于左上角，巍然不动！</h2>
    <h3>我是一个正常的标题，滚着滚着就不见了！</h3>
    <br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br>
    <br><br><br><br><br><br><br><br><br><br>
</body>
```

### 5. CSS 盒模型

[![cph9eJ.md.jpg](https://z3.ax1x.com/2021/03/28/cph9eJ.md.jpg)](https://imgtu.com/i/cph9eJ)

#### 5.1 边框相关属性

| 属性名         | 取值                           | 描述       |
| -------------- | ------------------------------ | ---------- |
| `border-style` | `solid;double;dashed;dotted`等 | 边框的样式 |
| `border-color` | 16进制；用于表示颜色的英文     | 边框的颜色 |
| `border-width` | 数值                           | 边框的粗细 |

#### 5.2 外边距相关属性

`margin`：外边距，边框和边框外层的元素的距离

| 属性名          | 取值                 | 描述           |
| --------------- | -------------------- | -------------- |
| `margin`        | 数值，顺序：上右下左 | 四个方向的距离 |
| `margin-top`    | 数值                 | 上间距         |
| `margin-bottom` | 数值                 | 下间距         |
| `margin-left`   | 数值                 | 左间距         |
| `margin-right`  | 数值                 | 右间距         |

## 第二十四章 Servlet

### 1. 引言

#### 1.1 C/S 架构和 B/S 架构

这是在软件发展过程中出现的两种软件架构方式

#### C/S 架构（Client/Server：客户端/服务器）

* 特点：必须在客户端安装特定软件
* 优点：图形效果显示较好（如：3D 游戏）
* 缺点：服务器的软件和功能进行升级，客户端也必须升级，不利于维护
* 常见的 `C/S` 程序：`QQ`、微信等

[![cpI2nS.md.png](https://z3.ax1x.com/2021/03/28/cpI2nS.md.png)](https://imgtu.com/i/cpI2nS)

#### 1.3 B/S 架构（Browser/Server 浏览器/服务器）

* 特点：无需安装客户端，任何浏览器都可直接访问
* 优点：涉及到功能的升级，只需要升级服务器端
* 缺点：图形显示效果不如 `C/S` 架构
* 需要通过 `HTTP` 协议访问

[![cpofKK.md.png](https://z3.ax1x.com/2021/03/28/cpofKK.md.png)](https://imgtu.com/i/cpofKK)

### 2. 服务器

#### 2.1 概念

##### 什么是 Web

`Web（World Wide Web）` 称为万维网，简单理解就是网站，它用来表示 `Internet` 主机上供外界访问的资源

`Internet` 上供外界访问的资源分为两大类：

* 静态资源：指 `web` 页面中供人们浏览的数据始终是不变的（`HTML、CSS`）
* 动态资源：指 `web` 页面中供人们浏览的数据是由程序产生的，不同时间点，甚至不同设备访问 `Web` 页面看到的内容各不相同（`JSP/Servlet`）
* 在 `Java` 中，动态 `web` 资源开发技术我们统称为 `Java Web`

##### 什么是 web 服务器

`web` 服务器是运行及发布 `web` 应用的容器，只有将开发的 `web` 项目放置到该容器中，才能使网络中的所有用户通过浏览器进行访问

#### 2.2 常用服务器

* 开源：`OpenSource`（1. 开放源代码；2. 免费；）
  * `Tomcat`：主流服务器之一，适合初学者
  * `jetty`：淘宝，运行效率比 `Tomcat` 高
  * `resin`：新浪，所有开源服务器软件中，运行效率最高的
  * 三者的用法从代码角度完全相同，只有在开启、关闭服服务器软件时对应的命令稍有区别，掌握一个即掌握所有
* 收费
  * `WebLogic`：`Oracle`
  * `WebSphere`：`IBM`
  * 提供相应的服务与支持，软件大，耗资源

#### 2.3 Tomcat

`Tomcat` 是 `Apache` 软件基金会（`Apache Software Foundation）` 的 `Jakarta` 项目中的一个核心项目，免费开源、并支持 `Servlet` 和 `JSP` 规范。目前 `Tomcat` 最新版本为 `9.0`

`Tomcat` 技术先进、性能稳定，深受 `Java` 爱好者喜爱并得到了部分软件开发商的认可，成为目前比较流行的 `Web` 应用服务器

#### 2.4 Tomcat 安装

##### 下载

[官网下载](http://tomcat.apache.org) 下载一个解压缩版本即可

##### 解压安装

将 `Tomcat` 解压到一个没有特殊符号的目录中（一般纯英文即可）

> 注意：
>
> 1. 不建议将服务器软件放在磁盘层次很多的文件夹
> 2. 不建议放在中文路径下

##### 目录结构

| 文件夹    | 说明                                                         | 备注                                                         |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| `bin`     | 该目录下存放的是二进制可执行文件                             | `startup.sh` 启动 `Tomcat`、`shutdown.sh` 停止 `Tomcat`      |
| `conf`    | 这是一个非常重要的目录，这个目录下有两个最为重要的文件 `server.xml` 和 `web.xml` | `server.xml`：配置整个服务器信息，例如修改商品号、编码格式等<br />`web.xml`：项目部署描述符文件，这个文件中注册了很多 `MIME` 类型，即文档类型 |
| `lib`     | `Tomcat` 的类库，里面存放 `Tomcat` 运行所需要的 `jar` 文件   |                                                              |
| `logs`    | 存放上场文件，记录了 `Tomcat` 启动和关闭的信息。如果启动 `Tomcat` 时有错误，异常也会记录在日志文件中 |                                                              |
| `temp`    | `Tomcat` 的临时文件，这个目录下的东西在停止 `Tomcat` 后删除  |                                                              |
| `webapps` | 存放 `web` 项目的目录，其中每个文件夹老师一个项目；其中 `ROOT` 是一个特殊的项目，在地址栏中没有给出项目目录时，对应的就是 `ROOT` 项目 |                                                              |
| `work`    | 运行时生成的文件，最终运行的文件都在这里                     | 当客户端用户访问一个 `JSP` 文件时，`Tomcat` 会通过 `JSP` 生成 `Java` 文件，然后再编译 `Java` 文件生成 `.class` 文件，生成的 `Java` 文件和 `class` 文件都会放在这个目录下 |

#### 2.5 Tomcat 启动和停止

* 使用命令行进入 `Tomcat` 的 `bin` 目录下
* 输入命令：`sudo chmod 755 *.sh`，设置权限
* 输入命令：`sudo sh startup.sh` 启动 `Tomcat`
* 验证：在浏览器中输入 `localhost:8080` 看到 `Tomcat` 主页即为成功
* 输入命令：`sudo sh shutdown.sh` 关闭 `Tomcat`

##### 修改端口号

`Tomcat` 默认端口号为 `8080`，可以通过 `conf/server.xml` 文件修改：

```xml
<Connector port="8080" protocol="HTTP/1.1"
               connectionTimeout="20000"
               redirectPort="8443" />
```

> 注意：修改端口号需要重启 Tomcat 才能生效

#### 2.6 部署项目及访问静态资源

`Tomcat` 是 `web` 服务器，我们的项目应用是部署在 `webapps` 下，然后通过特定的 `url` 访问

##### 创建项目

* 在 `webapps` 中建立文件夹（项目应用），比如：`myweb`
  * 创建 `WEB-INF` 文件夹，用于存放项目的核心内容
    * 创建 `classes` 文件夹，用于存放 `.class` 文件
    * 创建 `lib`，用于存放 `jar` 文件
    * 创建 `web.xml`，项目配置文件（到 `ROOT` 项目下的 `WEB-INF` 复制即可）
  * 把网页 `hello.html` 复制到 `myweb` 文件夹中，与 `WEB-INF` 在同级目录

##### 通过 URL 访问资源

在地址栏中输入：`http://localhost:8081/myweb/hello.html`

> URL 主要有四部分组成：协议、主机、端口、资源路径

[![cpOryn.md.png](https://z3.ax1x.com/2021/03/28/cpOryn.md.png)](https://imgtu.com/i/cpOryn)

##### Tomcat 响应流程图

[![cpjrV0.md.png](https://z3.ax1x.com/2021/03/28/cpjrV0.md.png)](https://imgtu.com/i/cpjrV0)

#### 2.7 常见错误

##### Tomcat 闪退

闪退问题是由于 `JAVA_HOME` 配置导致的，检查该配置是否合适

##### 404

访问资源不存在，出现 `404` 错误

### 3. Servlet【重点】

#### 3.1 概念

* `Servlet（Server Applet）`：是服务端的程序（代码、功能实现），可交互式的处理客户端发送到服务端的请求，并完成操作响应
* 动态网页技术
* `JavaWeb` 程序开发的基础，`JavaEE` 规范（一套接口）的一个组成部分

##### Servlet 作用

* 接收客户端请求，完成操作
* 动态生成网页（页面数据可变）
* 将包含操作结果的动态网页响应给客户端

#### 3.2 Servlet 开发步骤

##### 搭建开发环境

将 `Servlet` 相关的 `jar` 包（`lib/servlet-api.jar`）配置到 `classpath` 中

##### 编写 Servlet

* 实现 `javax.servlet.Servlet`
* 重写 5 个重要方法
* 在核心的 `service()` 方法中编写输出语句，打印访问结果

```java
import javax.servlet.Servlet;
import javax.servlet.ServletConfig;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;
import java.io.IOException;


public class MyServlet implements Servlet {
	
	public void init(ServletConfig servletConfig) throws ServletException {
	}

	public void service(ServletRequest request, ServletResponse response) throws ServletException, IOException {
		System.out.println("Hello Servlet!");
	}

	public void destroy() {
	}

	public ServletConfig getServletConfig() {
		return null;
	}
	
	public String getServletInfo() {
		return null;
	}
}
```

##### 部署 Servlet

编译 `MyServlet` 后，将生成的 `class` 文件放在 `WEB-INF/classes` 文件夹中

##### 配置 Servlet

编写 `WEB-INF` 下项目配置文件 `web.xml`

```xml
<servlet>
  <servlet-name>my</servlet-name>
  <servlet-class>MyServlet</servlet-class>
</servlet>

<servlet-mapping>
  <servlet-name>my</servlet-name>
  <url-pattern>/myservlet</url-pattern>
</servlet-mapping>
```

> url-pattern 配置的内容就是浏览器地址栏输入的 URL 中项目名称后资源的内容

#### 3.3 运行测试

启动 `Tomcat`，在地址栏中输入：[http://localhost:8080/myweb/myservlet]() 进行访问，在控制台中会打印出刚刚编写的输出语句，即为成功

#### 3.4 常见错误

##### 500

服务端出现异常

### 4. 使用 IDAE 创建 Web 项目

#### 4.1 创建项目

`File -> New -> Project -> Java Enterprise`，具体配置如下图所示：

[![c9Jzgf.md.png](https://z3.ax1x.com/2021/03/29/c9Jzgf.md.png)](https://imgtu.com/i/c9Jzgf)

##### 目录说明

* `src`：存放 `Java` 代码
* `web`：存放静态资源
  * `WEB-INF`：项目配置文件，`jar` 包和 `class` 文件
* `External Libraries`：外部 `jar`

#### 4.2 开发 Servlet

##### 编写 Servlet

```java
import javax.servlet.Servlet;
import javax.servlet.ServletConfig;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;
import java.io.IOException;


public class MyServlet implements Servlet {
	
	public void init(ServletConfig servletConfig) throws ServletException {
	}

	public void service(ServletRequest request, ServletResponse response) throws ServletException, IOException {
		System.out.println("Hello Servlet!");
	}

	public void destroy() {
	}

	public ServletConfig getServletConfig() {
		return null;
	}
	
	public String getServletInfo() {
		return null;
	}
}
```

##### 配置 Servlet

```xml
<servlet>
  <servlet-name>my</servlet-name>
  <servlet-class>MyServlet</servlet-class>
</servlet>

<servlet-mapping>
  <servlet-name>my</servlet-name>
  <url-pattern>/myservlet</url-pattern>
</servlet-mapping>
```

##### 部署 Web 项目

在 `Tomcat` 的 `webapps` 目录下，新建 `anotherproject` 项目文件夹

* 创建 `WEB-INF` 目录，存放核心文件
* 在 `WEB-INF` 目录下，创建 `classes` 文件夹，将编译后的 `MyServlet.class` 文件复制到这里

> [问题：每当我们编写了新的 Servlet 或者重新编译，都需要手工将新的 .class 部署到 Tomcat 中，非常麻烦，如何实现自动部署？]()

#### 4.3 部署 Web 项目

没有使用 `IDEA` 时，需要手动将文件拷贝到相应的目录下，使用了 `IDEA` 就不再需要手动做这些操作了，可以通过 `IDEA` 集成 `Tomcat` 服务器，实现自动部署

##### 集成 Tomcat

* `Preferences -> Build,Execution,Deployment -> Application Servers`
* 点击中间面板的 `+` 号
* 在 `Add application server` 面板中，选择 `Tomcat Server`
* 在 `Tomcat Server` 面板中，选择下载的 `Tomcat` 的解压地址，确定即可

##### 项目部署 Tomcat

选择 `Run/Debug Configurations`

[![c9hmDg.md.png](https://z3.ax1x.com/2021/03/29/c9hmDg.md.png)](https://imgtu.com/i/c9hmDg)

[![c9hBP1.md.png](https://z3.ax1x.com/2021/03/29/c9hBP1.md.png)](https://imgtu.com/i/c9hBP1)



#### 4.4 其它操作

##### 关联第三方 jar 包

* 在 `WEB-INF` 目录下新建 `lib` 目录
* 复制 `jar` 包到 `lib` 目录中
* 右击 `lib` 目录，选择 `Add as Library`
* 选择 `Project Library`，完成
  * `Global Library` ：表示所有工程都可以使用
  * `Project Library`：表示当前工程中所有模块都可以使用
  * `Module Library`：表示当前模块可以使用

##### 导出 war 包

项目完成后，有时候需要打成 `war` 方便部署。`war` 包可以直接放入 `Tomcat` 的 `webapps` 目录中，启动 `Tomcat` 后自动解压，即可访问

* 点击项目结构：`File -> Project Structure`
* 选择 `Artifacts`
* 点击 `+` 号
* 选择 `Web Application: Archive`
* 选择 `for ...`
* 构建项目：`Build -> Build Artifacts`
* 选择 `xx war -> build`
* 就会在项目的  `out/artifacts/` 目录下生成所需要的 `war` 包

### 5. HTTP 协议

#### 5.1 什么是 HTTP

超文本传输协议（`HTTP，HyperText Transfer Protocol`）是互联网上应用最为广泛的一种网络协议，是一个基于请求与响应模式的、无状态的、应用层的协议，运行于 `TCP` 协议基础之上。

#### 5.2 HTTP 协议特点

* 支持客户端（浏览器）/服务器模式
* 简单快速：客户端只向服务器发送请求方法和路径，服务器即可响应数据，因而通信速度很快。请求访求常用的有 `GET、POST` 等
* 灵活：`HTTP` 允许传输任意类型的数据，传输的数据类型由 `Content-Type` 标识
* 无连接：无连接指的是每次 `TCP` 连接只处理一个或多个请求，服务器处理完客户的请求后，即断开连接，采用这种方式可以节省传输时间
  * `HTTP1.0` 版本是一个请求响应之后，直接就断开了，称为短连接
  * `HTTP1.1` 版本不是响应后直接就断开了，而是等几秒钟，这几秒钟之内有新的请求，那么还是通过之前的连接通道来收发消息，如果过了这几秒钟用户没有发送新的请求，就会断开连接，称为长连接
* 无状态：`HTTP` 协议是无状态协议
  * 无状态是指协议对于事务处理没有记忆能力

#### 5.3 HTTP 协议通信流程

* 客户与服务器建立连接（三次握手）
* 客户向服务器发送请求
* 服务器接受请求，并根据请求返回相应的文件作为应答
* 客户与服务器关闭连接（四次挥手）

[![cCKSy9.md.png](https://z3.ax1x.com/2021/03/29/cCKSy9.md.png)](https://imgtu.com/i/cCKSy9)

#### 5.4 请求报文和响应报文【了解】

##### HTTP 请求报文

当浏览器向 `Web` 服务器发出请求时，它向服务器传递了一个数据块，也就是请求信息（请求报文），`HTTP` 请求信息由 4 部分信息组成：

1. 请求行：请求方法/地址 `URI` 协议/ 版本
2. 请求头：（`Request Header`）
3. 空行
4. 请求正文

[![cCK5tK.md.png](https://z3.ax1x.com/2021/03/29/cCK5tK.md.png)](https://imgtu.com/i/cCK5tK)

##### HTTP 响应报文

`HTTP` 响应报文与 `HTTP` 请求报文相似：

1. 状态行
2. 响应头
3. 空行
4. 响应正文

[![cCQSV1.md.png](https://z3.ax1x.com/2021/03/29/cCQSV1.md.png)](https://imgtu.com/i/cCQSV1)

#### 5.3 常见状态码

| 状态代码 | 状态描述              | 说明                                                         |
| -------- | --------------------- | ------------------------------------------------------------ |
| 200      | OK                    | 客户端请求成功                                               |
| 302      | Found                 | 临时重定向                                                   |
| 403      | Forbidden             | 服务器收到请求，但是拒绝提供服务。服务器通常会在响应正文中给出不提供服务的原因 |
| 404      | Not Found             | 请求的资源不存在                                             |
| 500      | Internal Server Error | 服务器发生不可预期的错误，导致无法完成客户端的请求           |

### 6. Servlet 核心接口和类

#### 6.1 核心接口和类

在 `Servlet` 体系结构中，除了实现 `Servlet` 接口，还可以通过继承 `GenericServlet` 或 `HttpServlet` 类，完成编写

##### 接口

在 `Servlet API` 中最重要的是 `Servlet` 接口，所有 `Servlet` 都会直接或间接的与该接口发生联系，或是直接实现该接口，或间接继承自实现了该接口的类。

该接口包括以下五个方法：

```java
void init(ServletConfig config);
ServletConfi getServletConfig();
service(ServletRequest req, ServletResponse res);
String getServletInfo();
void destroy();
```

##### GenericServlet 抽象类

`GnenricServlet` 使编写 `Servlet` 变得更容易。它提供生命周期方法 `init` 和 `destroy` 的简单实现，要编写一般的 `Servlet`，只需要重写抽象 `service` 方法即可

##### HttpServlet 类

`HttpServlet` 是继承 `GenericServlet` 的基础上进一步的扩展

提供将要被子类化以创建适用于 `Web` 站点的 `HTTP Servlet` 的抽象类。`HttpServlet` 的子类至少必须重写一个方法，该方法通常是以下这些方法之一：

* `doGet`：如果 `Servlet` 支持 `HTTP GET` 请求
* `doPost`：如果 `Servlet` 支持 `HTTP POST` 请求
* `doPut`：如果 `Servlet` 支持 `HTTP PUT` 请求
* `doDelete`：如果 `Servlet` 支持 `HTTP DELETE` 请求

#### 6.2 Servlet 两种创建方式

##### 实现接口 Servlet

```java
public class MyServlet implements Servlet {
    @Override
    public void init(ServletConfig servletConfig) throws ServletException {

    }

    @Override
    public ServletConfig getServletConfig() {
        return null;
    }

    @Override
    public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException {
        System.out.println("Hello Servlet!");
    }

    @Override
    public String getServletInfo() {
        return null;
    }

    @Override
    public void destroy() {

    }
}
```

> 该方法比较麻烦，需要实现接口中全部的 5 个方法

##### 继承 HttpServlet【推荐】

```java
public class HelloServlet extends HttpServlet {

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("这是通过 get 请求过来的！");
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("这是通过 post 请求过来的！");
    }
}
```

##### 常见错误

* `HTTP Status 404` ：资源找不到
  * 第一种情况：地址书写错误
  * 第二种情况：地址没有问题，把 `IDEA` 项目中 `out` 目录删除，然后重新运行
* `Servlet` 地址配置重复：`both mapped to the url-pattern [xxx] which is not permitted`
* `Servlet` 地址配置错误：比如没有写 `/`，`Invalid <url-pattern> [helloservlet2] in servlet mapping`

#### 6.3 Servlet 两种配置方式

##### 使用 web.xml（Servlet 2.5 之前使用）

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">

    <servlet>
        <servlet-name>my</servlet-name>
        <servlet-class>com.ch.wchya.servlet.MyServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>my</servlet-name>
        <url-pattern>/my</url-pattern>
    </servlet-mapping>

    <servlet>
        <servlet-name>hello</servlet-name>
        <servlet-class>com.ch.wchya.servlet.HelloServlet</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>hello</servlet-name>
        <url-pattern>/hello</url-pattern>
    </servlet-mapping>

</web-app>
```

###### url-pattern 取值说明

* 精确匹配：`/具体的名称`，只有 `url` 路径是具体的名称的时候才会触发 `Servlet`
* 后缀匹配：`*.xxx`，只要是以 `xxx` 结尾的就匹配触发 `Servlet`
* 通配符匹配：`/*`，匹配所有请求，包含服务器的所有资源。`注意：并不会影响精确匹配和后缀匹配`
* 通配符匹配：`/`，匹配所有请求，包含服务器的所有资源，不包括 `.jsp`

###### load-on-startup 属性说明

* 标记容器是否应该在 `web` 应用程序启动的时候就加载这个 `servlet`
* 它的值必须是一个整数，表示 `Servlet` 被加载的先后顺序
* 如果该元素的值为负数或者没有设置，则容器会当 `servlet` 被请求时再加载
* 如果值为正整数或者 0 时，表示容器在应用启动时就加载并初始化这个 `servlet`，值越小，`servlet` 的优先级越高，就越先被加载。值相同时，容器就会自己选择顺序来加载

> 该属性配置在 <servlet></servlet> 标签中

##### 使用注解（Servlet 3.0 后支持，推荐）

```java
@WebServlet("/hello")
public class AnotherServlet extends HttpServlet {

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("使用注解的 Servlet 的 GET 方法！");
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        System.out.println("使用注解的 Servlet 的 POST 方法！");
    }
}
```

###### @WebServlet 注解常用属性

* `name`：`Servlet` 名字（可选）

* `value`：配置 `url` 路径，可以配置多个

* `urlPatterns`：配置 `url` 路径，和 `value` 作用一样，不能同时使用

* `loadOnStartup`：配置 `Servlet` 的创建的时机，如果是 0 或者正数启动程序时创建，如果是负数，则访问时创建。数字越小优先级越高

> [注解和 xml 配置 Servlet 的方式可以同时存在、同时生效，不冲突]()

### 7. Servlet 应用【重点】

#### 7.1 request 对象

在 `Servlet` 中用来处理客户端请求需要用 `doGet` 或 `doPost` 方法的 `request` 对象

[![cCXGcQ.md.png](https://z3.ax1x.com/2021/03/29/cCXGcQ.md.png)](https://imgtu.com/i/cCXGcQ)

##### get 和 post 区别

* `get` 请求
  * `get` 提交的数据会放在 `URL` 之后，以 `？` 分割 `URL` 和传输数据，参数之间以 `&` 相连
  * `get` 方式明文传递，数据量小，不安全
  * 效率高，浏览器默认请求方式为 `GET` 请求
  * 对应的 `Servlet` 方法是 `doGet`
* `post` 请求
  * `post` 方法是把提交的数据放在 `HTTP` 包的 `Body` 中
  * 密文传递数据，数据量大，安全
  * 效率相对没有 `GET` 高
  * 对应的 `Servlet` 的方法是 `doPost`

##### request 主要方法

| 方法名                                      | 说明                           |
| ------------------------------------------- | ------------------------------ |
| `String getParameter(String name)`          | 根据表单组件名称获取提交的数据 |
| `void setCharacterEncoding(String charset)` | 指定每个请求的编码             |

##### request 应用

`HTML` 页面

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>欢迎页面</title>
</head>
<body>
    <h1>欢迎你！</h1>
    <div>
        <form action="/welcome" method="get">
            <label for="name">姓名：</label><input type="text" id="name" name="name"><br>
            <label for="age">年龄</label><input type="text" id="age" name="age"><br>
            <button type="submit">提交</button>
        </form>
    </div>
</body>
</html>
```

`Servlet` 代码

```java
@WebServlet("/welcome")
public class WelcomeServlet extends HttpServlet {

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        String name = req.getParameter("name");
        String age = req.getParameter("age");
        System.out.println("请求的参数值是：" + name + "\t" + age);
    }
}
```

##### get 请求收参问题

产生乱码是因为服务器和客户端沟通的编码不一致造成的，因此解决的办法是：在客户端和服务器之间设置一个统一的编码，之后就按照此编码进行数据的传输和接收

##### get 中文乱码

在 `Tomcat7` 及以下版本，客户端以 `UTF-8` 的编码传输数据到服务器端，而服务器端的 `request` 对象使用的是 `ISO-8859-1` 这个字符编码来接收数据，服务器和客户端沟通的编码不一致，因此才会产生中文筹码的。

解决办法：在接收到数据后，先获取 `request` 对象以 `ISO-8859-1` 字符编码接收到的原始数据的字节数组，然后通过字节数组以指定的编码构建降低串，解决筹码问题

`Tomcat8` 的版本中 `get` 方式不会出现筹码了，因为服务器对 `url` 的编码格式可以进行自动转换

解决 `Tomcat8` 以前版本乱码的问题：

```java
@WebServlet("/welcome")
public class WelcomeServlet extends HttpServlet {

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        String name = req.getParameter("name");
        name = new String(name.getBytes(Charset.forName("ISO-8859-1")), Charset.forName("utf-8"));
        String age = req.getParameter("age");
        System.out.println("请求的参数值是：" + name + "\t" + age);
    }
}
```

##### post 中文乱码

由于客户端是以 `UTF-8` 字符编码将表单数据传输到服务器端的，因此服务器也需要设置以 `UTF-8` 字符编码进行接收

解决方案：使用从 `ServletRequest` 接口继承而来的 `setCharacterEncoding(charset)` 方法进行统一的编码设置

```java
@WebServlet("/welcome")
public class WelcomeServlet extends HttpServlet {

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        req.setCharacterEncoding("utf-8");
        String name = req.getParameter("name");
        String age = req.getParameter("age");
        System.out.println("请求的参数值是：" + name + "\t" + age);
    }
}

```

#### 7.2 Response 对象

用于响应客户端请求并向客户端输出信息

[![cPFwpn.md.png](https://z3.ax1x.com/2021/03/29/cPFwpn.md.png)](https://imgtu.com/i/cPFwpn)

##### 主要方法

| 方法名称                       | 作用                               |
| ------------------------------ | ---------------------------------- |
| `setHeader(name, value)`       | 设置响应信息头                     |
| `setContentType(String)`       | 设置响应文件类型、响应式的编码格式 |
| `setCharacterEncoding(String)` | 设置服务端响应内容编码格式         |
| `getWriter()`                  | 获取字符输出流                     |

案例：使用 `response` 对象向浏览器输出 `HTML` 内容，实现用户登录后，输出 登录成功

```java
@WebServlet("/welcome")
public class WelcomeServlet extends HttpServlet {

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        req.setCharacterEncoding("utf-8");
        String name = req.getParameter("name");
        String age = req.getParameter("age");
        resp.setCharacterEncoding("utf-8");

        PrintWriter writer = resp.getWriter();
        writer.println("<html>");
        writer.println("<head><title>登录</title></head>");
        writer.println("<body>");
        writer.println("<h1>登录成功！</body>");
        writer.println("</body>");
        writer.println("</html>");
    }
}
```

> [如果输出内容包含中文，则出现乱码，因为服务器默认采用 IOS-8859-1 编码响应内容]()

##### 解决输出中文乱码【不推荐】

* 设置服务器端响应的编码格式
* 设置客户端响应内容的头内容的文件类型及编码格式

```java
response.setCharacterEncoding("utf-8"); // 设置响应编码格式为 utf-8
response.setHeader("Content-type", "text/html;charset=UTF-8");
```

##### 解决输出中文筹码【推荐】

同时设置服务端的编码格式和客户端响应的文件类型及响应时的编码格式

```java
response.setContentType("text/html;charset=UTF-8");
```

> 注意：在获取输出流（getWriter()）之前设置上面的代码

#### 7.3 综合案例（Servlet + JDBC）

##### 项目结构

[![cVFGh8.png](https://z3.ax1x.com/2021/04/01/cVFGh8.png)](https://imgtu.com/i/cVFGh8)



##### Entity

```java
@Data
public class User {
    private int userId;
    private String username;
    private String password;
    private String address;
    private String phone;
}
```

##### Dao

```java
public interface UserDao {

    int add(User t);

    int delete(int id);

    int delete(String id);

    int update(User t);

    User findOne(String id);

    User findOne(String username, String password);

    List<User> findAll();
}

public class UserDaoImpl implements UserDao {
    private QueryRunner queryRunner = new QueryRunner();

    @Override
    public int add(User user) {
        return 0;
    }

    @Override
    public int delete(int id) {
        return 0;
    }

    @Override
    public int delete(String id) {
        return 0;
    }

    @Override
    public int update(User user) {
        return 0;
    }

    @Override
    public User findOne(String id) {
        return null;
    }

    @Override
    public User findOne(String username, String password) {
        User user = null;
        try {
            user = queryRunner.query(JDBCUtil1.getConnection(), "select * from user where username=? and password=?", new BeanHandler<User>(User.class), username, password);
        } catch (SQLException e) {
            e.printStackTrace();
        }

        return user;
    }

    @Override
    public List<User> findAll() {
        List<User> userList = null;
        try {
            userList = queryRunner.query(JDBCUtil1.getConnection(), "select * from user", new BeanListHandler<User>(User.class));
        } catch (SQLException e) {
            e.printStackTrace();
        }
        return userList;
    }
}
```

##### Service

```java
public interface UserService {

    User login(String username, String password) throws Exception;
    List<User> findAllUsers();
}

public class UserServiceImpl implements UserService {
    private UserDaoImpl userDaoImpl = new UserDaoImpl();

    @Override
    public User login(String username, String password) {
        User user = null;
        try {
            JDBCUtil1.beginTransaction();
            user = userDaoImpl.findOne(username, password);
            JDBCUtil1.commit();
        } catch (Exception e) {
            e.printStackTrace();
            JDBCUtil1.rollback();
        }
        return user;
    }

    @Override
    public List<User> findAllUsers() {
        List<User> userList = null;
        try {
            userList = userDaoImpl.findAll();
        } catch (Exception e) {
            e.printStackTrace();
        }
        return userList;
    }
}
```

##### Controller

```java
@WebServlet(value = {"/login", "/userlist"})
public class UserServlet extends HttpServlet {
    private UserService userService = new UserServiceImpl();

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        req.setCharacterEncoding("utf-8");
        resp.setContentType("text/html; charset=UTF-8");

        String username = req.getParameter("username");
        String password = req.getParameter("password");

        User user = null;
        try {
            user = userService.login(username, password);
        } catch (Exception e) {
            e.printStackTrace();
        }
        PrintWriter writer = resp.getWriter();
        if (user != null) {
            writer.println("登录成功！欢迎 " + username + "！");
        } else {
            writer.println("用户不存在！");
        }
    }

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        req.setCharacterEncoding("utf-8");
        resp.setContentType("text/html; charset=UTF-8");

        List<User> allUsers = userService.findAllUsers();

        PrintWriter writer = resp.getWriter();
        writer.println("<html>");
        writer.println("<head>");
        writer.println("<title>用户列表</title>");
        writer.println("</head>");
        writer.println("<body>");
        writer.println("<table border='1' align='center'>");
        writer.println("<tr>");
        writer.println("    <td>姓名</td>");
        writer.println("    <td>住址</td>");
        writer.println("    <td>电话</td>");
        writer.println("</tr>");

        for (User user : allUsers) {
            writer.println("<tr>");
            writer.println("    <td>" + user.getUsername() + "</td>");
            writer.println("    <td>" + user.getAddress() + "</td>");
            writer.println("    <td>" + user.getPhone() + "</td>");
            writer.println("</tr>");
        }

        writer.println("</table>");
        writer.println("</body>");
        writer.println("</html>");
    }
}
```

### 8. 转发与重定向

#### 8.1 现有问题

在之前案例中，调用业务逻辑和显示结果页面都在同一个 `Servlet` 中，就会产生设计的问题：

* 不符合单一职能原则、各司其职的思想
* 不利于后续的维护

**结论：应该将业务逻辑和显示结果分离开**

[![cmCaZR.md.png](https://z3.ax1x.com/2021/04/02/cmCaZR.md.png)](https://imgtu.com/i/cmCaZR)

##### 业务、显示分离

[![cmzaWD.md.png](https://z3.ax1x.com/2021/04/03/cmzaWD.md.png)](https://imgtu.com/i/cmzaWD)



问题：

* 业务逻辑和显示结果分离后，如何跳转到显示结果的 `Servlet`
* 业务逻辑得到的数据结果如果传递给显示结果的 `Servlet`

#### 8.2 转发

转发的作用在服务端，将请求发送给服务器上的其他资源，以便共同完成一次请求的处理

##### 页面跳转

在调用业务逻辑的 `Servlet` 中，编写以下代码：

`request.getRequestDispatcher("/目标URL-pattern").forward(request, response);`

**注意：使用 forward 跳转时，是在服务器内部跳转，地址栏不发生变化，属于同一次请求**

[![cnSNBn.md.png](https://z3.ax1x.com/2021/04/03/cnSNBn.md.png)](https://imgtu.com/i/cnSNBn)

##### 数据传递

`forward` 表示一次请求，是在服务器内部跳转，可以共享同一次 `request` 作用域中的数据

* `request` 作用域：拥有存储数据的空间，作用范围是一次请求有效（一次请求可以经过多次转发）
  * 可以将数据存入 `request` 后，在一次请求过程中的任何位置进行获取
  * 可传递任何数据（基本数据类型、对象、数组、集合等）
* 存数据：`request.setAttribute(key, value);`
  * 以键值对形式存储在 `request` 作用域中，`key` 为 `String` 类型，`value` 为 `Object` 类型
* 取数据：`request.getAttribute(key);`
  * 通过 `String` 类型的 `key` 访问 `Object` 类型的 `value`

##### 转发特点

* 转发是服务器行为
* 转发是浏览器只做了一次访问请求
* 转发浏览器地址不变
* 转发再次跳转之间传输的信息不会丢失，所以可以通过 `request` 进行数据的传递
* 转发只能将请求转发给同一个 `web` 应用中的组件

#### 8.3 重定向

重定向作用在客户端，客户端将请求发送给服务器后，服务器响应给客户端一个新的请求地址，客户端重新发送新请求

##### 页面跳转

在调用业务逻辑的 `Servlet` 中，编写以下代码：

`response.sendRedirect("目标URI");`

> URI：统一资源标识符（Uniform Resource Identifier），用来表示服务器定位一个资源，资源在 web 项目中的路径（/project/source）

[![cnt2NR.md.png](https://z3.ax1x.com/2021/04/03/cnt2NR.md.png)](https://imgtu.com/i/cnt2NR)

##### 数据传递

`sendRedirect` 跳转时，地址栏改变，代表客户端重新发送的请求，属于两次请求：

* `response` 没有作用域，再次 `request` 请求中的数据无法共享
* 传递数据：通过 `URI` 的拼接进行数据传递（`/WebProject/b?username=tom`）
* 获取数据：`request.getParameter("username");`

##### 重定向特点

* 重定向是客户端行为
* 重定向是浏览器做了至少两次的访问请求
* 重定向浏览器地址改变
* 重定向再次跳转之间传输的信息会丢失（`request` 范围）
* 重定向可以指向任何的资源，包括当前应用程序中的其它资源、同一个站点上的其它应用程序中的资源、其它站点的资源

#### 8.4 转发、重定向总结

当两个 `Servlet` 需要传递数据时，选择 `forward` 转发，不建议使用 `sendRedirect` 进行传递

### 9. Servlet 生命周期

#### 9.1 生命周期四个阶段

##### 实例化

当用户第一次访问 `Servlet` 时，由容器调用 `Servlet` 的构造器创建具体的 `Servlet` 对象，也可以在容器启动之后立即创建实例。使用下面的代码可以设置 `Servlet` 是否在服务器启动时就创建：

`<load-on-startup>1</load-on-startup>`

> 注意：只执行一次

##### 初始化

在初始化阶段，`init()` 方法会被调用，这个方法在 `javax.servlete.Servlet` 接口中定义，其中，方法以一个 `ServletConfig` 类型的对象作为参数

> 注意：init 方法只被执行一次

##### 服务

当客户端有一个请求时，容器就会将请求 `ServletRequest` 与响应 `ServletResponse` 对象转给 `Servlet`，以参数的形式传给 `service` 方法

> 注意：此方法会执行多次

##### 销毁

当 `Servlet` 容器停止或者重新启动都会引起销毁 `Servlet` 对象并调用 `destroy` 方法

>注意：destory 方法执行一次

[![cnWUpT.md.png](https://z3.ax1x.com/2021/04/03/cnWUpT.md.png)](https://imgtu.com/i/cnWUpT)

```java
@WebServlet(value = {"/lifecycle"})
public class LifeCycleServlet implements Servlet {

    public LifeCycleServlet() {
        System.out.println("1. 实例化");
    }

    @Override
    public void init(ServletConfig servletConfig) throws ServletException {
        System.out.println("2. 初始化");
    }

    @Override
    public ServletConfig getServletConfig() {
        return null;
    }

    @Override
    public void service(ServletRequest servletRequest, ServletResponse servletResponse) throws ServletException, IOException {
        System.out.println("3. 服务中");
    }

    @Override
    public String getServletInfo() {
        return null;
    }

    @Override
    public void destroy() {
        System.out.println("4. 销毁");
    }
}
```

### 10. Servlet 特性

#### 10.1 线程安全问题

`Servlet` 在访问之后，会执行实例化操作，创建一个 `Servlet` 对象。而我们 `Tomcat` 容器可以同时多个线程迸发访问同一个 `Servlet`，如果在方法中对成员变量做修改操作，就会有线程安全的问题

#### 10.2 如何保证线程安全

* `synchronized`
  * 将存在线程安全问题的代码放到同步代码块中
* 实现 `SingleThreadModel` 接口
  * `Servlet` 实现 `SingleThreadModel` 接口后，每个线程都会创建 `Servlet` 实例，这样每个客户端请求就不存在共享资源的问题，但是 `Servlet` 响应客户端请求的效率太低，所以已经 **淘汰**
* 尽可能使用局部变量

### 11. 状态管理

#### 11.1 现有问题

* `HTTP` 协议是无状态的，不能保存每次提交的信息
* 如果用户发来一个新的请求，服务器无法知道它是否与上次的请求有联系
* 对于那些需要多次提交数据才能完成的 `web` 操作，比如登录来说，就成问题了

#### 11.2 概念

将浏览器与 `web` 服务器之间多次交互当作一个整体来处理，并且将多次交互所涉及的数据（即状态）保存下来

#### 11.3 状态管理分类

* 客户端状态管理技术：将状态保存在客户端，代表性的是 `cookie` 技术
* 服务器状态管理技术：将状态保存在服务器端。代表性的是 `session` 技术（服务器传递 `sessionID` 时需要使用 `cookie` 的方式）和 `application`

### 12. Cookie 的使用

#### 12.1 什么是 Cookie

* `Cookie` 是在浏览器访问 `Web` 服务器的某个资源时，由 `web` 服务器在 `HTTP` 响应消息头中附带传送给浏览器的一小段数据
* 一旦 `web` 浏览器保存了某个 `Cookie`，那么它在以后每次访问该 `web` 服务器时，都应在 `HTTP` 请求头中将这个 `Cookie` 回传给 `web` 服务器
* 一个 `Cookie` 主要由标识该信息的名称（`name`）和值（`value`）组成

[![cnoXvV.md.png](https://z3.ax1x.com/2021/04/03/cnoXvV.md.png)](https://imgtu.com/i/cnoXvV)

#### 12.2 创建 Cookie

```java
// 创建 Cookie
Cookie ck = new Cookie("code", code);
ck.setPath("/webs"); // 设置 Cookie 的路径
ck.setMaxAge(-1); // 内存存储，取值有三种：>0 有效期，单位秒；=0 立即失效；<0 内存存储。默认值： -1
response.addCookie(ck); // 添加到 response 对象中，响应时发送给客户端

// 注意：有效路径：当前访问资源的上一级目录，不带主机名
```

> chrome 浏览器查看 cookie 信息：chrome://settings/content/cookies

#### 12.3 获取 Cookie

```java
// 获取所有的 Cookie
Cookie[] cks = request.getCookies();
// 遍历 Cookie
for (Cookie ck : cks) {
  // 检索出自己的 Cookie
  if (ck.getName().equals("code")) {
    // 记录 cookie 的值
    code = ck.getValue()；
    break;
  }
}
```

#### 12.4 修改 Cookie

需要保证 `Cookie` 的名称和路径一致即可修改

```java
// 创建 Cookie
Cookie ck = new Cookie("code", code);
ck.setPath("/webs"); // 设置 Cookie 的路径
ck.setMaxAge(-1); // 内存存储，取值有三种：>0 有效期，单位秒；=0 立即失效；< 0 内存存储
response.addCookie(ck); // 让浏览器添加 Cookie
```

> 注意：如果改变 cookie 的 name 和有效路径会新建 cookie，而改变 cookie 值、有效期会覆盖原有 cookie

#### 12.5 Cookie 编码与解码

`Cookie` 默认不支持中文，只能包含 `ASCII` 字符，所以 `Cookie` 需要对 `Unicode` 字符进行编码，否则会出现乱码：

* 编码可以使用 `java.net.URLEncoder` 类的 `encode(String str, Strign encoding)` 方法
* 解码使用 `java.net.URLDecoder` 类的 `decode(String str, String encoding)` 方法

##### 创建带中文 Cookie

```java
Cookie cookie = new Cookie(URLEncoder.encode("姓名", "UTF-8"), URLEncoder.encode("张三", "UTF-8"));
// 发送到客户端
response.addCookie(cookie);
```

##### 读取带中文 Cookie

```java
if (request.getCookies() != null) {
  for (Cookie cc : request.getCookies()) {
    String CookieName = URLDecoder.decode(cc.getName(), "UTF-8");
    String cookieValue = URLDecoder.decode(cc.getValue(), "UTF-8");
    out.println(cookieName + "=");
    out.println(cookieValue + ";<br/>");
  }
} else {
  out.println("Cookie 未写入客户端。请刷新页面。");
}
```

#### 12.6 Cookie 优缺点

优点：

* 可配置到期规则
* 简单性：`Cookie` 是一种基于文本的轻量结构，包含简单的键值对
* 数据持久性：`Cookie` 默认在过期之前是可以一直存在客户端浏览器上的

缺点：

* 大小受到限制：大多数浏览器对于 `Cookie` 的大小有 4K、8K 字节的限制
* 用户配置为禁用：有些用户禁用了浏览器或客户端设备接收 `Cookie` 的能力，因此限制了这一功能
* 潜在的安全风险：`Cookie` 可能会被篡改，会对安全性造成潜在风险或者导致依赖于 `Cookie` 的应用程序失败

### 13. Session 对象【重点】

#### 13.1 Sesssion 概述

* `Session` 用于记录用户的状态。`Session` 指的是在一段时间内，单个客户端与 `web` 服务器的一连串相关的交互过程
* 在一个 `Session` 中，客户可能会多次请求访问同一个资源，也有可能请求访问各种不同的服务器资源

#### 13.2 Session 原理

* 服务器会为每一次会话分配一个 `Session` 对象
* 同一个浏览器发起的多次请求，同属于一次会话（`Session`）
* 首次用到 `Session` 时，服务器会自动创建 `Session`，并创建 `Cookie` 存储 `SessionId` 发送回客户端

> 注意：session 是由服务端创建的

#### 13.3 Session 使用

* `Session` 作用域：拥有存储数据的空间，作用范围是一次会话有效
  * 一次会话是使用同一浏览器发送的多次请求，一旦浏览器关闭，则结束会话
  * 可以将数据存入 `Session` 中，在一次会话的任意位置进行获取
  * 可传递任何数据（基本数据类型、对象、集合、数组）

##### 获取 Session

```java
// 获取 Session 对象
HttpSession session = reqeust.getSession();
// 唯一标识
System.out.println("Id," + session.getId());
```

#####  Session 保存数据

`setAttribute(属性名, Object);` ：保存数据到 `Session` 中，以键值对形式存储在 `Session` 作用域中

##### Session 获取数据

`getAttribute(属性名);` ：获取 `Session` 中数据，通过 `String` 类型的 `key` 访问 `Object` 类型的 `value`

##### Session 移除数据

`removeAttribute(属性名)` ：从 `Session` 中删除数据，通过键移除 `Session` 作用域中的值

#### 13.4 Session 与 Request 的应用区别

* `request` 是一次请求有效，请求改变，则 `request` 改变
* `session` 是一次会话有效，浏览器改变，则 `session` 改变

#### 13.5 Session 的生命周期

* 开始：第一次使用到 `Session` 的请求产生，则创建 `Session`
* 结束：
  * 浏览器关闭，则失效
  * `Session` 超时，则失效
    * `session.setMaxinactiveInterval(seconds); // 设置最大有效时间（单位：秒）` 
  * 手工销毁，则失效
    * `session.invalidate(); // 登录退出、注销`

#### 13.6 浏览器禁用 Cookie 的解决方案【了解】

#####  浏览器禁用 Cookie 的后果

服务器在默认情况下，会使用 `Cookie` 的方式将 `sessionID` 发给浏览器，如果用户禁止 `Cookie`，则 `sessionID` 不会被浏览器保存，此时，服务器可以使用如 `URL` 重写这样的方式发送 `sessionID`

##### URL 重写

浏览器在访问服务器上的某个地址时，不再使用原来的那个地址，而是使用经过改写的地址（即在原来的地址后面加上了 `sessionID`）

##### 实现 URL 重写

`response.encodeRedirectURL(String url)` 生成重写的 `URL`

```java
HttpSession session = request.getSession();
// 重写 URL 追加 SessionId
String newURL = response.encodeRedirectURL("/项目名称/cs");
System.out.println(newURL);

response.sendRedirect(newURL);
```

#### 13.7 Session 实战权限验证

[![cKNaa4.md.png](https://z3.ax1x.com/2021/04/04/cKNaa4.md.png)](https://imgtu.com/i/cKNaa4)



```java
// 实体类
@Data
public class User {

  private long userId;
  private String username;
  private String password;
  private String address;
  private String phone;
  private java.sql.Date birthday;

  public User() {
  }

  public User(String username, String password, String address, String phone, Date birthday) {
    this.username = username;
    this.password = password;
    this.address = address;
    this.phone = phone;
    this.birthday = birthday;
  }
}

// Dao 层
public abstract class AbstractDao {

    public abstract int add(User user) throws Exception;
    public abstract int delete(long id) throws Exception;
    public abstract int update(User user) throws Exception;
    public abstract User findOne(long id) throws Exception;
    public abstract List<User> findAll() throws Exception;
}
public class UserDao extends AbstractDao {
    private static final QueryRunner QUERY_RUNNER = new QueryRunner();


    @Override
    public int add(User user) throws Exception {
        return QUERY_RUNNER.update(DBUtil.getConnection(), "insert into user (username, password, address, phone, birthday) values (?, ?, ?, ?, ?)", user.getUsername(), user.getPassword(), user.getAddress(), user.getPhone(), user.getBirthday());
    }

    @Override
    public int delete(long id) throws Exception {
        return 0;
    }

    @Override
    public int update(User user) throws Exception {
        return 0;
    }

    @Override
    public User findOne(long id) throws Exception {
        return null;
    }

    public User findOneByName(String username) throws Exception {
        return QUERY_RUNNER.query(DBUtil.getConnection(), "select * from user where username=?", new BeanHandler<User>(User.class), username);
    }

    @Override
    public List<User> findAll() throws Exception {
        return QUERY_RUNNER.query(DBUtil.getConnection(), "select * from user", new BeanListHandler<>(User.class));
    }
}

// Service 层
public interface UserService {

    boolean addUsers(List<User> users) throws Exception;

    User login(String username, String password) throws Exception;

    List<User> getAllUsers() throws Exception;
}
public class UserServiceImpl implements UserService {
    private static final UserDao USER_DAO = new UserDao();

    @Override
    public boolean addUsers(List<User> users) throws Exception {
        DBUtil.beginTransaction();
        try {
            for (User user : users) {
                USER_DAO.add(user);
            }

            DBUtil.commit();
            return true;
        } catch (Exception ex) {
            DBUtil.rollback();
            throw ex;
        }
    }

    @Override
    public User login(String username, String password) throws Exception {
        User user = null;
        try {
            // 1. 根据用户名查找
            user = USER_DAO.findOneByName(username);
            if (user != null) {
                if (!user.getPassword().equals(password)) {
                    throw new Exception("密码不正确！");
                }
            } else {
                throw new Exception("用户不存在！");
            }
        } catch (Exception ex) {
            ex.printStackTrace();
            throw ex;
        }
        return user;
    }

    @Override
    public List<User> getAllUsers() throws Exception {
        List<User> users;
        try {
            users = USER_DAO.findAll();
        } catch (Exception ex) {
            throw ex;
        }
        return users;
    }
}

// Servlet 层
@WebServlet("/addUsersServlet")
public class AddUsersServlet extends HttpServlet {
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        res.setContentType("text/html; charset=UTF-8");
        UserService userService = new UserServiceImpl();
        List<User> users = new ArrayList<>();
        PrintWriter writer = res.getWriter();

        try {
            users.add(new User("张三", "123", "兰州市城关区段家滩", "12332112332", DateUtil.utilDateToSqlDate(DateUtil.strToUtilDate("1983-03-02"))));
            users.add(new User("李四", "234", "兰州市城关区高新区", "23423423423", DateUtil.utilDateToSqlDate(DateUtil.strToUtilDate("1984-04-02"))));
            users.add(new User("刘六", "345", "兰州市城关区宋家滩", "34534534534", DateUtil.utilDateToSqlDate(DateUtil.strToUtilDate("1985-05-02"))));

            userService.addUsers(users);

            res.sendRedirect("/login.html");
        } catch (Exception e) {
            e.printStackTrace();
            writer.println("<h1>添加用户失败，原因：</h1>");
            writer.println(e.getMessage());
        }
    }

    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        this.doPost(req, res);
    }
}
@WebServlet("/login")
public class Login extends HttpServlet {
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        UserService userService = new UserServiceImpl();

        req.setCharacterEncoding("utf-8");
        res.setContentType("text/html; charset=UTF-8");

        String username = req.getParameter("username");
        String password = req.getParameter("password");

        PrintWriter writer = res.getWriter();

        try {
            User user = userService.login(username, password);
            if (user != null) {
                HttpSession session = req.getSession();
                session.setAttribute("user", user);

                res.sendRedirect("/showallController");
            } else {
                res.sendRedirect("/login.html");
            }
        } catch (Exception e) {
            e.printStackTrace();
            writer.println("<h1>" + e.getMessage() + "</h1>");
        }
    }

    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        this.doPost(req, res);
    }
}
@WebServlet("/showallController")
public class ShowAllUsersController extends HttpServlet {

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        HttpSession session = req.getSession();
        Object username = session.getAttribute("user");
        if (username == null) {
            resp.sendRedirect("/login.html");
        } else {
            UserService userService = new UserServiceImpl();

            try {
                List<User> users = userService.getAllUsers();

                req.setAttribute("users", users);
                req.getRequestDispatcher("/showalljsp").forward(req, resp);
            } catch (Exception e) {
                e.printStackTrace();
            }
        }
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
@WebServlet("/showalljsp")
public class ShowAllJSP extends HttpServlet {

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        Object user1 = req.getSession().getAttribute("user");

        if (user1 == null) {
            resp.sendRedirect("/login.html");
        } else {
            List<User> users = (List<User>) req.getAttribute("users");
            resp.setContentType("text/html; charset=UTF-8");
            PrintWriter writer = resp.getWriter();
            writer.println("<html>");
            writer.println("<head>");
            writer.println("<title>用户列表页面</title>");
            writer.println("</head>");
            writer.println("<body>");
            writer.println("<table border='1' align='center'>");
            writer.println("    <tr>");
            writer.println("        <th>姓名</th>");
            writer.println("        <th>密码</th>");
            writer.println("        <th>电话</th>");
            writer.println("        <th>地址</th>");
            writer.println("        <th>生日</th>");
            writer.println("    </tr>");

            for (User user : users) {
                writer.println("    <tr>");
                writer.println("        <td>" + user.getUsername() + "</td>");
                writer.println("        <td>" + user.getPassword() + "</td>");
                writer.println("        <td>" + user.getPhone() + "</td>");
                writer.println("        <td>" + user.getAddress() + "</td>");
                writer.println("        <td>" + DateUtil.utilDateToStr(DateUtil.sqlDateToUtilDate(user.getBirthday())) + "</td>");
                writer.println("    </tr>");
            }

            writer.println("</table>");
            writer.println("</body>");
            writer.println("</html>");
        }
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}

// login.html 页面
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>登录</title>
</head>
<body>
    <form action="/login" method="post">
        <label for="username">用户名：</label><input type="text" id="username" name="username">
        <label for="password">密码：</label><input type="password" id="password" name="password">
        <button type="submit">登录</button>
    </form>
</body>
</html>
```

#### 13.8 Session 实战之验证码

##### 导入 ValidateCode.jar 包

[下载地址](https://www.jianshu.com/p/86669357074b)

`jar` 包作用：帮助生成验证码图片

##### 编写 ValidateCode Servlet

```java
@WebServlet("/validateCode")
public class ValidateCode extends HttpServlet {
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        cn.dsna.util.images.ValidateCode validateCode = new cn.dsna.util.images.ValidateCode(200, 40, 4, 20);

        req.getSession().setAttribute("codes", validateCode.getCode());

        validateCode.write(res.getOutputStream());
    }

    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        this.doPost(req, res);
    }
}
```

##### 修改 login.html 页面

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>登录</title>
</head>
<body>
    <form action="/login" method="post">
        <label for="username">用户名：</label><input type="text" id="username" name="username"><br>
        <label for="password">密码：</label><input type="password" id="password" name="password"><br>
        <label for="code">验证码：</label><input type="text" id="code" name="code"><img src="/validateCode"/> <br>
        <button type="submit">登录</button>
    </form>
</body>
</html>
```

##### 修改 login servlet

```java
@WebServlet("/login")
public class Login extends HttpServlet {
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        UserService userService = new UserServiceImpl();

        req.setCharacterEncoding("utf-8");
        res.setContentType("text/html; charset=UTF-8");

        String username = req.getParameter("username");
        String password = req.getParameter("password");
        String code = req.getParameter("code");

        String codes = (String) req.getSession().getAttribute("codes");

        PrintWriter writer = res.getWriter();

        try {
            if (codes != null && codes.equalsIgnoreCase(code)) {
                User user = userService.login(username, password);
                if (user != null) {
                    HttpSession session = req.getSession();
                    session.setAttribute("user", user);

                    res.sendRedirect("/showallController");
                } else {
                    res.sendRedirect("/login.html");
                }
            } else {
                res.sendRedirect("/login.html");
            }
        } catch (Exception e) {
            e.printStackTrace();
            writer.println("<h1>" + e.getMessage() + "</h1>");
        }
    }

    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        this.doPost(req, res);
    }
}
```

### 14. ServletContext 对象【重点】

#### 14.1 概述

* 全局对象，也拥有作用域，对应一个 `Tomcat` 中的 `Web` 应用
* 当 `Web` 服务器启动时，会为每一个 `Web` 应用程序创建一块共享的存储区域（`ServletContext`）
* `ServletContext` 在 `Web` 服务器启动时创建，服务器关闭时销毁

#### 14.2 获取

* `GenericServlet` 提供了 `getServletContext()` 方法（推荐）`this.getServletContext();`
* `HttpServletRequest` 提供了 `getServletContext()` 方法（推荐）
* `HttpSession` 提供了 `getServletContext()` 方法

#### 14.3 作用

##### 获取项目真实路径

获取当前项目在服务器发布的真实路径：

`String realpath = servletContext.getRealPath("/");`

##### 获取项目上下文路径

获取当前项目上下文路径（应用程序名称）：

```java
System.out.println(servletContext.getContextPath()); // 上下文路径（应用程序名称）
System.out.println(request.getContextPath());
```

##### 全局容器

`ServletContext` 拥有作用域，可以存储数据到全局容器中：

* 存储数据：`servletContext.setAttribute("name", value);`
* 获取数据：`servletContext.getAttribute("name");`
* 移除数据：`servletContext.removeAttribute("name");`

#### 14.4 特点

* 唯一性：一个应用对应一个 `servlet` 上下文
* 生命周期：只要容器不关闭或者应用不卸载，`servlet` 上下文就一直存在

#### 14.5 应用场景

统计当前项目的访问次数：

```java
@WebServlet("/CountController")
public class CountController extends HttpServlet {
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        ServletContext servletContext = getServletContext();

        Integer count = (Integer) servletContext.getAttribute("count");

        if (count == null) {
            count = 1;
            servletContext.setAttribute("count", count);
        } else
            servletContext.setAttribute("count", ++count);

        System.out.println("当前访问次数：" + count);
    }

    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        this.doPost(req, res);
    }
}
```

#### 14.6 作用域总结

* `HttpservletRequest`：一次请求，请求响应之前有效
* `HttpSession`：一次会话开始，浏览器不关闭或不超时之前有效
* `ServletContext`：服务器启动开始，服务器停止之前有效

### 15. 过滤器【重点】

#### 15.1 现有问题

在以往的 `servlet` 中，是否有冗余的代码，多个 `servlet` 都要进行编写？

#### 15.2 概念

过滤器（`Filter`）是处于客户端与服务器目标资源之间的一道过滤技术

[![cGrvAH.md.png](https://z3.ax1x.com/2021/04/07/cGrvAH.md.png)](https://imgtu.com/i/cGrvAH)

#### 15.3 作用

* 执行地位在 `servlet` 之前，客户端发送请求时，会先经过 `Filter`，再到达目标 `Servlet` 中，响应时，会根据执行流程再次反向执行 `Filter`
* 可以解决多个 `Servlet` 共性代码的冗余问题（例如：乱码处理、登录验证等）

#### 15.4 编写过滤器

`Servlet API` 中提供了一个 `Filter` 接口，开发人员编写一个 `Java` 类实现了这个接口即可，这个 `Java` 类称之为过滤器

##### 实现过程

* 编写 `Java` 类实现 `Filter` 接口
* 在 `doFilter` 方法中编写拦截逻辑
* 设置拦截路径

```java
@WebFilter("/t")
public class MyFilter implements Filter {
    @Override
    public void doFilter(ServletRequest servletRequest, ServletResponse servletResponse, FilterChain filterChain) throws IOException, ServletException {
        System.out.println("Filter");

        filterChain.doFilter(servletRequest, servletResponse);

        System.out.println("end");
    }
}

@WebServlet("/t")
public class TargetController extends HttpServlet {
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        System.out.println("target");
    }

    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        this.doPost(req, res);
    }
}
```

#### 15.5 配置

##### 注解配置

在自定义的 `Filter` 类上使用注解 `@WebFilter(value="/过滤目标资源")`

##### xml 配置

在 `web.xml` 中进行过滤器的配置

```xml
<!-- 过滤器的 xml 配置-->
<filter>
  <!--名称-->
  <filter-name>sf</filter-name>
  <!--过滤器类全称-->
  <filter-class>com.qf.web.filter.SecondFilter</filter-class>
</filter>
<!--映射路径配置-->
<filter-mapping>
  <!--名称-->
  <filter-name>sf</filter-name>
  <!--过滤的 url 匹配的规则和 Servlet 类似-->
  <url-pattern>/*</url-pattern>
</filter-mapping>
```

##### 关于拦截路径

过滤器的拦截路径通常有三种形式：

* 精确拦截匹配：`/index.jsp`、`/myservlet` 等
* 后缀拦截匹配：`*.jsp`、`*.html`、`*.jpg`
* 通配符拦截匹配 `/*` ：表示拦截所有。注意过滤器不能使用 `/` 匹配，`/aaa/bbb/*` 允许

#### 15.6 过程器链和优先级

##### 过滤器链

客户端对服务器请求之后，服务器调用 `Servlet` 之前会执行一组过滤器（多个过滤器），那么这组过滤器就称为一条过滤器链

每个过滤器实现某个特定的功能，当第一个 `Filter` 的 `doFilter` 方法被调用时，`web` 服务器会创建一个代表 `Filter` 链的 `FilterChain` 对象传递给该方法。在 `doFilter` 方法中，开发人员如果调用了 `FilterChain` 对象的 `doFilter` 方法，则 `web` 服务器会检查 `FilterChain` 对象中是否还有 `filter`，如果有，则调用第 2 个 `filter`，如果没有，则调用目标资源

[![cY9gZq.md.png](https://z3.ax1x.com/2021/04/08/cY9gZq.md.png)](https://imgtu.com/i/cY9gZq)

##### 过滤器优先级

在一个 `web` 应用中，可以开发编写多个 `Filter`，这些 `Filter` 组合起来称之为一个 `Filter` 链

优先级：

* 如果为注解的话，是按照类全名称的字符串顺序决定作用顺序
* 如果 `web.xml`，按照 `filter-mapping` 注册顺序，从上往下
* `web.xml` 配置高于注解方式
* 如果注解和 `web.xml` 同时配置，会创建多个过滤器对象，造成过滤多次

#### 15.7 过滤器典型应用

##### 解决乱码

```java
@WebFilter("/*")
public class EncodingFilter implements Filter {

    public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain) throws ServletException, IOException {
        // 对 request 对象请求消息增强
        req.setCharacterEncoding("utf-8");
        // 放行
        chain.doFilter(req, res);

        // 对 response 对象响应消息增强
        res.setContentType("text/html; charset=UTF-8");
    }

    public void destroy() {
    }

    public void init(FilterConfig config) throws ServletException {

    }
}
```

##### 权限验证

```java
// 创建了该过滤器后，原来在 showallController 中写的权限判断的代码就可以不使用了
@WebFilter("/showallController")
public class AuthorityFilter implements Filter {

    public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain) throws ServletException, IOException {
        // 对 request 对象请求消息增强
        HttpServletRequest request = (HttpServletRequest) req;
        HttpServletResponse response = (HttpServletResponse) res;
        HttpSession session = request.getSession();
        User user = (User) session.getAttribute("user");

        if (user != null) {
            // 放行
            chain.doFilter(req, res);
        } else {
            response.sendRedirect(req.getServletContext().getContextPath() + "/login.html");
            chain.doFilter(req, res);
        }

        // 对 response 对象响应消息增强
    }

    public void destroy() {
    }

    public void init(FilterConfig config) throws ServletException {

    }
}
```

### 16. 综合案例







## 第二十五章 JSP

### 1. 现有问题

在之前学习 `Servlet` 时，服务端通过 `Servlet` 响应客户端页面，有以下不足之处：

* 开发方式麻烦：继承父类、覆盖方法、配置 `web.xml` 或注解
* 代码修改麻烦：重新编译、部署、重启服务
* 显示方式麻烦：获取流、使用 `println("")` 逐行打印
* 协同开发麻烦：`UI` 负责美化页面、程序员负责编写代码。`UI` 不懂 `Java` ，程序员又不能将所有前端页面的内容通过流输出

### 2. JSP（Java Server Page）

#### 2.1 概念

简化的 `Servlet` 设计，在 `HTML` 标签中嵌套 `Java` 代码，用以高效开发 `Web` 应用的动态网页

#### 2.2 作用

替换显示页面部分的 `Servlet`（使用 `*.jsp` 文件替换 `xxxJSP.java`）

### 3. jsp 开发【重点】

> jsp 开发需要的 jar 包（maven配置）如下：
>
> ```xml
> <dependency>
>   <groupId>javax.servlet</groupId>
>   <artifactId>javax.servlet-api</artifactId>
>   <scope>provided</scope>
> </dependency>
> <dependency>
>   <groupId>javax.servlet</groupId>
>   <artifactId>jsp-api</artifactId>
>   <scope>provided</scope>
> </dependency>
> ```

#### 3.1 创建 JSP

在 `web` 目录下新建 `*.jsp` 文件（与 `WEB-INF` 平级）

##### JSP 编写 Java 代码

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Hello World</title>
</head>
<body>
    <%=new java.util.Date() %>
</body>
</html>
```

> 使用 `<%= %>` 标签编写 ` Java ` 代码在页面中打印当前系统时间

##### 访问 JSP

在浏览器地址栏中输入：`http://ip:port/项目路径/资源名称`

#### 3.2 JSP 与 Servlet

* 关系
  * `JSP` 文件在容器中会转换成 `Servlet` 执行
  * `JSP` 是对 `Servlet` 的一种高级封装，本质还是 `Servlet`
* 区别
  * 与 `Servlet` 相比，`JSP` 可以很方便的编写或者修改 `HTML` 网页而不用去面对大量的 `println` 语句

[![cNveKA.md.png](https://z3.ax1x.com/2021/04/09/cNveKA.md.png)](https://imgtu.com/i/cNveKA)

#### 3.3 实现原理

`Tomcat` 会将 `xxx.jsp` 转换成 `Java` 代码，进而编译成 `.class` 文件运行，最终将运行结果通过 `response` 响应给客户端

[![cNvdaV.md.png](https://z3.ax1x.com/2021/04/09/cNvdaV.md.png)](https://imgtu.com/i/cNvdaV)

##### Jsp.java 源文件存放目录

使用 `IDEA` 开发工具，`Tomcat` 编译后的 `JSP` 文件（`Xxx_jsp.class` 和 `Xxx_jsp.java`）的存放地址：

启动应用后，在控制台查找 `catalina.base=路径` ，路径就是实际的项目部署地址，在 `路径/work/Catalina/localhost/应用上下文/` 下就是真实的存放路径

### 4. JSP 与 HTML 集成开发

#### 4.1 脚本

脚本可以编写 `Java` 语句、变量、方法或表达式

##### 普通脚本

语法：`<% java 代码%>`

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>Hello World</title>
</head>
<body>
    Hello World!<br>
    <%
        // jsp 中，使用小脚本嵌入 java 代码
        out.println("hi"); // 打印内容在客户端页面
        System.out.println("hi"); // 打印内容在控制台
    %>
</body>
</html>
```

* 经验：普通脚本可以使用所有 `Java` 语法，除了定义函数
* 注意：脚本与脚本之间不可嵌套，脚本与 `HTML` 标签不可嵌套

##### 声明脚本

语法：`<%! 定义变量、函数 %>`

```jsp
<body>
    <%! int i = 0; %>
    <% int a, b, c; %>
    <% Object object = new Object(); %>
    <%!
        // 定义方法
        public void m1() {
            System.out.println("你好！");
        }
    %>
</body>
```

* 注意：声明脚本中声明的变量是全局变量
* 声明脚本的内容必须在普通脚本 `<% %>` 中调用
* 如果声明脚本中的函数具有返回值，使用输出脚本调用 `<%= %>`

##### 输出脚本

语法：`<%=Java表达式%>`

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>JSP基本使用</title>
</head>
<body>
    <p>
        今天的日期是：<%= new java.util.Date() %>
    </p>
</body>
</html>
```

* 经验：输出脚本可以输出带有返回值的函数
* 注意：输出脚本中不能加 `;`

#### 4.2 JSP 注释

`JSP` 注释主要有两个作用：为脚本代码作注释以及 `HTML` 内容注释

##### 语法规则

| 语法             | 描述                                                    |
| ---------------- | ------------------------------------------------------- |
| `<%-- 注释 --%>` | `JSP` 注释，注释内容不会被发送至浏览器甚至不会被编译    |
| `<!-- 注释 -->`  | `HTML` 注释，通过浏览器查看网页源代码时可以看见注释内容 |

#### 4.3 JSP 指令

`JSP` 指令用来设置与整个 `JSP` 页面相关的属性

| 指令                 | 描述                                                      |
| -------------------- | --------------------------------------------------------- |
| `<%@ page ... %>`    | 定论页面的依赖属性，比如脚本语言、`error`页面、缓存需求等 |
| `<%@ include ... %>` | 包含其它文件                                              |
| `<%@ taglib ... %>`  | 引入标签库的定义，可以是自定义标签                        |

##### page 指令

* 语法：`<%@ page attribute1="value1" attribute2="value2" %>`
* `page` 指令为容器指代当前页面的使用说明，一个 `JSP` 页面可以包含多个 `page` 指令

| 属性           | 描述                                                         |
| -------------- | ------------------------------------------------------------ |
| `contentType`  | 指定当前 `jsp` 页面的 `MIME` 类型和字符编码格式              |
| `errorPage`    | 指定当 `jsp` 页面发生异常时需要转向的错误处理页面            |
| `isErrorPage`  | 指定当前页面是否可以作为另一个 `jsp` 页面的错误处理页面      |
| `import`       | 导入要使用的 `java` 类                                       |
| `language`     | 定义 `jsp` 页面所使用的脚本语言，默认是 `java`               |
| `session`      | 指定 `jsp` 页面是否使用 `session`。默认为 `true` 立即创建，`false` 为使用时创建 |
| `pageEncoding` | 指定 `jsp` 页面的解码格式                                    |

##### include 指令

* 语法：`<%@ include file="被包含的jsp路径"%>`
* 通过 `include` 指令来包含其他文件
* 被包含的文件可以是 `jsp` 文件、`html` 文件或文本文件。包含的文件就好像是当前 `jsp` 文件的一部分，会被同时编译执行（静态包含）

```jsp
<%@ include file="header.jsp"%>
...
...
<%@ include file="fotter.jsp"%>
```

* 注意：可能会有重名的冲突问题，不建议使用

##### taglib 指令

* 语法：`<%@ taglib uri="外部标签库路径" prefix="前缀" %>`
* 引入 `jsp` 的标准标签库

`<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %@>`

#### 4.4 动作标签

语法：`<jsp:action_name attribute="value" />`

动作标签指的是 `jsp` 页面在运行期间的命令

##### include

* 语法：`<jsp:include page="相对 URL 地址" />`
* `<jsp:include> `动作元素会将外部文件输出结果包含在 JSP 中（动态包含）

| 属性 | 描述                        |
| ---- | --------------------------- |
| page | 包含在页面中的相对 URL 地址 |

`<jsp:include page="index.jsp" />`

* 注意：前面已经介绍过 `include` 指令，它是将外部文件的输出代码复制到了当前 `jsp` 文件中。而这里的 `jsp:include` 动作不同，是将外部文件的输出结果引入到了当前的 `jsp` 文件中

##### useBean

* 语法：`<jsp:useBean id="name" class="package.className" />`
* `jssp:useBean` 动作用来加载一个将在 `jsp` 页面中使用的 `JavaBean`

`<jssp:useBean id="user" class="com.ch.wchya.entity.User" />`

* 在类载入后，我们可以通过 `jsp:setProperty` 和 `jsp:getProperty` 动作来修改和获取 `bean` 的属性

###### setProperty

可以在 `jsp:useBean` 元素之后使用 `jsp:setProperty` 进行属性的赋值

| 属性       | 描述                                  |
| ---------- | ------------------------------------- |
| `name`     | 必需的，表示要设置的属性是哪个 `Bean` |
| `property` | 必需的，表示要设置哪个属性            |
| `value`    | 可选的，用来指定 `Bean` 属性的值      |

```jsp
<jsp:useBean id="user" class="com.ch.wchya.entity.User" />
<jsp:setProperty name="user" property="name" value="Jack" />
```

###### getProperty

`jsp:getProperty` 动作提取指定 `Bean` 属性的值，转换成字符串，然后输出

| 属性       | 描述                                        |
| ---------- | ------------------------------------------- |
| `name`     | 要检索的 `Bean` 属性名称，`Bean` 必须已定义 |
| `property` | 表示要提取 `Bean` 属性的值                  |

```jsp
<jsp:useBean id="user" class="com.ch.wchya.entity.User" />
<jsp:setProperty name="user" property="name" value="Jack" />
<jsp:getProperty name="user" property="name" />
```

##### forward

* 语法：`<jsp:forward page="相对 URL 地址" />`
* `jsp:forward` 动作把请求转到另外的页面

| 属性   | 描述                              |
| ------ | --------------------------------- |
| `page` | `page` 属性包含的是一个相对 `URL` |

`<jsp:forward page="index.jsp" />`

##### param

* 语法：`<jsp:param name="" value="" />`
* 在转发动作内部使用，做参数传递

```jsp
<jsp:forward page="index.jsp">
  <%!--http 请求参数传递--%>
  <jsp:param name="sex" value="man" />
</jsp:forward>
```

#### 4.5 内置对象

由 `jsp` 自动创建的对象，可以直接使用

| 对象名        | 类型                                     | 说明                          |
| ------------- | ---------------------------------------- | ----------------------------- |
| `request`     | `javax.servlet.http.HttpServletRequest`  |                               |
| `response`    | `java.xservlet.http.HttpServletResponse` |                               |
| `session`     | `javax.servlet.http.HttpSessiion`        | 由 `session="true"` 开关      |
| `application` | `javax.servlet.ServletContext`           |                               |
| `config`      | `javax.servlet.ServletConfig`            |                               |
| `exception`   | `java.lang.Throwable`                    | 由 `isErrorPage="false"` 开关 |
| `out`         | `javax.servlet.jsp.JspWriiter`           |                               |
| `pageContext` | `javax.servlet.jsp.PageContext`          |                               |
| `page`        | `java.lang.Object` 当前对象 `this`       | 当前 `servlet` 实例           |

##### 四大域对象

`Jsp` 有四大作用域对象，存储数据和获取数据的方式一样，不同的是取值的范围有差别：

* `pageContext(javax.servlet.jsp.PageContext)`：当前 `jsp` 页面范围
* `request(javax.servlet.http.HttpServletRequest)`：一次请求有效
* `session(javax.servlet.http.HttpSession)`：一次会话有效（关闭浏览器失效）
* `application(javax.servlet.ServletContext)`：整个 `web` 应用有效（服务器重启或关闭失效）

##### pageContext 对象

* `pageContext` 对象是 `javax.servlet.jsp.PageContext` 类的实例，拥有作用域，用来代表整个 `jsp` 页面
* 当前页面的作用域对象，一旦跳转则失效
* 通过 `setAttribute("name", value);` 存储值
* 通过 `getAttribute("name");` 获取值
* 用于获取其他 8 个内置对象或者操作其他对象的作用域

```jsp
<%
	pageContext.setAttribute("name", value); // 当前作用域有效
%>
```

##### pageContext 获取其它内置对象

```jsp
<%
  pageContext.getRequest();
  pageContext.getResponse();
  pageContext.getServletContext();
  pageContext.getSession();
  pageContext.getOut();
  pageContext.getException();
  pageContext.getPage();
  pageContext.getServletConfig();
%>
```

##### pageContext 操作其它内置对象的作用域

`pageContext` 对象可以操作其它作用域存储和获取

```jsp
<%
  pageContext.setAttribute("name", value); // 当前页面有效
  pageContext.setAttribute("name", value, PageContext.REQUEST_SCOPE); // request 作用域
  pageContext.setAttribute("name", value, PageContext.SESSION_SCOPE);	// session 作用域
  pageContext.setAttribute("name", value, PageContext.APPLICATION_SCOPE); // application 作用域
%>
<%
  pageContext.getAttribute("name");   // 当前作用域
  pageContext.getAttribute("name", PageContext.REQUEST_SCOPE);    // request 作用域
  pageContext.getAttribute("name", PageContext.SESSION_SCOPE);    // session 作用域
  pageContext.getAttribute("name", PageContext.APPLICATION_SCOPE);// application 作用域
  pageContext.findAttribute("name");  // 从 pageContext、request、session、application 依次查找
%>
```

#### 4.6 整合

将 `emp` 项目所有显示页面 `jsp` 的 `servlet` 替换为 `jsp` 页面，使用脚本进行显示

### 5. EL 表达式（Expression Language）

#### 5.1 概念

`EL` 使 `Jsp` 写起来更简单、简洁。主要用于 **获取*作用域*中的数据**

#### 5.2 作用

`用于替换：作用域对象.getAttribute("name")`

#### 5.3 EL 的应用（获取基本类型、字符串）

* `${scope.name}` ：获取具体某个作用域中的数据
* `${name}` ：获取作用域中的数据，逐级查找 `pageContext、request、session、application`

##### 应用案例

```jsp
<%
	// 存储在 request 作用域
	request.setAttribute("name", "tom");
	request.setAttribute("age", 18);
%>

${requestScope.name} <%--获取request作用域中 name 对应的值，找到就返回值，没找到返回"" --%>
${name}  <%--从最小作用域逐级查找 name 对应的值，找到就返回值，没找到返回 ""--%>
```

##### EL 和 JSP 脚本的区别

* `<%=request.getAttribute() %>  <%--没有找到返回null--%>`
* `${requestScope.name}  <%--没有找到返回 "" --%>`

#### 5.4 EL 的应用（获取引用类型）

使用 `EL` 获取作用域中的对象调用属性时，只能访问对象的 `get` 方法，必须遵守命名规范定义

```jsp
<%
	Emp e = new Emp();
	e.setName("gavin");
	e.setAge(19);
	request.setAttribute("e", e);
%>
${requestScope.e.name} <%--调用getName()方法--%>
```

#### 5.5 EL 的应用（获取数组、集合的元素）

`EL` 可以获取 `Array、List、Map` 中的元素，`Set` 由于没下标，无法直接访问元素，后续可遍历

```jsp
<%
	int[] array = new int[]{1, 2, 3, 4, 5};
	request.setAttribute("array", array);

	List<Emp> emps = new ArrayList<>();
	emps.add(new Emp(1, "gavin", 2000, 19);
  emps.add(new Emp(2, "marry", 3000, 29);
  emps.add(new Emp(3, "jack", 4000, 39);
  request.setAttribute("emps", emps);
           
  Map<String, String> maps = new HashMap<>();
  maps.put("CN", "中国");
  maps.put("FK", "法国");
  maps.put("US", "美国");
  request.setAttribute("maps", maps);
%>
${requestScope.array[0]}
${requestScope.emps[0]} <%-- 也可以使用 ${requestScope.emps.get(0)} --%>
${requestScope.maps[0]} <%-- 也可以使用 ${requestScope.maps["US"]} -->
```

#### 5.5 EL 运算符

| 操作符              | 描述                                 |
| ------------------- | ------------------------------------ |
| `.`                 | 访问一个 `Bean` 属性或者一个映射条目 |
| `[]`                | 访问一个数组或者链表的元素           |
| `+、-、*、/ or div` | 加、减或负、乘、除                   |
| `% or mod`          | 取模                                 |
| `== or eq`          | 测试是否相等                         |
| `!= or ne`          | 测试是否不等                         |
| `< or lt`           | 测试是否小于                         |
| `> or gt`           | 测试是否大于                         |
| `<= or le`          | 测试是否小于等于                     |
| `>= or ge`          | 测试是否大于等于                     |
| `&& or and`         | 测试逻辑与                           |
| `|| or or`          | 测试逻辑或                           |
| `! or not`          | 测试取反                             |
| `empty`             | 测试是否空值                         |

#### 5.7 隐式对象

`EL` 表达式定义了 11 个隐式对象

| 隐式对象           | 描述                             |
| ------------------ | -------------------------------- |
| `pageScope`        | `page` 作用域                    |
| `requestScope`     | `request` 作用域                 |
| `sessionScope`     | `session` 作用域                 |
| `applicationScope` | `application` 作用域             |
| `param`            | `Request` 对象的参数，字符串     |
| `paramValues`      | `Request` 对象的参数，字符串集合 |
| `header`           | `HTTP` 信息头，字符串            |
| `initParam`        | 上下文初始化参数                 |
| `cookie`           | `Cookie` 值                      |
| `pageContext`      | 当前页面的 `pageContext`         |

##### 获得应用上下文

```jsp
<%=request.getContextPath() %>
{pageContext.request.contextPath}
```

##### 获取 Cookie 对象

```jsp
${cookie.username} //获取名为 username 的 cookie 对象
${cookie.password} // 获取名为 password 的 cookie 对象
${cookie.password.value} // 获取 password 的 cookie 的 value 值
```

### 6. JSTL 标准标签库

#### 6.1 现有问题

* `EL` 主要是用于作用域获取数据，虽然可以做运算判断，但是得到的都是一个结果，做展示
* `EL` 不存在流程控制，比如判断
* `EL` 对于集合只能做单点访问，不能实现遍历操作，比如循环

#### 6.2 什么是 JSTL

* 全称：`Java Server Pages Standard Tag Library`
* `JSP` 标准标签库（`JSTL`）是一个 `JSP` 标签集合

#### 6.3 作用

* 可对 `EL` 获取到的数据进行逻辑操作
* 与 `EL` 合作完成数据的展示

#### 6.4 JSTL 使用

* 导入两个 `jar` 文件：`standard.jar` 和 `jstl.jar` 文件都放到 `/WEB-INF/lib/` 目录下
* 在 `jsp` 页面引入标签库 `<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" >`

#### 6.5 核心标签

##### 条件判断 if 判断

语法：`<c:if test="条件"></c:if>`

```jsp
<!-- test 属性中是条件，但条件需要使用 EL 表达式来书写 -->
<h3>条件标签：if</h3>
<c:if test="${8 > 3}">
  8 大于 3 是成立的
</c:if>
<c:if test="${8 < 3}">
  8 小于 3 是成立的
</c:if>
```

##### 多条件判断 choose

```jsp
<c:choose>
  <c:when test="条件1">结果1</c:when>
  <c:when test="条件2">结果2</c:when>
  <c:when test="条件3">结果3</c:when>
  <c:otherwise>结果4</c:otherwise>
</c:choose>
```

```jsp
<c:set var="score" value="85"></c:set>
<c:choose>
  <c:when test="${score < 60}">不及格</c:when>
  <c:when test="${score >= 60 and score < 80}">合格</c:when>
  <c:when test="${score >= 80 and score < 90}">优良</c:when>
  <c:otherwise>优秀</c:otherwise>
</c:choose>
```

##### 迭代标签 foreach

```jsp
<c:foreach
           var="变量名"
           items="集合"
           begin="起始下标"
           end="结束下标"
           step="步长"
           varstatus="遍历状态">
</c:foreach>
<%--varstatus 有四个值：first（是否第一行）, last（是否最后一行）, count（当前行数）, index（当前元素的下标）--%>
```

```jsp
<%
  List<String> list = new ArrayList<>();
  list.add("A");
  list.add("B");
  list.add("C");
  list.add("D");

  request.setAttribute("list", list);
%>
<c:forEach var="list" items="${list}" varStatus="var" begin="0" step="1" end="${list.size() - 1}">
  
<h1>${list}&nbsp;&nbsp;${var.index}&nbsp;&nbsp;${var.first}&nbsp;&nbsp;${var.last}&nbsp;&nbsp;${var.count}&nbsp;&nbsp;${var.index}</h1>
  
</c:forEach>
```

##### url 标签

在 `Cookie` 禁用的情况下，通过重写 `URL` 拼接 `JSESSIONID` 来传递 `ID` 值，便于下一次访问时仍可查找到上一次的 `Session` 对象

```jsp
<c:url context="/${pageContext.request.contextPath}" value="/xxxController" />

// 在 form 表单的 action 中嵌套动态路径
<form action="<c:url context='/${pageContext.request.contextPath}' value='/xxxController'">
  
</form>
```

* 经验：所有涉及到页面跳转或者重定向跳转时，都应该使用 `URL` 重写
* 注意：当 `<c:url/>` 中指定了 `context` 属性时，`context` 和 `value` 的值都必须以 `/` 开头

#### 6.6 整合

使用 `EL + JSTL` 替换 `emp` 项目中的脚本代码

### 7. MVC 框架（Model View Controller）

#### 7.1 MVC 概念

`MVC` 又称为编程模式，是一种软件设计思想，将数据操作、页面展示、业务逻辑分为三个层级（模块），独立完成，相互调用

* 模型层（`Model`)
* 视图（`View`）
* 控制器（`Controller`）

#### 7.2 MVC 模式详解

`MVC` 并不是 `Java` 独有的，现在几乎所有的 `B/S` 的架构都采用了 `MVC` 模式

* 视图 `View`：视图即是用户看到并与之交互的界面，比如 `HTML`（静态资源）、`JSP`（动态资源）等
* 控制器 `Controller`：控制器即是控制请求的处理逻辑，对请求进行处理，负责流程跳转（转发和重定向）
* 模型 `Model`：对客观世界的一种代表和模拟（业务模拟、对象模拟）

[![cwMPlF.md.png](https://z3.ax1x.com/2021/04/11/cwMPlF.md.png)](https://imgtu.com/i/cwMPlF)

#### 7.3 优点

* 低耦合性：模块与模块之间的关联性不强，不与某一种具体实现产生密不可分的关联性
* 高维护性：基于低耦合性，可做到不同层级的功能模块灵活更换、插拔
* 高重用性：相同的数据库操作，可以服务于不同的业务处理。将数据作为独立模块，提高重用性

#### 7.4 MVC 在框架中的应用

`MVC` 模式被广泛用于 `Java` 的各种框架中，比如 `Struts2`、`SpringMVC` 等等都用到了这种思想

#### 7.5 三层架构与 MVC

##### 三层架构

`View` 层（表示|界面层）、`Service`（业务逻辑层）、`DAO`（数据访问层）

[![cwMW1U.md.png](https://z3.ax1x.com/2021/04/11/cwMW1U.md.png)](https://imgtu.com/i/cwMW1U)

##### MVC 与三层架构的区别

* `MVC` 强调的是视图和业务代码的分离，严格的说 `MVC` 其实关注的是 `Web` 层。`View` 就是单独的页面，如 `JSP`、`HTML` 等，不负责业务处理，只负责数据的展示。而数据封装到 `Model` 里，由 `Controller` 负责在 `V` 和 `M` 之间传递。`MVC` 强调业务和视图分离
* 三层架构是”数据访问层“、”业务逻辑层“、”表示层“，指的是代码之间的解耦，方便维护和复用

### 9. 分页

#### 9.1 概念

分布是 `Web` 应用程序非常重要的一个技术，数据库中的数据可能是成千上万的，不可能把这么多的数据一次显示在浏览器上面。一般根据每行数据在页面上所占的空间设置每页显示若干行，比如一般 20 行是一个比较理想的显示状态

#### 9.2 分布实现思路

对于少量的数据查询，需要多少就取多少，显示是最佳的解决方法，假如某个表中有 200 万条记录，第一页取前 20 条，第二页取 21~40 条记录

```sql
select * from 表名 order by id limit 0,20;
select * from 表名 order by id limit 20,20;
select * from 表名 order by id limit 40,20;
```

#### 9.3 分布代码实现

步骤：

1. 确定每页显示的数据量
2. 确定分布显示所需的总页数
3. 编写 `SQL` 查询语句，实现数据查询
4. 在 `JSP` 页面中进行分布显示设置

## 第二十六章 综合项目

### 1. 场景

* 在项目中，文件的上传和下载是最常见的功能，很多程序或者软件中都经常使用到文件的上传和下载
* 邮箱中有附件的上传和下载
* `OA` 办公系统中有附件材料的上传

### 2. 文件上传

#### 2.1 概念

当用户在前端页面点击文件上传后，用户上传的文件数据提交给服务器端，实现保存

#### 2.2 文件上传实现步骤

##### 提交方式

* 提供 `form` 表单，`method` 必须是 `post`，因为 `post` 请求无数据限制

`<form method="post"></form>`

##### 提交数据格式

* 表单的 `enctype` 的属性值必须为 `multipart/form-data`
  * 以多段的形式进行拼接提交。以二进制流的方式来处理表单数据，会把指定的文件内容封装进请求参数中

```html
<form enctype="multipart/form-data" method="post"></form>
```

##### 提供组件

* 提供 `file` 表单组件，提供给用户上传文件

```html
<from enctype="multipart/form-data" method="post">
  上传用户：<input type="text" name="username"><br>
  上传文件：<input type="file" name="file1"><br>
  <input type="submit" value="提交">
</form>
```

##### Controller 编写

在 `Servlet 3.0` 及其以上版本的容器中进行服务器端文件上传的编程，是围绕着注解类型 `MultipartConfig` 和 `javax.servlet.http.Part` 接口进行的。处理已上传文件的 `Servlet` 必须以 `@MultipartConfig` 进行注解：

```html
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>上传文件示例</title>
</head>
<body>
    <form action="/upload" method="post" enctype="multipart/form-data">
        用户名：<input type="text" name="username"><br>
        上传文件：<input type="file" name="file1"><br>
        <input type="submit" value="上传">
    </form>
</body>
</html>
```

```java
@WebServlet("/upload")
@MultipartConfig(maxFileSize = 1024 * 1024 * 100, maxRequestSize = 1024 * 1024 * 200)
public class Upload extends HttpServlet {
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        req.setCharacterEncoding("utf-8");
        res.setContentType("text/html; charset=UTF-8");

        String username = req.getParameter("username");

        Part file = req.getPart("file1");

        String realPath = req.getServletContext().getRealPath("/WEB-INF/upload");

        File file1 = new File(realPath);
        if (!file1.exists()) {
            file1.mkdirs();
        }

        file.write(realPath + File.separator + file.getSubmittedFileName());

        res.getWriter().println(file.getSubmittedFileName() + "文件上传成功！");
    }

    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        this.doPost(req, res);
    }
}
```

> 注意：getRealPath() 获取的是项目部署后的真实路径，即在 IDEA 中项目的 out 目录下进行查看上传是否成功

#### 2.3 文件上传细节

##### 安全问题

为保证服务器安全，上传文件应该放在外界无法直接访问的目录下，比如放于 `WEB-INF` 目录下

```java
String filepath = request.getServletContext().getRealPath("/WEB-INF/upload");
```

##### 文件覆盖

当上传重名文件时，为防止文件覆盖的现象发生，要为上传文件产生一个唯一的文件名

```java
public class UploadUtils {
  // 使用 UUID 生成唯一标识码，拼接上图片的名称
  public static String newFileName(String filename) {
    return UUID.randomUUID().toString.replaceAll("-", "") + "_" + filename;
  }
}
```

##### 散列存储

为防止一个目录下面出现太多文件，要使用 `hash` 算法打散存储

```java
public static String newFilePath(String basePath, String filename) {
  int hashcode = filename.hashCode();
  int path1 = hashcode & 15; // 与运算 0~15 二级
  int path2 = (hashcode >> 4) & 15; // 与运算 0~15 三级
  String dir = basePath + "/" + path1 + "/" + path2; // 与一级目录拼接在一起
  File file = new File(dir); // 创建文件夹对象
  if (!file.exists()) { // 不存在则新建
    file.mkdirs();
  }
  return dir; // 返回新路径
}
```

[![cDk3p4.md.png](https://z3.ax1x.com/2021/04/12/cDk3p4.md.png)](https://imgtu.com/i/cDk3p4)



##### 文件类型上传限制

要限制上传文件的类型，在收到上传文件名时，判断后缀名是否合法

```java
// 创建一个集合存放允许上传的文件的类型（后缀名）
// 判断所上传的文件在当前集合当中是否包含
List<String> nameList = new ArrayList<String>();
nameList.add(".jpg");
nameList.add(".bmp");
nameList.add(".png");
String extName = filename.substring(filename.lastIndexOf("."));
if(!nameList.contains(extName)) {
  res.getWriter.println("文件格式不正确，上传失败！");
  continue;
}
```

#### 多文件上传

```java
@WebServlet("/moreUpload")
@MultipartConfig(maxFileSize = 1024 * 1024 * 10, maxRequestSize = 1024 * 1024 * 20)
public class MoreUpload extends HttpServlet {
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        req.setCharacterEncoding("utf-8");
        res.setContentType("text/html; charset=UTF-8");

        Collection<Part> parts = req.getParts();
        String rootPath = req.getServletContext().getRealPath("/WEB-INF/upload");
        for (Part part : parts) {
            String fileName = part.getSubmittedFileName();
            if (fileName != null) {
                String path = FileUploadUtil.newFilePath(rootPath, fileName);
                String realName = FileUploadUtil.newFileName(fileName);
                part.write(path + File.separator + realName);
            } else {
                String username = req.getParameter(part.getName());
                System.out.println(username);
            }
        }
    }

    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        this.doPost(req, res);
    }
}
```

### 3. 文件下载

#### 3.1 概念

我们要将 `web` 应用系统中的文件资源提供给用户进行下载，首先我们要有一个页面列出上传文件目录下的所有文件，当用户点击文件下载超链接时就进行下载操作

#### 3.2 获取文件列表

```java
@WebServlet("/fileList")
public class FileList extends HttpServlet {
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        req.setCharacterEncoding("utf-8");
        res.setContentType("text/html; charset=UTF-8");
        // 返回一个文件列表
        File rootFile = new File(req.getServletContext().getRealPath("/WEB-INF/upload"));
        Map<String, String> map = new HashMap<>();

        FileUploadUtil.getFileList(rootFile, map);

        req.setAttribute("map", map);
        req.getRequestDispatcher("/filelist.jsp").forward(req, res);
    }

    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        this.doPost(req, res);
    }
}
```

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
<html>
<head>
    <title>文件列表</title>
</head>
<body>
    <table border="1" cellpadding="0" cellspacing="0" align="center">
        <caption>文件下载</caption>
        <thead>
        <tr>
            <th>文件</th>
            <th>操作</th>
        </tr>
        </thead>
        <tbody>
        <c:forEach var="map" items="${map}">
        <tr>
            <td>${map.value}</td>
            <td><a href="<c:url context='/${pageContext.request.contextPath}' value='/download?filename=${map.key}' />">下载</a></td>
        </tr>
        </c:forEach>
        </tbody>
    </table>
</body>
</html>
```

#### 3.3 下载

```java
@WebServlet("/download")
public class Download extends HttpServlet {
    protected void doPost(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        req.setCharacterEncoding("utf-8");
        res.setContentType("text/html; charset=UTF-8");

        String filename = req.getParameter("filename");
        String realName = filename.substring(filename.indexOf("_") + 1);
        String path = FileUploadUtil.newFilePath(getServletContext().getRealPath("/WEB-INF/upload"), realName);

        res.setHeader("content-disposition", "attachment;filename=" + URLEncoder.encode(realName,"UTF-8"));
        try (FileInputStream fis = new FileInputStream(path + File.separator + filename); ServletOutputStream sos = res.getOutputStream()) {
            byte[] buff = new byte[1024];
            int len = 0;
            while ((len = fis.read(buff)) != -1) {
                sos.write(buff, 0, len);
            }
        }
    }

    protected void doGet(HttpServletRequest req, HttpServletResponse res) throws ServletException, IOException {
        this.doPost(req, res);
    }
}
```

### Web 开发流程

在 `web` 开发流程中，遵守以下开发顺序

* `Dao`
  * `table`
  * `entity`
  * `DAO` 接口
  * `DAO` 实现
* `Service`
  * `Service` 接口
  * `Service` 实现（调用 `DAO` 实现类，并控制事务
* `Controller` 处理请求的 `Servlet`
  * [收集请求中的数据]
  * 调用业务功能（`Service` 实现类）
  * [在相应合适的作用域中存储数据]
  * 流程跳转（`forward | sendRedirect -> *.jsp）`
* `JSP`
  * [在作用域中获取数据]
  * 使用 `EL + JSTL` 将数据嵌套在 `HTML` 标签中
* `Filter`
  * `EncodingFilter`
  * `CheckFilter`

## 第二十七章 JavaScript（1）

### 1. 基本语法

#### 1.1 变量声明

* 在 `JavaScript` 中，任何变量都用 `var` 关键字来声明，`var` 是 `variable` 的缩写
* `var` 是声明关键字，后面跟的是变量名，语句以分号结尾
* `JavaScript` 中的关键字，不可以作为变量名

##### 关键字

![6RSwDS.md.png](https://s3.ax1x.com/2021/03/18/6RSwDS.md.png)

#### 1.2 基本类型

* 变量的基本类型有：`Number、String、Boolean、undefined、null` 五种

* 声明一个数字 `Number` 类型：`var a = 1;`

* 声明一个字符串 `String` 类型：`var a = "1"/'1';`

* 声明一个 `Boolean` 类型：`var a = true/false;`

* `undefined`：

  * 在 `Java` 中，当一个变量未被初始化的时候，它是 `null` 或者基本数据类型的默认值

  * 在 `JavaScript` 中，当一个变量未被初始化的时候，它的值是 `undefined`

  * 以下情况是 `undefined`：

    ```javascript
    var a;
    document.write(a);
    ```

#### 1.3 引用类型

* 在 `Java` 中需要类定义，然后再实例对象

* 在 `JavaScript` 中对象可以直接写出来

  ```javascript
  var student = {id: 1, name: '张三', age: 18};
  document.write(student.id);
  document.write(student.name);
  document.write(student.age);
  ```

> 事实上，student 被赋值给了一个 JSON，JSON 的全称是：JavaScript Object Notation，叫做 JavaScript 对象标记，也就是说，在 JavaScript 中，JSON 是用于标记一个对象的

#### 1.4 数组类型

数组就是和 `Java` 中理解的数组概念一致，而在 `JavaScript` 中成为 `Array` 类型：

```javascript
var students = [
  {id: 1, name: '张三', age: 18},
  {id: 2, name: '李四', age: 19},
  {id: 3, name: '刘六', age: 20}
]
document.write(students[0].id);
document.write(students[0].name);
document.write(students[0].age);
document.write('<br>');
document.write(students[1].id);
document.write(students[1].name);
```

> JavaScript 的数组中元素的类型可以不一致

#### 1.5 运算符

##### 逻辑运算

`&  ||  !`

##### 关系运算符

`==  <  <=  >  >=  !=  ===`

> * == ：判断值是否相等
> * === ：判断值和类型是否都相等

##### 单目运算

`++   --`

##### 算术运算符

`+  -  *  /  %  =  +=  -=  *=  /=  %=`

##### 三目运算符

`? :`

#### 1.6 条件分支结构

##### if-else 分支

##### switch 分支

#### 1.7 循环结构

##### for 循环

##### while 循环

##### do-while 循环

##### break

##### continue

#### 1.8 函数

**定义：**用 `function` 关键字来声明，后面是方法名称，参数列表里不写 var，整个方法不写返回值类型

```javascript
function functionName(parameters) {
  // 执行的代码
}
```

```javascript
function add(a, b) {
  return a + b;
}
var c = 1;
var d = 2;
var e = add(c, d);
document.write(e);
```

#### 1.9 常见弹窗函数

##### alert 弹框

* 这是一个只能点击确定按钮的弹窗
* 没有返回值
* 要关闭弹窗，要么点“确定”按钮，要么点 “X” 关闭

##### confirm 弹框

* 这是一个可以点击确定或者取消的弹窗
* 返回值是 `boolean` 类型
* 点击确定时，返回 `true`，点击取消或 "x"，返回 `false`

##### prompt 弹框

* 这是一个可以输入文本内容的弹窗
  * 第一个参数是提示信息，第二个参数是用户输入的默认值
* 当你点击确定的时候，返回用户输入的内容。当你点击取消或者关闭的时候，返回 `null`

#### 1.10 事件

| 事件名称      | 描述                               |
| ------------- | ---------------------------------- |
| `onchange`    | `HTML` 元素内容改变                |
| `onclick`     | 用户点击 `HTML` 元素               |
| `onmouseover` | 用户民将鼠标移入一个 `HTML` 元素中 |
| `onmousemove` | 用户在一个 `HTML` 元素上移动鼠标   |
| `onmouseout`  | 用户从一个 `HTML` 元素上移开鼠标   |
| `onkeyup`     | 键盘                               |
| `onkeydown`   | 用户按下键盘按键                   |
| `onload`      | 浏览器已完成页面的加载             |
| `onsubmit`    | 表单提交                           |

#### 1.11 正则表达式

* 正则表达式是描述字符模式的对象

* 正则表达式用于对字符串模式匹配及检索替换，是对字符串执行模式匹配的强大工具

* 语法：

  ```javascript
  var patt = new RegExp(pattern, modifiers);
  var patt = /pattern/modifiers;
  
  var re = new RegExp('\\w+');
  var re = /\w+/;
  ```

**修饰符：**用于执行区分大小写和全局匹配

| 修饰符 | 描述                                                   |
| ------ | ------------------------------------------------------ |
| `i`    | 执行对大小写不第三的匹配                               |
| `g`    | 执行全局匹配（查找所有匹配而非在找到第一个匹配后停止） |
| `m`    | 执行多行匹配                                           |

> 方括号用于查找某个范围内的字符

| 表达式             | 描述                          |
| ------------------ | ----------------------------- |
| `[abc\]`           | 查找方括号之间的任何字符      |
| `[^abc]`           | sjjra任何不在方括号之间的字符 |
| `[0-9]`            | 查找任何 0~9 的数字           |
| `(red|blue|green)` | 查找任何指定的选项            |

**元字符：**拥有特殊含义的字符

| 元字符   | 描述                               |
| -------- | ---------------------------------- |
| `.`      | 查找单个字符，除了换行和行结束符   |
| `\w`     | 查找单词字符                       |
| `\W`     | 查找非单词字符                     |
| `\d`     | 查找数字                           |
| `\D`     | 查找非数字字符                     |
| `\s`     | 查找空白字符                       |
| `\S`     | 查找非空白字符                     |
| `\b`     | 匹配单词边界                       |
| `\B`     | 匹配非单词边界                     |
| `\0`     | 查找 `NULL` 字符                   |
| `\n`     | 查找换行符                         |
| `\f`     | 查找换页符                         |
| `\r`     | 查找回车符                         |
| `\t`     | 查找制表符                         |
| `\v`     | 查找垂直制表符                     |
| `\xxx`   | 查找以八进制数 `xxx` 规定的字符    |
| `\xdd`   | 查找以十六进制数 `dd` 规定的字符   |
| `\uxxxx` | 查找以十六进制数 `xxxx` 规定的字符 |

**量词：**用以表示重复次数的含义

| 量词     | 描述                                                         |
| -------- | ------------------------------------------------------------ |
| `n+`     | 匹配任何包含至少一个 `n` 的字符串，例如：`/a+/` 匹配 `candy` 中的 `a`，`caaaaandy` 中所有的 `a` |
| `n*`     | 匹配任何包含零个或多个 `n` 的字符串。例如，`/bo*/` 匹配 `A ghost booooed` 中的 `boooo` |
| `n?`     | 匹配包含零个或一个 `n` 的字符串，例如，`/e?le?/` 匹配 `angel` 中的 `el`，`angle`  中的 `le` |
| `n{x}`   | 匹配包含  `x` 个 `n` 的序列的字符串，例如，`/a{2}/` 不匹配 `candy` 中的 `a`，但是匹配 `caandy` 中的两个 `a` |
| `n{x,}`  | `x` 是一个正整数。前面的模式 `n` 连续出现至少 `x` 次时匹配，例如，`/a{2,}` 不匹配 `candy` 中的 `a`，但是匹配 `caanndy` 和 `caaaaaandy` 中所有的 `a` |
| `n{x,y}` | `x` 和 `y` 为正整数。前面的模式 `n` 连续出现至少 `x` 次，至多 `y` 次时匹配，例如，`/a{1,3}/`  不匹配 `cndy`，匹配 `candy` 中的 `a`，`caandy` 中的两个 `a`，`caaaaaandy` 中的前面三个 `a` |
| `n[x]`   | 前面的模式 `n` 连续出现 `x` 次时匹配                         |
| `n$`     | 匹配任何结尾为 `n` 的字符串                                  |
| `^n`     | 匹配任何开头为 `n` 的字符串                                  |
| `?=n`    | 匹配任何其后紧接指定字符串 `n` 的字符串                      |
| `?!n`    | 匹配任何其后没有紧接指定字符串 `n` 的字符串                  |

**RegExp 对象方法**

| 方法      | 描述                                                         |
| --------- | ------------------------------------------------------------ |
| `compile` | 编译正则表达式                                               |
| `exec`    | 检索字符串中指定的值，返回找到的值，并确定其位置；如果没有发现匹配，则返回 `null` |
| `test`    | 检索字符串中指定的值，返回 `true` 或 `false`                 |

**支持正则表达式的 String 对象的方法**

| 方法      | 描述                           |
| --------- | ------------------------------ |
| `search`  | 检索与正则表达式相匹配的值     |
| `match`   | 找到一个或多个正则表达式的匹配 |
| `replace` | 替换与正则表达式匹配的子串     |
| `split`   | 把字符串分割为字符串数组       |

### 2. JavaScript 中的 DOM

#### 2.1 概述

* 通过 `HTML DOM`，可访问 `JavaScript HTML` 文档的所有元素
* 当网页被加载时，浏览器会创建页面的文档对象模型（`Document Object Model`）
* `HTML DOM` 模型被构造为对象的树

[![c4Op40.md.png](https://z3.ax1x.com/2021/04/17/c4Op40.md.png)](https://imgtu.com/i/c4Op40)

* 通过可编程的对象模型，`JavaScript` 获得了足够的能力来创建动态的 `HTML`
  * `JavaScript` 能够改变页面中的所有 `HTML` 元素
  * `JavaScript` 能够改变页面中的所有 `HTML` 属性
  * `JavaScript` 能够改变页面中的所有 `CSS` 样式
  * `JavaScript` 能够对页面中的所有事件做出反应

#### 2.2 查找 HTML 元素

* 通过 `JavaScript`，为了操作 `HTML` 元素，要做到下面的事情：
  * 通过 `id` 找到 `HTML` 元素
    * 在 `DOM` 中查找 `HTML` 元素的最简单的方法，是通过使用元素的 `id` 属性
    * 方法：`document.getElementById("id属性值");`
    * 如果找到该元素，则该方法将以对象（在 `x` 中）的形式返回该元素
    * 如果未找到该元素，则 `x` 将包含 `null`
  * 通过标签名找到 `HTML` 元素
    * 方法：`getElementsByTagName("合法的元素名");`
  * 通过类名找到 `HTML` 元素
    * 方法：`getElementsByClassName("class属性的值");`

#### 2.3 改变 HTML

##### 改变 HTML 输出流

`document.write()` 可用于直接向 `HTML` 输出流写内容

##### 改变 HTML 内容

使用 `innerHTML` 属性（适用于 `HTML` 的双标签）

##### 改变 HTML 属性

`document.getElementById("id").属性名 = 新属性;`

#### 2.4 CSS 变化

`对象.style.property = 新样式;`

> 注意：CSS 属性中有 - 连接的属性，换成驼峰式命名法，如：font-size 变为 fontSize

#### 3.5 DOM 事件

`HTML DOM` 允许通过触发元素的事件来执行相应的代码

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JS学习</title>
    <style>
        #first {
            width: 200px;
            height: 200px;
            background-color: gold;
        }
    </style>
</head>
<body>
    <div id="first">

    </div>
    <button onclick="changeColor()">随机改变 div 的颜色</button>
    <script>
        function changeColor() {
            var div = document.getElementById("first");
            var r = Math.ceil(Math.random() * 255);
            var g = Math.ceil(Math.random() * 255);
            var b = Math.ceil(Math.random() * 255);
            div.style.backgroundColor = "rgb(" + r + "," + g + "," + b + ")";
        }

    </script>
</body>
</html>
```

#### 2.6 EventListener

* `addEventListener()` 方法用于向指定元素添加事件句柄
* `addEventListener()` 方法添加的事件句柄不会覆盖已存在的事件句柄
* 可以向一个元素添加多个事件句柄
* 可以向同个元素添加多个同类型的事件句柄，如：两个 `click` 事件
* 可以向任何 `DOM` 对象添加事件监听，不仅仅是 `HTML` 元素，如：`window` 对象
* `addEventListener()` 方法可以更简单的控制事件（冒泡与捕获）
* 当使用 `addEventListener()` 方法时，`JavaScript` 从 `HTML` 标记中分享开来，可读性更强，在没有控制 `HTML` 标记时也可以添加事件监听

**可以使用 removeEventListener() 方法来移除事件的监听**

`addEventListener(event, function, useCapture)` 方法的参数：

| 参数名       | 描述                                    |
| ------------ | --------------------------------------- |
| `event`      | 事件的类型（如 `click` 或 `mousedown`） |
| `function`   | 事件触发后调用的函数                    |
| `useCapture` | 用于描述事件是冒泡还是捕获，可选        |

* 事件传递有两种方式：冒泡与捕获
* 事件传递定义了元素事件触发的顺序，如果将 `<p>` 元素插入到 `<div>` 元素中，用户点击 `<p>` 元素时：
  * 在冒泡方式中，内部元素的事件会先被触发，然后再触发外部元素，即：`<p>` 元素的点击事件先触发，然后会触发 `<div>` 元素的点击事件
  * 在捕获方式中，外部元素的事件会先被触发，然后才会触发内部元素的事件，即：`<div>` 元素的点击事件先触发，然后再触发 `<p>` 元素的点击事件
* `addEventListener()` 方法中的第三个参数，默认值为 `false`，即冒泡传递；当值为 `true` 时，事件使用捕获传递

#### 2.7 操作元素

##### 添加元素

* 创建元素：`document.createElement()`
* 追加元素：`appendChild()`

##### 移除元素

* `removeChild()`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JS学习</title>
    <style>
        #first {
            width: 200px;
            height: 200px;
            background-color: gold;
        }
        p {
            background-color: antiquewhite;
        }
    </style>
</head>
<body>
    <div id="first"></div>
    <br>
    <button onclick="addItem()">添加段落元素</button>
    <br>
    <button onclick="removeItem()">删除子元素</button>
    <script>
        function addItem() {
            var p = document.createElement("p");
            p.style.position = "relative";
            p.style.top = '15px';
            var text = document.createTextNode("这是一个段落");
            p.appendChild(text);

            var div = document.getElementById("first");
            div.appendChild(p);
        }
        function removeItem() {
            var div = document.getElementById("first");
            var child = div.children[0];
            if (child != null)
                div.removeChild(child);
        }
    </script>
</body>
</html>
```

### 3. 浏览器 BOM

* 浏览器对象模型（`BOM-Browser Object Model`）使 `JavaScript` 有能力与浏览器 “对话”
* 由于现代浏览器已经（几乎）实现了 `JavaScript` 交互性方面的相同方法和属性，因此常被认为是 `BOM` 的方法和属性

#### 3.1 window

* 所有浏览器都支持 `window` 对象，它表示浏览器窗口
* 所有 `JavaScript` 全局对象、函数以及变量均自动成为 `window` 对象的成员
* 全局变量是 `window` 对象的属性
* 全局函数是 `window` 对方的方法
* 甚至 `HTML DOM` 的 `document` 也是 `window` 对象的属性之一

##### window 的尺寸

* 对于 `Internet Explorer、Chrome、Firefox、Opera` 以及 `Safari`：

  * `window.innerHeight`：浏览器容器的内部高度（包括滚动条）
  * `window.innerWidth`：浏览器容器的内部宽度（包括滚动条）

* 对于 `Internet Explorer 8、7、6、5`：

  * `document.documentElement.clientHeight`
  * `document.documentElement.clientWidth`

  或者

  * `document.body.clientHeight`
  * `document.body.clientWidth`

##### Window Screen

* 可用宽度：`screen.availWidth` 属性返回访问者屏幕的宽度，以像素为单位，减去界面特性，比如窗口任务栏
* 可用高度：`screen.availHeight` 属性返回访问都屏幕的高度，以wqge为单位，减去界面特性，比如窗口任务栏

##### Window Location

该对象用于获得当前页面的地址（`URL`），并把浏览器重定向到新的页面

该对象在编写时不使用 `window` 这个前缀：

* `location.hostname`：`web` 主机的域名
* `location.pathname`：当前页面的路径和文件名
* `location.port`：`web` 主机的端口（80 或 443）
* `location.protocol`：所使用的 `web` 协议（`http://` 或 `https://`）
* `location.href`：返回当前页面的 `URL`
* `location.assign()`：加载新的文档

##### Window History

该对象在编写时可不使用 `window` 这个前缀

* `history.back()`：回退，与浏览器点击后退按钮作用相同
* `history.forward()` ：前进，与浏览器点击前进按钮作用相同

##### Window Navigator

用于获取浏览器等信息

* `navigator.appCodeName`：浏览器代号
* `navigator.appName`：浏览器名称
* `navigator.appVersion`：浏览器版本
* `navigator.cookieEnabled`：启用 `Cookies`
* `navigator.paltform`：硬件平台
* `navigator.userAgent`：用户代理
* `navigator.systemLanguage`：用户代理语言

#### 3.2 定时器

* 定义定时器
  * `setInterval('调用函数'，毫秒时间)`：每间隔固定毫秒值就执行一次函数
  * `setTimeout('调用函数'，毫秒时间)`：在固定时间之后执行一次调用函数
* 关闭定时器
  * `clearInterval(定时器名称)`
  * `clearTimeout(定时器名称)`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>JS学习</title>
    <style>
        #first {
            width: 200px;
            height: 200px;
            background-color: gold;
        }
    </style>
</head>
<body>
    <div id="first"></div>
    <br>
    <button onclick="stop()">停止颜色改变</button>
    <script>
        function changeColor() {
            var div = document.getElementById("first");
            var r = Math.ceil(Math.random() * 255);
            var g = Math.ceil(Math.random() * 255);
            var b = Math.ceil(Math.random() * 255);
            div.style.backgroundColor = "rgb(" + r + "," + g + "," + b + ")";
        }
        var itv = window.setInterval("changeColor()", 1000);
        function stop() {
            clearInterval(itv);
        }
    </script>
</body>
</html>
```

## 第二十七章 JavaScript

### 第一部分 语言核心

### 0. 概述

完整的 `JavaScript` 包含以下几个部分：`ECMAScript`、`DOM`、`BOM`

#### ECMAScript

它只是对实现规范描述的所有方面的一门语言的称呼。要成为 `ECMA-262` 实现，必须满足下列条件：

* 支持 `ECMA-262` 中描述的所有 “类、值、对象、属性、函数，以及程序语法及语义”
* 支撑 `Unicode` 字符标准

此外，符合性实现还可以满足下列要求：

* 增加 `ECMA-262` 中未提及的 “额外的类型、值、对象、属性和函数”。`ECMA-262` 所说的这些额外内容主要指规范中未给出的新对象或对象的新属性
* 支持 `ECMA-262` 中没有定义的 “程序和正则表达式语法”（意思是允许修改和扩展内置的正则表达式特性）

#### DOM

`DOM（Document Object Model）`：文档模型对象，是一个应用编程接口，用于在 `HTML` 中使用扩展的 `XML`。

 `DOM` 将整个页面抽象为一组分层节点，`HTML` 或 `XML` 页面的每个组成部分都是一种节点，包含不同的数据，例如：

```html
<html>
  <head>
    <title>Sample Page</title>
  </head>
  <body>
    <p>Hello World!</p>
  </body>
</html>
```

上面的代码可以通过 `DOM` 表示为一组分层节点：

[![6cyfI0.png](https://s3.ax1x.com/2021/03/17/6cyfI0.png)](https://imgtu.com/i/6cyfI0)

#### BOM

`BOM(Broswer Object Model)`：浏览器对象模型，用于支持访问和操作浏览器的窗口。

#### 小结

`JavaScript` 是一门用来与网页交互的脚本语言，包含以下三个组成部分：

* `ECMAScript`：由 `ECMA-262` 定义并提供核心内容
* 文档对象模型（`DOM`）：提供与网页内容交互的方法和接口
* 浏览器对象模型（`BOM`）：提供与浏览器交互的方法和接口

#### &lt;script&gt; 标签

`script` 元素的 8 个属性：

| 属性名        | 是否可选 | 解释                                                         |
| ------------- | -------- | ------------------------------------------------------------ |
| `async`       | 可选     | 表示应该立即开始下载脚本，但不能阻止页面上的其它动作，比如下载资源或者等待其它脚本加载。只对外部脚本文件有效 |
| `charset`     | 可选     | 使用 `src` 属性指定的代码字符集。这个属性很少使用，因为大多数浏览器不在乎它的值 |
| `crossorigin` | 可选     | 配置相关请求的 `CORS`（跨源资源共享）设置。默认不使用 `CORS` |
| `defer`       | 可选     | 表示脚本可以延迟到文档完全被解析和显示之后再执行。只对外部脚本文件有效 |
| `integrity`   | 可选     | 允许比对接收到的资源和指定的加密签名以验证子资源的完整性     |
| `language`    | 废弃     | 用于表示代码块中的脚本语言                                   |
| `src`         | 可选     | 表示包含要执行的代码的外部文件                               |
| `type`        | 可选     | 代替 `language`，表示代码块中脚本语言的内容类型              |

使用 `<script>` 的两种方式：

* 通过它直接在网页中嵌入 `JavaScript` 代码
  * 这种方式下，代码中不能出现字符串：`“</script>”`
* 通过它在网页中包含外部 `JavaScript` 文件
  * 要包含外部文件中的 `JavaScript`，就必须使用 `src` 属性，这个属性的值是一个 `URL`，指向包含 `JavaScript` 代码的文件

##### 标签位置

* 原来 `<script>` 标签都在 `<head>` 中放置，便于管理，但是会影响页面加载速度，影响用户体验
* 建议放在 `<body>` 标签内容的最后，`</body>` 标签的前面

##### 推迟执行脚本

`defer` 属性只对外部脚本才有效，会使脚本被延迟到整个页面都解析完毕之后再执行

### 1. 词法结构

#### 1.1 字符集

`JavaScript` 程序是用 `Unicode` 字符集编写的

##### 1.1.1 区分大小写

`JavaScript` 是区分大小写的语言，关键字、变量名、函数名和所有的标识符都区分大小写

> 注意：HTML 不区分大小写

##### 1.1.2 空格、空行、格式控制符

各种表示空格的字符：

| 含义       | 转义字符 |
| ---------- | -------- |
| 普通空格符 | `\u0020` |
| 水平制表符 | `\u0009` |
| 垂直制表符 | `\u000B` |
| 换页符     | `\u000C` |
| 不中断空白 | `\u00A0` |
| 字节序标记 | `\uFEFF` |

表示行结束符的字符：

| 含义     | 转义字符 |
| -------- | -------- |
| 换行符   | `\u000A` |
| 回车符   | `\u000D` |
| 行分隔符 | `\u2028` |
| 段分隔符 | `\u2029` |

> 注意：回车符加换行符在一起被解析为一个单行结束符

##### 1.1.3 Unicode 转义序列

在有些计算机硬件和软件里，无法显示或输入 `Unicode` 字符全集，为了支持那些使用老旧技术的程序员，`JavaScript` 定义了一种特殊序列，使用 6 个 `ASCII` 码字符来代表任意 16 位 `Unicode` 内码。

这些 `Unicode` 转义序列均以 `\u` 为前缀，其后跟随 4 个十六进制数。

这种 `Unicode` 转义写法可以用在 `JavaScript` 字符串直接量、正则表达式直接量和标识符中（关键字除外）。

```javascript
"café" === "caf\u00e9"  // true
```

#### 1.2 注释

`JavaScript` 支持两种格式的注释：

* 单行注释：`//`，在行尾 `//` 之后的文本都会被 `JavaScript` 当作注释忽略掉
* 多行注释：`/* 注释内容 */`，`/* ` 和 `*/` 之间的文本会被当作注释
  * 这种注释可以跨行书写
  * 这种注释不能够嵌套

#### 1.3 直接量

所谓直接量（`literal`），就是程序中直接使用的数据值，下面的都是直接量：

```javascript
12							// 数字
1.2							// 小数
"hello world"		// 字符串文本
'Hi'						// 也是字符串
true						// 布尔值
false						// 另一个布尔值
/javascript/gi	// 正则表达式直接量（用作模式匹配）
null						// 空
{x:1, y:2}			// 对象
[1, 2]					// 数组
```

#### 1.4 标识符和保留字

**标识符**就是一个名字，用来对变量和函数进行命名，或者用作代码中某些循环语句的跳转位置的标记。

标识符命名规则：

* 必须以 **字母、下划线、美元符** 开始
* 后续的字符可以是 **字母、下划线、美元符、数字**
* 标识符不能是保留字

> 数字不允许作为标签符的首字符出现，以便 `JavaScript` 可以轻易区分开标识符和数字

**保留字**：`JavaScript` 把一些标识符拿出来用做自己的关键字，因此，这些关键字就不能在程序中被用作标签符了。

[![6RSwDS.md.png](https://s3.ax1x.com/2021/03/18/6RSwDS.md.png)](https://imgtu.com/i/6RSwDS)

`JavaScript` 的具体实现可能定义独有的全局变量和函数，每一种特定的 `JavaScript` 运行环境都自己的一个全局属性列表，**这一点是需要牢记的**

#### 1.5 可选的分号

和其它许多编程语言一样，`JavaScript` 使用分号将语句分隔开

可以省略分号的地方：

* 语句各自独占一行
* 程序结尾
* 右花括号（`}`）之前

> * `return、break、continue` 和随后的表达式之间不能有换行
> * `++、--` 在做后缀表达式时，和前面的表达式应该在一行

### 2. 类型、值、变量

`JavaScript` 的数据类型分为两类：

* 原始类型
  * 数字
  * 字符串
  * 布尔值
  * `null`（空）
  * `undefined`（未定义）
* 对象类型
  * 对象（`Object`）是属性（`property`）的集合，每个属性都由 `键/值` 对组成
  * 特殊对象——全局对象（`global object`）
  * 特殊对象——数组，表示带编号的值的有序集合
  * 特殊对象——函数，是具有与它相关联的可执行代码的对象

#### 2.1 数字

和其它编程语言不同，`JavaScript` 不区分整数值和浮点数值，所有数字均用浮点数值表示。`JavaScript` 能表示的最大数值是：$\pm 1.7976931348623157 \times 10^{308}$ ，最小值是：$\pm 5 \times 10^{-324} $

按照 `JavaScript` 中的数字格式，能够表示整数的范围是：$-2^{53}$ ~ $2^{53}$ ，包含边界值

> 需要注意的是：`JavaScript` 中的实际操作（比如数组索引、位操作符）则是基于 32 位整数

##### 2.1.1 整形直接量

用一个数字序列表示一个十进制数：

```javascript
0
3
10000
```

`JavaScript` 同样能识别十六进制值——以 `0x` 或 `0X` 为前缀，其后跟随十六进制数串的直接量：

```javascript
0xff
0xCAFE91
```

> 有些 `JavaScript` 的实现不支持八进制，`ECMAScript 6` 的严格模式下，八进制是禁止的。因此，最后不要使用以 0 为前缀的整形直接量

##### 2.1.2 浮点直接量

* 浮点直接量可以含有小数点
* 可以使用指数记数法表示浮点直接量
  * 语法：`[digits][.digits][(E|e)[(+|-)]digits]`

```javascript
3.14
2345.789
.3333333
6.02e23
1.4738223E-32
```

##### 2.1.3 算术运算

运行符：

| 运算符 | 含义       |
| ------ | ---------- |
| +      | 加法运算符 |
| -      | 减法运算符 |
| *      | 乘法运算符 |
| /      | 除法运算符 |
| %      | 求余运算符 |

**上溢：**当数字运算结果超过了 `JavaScript` 所能表示的数字上限，结果为一个特殊的无穷大值：`Infinity`；当负数的值超过了 `JavaScript` 所能表示的最大负数范围，结果为负无数大：`-Infinity`

**下溢：**当运算结果无限接近于 0 并比 `JavaScript` 所能表示的最小值还小的时候发生的一种情形。这种情况下，`JavaScript` 会返回 0

**被零整除：**在 `JavaScript` 中并不报错，只是简单的返回无穷大（$\pm$ `Infinity`）

**零除以零：**没有意义，返回一个非数字（`not-a-number`）的值，用 `NaN` 表示。**无穷大除以无穷大、给任意负数做开方运算、算术运算符与不是数字或无法转换为数字的操作数一起使用时，都将返回 NaN**

_**NaN 与任何值都不相等，包括自身**_

判断一个值是 `NaN` 的方法：`x != x` 或者 `isNaN(x)`

`isFinite(参数)`：在参数不是 `NaN、Infinity、-Infinity` 时返回 `true`

##### 2.1.4 二进制和四舍五入错误

实数有无数个，但 `JavaScript` 通过浮点数的形式只能表示其中有限的个数。也就是说，当在 `JavaScript` 使用实数的时候，常常只是真实值的一个近似表示。

```javascript
var x = .3 - .2;
var y = .2 - .1;
x == y						// false，两值不相等
x == .1						// false，.3 - .2 不等于 .1
y == .1						// true，.2 - .1 等于 .1
```

> 以上的问题不只在 `JavaScript` 中才会出现，在任何使用二进制浮点数的编程语言中都会有这个问题

##### 2.1.5 时间和日期

* `JavaScript` 语言核心包括 `Date()` 构造函数，用来创建表示时间和日期的对象
* 日期对象的方法为日期的计算提供了简单的 `API`

日期对象简单用法：

```javascript
var then = new Date(2021, 2, 18);					// 2021年3月18日
var later = new Date(2021, 2, 18, 17, 10, 30);		// 同一天，当地时间下午 17:10:30
var now = new Date();											// 当前日期和时间
var elapsed = now - then;									// 日期减法，计算间隔的毫秒数
later.getFullYear();											// 2021
later.getMonth();													// 2：从 0 开始计数的月份
later.getDate();													// 18：从 1 开始计数的开数
later.getDay();														// 4：得到星期几，0代表星期日
later.getHours();													// 22：得到当地小时数
```

#### 2.2 文本

* 字符串是一组由 16 位值组成的不可变的有序序列
* 字符串的索引从 0 开始
* `JavaScript` 中并没有表示单个字符的字符型，要表示一个 16 位值，只需要将其赋值给字符串变量即可，这个字符串长度为 1

##### 2.2.1 字符串直接量

字符串直接量：由单引号或又引号括起来的字符序列

```javascript
""								// 空字符串：包含 0 个字符
'testing'
"3.14"
'name="myForm"'
"Are you OK?"
"This string \nhas two lines"
```

##### 2.2.2 转义字符

在 `JavaScript` 字符串中，反斜线 `\` 有着特殊的用途，反斜线符号后加一个字符，就不再表示它们的字面含义了。

| 转义字符 | 含义                                        |
| -------- | ------------------------------------------- |
| `\0`     | `NUL` 字符（`\u0000`）                      |
| `\b`     | 退格符（`\u0008`）                          |
| `\t`     | 水平制表符（`\u0009`）                      |
| `\v`     | 换行符（`\u000A`）                          |
| `\n`     | 垂直制表符（`\u000B`）                      |
| `\f`     | 换页符（`\u000C`）                          |
| `\r`     | 回车符（`\u000D`）                          |
| `\"`     | 双引号（`\u0022`）                          |
| `\'`     | 撇号或单引号（`\u0027`）                    |
| `\\`     | 反斜线（`\u005C`）                          |
| `\xXX`   | 由两位十六进制 `XX` 指定的 `Lantin-1` 字符  |
| `\uXXXX` | 由四位十六进制 `XXXX` 指定的 `Unicode` 字符 |

##### 2.2.3 字符串的使用

* 字符串连接：`+`
* 字符串长度：`string.length`
* 访问单个字符：`string[index]`

> 所有对字符串改变的操作，都会返回一个新的字符串，也就是说，字符串是不可变的

常用方法：

```javascript
var s = 'hello,world'						// 定义一个字符串
s.charAt(0)												// 'h'，第一个字符串
s.charAt(s.length - 1)						// 'd'，最后一个字符串
s.substring(1, 4)									// 'ell',第 2 ~ 4 个字符
s.indexOf('l')										// 2，字符 l 首次出现的位置
s.lastIndexOf('l')								// 10，字符 l 最后一次出现的位置
s.indexOf('l', 3)									// 3，在位置 3 及以后首次出现字符 l 的位置
s.split(',')											// ['hello', 'world']，分割成子串
s.replace('h','H')								// 'Hello,world'，全文字符替换
s.toUpperCase()										// 'HELLO,WORLD'
```

##### 2.2.4 模式匹配

`JavaScript` 定义了 `RegExp()` 构造函数，用来创建表示匹配模式的对象。这些模式称为 ”正则表达式“（`regular expression`），`JavaScript` 采用 `Perl` 中的正则表达式语法。

正则表达式直接量：

* 在两条斜线之间的文本构成了一个正则表达式直接量
* 第二条斜线之后也可以跟随一个或多个字母，用来修饰匹配模式的含义

```javascript
/^HTML/							// 匹配以 HTML 开始的字符串
/[1-9][0-9]*/				// 匹配一个非零数字，后面是任意个数字
/\bjavascript\b/i		// 匹配单词 javascript，忽略大小写
```

正则表达式示例：

```javascript
var text = "testing: 1, 2, 3";				// 文本
var pattern = /\d+/g;									// 匹配所有包含一个或多个数字的实例
pattern.test(text);										// true，匹配成功
text.search(pattern);									// 9，首次匹配成功的位置
text.match(pattern);									// ['1', '2', '3']，所有匹配成功的数组
text.replace(pattern, '#');						// 'testing: #, #, #'
text.split(/\D+/);										// ['', '1', '2', '3']，用非数字字符截取字符串
```

#### 2.3 布尔值

布尔值指代真或假、开或关、是或否，这个类型只有两个值：`true`、`false`

**任意的 JavaScript 的值都可以转换为布尔值**

下面这些值会被转换成 `false`：

```javascript
undefined
null
0
-0
NaN
""
```

除上面的 6 个值以外的其它值，都会转换成 `true`

#### 2.4 null、undefined

* `null` ：是一个特殊的对象值，含义是 “非对象”，用来描述 “空值”
  * 是关键字

* `undefined`：是变量的一种取值，表示变量没有初始化
  * 是预定义的全局变化，不是关键字
  * 如果要查询对象属性或数组元素的值时返回 `undefined` 则说明这个属性或元素不存在
  * 如果函数没有返回任何值，则返回 `undefined`
  * 函数引用没有提供实参时，函数形参的值也只会得到 `undefined`

> 注意：如果使用 null == undefined，返回的是 true
>
> ​           要判断 null 和 undefined 的相等性，需要使用 null === undefined 进行判断

#### 2.5 全局对象

全局对象（`global object`）在 `JavaScript` 中有着重要的用途：

* 全局对象的属性是全局定义的符号，`JavaScript` 程序可以直接使用
* 当 `JavaScript` 解释器启动时（或者任何 `Web` 浏览器加载新页面时），它将创建一个全新的全局对象，并给它一组定义的初始属性
  * 全局属性，比如：`undefined、Infinity、NaN`
  * 全局函数，比如：`isNaN()、parseInt()、eval()`
  * 构造函数，比如：`Date()、RegExp()、String()、Object()、Array()`
  * 全局对象，比如：`Math、JSON`

在代码的最顶级——不在任何函数内的 `JavaScript` 代码——可以使用 `JavaScript` 关键字 `this` 来引用全局对象：

`var global = this;  // 定义一个引用全局对象的全局变量`

在客户端 `JavaScript` 中，在其表示的浏览器窗口中的所有 `JavaScript` 代码中，`Window` 对象充当了全局对象。这个全局 `Window` 对象有一个属性 `window` 引用其自身，它可以代替 `this` 来引用全局对象

#### 2.6 包装对象

本章一开始就说了，`JavaScript` 的数据类型分为：**原始类型**、**对象类型**，对象类型有方法和属性，原始类型不应该有方法和属性。但是，在讲解字符文本（原始类型）时，也讲解了它们的一些属性和方法。它们的方法到底是怎么来的？

原因是：只要引用了字符串的属性，`JavaScript` 就会将字符串值通过调用 `new String(s)` 的方式转换为对象，这个对象继承了字符串的方法，并被用来处理属性的引用。一旦属性引用结束，这个新创建的对象就会销毁。

同字符串一样，数字和布尔值也各具有各自的方法：通过 `Number()` 和 `Boolean()` 构造函数创建一个临时对象，这些方法的调用均是来自于这个临时对象。

**`null` 和 `undefined` 没有包装对象**

查看如下的示例，思考最终的执行结果：

```javascript
var s = 'test';
s.len = 4;
var t = s.len;
console.log(t);    // 结果是？
```

#### 2.7 不可变的原始值和可变的对象引用

原始值是不可变的：任何方法都无法更改（或 “突变”）一个原始值。要请注意的原始值是字符串，字符串的很多操作看上去像是修改了原始值，其实都只是返回了一个新的字符串：

```javascript
var s = 'hello';			// 原始字符串小写
s.toUpperCase();			// 返回一个新的大写的字符串
s;										// 仍然是 hello，没有发生任何变化
```

**原始类型的比较是值的比较：只有值相等，两个原始类型的变量才相等**

**对象的比较是引用的比较：当且仅当它们引用同一基对象时，它们才相等**

#### 2.8 类型转换

当 `JavaScript` 期望使用某个类型的值时，程序可以提供任意类型的值，`JavaScript` 将根据需要自行转换类型。

转换的规则如下：

[![6WoffS.md.png](https://s4.ax1x.com/2021/03/19/6WoffS.md.png)](https://imgtu.com/i/6WoffS)

注意：

* 转换为数字的情况比较微秒，那些以数字表示的字符串可以直接表示为数字，也允许在开始和结尾处带有空格，但在开始和结尾处的任意非空字符都不会被当成数字直接量的一部分，进而造成字符串转换为数字的结果为 `NaN`
* 转换为数字时：`true` 转换为 1， `false` 转换为 0

##### 2.8.1 转换和相等性

由于 `JavaScript` 可以做灵活的类型转换，因此其 `==` 运算符也随相等的含义灵活多变。例如：下面的比较结果均为 `true`：

```javascript
null == undefined		// 这两个值被认为相等
"0" == 0				// 在比较之前字符串转换为数字
0 == false				// 在比较之前布尔值转换为数字
"0" == false			// 在比较之前字符串和布尔值都转换为数字
```

> 注意：一个值转换为另一个值并不意味着这两个值相等

##### 2.8.2 显式类型转换

做显式类型转换最简单的方法就是使用：`Boolean()、Number()、String()、Object()` 函数。当不通过 `new` 运算符调用这些函数时，它们会作为类型转换函数并按照 `2.8` 节一开始所描述的规则做类型转换：

```javascript
Number("3")				// 3
String(false)			// "false"
Boolean([])				// true
Object(3)				// new Number(3)
```

> 除了 `null` 和 `undefined` 以外的任何值都具有 `toString()` 方法，这个方法的执行结果通常和 `String()` 方法的返回结果一致

> 如果试图把 `null` 和 `undefined` 转换为对象，会抛出一个类型错误。`Object` 在这种情况下不会抛出异常，它仅简单的返回一个新创建的空对象

**运算符的隐式类型转换：**

* 二元 `+` 运算符的一个操作数是字符串，它会把另一个操作数转换为字符串；如果一个操作数是对象，则 `JavaScript` 使用特殊的方法将对象转换为原始值，而不是使用其它运算符的方法执行对象到数字的转换
* 一元 `+` 运算符将其操作数转换为数字
* 一元 `!` 运算符将其操作数转换为布尔值并取反

```javascript
x + ''		// 等价于 String(x)
+x			// 等人于 Number(x)，也可以是 x - 0
!!x			// 等人于 Boolean(x)。注意是双叹号
```

**数字与字符串之间的相互转换**

* **整数→字符串：** `Number` 类定义的 `toString()` 方法可以接收表示转换基数的可选参数

  ```javascript
  var n = 17;
  var binary_str = n.toString(2);		// 转换为 '10001'
  var octal_str = n.toString(8);		// 转换为 '021'
  var hex_str = n.toString(16);		// 转换为 '0x11'
  var decimal_str = n.toString();		// 转换为 '17'
  ```

* **小数→字符串：**

  * 控制输出中小数点的位置：`toFixed()`
  * 控制输出中小数的有效位数：`toPrecision()`
  * 控制输出是否需要指数计数法：`toExponential()`

  ```javascript
  var n = 123456.789;
  n.toFixed(0);			// '123457'
  n.toFixed(2);			// '123456.79'
  n.toFixed(5);			// '123456.78900'
  n.toExponential(1);		// '1.2e+5'
  n.toExponential(3);		// '1.235e+5'
  n.toPrecision(4);		// '1.235e+5'
  n.toPrecision(7);		// '123456.8'
  n.toPrecision(10);		// '123456.7890'
  ```

* **字符串→数字：**

  * `parseInt()`：将一个字符串转换为整数直接量
  * `parseFloat()`：将一个字符串转换为小数直接量
  * 这两个方法都是全局函数，不属性任何类的方法
  * 这两个方法都会跳过任意数量的前导空格，尽可能解析更多的数字字符
  * 如果第一个非空格字符是一个非法的数字直接量，将最终返回 `NaN`

  ```javascript
  parseInt('3 sdf sdf');				// 3
  parseFloat('  3.14 sdf ladkf');		// 3.14
  parseInt('-12.34');					// -12
  parseInt('0xFF');					// 255
  parseInt('-0xFF');					// -255
  parseFloat('.1');					// 0.1
  parseInt('0.1');					// 0
  parseInt('.1');						// NaN，整数不能以 . 开始
  parseFloat('$72.47');			// NaN，数字不能以 $ 开始
  ```

  > `parseInt()` 可以接收第二个可选参数，这个参数指定数字转换的基数，合法的取值范围是 2 ~ 36

##### 2.8.3 对象转换为原始值

* **对象→布尔值：**
  * 所有的对象（包括数组和函数）都转换为 `true`
* **对象→字符串：**
  * 如果对象具有 `toString()` 方法，则调用这个方法。如果它返回一个原始值，`JavaScript` 将这个原始值转换为字符串（如果本身不是字符串的话），并返回这个字符串的结果
  * 如果对象没有 `toString()` 方法，或者这个方法并不返回一个原始值，那么 `JavaScript` 会调用 `valueOf()` 方法。如果存在这个方法，则 `JavaScript` 调用它。如果返回的是原始值，`JavaScript` 将这个值转换为字符串（如果本身不是字符串的话），并返回这个字符串结果
  * 否则，`JavaScript` 无法从 `toString()` 或者 `valueOf()` 获得一个原始值，因此这时它将抛出一个类型错误异常
* **对象→数字：**
  * 如果对象具有 `valueOf()` 方法，后者返回一个原始值，则 `Javascript` 将这个原始值转换为数字（如果有需要的话）并返回这个数字
  * 否则，如果对象具有 `toString()` 方法，后者返回一个原始值，则 `JavaScript` 将其转换并返回
  * 否则，`JavaScript` 抛出一个类型错误异常

#### 2.9 变量声明

使用一个变量之前应当先声明，变量是使用关键字 `var` 来声明的：

```javascript
var i;				// i -> undefined
var num;			// num -> undefined
var i, sum;         // i,num -> undefined
var msg = 'hello';	// msg -> 'hello'
```

> `JavaScript` 变量可以是任意数据类型

* 在严格模式下，给一个没有声明的变量赋值会报错
* 非严格模式下，给一个没有声明的变量赋值，`Javascript` 会给全局对象创建一个同名属性
  * **使用未声明的变量是一个非常不好的习惯，应该始终使用 var 来声明变量**

#### 2.10 变量作用域

一个变量的作用域（`scope`）是程序源代码中定义这个变量的区域。

* 全局变量拥有全局作用域，在 `JavaScript` 代码中的任何地方都是有定义的
* 在函数内声明的变量只在函数体内有定义，它们是局部变量，作用域是局部的
* 函数参数也是局部变量，它们只在函数体内有定义

```javascript
var scope = 'global scope';			// 全局变量
function checkScope() {
    var scope = 'local scope';		// 局部变量
    function nested() {
        var scope = 'nested scope';	// 嵌套作用域内的局部变量
        return scope;				// 返回当前作用域内的值
    }
    return nested();					
}

checkScope();						// 嵌套作用域
```

##### 2.10.1 函数作用域和声明提前

函数作用域：变量在声明它们的函数体以及这个函数体嵌套的任意函数体内都是有定义的。

上句话也就意味着：变量在声明前基本已经可以用了——声明提前

```javascript
var scope = 'global';
function f() {
    console.log(scope);		// 输出 'undefined'，而不是 'global'
    var scope = 'local';	// 变量在这里赋初值，但变量本身在函数体内任何地方均是有定义的
    console.log(scope);		// 'local'
}
```

> 良好的编程习惯：将变量声明放在函数体顶部，这样会非常清晰的反应真实的变量作用域

##### 2.10.2 作为属性的变量

* 当使用 `var` 声明一个变量时，创建的这个属性是不可配置的，即，无法使用 `delete` 运算符删除
* 当没有使用严格模式并给一个未定义的变量赋值的话，`JavaScript` 会自动创建一个全局变量，以这种方式创建的变量是全局对象的正常的可配置的属性，可以被删除

```javascript
var temp = 1;						// 声明一个不可删除的全局变量
tmp = 2;								// 创建全局对象的一个可删除属性
this.tmp2 = 2;					// 同上
delete temp;						// false：变量并没有被删除
delete tmp;							// true：变量被删除
delete this.tmp2;				// true：变量被删除
```

##### 2.10.3 作用域链（重要）

* 每一段 `JavaScript` 代码（全局代码或函数）都有一个与之相关联的作用域链（`scope chain`）
* 这个作用域链是一个对象列表或链表，这组对象定义了这段代码 “作用域中” 的变量
* 当 `JavaScript` 需要查找变量 `x` 的值时（这个过程叫做变量解析（`variable resolution`）），它会从链中的第一个对象开始查找，如果这个对象有一个名为 `x` 的属性，则会直接使用这个属性的值，如果第一个对象中不存在名为 `x` 的属性，则会继续查找下一个对象，以此类推。如果作用域上没有任何一个对象含有属性 `x`，那么就认为这段代码的作用域链上不存在 `x`，并最终抛出一个引用错误（`RefferenceError`）异常

### 3. 表达式和运算符

**表达式（expression）：**`JavaScript` 中的一个短语，`JavaScript` 解释器会将其计算（`evaluate`）出一个结果。

表达式举例：变量名，数组访问表达式，函数调用表达式等等

#### 3.1 原始表达式

原始表达式是表达式的最小单位——它们不再包含其它表达式。`JavaScript` 中的原始表达式包含常量或直接量、关键字和变量

```javascript
// 直接量表达式
1.23
'hello'
/pattern/
  
// 保留字表达式
true
false
null
this

// 变量表达式
i
sum
undefined
```

#### 3.2 对象和数组的初始化表达式

对象和数组初始化表达式实际上是一个新创建的对象和数组，也可以叫做：对象直接量、数组直接量。

数组初始化表达式：通过一对方括号和其内由逗号隔开的列表构成的。初始化的结果是一个新创建的数组，数组的元素是逗号分隔的表达式的值：

```javascript
[]								// 一个空数组：[]内留空即表示该数组没有任何元素
[1+2, 3+4]				// 拥有两个元素的数组，第一个是 3，第二个是 7
```

数组直接量中的列表逗号之间的元素可以省略，这时省略的空位会填充值 `undefined`：

```javascript
var arr = [1,,,,5];
```

> 数组直接量的元素列表结尾处可以留下单个逗号，这时并不会创建一个新的值为 undefined 的元素

对象初始化表达式和数组初始化表达式非常类似，只是方括号被花括号代替，并且每个子表达式都包含一个属性名和一个冒号作为前缀：

```javascript
var p = {x: 2.3, y:-1.2}				// 一个拥有两个属性成员的对象
var q = {};											// 一个空对象
q.x = 2.3; q.y = -1.2;					// q 的属性成员和 p 的一样
```

> 对象和数组都可以进行嵌套

#### 3.3 函数定义表达式

**函数定义表达式定义一个 JavaScript 函数，表达式的值是这个新定义的函数**

一个典型的函数定义表达式包含关键字 `function`，跟随其后的是一对圆括号，括号内是一个以逗号分割的列表，列表含有 0 个或多个标识符（参数名），然后再跟随一个由花括号包裹的 `JavaScript` 代码段（函数体）：

```javascript
// 这个函数返回传入参数值的平方
var square = function(x) {return x * x;}
```

#### 3.4 属性访问表达式

`JavaScript` 为属性访问定义了两种语法：

```javascript
expression.indetifier						// 表达式后跟随一个句点和标识符
expression[ expression ]				// 使用方括号，方括号内是另外一个表达式（这种方法适用于对象和数组）
```

```javascript
var o = {x:1, y:{z:3}};					// 一个对象
var a = [o, 4, [5, 6]];					// 一个包含这个对象的数组
o.x															// 1：表达式 o 的 x 属性
o.y.z														// 3：表达式 o.y 的 z 属性
o['x']													// 1：对象 o 的 x 属性
a[1]														// 4：表达式 a 中索引为 1 的元素
a[2]['1']												// 6：表达式 a[2] 中索引为 1 的元素
a[0].x													// 1：表达式 a[0] 的 x 属性
```

> * 如果属性名称是一个保留字或者包含空格或标点符号，或是一个数字（对于数组来说），则必须使用方括号的写法
> * 当属性名是通过运算得出的值而不是固定的值的时候，必须使用方括号写法

#### 3.5 调用表达式

`JavaScript` 中的调用表达式（`invocation expression`）是一种调用（或执行）函数或方法的语法表示：它以一个函数表达式开始，这个函数表达式指代了要调用的函数。函数表达式后跟随一对圆括号，括号内是一个以逗号隔开的参数列表，参数可以有 0 个，也可以有多个：

```javascript
f(0)					// f 是一个函数表达式，0 是一个参数表达式
Math.max(x,y,z)			// Math.max 是一个函数，x，y，z 是参数
a.sort()				// a.sort 是一个函数，它没有参数
```

#### 3.6 对象创建表达式

对象创建表达式创建一个对象并调用一个函数（这个函数称作构造函数）初始化新对象的属性：

```javascript
new Object()
new Point(2, 3)

// 如果一个对象创建表达式不需要传入任何参数给构造函数的话，那么这对空圆括号可以省略

new Object
new Date
```

#### 3.7 运算符

[![6oXtsI.png](https://z3.ax1x.com/2021/03/22/6oXtsI.png)](https://imgtu.com/i/6oXtsI)

##### 3.7.1 操作数的个数

* 大多数操作符是 二元运算符
* 小部分是 一元运算符（例如：`-、!`）
* 只有一个三元运算符：`? :`

##### 3.7.2 操作数类型和结果类型

`JavaScript` 运算符通常会根据需要对操作数进行类型转换（转换规则参照 `2.8` 节内容）

##### 3.7.3 左值

左值：表达式只能出现在赋值运算符的左侧

##### 3.7.4 运算符的副作用

有副作用的运算符：

`=、++、--、delete`

##### 3.7.5 运算符优先级

运算符优先级在上面的表格中，从上到下依次递减。

> 小技巧：
>
> * 如果你真的不确定你所使用的运算符的优先级，最简单的方法就是使用圆括号来强行指定运算次序。
> * 有些重要规则需要熟记：乘除法的优先级高于加减法，赋值运算的优先级非常低，通常总是最后执行

##### 3.7.6 运算符的结合性

上面的表中标题为 `A` 的列说明了运算符的结合性。`L` 指从左至右结合，`R` 指从右至左结合

* 一元操作符、赋值、三元条件运算符都具有从右至左的结全性

##### 3.7.7 运算顺序

`JavaScript` 总是严格按照从左至右的顺序来计算表达式，只有在任何一个表达式具有副作用而影响到其他表达式的时候，其求值顺序才会和看上去有所不同

#### 3.8 算术表达式

在算术表达式中，所有无法转换为数字的操作数都转换为 `NaN` 值，如果操作数（或者转换结果）是 `NaN` 值，算术运算的结果也是 `NaN`

## 第二十八章 Ajax

### 1. JSON 概述

#### 1.1 什么是 json

`JSON(JavaScript Object Notation)`——JS对象标记，是一种轻量级的数据交换格式。它基于 `ECMAScript`（`w3c` 制定的 `js` 规范）的一个子集，采用完全独立于编程语言的文本格式来存储和表示数据。简洁和清晰的层次结构使得 `JSON` 成为理想的数据交换语言，易于人阅读和编写，同时也易于机器解析和生成，并有效地提升网络传输效率

#### 1.2 json 语法

* `[]`：表示数据
* `{}`：表示对象
* `""/''`：表示是属性或字符串类型的值
* `:`：表示属性和值之间的间隔符
* `,`：表示多个属性的间隔符或者多个元素的间隔符

### 2. JSON 解析

将 `JSON` 字符串解析为 `java` 对象

```javascript
// 对象嵌套数组
String json1 = {'id':1, 'name': 'JAVAEE-1703', 'stus': [{'id': 101, 'name': '张三', 'age': 16}]};
// 数组
String json2 = "['北京', '天津', '杭州']";
```

初始的类：

* `Student.java`
* `Grade.java`

```java
public class Student {
  private int id;
  private String name;
  private int age;
  // 此处省略 getter 和 setter 方法
}

public class Grade {
  private int id;
  private String name;
  private ArrayList<Student> stus;
  // 此处省略 getter 和 setter 方法
}
```

#### 2.1 FASTJSON 解析

* `Fastjson` 是一个 `Java` 库，可以将 `Java` 对象转换为 `JSON` 格式，当次也可以将 `JSON` 字符串转换为 `Java` 对象
* 提供了 `toJSONString()` 和 `parseObject()` 方法来将 `Java` 对象与 `JSON` 相互转换：
  * 调用 `toJSONString` 方法即可将对象转换成 `JSON` 字符串
  * `parseeObject` 方法则反过来将 `JSON` 字符串转换成对象

对象转 `JSON` 字符串：

```java
@Data
public class User {
    private int id;
    private String name;
    private boolean gender;
    private Date birthday;
}

public static void main(String[] args) throws ParseException {
    User user = new User();
    user.setId(1);
    user.setName("张三");
    user.setGender(true);
    user.setBirthday(DateTimeUtil.strToUtilDate("1994-04-04"));

    String userStr = JSON.toJSONString(user);
    System.out.println(userStr);
  	// 最后输出：{"birthday":765388800000,"gender":true,"id":1,"name":"张三"}
}
```

`JSON` 字符串转对象：

```java
@Test
public void test() {
    String json = "{\"birthday\":765388800000,\"gender\":true,\"id\":1,\"name\":\"张三\"}";
    User user = JSON.parseObject(json, User.class);
    System.out.println(user);
}
```

#### 2.2 Jackson 解析【推荐】

* `Jackson` 是一个能够将 `java` 对象序列化为 `JSON` 字符串，也能够将 `JSON` 字符串反序列化为 `java` 对象的框架
* 主要通过 `readValue` 和 `writeValue` 方法实现

对象转 `JSON` 字符串：

```java
@Test
public void testJacksonToString() throws JsonProcessingException {
    User user = new User();
    user.setName("李四");
    user.setId(2);
    user.setGender(false);
    user.setBirthday(new Date());

    ObjectMapper mapper = new ObjectMapper();
    String json = mapper.writeValueAsString(user);
    System.out.println(json);
}
```

`JSON` 字符串转对象：

```java
@Test
public void testJacksonToObject() throws JsonProcessingException {
    String json = "{\"id\":2,\"name\":\"李四\",\"gender\":false,\"birthday\":1618883809238}";
    ObjectMapper mapper = new ObjectMapper();
    User user = mapper.readValue(json, User.class);
    System.out.println(user);
}
```

#### 2.3 浏览器处理 JSON 字符串

`JSON.stringify()`

```javascript
var json = {name: '20', age: 34}
var str = JSON.stringify(json);
alert(str);
```

#### 2.4 浏览器转换为 JSON 对象

`JSON.parse()`

### 3. Ajax 概述

#### 3.1 什么是 Ajax

* `Ajax` 是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术
* `Ajax = Asynchronous JavaScript and XML`
* `Ajax` 是一种用于创建快速动态网页的技术
* 通过在后台与服务器进行少量数据交换，`Ajax` 可以使网页实现异步更新。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新
* 传统的网页（不使用 `Ajax`）如果需要更新内容，必须重载整个网页

#### 3.2 工作原理

[![c7kKtP.md.png](https://z3.ax1x.com/2021/04/20/c7kKtP.md.png)](https://imgtu.com/i/c7kKtP)

* `Ajax` 基于现有的 `Internet` 标准，并且联合使用它们
* `XMLHttpRequest` 对象：异步的与服务器交换数据
* `JavaScript/DOM` ：信息显示/交互
* `css`：给数据定义样式
* `xml`：作为转换数据的格式

#### 3.3 Ajax 实例

* `html` 代码部分： `Ajax` 应用程序包含一个 `div` 和一个按钮
* `div` 部分用于显示来自服务器的信息。当按钮被点击时，它负责调用名为 `loadXMLDoc()` 的函数

```html
<div id="myDiv"><h2>使用 Ajax 修改该文本内容</h2></div>
<button type="btton" onclick="loadXMLDoc()">修改内容</button>
```

接下来，在页面的 `head` 部分添加一个 `<script` 标签，该标签中包含了这个 `loadXMLDoc()` 函数

```html
<head>
  <script>
    function loadXMLDoc() {
      ... Ajax 脚本执行
    }
  </script>
</head>
```

#### 3.4 创建 XMLHttpRequest 对象

* `XMLHttpRequest` 对象是 `Ajax` 的基础
* 所有现代浏览器均支持 `XMLHttpRequest` 对象（`IE5` 和 `IE6` 使用 `ActiveXObject`）
* `XMLHttpRequest` 用于在后台与服务器交换数据。这意味着可以在不重新加载整个网页的情况下，对网页的某部分进行更新
* 所有现代浏览器（`IE7+、Firefox、chrome、Safari、Opera`）均内建 `XMLHttpRequest` 对象，创建 `XMLHttpRequest` 对象的语法

```javascript
var xmlHttp = new XMLHttpRequest();
```

老版本的 `IE5、IE6` 使用 `ActiveX` 对象：

```javascript
var xmlHttp = new ActiveXObject('Microsoft.XMLHTTP');
```

为了应对所有的现代浏览器和 `IE5、IE6` ，需要检查浏览器是否支持 `XMLHttpRequest` 对象。如果支持，则创建 `XMLHttpRequest` 对象。如果不支持，则创建 `ActiveXObject` 对象：

```javascript
var xmlHttp;
if (window.XMLHttpRequest) {
  xmlHttp = new XMLHttpRequest();
} else {
  xmlHttp = new ActiveXObject('Microsoft.XMLHTTP');
}
```

#### 3.5 XMLHttpRequest 请求

如需将请求发送到服务器，我们使用 `XMLHttpRequest` 对象的 `open()` 和 `send()` 方法：

```javascript
xmlHttp.open('GET', 'ajax_info.txt', true);
xmlHttp.send();
```

| 方法                     | 描述                                                         |
| ------------------------ | ------------------------------------------------------------ |
| `open(method,url,async)` | 规定请求的类型、`URL` 以及是否异步处理请求。`method`：请求的类型，`GET` 或 `POST`；`url`：文件在服务器上的位置，即请求路径；`async`：`true`（异步）或 `false`（同步），并且 `XMLHttpRequest` 对象如果要用于 `Ajax` 的话，其 `open()` 方法的 `async` 参数必须设置为 `true` |
| `send(String)`           | 将请求发送到服务器。`String`：仅用于 `POST` 请求             |

> 使用 GET 还是 POST？
>
> * 与 POST 相比，GET 更简单也更快，并且在大部分情况下都能用
> * 但是，在下列情况下，请使用 POST 请求：
>   * 无法使用缓存文件（更新服务器上的文件或数据库）
>   * 向服务器发送大量数据（POST 没有数据量限制）
>   * 发送包含未知字符的用户输入时，POST 比 GET 更稳定也更可靠

`GET` 请求：

```javascript
// 情形一：简单请求
xmlHttp.open('GET', '/demoGet', true);
xmlHttp.send();
// 情形二：上面的情形可能得到缓存的结果，为了避免这种情况，请向 URL 添加一个唯一的 ID
xmlHttp.open('GET', '/demoGet?t=' + Math.random(), true);
xmlHttp.send();
// 情形三：可以向 URL 添加信息来向服务端发送
xmlHttp.open('GET', '/demoGet?fname=Henry&lname=Ford', true);
xmlHttp.send();
```

`POST` 请求：

```javascript
// 情形一：简单请求
xmlHttp.open('POST', '/demoPost', true);
xmlHttp.send();
// 情形二：如果需要像 HTML 表单那样 POST 数据，需使用 setRequestHeader() 来添加 HTTP 头，然后在 send() 方法中规定希望发送的数据
xmlHttp.open('POST', '/demoPost', true);
xmlHttp.setRequestHeader('Content-type', 'application/x-www-form-urlencoded');
xmlHttp.send('fname=Henry&lname=Ford');
```

| 方法                              | 描述                                                         |
| --------------------------------- | ------------------------------------------------------------ |
| `setRequestHeader(header, value)` | 向请求添加 `HTTP` 头。`header`：规定头的名称；`value`：规定头的值 |

* 对于 `web` 开发人员来说，发送异步请求是一个巨大的进步。很多在服务器执行的任务都相当费时。`Ajax` 出现之前，这可能会引起应用程序挂起或停止
* 通过 `Ajax、JavaScript` 无需等待服务器的响应，而是：
  * 在等待服务器响应时执行其它脚本
  * 当响应就绪后对响应进行处理

当使用 `Async=true` 时，需要规定在响应处于 `onreadystatechange` 事件中的就绪状态时执行的函数：

```javascript
// 绑定执行函数
xmlHttp.onreadystatechange = function() {
  if (xmlHttp.readyState == 4 && xmlHttp.status == 200) {
    document.getElementById('myDiv').innerHtml = xmlHttp.responseText;
  }
}
```

* 如果需要，可以使用 `async=false`，这种方式不推荐，但是对于一些小型的请求，也是可以的
* `JavaScript` 会等到服务器响应就绪才继续执行。如果服务器繁忙或缓慢，应用程序会挂起或停止
* 注意：当使用 `async=false` 时，请不要编写 `onreadystatechange` 函数 —— 把代码放到 `send()` 语句后面即可

#### 3.6 readyState

* 每当 `readyState` 改变时，就会触发 `onreadystatechange` 事件
* 在 `onreadystatechange` 事件中，我们规定当服务器响应已做好被处理的准备时所执行的任务
* `readyState` 属性存有 `XMLHttpRequest` 的状态信息
* 当 `readyState` 等于 4 且 `status` 为 200 时，表示响应已就绪

`XMLHttpRequest` 对象的三个重要的属性：

| 属性                 | 描述                                                         |
| -------------------- | ------------------------------------------------------------ |
| `onreadystatechange` | 存储函数（或函数名），每当 `readyState` 属性改变时，就会调用该函数 |
| `readyState`         | 存有 `XMLHttpRequest` 的状态，从 0 到 4 发生变化。0：请求未初始化；1：服务器连接已建立；2：请求已接收；3：请求处理中；4：请求已完成，且响应已就绪 |
| `status`             | 例：200：`OK`；404：未找到页面                               |

| 响应码 | 描述                                                         |
| ------ | ------------------------------------------------------------ |
| 100    | 客户必须继续发出请求                                         |
| 101    | 客户要求服务器根据请求转换 HTTP 协议版本                     |
| 200    | 交易成功                                                     |
| 201    | 提示知道新文件的 URL                                         |
| 202    | 接收和处理、但处理未完成                                     |
| 203    | 返回信息不确定或不完整                                       |
| 204    | 请求收到，但返回信息为空                                     |
| 205    | 服务器完成了请求，用户代理必须复位当前已经浏览过的文件       |
| 206    | 服务器已经完成了部分用户的 GET 请求                          |
| 300    | 请求的资源可在多处得到                                       |
| 301    | 删除请求数据                                                 |
| 302    | 在其他地址发现了请求数据                                     |
| 303    | 建议客户访问其它 URL 或访问方式                              |
| 304    | 客户端已经执行了 GET，但文件未变化                           |
| 305    | 请求的资源必须从服务器指定的地址得到                         |
| 306    | 前一版本 HTTP 中使用的代码，现行版本中不再使用               |
| 307    | 申明请求的资源临时性删除                                     |
| 400    | 错误请求，如语法错误                                         |
| 401    | 请求授权失败                                                 |
| 402    | 保留有效 ChargeTo 头响应                                     |
| 403    | 请求不允许                                                   |
| 404    | 没有发现文件、查询或 URI                                     |
| 405    | 用户在 Request-Line 字段定义的方法不允许                     |
| 406    | 根据用户发送的 Accept 拖，请求资源不可访问                   |
| 407    | 类似 401，用户必首先在代理服务器上得到授权                   |
| 408    | 客户端没有在用户指定的时间内完成请求                         |
| 409    | 对当前资源状态，请求不能完成                                 |
| 410    | 服务器上不再有此资源且无进一步的参考地址                     |
| 411    | 服务器拒绝用户定义的 Content-Length 属性请求                 |
| 412    | 一个或多个请求头字段在当前请求中错误                         |
| 413    | 请求的资源大于服务器允许的大小                               |
| 414    | 请求的资源 URL 长于服务器允许的长度                          |
| 415    | 请求资源不支持请求项目格式                                   |
| 416    | 请求中包含 Range 请求头字段，在当前请求资源范围内没有 range 指示值，请求也不包含 If-Range 请求头字段 |
| 417    | 服务器不满足请求 Except 头字段指定的期望值，如果是代理服务器，可能是下一级服务器不能满足请求 |
| 500    | 服务器产生内部错误                                           |
| 501    | 服务器不支持请求的函数                                       |
| 502    | 服务器暂时不可用，有时是为了防止发生系统过载                 |
| 503    | 服务器过载或暂停维修                                         |
| 504    | 关口过载，服务器使用另一个关口或服务来响应用户，等待时间设定值较长 |
| 505    | 服务器不支持或拒绝请求头中指定的 HTTP 版本                   |

#### 3.7 XMLHttpRequest 响应

如需获得来自服务器的响应，请使用 `XMLHttpRequest` 对象的 `responseText` 或 `responseXML` 属性

| 属性           | 描述                      |
| -------------- | ------------------------- |
| `responseText` | 获得字符串形式的响应数据  |
| `responseXML`  | 获得 `XML` 形式的响应数据 |

* `responseText` 属性
  * 如果来自服务器的响应并非 `XML`，请使用 `responseText` 属性
  * `responseText` 属性返回字符串形式的响应
* `responseXML` 属性
  * 如果来自服务器的响应是 `XML`，而且需要作为 `XML` 对象进行解析，请使用 `responseXML` 属性

```javascript
xmlDoc = xmlHttp.responseXML;
txt = '';
x = xmlDoc.getElementsByTagName('ARTIST');
if (i = 0; i < x.length; i++) {
  txt = txt + x[i].childNodes[0].nodeValue + '<br>';
}
document.getElementById('myDiv').innerHTML = txt;
```

#### 3.8 使用回调函数

* 回调函数是一种以参数形式传递给另一个函数的函数
* 如果网站上存在多个 `Ajax` 任务，那么应该为创建 `XMLHttpRequest` 对象编写一个标准的函数，并为每个 `Ajax` 任务调用该函数
* 该函数调用应该包含 `URL` 以及发生 `onreadystatechange` 事件时执行的任务（每次调用可能不尽相同）

### 4. Ajax 的使用

登录案例：`html + css + ajax + Servlet + commons-dbutils`

```sql
create table login_user
(
  id       int auto_increment primary key,
  name     varchar(32) not null,
  password varchar(32) not null
);
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>登录</title>
    <style>
        div {text-align: center;}
        #loginForm {width: 250px; margin: 0 auto;}
        label {width: 100px; display: inline-block;}
        input {width: 142px;}
        #loginBtn {width: 150px;}
        p:last-child {text-align: right;}
        p#tips {font-size: 10px; color: red;}
    </style>
</head>
<body>
    <div>
        <h2>登录</h2>
        <form id="loginForm">
            <label for="username">用户名：</label><input type="text" id="username"><br><br>
            <label for="password">密码：</label><input type="password" id="password">
            <p id="tips"></p>
            <p><button id="loginBtn">登录</button></p>
        </form>
    </div>
    <script>
        var loginBtn = document.getElementById('loginBtn');
        var tips = document.getElementById('tips');
        loginBtn.addEventListener('click', function (ev) {
            tips.innerHTML = '登录验证中，请稍候……';
            var username = document.getElementById('username').value;
            var password = document.getElementById('password').value;
            if (username === '') {
                ev.preventDefault();
                alert('用户名不能为空！');
                return;
            }
            if (password === '') {
                ev.preventDefault();
                alert('密码不能为空！');
                return;
            }

            var xhr = new XMLHttpRequest();
            xhr.open('post', '/loginAjax');
            xhr.setRequestHeader('Content-type', 'application/x-www-form-urlencoded');
            xhr.send('username=' + username + '&password=' + password);
            xhr.onreadystatechange = function (ev1) {
                if (xhr.readyState === 4 && xhr.status === 200) {
                    tips.innerHTML = xhr.responseText;
                }
            };

            ev.preventDefault();
        })
    </script>
</body>
</html>
```

```java
@WebServlet(name = "LoginServlet", value = "/loginAjax")
public class LoginServlet extends HttpServlet {

    @Override
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        request.setCharacterEncoding("utf-8");
        response.setContentType("text/html; charset=utf-8");

        String username = request.getParameter("username");
        String password = request.getParameter("password");

        QueryRunner queryRunner = new QueryRunner(DBUtil.getDataSource());
        LoginUser loginUser = null;
        try {
            loginUser = queryRunner.query("select * from login_user where name=? and password=?", new BeanHandler<>(LoginUser.class), username, password);
            Thread.sleep(1000);
        } catch (Exception e) {
            e.printStackTrace();
        }

        String res = loginUser == null ? "登录失败！" : "登录成功！<br>用户名：" + username + ", 密码：" + password;
        response.getWriter().print(res);
    }
}
```

## 第二十九章 jQuery

### 1. 概述

#### 1.1 简介

* `jQuery` 是一个快速、简洁的 `JavaScript` 框架，是继 `Prototype` 之后又一个优秀的 `JavaScript` 代码库（框架）。`jQuery` 设计的宗旨是 `write less, do more`，即倡导写更少的代码，做更多的事情。它封装 `JavaScript` 常用的功能代码，提供一种简便的 `JavaScript` 常用的功能代码，提供一种简便的 `JavaScript` 设计模式，优化 `HTML` 文档操作、事件处理、动画设计和 `Ajax` 交互
* `jQuery` 的核心特性可以总结为：具有独特的链式语法和短小的多功能接口；具有高效灵活的 `css` 选择器，并且可对 `css` 选择器进行扩展；拥有便捷的插件扩展机制和丰富的插件。`jQuery` 兼容各种主流浏览器，如 `IE 6.0+、FF 1.5+、Opera 9.0+` 等

#### 1.2 功能

`jQuery` 库包含以下功能：

* `HTML` 元素选取
* `HTML` 元素操作
* `CSS` 操作
* `HTML` 事件函数
* `JavaScript` 特效和动画
* `HTML DOM` 遍历和修改
* `Ajax`
* `Utilities`

#### 1.3 为什么要使用

目前网上有大师开源的 `JS` 框架，但是 `jQuery` 是目前最流行的 `JS` 框架，而且提供了大师的扩展。很多大公司都在使用 `jQuery`，如：

* `Google`
* `Microsoft`
* `IBM`

### 2. 安装

可以通过多种方法在网页中添加 `jQuery`：

* 从 [官网](https://jquery.com) 下载 `jQuery` 库
* 从 `CDN` 中载入 `jQuery`，如从 `Google` 中加载 `jQuery` 

有两个版本的 `jQuery` 可供下载：

* `Production version` - 用于实际的网站中，已被精简和压缩
* `Development version` - 用于测试和开发（未压缩，是可读的代码）

#### 2.1 网页中安装

```html
<head>
  <script src='jquery-1.10.2.min.js'></script>
</head>
```

#### 2.2 CDN 安装

```html
<head>
  <script src='https://apps.bdimg.com/libs/jquery/2.1.4/jquery.min.js'></script><!--百度CDN-->
  <script src='https://lib.sinaapp.com/js/jquery/2.0.2/jquery-2.0.2.min.js'></script><!--新浪CDN-->
  <script src='https://ajax.googleapis.com/ajax/libs/jquery/1.10.2/jquery.min.js'></script><!--谷歌CDN-->
  <script src='https://ajax.htmlnetcdn.com/ajax/jQuery/jquery-1.10.2.min.js'></script><!--微软CDN-->
</head> 
```

### 3. 语法

基础语法：`$(selector).action()`

* `jQuery` 语法是通过选取 `HTML` 元素，并对选取的元素执行某些操作
* 可以使用美元符号 `$` 来代替 `jQuery`
* 选择符（`selector`）用于 “查询” 和 “查找” `HTML` 元素
* `jQuery` 的 `action()` 执行对元素的操作，例如：
  * `$(this).hide()`：隐藏当前元素
  * `$('p').hide()`：隐藏所有 `<p>` 元素
  * `$('p.test').hide()`：隐藏所有 `class="test"` 的 `<p>` 元素
  * `$('#test').hide()`：隐藏所有 `id="test"` 的元素

#### 3.1 jQuery 选择器

##### 元素选择器

基于元素名选取元素

```javascript
$('p')
```

##### id 选择器

通过 `HTML` 元素的 `id`  属性选取指定的元素

> 页面中元素的 id 应该是唯一的，所以要在页面中选取唯一的元素需要通过 #id 选择器

```javascript
$('#test')
```

##### class 选择器

通过指定的 `class` 查找元素

#### 3.2 常用事件方法

* 事件：页面对不同访问者的响应叫做事件

* 事件处理程序指的是当 `HTML` 中发生某些事件时所调用的方法，例如：在元素上移动鼠标，选取单选按钮

* 点击元素：在事件中经常使用术语 “触发” （或“激发”），例如：当按下键时触发 `keypress` 事件

常见 `DOM` 事件：

| 鼠标事件     | 键盘事件   | 表单事件 | 文档/窗口事件 |
| ------------ | ---------- | -------- | ------------- |
| `click`      | `keypress` | `submit` | `load`        |
| `dblclick`   | `keydown`  | `change` | `resize`      |
| `mouseenter` | `keyup`    | `focus`  | `scroll`      |
| `mouseleave` |            | `blur`   | `unload`      |

在 `jQuery` 中，大多数 `DOM` 事件都有一个等效的 `jQuery` 方法，例如点击事件：

```javascript
$('p').click();

$('p').click(function() {
    // 动作触发后执行的代码
});
```

总结：不传参数是点击，传参数是设置事件

```javascript
$(function() {});

$(document).ready(function() {});
```

上面的方法是在文档完全加载完成后执行函数

### 4. 效果

#### 4.1 隐藏显示

* `hide()`：隐藏元素
* `show()`：显示元素
* `toggle()`：切换 `hide()` 方法和 `show()` 方法

上面这三个方法都有两个参数：`speed, callback`

* `speed`：规定显示/隐藏的速度，取值：`slow`、`fast`，或者毫秒值
* `callback`：隐藏或显示完成后所执行的函数名称

#### 4.2 淡入淡出

* `fadeIn()`：淡入
* `fadeOut()`：淡出
* `fadeToggle()`：切换淡入、淡出
* `fadeTo()`：可以添加透明度的属性



#### 4.6 Callback

* 许多 `jQuery` 函数涉及动画。这些函数也许会将 `speed` 或 `duration` 作为可选参数
* 例子：`$('p').hide('slow');`
* `speed` 或 `duration` 参数可以设置许多不同的值，比如：`slow`、`fast`、`normal`，或者毫秒值

```javascript
$('button').click(function() {
    $('p').hide('slow', function() {
        alert('段落现在被隐藏了');
    });
});
```

…… 未完待续

## 第三十章 Maven

### 1. 引言

项目中 `jar` 包资源越来越多，`jar` 包的管理越来越繁琐

* 要为每个项目手动导入所需的 `jar`，需要搜集全部 `jar` —— 繁琐
* 项目中的 `jar` 如果需要版本升级，就需要再重新搜集 `jar` —— 复杂
* 相同的 `jar` 在不同的项目中保存了多份 —— 存储冗余，散乱

`java` 项目需要一个统一的便捷的管理方案

### 2. 介绍

`maven` 这个单词来自于意第绪语（犹太语），意为知识的积累。这是一个基于项目对象模型（`POM`）概念的纯 `java` 开发的开源项目管理工具。主要用来管理 `Java` 项目，进行依赖管理（`jar` 包依赖管理）和项目构建（项目编译、打包、测试、部署）。此外，还能分块开发，提高开发效率

### 3. 安装

#### 3.1 下载

[maven](http://us.mirros.quenda.co/apache/maven/maven-3/3.5.4/binaries)

#### 3.2 Maven 安装

##### 解压

注意：解压文件尽量不要放在含有中文或者特殊字符的目录下

##### 目录

* `bin`：含有 `mvn` 运行的脚本
* `boot`：含有 `plexus-classworlds` 类加载器框架，`maven` 使用该框架加载自己的类库
* `conf`：含有 `settings.xml` 配置文件
* `lib`：含有 `maven` 运行时所需要的 `java` 类库

##### 环境变量

`maven` 依赖 `java` 环境，所以要确保 `java` 环境已经配置好（`maven-3.3+` 需要 `jdk7+`）

`maven` 本身有 2 个环境变量需要配置：

* `MAVEN_HOME=maven的安装目录`
* `PATH=maven安装目录下的bin目录`

##### 测试

```shell
# 查看maven的版本信息
mvn -v
```

### 4. 配置

#### 4.1 本地仓库

`maven` 的 `conf` 目录中有 `settings.xml`，是 `maven` 的配置文件，把 `<localRepository>` 节点放出来，该节点用来配置本地存储 `jar` 包的位置：

```xml
<localRepository>/Users/xxxx/xxxx/maven_repository</localRepository>
```

#### 4.2 JDK 配置

```xml
<profiles>
  <!--在已有的profiles标签中添加profile标签-->
  <profile>
    <id>myjdk</id>
    <activation>
      <activeByDefault>true</activeByDefault>
      <jdk>1.8</jdk>
    </activation>
    <properties>
      <maven.compiler.source>1.8</maven.compiler.source>
      <maven.compiler.target>1.8</maven.compiler.target>
      <maven.compiler.compilerVersioni>1.8</maven.compiler.compilerVersion>
    </properties>
  <profile>
</profiles>
<!--让增加的 profile 生效-->
<activeProfiles>
  <activeProfile>myjdk</activeProfile>
</activeProfiles>
```

### 5. 仓库

存储依赖的地方。仓库中不仅存放依赖，而且每个依赖都有唯一标识（坐标），供 `java` 项目索取

#### 5.1 分类

[![cvUXLt.md.png](https://z3.ax1x.com/2021/04/24/cvUXLt.md.png)](https://imgtu.com/i/cvUXLt)

当需要检索依赖时，会从仓库中去查找，查找顺序为：

`本地仓库 > 私服（如果配置了的话） > 公共仓库（如果配置了的话） > 中央仓库`

#### 5.2 本地仓库

即在 `settings.xml` 中配置的目录，使用过的依赖都会自动存储在本地仓库中，后续可以复用

#### 5.3 远程仓库

##### 中央仓库

`maven` 中央仓库是由 `maven` 社区提供的仓库，不用任何配置，`maven` 中内置了中央仓库的地址。其中包含了绝大多数流行的开源 `java` 构件

[https://mvnrepository.com/]() 可以搜索需要的依赖的相关信息（仓库搜索服务）【重点】

[http://repo.maven.apache.org/maven2]() 中央仓库地址

##### 公共仓库（重点）

除中央仓库之外，还有其它远程仓库。比如 `aliyun` 仓库（[http://maven.aliyun.com/nexus/content/groups/public/]()）。中央仓库在国外，下载依赖的速度过慢，所以都会配置一个国内的公共仓库替代中央仓库

```xml
<!--setting.xml中添加如下配置-->
<mirrors>
  <mirror>
    <id>aliyun</id>
    <!--中心仓库的mirror（镜像）-->
    <mirrorOf>central</mirrorOf>
    <name>Nexus aliyun</name>
    <!--aliyun仓库地址，以后所有要指向中心仓库的请求，都会指向aliyun仓库-->
    <url>http://maven.aliyun.com/nexus/content/groups/public</url>
  </mirror>
</mirrors>
```

#### 6. 私服（了解）

公司范围内共享的仓库，不对外开放。可以通过 `nexus` 来创建、管理一个私服

### 6.idea-maven

#### 6.1 idea 关联 maven

在 `idea` 中关联本地安装的 `maven` ，后续就可以通过 `idea` 使用 `maven`，管理项目

[![cvwaMd.md.png](https://z3.ax1x.com/2021/04/24/cvwaMd.md.png)](https://imgtu.com/i/cvwaMd)

#### 6.2 新建 maven 项目

##### 新建项目

选择：`file -> new -> project` 菜单，选择 `maven`：

[![cv05Xd.md.png](https://z3.ax1x.com/2021/04/24/cv05Xd.md.png)](https://imgtu.com/i/cv05Xd)

[![cv0xXj.md.png](https://z3.ax1x.com/2021/04/24/cv0xXj.md.png)](https://imgtu.com/i/cv0xXj)

[![cvB97q.md.png](https://z3.ax1x.com/2021/04/24/cvB97q.md.png)](https://imgtu.com/i/cvB97q)

##### 项目结构

* `src/main/java`：存放源代码，建包，存放项目中代码
* `src/main/resources`：放置配置文件，静态资源等
* `src/test/java`：存放测试代码
* `src/test/resources`：放置测试相关的配置文件
* `项目根目录/pom.xml`：`maven` 项目核心文件，其中定义项目构建方式，声明依赖等

> maven 项目中创建包、类，执行等操作，都和普通项目无差异

[![cvBqbR.md.png](https://z3.ax1x.com/2021/04/24/cvBqbR.md.png)](https://imgtu.com/i/cvBqbR)

#### 6.3 导入依赖

建好项目后，需要导入需要的 `jar`，要通过【坐标】完成

* 每个构件都有自己的坐标（标识）：`groupId + artifactId + version`（项目标识+项目名+版本号）
* 在 `maven` 项目中只需要配置坐标，`maven` 便会自动加载对应依赖，删除坐标则会移除依赖

##### 查找依赖

依赖查找服务：[https://mvnrepository.com]()，获得依赖的坐标，在 `maven` 项目中导入：

##### 导入依赖

在上面的网站中选择好自己需要的 `jar` 包，拷贝坐标，粘贴到项目 `pom.xml` 文件的 `<dependencies>` 节点中

##### 同步依赖

`idea` 的右下角会弹出选择框，可以选择每次手动导入或者自动导入来对依赖进行同步

#### 6.4 创建 web 项目

##### 打包方式

`pom.xml` 设置：`<packaging>war</packaging>`

[![cvrj1O.md.png](https://z3.ax1x.com/2021/04/24/cvrj1O.md.png)](https://imgtu.com/i/cvrj1O)

##### web 依赖

导入 `jsp`、`servlet` 和 `JSTL` 依赖，使项目具有 `web` 编译环境

```xml
<packaging>war</packaging>

<dependencies>
  <dependency><!--jstl支持-->
    <groupId>javax.servlet</groupId>
    <artifactId>jstl</artifactId>
    <version>1.2</version>
  </dependency>
  <dependency><!--servlet编译环境-->
    <groupId>javax.servlet</groupId>
    <artifactId>javax.servlet-api</artifactId>
    <version>3.1.0</version>
    <scope>provided</scope>
  </dependency>
  <dependency><!--jsp编译环境-->
    <groupId>javax.servlet.jsp</groupId>
    <artifactId>javax.servlet.jsp-api</artifactId>
    <version>2.3.1</version>
    <scope>provided</scope>
  </dependency>

</dependencies>
```

##### webapp 目录

按照 `maven` 规范，新建 `web` 项目特有目录：

[![cvy7Jx.md.png](https://z3.ax1x.com/2021/04/24/cvy7Jx.md.png)](https://imgtu.com/i/cvy7Jx)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee
                      http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0"
         metadata-complete="true">
  
  <!--这是一个空的web.xml文件模板-->

</web-app>
```

##### 定义 Servlet 和 JSP

[![cvRwUH.md.png](https://z3.ax1x.com/2021/04/24/cvRwUH.md.png)](https://imgtu.com/i/cvRwUH)

#### 6.5 部署 web 项目

##### 新增 Tomcat

##### 部署 web 项目

##### 启动 Tomcat，访问项目

#### 6.6 依赖生命周期

项目中导入的依赖可以对生命周期进行管理——指的是依赖在哪个生命周期过程中有效：

* `compile`：缺省值，适用于所有阶段（测试，编译，运行，打包），会随着项目一起发布（被打包）
* `provided`：类似 `compile`，期望 `JDK`、容器或使用者会提供这个依赖。如  `servlet-api.jar`，参与测试，编译，不会被打钆
* `runtime`：只在运行时使用，如 `jdbc6.jar`，适用运行和测试阶段，会被一起发布
* `test`：只在测试时使用，用于编译和运行测试代码，如 `junit.jar`，不会随项目发布，在非 `test` 包下也不能使用
* `system`：类似 `provided`，但 `maven` 不会在 `Reposistory` 中查找它，要在本地磁盘目录中查找，参与编译、测试、打包、运行【基本不使用】

### 7. 命令

#### 7.1 常用指令

* `clean`：清除上一次编译的结果（删除 `target` 目录）
* `compile`：对项目进行编译，创建 `target` 目录，并将编译结果放入
* `package`：对项目进行打包（根据 `pom.xml` 中的 `packagin` 节点配置的属性）
* `install`：把项目打成一个 `jar` 包，并且安装到本地仓库中

#### 7.2 面板

`idea` 中有 `maven` 面板，其中可以快速执行 `maven` 命令

#### 7.3 命令行

`idea` 的 `terminal` 中可以输入 `maven` 指令

### 8. 私服【了解】

私服是架设在局域网的一种特殊的远程仓库，目的是代理远程仓库及部署第三方构件。

有了私服之后，当 `maven` 需要下载构件时，直接请求私服，私服上存在则下载到本地仓库；否则，私服请求外部的远程仓库，将构件下载到私服，再提供给本地仓库下载

私服可以解决在企业做开发时每次需要的 `jar` 包都要在中心仓库下载，且每次下载完只能被自己使用，不能被其他开发人员使用

所谓私服就是一个服务器，但是不是本地层面的，是公司层面的，公司中所有开发人员都在使用同一个私服

[![cz0o7R.md.png](https://z3.ax1x.com/2021/04/25/cz0o7R.md.png)](https://imgtu.com/i/cz0o7R)

我们可以使用专门的 `maven` 仓库管理软件来搭建私服，比如：`Apache Archiva，Artifactory，Sonatype Nexus` 。

#### 8.1 Nexus 安装【了解】

* [官网](https://blog.sonatype.com)
* 下载 [nnexus-2.x-bundle.zip](https://help.sonatype.com/repomanager2/download/download-archives---repository-manager-oss) 解压即可
* 解压后在 `bin` 目录中执行命令：
  * `nexus install` 在系统中安装 `nexus` 服务
  * `nexus uninstall` 卸载 `nexus` 服务
  * `nexus start` 启动服务
  * `nexus stop` 停止服务
* 访问私服：[http://localhost:8081/nexus/](http://localhost:8081/nexus/)
* 登录私服：[admin/admin123]()

[![czB48f.md.png](https://z3.ax1x.com/2021/04/25/czB48f.md.png)](https://imgtu.com/i/czB48f)



未完待续……

## 第三十一章 MyBatis

### 1. 引言

#### 1.1 什么是框架

软件的半成品，解决了软件过程当中的普适性问题，从而简化了开发步骤，提供了开发的效率

#### 1.2 什么是 ORM 框架

* `ORM(Object Relation Mapping)` 对象关系映射，将程序中的一个对象与表中的一行数据一一对应
* `ORM` 框架提供了持久化类与表的映射关系，在运行时参照映射文件的信息，把对象持久化到数据库中

#### 1.3 使用 JDBC 完成 ORM 操作的缺点

* 存在大师冗余的代码
* 手工创建 `Connection、Statement` 等
* 手工将结果集封装成实体对象
* 查询效率低，没有数据访问进行过优化（`Not Cache`）

### 2. MyBatis 框架

#### 2.1 概念

* `MyBatis` 本是 `Apache` 软件基金会的一个开源项目 `iBatis`，2010 年这个项目由 `apache software foundation` 迁移到了 `Google Code`，并且改名为 `MyBatis`。2013 年 11 月迁移到 `GitHub`
* `MyBatis` 是一个优秀的基于 `Java` 的持久层框架，支持自定义 `SQL`，存储过程和高级映射
* `MyBatis` 对原有 `JDBC` 操作进行了封装，几乎消除了所有 `JDBC` 代码，使开发者只需关注 `SQL` 本身
* `MyBatis` 可以使用简单的 `XML` 或 `Annotation` 来配置执行 `SQL`，并自动完成 `ORM` 操作，将执行结果返回

#### 2.2 访问与下载

[官方网站](http://www.mybatis.org/mybatis-3)

[下载地址](https://github.com/mybatis/mybatis-3/release/tag/mybatis-3.5.1)

### 3. 开发步骤

#### 3.1 创建数据库

```sql
create table login_user
(
  id            int auto_increment
    primary key,
  name          varchar(32) not null,
  password      varchar(32) not null,
  register_date date        not null
);

```

#### 3.2 创建实体对象

```java
@Data
public class LoginUser {
    private long id;
    private String name;
    private String password;
    private Date registerDate;
}
```

#### 3.3 创建 MyBatis 配置文件

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
  	<!--标签出现的先后顺序：configuration (properties?, settings?, typeAliases?,
                                        typeHandlers?, objectFactory?, objectWrapperFactory?,
                                        reflectorFactory?, plugins?, environments?,
                                        databaseIdProvider?, mappers?)-->
  	
  	<!--引入数据库相关信息的配置文件-->
  	<properties resources="jdbc.properties"/>
  
  	<!--配置别名-->
  	<typeAliases>
      <package name="com.ch.wchya.test.entity"/>
  	</typeAliases>
  
    <!--核心配置信息-->
    <environments default="main_config">
        <!--数据库相关信息-->
        <environment id="main_config">
            <!--事务控制类型-->
            <transactionManager type="jdbc"></transactionManager>
            <!--数据库连接参数-->
            <!--下面这句也可以写为：
            <dataSource type="POOLED">
            -->
            <dataSource type="org.apache.ibatis.datasource.pooled.PooledDataSourceFactory">
                <property name="driver" value="${jdbc.driver}"/>
                <!--注意：<>内不能写&，需要使用转义字符 &amp;-->
                <property name="url" value="${jdbc.url}"/>
                <property name="username" value="${jdbc.username}"/>
                <property name="password" value="${jdbc.password}"/>
            </dataSource>
        </environment>
    </environments>

    <!--
		指定映射配置文件的位置，映射配置文件指的是每个dao独立的配置文件
		如果这里用注解配置的话，此处应该使用class属性指定被注解的dao全限定类名
		-->
    <mappers>
        <mapper resource="LoginUserDaoMapper.xml"/>
        <!--<mapper class="com.ch.wchya.mybatisstudy.dao.IMUserDao"/>-->
    </mappers>
</configuration>
```

> mybatis 连接池配置的位置：主配置文件的 dataSource 标签，type 属性就是表示采用何种连接池方式（提供了3种方式的配置），type的取值有：
>
> * POOLED：采用传统的 javax.sql.DataSource 规范中的连接池，mybatis 中有针对规范的实现
> * UNPOOLED：采用传统的获取连接的方式，虽然也实现了 javax.sql.DataSource 接口，但是并没有使用池的思想
> * JNDI：采用服务器提供的 JNDI 技术实现，来获取 DataSource 对象，不同的服务器所能拿到的 DataSource 是不一样的。注意：如果不是 web 或者 maven 的 war 工程，是不能使用的

#### 3.4 创建 mapper 映射文件

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.ch.wchya.servlet.dao.LoginUserDao">
    <!--描述方法-->
    <!--注意：mybatis 中数据库字段和实体对象的映射规则默认是同名映射，如果不一样，需要在sql语句中使用as关键字定义别名-->
    <select id="getUserById" resultType="com.ch.wchya.entity.servlet.LoginUser">
        select id,name,password,register_date as registerDate
        from login_user
        where id=#{arg0}
    </select>
</mapper>
```

#### 3.5 测试

```java
@Test
public void testLoginUser() throws IOException {
    // 1. 加载配置文件
    InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
    // 2. 构建 SqlSessionFactory
    SqlSessionFactory sessionFactory = new SqlSessionFactoryBuilder().build(is);
    // 3. 通过 sessionFactory 创建 SqlSession
    SqlSession sqlSession = sessionFactory.openSession();
    // 4. 通过 sqlSession 获取 DAO 的实现类对象
    LoginUserDao mapper = sqlSession.getMapper(LoginUserDao.class);
    // 5. 测试查询方法
    LoginUser user1 = mapper.getUserById(1);
    LoginUser user2 = mapper.getUserById(2);
    System.out.println(user1);
    System.out.println(user2);
}
```

#### 3.6 输出

```java
LoginUser(id=1, name=张三, password=12345, registerDate=Sun Apr 11 00:00:00 CST 2021)
LoginUser(id=2, name=zhangsan, password=23456, registerDate=Thu Apr 22 00:00:00 CST 2021)
```

### 4. 细节补充

#### 4.1 解决 mapper.xml 存放在 resources 以外路径中的读取问题

在 `pom.xml` 文件最后追加 `<build>` 标签，以便可以将 `xml` 文件复制到 `classes` 目录中，并在程序运行时正确获取：

```xml
<build>
    <resources>
        <!--更改 Maven 编译规则-->
        <resource>
            <!--资源目录-->
            <directory>src/main/java</directory>
            <includes>
                <include>*.xml</include><!--默认值，如果新添加规则则该条规则失效-->
                <include>**/*.xml</include><!--新添加的规则：*/代表1级目录，**/代表多级目录-->
            </includes>
            <filtering>true</filtering>
        </resource>
    </resources>
</build>
```

#### 4.2 properties 配置文件

在 `mybatis-config.xml` 这个核心配置中，如果存在需要频繁改动的数据内容，可以提取到 `properties` 中

##### 添加 jdbc.properties 文件

```properties
driver=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://localhost:3306/emp?useUnicode=true&characterEncoding=utf-8
username=xxxx
password=xxxx
```

##### 修改 mybatis-config.xml 文件内容 

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
  	<!--标签出现的先后顺序：configuration (properties?, settings?, typeAliases?,
                                        typeHandlers?, objectFactory?, objectWrapperFactory?,
                                        reflectorFactory?, plugins?, environments?,
                                        databaseIdProvider?, mappers?)-->
    <!--导入配置-->
    <properties resource="jdbc.properties"/>
    <!--核心配置信息-->
    <environments default="main_config">
        <!--数据库相关信息-->
        <environment id="main_config">
            <!--事务控制类型-->
            <transactionManager type="jdbc"></transactionManager>
            <!--数据库连接参数-->
            <dataSource type="org.apache.ibatis.datasource.pooled.PooledDataSourceFactory">
                <property name="driver" value="${driver}"/>
                <property name="url" value="${url}"/>
                <property name="username" value="${username}"/>
                <property name="password" value="${password}"/>
            </dataSource>
        </environment>
    </environments>

    <!--注册mapper文件-->
    <mappers>
        <!--<mapper resource="LoginUserDaoMapper.xml"/>-->
        <mapper resource="com/ch/wchya/servlet/dao/LoginUserDaoMapper.xml"/>
    </mappers>
</configuration>
```

#### 4.3 类型别名

为实体类定义别名，提高书写效率

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <!--导入配置-->
    <properties resource="jdbc.properties"/>
    <!--实体类别名-->
    <typeAliases>
        <!--自定义类的别名-->
        <!--<typeAlias type="com.ch.wchya.entity.servlet.LoginUser" alias="loginUser"/>-->
        <package name="com.ch.wchya.entity.servlet"/>
    </typeAliases>
    <!--核心配置信息-->
    <environments default="main_config">
        <!--数据库相关信息-->
        <environment id="main_config">
            <!--事务控制类型-->
            <transactionManager type="jdbc"></transactionManager>
            <!--数据库连接参数-->
            <dataSource type="org.apache.ibatis.datasource.pooled.PooledDataSourceFactory">
                <property name="driver" value="${driver}"/>
                <property name="url" value="${url}"/>
                <property name="username" value="${username}"/>
                <property name="password" value="${password}"/>
            </dataSource>
        </environment>
    </environments>

    <!--注册mapper文件-->
    <mappers>
        <!--<mapper resource="LoginUserDaoMapper.xml"/>-->
        <mapper resource="com/ch/wchya/servlet/dao/LoginUserDaoMapper.xml"/>
    </mappers>
</configuration>
```

#### 4.4 创建 log4j 配置文件

`pom.xml` 添加 `log4j` 依赖

```xml
<dependency>
    <groupId>log4j</groupId>
    <artifactId>log4j</artifactId>
    <version>1.2.17</version>
</dependency>
```

创建并配置 `log4j.properties`（名称是固定的）

```properties
# 全局日志配置
log4j.rootLogger=DEBUG, stdout
# MyBatis 日志配置
log4j.logger.org.mybatis.example.BlogMapper=TRACE
# 控制台输出
log4j.appender.stdout=org.apache.log4j.ConsoleAppender
log4j.appender.stdout.layout=org.apache.log4j.PatternLayout
log4j.appender.stdout.layout.ConversionPattern=%5p [%t] - %m%n
```

### 5. CRUD 操作

#### 5.1 查询

标签：`<select id="" resultType="">`，下面的示例包括（按顺序）：**序号参数绑定、注解参数绑定【推荐】、Map 参数绑定、对象参数绑定、模糊查询**

```java
public interface LoginUserDao {
  // 参数序号绑定
  LoginUser getUserById(long id);
  LoginUser getUserByIdAndPassword(long id, String pwd);
  // 注解参数绑定
  LoginUser getUserByIdAndName(@Param("id") long id, @Param("name") String name);
  // Map 参数绑定
  LoginUser getUserByMap(Map map);
  // 对象参数绑定
  LoginUser getUserByUser(LoginUser user);
  // 模糊查询
  LoginUser getUserByKeyWord(@Param("keyword") String keyword);
}
```

```xml
<select id="getUserById" resultType="LoginUser">
    select id,name,password,register_date as registerDate
    from login_user
    where id=#{arg0}
</select>
<!--argX：X从0开始；paramX：X从1开始；-->
<select id="getUserByIdAndPassword" resultType="LoginUser">
    select id,name,password,register_date as registerDate
    from login_user
    where id=#{arg0} and password=#{param2}
</select>
<select id="getUserByIdAndName" resultType="LoginUser">
    select id,name,password,register_date as registerDate
    from login_user
    where id=#{id} and name=#{name}
</select>
<select id="getUserByMap" resultType="LoginUser">
    select id,name,password,register_date as registerDate
    from login_user
    where id=#{id} and password=#{password}
</select>
<select id="getUserByUser" resultType="LoginUser">
    select id,name,password,register_date as registerDate
    from login_user
    where id=#{id} and password=#{password}
</select>
<select id="getUserByKeyWord" resultType="LoginUser">
    select id,name,password,register_date as registerDate
    from login_user
    where name like concat('%', #{keyword}, '%')
</select>
```

#### 5.2 删除

标签：`<delete id="" paramterType="">`

```xml
<delete id="deleteUser" parameterType="long">
    delete from login_user
    where id=#{id}
</delete>
```

```java
public interface LoginUserDao {
    // 根据 id 删除用户
    void deleteUser(@Param("id") long id);
}
```

#### 5.3 更新

```java
public interface LoginUserDao {
    // 更新用户
    void updateUser(LoginUser user);
}
```

```xml
<update id="updateUser" parameterType="LoginUser">
    update login_user
    set name=#{name},password=#{password},register_date=#{registerDate}
    where id=#{id}
</update>
```

#### 5.4 新增

```java
public interface LoginUserDao {
    // 新增用户
    void addUser(LoginUser user);
}
```

```xml
<!--自动增加主键-->
<insert id="addUser" parameterType="LoginUser">
    insert into login_user(name, password, register_date) values (#{name},#{password},#{registerDate})
</insert>
<insert id="addUser" parameterType="LoginUser">
    insert into login_user values (NULL,#{name},#{password},#{registerDate})
</insert>
<!--手动增加主键-->
<insert id="addUser" parameterType="LoginUser">
    insert into login_user values (#{id},#{name},#{password},#{registerDate})
</insert>
```

> 注意：上面的增、删、改方法，可以在接口方法申明时，把返回值类型声明为 Integer，这样，MyBatis 在执行完成后，会将受影响的行数返回

#### 5.5 主键回填

```xml
<insert id="addUser" parameterType="LoginUser">
    <!--主键回填：将新增数据的主键值，存入java对象和主键对应的属性中-->
    <selectKey order="AFTER" resultType="int" keyProperty="id"><!--该策略适用于主键是自增整形的主键-->
        select last_insert_id()
    </selectKey>
    insert into login_user(name, password, register_date) values (#{name},#{password},#{registerDate})
</insert>

<insert id="addUser" parameterType="LoginUser">
    <!--主键回填：将新增数据的主键值，存入java对象和主键对应的属性中-->
    <selectKey order="BEFORE" resultType="string" keyProperty="id"><!--该策略适用于主键是字符串类型的主键-->
        select replace(uuid(),'-','')
    </selectKey>
    insert into login_user(name, password, register_date) values (#{name},#{password},#{registerDate})
</insert>
```

### 6. 工具类

#### 6.1 封装工具类

* `Resource`：用于获得读取配置文件的 `IO` 对象，耗费资源，建议通过 `IO` 一次性读取所有所需要的数据
* `SqlSessionFactory`：`SqlSession` 工厂类，内存占用多，耗费资源，建议每个应用只创建一个对象
* `SqlSession`：相当于 `Connection`，可控制事务，应为线程私有，不被多线程共享
* 将获得连接、关闭连接、提交事务、回滚事务、获得接口实现类等方法进行封装

```java
public class MyBatisUtil {
    private MyBatisUtil() {}

    private static SqlSessionFactory factory;
    private static final ThreadLocal<SqlSession> THREAD_LOCAL = new ThreadLocal<>();

    static { // 加载配置并构建 session 工厂
        try {
            InputStream is = Resources.getResourceAsStream("mybatis-config.xml");
            factory = new SqlSessionFactoryBuilder().build(is);
        } catch (IOException e) {
            e.printStackTrace();
        }
    }

    /**
     * 获取 SqlSession
     * @return - SqlSession
     */
    public static SqlSession openSession() {
        SqlSession sqlSession = THREAD_LOCAL.get();
        if (sqlSession == null) {
            sqlSession = factory.openSession();
            THREAD_LOCAL.set(sqlSession);
        }
        return sqlSession;
    }

    /**
     * 提交事务
     */
    public static void commit() {
        SqlSession sqlSession = openSession();
        sqlSession.commit();
        close();
    }

    /**
     * 回滚事务
     */
    public static void rollback() {
        SqlSession sqlSession = openSession();
        sqlSession.rollback();
        close();
    }

    /**
     * 关闭 SqlSession
     */
    public static void close() {
        SqlSession sqlSession = THREAD_LOCAL.get();
        sqlSession.close();
    }

    /**
     * 获取接口相对应的 Mapper
     */
    public static <T> T getMapper(Class<T> mapper) {
        SqlSession sqlSession = openSession();
        return sqlSession.getMapper(mapper);
    }
}
```

### 7. ORM 映射【重点】

#### 7.1 MyBatis 自动 ORM 失效

`MyBatis` 只能自动维护库表“列名”与“属性名”相同时的一一对应关系，二者不同时，无法自动 `ORM`

[![gPIhjO.md.png](https://z3.ax1x.com/2021/04/28/gPIhjO.md.png)](https://imgtu.com/i/gPIhjO)

#### 7.2 方案一：列的别名

在 `SQL` 中使用 `as` 为查询字段添加列别名，以匹配属性名

#### 7.3 方案二：结果映射（ResultMap - 查询结果的封装规则）

通过 `<resultMap id="" type="">` 映射，匹配列名与属性名

```xml
<resultMap id="user_map" type="LoginUser">
  	<!--关联主键与列名-->
    <id property="id" column="id"></id>
  	<!--关联属性与列名-->
    <result property="name" column="name"/>
    <result property="password" column="password"/>
    <result property="registerDate" column="register_date"/>
</resultMap>
<!--使用 resultMap 作为 ORM 映射的依据-->
<select id="getUserById" resultMap="user_map">
    select id,name,password,register_date as registerDate
    from login_user
    where id=#{arg0}
</select>
```

### 8. 处理关联关系——多表连接【重点】

实体间的关系：关联关系（拥有 `has`、属于 `belong`）

* `OneToOne`：一对一关系（`Passenger-Passport`）
* `OneToMany`：一对多关系（`Employee-Department`）
* `ManyToMany`：多对多关系（`Student-Subject`）

#### 8.1 一对一关系

[![gPx7V0.md.png](https://z3.ax1x.com/2021/04/28/gPx7V0.md.png)](https://imgtu.com/i/gPx7V0)

```sql
# 创建数据库表
# 乘客表
create table t_passengers (
  id int primary key auto_increment, name varchar (50), sex varchar (1), birthday date
) default charset =utf8;
# 护照表
create table t_passports (
  id int primary key auto_increment, nationality varchar (50), expire date,
  passenger_id int unique,
  foreign key (passenger_id) references t_passengers(id)
) default charset =utf8;

# 插入数据
insert into t_passengers values(null,'shine 01','f','2018-11-11');
insert into t_passengers values(null,'shine 02','m','2019-12-12');
insert into t_passports values(null,'China','2030-12-12',1);
insert into t_passports values(null,'America','2035-12-12',2);
```

```java
// 创建实体
@Data
public class Passenger {

  private long id;
  private String name;
  private String sex;
  private java.sql.Date birthday;

  private Passport passport;

  @Override
  public String toString() {
    return "Passenger{" +
            "id=" + id +
            ", name='" + name + '\'' +
            ", sex='" + sex + '\'' +
            ", birthday=" + birthday +
            '}';
  }
}

@Data
public class Passport {

  private long id;
  private String nationality;
  private java.sql.Date expire;
  private long passengerId;

  private Passenger passenger;

  @Override
  public String toString() {
    return "Passport{" +
            "id=" + id +
            ", nationality='" + nationality + '\'' +
            ", expire=" + expire +
            ", passengerId=" + passengerId +
            '}';
  }
}
```

```java
// 创建接口
public interface PassengerDao {

    // 通过旅客的 ID，查询旅客信息及护照信息，关联查询/级联查询
    Passenger queryPassagerById(@Param("id") long id);
}
```

```xml
<!--创建mapper文件-->
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.ch.wchya.servlet.dao.PassengerDao">
		<!--无法使用mybatis的同名规则进行匹配的字段，需要使用 resultMap 进行自定义规则-->
    <resultMap id="passenger_passport" type="Passenger">
        <id column="id" property="id"/>
        <result column="name" property="name"/>
        <result column="sex" property="sex"/>
        <result column="birthday" property="birthday"/>

        <association property="passport" javaType="Passport">
            <id column="passId" property="id"/>
            <result column="nationality" property="nationality"/>
            <result column="expire" property="expire"/>
        </association>
    </resultMap>

    <select id="queryPassagerById" resultMap="passenger_passport">
        select t_passengers.id, t_passengers.name, t_passengers.sex, t_passengers.birthday,
               tp.id as passId, tp.nationality, tp.expire
        from t_passengers join t_passports tp
        on t_passengers.id = tp.passenger_id
        where t_passengers.id = #{id};
    </select>

</mapper>
```

```java
// 单元测试
@Test
public void testPassenger() {
    PassengerDao passengerDao = MyBatisUtil.getMapper(PassengerDao.class);
    Passenger passenger = passengerDao.queryPassagerById(1);
    System.out.println(passenger);
    System.out.println(passenger.getPassport());
}

// 下面是输出
// Passenger{id=1, name='shine 01', sex='f', birthday=2018-11-11}
// Passport{id=1, nationality='China', expire=2030-12-12, passengerId=0}
```

#### 8.2 一对多关系

```sql
# 创建表
create table t_departments (
  id int primary key auto_increment, name varchar (50), location varchar (100)
) default charset =utf8;
create table t_employees (
  id int primary key auto_increment, name varchar (50), salary double, dept_id int,
  foreign key (dept_id) references t_departments(id)
) default charset =utf8;
# 插入数据
insert into t_departments values(1,"教学部","北京"),(2,"研发部","上海");
insert into t_employees values(1,"shine01",10000.5,1),(2,"shine02",20000.5,1),
                              (3,"张三", 9000.5,2),(4,"李四",8000.5,2);
```

```java
// 创建实体
@Data
public class Department {

  private long id;
  private String name;
  private String location;

  private List<Employee> employees;

  @Override
  public String toString() {
    return "Department{" +
            "id=" + id +
            ", name='" + name + '\'' +
            ", location='" + location + '\'' +
            '}';
  }
}

@Data
public class Employee {

  private long id;
  private String name;
  private double salary;
  private long deptId;

  private Department department;

  @Override
  public String toString() {
    return "Employee{" +
            "id=" + id +
            ", name='" + name + '\'' +
            ", salary=" + salary +
            ", deptId=" + deptId +
            '}';
  }
}
```

```java
// 创建接口
public interface DepartmentDao {
    // 查询部门，及其所有员工信息
    Department queryDepartmentById(@Param("id") long id);
}
```

```xml
<!--创建mapper文件-->
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.ch.wchya.servlet.dao.DepartmentDao">

    <resultMap id="depart_employee" type="Department">
        <id property="id" column="id"/>
        <result property="name" column="name"/>
        <result property="location" column="location"/>

        <collection property="employees" ofType="Employee">
            <id column="empid" property="id"/>
            <result property="name" column="empname"/>
            <result property="salary" column="salary"/>
        </collection>
    </resultMap>
    <select id="queryDepartmentById" resultMap="depart_employee">
        select t_departments.id,t_departments.name,t_departments.location,
               employee.id empid,employee.name empname,employee.salary
        from t_departments left join t_employees employee on t_departments.id = employee.dept_id
        where t_departments.id=#{id}
    </select>
</mapper>
```

```java
@Test
public void testDepartment() {
    DepartmentDao departmentDao = MyBatisUtil.getMapper(DepartmentDao.class);
    Department department = departmentDao.queryDepartmentById(1);
    System.out.println(department);
    department.getEmployees().forEach(System.out::println);
}

// 下面是输出
// Department{id=1, name='教学部', location='北京'}
// Employee{id=1, name='shine01', salary=10000.5, deptId=0}
// Employee{id=2, name='shine02', salary=20000.5, deptId=0}
```

#### 8.3 多对多关系

[![gk4674.md.png](https://z3.ax1x.com/2021/04/29/gk4674.md.png)](https://imgtu.com/i/gk4674)

```sql
# 创建学生表、班级表、中间表
create table t_students (
    id int primary key auto_increment, name varchar (50), sex varchar (1)
) default charset =utf8;
create table t_subjects (
    id int primary key auto_increment, name varchar (50), grade int
) default charset =utf8;
create table t_stu_sub (
    student_id int, subject_id int,
    foreign key (student_id) references t_students (id),
    foreign key (subject_id) references t_subjects (id),
    primary key (student_id, subject_id)
) default charset =utf8;

# 插入数据
insert into t_students values(1,'shine','m'),(2,'张三','f');
insert into t_subjects values(1001,'JavaSE',1),(1002,'Javaweb',2); 
insert into t_stu_sub values(1,1001),(1,1002),(2,1001),(2,1002);
```

```java
// 创建实体
@Data
public class Student {

  private long id;
  private String name;
  private String sex;

  private List<Subject> subjects;

  @Override
  public String toString() {
    return "Student{" +
            "id=" + id +
            ", name='" + name + '\'' +
            ", sex='" + sex + '\'' +
            '}';
  }
}
@Data
public class Subject {

  private long id;
  private String name;
  private long grade;

  private List<Student> students;

  @Override
  public String toString() {
    return "TSubjects{" +
            "id=" + id +
            ", name='" + name + '\'' +
            ", grade=" + grade +
            '}';
  }
}
@Data
public class StuSub {

  private long studentId;
  private long subjectId;

  @Override
  public String toString() {
    return "TStuSub{" +
            "studentId=" + studentId +
            ", subjectId=" + subjectId +
            '}';
  }
}
```

```java
// 创建接口
public interface SubjectDao {
    // 查询课程及课程对应的学生信息
    Subject querySubjectById(@Param("id") long id);
}
```

```xml
<!--创建mapper文件-->
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.ch.wchya.servlet.dao.SubjectDao">

    <resultMap id="sub_stu" type="Subject">
        <id property="id" column="id"/>
        <result property="name" column="name"/>
        <result property="grade" column="grade"/>

        <collection property="students" ofType="Student">
            <id property="id" column="sid"/>
            <result property="name" column="sname"/>
            <result property="sex" column="sex"/>
        </collection>
    </resultMap>

    <select id="querySubjectById" resultMap="sub_stu">
        select ts.id, ts.name, ts.grade, t.id sid, t.name sname, t.sex
        from t_subjects ts
        join t_stu_sub tss on ts.id = tss.subject_id
        join t_students t on t.id = tss.student_id
        where ts.id=#{id}
    </select>
</mapper>
```

```java
// 测试
@Test
public void testSubject() {
    SubjectDao subjectDao = MyBatisUtil.getMapper(SubjectDao.class);
    Subject subject = subjectDao.querySubjectById(1001);
    System.out.println(subject);
    subject.getStudents().forEach(System.out::println);
}

// 以下是输出
// TSubjects{id=1001, name='JavaSE', grade=1}
// Student{id=1, name='shine', sex='m'}
// Student{id=2, name='张三', sex='f'}
```

#### 8.4 关系总结

* 一方，添加集合；多方，添加对象
* 双方均可建立关系属性，建立关系属性后，对应的 `Mapper` 文件中需要使用 `<ResultMap>` 完成多表映射
* 持有对象关系属性，使用 `<association property="xx" javaType="xx">`
* 持有集合关系属性，使用 `<collection property="xx" ofType="xx">`

### 9. 动态 SQL【重点】

`MyBatisi` 的映射文件中支持在基础 `SQL` 上添加一些逻辑操作，并动态拼接成完整的 `SQL` 之后再执行，以达到 `SQL` 复用、简化编程的效果

#### 9.1 sql

```xml
<mapper namespace="com.ch.wchya.sevlet.dao.BookDao">
		<sql id="books_field"><!-- 定义sql片断 -->
    	select id,name,author,publish,sort
    </sql>
    
    <select id="selectBookByCondition" resultType="Book">
    	<include refid="books_field" /><!--通过ID引用sql片断-->
        from t_tooks
    </select>
</mapper>
```

#### 9.2 where

```xml
<mapper namespace="com.ch.wchya.sevlet.dao.BookDao">
		<sql id="books_field"><!-- 定义sql片断 -->
    	select id,name,author,publish,sort
    </sql>
    
    <select id="selectBookByCondition" resultType="Book">
    	<include refid="books_field" /><!--通过ID引用sql片断-->
        from t_tooks
        <!--
				where 标签作用：
											1. 只会在子元素返回内容的情况下添加 where 子句；
											2. 如果以 or、and 开头，会把开头的 or、and 去掉；
				-->
        <where>
        		<if test="name!=null">
            username=#{username}
            </if>
            <if test="price!=null">
            and price=#{price}
            </if>
        </where>
    </select>
</mapper>
```

#### 9.3 set

```xml
<update id="updateBookByCondition">
	update t_books
    <set><!--去除set标签最后的逗号，-->
    	<if test="name!=null"><!-- where子句中满足条件的if，会自动忽略后缀（如：,）-->
			name=#{name},       
        </if>
        <if test="author!=null">
			author=#{author},       
        </if>
        <if test="publish!=null">
			publish=#{publish},       
        </if>
        <if test="sort!=null">
			sort=#{sort},       
        </if>
    </set>
    where id=#{id}
</update>
```

#### 9.4 trim

`<trim prefix="" suffix="" prefixOverrides="" suffixOverrides="">代替<where> <set>`

```xml
<select id="selectBookByCondition" resultType="com.ch.wchya.entity.servlet.Book">
	select id,name,author,publish,sort
    from t_books
    <!--补充where关键字，如果where子句以and或or开头，会被覆盖-->
    <trim prefix="where" prefixOverrides="and|or">
    	<if test="id!=null">
        	and id=#{id}
        </if>
    	<if test="author!=null">
			author=#{author},       
        </if>
        <if test="publish!=null">
			publish=#{publish},       
        </if>
        <if test="sort!=null">
			sort=#{sort},       
        </if>
    </trim>
</select>

<update id="updateBookByCondition">
	update t_books
    <trim prefix="set" suffixOverrides=","><!--去除set标签最后的逗号，-->
    	<if test="name!=null">
			name=#{name},       
        </if>
        <if test="author!=null">
			author=#{author},       
        </if>
        <if test="publish!=null">
			publish=#{publish},       
        </if>
        <if test="sort!=null">
			sort=#{sort},       
        </if>
    </trim>
    where id=#{id}
</update>
```

#### 9.5 foreach

```xml
<delete id="deleteBookByIds">
	delete from t_books
    where id in
    <foreach collection="list" open="(" separator="," close=")" item="id" index="i">
    	#{id}
    </foreach>
</delete>
```

| 参数         | 描述     | 取值                                        |
| ------------ | -------- | ------------------------------------------- |
| `collection` | 容器类型 | `list、array、map`                          |
| `open`       | 起始符   | `(`                                         |
| `close`      | 结束符   | `)`                                         |
| `separator`  | 分隔符   | `,`                                         |
| `index`      | 下标号   | 从0开始，依次递增                           |
| `item`       | 当前项   | 任意名称（循环中通过#{任意名称}表达式访问） |

### 10. 缓存（Cache）【重点】

内存中的一块存储空间，服务于某个应用程序，旨在将频繁读取的数据临时保存在内存中，便于二次快速访问

[![gAecl9.md.png](https://z3.ax1x.com/2021/04/30/gAecl9.md.png)](https://imgtu.com/i/gAecl9)



#### 10.1 一级缓存

`SqlSession` 级别的缓存，同一个 `SqlSession` 发起的多次同构查询，会将数据保存在一级缓存中

#### 10.2 二级缓存

`SqlSessionFactory` 级别的缓存，同一个 `SqlSessionFactory` 构建的 `SqlSession` 发起的多次同构查询，会将数据保存在二级缓存中

> 注意：在 sqlSession.commit() 或者 sqlSessin.close() 之后生效

##### 开启全局缓存

在 `mybatis-config.xml` 文件中，全局缓存是默认开启的

##### 指定 Mapper 缓存

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="com.ch.wchya.servlet.dao.DepartmentDao">
    <!--二级缓存默认开启，但是并不是所有的查询结果，都会进入二级缓存-->
  	<!--在Mapper中写了<cache/>标签的文件里所有的查询方法都会进行缓存-->
    <cache/>
    <resultMap id="depart_employee" type="Department">
        <id property="id" column="id"/>
        <result property="name" column="name"/>
        <result property="location" column="location"/>

        <collection property="employees" ofType="Employee">
            <id column="empid" property="id"/>
            <result property="name" column="empname"/>
            <result property="salary" column="salary"/>
        </collection>
    </resultMap>
    <select id="queryDepartmentById" resultMap="depart_employee">
        select t_departments.id,t_departments.name,t_departments.location,
               employee.id empid,employee.name empname,employee.salary
        from t_departments left join t_employees employee on t_departments.id = employee.dept_id
        where t_departments.id=#{id}
    </select>
</mapper>
```

##### 缓存清空并重新缓存

```java
@Test
public void testLoginUserCache() {
    SqlSession sqlSession = MyBatisUtil.getSession();
    LoginUserDao userDao = sqlSession.getMapper(LoginUserDao.class);
    LoginUser user1 = userDao.getUserById(1);
    // 必须关闭 SqlSession 才可缓存数据
    sqlSession.close();

    SqlSession session = MyBatisUtil.getSession();
    LoginUserDao userDao1 = session.getMapper(LoginUserDao.class);
    LoginUser loginUser = new LoginUser();
    loginUser.setName("缓存");
    loginUser.setPassword("huancun");
    loginUser.setRegisterDate(new Date());
    Integer count = userDao1.addUser(loginUser);
    session.commit(); // DML 成功，数据发生变化，缓存清空
    session.close();

    SqlSession session1 = MyBatisUtil.getSession();
    LoginUserDao mapper = session1.getMapper(LoginUserDao.class);
    LoginUser user = mapper.getUserById(1);
    session1.close(); // 缓存未击中，重新查询数据库，重新缓存

    SqlSession session2 = MyBatisUtil.getSession();
    LoginUserDao mapper1 = session2.getMapper(LoginUserDao.class);
    LoginUser user2 = mapper1.getUserById(1);
    session2.close(); // 缓存击中，使用缓存
}
```

### 11. Druid 连接池

#### 11.1 概念

`Druid` 是阿里巴巴开源平台上的一个项目，整个项目由数据库连接池、插件框架和 `SQL` 解析器组成。该项目主要是为了扩展 `JDBC` 的一些限制，可以让程序员实现一些特殊的需求，比如向密钥服务请求凭证、统计 `SQL` 信息、`SQL` 性能收集、`SQL` 注入检查、`SQL` 翻译等，程序员可以通过定制来实现自己需要的功能

#### 11.2 不同连接池对比

测试执行申请归还连接 1,000,000（一百万）次总耗时性能对比

##### 测试环境

| 环境  | 版本                    |
| ----- | ----------------------- |
| `OS`  | `OS X 10.8.2`           |
| `CPU` | `Intel I7 2GHz 4 Core`  |
| `JVM` | `Java Version 1.7.0_05` |

##### 基准测试结果对比

[![gAUzqK.md.png](https://z3.ax1x.com/2021/04/30/gAUzqK.md.png)](https://imgtu.com/i/gAUzqK)

##### 测试结论

* `Druid` 是性能最好的数据库连接池，`tomcat-jdbc` 和 `druid` 性能接近
* `C3P0` 相当慢，影响 `sql` 执行效率
* `BoneCP` 性能并不优越，采用 `LinkedTransferQueue` 并没有能够获得性能提升
* 除了 `boneCP`，其它的在 `JDK 7` 上跑得比 `JDK 6` 上快
* `jboss-datasource` 虽然稳定，但性能很糟糕

#### 11.3 配置 pom.xml

引入依赖：

```xml
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid</artifactId>
    <version>1.2.5</version>
</dependency>
```

#### 11.4 创建 DruidDataSourceFactory

`MyDruidDataSourceFactory` 继承自 `PooledDataSourceFactory`，并替换数据源：

```java
import com.alibaba.druid.pool.DruidDataSource;
import org.apache.ibatis.datasource.pooled.PooledDataSourceFactory;

public class MyDruidDataSourceFactory extends PooledDataSourceFactory {
    public MyDruidDataSourceFactory() {
        this.dataSource = new DruidDataSource(); // 替换数据源
    }
}
```

#### 11.5 替换配置文件中的工厂类

```xml
<!--核心配置信息-->
<environments default="main_config">
    <!--数据库相关信息-->
    <environment id="main_config">
        <!--事务控制类型-->
        <transactionManager type="jdbc"></transactionManager>
        <!--数据库连接参数-->
        <dataSource type="com.ch.wchya.servlet.utils.MyDruidDataSourceFactory"><!--这里替换为上面的类-->
            <property name="driverClass" value="${driver}"/><!--这里更换为 driverClass-->
            <property name="jdbcUrl" value="${url}"/><!--这里更换为 jdbcUrl-->
            <property name="username" value="${username}"/>
            <property name="password" value="${password}"/>
        </dataSource>
    </environment>
</environments>
```

### 12. PageHelper

`PageHelper` 是适用于 `MyBatis` 框架的一个分布插件，使用方式极为便捷，支持任何复杂的单表、多表分布查询操作

#### 12.1 访问与下载

[官方网站](https://pagehelper.github.io)

[下载地址](https://github.com/pagehelper/Mybatis-PageHelper)

#### 12.2 开发步骤

`PageHelper` 中提供了多个分布操作的静态方法入口

#### 12.3 引入依赖

`pom.xml` 中引入 `PageHelper` 依赖

```xml
<dependency>
    <groupId>com.github.pagehelper</groupId>
    <artifactId>pagehelper</artifactId>
    <version>5.1.10</version>
</dependency>
```

#### 12.4 在 MyBatis 中安装插件

在 `mybatis-config.xml` 中添加如下配置：

```xml
<plugins>
    <plugin interceptor="com.github.pagehelper.PageInterceptor"></plugin>
</plugins>
```

#### 12.5 分页

```java
@Test
public void testPageHelper() {
    LoginUserDao userDao = MyBatisUtil.getMapper(LoginUserDao.class);
  	// 在查询前，设置分布，查询第一页，每页3条数据
    // PageHelper 对其之后的第一个查询，进行分页功能追加
    PageHelper.startPage(1, 3);
    List<LoginUser> loginUsers = userDao.queryForAll();
    loginUsers.forEach(System.out::println);
}
```

##### PageInfo 应用

```java
@Test
public void testPageHelper() {
    LoginUserDao userDao = MyBatisUtil.getMapper(LoginUserDao.class);
    // 在查询前，设置分布，查询第一页，每页3条数据
    // PageHelper 对其之后的第一个查询，进行分页功能追加
    PageHelper.startPage(1, 3);
    List<LoginUser> loginUsers = userDao.queryForAll();
    loginUsers.forEach(System.out::println);
    // 包装后的 pageInfo，会有分页相关的一切信息
    PageInfo<LoginUser> pageInfo = new PageInfo<>(loginUsers);
    System.out.println("-----");
}
```

##### 注意事项

* 只有在 `PageHelper.startPage()` 方法之后的第一个查询会有执行分页
* 分布插件不支持带有 `for udpate` 的查询语句
* 分页插件不支持 **嵌套查询**，会导致结果集折叠

##### 分页练习

使用 `Servlet+JSP+MyBatis+分页插件`，完成分页查询功能 

### 13. 补充【了解】

#### 13.1 MyBatis 注解操作

通过在接口中直接添加 `MyBatis` 注解，完成 `CRUD`

* 接口注解定义完毕后，需将接口全限定名注册到 `mybatis-config.xml` 的 `<mappers>` 节点中
* 经验：注解模式属于硬编码到 `.java` 文件中，失去了使用配置文件外部修改的优势，可结合需求选用

```xml
<mappers>
  <mapper class="com.ch.wchya.servlet.dao.LoginUserDao"/><!--class="接口全限定名"-->
</mapper>
```

##### 查询

```java
public interface LoginUserDao {
  @Select("select * from login_user where id=#{id}")
  public LoginUser selectUserById(Integer id);
  
  @Select("select * from login_user where id=#{id} and password=#{pwd}")
  public LoginUser selectUserByIdAndPwd(@Param("id") Integer id, @Param("pwd") String password);
}
```

##### 删除

```java
@Delete(value="delete from login_user where id=#{id}")
public int deleteUser(Integer id);
```

##### 修改

```java
@Update("update login_user set name=#{name},password=#{password},salary=#{salary},birthday=#{birthday} where id=#{id}")
public int updateUser(LoginUser user);
```

##### 插入

```java
@Insert("insert into login_user values(#{id},#{name},#{password},#{salary},#{birthday},null)")
public int insertUser(LoginUser user);

@Options(useGeneratedKeys=true, keyProperty="id") // 自增 key，主键为 id
@Insert("insert into login_user values(#{id},#{name},#{password},#{salary},#{birthday},null)")
public int insertUserGeneratedKeys(LoginUser user);
```

#### 13.2 $ 符的应用场景

`${attribute}` 属于字符串拼接 `SQL`，而非预编译占位符，会有注入攻击问题，不建议在常规 `SQL` 中使用，常用于可解决动态升降序问题

##### 符号参数绑定

```java
public List<LoginUser> selectAllUsers2(LoginUser user);// ${name} ${id} 可获取 user 中的属性值
public Liist<LoginUser> selectAllUsers2(@Param("rule") String rule);// 必须使用 @Param，否则会作为属性解析
```

```xml
<select id="selectAllUsers" resultType="user">
  select * from login_user
  where name='${name}' or id=${id} <!--拼接name和id，如果是字符类型需要用单引号-->
</select>
<select id="selectAllUsers2" resultType="user">
  select * from login_user
  order by id ${rule} <!--拼接 asc|desc-->
</select>
```

```java
LoginUser user = new LoginUser(...);
List<LoginUser> users1 = userDao.selectAllUsers1(user); // 调用时传入 user 对象
List<LoginUser> users2 = userDao.selectAllUsers2("desc"); // 调用时传入 asc | desc
```

##### sql 注入

使用 `$` 作为参数的值进行拼接时，会有 `SQL` 注入的风险，不建议使用

#### 13.3 MyBatis 处理关联关系-嵌套查询【了解】

思路：查询部门信息时，关联查询所属的员工信息

* `DepartmentDao` 接口中定义 `selectDepartmentById`，并实现 `Mapper`
* `EmployeeDao` 接口中定义 `selectEmployeesByDeptId`，并实现 `Mapper`
* 当 `selectDepartmentById` 被执行时，通过 `<collection>` 调用 `selectEmployeesByDeptId` 方法，并传入条件参数

##### 主表查询

定义 `selectEmployeesByDeptId`，并书写 `Mapper`，实现根据部门 `ID` 查询员工信息

```java
public interface EmployeeDao {
  /**
   * 根据部门编号查询员工信息
   * @param did 部门编号
   * @return 该部门中的所有员工
   */
  public List<Employee> selectEmployeeByDeptId(@param("did") String did);
}
```

```xml
<mapper namespace="com.ch.wchya.servlet.dao.EmployeeDao">
  <!--根据部门编号查询所有员工-->
  <select id="selectEmployeeById" resultType="employee">
    select id,name,salary,dept_id
    from t_employees
    where dept_id=#{did}
  </select>
</mapper>
```

##### 级联调用

定义 `selectDepartmentById`，并书写 `Mapper`，实现根据部门 `ID` 查询部门信息，并级联查询该部门员工信息

```java
public interface DepartmentDao {
  /**
   * 查询部门信息
   * @param id
   * @return
   */
  public Department selectDepartmentById(@Param("id") String id);
}
```

```xml
<mapper namespace="com.ch.wchya.servlet.dao.DepartmentDao">
  <resultMap id="departmentResultMap" type="department">
    <id property="id" column="name"/>
    <result property="name" column="name"/>
    <result property="location" column="location" />
    <!--column="传入目标方法的条件参数" select="级联调用的查询目标"-->
    <collection property="emps" ofType="Employee" column="id"
                select="com.ch.wchya.servlet.dao.EmployeeDao.selectEmployeeByDeptId" />
  </resultMap>
  <select id="selectAllDepartments" resultMap="departmentResultMap">
    select id,name,location
    from t_departments
    where id=#{id}
  </select>
</mapper>
```

##### 延迟加载

`mybatis-config.xml` 中开启延迟加载

```xml
<settings>
  <setting name="lazyLoadingEnabled" value="true"/><!--开启延迟加载（默认false）-->
</settings>
```

> 注意：开启延迟加载后，如果不使用级联数据，则不会触发级联查询操作，有利于加快查询速度，节省内存资源

## 第三十二章 Spring

### 1. 原生 Web 开发中存在的问题

* 传统 `web` 开发存在硬编码所造成的过度程序耦合（例如：`Service` 中作为属性 `Dao` 对象）
* 部分 `Java EE API` 较为复杂，使用效率低（例如：`JDBC` 开发步骤
* 侵入性强，移植性差（例如：`DAO` 实现的更换）

### 2. Spring 框架

#### 2.1 概念

* `spring` 是一个项目管理框架，同时也是一套 `Java EE` 解决方案
* `Spring` 是众多优秀设计模式的组合（工厂、单例、适配器、包装器、观察者、模板、策略）
* `Spring` 并未替代现有框架产品，而是将众多框架进行有机整合，简化企业级开发，俗称 “胶水框架”

#### 2.2 访问与下载

[官方网站](https://spring.io/)

[下载地址](http://repo.spring.io/release/org/springframework/spring)

### 3. Spring 架构组成

`Spring` 架构由诸多模块组成，可分类为：

* 核心技术：依赖注入，事件，资源，`i18n`，验证，数据绑定，类型转换，`SpEL`，`AOP`
* 测试：模拟对象，`TestContext` 框架，`Spring MVC` 测试，`WebTestClient`
* 数据访问：事务，`DAO` 支持，`JDBC`，`ORM`，封装 `XML`
* `Spring MVC` 和 `Spring WebFlux Web` 框架
* 集成：远程处理，`JMS`，`JCA`，`JMX`，电子邮件，任务，调度，缓存
* 语言：`Kotlin`，`Groovy`，动态语言

[![cjBQoV.md.png](https://z3.ax1x.com/2021/04/24/cjBQoV.md.png)](https://imgtu.com/i/cjBQoV)



| GroupId               | ArtifactId                   | 说明                                                |
| --------------------- | ---------------------------- | --------------------------------------------------- |
| `org.springframework` | [`spring-beans`]()           | [`Beans` 支持，包含 `Groovy`]()                     |
| `org.springframework` | [`spring-aop`]()             | [基于代理的 `AOP` 支持]()                           |
| `org.springframework` | [`spring-aspects`]()         | [基于 `AspectJ` 的切面]()                           |
| `org.springframework` | [`spring-context`]()         | [应用上下文运行时，包括调试和远程抽象]()            |
| `org.springframework` | [`spring-context-support`]() | [支持将觉的第三方类库集成到 `Spring` 应用上下文]()  |
| `org.springframework` | [`spring-core`]()            | [其它模块所依赖的核心模块]()                        |
| `org.springframework` | [`spring-expression`]()      | [`Spring` 表达式语言，`SpEL`]()                     |
| `org.springframework` | `spring-instrument`          | `JVM` 引导仪表（监测器）代理                        |
| `org.springframework` | `spring-instrument-tomcat`   | `Tomcat` 的仪表（监测器）代理                       |
| `org.springframework` | `spring-jdbc`                | 支持包括数据源设置和 `JDBC` 访问支持                |
| `org.springframework` | `spring-jms`                 | 支持包括发送/接收 `JMS` 消息的助手类                |
| `org.springframework` | `spring-messaging`           | 对消息架构和协议的支持                              |
| `org.springframework` | `spring-orm`                 | 对象/关系映射，包括对 `JPA` 和 `Hibernate` 的支持   |
| `org.springframework` | `spring-oxm`                 | 对象 / `XML` 映射（`Object/XML Mapping，OXM`）      |
| `org.springframework` | [`spring-test`]()            | [单元测试和集成测试支持组件]()                      |
| `org.springframework` | [`spring-tx`]()              | [事务基础组件，包括对 DAO 的支持及 JCA 的集成]()    |
| `org.springframework` | [`spring-web`]()             | [web 支持包，包括客户端及 web 远程调用]()           |
| `org.springframework` | [`spring-webmvc`]()          | [REST web 服务器及 web 应用的 MVC 实现]()           |
| `org.springframework` | `spring-webmvc-portlet`      | 用于 `Portlet` 环境的 `MVC` 实现                    |
| `org.springframework` | `spring-websocket`           | `WebSocket` 和 `SockJS` 实现，包括对 `STOMP` 的支持 |
| `org.springframework` | [spring-jcl]()               | [Jakarta Commons Logging` 日志系统]()               |

### 4. 自定义工厂

#### 4.1 配置文件

```properties
userDao=com.ch.wchya.springprimary.dao.UserDaoImpl
userService=com.ch.wchya.springprimary.service.UserServiceImpl
```

#### 4.2 工厂类

```java
public class FactoryDIY {
    private static final Properties PROPERTIES = new Properties();

    public FactoryDIY(String config) throws IOException {
        PROPERTIES.load(FactoryDIY.class.getResourceAsStream(config));
    }

    public Object getBean(String beanName) throws ClassNotFoundException, IllegalAccessException, InstantiationException {
        String classPath = PROPERTIES.getProperty(beanName);
        if (classPath != null) {
            // 通过反射加载类
            Class aClass = Class.forName(classPath);
            // 通过反射获取类对象
            return aClass.newInstance();
        }
        return null;
    }
}
```

### 5. Spring 环境搭建

#### 5.1 POM 文件中引入常用依赖

```xml
<dependencies>
    <dependency>
        <groupId>org.springframework</groupId>
        <artifactId>spring-context</artifactId>
        <version>5.2.9.RELEASE</version>
    </dependency>
</dependencies>
```

#### 5.2 创建 Spring 配置文件

命名无限制，约定俗成命名有：`spring-context.xml、applicationContext.xml、beans.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
  
</beans>
```

#### 5.3 添加配置

在上面创建的 `xml` 中添加配置：

```xml
<!--需要工厂生产的对象-->
<bean id="userDao" class="com.ch.wchya.springprimary.dao.UserDaoImpl"></bean>
<bean id="userService" class="com.ch.wchya.springprimary.service.UserServiceImpl"></bean>
```

#### 5.4 创建测试类

```java
@Test
public void testSpringFactory() {
    // 启动工厂
    ApplicationContext context = new ClassPathXmlApplicationContext("/beans.xml");
    // 获得对象
    UserDao userDao = (UserDao) context.getBean("userDao");
    UserService userService = (UserService) context.getBean("userService");

    userDao.printInfo();
    userService.printInfo();
}
```

### 6. 依赖与配置文件详解

`Spring` 框架包含多个模块，每个模块各司其职，可结合需求引入相关依赖 `jar` 包实现功能

#### 6.1 Spring 依赖关系

[![gVEZQA.md.png](https://z3.ax1x.com/2021/05/01/gVEZQA.md.png)](https://imgtu.com/i/gVEZQA)

> 注意：jar 包彼此存在依赖，只需引入最外层 jar 即可由 maven 自动将相关依赖 jar 引入到项目中

#### 6.2 schema

配置文件中的顶级标签中包含了语义化标签的相关信息：

* `xmlns`：语义化标签所在的命名空间
* `xmlns:xsi`：`XMLSchema-instance` 标签遵循 `schema` 标签标准
* `xsi:schemaLocation`：`xsd` 文件位置，用以描述标签语义、属性、取值范围等

### 7. IoC（Inversion of ）控制反转【重点】

* 反转了依赖关系的满足方式，由之前的自己创建依赖对象，变为由工厂推送（变主动为被动，即反转）

* 解决了具有依赖关系的组件之间的强耦合，使得项目形态更加稳健

#### 7.1 项目中强耦合问题

```java
public class UserDaoImpl implements UserDao {...}
```

```java
public class UserServiceImpl implements UserService {
  // 强耦合了 UserDaoImpl，使得 UserServiceImpl 变得不稳健
  private UserDao userDao = new UserDaoImpl();
  @Override
  public User queryUser() {
    return userDao.queryUser();
  }
  ...
}
```

#### 7.2 解决方案

```java
// 不引用任何一个具有的组件（实现类），在需要其他组件的位置预留存取值入口（set/get）
public class UserServiceImpl implements UserService {
  // 不再耦合任何 dao 实现，消除不稳健因素
  private UserDao userDao;
  // 为 userDao 定义 get/set，允许 userDao 属性接收 spring 赋值
  // getters and setters
  ...
}
```

```xml
<bean id="userDao" class="com.ch.wchya.servlet.dao.UserDaoImpl"></bean>
<!--UserServiceImpl组件-->
<bean id="userService" class="com.ch.wchya.servlet.service.UserServiceImpl">
  <!--由spring为userDao属性赋值，值为id="userDao"的bean-->
  <property name="userDao" ref="userDao"/>
</bean>
```

此时，如果需要更换其它 `UserDao` 实现类，则 `UserServiceImpl` 不用任何改动！现在的 `UserServiceImpl` 组件变得更加稳健

### 8. DI（Dependency Injection）依赖注入【重点】

#### 8.1 概念

在 `Spring` 创建对象的同时，为其属性赋值，称之为依赖注入

#### 8.2 Set 注入

创建对象时，`Spring` 工厂会通过 `set` 方法为对象的属性赋值

##### 定义目标 Bean 类型

```java
@Data
public class Address {
    private Integer id;
    private String city;
}
@Data
public class User {
    private Integer id;
    private String password;
    private String sex;
    private Integer age;
    private Date bornDate;
    private String[] hobbys;
    private Set<String> phones;
    private List<String> names;
    private Map<String, String> countries;
    private Properties files;
    // 自定义属性
    private Address address;
}
```

##### 在 beans.xml 中注入值

```xml
<bean id="addr" class="com.ch.wchya.entity.springprimary.Address">
    <property name="id" value="1"/>
    <property name="city" value="beijing"/>
</bean>

<bean id="user" class="com.ch.wchya.entity.springprimary.User">
    <!--基本数据类型，String，Date-->
    <property name="id" value="1234"/>
    <property name="password" value="4321"/>
    <property name="sex" value="男"/>
    <property name="age" value="12"/>
    <property name="bornDate" value="2013/03/03 03:03:03"/><!--注意：这里的字符日期中只能使用/分隔，不能使用-分隔-->

    <!--集合，Properties-->
    <property name="hobbys">
        <array>
            <value>游泳</value>
            <value>跑步</value>
        </array>
    </property>
    <property name="phones">
        <set>
            <value>18919999999</value>
            <value>18818888888</value>
        </set>
    </property>
    <property name="names">
        <list>
            <value>张三</value>
            <value>李四</value>
        </list>
    </property>
    <property name="countries">
        <map>
            <entry key="cn" value="Chinesse"/>
            <entry key="en" value="English"/>
        </map>
    </property>
    <property name="files">
        <props>
            <prop key="url">jdbc:mysql://localhost:3306/emp?useUnicode=true&amp;characterEncoding=utf-8</prop>
            <prop key="username">username</prop>
        </props>
    </property>

    <!--自定义属性-->
    <property name="address" ref="addr"/>
</bean>
```

##### 测试

```java
@Test
public void testSetDI() {
    ApplicationContext context = new ClassPathXmlApplicationContext("/beans.xml");
    User user = (User) context.getBean("user");
    System.out.println(user);
}

// 以下是输出
// User(id=1234, password=4321, sex=男, age=12, bornDate=Sun Mar 03 03:03:03 CST 2013, hobbys=[游泳, 跑步], phones=[18919999999, 18818888888], names=[张三, 李四], countries={cn=Chinesse, en=English}, files={url=jdbc:mysql://localhost:3306/emp?useUnicode=true&characterEncoding=utf-8, username=username}, address=Address(id=1, city=beijing))
```

#### 8.3 构造注入【了解】

创建对象时，`spring` 工厂会通过构造方法为对象的属性赋值

##### 定义目标 bean 类型

```java
@Data
public class Student {
    private Integer id;
    private String name;
    private String sex;
    private Integer age;

    public Student(Integer id, String name, String sex, Integer age) {
        this.id = id;
        this.name = name;
        this.sex = sex;
        this.age = age;
    }
}
```

##### 在 beans.xml 中注入值

```xml
<!--构造注入-->
<bean id="student" class="com.ch.wchya.entity.springprimary.Student">
    <constructor-arg name="id" value="1"/>
    <constructor-arg name="name" value="shine"/>
    <constructor-arg name="sex" value="male"/>
    <constructor-arg name="age" value="1"/>
</bean>
```

##### 测试

```java
@Test
public void testConstructDI() {
    ApplicationContext context = new ClassPathXmlApplicationContext("/beans.xml");
    Student student = (Student) context.getBean("student");
    System.out.println(student);
}

// 以下是输出
// Student(id=1, name=shine, sex=male, age=1)
```

#### 8.4 自动注入

不用在配置中，指定为哪个属性赋值，及赋什么值。由 `spring` 自动根据某个”原则“，在工厂中查找一个 `bean`，为属性注入属性值

```java
public class UserServiceImpl implements UserService {
  private UserDao userDao;
  // getters and setters
  ...
}
```

```xml
<bean id="userDao" class="com.ch.wchya.springprimary.service.UserDaoImpl"/>
<!--为UserServiceImpl中的属性基于类型自动注入值-->
<bean id="userService" class="com.ch.wchya.springprimary.service.UserServiceImpl" autowire="byType"/>
```

```xml
<bean id="userDao" class="com.ch.wchya.springprimary.service.UserDaoImpl"/>
<!--为UserServiceImpl中的属性基于名称自动注入值-->
<bean id="userService" class="com.ch.wchya.springprimary.service.UserServiceImpl" autowire="byName"/>
```

### 9. bean 细节

#### 9.1 控制简单对象的单例、多例模式

配置：`<bean scope="singleton|prototype"/>`

```xml
<!--
		singleton（默认）：每次调用工作，得到的都是同一个对象
		prototype：每次调用工厂，都会创建新的对象
-->
<bean id="mc" class="com.ch.wchya.entity.springprimary.MyClass" scope="singleton"/>
```

* 需要根据场景决定对象的单例、多例模式
* 可以共用：`Service、Dao、SqlSessionFactory` 或者是所有的工厂
* 不可共用：`Connection、SqlSession、ShoppingCart`

#### 9.2 FactoryBean 创建复杂对象【了解】

作用：让 `Spring` 可以创建复杂对象、或者无法直接通过反射创建的对象

##### 实现 FactoryBean

```java
public class MyFactoryBean implements FactoryBean<Connection> {
    @Override
    public Connection getObject() throws Exception {
        Class.forName("com.mysql.cj.jdbc.Driver");
        return DriverManager.getConnection("jdbc:mysql://localhost:3306/emp?useUnicode=true&characterEncoding=utf-8", "xxxx", "xxxx");
    }

    @Override
    public Class<?> getObjectType() {
        return Connection.class;
    }

    @Override
    public boolean isSingleton() {
        return false;
    }
}
```

##### beans.xml 添加配置

```xml
<bean id="conn" class="com.ch.wchya.springprimary.factory.MyFactoryBean"/>
```

##### 测试

```java
@Test
public void testMyFactoryBean() throws SQLException {
    ApplicationContext context = new ClassPathXmlApplicationContext("/beans.xml");
    Connection conn = (Connection) context.getBean("conn");
    Connection conn1 = (Connection) context.getBean("conn");
    Connection conn2 = (Connection) context.getBean("conn");
    System.out.println(conn);
    System.out.println(conn1);
    System.out.println(conn2);
    PreparedStatement pstm = conn.prepareStatement("select * from login_user");
    ResultSet rs = pstm.executeQuery();
    rs.next();
    System.out.println(rs.getString(2));
}

// 下面是输出
com.mysql.cj.jdbc.ConnectionImpl@3a4e343
com.mysql.cj.jdbc.ConnectionImpl@6a1d204a
com.mysql.cj.jdbc.ConnectionImpl@62dae245
张三
```

### 10. spring 工厂特性

#### 10.1 饿汉式创建优势

工厂创建之后，会将 `spring` 配置文件中的所有对象都创建完成（饿汉式）

好处：提高程序运行效率，避免多次 `IO`，减少对象创建时间（这个概念接近连接池，一次性创建好，使用时直接获取）

#### 10.2 生命周期方法

* 自定义初始化方法：添加 `init-method` 属性，`spring` 则会在创建对象之后，调用此方法
* 自定义销毁方法：添加 `destory-method` 属性，`spring` 则会在销毁对象之前，调用此方法
* 销毁：工厂的 `close()` 方法被调用之后，`spring` 会毁掉所有已创建的单例对象
* 分类：`Singleton` 对象由 `spring` 容器销毁，`Prototype` 对象由 `JVM` 销毁

在原有的 `Address` 类中添加一些打印语句和两个用于初始化和销毁的方法：

```java
@Data
public class Address {
    private Integer id;
    private String city;

    public Address() {
        System.out.println("Address 空构造方法");
    }

    public void setId(Integer id) {
        System.out.println("Address setId");
        this.id = id;
    }

    public void setCity(String city) {
        System.out.println("Address setCity");
        this.city = city;
    }

    public void init_addr() {
        System.out.println("Address 初始化方法");
    }

    public void destory_addr() {
        System.out.println("Address 销毁方法");
    }
}
```

修改 `beans.xml` 中 `Address` 的相关配置：

```xml
<bean id="addr" class="com.ch.wchya.entity.springprimary.Address" init-method="init_addr" destroy-method="destory_addr">
    <property name="id" value="1"/>
    <property name="city" value="beijing"/>
</bean>
```

测试：

```java
@Test
public void testBeanLifeCycle() {
    ClassPathXmlApplicationContext context = new ClassPathXmlApplicationContext("/beans2.xml");

    System.out.println("=========");
    context.close();
}

// 下面是输出
// Address 空构造方法
// Address setId
// Address setCity
// Address 初始化方法
// =========
// Address 销毁方法
```

#### 10.3 生命周期注解

```java
@PostConstruct // 初始化
public void init() {
  System.out.println("init method execute");
}
@PreDestory // 销毁
public void destory() {
  System.out.println("destory method execute");
}
```

#### 10.4 生命周期阶段

* 单例 `bean（singleton）`：
  * 随工厂启动 创建 =》构造方法 =》set方法（注入值）=》init（初始化）=》构建完成 =》随工厂关闭 销毁
* 多例 `bean（prototype）`：
  * 被使用时 创建 =》 构造方法 =》set方法（注入值）=》init（初始化）=》构建完成 =》JVM 垃圾回收 销毁

### 11. 代理设计模式

#### 11.1 概念

将核心功能与辅助功能（事务、日志、性能监控代码）分享，达到核心业务功能更纯粹、辅助业务功能可复用

[![gV5dte.md.png](https://z3.ax1x.com/2021/05/01/gV5dte.md.png)](https://imgtu.com/i/gV5dte)

#### 11.2 静态代理设计模式

通过代理类的对象，为原始类的对象（目标类的对象）添加辅助功能，更容易更换代理实现类、利于维护

[![gKTOv8.md.png](https://z3.ax1x.com/2021/05/05/gKTOv8.md.png)](https://imgtu.com/i/gKTOv8)

```java
/**
 * 描述: 房东Service
 **/
public interface HouseOwnerService {
    void rentHousetoOthers();
}

/**
 * 描述: 房东
 **/
public class HouseOwner implements HouseOwnerService {
    @Override
    public void rentHousetoOthers() {
        System.out.println("签合同");
        System.out.println("收房租");
    }
}

/**
 * 描述: 房东代理——中介
 **/
public class HouseOwnerProxy implements HouseOwnerService {

    private HouseOwner houseOwner = new HouseOwner();
    @Override
    public void rentHousetoOthers() {
        System.out.println("发布租房信息");
        System.out.println("带租客看房");

        houseOwner.rentHousetoOthers();
    }
}

/**
 * 描述: 测试代理模式
 **/
public class TestProxyDesignModel {

    @Test
    public void testStaticsProxy() {
        HouseOwnerProxy proxy = new HouseOwnerProxy();
        proxy.rentHousetoOthers();
    }
}

// 以下是输出
// 发布租房信息
// 带租客看房
// 签合同
// 收房租
```

#### 11.3 动态代理设计模式

动态创建代理的对象，为原始类的对象添加辅助功能

##### JDK 动态代理实现（基于接口）

```java
import java.lang.reflect.InvocationHandler;
import java.lang.reflect.Method;
import java.lang.reflect.Proxy;

@Test
public void testJDKDynamicProxy() {
    // 目标
    HouseOwnerService houseOwnerService = new HouseOwner();

    // 额外功能
    InvocationHandler handler = new InvocationHandler() {

        @Override
        public Object invoke(Object proxy, Method method, Object[] args) throws Throwable {
            // 增加额外功能
            System.out.println("发布租房信息");
            System.out.println("带租客看房");
            // 调用核心功能
            houseOwnerService.rentHousetoOthers();
            return null;
        }
    };

    // 动态生成代理类
    HouseOwnerService service = (HouseOwnerService) Proxy.newProxyInstance(TestProxyDesignModel.class.getClassLoader(), houseOwnerService.getClass().getInterfaces(), handler);

    service.rentHousetoOthers();
}
```

##### CGLib 动态代理实现（基于继承）

```java
import org.springframework.cglib.proxy.Enhancer;

@Test
public void testCGLib() {
    // 目标
    HouseOwnerService houseOwnerService = new HouseOwner();

    Enhancer enhancer = new Enhancer();
    enhancer.setSuperclass(HouseOwner.class);
    enhancer.setCallback(new org.springframework.cglib.proxy.InvocationHandler() {
        @Override
        public Object invoke(Object o, Method method, Object[] objects) throws Throwable {
            // 增加额外功能
            System.out.println("发布租房信息");
            System.out.println("带租客看房");
            // 调用核心功能
            houseOwnerService.rentHousetoOthers();
            return null;
        }
    });

    // 动态生成代理类
    HouseOwner proxy = (HouseOwner) enhancer.create();

    proxy.rentHousetoOthers();
}
```

### 12. 面向切面编程【重点】

#### 12.1 概念

`AOP（Aspect Oriented Programming）`，即面向切面编程，利用一种称为“横切”的技术，剖开封装的对象内部，并将那些影响了多个类的公共行为封装到一个可重用模块，并将其命名为 `Aspect`，即切面。所谓切面，简单说就是那些与业务无关，却将业务模块所共同调用的逻辑或责任封装起来，便于减少系统的重复代码，降低模块之间的耦合度，并有利于未来的可操作性和可维护性。

#### 12.2 AOP 开发术语

* 连接点（`Joinpoint`）：连接点是程序类中客观存在的方法，可被 `Spring` 拦截并切入内容
* 切入点（`Pointcut`）：被 `Spring` 切入连接点
* 通知、增强（`Active`）：可以为切入点添加额外功能，分为：前置通知、后置通知、异常通知、环绕通知等
* 目标对象（`Target`）：代理的目标对象
* 引介（`Introduction`）：一种特殊的增强，可以在运行期为类动态添加 `Field` 和 `Method`
* 织入（`Weaving`）：被 `AOP` 织入通知后，产生的结果类
* 切面（`Aspect`）：由切点和通知组成，将横切逻辑织入切面所指定的连接点中

#### 12.3 作用

`Spring` 的 `AOP` 编程即是通过动态代理类为原始类的方法添加辅助功能

#### 12.4 环境搭建

引入 `AOP` 相关依赖

```xml
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-aspects</artifactId>
    <version>5.2.9.RELEASE</version>
</dependency>
```

`spring-context.xml` 引入 `AOP` 命名空间：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/aop
                           http://www.springframework.org/schema/aop/spring-aop.xsd">
  
</beans>
```

#### 12.5 开发流程

##### 定义原始类

```java
public class UserServiceImpl implements UserService {
    @Override
    public void printInfo() {
        System.out.println("UserServiceImpl printInfo method");
    }

    @Override
    public List<User> queryUsers() {
//        System.out.println("事务控制");
//        System.out.println("日志打印");
        System.out.println("queryUsers");
        return new ArrayList<>();
    }

    @Override
    public Integer updateUser() {
//        System.out.println("事务控制");
//        System.out.println("日志打印");
        System.out.println("updateUser");
        return 1;
    }

    @Override
    public Integer saveUser() {
//        System.out.println("事务控制");
//        System.out.println("日志打印");
        System.out.println("saveUser");
        return 1;
    }

    @Override
    public Integer deleteUser() {
//        System.out.println("事务控制");
//        System.out.println("日志打印");
        System.out.println("deleteUser");
        return 1;
    }
}
```

##### 定义通知类（添加额外功能）

```java
public class MyAdvice implements MethodBeforeAdvice { // 实现前置通知接口
    @Override
    public void before(Method method, Object[] objects, Object o) throws Throwable {
        System.out.println("事务控制");
        System.out.println("日志打印");
    }
}
```

##### 定义 bean 标签

```xml
<bean id="userService" class="com.ch.wchya.springprimary.service.UserServiceImpl"></bean>
<bean id="before" class="com.ch.wchya.springprimary.aop.MyAdvice"/>
```

##### 定义切入点（PointCut）

```xml
<!--定义切入点-->
<aop:config>
    <!--切入点 修饰符 返回值 包，类 方法名 参数表-->
    <aop:pointcut id="pc_before" expression="execution(* queryUsers())"/>
</aop:config>
```

##### 形成切面（Aspect）

```xml
<!--定义切入点-->
<aop:config>
    <!--组装-->
    <aop:advisor advice-ref="before" pointcut-ref="pc_before"/>
</aop:config>
```

#### 12.6 AOP 小结

* 通过 `AOP` 提供的编码流程，更便利的定制切面，更方便的定制了动态代理
* 进而彻底解决了辅助功能冗余的问题
* 业务类中职责单一性得到更好保障
* 辅助功能也有很好的复用性

#### 12.7 通知类【可选】

定义通知类，达到通知效果

* 前置通知：`MethodBeforeAdvice`
* 后置通知：`AfterAdvice`
* 后置通知：`AfterReturningAdvice`（有异常不执行，方法会因异常而结束，无返回值）
* 异常通知：`ThrowsAdvice`
* 环绕通知：`MethodInterceptor`

```java
// 前置通知
public class MyBeforeAdvice implements MethodBeforeAdvice { // 实现前置通知接口
    @Override
    public void before(Method method, Object[] objects, Object o) throws Throwable {
        System.out.println("事务控制");
        System.out.println("日志打印");
    }
}
// 后置通知
public class MyAfterAdvice implements AfterReturningAdvice {
    @Override
    public void afterReturning(Object o, Method method, Object[] objects, Object o1) throws Throwable {
        System.out.println("AfterReturningAdvice");
    }
}
// 异常通知（后置）
public class MyThrowsAdvice implements ThrowsAdvice { // 在核心中抛出异常时执行
    public void afterThrowing(Exception ex) {
        System.out.println("After Throwing");
    }
}
// 环绕通知
public class MyInterceptorAdvice implements MethodInterceptor {
    @Override
    public Object invoke(MethodInvocation methodInvocation) throws Throwable {
        System.out.println("环绕 开始");
        Object ret = methodInvocation.proceed(); // 触发，执行核心功能
        System.out.println("环绕 结束");
        return ret;
    }
}
```

```xml
<!--通知，额外功能-->
<bean id="before" class="com.ch.wchya.springprimary.aop.MyBeforeAdvice"/>
<bean id="after" class="com.ch.wchya.springprimary.aop.MyAfterAdvice"/>
<bean id="throws" class="com.ch.wchya.springprimary.aop.MyThrowsAdvice"/>
<bean id="interceptor" class="com.ch.wchya.springprimary.aop.MyInterceptorAdvice"/>

<!--定义切入点-->
<aop:config>
    <!--切入点 修饰符 返回值 包，类 方法名 参数表-->
    <aop:pointcut id="pc_before" expression="execution(* queryUsers())"/>
    <aop:pointcut id="pc_after" expression="execution(* deleteUser())"/>
    <aop:pointcut id="pc_throws" expression="execution(* updateUser())"/>
    <aop:pointcut id="pc_interceptor" expression="execution(* saveUser())"/>
    <!--组装-->
    <aop:advisor advice-ref="before" pointcut-ref="pc_before"/>
    <aop:advisor advice-ref="after" pointcut-ref="pc_after"/>
    <aop:advisor advice-ref="throws" pointcut-ref="pc_throws"/>
    <aop:advisor advice-ref="interceptor" pointcut-ref="pc_interceptor"/>
</aop:config>
```

#### 12.8 通配切入点

根据表达式通配切入点：

```xml
<!--匹配参数-->
<aop:pointcut id="myPointCut" expression="execution(* *(com.ch.wchya.springprimary.aop.User))" />
<!--匹配方法名（无参）-->
<aop:pointcut id="myPointCut" expression="execution(* save())" />
<!--匹配方法名（任意参数）-->
<aop:pointcut id="myPointCut" expression="execution(* save(..))" />
<!--匹配返回值类型-->
<aop:pointcut id="myPointCut" expression="execution(com.ch.wchya.springprimary.aop.User *(..))" />
<!--匹配类名-->
<aop:pointcut id="myPointCut" expression="execution(* com.ch.wchya.springprimary.aop.UserServiceImpl.*(..))" />
<!--匹配包名-->
<aop:pointcut id="myPointCut" expression="execution(* com.ch.wchya.springprimary.*.*(..))" />
<!--匹配包名，以及子包名-->
<aop:pointcut id="myPointCut" expression="execution(* com.ch.wchya.springprimary.aop..*.*(..))" />
```

#### 12.9 JDK 和 CGLib 选择

`Spring` 底层，包含 了 `jdk` 代理和 `cglib` 代理两种动态代理机制，选择的基本规则是：目标业务类如果有接口则用 `JDK` 代理，没有接口则用 `CGLib` 代理

```java
class DefaultAopProxyFactory {
  // 该方法中明确定义了 JDK 代理和 CGLib 代理的选取规则
  // 基本规则是：目标业务类如果有接口则用 JDK 代理，没有接口则用 CGLib 代理
  public AopProxy createAopProxy() {...}
}
```

#### 12.10 后处理器

`spring` 中定义了很多后处理器。后处理器：每个 `bean` 在创建完成之前，都会有一个后处理过程，即再加工，对 `bean` 做出相关改变和调整。

`spring-AOP` 中，就有一个专门的后处理器，负责通过原始业务组件（`Service`），再加工得到一个代理组件

[![glAqDU.md.png](https://z3.ax1x.com/2021/05/06/glAqDU.md.png)](https://imgtu.com/i/glAqDU)

##### bean 生命周期

`构造 》注入属性 满足依赖 》后处理器前置过程 》初始化 》后处理器后置过程 》返回 》销毁`

### 13. Spring+MyBatis【重点】

#### 13.1 配置数据库

将数据源配置到项目中

##### 引入 jdbc.properties 配置文件

```properties
driverClassName=com.mysql.cj.jdbc.Driver
url=jdbc:mysql://localhost:3306/employees?useUnicode=true&characterEncoding=utf-8
username=xxxx
password=xxxx
```

##### 整合 spring 配置文件和 properties 配置文件

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/context
                           http://www.springframework.org/schema/context/spring-context.xsd"
>

    <!--配置文件参数化（参数点位符）-->
    <context:property-placeholder location="classpath:jdbc.properties"/>

    <!--与PooledDataSource集成（二选一）-->
    <bean id="dataSource2" class="org.apache.ibatis.datasource.pooled.PooledDataSourceFactory">
        <property name="driver" value="${driverClassName}"/>
        <property name="url" value="${url}"/>
        <property name="username" value="${username}"/>
        <property name="password" value="${password}"/>
    </bean>

    <!--与DruidDataSource集成（二选一）-->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSourceFactory" init-method="init" destroy-method="close">
        <!--基本配置-->
        <property name="driverClassName" value="${driverClassName}"/>
        <property name="url" value="${url}"/>
        <property name="username" value="${username}"/>
        <property name="password" value="${password}"/>
    </bean>

</beans>
```

##### Druid 连接池可选参数

```xml
<!--与DruidDataSource集成（二选一）-->
<bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSourceFactory" init-method="init" destroy-method="close">
    <!--基本配置-->
    <property name="driverClassName" value="${driverClassName}"/>
    <property name="url" value="${url}"/>
    <property name="username" value="${username}"/>
    <property name="password" value="${password}"/>

    <!--配置初始化大小、最小、最大-->
    <property name="initalSize" value="${initialSize}"/>
    <property name="minIdle" value="${minIdle}"/>
    <property name="maxActive" value="${maxActive}"/>
    <property name="maxWait" value="${maxWait}"/>

    <!--配置间隔多久才进行一次检测，检测需要关闭的空闲连接，单位是毫秒-->
    <property name="timeBetweenEvictionRunsMillis" value="60000"/>

    <!--配置一个连接在池中最小生存的时间，单位是毫秒-->
    <property name="minEvictableIdleTimeMillis" value="300000"/>
</bean>
```

##### Druid 监控中心



##### 测试监控中心

配置 `tomcat`，并访问：`protocol://ip:port/project/druid/index.html`

#### 13.2 整合 MyBatis

将 `SqlSessionFactory、Dao、Service` 配置到项目中

##### 导入依赖

```xml
<!--spring-jdbc-->
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-jdbc</artifactId>
    <version>5.2.9.RELEASE</version>
</dependency>
<!--spring+mybatis集成依赖-->
<dependency>
    <groupId>org.mybatis</groupId>
    <artifactId>mybatis-spring</artifactId>
    <version>1.3.1</version>
</dependency>
```

##### 配置 SqlSessionFactory

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/context
                           http://www.springframework.org/schema/context/spring-context.xsd"
>

    <!--配置文件参数化（参数点位符）-->
    <context:property-placeholder location="classpath:jdbc.properties"/>

    <!--与PooledDataSource集成（二选一）-->
    <bean id="dataSource2" class="org.apache.ibatis.datasource.pooled.PooledDataSource">
        <property name="driver" value="${driverClassName}"/>
        <property name="url" value="${url}"/>
        <property name="username" value="${username}"/>
        <property name="password" value="${password}"/>
    </bean>

    <!--与DruidDataSource集成（二选一）-->
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" init-method="init" destroy-method="close">
        <!--基本配置-->
        <property name="driverClassName" value="${driverClassName}"/>
        <property name="url" value="${url}"/>
        <property name="username" value="${username}"/>
        <property name="password" value="${password}"/>

        <!--配置初始化大小、最小、最大-->
        <property name="initialSize" value="${initialSize}"/>
        <property name="minIdle" value="${minIdle}"/>
        <property name="maxActive" value="${maxActive}"/>
        <property name="maxWait" value="${maxWait}"/>

        <!--配置间隔多久才进行一次检测，检测需要关闭的空闲连接，单位是毫秒-->
        <property name="timeBetweenEvictionRunsMillis" value="60000"/>

        <!--配置一个连接在池中最小生存的时间，单位是毫秒-->
        <property name="minEvictableIdleTimeMillis" value="300000"/>
    </bean>

    <!--工厂bean：生成SqlSessionFactory-->
    <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
        <!--注入连接池-->
        <property name="dataSource" ref="dataSource"/>
        <!--注入dao-mapper文件信息，如果映射文件和dao接口 同包且同名，则此配置可省略-->
        <property name="mapperLocations">
            <list>
                <value>classpath:com/ch/wchya/springprimary/dao/*.xml</value>
            </list>
        </property>
        <!--为 dao-mapper文件中的实体 定义缺少包路径。如：<select id="queryAll" resultType="User"> 中 User类可以不定义包-->
        <property name="typeAliasesPackage" value="com.ch.wchya.entity.springprimary"/>
        <!--配置mybatis使用log4j打印-->
        <property name="configuration">
            <bean class="org.apache.ibatis.session.Configuration">
                <property name="logImpl" value="org.apache.ibatis.logging.stdout.StdOutImpl"/>
            </bean>
        </property>
    </bean>

</beans>
```

##### 配置 MapperScannerConfigurer

管理 `Dao` 实现类的创建，并创建 `Dao` 对象，存入工厂管理：

* 扫描所有 `Dao` 接口，去构建 `Dao` 实现
* 将 `Dao` 实现存入工厂管理
* `Dao` 实现对象在工厂中的 `id` 是：**首字母小宝的接口的类名**，例如：`UserDao=>userDao, OrderDao=>orderDao`

```xml
<bean id="mapperScannerConfigurer" class="org.mybatis.spring.mapper.MapperScannerConfigurer">
    <!-- 到接口所在的包，如果有多个包，可以用逗号或分号分隔
    <property name="basePackage" value="com.ch.wchya.springprimary.dao,com.ch.wchya.springprimary.entity"/>
    -->
    <property name="basePackage" value="com.ch.wchya.springprimary.dao"/>

    <!--如果工厂中只有一个SqlSessionFactory的bean，此配置可省略-->
    <property name="sqlSessionFactoryBeanName" value="sqlSessionFactory"/>
</bean>
```

##### 配置 Service

```xml
<bean id="userService" class="com.ch.wchya.springprimary.service.UserServiceImpl">
    <!--注意：这里引用的userDao已经通过上面的mapperScannerConfigurer自动生成了，按照生成的规则，所以这里引用的名字是：userDao-->
    <property name="userDao" ref="userDao"/>
</bean>
```

### 14. 事务【重点】

#### 14.1 配置 DataSourceTransactionManager

事务管理器，其中持有 `DataSource`，可以控制事务功能（`commit,rollback` 等）

```xml
<!--引入一个事务管理器，其中依赖 DataSource，借以获得连接，进而控制事务逻辑-->
<bean id="tx" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
  <property name="dataSource" ref="dataSource"/>
</bean>
```

> 注意：DataSourceTransactionManager 和 SqlSessionFactoryBean 要注入同一个 DataSource 的 Bean，否则事务控制失败

#### 14.2 配置事务通知

基于事务管理器，进一步定制，生成一个额外功能：`Advice`

此 `Advice` 可以切入任何需要事务的方法，通过事务管理器为方法控制事务

#### 14.3 事务属性

##### 隔离级别

`isolation`：隔离级别

* `default`：默认值，采用数据库的默认设置【建议】
* `read-uncommited`：读未提交
* `read-commited`：读提交（`Oracle` 数据库默认的隔离级别）
* `repeatable-read`：可重复读（`MySQL` 数据库默认的隔离级别）
* `serialized-read`：序列化读

隔离级别由低到高为：

`read-uncommited < read-commited < repeatable-read < serialized-read`

**安全性：**级别越高，多事务并发时，越安全，因为共享的数据越来越少，事务间彼此干扰减少

**并发性：**级别越高，多事务并发时，迸发越差，因为共享的数据越来越少，事务间阻塞情况增多

事务并发时的安全问题：

* 脏读：一个事务读取到另一个事务还未提交的数据
  * 大于等于 `read-commited` 可防止
* 不可重复读：一个事务内多次读取一行数据的相同内容，其结果不一致
  * 大于等于 `repeatable-read` 可防止
* 幻影读：一个事务内多次读取一张表中的相同内容，其结果不一致
  * `serialized-read` 可防止

##### 传播行为

`propagation`：传播行为

当涉及到事务嵌套（`Service` 调用 `Service`）中，可能会存在问题

* `SUPPORTS`：不存在外部事务，则不开启新事务；存在外部事务，则合并到外部事务中（适合查询）
* `REQUIRED`：不存在外部事务，则开启新事务；存在外部事务，则合并到外部事务中（默认值，适合增删改）

##### 读写性

`readonly`：读写性

* `true`：只读，可提高查询效率（适合查询）
* `false`：可读可写（默认值，适合增删改）

##### 事务超时

`timeout`：事务超时时间

当前事务所需操作的数据被其它事务占用，则等待：

* 100：自定义等待时间 100 （秒）
* -1：由数据库指定等待时间，默认值（建议）

##### 事务回滚

`rollback-for`：回滚属性

* 如果事务中抛出 `RuntimeException`，则自动回滚
* 如果事务中抛出 `CheckException` 运行时异常，不会自动回滚，而是默认提交事务
* 处理方案：将 `CheckException` 转换成 `RuntimeException` 上抛，或设置 `rollback-for="Exception"`

```xml
<tx:advice id="txManager" transaction-manager="tx">
    <!--事务属性-->
    <tx:attributes>
        <tx:method name="queryUsers" propagation="SUPPORTS"/>
        <!--以User结尾的方法，切入此方法时，采用对应事务实行-->
        <tx:method name="*User"/>
        <!--剩余所有方法-->
        <tx:method name="*"/>
    </tx:attributes>
</tx:advice>
```

#### 14.4 编织

将事务管理的 `Advice` 切入需要事务的业务方法中

```xml
<aop:config>
  <aop:pointcut expression="execution(* com.ch.wchya.springprimary.service.UserServiceImpl.*(..))" id="pc"/>
  <!--组织切面-->
  <aop:advisor advice-ref="txManager" pointcut-ref="pc"/>
</aop:config>
```

### 15. 注解开发

#### 15.1 声明 bean

用于替换自建类型组件的 `<bean...>` 标签，可以更快速的声明 `bean`：

* `@Service`：业务类专用
* `@Repository`：`dao` 实现类专用
* `@Controller`：`web` 层专用
* `@Component`：通用
* `@Scope`：用户控制 `bean` 的创建模式

```java
// @Service 说明此类是一个业务类，需要将此类纳入工厂，等价替换掉 <bean class="xxx.UserServiceImpl"/>
// @Service 默认 beanId=首字母小写的类名，即 userServiceImpl
// @Service("userService") 自定义 beanId 为 userService
@Service	// 声明 bean，且 id="userServiceImpl"
@Scope("singleton")	// 声明创建模式，默认为单例模式；@Scope("prototype") 即可设置为多例模式
public class UserServiceImpl implements UserService {
  ...
}
```

#### 15.2 注入（DI）

用于完成 `bean` 中属性值的注入

* `@Autowired`：基于类型自动注入
* `@Resource`：基于名称自动注入
* `@Qualifier("userDao")`：限定要自动注入的 `bean` 的 `id`，一般和 `@Autowired` 联用
* `@value`：注入简单类型数据（`jdk 8种基本数据类型 + String`）

```java
@Service
public class UserServiceImpl implements UserService {
    @Autowired	// 注入类型为 UserDao 的 bean
    @Qualifier("userDao")	// 如果有多个类型为 userDao 的 bean，可以用此注解从中挑选一个
    private UserDao userDao;
}

public class XX {
  	@Value("100")	//注入数字
  	private Integer id;
  	@Value("shine")	//注入String
	  private String name;
}
```

#### 15.3 事务控制

用于控制事务切入：`@Transactional`，工厂配置中的 `<tx:advice...` 和 `<aop:config...` 可以省略

```java
// 类中的每个方法都切入事务（有自己的事务控制的方法除外）
@Transaction(isolation=Isolation.READ_COMMITTED,propagation=Propagation.REQUIRED,readOnly=false,rollbackFor=Exception.class,timeout=-1)
public class UserServiceImpl implements UserService {
  	...
    // 该方法自己的事务控制，仅对此方法有效
    @Transactional(propagation=Propagation.SUPPORTS)
    public List<User> queryAll() {
    	return userDao.queryAll();
  	}
  	public void save(User user) {
      userDao.save(user);
    }
}
```

#### 15.4 注解所需配置

```xml
<!--告知spring，哪些包中，有被注解的类、方法、属性-->
<context:component-scan base-package="com.ch.wchya"></context:component-scan>

<!--告知spring，@Transactional在定制事务时，基于txManager=DataSourceTransactionManager-->
<tx:annotation-driven transaction-manager="tx"/>
```

#### 15.5 AOP 开发

##### 注解使用

```java
@Aspect // 声明此类是一个切面类：会包含切入点（pointcut）和通知（advice）
@Component  // 声明组件，进入工厂
public class MyAspect {
    // 定义切入点
    @Pointcut("execution(* com.ch.wchya.springprimary.service.UserServiceImpl.*(..))")
    public void pc() {}

    @Before("pc()")
    public void mybefore(JoinPoint a) {
        System.out.println("target:" + a.getTarget());
        System.out.println("args:"+ a.getArgs());
        System.out.println("method's name:" + a.getSignature().getName());
        System.out.println("before...");
    }

    @AfterReturning(value = "pc()", returning = "ret") // 后置通知
    public void myAfterReturing(JoinPoint a, Object ret) {
        System.out.println("after~~~~:" + ret);
    }

    @Around("pc()") // 环绕通知
    public Object myInterceptor(ProceedingJoinPoint p) throws Throwable {
        System.out.println("Interceptor1~~~~");
        Object ret = p.proceed();
        System.out.println("Interceptor2~~~~");
        return ret;
    }

    @AfterThrowing(value = "pc()", throwing = "ex") // 异常通知
    public void myThrow(JoinPoint jp, Exception ex) {
        System.out.println("throws");
        System.out.println("===" + ex.getMessage());
    }
}
```

##### 配置

```xml
<!--添加如下配置，启用aop注解-->
<aop:aspectj-autoproxy></aop:aspectj-autoproxy>
```

### 16. 集成 JUnit

#### 16.1 导入依赖

```xml
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-test</artifactId>
    <version>5.2.9.RELEASE</version>
</dependency>
<dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.12</version>
</dependency>
```

#### 16.2 编码

* 可以免去工厂的创建过程
* 可以直接将要测试的组件注入到测试类

```java
// 测试启动，会启动spring工厂，并且当前测试类也会被工厂生产
@RunWith(SpringJUnit4ClassRunner.class) // 由SpringJUnit4ClassRunner启动测试
@ContextConfiguration("classpath:applicationContext.xml")   // spring的配置文件位置
public class TestSpringTest {

    @Autowired  // 注入要测试的组件
    private UserService userService;

    @Test
    public void testUserService() {
        List<SimpleUser> simpleUsers = userService.queryUsers();
        simpleUsers.forEach(System.out::println);
    }
}
```

## 第三十三章 SpringMVC

### 1. 概述

#### 1.1 引言

* 它是一个 `java` 开源的框架，是 `Spring Framework` 的一个独立模块
* 这是一个 `MVC` 框架，在项目中开辟了 `MVC` 层次架构
* 它对控制器中的功能进行了包装、简化、扩展，践行了工厂模式，它所有的功能都架构在工厂之上

#### 1.2 MVC 架构

`MVC：Model View Controller`，即：模型、视图、控制器：

* 模型：即业务模型，负责完成业务中的数据通信处理，对应项目中的 `service` 和 `dao`
* 视图：渲染数据，生成页面，对应项目中的 `JSP`
* 控制器：直接对接请求，控制 `MVC` 流程，高度模型，选择视图，对应项目中的 `Servlet`

`MVC` 是现下软件开发中的最流行的代码结构形态。人们根据负责的不同逻辑，将项目中的代码分成 `MVC` 3个层次。层次的内部职责单一，层次之间耦合度低。符合低耦合、高内聚的设计理念，也实际有际于项目的长期维护

### 2. 开发流程

#### 2.1 导入依赖

```xml
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-webmvc</artifactId>
    <version>5.2.9.RELEASE</version>
</dependency>
```

#### 2.2 配置核心（前端）控制器

作为一个 `MVC` 框架，首先要解决的是：如何能够收到请求！

**所以 MVC 框架大都会设计一款前端控制器，选型是 Servlet 或 Filter ，在框架最前沿率先工作，接收所有请求**

此控制器在接收到请求后，还会负责 `springMVC` 的核心的高度管理，所以既是前端又是核心

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">

    <!--springmvc 前端控制器-->
    <servlet>
        <servlet-name>mvc</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>

        <!--懒汉/饿汉 加载-->
        <load-on-startup>1</load-on-startup>
    </servlet>
    <servlet-mapping>
        <servlet-name>mvc</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>
</web-app>
```

#### 2.3 后端控制器

等价于之前定义的 `Servlet`

```java
@Controller
@RequestMapping("/hello")
public class HelloWorldController {

    @RequestMapping("/test1")
    public String hello() {
        System.out.println("/hello/test1");
        return null;
    }
}
```

#### 2.4 配置文件

默认名称：`核心控制器-servlet.xml`，默认位置：`WEB-INF/`

该名称可以随意起，比如：`mvc.xml`，存放位置也可以随意，如：`resources/`，但需要配置在核心控制器中

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           https://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/context
                           https://www.springframework.org/schema/context/spring-context.xsd
                           http://www.springframework.org/schema/mvc
                           https://www.springframework.org/schema/mvc/spring-mvc.xsd"
>

    <!--注解扫描-->
    <context:component-scan base-package="com.ch.wchya.springwebmvc.controller"/>

    <!--注解驱动-->
    <mvc:annotation-driven/>

    <!--视图解析器
            作用：1. 捕获后端控制器的返回值，=>    hello
                 2. 解析：在返回值的前后进行拼接 =>   /hello.jsp
    -->
    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <!--前缀-->
        <property name="prefix" value="/"/>
        <!--后缀-->
        <property name="suffix" value=".jsp"/>
    </bean>

</beans>
```

#### 2.5 访问

```
http://localhost:8081/hello/test1
```

### 3. 接收请求参数

通过控制器中方法的形参，接收请求参数

#### 3.1 基本类型参数

**要求：请求参数和方法的形参同名即可**

`springMVC` 默认可以识别的日期字符串格式为：`YYYY/MM/dd HH:mm:ss`，通过 `@DateTimeformat` 可以修改默认日期格式

```java
// 访问地址：http://localhost:8081/.../test1?id=1&name=zzz&gender=false&birth=2018-12-12 12:20:30
@RequestMapping("/test1")
public String testParam1(Integer id,
                         String name,
                         Boolean gender,
                         @DateTimeFormat(pattern="yyyy-MM-dd HH:mm:ss") Date birth) {
  System.out.println("test param1");
  return "index";
}
```

#### 3.2 实体收参【建议】

**要求：请求参数和对象实体的字段名称相同即可**

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>演示参数传递</title>
</head>
<body>
    <form action="${pageContext.request.contextPath}/param/test1">
        <label for="id">主键：</label><input type="text" id="id" name="id"><br>
        <label for="name">姓名：</label><input type="text" id="name" name="name"><br>
        <label>性别：</label><input type="radio" name="gender" value="true">男 <input type="radio" name="gender" value="false">女<br>
        <label for="birth">生日：</label><input type="text" id="birth" name="birth"><br>
        <label>爱好：</label><input type="checkbox" value="足球" name="hobby">足球 <input type="checkbox" value="篮球" name="hobby">篮球
        <input type="checkbox" value="排球" name="hobby">排球<br>
        <input type="submit" value="提交"><input type="reset" value="重置">
    </form>
</body>
</html>
```

```java
@Data
public class User {
    private Integer id;
    private String name;
    private boolean gender;
    private Date birth;
    private String[] hobby;
}
@Controller
@RequestMapping("/param")
public class ParamController {

    @RequestMapping
    public String index() {
        return "param";
    }

    @RequestMapping("/test1")
    public String test1(User user) {
        System.out.println(user);
        return "hello";
    }
}
```

```shell
# 控制台打印的结果如下：
User(id=23, name=囧扥, gender=true, birth=Wed Dec 12 12:12:12 CST 2012, hobby=[篮球, 排球])
```

#### 3.3 数组收参

传递参数时，多个键值对的键相同，值不同，就可以形成数组参数，详情参见上个示例

#### 3.4 集合收参【了解】

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>集合收参</title>
</head>
<body>
    <form action="${pageContext.request.contextPath}/param/test2">
        <div><label for="id">主键：</label><input type="text" id="id" name="users[0].id"></div>
        <div><label for="name">姓名：</label><input type="text" id="name" name="users[0].name"></div>
        <div><label for="gender">性别：</label><input type="text" id="gender" name="users[0].gender"></div>
        <hr>
        <div><label for="id1">主键：</label><input type="text" id="id1" name="users[1].id"></div>
        <div><label for="name1">姓名：</label><input type="text" id="name1" name="users[1].name"></div>
        <div><label for="gender1">性别：</label><input type="text" id="gender1" name="users[1].gender"></div>
        <hr>
        <div><input type="submit" value="提交"><input type="reset" value="重置"></div>
    </form>
</body>
</html>
```

```java
@Data
public class UserList {
    private List<User> users;
}
@Controller
@RequestMapping("/param")
public class ParamController {

    @RequestMapping("/collection")
    public String collection() {
        return "param_collection";
    }

    @RequestMapping("/test2")
    public String test2(UserList users) {
        users.getUsers().forEach(System.out::println);
        return "hello";
    }
}
```

```shell
# 控制台打印的结果如下：
User(id=11, name=adf, gender=true, birth=null, hobby=null)
User(id=22, name=顶起, gender=false, birth=null, hobby=null)
```

#### 3.5 路径参数

```java
// {id} 定义名为id的路径；/hello/{id} 的匹配能力和 /hello/* 等价
// http://.../hello/10	{id} 匹配到10
// http://.../hello/200	{id} 匹配到200
@RequestMapping("/hello/{id}")
// @PathVariable 将 {id}路径匹配到值赋给 id 参数
// 路径名和参数名相同则 @PathVariable("id") 可简写为 @PathVariable
public String testParam5(@PathVariable("id") Integer id) {
  System.out.println("id:" + id);
  return "hello";
}

// http://.../hello/tom		{username}匹配到tom
// http://.../hello/jack	{username}匹配到jack
@RequestMapping("/hello/{username}")
public String testParam6(@PathVariable("username") String name) {
  System.out.println("username:" + name);
  return "hello";
}
```

#### 3.6 中文乱码

首先，页面中字符集统一

```java
jsp：<%@page pageEncoding="utf-8" %>
html：<meta charset="UTF-8">
```

其次，`tomcat` 中字符集设置，对 `get` 请求中，中文参数乱码有效【[参见7.1 get请求收参问题]()】

`Tomcat 配置：URIEncoding=utf-8`

最后，设置下面的 `filter`，对 `post` 请求中，中文参数乱码有效

```xml
<!--此过滤器会进行：request.setCharactorEncoding("utf-8");的操作-->
<filter>
  <filter-name>encoding</filter-name>
  <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
  <init-param>
    <param-name>encoding</param-name>
    <param-value>utf-8</param-name>
  </init-param>
<filter-mapping>
  <filter-name>encoding</filter-name>
  <url-pattern>/*</url-pattern>
</filter-mapping>
```

### 4. 跳转

跳转关键字：`forward:    redirect:`

**forward:** 是一个关键字，`InternalResourceViewResolver`  的父类 `UrlBasedViewResolver` 中有定义，当发现有这个关键字时，就知道该关键字后面跟着的是一个绝对地址，在 `mvc.xml` 中配置的视图解析器就不再起作用，不再拼接前缀、后缀

#### 4.1 转发

```java
@Controller
@RequestMapping("/jump")
public class JumpController {

    @RequestMapping("/test1")
    public String test1() {
        System.out.println("test1");
        return "forward:/hello.jsp";
    }

    @RequestMapping("/test2")
    public String test2() {
        System.out.println("test2");
        // 因为在一个类中，所以下面的语句等价于：return "forward:test1"; // 相对路径;
        return "forward:/jump/test1"; // 绝对路径
    }
}
```

#### 4.2 重定向

```java
@Controller
@RequestMapping("/jump")
public class JumpController {

    @RequestMapping("/test3")
    public String test3() {
        System.out.println("test3");
        return "redirect:/hello.jsp";
    }

    @RequestMapping("/test4")
    public String test4() {
        System.out.println("test4");
        // 因为在一个类中，所以下面的语句等价于：return "redirect:test3";  // 相对路径
        return "redirect:/jump/test3";  // 绝对路径
    }
}
```

#### 4.3 跳转细节

* 在增删改之后，为了防止请求重复提交，重定向跳转
* 在查询之后，可以做转发跳转

### 5. 传值

`C` 得到数据后，跳转到 `V`，并向 `V` 传递数据，进而 `V` 中可以渲染数据，让用户看到含有数据的页面

**转发跳转：Request 作用域**

**重定向跳转：Sessioni 作用域**

#### 5.1 Request 和 Session

```java
// 形参中，即可获得 request 和 session 对象
@RequestMapping("/test1")
public String testData(HttpSession session, HttpServletRequest req, Integer id) {
  session.setAttribute("user", new User());
  req.setAttribute("user", new User());
  req.setAttribute("age", 18);
  req.setAttribute("users", Arrays.asList(new User(), new User()));
  // return "test2";
  return "forward:/WEB-INF/test2.jsp";
}
```

#### 5.2 JSP 中取值

> 建议：重点复习 EL、JSTL 语法

```jsp
${sessionScope.user.name}
${requestScope.age}
```

#### 5.3 Model

```java
// model 中的数据，会在 View 渲染之前，将数据复制一份给 request
@RequestMapping("/test")
public String testData(Model model) {
  model.addAttribute("name", "张三");
  return "index";
}
```

#### 5.4 ModelAndView

```java
// modelandview 可以集中管理 view 和 data
@RequestMapping("/test")
public ModelAndView testData() {
  // 新建 ModelAndView 对象
  ModelAndView mav = new ModelAndView();
  // 设置视图名，即如何跳转
  mav.setViewName("forward:/index.jsp");
  // 增加数据
  mav.addObject("age", 10);
  return mav;
}
```

#### 5.5 @SessionAttributes

该注解在类上添加。

* `@SessionAttributes({"gender", "name"})` ，配置了这个以后，再使用 `model` 添加同名的属性值时，就会存入 `session` 中
* `SessionStatus`，用于移除 `session` 中使用 `model` 添加的值

```java
@Controller
@RequestMapping("/data")
@SessionAttributes(value = {"city", "street"})
public class DataController {

    @RequestMapping("/test2")
    public String test2(Model model) {
        model.addAttribute("country", "中国");
        model.addAttribute("city", "兰州");
        model.addAttribute("street", "雁南路");
        return "data2";
    }

    @RequestMapping("/test3")
    public String test3(SessionStatus status) {
        // 清空所有通过 model 存入 session 的数据
        status.setComplete();
        return "data2";
    }
}
```

### 6. 静态资源

静态资源有：`html、js文件、css文件、图片文件`。静态文件没有 `url-pattern`，所以默认是访问不到的。之所以在网站中可以访问，是因为，`tomcat` 中有一个全局的 `servlet`：`org.apache.catalina.servlets.DefaultServlet`，它的 `url-pattern` 是 `/`，是全局默认的 `servlet`，所以每个项目中不能匹配的静态资源的请求，由这个 `servlet` 来处理即可。

但是，在 `springmvc` 中的 `DispatcherServlet` 也采用了 `/` 作为 `url-pattern` ，所以项目中不会再使用全局的 `servlet`，则静态资源不能完成访问

#### 6.1 解决方案1

`DispatcherServlet` 采用其它的 `url-pattern`，如下所示，但是此时，所有访问 `handler` 的路径都要以 `action` 结尾了

```xml
<servlet>
  <servlet-name>mvc9</servlet-name>
  <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
</servlet>
<servlet-mapping>
  <servlet-name>mvc9</servlet>
  <url-pattern>*.action</url-pattern>
</servlet-mapping>
```

#### 6.2 解决方案2

`DispatcherServlet` 的 `url-pattern` 依然采用 `/`，但追加配置

```xml
<!--
        额外的增加一个 handler，且其 requestMapping：/**，可以匹配所有请求，但是优先级最低。
        所以，如果其它所有的 handler 都匹配不上，请求会转身 /**。恰好，这个 handler 就是处理静态资源的处理方式：
        将请求转发到 tomcat 中名为 default 的 servlet
        RequestMapping  /*  可以匹配到的路径有：/a,/b,/c,...，不能匹配：/a/b,/a/b/c,...
                        /** 可以匹配任意路径
        下面配置的 handler 做的事情：将收到的请求转发到 tomcat 的 default servlet
-->
<mvc:default-servlet-handler/>
```

#### 6.3 解决方案3

```xml
<!--
		1) mapping是访问路径，location是静态资源存放路径
		2) 将 /html/** 中的 /** 匹配到的内容，拼接到 /hhh/ 后
			 http://.../html/a.html	访问 /hhh/a.html
			 http://.../html/page/b.html 访问 /hhh/page/b.html
-->
<mvc:resources mapping="/html/**" location="/hhh/" />
```

### 7. Json 处理

`springmvc` 默认的 `json` 解决方案选择的是 `Jackson`，所以只需要导入 `jackson` 的 `jar`，即可使用

#### 7.1 导入依赖

```xml
<dependency>
    <groupId>com.fasterxml.jackson.core</groupId>
    <artifactId>jackson-databind</artifactId>
    <version>2.11.3</version>
</dependency>
```

#### 7.2 使用 @ResponseBody

```java
@Controller
@RequestMapping("/json")
public class JsonController {

    @RequestMapping("/test1")
    @ResponseBody
    public User test1() {
        System.out.println("/json/test1");
        User user = new User();
        user.setName("测试");
        user.setBirth(new Date());
        return user;
    }

    @RequestMapping("/test2")
    @ResponseBody
    public List<User> test2() {
        System.out.println("/json/test2");
        User user = new User();
        user.setName("测试");
        user.setBirth(new Date());
        User user1 = new User();
        user1.setName("again");
        user1.setHobby(new String[]{"顶起", "加载"});
        return Arrays.asList(user, user1);
    }

    @RequestMapping(value = "/test3", produces = "text/html;charset=utf-8")
    @ResponseBody
    public String test3() { // 直接返回字符串时，springmvc 就不会再使用 jackson 进行转换，也就不会为返回值设置相应的编码，所以需要添加 produces = "text/html;charset=utf-8" 的注解
        System.out.println("/json/test3");
        return "你好";
    }
}
```

#### 7.3 使用 @RestController

如果一个类中的所有方法都需要使用 `@ResponseBody` 注解，就可以把类上的 `@Controller` 注解更换为 `@RestController` 注解，并且在方法上也不需要 `@ResponseBody` 这个注解

#### 7.4 使用 @RequestBody

该注解用于接收 `Json` 参数

> 注意：该注解可以接收的请求类型是：post，不能接收 get 类型的请求

##### 定义 Handler

```java
// 实体类
@Data
public class User {
  private Integer id;
  private String name;
  private Boolean gender;
}
@RequestMapping("/users")
public String addUser(@RequestBody User user) {//@RequestBody 将请求体中的 json 数据转换为 java 对象
  System.out.println("/users");
  System.out.println("Post user:" + user);
  return "index";
}
```

##### Ajax 发送 json

```js
// 原生 ajax
var xhr = new XMLHttpRequest();
xhr.open("post", "${pageContext.request.contextPath}/users?" + new Date().getTime();
xhr.setRequestHeader("content-type", "application/json");//设置请求头
xhr.send('{"id":1, "name": "shine", "gender": "true"}');//传递 json 串

// jQuery 方式
var user = {id: 1, name: "shine", gender: true};
$.ajax({
  url: '${pageContext.request.contextPath}/json/adduser',
  type: 'post',
  data: JSON.stringify(user),
  contentType: 'application/json',
  success: function(res) {
    alert(res);
  }
});
```

#### 7.5 Jackson 常用注解

##### 日期格式化

`@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss")`

```java
// 实体类
@Data
public class User {
  private Integer id;
  private String name;
  @JsonFormat(pattern="yyyy-MM-dd HH:mm:ss", timezone = "GMT+8")
  private Date birth;
}
```

##### 属性名修改

`@JsonProperty("new_name")`

```java
// 实体类
@Data
public class User {
  @JsonProperty("new_id")	// 不再使用原属性名
  private Integer id;
  private String name;
  private Boolean gender;
}

// 输出的 json：{"new_id": xx, "name": "xx"}
```

##### 属性忽略

`@JsonIgnore`

```java
// 实体类
@Data
public class User {
  @JsonIgnore
  private Integer id;
  private String name;
  private Boolean gender;
}
```

##### null 和 empty 属性排除

`Jackson` 默认会输出 `null` 值的属性，如果不需要，可以排除

`@JsonInclude(JsonInclude.Include.NON_NULL)	//null值属性不输出`

`@JsonInclude(JsonInclude.Include.NON_EMPTY)	//empty属性不输出（空串，长度为0的集合，null值）`

```java
// 实体类
@Data
public class User {
  private Integer id;
  @JsonInclude(JsonInclude.Include.NON_NULL)	// 若 name=null，忽略此属性
  private String name;
  @JsonInclude(JsonInclude.Include.NON_EMPTY)
  private List<String> hobby;	// 若hobby长度为0或==null，忽略此属性
}
```

##### 自定义序列化

`@JsonSerialize(using=MySerializer.class)	//使用 MySerializer 输出某属性`

```java
public class User {
  private Integer id;
  private String name;
  @JsonSerialize(using = MySerializer.class)
  private Double salary = 10000.126;	//在输出此属性时，使用 MySerializer 输出
}

// 输出的json：{"id":xx, "name":"xxx", "salary":10000.13}

public class MySerializer extends JsonSerializer<Double> {
  // value 即 Double salary 的值
  @Override
  public void serialize(Double value, JsonGenerator gen, SerializerProvider serializers) throws IOException {
    // 将 Double salary 的值四舍五入
    String number = BigDecimal.valueOf(value).setScale(2, BigDecimal.ROUND_HALF_UP).toString();
    // 输出四舍五入后的值
    gen.writeNumber(number);
  }
}
```

#### 7.6 FastJson

如果不想使用 `Jackson`，则也可以安装其它的 `json` 处理方案，如：`FastJson`

##### 导入依赖

```xml
<dependency>
  <groupId>com.alibaba</groudId>
  <artifactId>fastjson</artifactId>
  <version>1.2.54</vsersion>
</dependency>
```

##### 安装

```xml
<mvc:annotation-driven>
  <!--安装FastJson转换器-->
  <mvc:message-converters>
    <bean class="com.alibaba.fastjson.support.spring.FastJsonHttpMessageConverter">
      <!--声明转换类型：json-->
      <property name="supportedMediaTypes">
        <list>
          <value>application/json</value>
        </list>
      </property>
    </bean>
  </mvc:message-converters>
</mvc:annotation-driven>
```

##### 使用

`@ResponseBody	@RequestBody	@RestController` 使用方法不变

##### 常用注解

* 日期格式化：`@JSONField(format="yyyy/MM/dd")`
* 属性名修改：`@JSONField(name="birth")`
* 忽略属性：`@JSONField(serialize=false)`
* 包含 `null` 值：`@JSONField(serializeFeatures=SerializerFeature.WriteMapNullValue)`，默认会忽略所有 `null` 值，有些注解会输出 `null`
* 自定义序列化：`@JSONField(serializeUsing = MySerializer2.class)`

```java
public class User implements Serializeable {
  @JSONField(serialize = false)
  private Integer id;
  @JSONField(name = "NAME", serialzeFeatures = SerializerFeature.WriteNullStringAsEmpty)
  private String name;
  @JSONField(serializeFeatures = SerializerFeature.WriteMapNullValue)
  private String city;
  @JSONField(format="yyyy/MM/dd")
  private Date birth;
  @JSONField(serializeUsing = MySerializer2.class)
  private Double salary;
}

public class MySerializer2 implements ObjectSerializer {
  @Override
  public void write(JSONSerializer serializer, Object object, Object fieldName, Type fieldType, int features) throws IOException {
    Double value = (Double) object;	// salary属性值
    String text = value + "元";	// 在salary后拼接元
    serializer.write(text);	// 输出拼接后的内容
  }
}

// 创建的对象是：new User(1, null, null, new Date(), 100.5)
// 输出的json是：{"NAME":"", "city":null, "birth":"2020/12/12", "salary": "100.5元"}
```

### 8. 异常解析器

#### 8.1 现有方案，分散处理

`Controller` 中的每个 `Handler` 自己处理异常。

此种处理方案中，异常处理逻辑，分散在各个 `Handler` 中，不利于集中管理

 ```java
 public String xxx() {
   try {
     ...
   } catch(Exception1 e) {
     e.printStackTrace();
     return "redirect:/xx/error1";
   } catch(Exception2 e) {
     e.printStackTrace();
     return "redirect:/xx/error2";
   }
 }
 ```

#### 8.2 异常解析，统一处理

定义一个异常解析器，集中捕获处理所有异常，这样，`Controller` 中的每个 `Handler` 不再自己处理异常，而是直接 `throws` 所有异常。

此种处理方案，在集中管理异常方面，更有优势！

```java
// 自定义异常类
public class MyException1 extends Exception {

    public MyException1(String message) {
        super(message);
    }
}
public class MyException2 extends Exception {

    public MyException2(String message) {
        super(message);
    }
}
// 自定义异常解析器
public class MyExResolver implements HandlerExceptionResolver {
    @Override
    public ModelAndView resolveException(HttpServletRequest httpServletRequest, HttpServletResponse httpServletResponse, Object o, Exception e) {
        ModelAndView mav = new ModelAndView();
        mav.addObject("ex", e.getMessage());
        if (e instanceof MyException1) {
            mav.setViewName("forward:/error1.jsp");
        } else if (e instanceof MyException2) {
            mav.setViewName("forward:/error2.jsp");
        }
        return mav;
    }
}
```

```xml
<!--mvc.xml-->
<!--自定义的异常解析器-->
<bean class="com.ch.wchya.springwebmvc.resolver.MyExResolver"/>
```

```java
// Handler
@Controller
@RequestMapping("/haha")
public class ExController {

    @RequestMapping("/test1")
    public String test1(Integer id) throws MyException1 {
        System.out.println("/ex/test1");
        if (id == 1) {
            throw new MyException1("错误1");
        }
        return "hello";
    }

    @RequestMapping("/test2")
    public String test2(Integer id) throws MyException2 {
        System.out.println("/ex/test2");
        if (id == 1) {
            throw new MyException2("错误2");
        }
        return "hello";
    }
}
```

### 9. 拦截器

作用：抽取 `handler` 中的冗余功能

#### 9.1 定义拦截器

执行顺序：`preHandle--postHandle--afterCompletion`

```java
// 主要逻辑：在 handler 之前执行：抽取 handler 中的冗余代码
public class MyInterceptor implements HandlerInterceptor {

    // 在 handle 之前执行
    @Override
    public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
        HttpSession session = request.getSession();
        if (session.getAttribute("state") != null)
            return true;
        // 中断之前，响应请求
        response.sendRedirect("/login.jsp");
        return false;
    }

    // 在 handle 之后，响应之前执行
    @Override
    public void postHandle(HttpServletRequest request, HttpServletResponse response, Object handler, ModelAndView modelAndView) throws Exception {

    }

    // 在视图渲染完毕之后进行，可以用来做资源的回收
    @Override
    public void afterCompletion(HttpServletRequest request, HttpServletResponse response, Object handler, Exception ex) throws Exception {

    }
}
```

```java
@Controller
@RequestMapping("/inter")
@SessionAttributes("state")
public class InterController {

    @RequestMapping("/login")
    public String login(Model model) {
        model.addAttribute("state", "ok");
        return "index";
    }

    @RequestMapping("/test1")
    public String test1(Model model) {
        System.out.println("/inter/test1");
        return "index";
    }

    @RequestMapping("/test2")
    public String test2(Model model) {
        System.out.println("/inter/test2");
        return "index";
    }
}
```

#### 9.2 配置拦截路径

```xml
<!--拦截器-->
<mvc:interceptors>
    <mvc:interceptor>
        <mvc:mapping path="/inter/test1"/>
        <mvc:mapping path="/inter/test2"/>
        <mvc:mapping path="/inter/test*"/><!--test开头-->
        <mvc:mapping path="/inter/**"/><!--任意多级路径-->
        <mvc:exclude-mapping path="/inter/login"/><!--不拦截此路径-->
        <bean class="com.ch.wchya.springwebmvc.interceptor.MyInterceptor" /><!--拦截器类-->
    </mvc:interceptor>
</mvc:interceptors>
```

### 10. 上传

#### 10.1 导入 jar

```xml
<dependency>
    <groupId>commons-io</groupId>
    <artifactId>commons-io</artifactId>
    <version>2.8.0</version>
</dependency>
<dependency>
    <groupId>commons-fileupload</groupId>
    <artifactId>commons-fileupload</artifactId>
    <version>1.3.3</version>
</dependency>
```

#### 10.2 表单

```html
<form action="${pageContext.request.contextPath}/upload/test1" method="post" enctype="multipart/form-data">
    file: <input type="file" name="source"><br>
    <input type="submit" value="提交">
</form>
```

#### 10.3 上传解析器

```xml
<!--上传解析器，id必须是multipartResolver，要不然springmvc找不到上传解析器-->
<bean id="multipartResolver" class="org.springframework.web.multipart.commons.CommonsMultipartResolver">
    <!--最大可上传文件的大小，单位：byte，超过此大小后会抛出 MaxUploadSizeExceededException异常，可以使用异常解析器捕获-->
    <property name="maxUploadSize" value="1048576"/>
</bean>
```

#### 10.4 Handler

```java
@Controller
@RequestMapping("/upload")
public class UploadController {

    @RequestMapping("/test1")
    public String test1(MultipartFile source, HttpSession session) throws IOException {
        System.out.println("/upload/test1");
        // 获取原始文件名
        String filename = source.getOriginalFilename();
        // 获取上传文件的文件类型
        String contentType = source.getContentType();
        System.out.println(filename);
        System.out.println(contentType);
        // 上传文件根目录的真实路径
        String basePath = session.getServletContext().getRealPath(File.separator + "WEB-INF" + File.separator + "upload");
        // 获取有2、3级目录的存储路径
        String storePath = FileUploadUtil.newFilePath(basePath, filename);
        // 获取存储的文件名
        String newFilename = FileUploadUtil.newFileName(filename);
        // 获取最终存储的路径和文件名
        String finalName = storePath + File.separator + newFilename;
        source.transferTo(new File(finalName));
        return "login";
    }
}

// FileUploadUtil 工具类
public class FileUploadUtil {

    private FileUploadUtil() {}

    /**
     * 生成新的文件名称，生成规则：UUID_原文件名称
     * @param filename 原文件名称
     * @return 新生成的文件名称
     */
    public static String newFileName(String filename) {
        return UUID.randomUUID().toString().replaceAll("-", "") + "_" + filename;
    }

    /**
     * 生成存放上传文件的路径，生成规则：
     * 根路径/二级目录/三级目录，二级、三级目录都是根据文件名称的 hashCode（生成三级时进行了右移4位操作）和15做与运算以后生成的0~15的数字
     * 最多可以支持 16 的 8 次方个目录，共有 43 亿个目录
     * @param basePath 根路径
     * @param filename 文件名
     * @return 存放文件的最终路径
     */
    public static String newFilePath(String basePath, String filename) {
        int hashCode = filename.hashCode();
        int path2 = hashCode & 15; // 和15进行与运算，生成二级目录
        int path3 = (hashCode >> 4) & 15; // hashCode 右移4位，然后和15进行与运算，生成三级目录
        String dir = basePath + File.separator + path2 + File.separator + path3; // 将1、2、3级目录拼接在一起
        // 如果路径不存在，创建
        File fileDir = new File(dir);
        if (!fileDir.exists())
            fileDir.mkdirs();

        // 返回存放文件的最终路径
        return dir;
    }
}
```

### 11. 下载

#### 11.1 下载页面

##### 导入 jstl 依赖

```xml
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>jstl</artifactId>
  	<version>1.2</version>
    <scope>runtime</scope>
</dependency>
<dependency>
    <groupId>taglibs</groupId>
    <artifactId>standard</artifactId>
  	<version>1.1.2</version>
</dependency>
```

##### 创建下载jsp页面

```jsp
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>下载</title>
</head>
<body>
    <a href="${pageContext.request.contextPath}/download/test1?name=比翼研发云平台介绍及使用成效.docx">下载附件</a>
    <table>
        <thead>
        <tr>
            <th>文件名</th>
            <th>下载链接</th>
        </tr>
        </thead>
        <tbody>
        <c:forEach items="${allFiles}" var="files">
            <tr>
                <td>${files.value}</td>
                <td><a href="${pageContext.request.contextPath}/download/test1?name=${files.key}">下载</a></td>
            </tr>
        </c:forEach>
        </tbody>
    </table>
</body>
</html>
```

#### 11.2 Handler

```java
@Controller
@RequestMapping("/download")
public class DownloadController {

    @RequestMapping("/test1")	// 用于下载
    public void test1(String name, HttpSession session, HttpServletResponse resp) throws IOException {
        // 获得文件存放的根目录
        String path = session.getServletContext().getRealPath(File.separator + "WEB-INF" + File.separator + "upload");
        // 获取真实文件名称（带后缀）
        String filename = name.substring(name.indexOf("_") + 1);
        // 获取最终的下载路径
        String realPath = FileUploadUtil.newFilePath(path, filename);
        String downloadUrl = realPath + File.separator + name;

        // 设置响应头，告知浏览器，要以附件的形式保存内容，filename=浏览器显示的下载文件名
        resp.setHeader("content-disposition", "attachment;filename=" + URLEncoder.encode(filename,"UTF-8"));
        // 读取目标文件，写出给客户端
        IOUtils.copy(new FileInputStream(downloadUrl), resp.getOutputStream());
    }

    @RequestMapping("/filesmap")	// 用于展示可用的下载文件
    public String filesmap(HttpServletRequest request) {
        // 获得文件存放的根目录
        String path = request.getServletContext().getRealPath(File.separator + "WEB-INF" + File.separator + "upload");

        // 获取该目录下的所有文件
        Map<String, String> allFiles = new HashMap<>();
        File root = new File(path);
        if (!root.exists()) {
            root.mkdirs();
            request.setAttribute("allFiles",allFiles);
        } else
            FileUtil.getAllFilesRecursion(root, allFiles);

        request.setAttribute("allFiles", allFiles);
        return "download";
    }
}
```

### 12. 验证码

网页中的验证码是网页安全的一个屏障，可以一定程序上防止暴力破解

#### 12.1 导入jar

```xml
<dependency>
    <groupId>com.github.penggle</groupId>
    <artifactId>kaptcha</artifactId>
    <exclusions>
        <exclusion>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
        </exclusion>
    </exclusions>
</dependency>
```

#### 12.2 web.xml 配置

```xml
<servlet>
    <servlet-name>cap</servlet-name>
    <servlet-class>com.google.code.kaptcha.servlet.KaptchaServlet</servlet-class>
    <init-param>
        <param-name>kaptcha.border</param-name>
        <param-value>no</param-value>
    </init-param>
    <init-param>
        <param-name>kaptcha.textproducer.char.length</param-name>
        <param-value>4</param-value>
    </init-param>
    <init-param>
        <param-name>kaptcha.textproducer.char.string</param-name>
        <param-value>abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789</param-value>
    </init-param>
    <init-param>
        <param-name>kaptcha.background.clear.to</param-name>
        <param-value>211,229,237</param-value>
    </init-param>
    <init-param>
        <!--session.setAttribute("captcha", "验证码")-->
        <param-name>kaptcha.session.key</param-name>
        <param-value>captcha</param-value>
    </init-param>
</servlet>
<servlet-mapping>
    <servlet-name>cap</servlet-name>
    <url-pattern>/captcha</url-pattern>
</servlet-mapping>
```

#### 12.3 页面

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>验证码</title>
</head>
<body>
    <form action="${pageContext.request.contextPath}/code/test1">
        <img src="${pageContext.request.contextPath}/captcha" id="validateCode">
        <input type="text" name="code"><br>
        <input type="submit" value="提交">
    </form>
    <script>
        var img = document.getElementById("validateCode");
        img.style.cursor = "pointer";
        img.style.width = "100px";
        img.onclick = function (ev) {
            img.src = "${pageContext.request.contextPath}/captcha?" + new Date().getTime()
        };
    </script>
</body>
</html>
```

#### 12.4 handler

```java
@Controller
@RequestMapping("/code")
public class ValidateCodeController {

    @RequestMapping("/test1")
    public String test1(String code, HttpSession session) {
        System.out.println("/code/test1");
        String vCode = (String) session.getAttribute("captcha");
        if (vCode.equalsIgnoreCase(code))
            return "index";
        return "error1";
    }
}
```

### 13. REST

这是一种开发风格，遵从此风格开发的软件，就符合 `REST` 风格，则称它是 `RESTFUL` 的

两个核心要求：

* 每个资源都有唯一的标识（`URL`）
* 不同的行为，使用对应的 `http-method`

| 访问标识                                     | 资源            |
| -------------------------------------------- | --------------- |
| [http://localhost:8081/xxx/users]()          | 所有用户        |
| [http://localhost:8081/xxx/users/1]()        | 用户1           |
| [http://localhost:8081/xxx/users/1/orders]() | 用户1的所有订单 |

| 请求方式 | 标识                                          | 意图                        |
| -------- | --------------------------------------------- | --------------------------- |
| `GET`    | [http://localhost:8081/xxx/users]()           | 查询所有用户                |
| `POST`   | [http://localhost:8081/xxx/users]()           | 在所有用户中增加一个        |
| `PUT`    | [http://localhost:8081/xxx/users]()           | 在所有用户中修改一个        |
| `DELETE` | [http://localhost:8081/xxx/users/1]()         | 删除用户1                   |
| `GET`    | [http://localhost:8081/xxx/users/1]()         | 查询用户1                   |
| `GET`    | [http://localhost:8081/xxx/users/1/orders]()  | 查询用户1的所有订单         |
| `POST`   | [htttp://localhost:8081/xxx.users/1/orders]() | 在用户1的所有订单中增加一个 |

#### 13.1 优点

* 看 `URL` 就知道要什么
* 看 `http method` 就知道要干什么

#### 13.2 使用

##### 定义 RESTFUL 风格的 controller

```java
@RequestMapping(value="/users", method = RequestMethod.GET)
```

等价于

```java
@GetMapping("/users")
```

#### 13.3 示例

```java
@RestController
@RequestMapping("/rest")
public class RestfulController {

    @GetMapping("/users")
    public List<User> queryUsers() {
        System.out.println("query users with get");
        User user1 = new User(1, "张三", true);
        User user2 = new User(2, "李四", false);
        return Arrays.asList(user1, user2);
    }

    @GetMapping("/users/{id}")
    public User queryOne(@PathVariable Integer id) {
        System.out.println("query one with get");
        return new User(1, "张三", true);
    }

    @DeleteMapping("/users/{id}")
    public String deleteOne(@PathVariable Integer id) {
        System.out.println("delete one with get：" + id);
        return "ok";
    }

    @PostMapping("/users")
    public String saveUser(@RequestBody User user) {
        System.out.println("add user with post: " + user);
        return "ok";
    }

    @PutMapping("/users")
    public String updateUser(@RequestBody User user) {
        System.out.println("update user with get: " + user);
        return "ok";
    }
}
```

### 14. 跨域请求

#### 14.1 域

**域：协议 + IP + 端口**，例如：

* [http://localhost:8081]()
* [http://localhost:8080]()
* [http://www.baidu.com:80]()

#### 14.2 Ajax 跨域问题

* `Ajax` 发送请求时，不允许跨域，以防用户信息泄露
* 当 `Ajax` 跨域请求时，响应会被浏览器拦截，并报错，即浏览器默认不允许 `Ajax` 跨域得到响应内容
* 互相信任的域之间如果需要 `Ajax` 访问（比如前后端分离项目中，前端项目和后端项目之间），则需要额外的设置才可正常请求

#### 14.3 解决方案

在被访问方的 `Controller` 类上，添加注解

```java
@CrossOrigin("http://localhost:8080")	// 允许此域发请求访问
public class SysUserController {
  ...
}
```

携带对方 `cookie`，使得 `session` 可用。

在访问方，`Ajax` 添加属性：`withCredentials=true`

```javascript
$.ajax({
  type:'post',
  url:'http://localhost:8081/web/sys/login',
  ...
  xhrFields: {
    // 跨域携带cookie
    withCredentials: true
  }
});
// 或
var xhr = new XMLHttpRequest();
// 跨域携带cookie
xhr.withCredentials=true;
```

### 15. SpringMVC 执行流程

[![gdRtdx.md.png](https://z3.ax1x.com/2021/05/12/gdRtdx.md.png)](https://imgtu.com/i/gdRtdx)

### 16. Spring 整合

#### 16.1 整合思路

此时项目中有两个工厂：

* `DispatcherServlet` 启动的 `springmvc` 工厂 == 负责生产 `C` 及 `springmvc` 自己的系统组件
* `ContextLoaderListener` 启动的 `spring` 工厂 == 负责生产其它所有组件
* `springmvc` 的工厂会被设置为 `spring` 工厂的子工厂，可以随意获取 `spring` 工厂中的组件
* 整合过程，就是累加：**代码 + 依赖 + 配置**，然后将 `service` 注入给 `controller` 即可

#### 16.2 整合技巧

两个工厂不能有彼此侵入，即，生产的组件不能有重合

```xml
<!--这是 springmvc 的配置，告知 springmvc，哪些包下存在被注解的类
		use-default-filters=true	凡是被 @Controller,@Service,@Repository 注解的类，都会被扫描
		use-default-filters=false	默认不扫描包内的任何类，只扫描 include-filter 中指定的注解
		即，以下配置声明了只扫描被 @Controller 注解的类
-->
<context:component-scan base-package="com.ch.wchya.ssm">
    <context:include-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
</context:component-scan>

<!--这是 spring 的配置，配置了自动扫描的路径，除了 Controller 注解不扫描，其它的都扫描-->
    <context:component-scan base-package="com.ch.wchya.ssm" use-default-filters="true">
        <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
    </context:component-scan>
```

#### 16.3 整合

##### pom.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <parent>
        <artifactId>all</artifactId>
        <groupId>com.ch.wchya</groupId>
        <version>1.0-SNAPSHOT</version>
        <relativePath>../pom.xml</relativePath>
    </parent>
    <modelVersion>4.0.0</modelVersion>

    <artifactId>ssm</artifactId>

    <packaging>war</packaging>

    <dependencies>

        <!--project dependency-->
        <dependency>
            <groupId>com.ch.wchya</groupId>
            <artifactId>entity</artifactId>
            <version>1.0-SNAPSHOT</version>
        </dependency>

        <!--spring-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-core</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-context</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-jdbc</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-test</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-aop</artifactId>
        </dependency>
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-aspects</artifactId>
        </dependency>

        <!--spring mvc-->
        <dependency>
            <groupId>org.springframework</groupId>
            <artifactId>spring-webmvc</artifactId>
        </dependency>

        <!--mysql-->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
        </dependency>

        <!--mybatis-->
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis</artifactId>
        </dependency>
        <dependency>
            <groupId>org.mybatis</groupId>
            <artifactId>mybatis-spring</artifactId>
        </dependency>

        <!--javaweb-->
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>javax.servlet-api</artifactId>
        </dependency>
        <dependency>
            <groupId>javax.servlet</groupId>
            <artifactId>jstl</artifactId>
        </dependency>
        <dependency>
            <groupId>taglibs</groupId>
            <artifactId>standard</artifactId>
        </dependency>
        <dependency>
            <groupId>javax.servlet.jsp</groupId>
            <artifactId>javax.servlet.jsp-api</artifactId>
        </dependency>

        <!--json-->
        <dependency>
            <groupId>com.alibaba</groupId>
            <artifactId>fastjson</artifactId>
        </dependency>

        <!--log4j-->
        <dependency>
            <groupId>log4j</groupId>
            <artifactId>log4j</artifactId>
        </dependency>

        <!--junit-->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <scope>test</scope>
        </dependency>

    </dependencies>

    <build>
        <resources>
            <resource><!--设置 src/main/java/ 目录下的 xml 文件也被当作资源读取-->
                <directory>src/main/java</directory>
                <includes>
                    <include>**/*.xml</include>
                </includes>
            </resource>
            <resource>
                <directory>src/main/resources</directory>
                <includes>
                    <include>*.xml</include>
                    <include>*.properties</include>
                </includes>
            </resource>
        </resources>
    </build>

</project>
```

##### web.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">

    <!--配置 springmvc 的前端控制器和配置信息-->
    <servlet>
        <servlet-name>mvc</servlet-name>
        <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:mvc.xml</param-value>
        </init-param>

        <load-on-startup>1</load-on-startup>

        <!--  StandardServletMultipartResolver 属性配置  -->
        <multipart-config>
            <!--上传到/tmp/upload 目录,如果配置为/使用HttpServletRequest上传时，可能会抛出异常/无权限操作-->
            <!--<location>/</location>-->
            <!--文件大小为2M-->
            <max-file-size>2097152</max-file-size>
            <!--整个请求不超过4M-->
            <max-request-size>4194304</max-request-size>
            <!--所有文件都要写入磁盘-->
            <file-size-threshold>0</file-size-threshold>
        </multipart-config>
    </servlet>
    <servlet-mapping>
        <servlet-name>mvc</servlet-name>
        <url-pattern>/</url-pattern>
    </servlet-mapping>
    
    <!--配置 spring 的相关内容-->
    <context-param>
        <param-name>contextConfigLocation</param-name>
        <param-value>classpath:applicationContext.xml</param-value>
    </context-param>
    <listener>
        <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
    </listener>

    <!--此过滤器会进行：request.setCharactorEncoding("utf-8");的操作-->
    <filter>
        <filter-name>encoding</filter-name>
        <filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
        <init-param>
            <param-name>encoding</param-name>
            <param-value>utf-8</param-value>
        </init-param>
    </filter>
    <filter-mapping>
        <filter-name>encoding</filter-name>
        <url-pattern>/*</url-pattern>
    </filter-mapping>

</web-app>
```

##### applicationContext.xml（spring配置文件）

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:tx="http://www.springframework.org/schema/tx"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           http://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/context
                           http://www.springframework.org/schema/context/spring-context.xsd
                           http://www.springframework.org/schema/tx
                           http://www.springframework.org/schema/tx/spring-tx.xsd
                           http://www.springframework.org/schema/aop
                           http://www.springframework.org/schema/aop/spring-aop.xsd
                          "
>

    <!--配置自动扫描的路径，除了 Controller 注解不扫描，其它的都扫描-->
    <context:component-scan base-package="com.ch.wchya.ssm" use-default-filters="true">
        <context:exclude-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
    </context:component-scan>

    <!--DataSource-->
    <context:property-placeholder location="classpath:jdbc.properties"/>
    <bean id="dataSource" class="com.alibaba.druid.pool.DruidDataSource" init-method="init" destroy-method="close">
        <!--基本配置-->
        <property name="driverClassName" value="${driverClassName}"/>
        <property name="url" value="${url}"/>
        <property name="username" value="${username}"/>
        <property name="password" value="${password}"/>

        <!--高级配置-->
        <property name="initialSize" value="${initialSize}"/>
        <property name="minIdle" value="${minIdle}"/>
        <property name="maxActive" value="${maxActive}"/>
        <property name="maxWait" value="${maxWait}"/>
    </bean>

    <!--SqlSessionFactory-->
    <bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean"><!--该配置用于生产 SqlSessionFactory-->
        <!--注入连接池-->
        <property name="dataSource" ref="dataSource"/>
        <property name="configLocation" value="classpath:mybatis-config.xml"/>
        <!--注入 dao-mapper 文件信息，如果 mapper 与 dao 同包且同名，该配置可省略-->
        <property name="mapperLocations">
            <list>
                <value>classpath:com/ch/wchya/ssm/dao/*.xml</value>
            </list>
        </property>
        <!--为 mapper 中用到的实体定义所在的包路径，这样，在 mapper 中就可以不用写实体的完全限定名称了-->
        <property name="typeAliasesPackage" value="com.ch.wchya.entity.ssm"/>
    </bean>

    <!--dao-mapper 扫描路径配置-->
    <bean class="org.mybatis.spring.mapper.MapperScannerConfigurer">
        <!--dao接口所在的包，如果有多个包，可以用，分隔-->
        <property name="basePackage" value="com.ch.wchya.ssm.dao"/>
        <!--如果工厂中只有一个 sqlSessionFactory 的 bean，则此配置可以省略-->
        <!--<property name="sqlSessionFactoryBeanName" value="sqlSessionFactory"/>-->
    </bean>

    <!--配置事务相关-->
    <bean id="transactionManager" class="org.springframework.jdbc.datasource.DataSourceTransactionManager">
        <property name="dataSource" ref="dataSource"/>
    </bean>

    <!--配置增强通知-->
    <tx:advice id="txAdvice" transaction-manager="transactionManager">
        <tx:attributes>
            <tx:method name="get*" read-only="true" propagation="SUPPORTS"/>
            <tx:method name="find*" read-only="true" propagation="SUPPORTS"/>
            <tx:method name="select*" read-only="true" propagation="SUPPORTS"/>
            <tx:method name="add*"/>
            <tx:method name="save*"/>
            <tx:method name="insert*"/>
            <tx:method name="update*"/>
            <tx:method name="delete*"/>
        </tx:attributes>
    </tx:advice>
    <aop:config>
        <aop:advisor advice-ref="txAdvice" pointcut="execution(* com.ch.wchya..service..*.*(..))"/>
    </aop:config>

</beans>
```

##### mvc.xml（springmvc 的配置文件）

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
                           https://www.springframework.org/schema/beans/spring-beans.xsd
                           http://www.springframework.org/schema/context
                           https://www.springframework.org/schema/context/spring-context.xsd
                           http://www.springframework.org/schema/mvc
                           https://www.springframework.org/schema/mvc/spring-mvc.xsd
">

    <!--告知 springmvc，哪些包下存在被注解的类
      use-default-filters=true   凡是被 @Controller,@Service,@Repository 注解的类，都会被扫描
      use-default-filters=false  默认不扫描包内的任何类，只扫描 include-filter 中指定的注解
      即，以下配置声明了只扫描被 @Controller 注解的类
    -->
    <context:component-scan base-package="com.ch.wchya.ssm" use-default-filters="false">
        <context:include-filter type="annotation" expression="org.springframework.stereotype.Controller"/>
    </context:component-scan>

    <!--启用注解-->
    <mvc:annotation-driven>
        <mvc:message-converters><!--使用 fastjson 作为 json 转换器-->
            <bean class="com.alibaba.fastjson.support.spring.FastJsonHttpMessageConverter">
                <property name="supportedMediaTypes">
                    <list>
                        <value>application/json</value>
                    </list>
                </property>
            </bean>
        </mvc:message-converters>
    </mvc:annotation-driven>

    <!--视图解析器
            作用：1. 捕获后端控制器的返回值，=>    hello
                 2. 解析：在返回值的前后进行拼接 =>   /hello.jsp
    -->
    <bean class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/views/"/>
        <property name="suffix" value=".jsp"/>
        <property name="contentType" value="text/html;charset=UTF-8" />
        <property name="viewClass" value="org.springframework.web.servlet.view.JstlView"/>
    </bean>

    <!--
        额外的增加一个 handler，且其 requestMapping：/**，可以匹配所有请求，但是优先级最低。
        所以，如果其它所有的 handler 都匹配不上，请求会转身 /**。恰好，这个 handler 就是处理静态资源的处理方式：
        将请求转发到 tomcat 中名为 default 的 servlet
        RequestMapping  /*  可以匹配到的路径有：/a,/b,/c,...，不能匹配：/a/b,/a/b/c,...
                        /** 可以匹配任意路径
        下面配置的 handler 做的事情：将收到的请求转发到 tomcat 的 default servlet
    -->
    <mvc:default-servlet-handler/>

</beans>
```

##### 配置 mybatis 使用 log4j 打印日志

```xml
<!--mybatis-config.xml，mybatis的主配置文件-->
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
        PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
    <settings>
        <setting name="logImpl" value="LOG4J"/>
    </settings>
</configuration>
```

```properties
# log4j 的配置文件
# Set root category priority to INFO and its only appender to CONSOLE.
#log4j.rootCategory=INFO, CONSOLE            debug   info   warn error fatal
log4j.rootCategory=debug, CONSOLE, LOGFILE

# Set the enterprise logger category to FATAL and its only appender to CONSOLE.
log4j.logger.org.apache.axis.enterprise=FATAL, CONSOLE

# CONSOLE is set to be a ConsoleAppender using a PatternLayout.
log4j.appender.CONSOLE=org.apache.log4j.ConsoleAppender
log4j.appender.CONSOLE.layout=org.apache.log4j.PatternLayout
log4j.appender.CONSOLE.layout.ConversionPattern=%d{ISO8601} %-6r [%15.15t] %-5p %30.30c %x - %m\n

# LOGFILE is set to be a File appender using a PatternLayout.
log4j.appender.LOGFILE=org.apache.log4j.FileAppender
log4j.appender.LOGFILE.File=/Users/wchya/project/mybatis-log/
log4j.appender.LOGFILE.Append=true
log4j.appender.LOGFILE.layout=org.apache.log4j.PatternLayout
log4j.appender.LOGFILE.layout.ConversionPattern=%d{ISO8601} %-6r [%15.15t] %-5p %30.30c %x - %m\n
```

##### Entity

```java
@Data
public class MUser {
  private long id;
  private String username;
  private Date birthday;
  private String sex;
  private String address;
}
```

##### Dao

```java
public interface MUserDao {
    List<MUser> findAll();
    int addMUsers(MUser mUser);
}
```

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
        "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.ch.wchya.ssm.dao.MUserDao">
    <select id="findAll" resultType="MUser">
        select * from m_user
    </select>

    <insert id="addMUsers" parameterType="MUser">
        insert into m_user(username,birthday,sex,address) values(#{username},#{birthday},#{sex},#{address})
    </insert>
</mapper>
```

##### Service

```java
public interface MUserService {
    List<MUser> findAll();
    int addMUser(MUser mUser);
}
@Service("mUserService")
public class MUserServiceImpl implements MUserService {

    @Autowired
    private MUserDao mUserDao;

    @Override
    public List<MUser> findAll() {
        return mUserDao.findAll();
    }

    @Override
    public int addMUser(MUser mUser) {
        return mUserDao.addMUsers(mUser);
    }
}
```

##### Controller

```java
@Controller
@RequestMapping("/muser")
public class MUserController {

    @Autowired
    private MUserService mUserService;

    @RequestMapping
    public String index() {
        return "addmuser";
    }

    @RequestMapping("/all")
    public String all(Model model) {
        List<MUser> mUsers = mUserService.findAll();
        model.addAttribute("mUsers", mUsers);
        return "musers";
    }

    @RequestMapping("/add")
    @ResponseBody
    public String add(@RequestBody MUser mUser) {
        int count = mUserService.addMUser(mUser);
        System.out.println(count);
        return "ok";
    }
}
```

##### JSP

```jsp
<!--addmuser.jsp-->
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>添加用户</title>
</head>
<body>
<form>
    <label for="username">姓名：</label><input type="text" id="username" name="username"><br>
    <label for="birthday">生日：</label><input type="date" id="birthday" name="birthday"><br>
    <label for="sex">性别：</label><input type="radio" name="sex" id="sex" value="男">男<input type="radio" name="sex" value="女">女<br>
    <label for="address"></label><input type="text" id="address" name="address"><br>
    <button id="btnAdd">新增</button>
</form>
<script>
    let addBtn = document.getElementById("btnAdd");
    addBtn.onclick = function (ev) {
        let username = document.getElementById("username").value;
        let birthday = document.getElementById("birthday").value;
        let sex = document.getElementById("sex").value;
        let address = document.getElementById("address").value;
        ev.preventDefault();
        if (username === '')
            alert('请输入用户名！');
        else if (birthday === '')
            alert('请输入生日！');
        else if (sex === '')
            alert('请选择性别！');
        else if (address === '')
            alert('请输入地址！')
        else {
            let xhr = new XMLHttpRequest();
            let mUser = {username: username, birthday: birthday, sex: sex, address: address};
            xhr.open('post', '/muser/add')
            xhr.setRequestHeader('Content-Type', 'application/json;charset=UTF-8');
            xhr.send(JSON.stringify(mUser));
            xhr.onreadystatechange = function (ev1) {
                if (xhr.readyState === 4 && xhr.status === 200) {
                    window.location.replace('/muser/all');
                }
            }
        }
    };
</script>
</body>
</html>
<!--musers.jsp-->
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
<html>
<head>
    <title>用户列表</title>
</head>
<body>
    <table align="center" border="1">
        <tr>
            <th>序号</th>
            <th>姓名</th>
            <th>生日</th>
            <th>性别</th>
            <th>地址</th>
        </tr>
        <c:forEach items="${mUsers}" var="user">
            <tr>
                <td>${user.id}</td>
                <td>${user.username}</td>
                <td><fmt:formatDate value="${user.birthday}" pattern="yyyy/MM/dd"/> </td>
                <td>${user.sex}</td>
                <td>${user.address}</td>
            </tr>
        </c:forEach>
    </table>
</body>
</html>
```

### 17. SpringMVC 绑定参数之类型转换

#### 实体类中加日期格式化注解

```java
@DateTimeFormat(pattern="yyyy-MM-dd HH:mm")
private Date createTime;
```

#### 属性编辑器

> Spring 3.1 之前提供

在 `Controller` 类中通过 `@initBinder` 完成

```java
/**
 *	在Controller层中添加一段数据绑定代码
 *	@param webDataBinder
*/
public void initBinder(WebDataBinder webDataBinder) throws Exception {
  SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm");
  sdf.setLenient(false);
  webDataBinder.registerCustomeEditor(Date.class, new CustomDateEditor(sdf, true));
}
```

> 自定义类型转换器必须实现 PropertyEditor 接口或者继承 PropertyEditorSupport 类

```java
public class YourClass extends PropertyEditorSupport { // 或者 implements PropertyEditor
  public void setAsText(String text) {
  	  SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd HH:mm");
  		Date date = sdf.parse(text);
    	this.setValue(date);
	}    
  
  public String setAsText() {
    Date date = (Date) this.getValue();
    return this.dateFormat.format(date);
  }
}
```



## 第三十四章 日志管理体系

### 1. 引言

#### 1.1 日志介绍

用户记录系统中发生的各种事件，记录泊位置常见的有：控制台、磁盘文件等

#### 1.2 日志级别

日志级别从低到高：`TRACE、DEBUG、INFO、WARN、ERROR、FATAL`

#### 1.3 日志作用

* 通过日志观察、分析项目的运行情况（项目维护）
* 通过日志分析用户的使用情况（大数据分析）

### 2. 解决方案1

#### 2.1 Log4j + Commons-Logging

##### 导入依赖

项目中添加 `Log4j` 和 `Commons-Logging` 的依赖

```xml
<dependency>
    <groupId>log4j</groupId>
    <artifactId>log4j</artifactId>
    <version>1.2.17</version>
</dependency>
<dependency>
    <groupId>commons-logging</groupId>
    <artifactId>commons-logging</artifactId>
    <version>1.2</version>
</dependency>
```

#### 2.2 基本使用

```java
public class HelloLog {
  // 需要一个输出日志的类，可以创建一个log属性
  Log log = LogFactory.getLog(HelloLog.class);
  
  @Test
  public void test1() {
    log.trace("hello trace");
    log.debug("hello debug");
    log.info("hello info");
    log.warn("hello warn");
    log.error("hello error");
    log.fatal("hello fatal");
  }
}
```

#### 2.3 配置信息

定义配置文件：`log4j.xml`

| 占位符 | 描述                                                         |
| ------ | ------------------------------------------------------------ |
| `%p`   | 输出优先级，即：`DEBUG、INFO、WARN、ERROR、FATAL`            |
| `%r`   | 输出自应用启动到输出该 `log` 信息耗费的毫秒数                |
| `%c`   | 输出所在类的全名                                             |
| `%t`   | 输出产生该日志事件的线程名                                   |
| `%n`   | 输出一个回车换行符                                           |
| `%d`   | 输出日志时间点的日期或时间，默认格式为 `ISO8601`，也可以在其后指定格式，比如：`%d[yyyy-MM-dd HH:mm:ss,SSS]`，输出类似：`2020-02-02 02:02:02,222` |
| `%l`   | 输出日志事件的发生位置，包括类名、发生的线程，以及在代码中的行数，例如：`Test4.main(Test4.java:10)` |

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE log4j:configuration PUBLIC "-//LOGGER" "http://org.apache/log4j/xml/log4j.dtd">
<log4j:configuration>
  
  <!--org.apache.log4j.ConsoleAppender 输出到控制台-->
  <appender name="myConsole" class="org.apache.log4j.ConsoleAppender">
    <!--输出格式-->
    <layout class="org.apache.log4j.PatternLayout">
      <param name="ConversionPattern" value="%-d{yyyy-MM-dd HH:mm:ss,SSS} [%c]-[%p] %m%n" />
    </layout>
  </appender>
  <!--输出到文件-->
  <appender name="myFile1" class="org.apache.log4j.RollingFileAppender">
    <param name="File" value="/Users/wchya/project/logs/log4j/hello.log"/><!--文件位置-->
    <param name="Append" value="true"/><!--是否选择追加-->
    <param name="MaxFileSize" value="1kb"/><!--文件最大字节数-->
    <param name="MaxBackupIndex" value="2"/><!--新文件数量-->
    <layout class="org.apache.log4j.PatternLayout">
      <param name="ConversionPattern" value="%p (%c:%l)- %m%n"/>
    </layout>
  </appender>
  <appender name="myFile2" class="org.apache.log4j.DailyRollingFileAppender">
    <param name="File" value="/Users/wchya/logs/log4j/hello2.log"/><!--文件位置-->
    <param name="Append" value="true"/><!--是否选择追加-->
    <layout class="org.apache.log4j.PatternLayout">
      <param name="ConversionPattern" value="%-d{yyyy-MM-dd HH:mm:ss,SSS} [%c]-[%p] %m%n"/>
    </layout>
  </appender>
  <!--根logger的位置-->
  <root>
    <!--优先级设置，all < trace < debug < info < warn < error < fatal < off-->
    <priority value="all"/>
    <appender-ref ref="myConsole"/>
    <appender-ref ref="myFile1"/>
  </root>
</log4j:configuration>
```

### 3. 解决方案2

#### 3.1 Logback + SJF4j

##### 导入依赖

```xml
<dependency>
    <groupId>ch.qos.logback</groupId>
    <artifactId>logback-classic</artifactId>
    <version>1.2.3</version>
    <scope>test</scope>
</dependency>
```

#### 3.2 基本使用

```java
public class TestLog2 {
    private final Logger logger = LoggerFactory.getLogger(TestLog2.class);

    @Test
    public void test() {
        System.out.println(logger.getClass());
        logger.trace("hello trace");
        logger.debug("hello debug");
        logger.info("hello info");
        logger.warn("hello warn");
        logger.error("hello error");
    }
}
```

#### 3.3 配置信息

定义：`logback.xml`

| 点位符                        | 描述                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| `%d[yyyy-MM-dd HH:mm:ss.SSS]` | 日期                                                         |
| `%5p`                         | 日志级别，5位字符长度显示，如果内容占有不满5位则内容右对齐并在左侧补空格 |
| `%-5p`                        | 5位字符长度显示日志级别，如果内容占有不满5位则内容左对齐并在右侧补空格，-代表左对齐 |
| `%logger`                     | 日志所在包和类                                               |
| `%M`                          | 日志所在方法名                                               |
| `%L`                          | 日志所在代码行                                               |
| `%m`                          | 日志下方                                                     |
| `%n`                          | 换行                                                         |

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!--scan:当此属性设置为true时，配置文件如果发生改变，将会被重新加载，默认值为true-->
<!--scanPeriod:设置监测配置文件是否有修改的时间间隔，如果没有给出时间单位，默认单位是毫秒。当scan为true时，此属性失效，默认的时间间隔为1分钟-->
<!--debug:当此属性设置为true时，将打印出logback内部日志信息，实时查看logback运行状态，默认值为false-->
<configuration scan="true" scanPeriod="60 seconds" debug="true">
  
  <!--定义变量，可通过 ${log.path} 和 ${CONSOLE_LOG_PATTERN} 得到变量值-->
  <property name="log.path" value="/Users/wchya/project/logs/logback/"/>
  <property name="CONSOLE_LOG_PATTERN" value="%d{yyyy-MM-dd HH:mm:ss.SSS} |-[%-5p] in %logger.%M[line-%L] -%m%n"/>
  <!--输出到控制台-->
  <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
    <!--Threshold=即最低日志级别，此appender输出大于等于对应级别的日志（当然还要满足root中定义的最低级别）-->
    <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
      <level>debug</level>
    </filter>
    <encoder>
      <!--日志格式（引用变量）-->
      <Pattern>${CONSOLE_LOG_PATTERN}</Pattern>
      <!--设置字符集-->
      <charset>UTF-8</charset>
    </encoder>
  </appender>
  <!--追加到文件中-->
  <appender name="file" class="ch.qos.logback.core.FileAppender">
    <file>${log.path}/hello2.log</file>
    <encoder>
      <pattern>${CONSOLE_LOG_PATTERN}</pattern>
    </encoder>
  </appender>
  <!--滚动追加到文件中-->
  <appender name="file2" class="ch.qos.logback.core.rolling.RollingFileAppender">
    <!--正在记录的日志文件的路径及文件名-->
    <file>${log.path}/hello.log</file>
    <!--日志文件输出格式-->
    <encoder>
      <pattern>${CONSOLE_LOG_PATTERN}</pattern>
      <charset>UTF-8</charset><!--设置字符集-->
    </encoder>
    <!--日志记录器的滚动策略，按日期，按大小记录
				文件超过最大尺寸后，会新建文件，然后新的日志文件中继续写入
				如果日期变更，也会新建文件，然后在新的日志文件中写入当天日志-->
    <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
      <!--新建文件后，原日志改名如下 %i=文件序号，i从0开始-->
      <fileNamePattern>${log.path}/hello-%d{yyyy-MM-dd}.%i.log</fileNamePattern>
      <!--每个日志文件的最大体量-->
      <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
        <maxFileSize>8kb</maxFileSize>
      </timeBasedFileNamingAndTriggeringPolicy>
      <!--日志文件保留天数，1=只保留昨天的归档日志文件，不设置则保留所有日志-->
      <maxHistory>1</maxHistory>
    </rollingPolicy>
  </appender>
  
  <root level="trace">
    <appender-ref ref="CONSOLE"/>
    <appender-ref ref="file"/>
    <appender-ref ref="file2"/>
  </root>
  
</configuration>
```

## 第三十五章 Quartz

### 1. 简介

`Quzrtz:http://www.quartz-scheduler.org/`，是一个定时任务调度框架。比如你遇到这样的问题：

* 想在30分钟后，查看订单是否支付，未支付则取消订单
* 想在每月29号，信用卡自动还款
* ……
* 想定时在某个时间，去做某件事（任务）

`Quartz` 是要做定时任务的调度，设置好触发时间规则，以及相应的任务（`Job`）即可

### 2. 使用

#### 2.1 导入依赖

```xml
<dependency>
    <groupId>org.quartz-scheduler</groupId>
    <artifactId>quartz</artifactId>
    <version>2.3.2</version>
</dependency>
```

#### 2.2 定义 job

```java
public class HelloJob implements Job {
    @Override
    public void execute(JobExecutionContext jobExecutionContext) throws JobExecutionException {
        JobDetail jobDetail = jobExecutionContext.getJobDetail();
        JobKey key = jobDetail.getKey();
        System.out.println(key.getName());
        System.out.println(key.getGroup());
        System.out.println("Hello job" + new Date());
    }
}
```

#### 2.3 API 测试

```java
public class HelloQuartz {

    public static void main(String[] args) throws SchedulerException {
        // 1. 调度器 Scheduler
        Scheduler scheduler = StdSchedulerFactory.getDefaultScheduler();

        // 2. 触发器
        SimpleTrigger trigger = TriggerBuilder.newTrigger().withIdentity("trigger1", "group1")
                .startNow()
                .withSchedule(SimpleScheduleBuilder.simpleSchedule().withIntervalInSeconds(1).withRepeatCount(5))
                .endAt(new GregorianCalendar(2021, 4, 15, 16, 55, 00).getTime())
                .build();

        // 3. JobDetail
        JobDetail jobDetail = JobBuilder.newJob(HelloJob.class).withIdentity("job1", "group1").build();

        // 4. 将 JobDetail 和 触发器 增加到调度器中
        scheduler.scheduleJob(jobDetail, trigger);

        // 5. 启动，调度器开始工作
        scheduler.start();
    }
}
```

#### 2.4 配置

```properties
# 名为：quartz.properties，放置在 classpath 下，如果没有此配置则按默认配置启动
# 指定调度器名称，非实现类
org.quartz.scheduler.instanceName=DefaultQuartzScheduler
# 指定线程池实现类
org.quartz.threadPool.class=org.quartz.simpl.SimpleThreadPool
# 线程池线程数量
org.quartz.threadPool.threadCount=10
# 优先级，默认5
org.quartz.threadPool.threadPriority=5
# 非持久化job
org.quartz.jobStore.class=org.quartz.simpl.RAMJobStore
```

#### 2.5 核心类说明

* `Scheduler`：调度器。所有的高度都是由它控制，是 `Quartz` 的大脑，所有任务都是由它来管理
* `Job`：任务，想定时执行的事情（定义业务逻辑）
* `JobDetail`：基于 `Job`，进一步包装。其中关联一个 `Job`，并为 `Job` 指定更详细的属性，比如标识等
* `Trigger`：触发器。可以指定给某个任务，指定任务的触发机制

### 3. Trigger

#### 3.1 SimpleTrigger

以一定的时间间隔（单位是毫秒）执行的任务：

* 指定起始和戴上时间（时间段）
* 指定时间间隔、执行次数

##### 示例

```java
SimpleTrigger trigger = TriggerBuilder.newTrigger()
  								.withIdentity("trigger1", "group1")
  								.startNow()
  								.withSchedule(SimpleScheduleBuilder.simpleShedule()
                                		.withIntervalInSeconds(1)	//每秒执行一次
                                		.repeatForever())//不限执行次数
  								.endAt(new GregorianCalendar(2021, 5, 15, 16, 35, 0).getTime())
  								.build();
```

```java
SimpleTrigger trigger = TriggerBuilder.newTrigger()
  								.withIdentity("trigger1", "group1")
  								.startNow()
  								.withSchedule(SimpleScheduleBuilder.simpleShedule()
                                		.withIntervalInMinutes(3)	//每3分钟执行一次
                                		.withRepeatCount(3))//执行次数不超过3次
  								.endAt(new GregorianCalendar(2021, 5, 15, 16, 35, 0).getTime())
  								.build();
```

#### 3.2 CronTrigger【重点】

适合于更复杂的任务，它支持类似于 `Linux Cron` 的语法（并且更强大）

##### 示例

```java
// 每天 10:00-12:00，每隔2分钟执行一次
CronTrigger trigger = TriggerBuilder.newTrigger()
  						.withIndentity("t1", "g1")
  						.withSchedule(CronScheduleBuilder.cronSchedule("0 0/2 10-12 * * ?")).build();
```

##### Cron 表达式组成

表达式组成：`秒 分 时 日 月 星期几 [年]`，其中 年 是可选的，一般不指定，如：`10 20 18 3 5 ?` 代表 `5月3日18点20分10秒，星期几不确定`

| 位置 | 时间域       | 允许值           | 特殊值   |
| ---- | ------------ | ---------------- | -------- |
| 1    | 秒           | 0-59             | `,-*/`   |
| 2    | 分钟         | 0-59             | `,-*/`   |
| 3    | 小时         | 0-23             | `,-*/`   |
| 4    | 日期         | 1-31             | `,-*/LW` |
| 5    | 月份         | 1-12             | `,-*/`   |
| 6    | 星期         | 1-7（1是星期日） | `,-*/L#` |
| 7    | 年份（可选） |                  | `,-*/`   |

##### Cron 表达式符号

表达式中可以使用的特殊符号的含义如下

| 符号      | 语义                                                         |
| --------- | ------------------------------------------------------------ |
| `*`       | 可用在所有字段中，表示对应时间域的每一个时刻，例如，在分钟字段时，表示每分钟 |
| `?`       | 该字符只在日期和星期字段中使用，它通常表示不确定值           |
| `-`       | 表达一个范围，如在小时字段中使用“10-12”，则表示从10到12点，即10，11，12 |
| `,`       | 表达一个列表值，如在星期字段中使用“MON,WED,FRI”，则表示星期一、三、五 |
| `/`       | `x/y` 表达一个等步长序列，`x` 为起始值，`y` 为增量步长值。如在分钟字段中使用 `0/15`，则表示为0，15，30和45秒 |
| `#`       | 该字符只用在星期字段中，`4#2` 代表第一个星期3，`5#4` 代表第4个星期4 |
| `L`       | 该字符只在日期和星期字段中使用，代表 `Last` 的意思，但它在两个字段中意思不同。 |
|           | 如果用在星期字段里，则表示星期六，等同于使用数字7            |
|           | `L` 出现在星期字段里，而且在前面有一个数据 `x`，则表示 “这个月的最后一个周x”，例如，6L表示该月的最后星期五 |
|           | `L` 在日期字段中，表示这个月份的最后一天，如一月的31号，非闰年的二月28号 |
| `W`       | 该字符只能出现在日期字段里，是对前导日期的修饰，表示离该日期最近的工作日 |
|           | 例如 `15W` 表示离该月15号最近的工作日，如果该月15号是星期六，则匹配14号星期五，如果15日是星期日，则匹配16号星期一；如果15号是星期二，那结果就是15号星期二；但必须注意关联的匹配日期不能够跨月 |
| `LW` 组合 | 在日期字段可以组合使用 `LW`，它的意思是当月的最后一个工作日  |

##### Cron 表达式示例

| 表达式                   | 说明                                                         |
| ------------------------ | ------------------------------------------------------------ |
| 0 0 12 * * ?             | 每天12点运行                                                 |
| 0 15 10 * * ?            | 每天10:15运行                                                |
| 0 15 10 * * ? 2008       | 在2008年的每天10:15运行                                      |
| 0 * 14 * * ?             | 每天14点到15点之间每分钟运行一次，开始于14点，结束于14:50    |
| 0 0/5 14 * * ?           | 每天14点到15点每5分钟运行一次，开始于14点，结束于14:55       |
| 0 0/5 14,18 * * ?        | 每天14点到15点每5分钟运行一次，此外每天18点到19点第5分钟也运行一次 |
| 0 0-5 14 * * ?           | 每天14点到14:05，第分钟运行一次                              |
| 0 0-5/2 14 * * ?         | 每天14点到14:05，第2分钟运行一次                             |
| 0 10,44 14 ? 3 4         | 3月每周三的14:10分和14:44，每分钟运行一次                    |
| 0 15 10 ? * 2-6          | 每周一、二、三、四、五的10:15分运行                          |
| 0 15 10 15 * ？          | 每月15日10:15分运行                                          |
| 0 15 10 L * ?            | 每月最后一天10:15分运行                                      |
| 0 15 10 ? * 6L           | 每月最后一个星期五10:15分运行【此时天必须是?】               |
| 0 15 10 ? * 6L 2007-2009 | 在2007，2008，2009年每个月的最后一个星期五的10:15分运行      |

### 4. Spring 整合 Quartz【重点】

#### 4.1 依赖

```xml
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-context-support</artifactId>
</dependency>
<dependency>
    <groupId>org.quartz-scheduler</groupId>
    <artifactId>quartz</artifactId>
</dependency>
```

#### 4.2 定义 Job

```java
public class HelloJob implements Job {
    @Override
    public void execute(JobExecutionContext jobExecutionContext) throws JobExecutionException {);
        System.out.println("Hello job" + new Date());
    }
}
```

#### 4.3 配置

* 调度器：`SchedulerFactoryBean`
* 触发器：`CronTriggerFactoryBean`
* `JobDetail`：`JobDetailFactoryBean`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context 
        http://www.springframework.org/schema/context/spring-context.xsd 
        ">
  
  <!--
			Spring整合Quartz进行配置遵循下面的步骤：
			1. 定义工作任务的Job
			2. 定义触发器Trigger，并将触发器与工作任务绑定
			3. 定义调度器，并将Trigger注册到Scheduler
	-->
  <!-- 1. 定义任务的bean，这里使用JobDetailFactoryBean，也可以使用MethodInvokingJobDetailFactoryBean，配置类似-->
  <bean name="1xJob" class="org.springframework.scheduling.quartz.JobDetailFactoryBean">
    <!--指定job的名称-->
    <property name="name" value="job1"/>
    <!--指定job的分组-->
    <property name="group" value="job_group1"/>
    <!--指定具体的job类-->
    <property name="jobClass" value="com.ch.wchya.quartz.job.HelloJob"/>
  </bean>
  <!-- 2. 定义触发器的bean，定义一个Cron的Trigger，一个触发器只能和一个任务进行绑定-->
  <bean id="cronTrigger" class="org.springframework.scheduling.quartz.CronTriggerFactoryBean">
    <!--指定Trigger的名称-->
    <property name="name" value="trigger1"/>
    <!--指定Trigger的名称-->
    <property name="group" value="trigger_group1"/>
    <!--指定Trigger绑定的JobDetail-->
    <property name="jobDetail" ref="1xJob"/>
    <!--指定Cron的表达式，当前是每隔5s运行一次-->
    <property name="cronExpression" value="*/5 * * * * ?"/>
  </bean>
  <!--3. 定义调度器，并将Trigger注册到调度器中-->
  <bean id="scheduler" class="org.springframework.scheduling.quartz.SchedulerFactoryBean">
    <property name="triggers">
      <list>
        <ref bean="cronTrigger"/>
      </list>
    </property>
    <!--添加quartz配置，如下两种方式均可-->
    <!--<property name="configLocation" value="classpath:quartz.properties"/>-->
    <property name="quartzProperties">
      <value>
        # 指定高度器名称，实际类型为：QuartzScheduler
        org.quartz.scheduler.instanceName=MyScheduler
        # 指定连接池
        org.quartz.threadPool.class=org.quartz.simpl.SimpleThreadPool
				# 线程池线程数量
        org.quartz.threadPool.threadCount=10
        # 优先级，默认5
        org.quartz.threadPool.threadPriority=5
        # 非持久化job
        org.quartz.jobStore.class=org.quartz.simpl.RAMJobStore
      </value>
    </property>
  </bean>
</beans>
```

#### 4.4 操作

##### 启动任务

工厂启动，调度器启动，任务调度开始

```java
public class TestJob {

    public static void main(String[] args) {
        // 工厂启动，任务启动，工厂关闭，任务停止
        ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
    }
}
```

##### 任务操作

###### 删除任务

```java
public static void main(String[] args) throws InterruptedException,ScheduleException {
  ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
  System.out.println("==============");
  StdScheduler scheduler = (StdScheduler) context.getBean("scheduler");
  Thread.sleep(3000);
  // 删除Job
  scheduler.deleteJob(JobKey.jobKey("job1","job_group1");
}
```

###### 暂停、恢复

```java
public static void main(String[] args) throws InterruptedException,SchedulerException {
  ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
  System.out.println("==============");
  StdScheduler scheduler = (StdScheduler) context.getBean("scheduler");
  Thread.sleep(3000);
  // 暂停、恢复工作
  scheduler.pauseJob(JobKey.jobKey("job1", "job_group1"));// 暂停工作
  Thread.sleep(3000);
  scheduler.resumeJob(JobKey.jobKey("job1", "job_group1"));// 恢复工作
}
```

###### 批量操作

```java
public static void main(String[] args) throws InterruptedException,SchedulerException {
  ApplicationContext context = new ClassPathXmlApplicationContext("applicationContext.xml");
  System.out.println("==============");
  StdScheduler scheduler = (StdScheduler) context.getBean("scheduler");
  Thread.sleep(3000);
  // 暂停、恢复工作
  GroupMatcher<JobKey> group1 = GrouopMatcher.goupEquals("group1");
  scheduler.pauseJobs(group1);// 暂停组中所有工作
  Thread.sleep(2000);
  scheduler.resumeJobs(group1);// 恢复组中所有工作
} 
```

## 第三十六章 开放平台项目实战

### 1. 引言

#### 1.1 开放平台介绍

开放平台（`Open Platform`）：在软件行业和网络中，开放平台是指软件系统通过公开其应用程序编程接口（`API`）或函数（`function`）来使外部的程序可以增加该软件系统的功能或使用该软件系统的资源，而不需要更改该软件系统的源代码。在互联网时代，把网站的服务封装成一系列计算机易识别的数据接口开放出去，供第三方开发者使用，这种行为就叫做 `Open API`，提供开放 `API` 的平台本身就被称为开放平台。

#### 1.2 开放平台的使用场景

企业要调用别人的长板，通过 `API` 技术，互相调用，与行业形成链接。在借助他人长板的同时，也把自己的长板贡献给他人，这就是互相赋能。

开发平台的作用简单地说就是通过第三方的力量来扩展自己的生态和能力，因为光凭自己做的软件并不能覆盖所有的场景，例如阿里，京东可以提供标准化的应用软件，可能满足于一些小的卖家使用，但是数百万形形色色的卖家对于修改化要求的软件，并不是一个公司的力量可以满足的，所以就把这些需求开放给众多的第三方开发者。

开放平台使用广泛、几乎所有的互联网公司都有自己的开放平台，知名的如京东的宙斯（`JD Open Platform`），淘宝开放平台（`Taobao Open Platform`），百度的数据开放平台（[https://open.baidu.com](https://open.baidu.com)），大公司的开放平台都是一个完整的生态链，有很多第三方开发者（`ISV`），专门根据大的平台开放的接口，来开发出一些能用的软件，比如“E店宝”，依赖于淘宝、天猫、京东、拼多多等大型电商开放的接口，开发出的电商 `ERP` 的管理软件，通过这个 `ERP` 可以直接执行淘宝、京东等电商对外提供的功能，如查看订单、退货、上架产品等等。

[![gg5DQH.md.png](https://z3.ax1x.com/2021/05/16/gg5DQH.md.png)](https://imgtu.com/i/gg5DQH)

### 2. 管理平台

#### 2.1 管理平台介绍

管理平台主要是对开放平台中的一些数据进行综合性管理，如客户管理、应用管理、充值管理、`api` 路由管理、网关参数管理、用户 `Token` 管理、日志搜索、权限管理等，实现对服务的限流、熔断等动态配置，通过管理平台可以查看生成的数据，也可以通过管理平台将修改的数据同步到开放平台的风头系统中来实现实时更新功能

#### 2.2 客户管理

##### 介绍

客户指的是注册了开放平台并通过平台来获取响应数据的人，如我们的淘宝账号可以通过淘宝的开放平台提供的 `API` 来实现对淘宝的一些功能的调用，如订单管理、商品管理等

客户主要包含的信息：`用户名、密码、公司名称、账户余额、公司地址、账户状态` 等

客户管理主要是针对在开放平台上注册的用户进行管理，可以对用户的账号密码、企业名称、账户余额等内容进行管理，并且可以代用户进行注册、编辑、删除账户等操作

##### 数据库结构

| 列名       | 类型     | 描述               |
| ---------- | -------- | ------------------ |
| `id`       | `int`    | 主键               |
| `username` | `String` | 用户名             |
| `password` | `String` | 密码               |
| `nickname` | `String` | 公司名称           |
| `address`  | `String` | 地址               |
| `money`    | `int`    | 余额（毫）         |
| `state`    | `int`    | 状态：1正常，0停用 |

#### 2.3 应用管理

##### 介绍

应用指的是客户在我们的平台创建的应用，一个客户可以创建多个应用，比如：抖音、今日头条、火山视频都是字节跳动的产品，它们都使用了微信分享和登录这些开放功能，那么在微信的开放平台中，字节跳动就是一个客户，而抖音、今日头条都是字节跳动下面不同的应用，他们需要分别在微信开放平台创建出来才可以使用微信开放的功能

应用主要包含的信息：`所属客户、应用名称、应用的 key、应用的秘钥（签名用）、应用接收信息的回调 URL、应用对开放平台中接口的免费调用次数、应用描述` 等，关联功能为 `客户管理`

应用管理中主要包含创建应用，展示应用的相关信息，编辑修改应用，以及指删除等操作，让管理人员可以随时通过对应用的信息修改来实现动态实时的限制

##### 数据库结构

| 列名          | 类型     | 描述                             |
| ------------- | -------- | -------------------------------- |
| `id`          | `int`    | 主键                             |
| `corpName`    | `String` | 关联企业名称，冗余字段，减少查询 |
| `appName`     | `String` | 应用名称                         |
| `appKey`      | `String` | 应用唯一标示 `Key`               |
| `appSecret`   | `String` | 应用签名秘钥                     |
| `redirectUrl` | `String` | 应用回调用 `URL`                 |
| `limit`       | `int`    | 免费接口日调用限制次数           |
| `description` | `String` | 应用介绍                         |
| `cusid`       | `int`    | 关联客户 `id`                    |
| `state`       | `int`    | 状态                             |

#### 2.4 路由管理

##### 介绍

在开放平台中，因为开放的服务的数量不确定，有的服务可能今年开放的，有的服务可能是明年新开发后开放的，有的服务可能过一段时间后下线了，这一切都可能是随时变化的。因为如果每个服务都单独开发一套接口来让客户调用的话就变得非常繁琐，无法实现动态的调整。就像一个公司会有很多部门，每个部门都会招聘人，如果每个部门的抛出信息上面都写对应部门的人的话，就会变得很麻烦。我们需要在公司前台那里给每个部分留一个面试官，分浪费人员，最合适的办法是我们只要都留公司前台地址就行，我们只需要告诉前台每个部门的对接人信息就行，来面试的人员只要说明自己来面试哪个部门即可，前台会根据部门来找到对接人然后通知对接人即可，那个这个前台就是统一的入口，他记录的对接人的信息就属于跌幅信息，我们只需要和前台沟通随时变更对接人信息即可，以后多了新的部门，只要和前台说新部门的信息即可。

路由主要包含的信息：`路由的标识、对应的真正服务 id、对应服务的地址、描述信息、服务状态、幂等性、是否收费` 等

路由管理主要是对路由信息的添加、修改、启用、停用、幂等性状态修改、是否收费等进行相关管理

##### 数据库结构

| 列名             | 类型     | 描述                   |
| ---------------- | -------- | ---------------------- |
| `id`             | `int`    | 主键                   |
| `getewayApiName` | `String` | 路由名称标识           |
| `indideApiUrl`   | `String` | 服务接口地址           |
| `serviceId`      | `String` | 服务名称               |
| `description`    | `String` | 介绍信息               |
| `state`          | `int`    | 状态：1有效，0无效     |
| `idempotents`    | `int`    | 幂等性：1幂等，0非幂等 |
| `needfee`        | `int`    | 是否收费：1收费，0免费 |

#### 2.5 系统参数管理

##### 介绍

我们的所有的服务在请求之前会要求我们必须传递某些名字的参数，就像我们去一家公司面试的时候，不管面试的是什么部门都要带简历一样，这些参数我们称为系统参数

系统参数包含的主要信息：`参数名称、参数描述、参数状态`

系统参数管理主要是针对我们在网关中请求时需要的系统参数进行管理，可以动态添加或者修改删除参数，修改后同步到网关中，网关即可实现动态参数校验的功能

##### 数据库结构

| 列名          | 类型     | 描述               |
| ------------- | -------- | ------------------ |
| `id`          | `int`    | 主键               |
| `name`        | `String` | 参数名             |
| `description` | `String` | 参数介绍           |
| `state`       | `int`    | 状态：1启用，0禁用 |

#### 2.6 Token 管理

##### 介绍

我们在访问功能的时候需要登录，单体项目的时候我们可以使用 `session` 来记录数据，但是在分布式系统中，`session` 共享比较复杂，所以我们会使用其它方式来记录这些状态。我们会在用户首次登录的时候给他生成一个 `token`，下次用户带着 `token` 来，我们只需要校验即可

信息在数据库中主要的信息：`客户 id、token 内容、开始时间、过期时间` 等

`Token` 管理主要是管理用户登录后生成的 `token` 数据，修改有效期、删除等

##### 数据库结构

| 列名           | 类型       | 描述         |
| -------------- | ---------- | ------------ |
| `id`           | `int`      | 主键         |
| `userId`       | `int`      | 客户 `id`    |
| `access_token` | `String`   | `token` 内容 |
| `startTime`    | `DateTime` | 开始时间     |
| `expireTime`   | `DateTime` | 结束时间     |

#### 2.7 充值管理

##### 介绍

开放平台部分接口的访问是需要收费的，因为用户需要先充值才可以使用

充值在数据库中的主要信息：`客户 id、订单号、充值金额、日期、付费方式、状态` 等

充值管理主要是查看用户的充值记录，并且可以在自动充值出现问题的时候手动为用户充值

##### 数据库结构

| 列名          | 类型       | 描述                            |
| ------------- | ---------- | ------------------------------- |
| `id`          | `int`      | 主键                            |
| `cusId`       | `int`      | 客户 `id`                       |
| `createTime`  | `DateTime` | 创建订单时间                    |
| `updateTime`  | `DateTime` | 更新时间                        |
| `state`       | `int`      | 状态：0未支付，1已支付，2已取消 |
| `paymenttype` | `int`      | 支付类型：0银联，1微信，2支付宝 |

### 3. 技术架构

我们的项目是一个管理平台，大部分的管理平台都是对内提供功能或者给用户提供部分可选功能，所以相对起来比较简单，大部分使用的是 `SSM` 单体架构，当前的项目也采用的 `SSM` 架构

#### 3.1 架构技术点

| 技术名称    | 针对的功能 | 介绍                                     | 版本  |
| ----------- | ---------- | ---------------------------------------- | ----- |
| `SpringMVC` | 控制层     | 主要用于接收用户请求，封装参数，返回数据 | 5.1.x |
| `Spring`    | 对象管理   | 主要对项目需要的对象进行生命周期管理     | 5.1.x |
| `MyBatis`   | 持久层     | 主要是用于和数据库进行交互               | 3.5.x |
| `Quzrtz`    | 定时任务   | 比如定时备份数据                         | 1.5.x |
| `LayUI`     | 前端展示   | 用于显示页面数据，传递数据到控制层       | 2.5.x |

#### 3.2 所需工具

| 工具名称        | 功能                  | 介绍                                          |
| --------------- | --------------------- | --------------------------------------------- |
| `IntelliJ IDEA` | 代码开发              | 开发集成编辑器                                |
| `Maven`         | 项目管理              | 项目构建管理工具                              |
| `Maven Helper`  | 快速运行 `Maven` 操作 | 一款 `IDEA` 插件，可以自定义执行 `Maven` 命令 |
| `MySQL`         | 持久化数据            | 免费开源的数据库                              |
| `Tomcat`        | 运行容器              | 基于 `Java Servlet` 规范的容器                |
| `VS Code`       | 文本编辑              | 免费开源的文本编辑器                          |

### 4. 编码规范

| 名称               | 规范                                   |
| ------------------ | -------------------------------------- |
| 包名               | `com.ch.wchya.openapi`                 |
| 控制层包名         | `controller`                           |
| 服务层包名         | `service/impl`                         |
| 数据层包名         | `mapper`                               |
| 工具类包名         | `utils`                                |
| 数据库对象包名     | `entity`                               |
| `view` 对象包名    | `bean`                                 |
| `mapper.xml`       | `resources` 目录下与接口包名对应的目录 |
| `spring` 配置文件  | `resources` 下 `spring` 目录           |
| `mybatis` 配置文件 | `resources` 下 `mybatis` 目录          |
| 其它配置文件       | `resources` 下 `conf` 目录             |
| 变量名             | 驼峰命名                               |
| 状态码             | 接口中定义常量                         |
| 其它规范           | 具体情况具体定义                       |

### 5. 编码顺序

在我们的实际开发中，我们会遇到选择的问题，就是到底是先写 `controller` 还是 `service` 还是 `dao`。其实先写谁都可以，这个取决于我们自己的角度，如果你先想项目有什么业务，那么一般会先写 `service`；另外一个方面，分析出数据库的表结构后，可以先写数据库相关的操作，也就是 `dao`；也可以先想一下会和前端做什么交互，先写 `controller`。这些，完全取决于我们的角度，当然如果不是前后端分享的项目，页面也是后端编写的，也可以按照需求先把页面写出来

## 第三十七章 SSM 综合实战

### 1. 功能介绍

#### 1.1 环境搭建

`maven` 工程搭建，基于 `mysql` 数据库的商品表信息，并完成 `SSM` 整合

#### 1.2 商品查询

基于 `SSM` 整合基础上完成商品查询，要掌握主页面及商品显示页面的创建

#### 1.3 商品添加

进一步巩固 `SSM` 整合，并完成商品添加功能，要注意事务操作以及产品添加页面的生成

#### 1.4 订单查询

订单的查询操作，主要完成简单的多表查询操作，查询订单时，需要查询出与订单关联的其它表中信息，做之前要清楚订单及其它关联关系

#### 1.6 订单分页查询

分页查询，使用的是 `mybatis` 分布插件 `pageHelper`

#### 1.7 Spring Security

`Spring Security` 是 `Spring` 项目组中用来提供安全认证服务的框架，它的使用很复杂，在这个项目中，只介绍了 `Spring Security` 的基本操作，通过该项目掌握 `spring security` 框架的配置及基本的认证与授权操作

#### 1.8 用户管理

用户管理中我们会介绍基于 `Spring Security` 的用户登录、退出操作，以及用户查询、添加、详情等操作，这些功能的练习是对前期 `SSM` 知识点的进一步巩固

#### 1.9 角色管理

角色管理主要完成角色查询、角色添加

#### 1.10 资源权限管理

资源权限管理主要完成查询、添加操作，它的操作与角色管理类似，角色 管理以及资源权限管理都是对权限管理的补充

#### 1.11 权限关联与控制

用户角色关联、角色权限关联，这两个操作是为了后续完成授权操作的基础

#### 1.12 AOP 日志处理

`AOP` 日志处理，使用 `spring AOP` 切面来完成系统级别的日志收集

### 2. 数据库

#### 2.1 产品表

```sql
create table product
(
    id            int auto_increment comment '主键'
        primary key,
    productNum    varchar(50)   not null comment '产品编号，唯一',
    productName   varchar(50)   null comment '产品名称（路线名称）',
    cityName      varchar(50)   null comment '出发城市',
    DepartureTime timestamp     null comment '出发时间',
    productPrice  double(10, 2) null comment '产品价格',
    productDesc   varchar(500)  null comment '产品描述',
    productStatus int           null comment '状态（0关闭，1开启）'
);
```

#### 2.2 订单表

```sql
create table `order`
(
    id          int auto_increment comment '主键'
        primary key,
    orderNum    varchar(50)  not null comment '下单编号，不为空',
    orderTime   timestamp    null comment '下单时间',
    peopleCount int          null comment '出行人数',
    orderDesc   varchar(500) null comment '订单描述（其它信息）',
    payType     int          null comment '支付方式（0支付宝，1微信，2其它）',
    orderStatus int          null comment '订单状态（0未支付，1已支付）',
    productId   int          null comment '产品id（外键）',
    memberId    int          null comment '会员（联系人）id（外键）'
);
```

#### 2.3 会员表

```sql
create table member
(
    id       int auto_increment comment '主键'
        primary key,
    name     varchar(20) null comment '姓名',
    nickname varchar(20) null comment '昵称',
    phoneNum varchar(11) null comment '电话号码',
    email    varchar(50) null comment '邮箱'
);

insert into MEMBER (name, nickname, phonenum, email) values ('张三', '小三', '18888888888', 'zs@163.com');
```

#### 2.4 旅客表

```sql
create table traveller
(
    id              int auto_increment comment '主键'
        primary key,
    name            varchar(20) null comment '姓名',
    sex             varchar(1)  null comment '性别',
    phoneNum        varchar(11) null comment '电话号码',
    credentialsType int         null comment '证件类型：0身份证，1护照，2军官证',
    credentialsNum  varchar(50) null comment '证件号码',
    travellerType   int         null comment '旅客类型（人群）0成人，1儿童'
);

insert into TRAVELLER (name, sex, phonenum, credentialstype, credentialsnum, travellertype)
values ('张龙', '男', '13333333333', 0, '123456789009876543', 0);
insert into TRAVELLER (id, name, sex, phonenum, credentialstype, credentialsnum, travellertype)
values ('张小龙', '男', '15555555555', 0, '987654321123456789', 1);
```

#### 2.5 用户表

```sql
create table user
(
    id       int auto_increment comment '主键'
        primary key,
    email    varchar(50) not null comment '邮箱，唯一',
    username varchar(50) null comment '用户名',
    password varchar(50) null comment '密码（加密）',
    phoneNum varchar(11) null comment '电话号码',
    status   int         null comment '状态：0未开启，1开启'
);
```

#### 2.6 角色表

```sql
create table role
(
    id       int auto_increment comment '主键'
        primary key,
    roleName varchar(20)  null comment '角色名',
    roleDesc varchar(100) null comment '角色描述'
);
```

#### 2.6 资源权限表

```sql
create table resource_right
(
    id             int auto_increment comment '主键'
        primary key,
    permissionName varchar(50)  null comment '权限名',
    url            varchar(255) null comment '资源路径'
);
```

#### 2.7 日志表

```sql
create table oper_log
(
    id            int auto_increment comment '主键'
        primary key,
    visitTime     timestamp    null comment '访问时间',
    username      varchar(50)  null comment '操作者用户名',
    ip            varchar(50)  null comment '访问者ip',
    url           varchar(255) null comment '访问资源url',
    executionTime int          null comment '执行时长'
);
```





```sql
-- 用户表
create table users
(
    id       varchar(32) not null
        primary key,
    email    varchar(50) not null,
    username varchar(50) null,
    PASSWORD varchar(50) null,
    phoneNum varchar(20) null,
    STATUS   int         null,
    constraint email
        unique (email)
);

-- 角色表
create table role
(
    id       varchar(32) not null
        primary key,
    roleName varchar(50) null,
    roleDesc varchar(50) null
);


-- 用户角色关联表
create table users_role
(
    userId varchar(32) not null,
    roleId varchar(32) not null,
    primary key (userId, roleId),
    constraint fk_roleid_id
        foreign key (roleId) references role (id),
    constraint fk_userid_id
        foreign key (userId) references users (id)
);

-- 资源权限表
create table permission
(
    id             varchar(32) not null
        primary key,
    permissionName varchar(50) null,
    url            varchar(50) null
);

-- 角色权限关联表
create table role_permission
(
    permissionId varchar(32) not null,
    roleId       varchar(32) not null,
    primary key (permissionId, roleId),
    constraint fk_permissionid_id
        foreign key (permissionId) references permission (id),
    constraint fk_roleidd_id
        foreign key (roleId) references role (id)
);

-- 会员表
create table member
(
    id       varchar(32) not null comment '主键'
        primary key,
    name     varchar(20) null comment '姓名',
    nickname varchar(20) null comment '昵称',
    phoneNum varchar(20) null comment '电话号码',
    email    varchar(50) null comment '邮箱'
);

-- 订单表
create table orders
(
    id          varchar(32)  not null
        primary key,
    orderNum    varchar(20)  not null,
    orderTime   datetime     null,
    peopleCount int          null,
    orderDesc   varchar(500) null,
    payType     int          null,
    orderStatus int          null,
    productId   varchar(32)  null,
    memberId    varchar(32)  null,
    constraint orderNum
        unique (orderNum),
    constraint fk_memberid_id
        foreign key (memberId) references member (id),
    constraint fk_productid_id
        foreign key (productId) references product (id)
);

-- 订单旅客表
create table order_traveller
(
    orderId     varchar(32) not null,
    travellerId varchar(32) not null,
    primary key (orderId, travellerId),
    constraint fk_orderid_id
        foreign key (orderId) references orders (id),
    constraint fk_travellerid_id
        foreign key (travellerId) references traveller (id)
);

-- 产品表
create table product
(
    id            varchar(32) '主键'
        primary key,
    productNum    varchar(50)   not null comment '产品编号，唯一',
    productName   varchar(50)   null comment '产品名称（路线名称）',
    cityName      varchar(50)   null comment '出发城市',
    DepartureTime datetime      null comment '出发时间',
    productPrice  double(10, 2) null comment '产品价格',
    productDesc   varchar(500)  null comment '产品描述',
    productStatus int           null comment '状态（0关闭，1开启）'
);

-- 旅客表
create table traveller
(
    id              varchar(32) not null
        primary key,
    NAME            varchar(20) null,
    sex             varchar(20) null,
    phoneNum        varchar(20) null,
    credentialsType int         null,
    credentialsNum  varchar(50) null,
    travellerType   int         null
);

-- 日志表
create table oper_log
(
    id            int auto_increment comment '主键'
        primary key,
    visitTime     datetime     null comment '访问时间',
    username      varchar(50)  null comment '操作者用户名',
    ip            varchar(50)  null comment '访问者ip',
    url           varchar(255) null comment '访问资源url',
    executionTime int          null comment '执行时长'
);

```







## 第三十八章 SpringBoot

### 1. 介绍

#### 1.1 引言

* 为了使用 `SSM` 框架开发，得准备 `SSM` 框架的模板配置
* 为了 `Spring` 整合第三方框架，单独的去编写 `xml` 文件
* 导致 `SSM` 项目后期 `xml` 文件特别多，维护 `xml` 文件的成本很高
* `SSM` 工程部署也是很麻烦，依赖第三方的容器
* `SSM` 开发方式是很笨重的

#### 1.2 介绍

* `SpringBoot` 是由 `Pivotal` 团队研发的，`SpringBoot` 并不是一门新技术，只是将之前常用的 `Spring，SpringMVC，data-jpa` 等常用的框架封装到了一起，帮助你隐藏这些框架的整合细节，实现敏捷开发
* `SpringBoot` 就是一个工具集

#### 1.3 特点

* `SpringBoot` 项目不需要模板化的配置
* `SpringBoot` 中整合第三方框架时，只需要导入相应的 `starter` 依赖包，就自动整合了
* `SpringBoot` 默认只有一个 `.properties` 的配置文件，不推荐使用 `xml`，后期会采用 `.java` 的文件去编写配置信息
* `SpringBoot` 工程在部署时，采用的是 `jar` 包的方式，内部自动依赖 `Tomcat` 容器，提供了多环境的配置
* 后期要学习的微服务框架 `SpringCloud` 需要建立在 `SpringBoot` 的基础上

### 2. 快速入门

#### 2.1 快速构建 SpringBoot

##### 选择构建项目的类型

[![gXwcgP.md.png](https://z3.ax1x.com/2021/05/23/gXwcgP.md.png)](https://imgtu.com/i/gXwcgP)

##### 项目描述

[![gXwfHg.md.png](https://z3.ax1x.com/2021/05/23/gXwfHg.md.png)](https://imgtu.com/i/gXwfHg)

##### 指定 SpringBoot 的版本和需要的依赖

[![gOYA56.md.png](https://z3.ax1x.com/2021/05/23/gOYA56.md.png)](https://imgtu.com/i/gOYA56)

> 第一次创建 SpringBoot 工程时，会下载大量依赖，在创建之前确保 maven 已经配置了阿里云的私服，要不然会下载灰常慢

##### 修改 pom 配置

```xml
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter</artifactId>
</dependency>
<!--将上面的配置修改为下面的内容，就将项目改为 web 项目了-->
<dependency>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

##### 创建 Controller

```java
@RestController
public class TestController {

    @GetMapping("/test")
    public String test() {
        return "Hello SpringBoot!";
    }
}
```

##### 快速运行项目

运行 `SpringBoot` 项目自动创建的 `XXXApplication` 的 `main` 方法即可

##### 访问 Controller

在网页中输入：`http://localhost:8080/test` 即可访问

#### 2.2 SpringBoot 的目录结构

1. `pom.xml` 文件
   1. 指定了一个父工程：指定当前工程为 `SpringBoot`，帮助我们声明了 `starter` 依赖的版本
   2. 项目的元数据：包名，项目名，版本号等
   3. 指定了 `properties` 信息：指定了 `java` 的版本
   4. 导入依赖：默认情况导入 `spring-boot-starter，spring-boot-starter-test`
   5. 插件：`spring-boot-maven-plugin`

2. `.gitignore` 文件：帮助我们忽略了一些文件和目录

3. `src` 目录

   ```
   -- src
     	-- main
     		-- java
     			-- 包名
     				-- 启动类.java			# 需要将 Controller 类，放在启动类的子包中或同级包下
     		-- resources
     			-- static						# 存放静态资源
     			-- templates				# 存放模板页面
     			-- application.properties	# SpringBoot 提供的唯一配置文件
     	-- test									# 只是为了测试用
   ```

#### 2.3 SpringBoot 启动的三种方式

1. 运行启动类的 `main` 方法即可运行 `SpringBoot` 工程（开发时用）
2. 采用 `maven` 的命令去运行 `SpringBoot` 工程：`mvn spring-boot:run`
3. 采用 `jar` 包的方式运行（正式项目使用）
   1. 将当前项目打包成一个 `jar` 文件：`mvc clean package`
   2. 通过 `java -jar jar文件的全路径+名称+后缀` 的方式运行

#### 2.4 SpringBoot 配置文件

`SpringBoot` 使用一个全局的配置文件，也叫核心配置文件，配置文件名 **在约定的情况下，名字是固定的：application.xml/yml**，支持两种格式的配置文件：

* `application.properties` ：扁平的 `k/v` 格式
* `application.yml` ：树形结构
  * 基本语法：`k:(空格)v`，表示一对键值对（空格必须有）
  * 以空格的缩进来控制层级关系，只要是左对齐的一列数据，都是同一个层级的
  * 属性和值都是大小写敏感的
  * 如果有特殊字符 `% &` ，记得用单引号 `'` 包起来

> 建议使用 `yml` 格式的配置文件，因为它的可读性更强

##### 配置文件加载顺序

```xml
<includes>
  <include>**/application.yml</include>
  <include>**/application.yaml</include>
  <include>**/application*.properties</include>
</includes>
```

如果同时存在不同后缀的文件，按照上面的顺序加载主配置文件。规则：**多个不同配置文件中同时存在同一个配置时，按照优先顺序进行加载；单独出现在某个配置文件中的所有配置都会被加载**

##### 外部约定配置文件加载顺序

`SpringBoot` 启动还会扫描以下位置的 `application.yml` 文件作为 `spring boot ` 的默认配置文件（优先级从低到高）：

* `classpath` 根目录下
* `classpath` 根 `config/`
* 项目根目录
  * 如果当前项目是继承/耦合关系的 `maven` 项目的话，项目根目录=父`maven` 项目的根
* 项目根目录 `/config`
* 直接子目录 `/config` （在命令行上的输入的目录路径）

以下是官网上的内容：

1. `optional:classpath:/`
2. `optional:classpath:/config/`
3. `optional:file:./`
4. `optional:file:./config/`
5. `optional:file:./config/*/`
6. `optional:classpath:custom-config/`
7. `optional:file:./custom-config/`

### 3. SpringBoot 常用注解

#### 3.1 @Configuration 和 @Bean

之前在使用 `SSM` 开发时，在 `xml` 文件中编写 `bean` 标签，但是 `springboot` 不推荐使用 `xml`，应该如下进行配置：

```java
@Data
@NoArgsConstructor
@AllArgsConstructor
public class User {
    private int id;
    private String name;
}

@Configuration
public class UserConfig {

    @Bean
    public User user() {
        User user = new User();
        user.setId(1);
        user.setName("张三");
        return user;
    }

    /**
     * 上面的内容相关于原来在 xml 中声明以下的内容：
     * <beans ...>
     *  <bean id="user" class="com.ch.wchya.bootstudy.entity.User"/>    
     * </beans><!--部署 springboot 的插件，只有加了这个插件，当运行 javr -jar xxx.jar 才能正常启动-->
     */
}
```

* `@Configuration` 相当于 `xml` 中的 `beans` 标签
* `@Bean` 注解相当于 `bean` 标签
  * `id="方法名|注解中的name属性(优先级更高)"`
  * `class="方法的返回结果"`

##### 应用实例

```java
@RestController
public class TestController {

    @Autowired
    private User user;

    @GetMapping("/user")
    public User user() {
        return user;
    }
}
```

在浏览器中访问：`http://localhost:8080/user`，就可以看到返回的 `User` 对象

#### 3.2 @SpringBootApplication

这是一个复合注解，由以下注解组成：

* `@SpringBootConfiguration` 就是 `@Configuration` 注解，代表启动类就是一个配置
* `@EnableAutoConfiguration` 实现自动装配，`springboot` 工程启动时，运行一个 `SpringFactoriesLoader` 的类，加载 `META-INF/spring.factories` 配置类（已经开启的），以 `for` 循环的方式，一个一个加载
  * 好处：无需编写大量的整合配置信息，只需按照 `springboot` 提供好了的约定去整合即可
  * 坏处：如果说导入了一个 `starter` 依赖，就需要填写它必要的配置信息
  * 手动关闭自动装配指定内容：`@SpringBootConfiguration(exclude=QuartzAutoConfiguration.class)`
* `@ComponentScan`：扫描注解

### 4. SpringBoot 常用配置

#### 4.1 配置文件格式

`SpringBoot` 的配置文件支持 `properties` 和 `yml`，甚至他还支持 `json`。

更推荐使用 `yml` 文件格式：

优点：

* `yml` 文件，会根据换行和缩进帮助咱们管理配置文件所在位置
* `yml` 文件，相比 `properties` 更轻量级一些

劣势：

* 严格遵循换行和缩进
* 在填写 `value` 时，一定要在 `:` 后面跟上空格

#### 4.2 多环境配置

1. 在 `application.yml` 文件中添加一个配置项：

   ```yaml
   spring:
   	profiles:
   		active: 环境名
   ```

2. 在 `resources` 目录下，创建多个 `application-环境名.yml` 文件即可

3. 在部署工程时，通过 `java -jar jar文件 --spring.profiles.active=环境名` 就可以动态指定所使用的环境了

4. 使用 `spring.config.location` 动态指定配置文件位置（可以不在项目中），该方式下，配置文件里的内容是不会进行互补的

> 还可以在 bean 上使用 @Profile("环境名") 来确定某个 bean 在哪个环境下起作用，使用了访该注解后，可以定义同名的访问路径

#### 4.3 引入外部配置文件信息

和传统的 `SSM` 方式一样，通过 `@Value` 的注解去获取 `properties/yml` 文件中的内容：

```yaml
# application.yml
picPath: /Users/wchya/pictures
```

```java
@RestController
public class TestController {

    @Value("${picPath}")
    private String picPath;

    @GetMapping("/path")
    public String path() {
        return picPath;
    }
}
```

如果在 `yml` 文件中需要编写大量的自定义配置，并且具有统一的前缀时，采用如下方式：

```yaml
# application.yml
aliyun:
  xxxx: xxxxxxx
  yyyy: yyyyyyy
  zzzz: zzzzzzz
```

```java
@ConfigurationProperties(prefix = "aliyun")
@Component
@Data
public class AliyunProperties {
    private String xxxx;
    private String yyyy;
    private String zzzz;
}

@RestController
public class TestController {

    @Autowired
    private AliyunProperties properties;

    @GetMapping("/aliyun")
    public AliyunProperties aliyun() {
        return properties;
    }
}
```

#### 4.4 热加载

##### 导入依赖

```xml
<!--热部署-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-devtools</artifactId>
    <optional>true</optional>
</dependency>
```

##### 修改配置

* `Preferences -> Build,Excution,Deployment -> Compiler`，勾选 `Build project Automatically` 选项
* 按下 `command + option + shift + /` 组合键，在弹出的对话框中选择 `compiler.automake.allow.when.app.running` 并勾选

##### 大功告成

以后在项目配置修改后，就不用重启配置了

### 5. 整合 MyBatis

#### 5.1 配置文件方式整合 MyBatis

##### 导入依赖

```xml
<!--mysql-->
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
</dependency>
<!--druid-->
<dependency>
    <groupId>com.alibaba</groupId>
    <artifactId>druid-spring-boot-starter</artifactId>
    <version>1.1.22</version>
</dependency>
<!--mybatis-->
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>1.3.2</version>
</dependency>
```

##### 编写配置文件

```java
// 实体类
@Data
public class District {

  private long id;
  private String name;

}
@Data
public class Air {

  private long id;
  private long districtId;
  private java.sql.Date monitorTime;
  private long pm10;
  private long pm25;
  private String monitoringStation;
  private java.sql.Date lastModifyTime;

}
```

```java
// Mapper 接口
public interface AirMapper {
    List<Air> finaAll();
}
```

```xml
<!--resources/mapper/AirMapper.xml-->
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE mapper
        PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.ch.wchya.bootstudy.mapper.AirMapper">
    <select id="finaAll" resultType="com.ch.wchya.bootstudy.entity.Air">
        select id,districtId,monitor_time,pm10,pm25,monitoring_station,last_modify_time from air
    </select>
</mapper>
```

```java
// 在启动类中添加注解，扫描 mapper 所在接口的包
@SpringBootApplication
@MapperScan(basePackages = "com.ch.wchya.bootstudy.mapper")
public class BootstudyApplication {

    public static void main(String[] args) {
        SpringApplication.run(BootstudyApplication.class, args);
    }
}
```

```yaml
# application.yml

# MyBatis 配置信息
mybatis:
  mapper-locations: classpath:mapper/*.xml
  type-aliases-package: com.ch.wchya.bootstudy.entity
  configuration:
    map-underscore-to-camel-case: true
    
# 连接数据库配置信息
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/webmaster?useUnicode=true&characterEncoding=utf8&serverTimezone=UTC
    username: wchya
    password: Own12345
    type: com.alibaba.druid.pool.DruidDataSource
```

##### 测试

* 右击 `Mapper` 接口的类名（在 `java` 文件中），选择 `goto -> Test`，就会自动在 `test` 目录下，创建当前接口的测试类
* 还会在启动类所在的包下（`test` 目录），创建一个 `项目名ApplicationTests.java` 文件
* 修改上面 `java` 文件的修饰符为 `public`，然后让接口的测试类继承该类
* 注入 `AirMapper`，写测试方法，运行

```java
class AirMapperTest extends BootstudyApplicationTests {

    @Autowired
    private AirMapper airMapper;

    @Test
    public void test() {
        List<Air> airs = airMapper.finaAll();
        airs.forEach(System.out::println);
    }
}
```

#### 5.2 注解方式整合 MyBatis

##### 创建 Mapper 接口

```java
public interface DistrictMapper {
    List<District> findAll();
}
```

##### 添加 Mybatis 注解

```java
public interface DistrictMapper {
    @Select("select * from district")
    List<District> findAll();

    @Select("select * from district where id=#{id}")
    District findOneById(@Param("id") long id);
}
```

> 还是需要在启动类中添加 @MapperScan 注解

##### 测试

```java
class DistrictMapperTest extends BootstudyApplicationTests {

    @Autowired
    private DistrictMapper districtMapper;

    @Test
    void findAll() {
        List<District> districts = districtMapper.findAll();
        districts.forEach(System.out::println);
    }

    @Test
    void findOneById() {
        District district = districtMapper.findOneById(3);
        System.out.println(district);
    }
}
```

###### 可以看到执行的sql语句

```yaml
# MyBatis 日志输出，这句配置的意思是：将接口所在的包写成 Key，并将日志级别设置为 debug
logging:
  level:
    com.ch.wchya.bootstudy.mapper: debug
```

#### 5.3 SpringBoot 整合分页助手

##### 导入依赖

```xml
<!--pageHelper-->
<dependency>
    <groupId>com.github.pagehelper</groupId>
    <artifactId>pagehelper-spring-boot-starter</artifactId>
    <version>1.2.12</version>
</dependency>
```

##### 测试使用

```java
@Test
void findAllByPage() {
    PageHelper.startPage(0, 2);
    List<District> districts = districtMapper.findAll();
    PageInfo<District> pageInfo = new PageInfo<>(districts);
    pageInfo.getList().forEach(System.out::println);
}
```

### 6. SpringBoot 整合 JSP

#### 6.1 导入依赖

```xml
<!--jsp核心引擎依赖-->
<dependency>
    <groupId>org.apache.tomcat.embed</groupId>
    <artifactId>tomcat-embed-jasper</artifactId>
</dependency>
<!--jstl-->
<dependency>
    <groupId>javax.servlet</groupId>
    <artifactId>jstl</artifactId>
</dependency>
```

#### 6.2 创建 webapp 和 WEB-INF 目录存放 JSP 页面

[![gXTfS0.md.png](https://z3.ax1x.com/2021/05/23/gXTfS0.md.png)](https://imgtu.com/i/gXTfS0)

#### 6.3 指定前缀和后缀

```yaml
spring:
  mvc:
    view:
      prefix: /WEB-INF/
      suffix: .jsp
```

```java
@Controller
public class JspController {

    @GetMapping("/index")
    public String index(Model model) {
        model.addAttribute("name", "张三");
        return "index";
    }
}
```













## 第XX章 Boot Strap

### 环境搭建

1. 下载 `Boot Strap` 相关资料（[说明：版本为 3.3.7]()）

   1. [下载地址](https://v3.bootcss.com/getting-started/#download)

2. 下载完成后解压 `Boot Strap` 压缩包

3. 将 `Boot Strap` 文件夹全部放入项目中

4. 页面使用

   ```html
   <meta name="viewport" content="width=device-width, initial-scale=1"> <!-- 移动设备优先 -->
   <link rel="stylesheet" href="../boot/css/bootstrap.min.css">
   ```

### Boot Strap 容器

```html
<!--两边留有一定宽度的 padding-->
<div class="container" style="border: 1px red solid;"></div>
<!--战用页面 100% 的宽度-->
<div class="container-fluid" style="border: 1px red solid;"></div>

<!--注意：两种容器不能互相嵌套-->
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

## 第XX章 GUI 编程

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

[![6BdeyD.md.png](https://s3.ax1x.com/2021/03/15/6BdeyD.md.png)](https://imgtu.com/i/6BdeyD)

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

[![6BB9eg.png](https://s3.ax1x.com/2021/03/15/6BB9eg.png)](https://imgtu.com/i/6BB9eg)

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

[![6BBSOS.png](https://s3.ax1x.com/2021/03/15/6BBSOS.png)](https://imgtu.com/i/6BBSOS)

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

[![6B0vSP.png](https://s3.ax1x.com/2021/03/15/6B0vSP.png)](https://imgtu.com/i/6B0vSP)

从图中可以看出，`MenuBar` 和 `Menu` 都实现了菜单容器接口，所以 `MenuBar` 可以盛装 `Menu`，而 `Menu` 可以盛装 `MenuItem`（包括 `Menu` 和 `CheckboxMenuItem` 两个子类对象）。`Menu` 还有一个子类：`PopupMenu`，代表上下文菜单，上下文菜单无须使用 `MenuBar` 盛装。

## 第XX章 Swing

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