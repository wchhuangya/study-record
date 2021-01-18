# Java

[Toc]

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

- `TODO` ：在 `IntelliJ IDEA` 中，正常的 `TODO` 注释会被自动识别并高亮显示，在 `TODO` 窗口中也会有响应的显示，用 `TODO` 注释来标记自己待开发的任务是一项非常常见的做法

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

#### 操作符优先级（优先级从高到低，依次递减）

|    说明    |                            操作符                            |
| :--------: | :----------------------------------------------------------: |
| 一元运算符 |                      ++、--、+、-、~、!                      |
| 算术运算符 |                           *、/、%                            |
| 算术运算符 |                             +、-                             |
|  位运算符  |                         <<、>>、>>>                          |
| 关系运算符 |                   <、>、<=、>=、instanceof                   |
| 逻辑运算符 |                            ==、!=                            |
|   按位与   |                              &                               |
|  按位异或  |                              ^                               |
|   按位或   |                              \|                              |
|   逻辑与   |                              &&                              |
|   逻辑或   |                             \|\|                             |
| 三元运算符 |                              ?:                              |
| 赋值运算符 | =、+= 、-=、 *= 、/= 、%= 、&=、 ^= 、\|= 、<<=、 >>= 、>>>= |



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

1. 可以用于判断的类型：`byte、short、int、char、String（JDK7+）、枚举`
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

作业：

1. 有一个式子：$1×2×3×...×n=m$，使用程序算出当m小于5000时n最大是多少？
2. 在控制台输入五个整数，用程序算出这五个数最大值和最小值分别是多少？
3. 把区间 (100,200) 中不能被3整除的数输出，每一行输出 4 个数字。
4. 有1、2、3、4这4个数字，能组成多少个没有重复数字的三位数？打印出来
5. 使用程序计算：$ (1×1) + (1×2) + (1×2×3) + (1×2×3×4) + (1×2×3×4×5) $ 的值
6. 控制台输入一个值，根据该值在控制台上用 * 绘制四个直角等腰三角形，直角边的长度等于输入的值，这4个三角形的斜边分别在右上、左上、右下、左下

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

#### 可变参数（任意数量的参数）

```java
public void test(int nums, double... prices) {
  // 方法体
}
```

**注意：** 

* 可变参数必须是最后一个
* 可变参数是一个数组
* 可变参数可以是一个、多个、或者没有

#### 值传递 VS 地址传递

1. 简单数据类型 `VS` 复杂数据类型

    1.1 简单数据类型：`int,double,float,char,boolean`
    
    1.2 复杂数据类型：数组，对象
    
2. 简单数据类型是 **值传递**，即方法内值的改变不会影响方法外参数的值
3. 复杂数据类型是 **地址传递**，即方法内任何改变都会影响原有数据

#### 返回值与返回类型

##### 方法返回值的条件

* 完成方法中的所有语句
* 遇到 `return` 语句
* 抛出异常

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

| 数据类型              | 默认值   |
| --------------------- | -------- |
| byte                  | 0        |
| short                 | 0        |
| int                   | 0        |
| long                  | 0L       |
| float                 | 0.0f     |
| double                | 0.0d     |
| char                  | '\u0000' |
| String(or any Object) | null     |
| boolean               | false    |

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
![image-20201127084720407](/Users/wchya/own/markdown/imgs/image-20201127084720407.png)

**转义字符：**

![image-20201127084654609](/Users/wchya/own/markdown/imgs/image-20201127084654609.png)

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

```java
class Student {
    private String name;
    private int age;
    private String sex;
    
    public void setName(String name) {
        this.name = name;
    }
    
    public String getName() {
        return this.name;
    }
    
    public void setAge(int age) {
        if (age >0 && age <= 100) {
            this.age = age;
        } else {
            this.age = 18;
        }
    }
    
    public int getAge() {
        return this.age;
    }
    
    public void setSex(String sex) {
        if ("男".equals(sex) || "女".equals(sex)) {
            this.sex = sex;
        } else {
            this.sex = "男";
        }
    }
}
```

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

```java
class Animal {
    String breed;
    String name;
    
    public void sleep() {
        System.out.println("Sleeping ...");
    }
    
    public void eat() {
        System.out.println("Eating ...");
    }
}

class Dog extends Animal {
    // 就算 Dog 类中什么都不写，此时也继承了父类 Animal 中可以继承的（具体见访问修饰符表）属性和方法
}
```

**类中不可以被继承的内容**

* 构造方法
* `private` 修饰的属性和方法
* 父子类不在同一个 `package` 中，`default` 修饰的属性和方法

**访问修饰符（可见性：✓可见，✕不可见）：**

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

### 创建、使用类和对象（归纳）

一个类的声明包括：类的名称和用 `{}` 包裹起来的类体，类名称前面可以有访问修饰符。类体包含有：字段、方法和构造函数。类的字段用于保存状态信息，类的方法用于实现各种行为。构造器名称与类名称相同，结构与方法类似，但没有返回值类型，主要用来实例化一个类的新实例。

类和类成员控制访问权限的方法一样：都是通过访问修饰符（例如：`public` 等），在声明时来进行控制的。

可以在定义变量和方法时，通过添加 `static` 关键字来把变量和方法变成与类相关的变量和方法。没有使用 `static` 关键字修饰的变量和方法是与类的某个实例相关联的。类变量和类方法被类的所有实例所共享，可以通过类名直接获取。每个类实例都会有一份实例变量的拷贝，该拷贝可以通过实例引用来获取。

可以通过 `new` 操作符和构造器一起，创建一个类的对象，`new` 操作符执行完成后会返回一个指向刚刚创建对象的引用，可以把这个引用赋值给一个变量，或者直接使用它。

可以在变量和方法声明的类外部，通过一个名字，对实例变量和方法进行改变和调用，一个实例变量的限定名称类似于下面：

`objectReference.variableName`

一个方法的限定名字如下所示：

`objectReference.methodName(argumentList)`

或者

`objectReference.methodName()`

垃圾回收机制会**自动清理**不再使用的对象。如果程序再没有使用该对象的引用，那就说这个对象是没有用的。你可以通过将 `null` 值赋值给变量的方法，显式地将一个引用丢弃。

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

        Integer i3 = Integer.valueOf(100); // Integer i3 = 100;
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

可变长字符串，`JDK 1.5` 提供，运行效率快、线程不安全

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

| 字母 | 时间或日期                 | 示例 |
| ---- | -------------------------- | ---- |
| y    | 年                         | 2019 |
| M    | 年中月份                   | 08   |
| d    | 月中天数                   | 07   |
| H    | 1天中小时数（0-23）        | 23   |
| m    | 分钟                       | 23   |
| s    | 秒                         | 23   |
| S    | 毫秒                       | 832  |
| w    | 年中的周数                 | 27   |
| W    | 月中的周数                 | 3    |
| F    | 月份中的星期               | 4    |
| E    | 月份中的天数               | 22   |
| k    | 1天中的小时数（0-24）      | 24   |
| K    | `am/pm` 中的小时数（0-11） | 0    |
| h    | `am/pm` 中的小时数（1-12） | 12   |

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

## 测试与调试

### 编码公约

* 对于 `private` 的方法
  * 如果在开发过程中有用，请使用 **断言**
* 对于 `public` 的方法
  * 在方法文档中提示错误处理
  * 对于不合法的参数，抛出 `IllegalArgumentException` 异常
  * 对于为 `null` 的参数，抛出 `NullPointerExceptions` 异常
  * 如果要显式地标识，请通过返回值处理

## 简单 Java 类

在以后进行项目的开发与设计的过程中，简单 `Java` 类都将作为一个重要的组成部分存在，慢慢接触到正规的项目设计之后，简单 `Java` 类无处不在，并且有可能会产生一系列的变化。

所谓的简单 `Java` 类指的是可以描述某一类信息的程序类，例如：描述一个人、描述一本书、描述一个部门、描述一个部员，并且在这个类之后并没有特别复杂的逻辑操作，只作为一种信息存储的媒介存在。

对于简单 `Java` 类而言，其核心的开发结构如下（未完成，后面有补充）：

* 类名一定要有意义，可以明确的描述一类的事物
* 类之中的所有属性都必须使用 `private` 进行封装，同时封装后的属性必须要提供有 `getter`、`setter` 方法
* 类之中可以提供有无数多个构造方法，但是必须要保留有无参构造方法
* 类之中不允许出现任何的输出语句，所有的内容的获取必须返回
* 【非必须】可以提供有一个获取对象详细信息的方法，暂时将此方法名称定义为 `getInfo`

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

| 值         | 格式                                                      | 输出        | 解释                                                         |
| ---------- | --------------------------------------------------------- | ----------- | ------------------------------------------------------------ |
| 123456.789 | ![](index_files/611dc453-3a19-4989-89c4-daae9fdcefa2.png) | 123,456.789 | # 表示一个数字，逗号是分组分隔符的占位符，句号是小数点分隔符的占位符 |
| 123456.789 | ![](index_files/9bd0fce7-afc8-4462-a53d-48e407539161.png) | 123456.79   | 该值在小数点右边有三位数，但是在格式中只有两位，`format` 通过四舍五入来解决该问题 |
| 123.78     | 000000.000                                                | 000123.780  | 该模式指定前导零和尾随零，因为使用0字符代替了井号（＃）      |
| 12345.67   | ![](index_files/72b9a82d-48fc-4e91-85f2-2f25c8630dc5.png) | $12,345.67  | 模式中的第一个字符是美元符号($)。注意，在格式化输出中，它紧接在最左边的数字前面。 |

## 第十六章 集合框架

### 集合

对象的容器，定义了对多个对象进行操作的常用方法。可实现数组的功能

#### 和数组的区别

* 数组固定长度，集合长度不固定
* 数组可以存储基本类型和引用类型，集合只能存储引用类型

#### 位置

集合相关的类都位于 `java.util` 包下

### Collection体系集合

![image-20210104122611180](/Users/wchya/own/markdown/imgs/image-20210104122611180.png)

#### Collection 父接口

代表一组任意类型的对象，无序、无下标、不能重复

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

#### 集合的问题

1. 集合对元素类型没有任何限制
2. 从集合取出的元素都是 `Object` 类型的，可能在使用时会引发 `ClassCastException` 异常

##### 错误举例

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
* `T` 可以换为任意一个大写字母，一般使用的有：`T（Type）`、`E（Element）`、`K（Key）`、`V（Value）`

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

