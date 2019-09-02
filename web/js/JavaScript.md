# JavaScript 基础

> JavaScript 程序是用 Unidoce 字符集编写的。ECMAScript5 要求支持 Unicode3 及后续版本

## 1. 如何写一段 JS 代码并运行

### 1.1 行内
```html
<input type="button" value="按钮" onclick="alert('Hello World')" >
```
### 1.2 标签内
```html
<script>
	alert(345);
</script>
```
### 1.3 JS 文件引用
```html
<script src="./tool.js"></script>
```

## 2. 词法结构

### 2.1 字符集

> JavaScript 区分大小写

#### 2.1.1 表示空格的字符

| Unicode 编码 | 含义       |
| ------------ | ---------- |
| \u0020       | 空格符     |
| \u0009       | 水平制表符 |
| \u000B       | 垂直制表符 |
| \u000C       | 换页符     |
| \u00A0       | 不中断空白 |
| \uFEFF       | 字节序标记 |

#### 2.1.2 行结束符

| Unicode 编码 | 含义     |
| ------------ | -------- |
| \u000A       | 换行符   |
| \u000D       | 回车符   |
| \u2028       | 行分隔符 |
| \u2029       | 段分隔符 |

> 回车符加换行符在一起被解析为一个单行结束符

#### 2.1.3 Unicode 转义

1. 为了支持使用老旧技术的程序员，JavaScript 定义了一种特殊序列，使用 6 个 ASCII 字符来代表任意 16 位 Unicode 内码。这些 Unicode 转义序列均以 \u 为前缀，其后跟 4 个十六进制数
2. 这种 Unicode 转义写法可以用在 JavaScript **字符串直接量**、**正则表达式直接量**、**标示符**（关键字除外）中

### 2.2 直接量

程序中直接使用的数据值

### 2.3 标示符和保留字

#### 2.3.1 标识符

1. 就是一个名字，用来对变量和函数进行命名，或者用做代码中某些循环语句中的跳转位置的标记
2. 必须以字母、下划线、美元符开始，后续的字符可以是字母、数字、下划线或美元符

> 数字是不允许作为首字符出现的，以便 JavaScript 可以轻易区分开标识符和数字

#### 2.3.2 保留字

| break    | delete  | function   | return | typeof |
| -------- | ------- | ---------- | ------ | ------ |
| case     | do      | if         | switch | var    |
| catch    | else    | in         | this   | void   |
| continue | false   | Instanceof | throw  | while  |
| debugger | finally | new        | true   | with   |
| default  | for     | Null       | try    |        |

#### 2.3.3 关键字

| class  | const | enum | export | extends |
| ------ | ----- | ---- | ------ | ------- |
| import | super |      |        |         |

### 2.4 不能换行的情况

1. return、break、continue 和随后的表达式之间不能有换行
2. ++、-- 运算符和随后的表达式之间不能有换行

## 3. 类型、值和变量

### 3.1 数字

1. JavaScript 中的所有数字均由浮点数值表示

> 由于某些 JavaScript 的实现支持八进制直接量，而有些不支持，因此最好不要使用以 0 为前缀的整形直接量。在 EMCAScript6 的严格模式下，八进制直接量是明令禁止的

### 3.2 算术运算

1. **溢出**：当数字运算结果超过了 JavaScript 所能表示的数字上限，结果为一个无穷大的值 Infinity；当负数的值超过了 JavaScript 所能表示的负数范围，结果为负无穷大 -Infinity
   1. 基于无穷大的加、减、乘、除还是无穷大（结果保留正负号）
   2. 
2. **下溢**：当运算结果无限接近于 0 并比 JavaScript 能表示的最小值还小的时候发生的一种情形
   1. 正数发生下溢，返回 0
   2. 负数发生下溢，返回 -0
   3. 0 与 -0 想等
3. **非数字值**：不是或不能转换为数字的值，用 NaN 表示
   1. 它和任何值都不想等，包括自身
   2. **判断方法**：x != x，该表达式只有当 x 为 NaN 时才为真，其余情况都为假

### 3.3 文本

1. 字符串是一组由 16 位值（2 个字节）组成的不可变的有序序列
2. 字符串的索引从 0 开始
3. 字符串是固定不变的

#### 3.3.1 字符串直接量

1. 由单引号或双引号括起来的字符序列
2. 可以拆分成数行，每行必须以反斜线（\）结束，反斜线和行结束符都不算是字符串直接量的内容（ECMAScropt5 中可用）

#### 3.3.2 转义字符

[转义符](#zyf)

## 2. 变量

变量就是存储数据的容器。
### 2.1 什么是变量
变量是计算机内存中存储数据的标识符，根据变量名称可以获取到内存中存储的数据
### 2.2 为什么要使用变量
使用变量可以方便的获取或修改内存中的数据

### 2.3 如何使用变量

> 声明一个变量，但未给变量赋值时，变量的值是 undifined

* var 声明变量

  ```javascript
  var age;
  var i, sum;
  var message = 'hello', i = 0, j = 0;
  ```

* 变量的赋值

  ```javascript
  var age;
  age = 18;
  ```

* 同时声明多个变量

  ```javascript
  var age, name, sex;
  age = 10;
  name = 'zs';
  ```

* 同时声明多个变量并赋值

  ```javascript
  var age = 10, name = 'zs';
  ```

### 2.4 变量的全名规则和规范

* 规则：必须遵守，不遵守会报错
  * 由字母、数字、下划线（_）、$符号组成，且不能以数字开头
  * 不能是关键字和保留字，例如：for，while 等

### 2.5 案例

1. 交换两个变量的值

   ```javascript
   var a = '1', b = '2';
   // 借助第三个变量
   var c = a;
   a = b;
   b = c;
   console.log(a, b);
   ```

2. 不使用临时变量，交换两个数值变量的值

   ```javascript
   var num1 = 10, num2 = 20;
   num1 = num1 + num2;
   num2 = num1 - num2;
   num1 = num1 - num2;
   console.log(num1);
   console.log(num2);
   ```

### 2.6 数据类型

#### 2.6.1 简单数据类型

数字、字符串、true、false、undefined、null

> 1. 以上五种也被称为：原始值
> 2. 原始值不可改变
> 3. 原始值的比较是值的比较：只有在它们的值相等时

##### 2.6.1.1 获取变量的类型

**typeof**

```javascript
var age = 18;
console.log(typeof(age)); // 'number'
```

##### 2.6.1.2 Number 类型

* 数值字面量：数值的固定值的表示法，例如：110，1024，60.5
* 浮点数
  * 浮点数可以使用科学计数法表示，例如：` var n = 5e-324  ` 表示的是 $ 5 × 10^{-324} $ 
  * 最高精度 17 位小数，在算数计算时数度远不如整数，例如：`var res = 0.1 + 0.2;` 该结果等于 0.30000000000000004，而不等于 0.3
  * **不要判断两个浮点是否相等** 

* 数值范围
  * 最小值：`Number.MIN_VALUE` 该值为： $ 5 × 10^{-324} $ 
  * 最大值：`Number.MAX_VALUE` 该值为：1.7976931348623157e+308
  * 无穷大：`Infinity`
  * 无穷小：`-Infinity`

##### 2.6.1.3 String 类型

* 字符字面量：'abc'，"abc"
* <span id="#zyf">转义符</span> 

| 字面量 | 含义                                                         |
| :----: | :----------------------------------------------------------- |
|   \n   | 换行                                                         |
|   \t   | 制表                                                         |
|   \b   | 空格                                                         |
|   \r   | 回车                                                         |
|   \v   | 垂直制表符                                                   |
|   \f   | 进纸，换页符                                                 |
|  \\\\  | 斜杠                                                         |
|  \\'   | 单引号，在单引号表示的字符串中使用                           |
|  \\"   | 双引号，在双引号表示的字符串中使用                           |
|  \xnn  | 以十六进制代码 nn 表示的一个字符（其中 n 为 0~F），例如：\x41 表示 'A' |
| \unnnn | 以十六进制代码 nnnn 表示的一个 Unicode 字符（其中 n 为 0~F），例如：\u03a3 表示希腊字符 $ \Sigma $ |

* 字符长度：length 属性用来获取字符串的长度
* 字符串拼接：使用 + 号
  * \+ 号两边只要有一个是字符串，那么 \+ 号就是字符串拼接功能
  * \+ 号两边都是数字，那 \+ 就是算术功能

##### 2.6.1.4 Boolean 功能

* 字面量：true、false，区分大小写
* 计算机内部存储：true 为 1，false 为 0

##### 2.6.1.5 Undefined 和 Null

* undefined 表示一个声明了但没有赋值的变量，变量只有声明时值默认是 undefined
* null 表示空，变量的值如果想为 null，必须手动设置

#### 2.6.2 复杂数据类型

Object

> 在谷歌浏览器中：
>
> 1. **字符串的颜色是黑色**
> 2. **数值类型是蓝色**
> 3. **布尔类型是蓝色**
> 4. **undefined 和 null 是灰色**

### 2.7 注释

* 行内注释：// 注释的内容，不能换行
* 整块注释：/* 注释的内容 */，可以换行

## 3. 数据类型转换

| 值                  | 转换为      |      |        |                       |
| ------------------- | ----------- | ---- | ------ | --------------------- |
|                     | 字符串      | 数字 | 布尔值 | 对象                  |
| undefinded          | "undefined" | NaN  | false  | throws TypeError      |
| null                | "null"      | 0    | false  | throws TypeError      |
| true                | "true"      | 1    |        | new Boolean(true)     |
| false               | "false"     | 0    |        | new Boolean(false)    |
| ""（空字符串）      |             | 0    | false  | new String("")        |
| "1.2"(非空，数字)   |             |      | true   | new String("1.2")     |
| "one"(非空，非数字) |             | NaN  | true   | new String("one")     |
| 0                   | "0"         |      | false  | new Number(0)         |
| -0                  | "0"         |      | false  | new Number(-0)        |
| NaN                 | "NaN"       |      | false  | new Number(NaN)       |
| Infinity            | "Infinity"  |      | true   | new Number(Infinity)  |
| -Infinity           | "-Infinity" |      | true   | new Number(-Infinity) |
| 1(无穷大，非零)     | "1"         |      | true   | new Number(1)         |

### 3.1 转换为字符串类型

* toString()

  ```javascript
  var num = 5;
  console.log(num.toString());
  ```

* String()

  ```javascript
  var s = null;
  console.log(String(s));
  ```

  > String() 函数存在的意义：有些值没有 toString() 方法（比如 null，undefined）

* 字符串拼接

  当 \+ 号两边一个操作符是字符串类型，一个操作符是其它类型的时候，会先把其它类型转换成字符串再进行字符串拼接，返回字符串
  
* 对象转换为字符串

  1. 如果对象具有 toString() 方法，则调用这个方法。如果他返回一个原始值，JavaScript 将这个值转化为字符串，并返回这个字符串结果
  2. 如果对象没有 toString() 方法，或者这个方法并不返回一个原始值，那么 JavaScript() 会调用 valueOf() 方法（如果存在该方法的话）。如果返回值是原始值，则将这个值转化为字符串并返回
  3. 否则，JavaScript 无法从 toString() 或 valueOf() 获得一个原始值，因此这时它将抛出一个类型错误异常

### 3.2 转换为数值类型

* Number()：只能对真正的数字进行转换，会把 null 转换为0，其余的都是 NaN

  ```javascript
  var a = 'ab', b = '1.2', c = '1.2.3.4', d = '1.3db', e = null, f = undefined;
  console.log(Number(a), Number(b), Number(c), Number(d), Number(e), Number(f));
  // 最终结果： NaN 1.2 NaN NaN 0 NaN
  ```

* parseInt()：会从左到右对值进行处理，如果一开始就不是数字，将输出 NaN；如果一开始是数字，就会把能转为整数的部分进行输出

  ```javascript
  var a = 'ab2', b = '1.2', c = '1.2.3.4', d = '1.3db', e = null, f = undefined;
  console.log(parseInt(a), parseInt(b), parseInt(c), parseInt(d), parseInt(e), parseInt(f));
  // 最终结果：NaN 1 1 1 NaN NaN
  ```

* parseFloat()：会从左到右对值进行处理，如果一开始就不是数字，将输出 NaN；如果一开始是数字，就会把能转为浮点数的部分进行输出

  ```javascript
  var a = 'ab2', b = '1.2', c = '1.2.3.4', d = '1.3db', e = null, f = undefined;
  console.log(parseFloat(a), parseFloat(b), parseFloat(c), parseFloat(d), parseFloat(e), parseFloat(f));
  // 最终结果： NaN 1.2 1.2 1.3 NaN NaN
  ```
  
* 对象转数字

  1. 如果对象具有 valueOf() 方法，后者返回一个原始值，则 JavaScript 将这个原始值转换为数字（如果需要的话）并返回这个数字
  2. 否则，如果对象具有 toString() 方法，后者返回一个原始值，则 JavaScript 将其转换并返回
  3. 否则，JavaScript 抛出一个类型错误异常

### 3.3 转换为布尔类型

* Boolean()

  ```javascript
  var a = Boolean('a'), b = Boolean(0), c = Boolean('2'), d = Boolean(null), e = Boolean(undefined), f = Boolean(''), g = Boolean(' ');
  console.log(a, b, c, d, e, f, g);
  // 最终结果：true false true false false false true
  ```

### 3.4 特殊的转换

* "+" 运算符可以进行数学加法和字符串连接操作。如果它的其中一个操作数是对象，则 JavaScript 将使用特殊的方法将对象转换为原始值，而不是使用其他算术运算符的方法执行对象到数字的转换
* "==" 相等运算符与 "+" 类似。如果将对象和一个原始值比较，则转换将会遵循对象到原始值的转换方式进行

## 4. 操作符

* 表达式：值和操作符，运算会有一个结果
* 表达式中的每个数值及部分表达式，又称为子表达式

![image-20190822215920221](/Users/wchya/own/markdown/imgs/image-20190822215920221.png)

### 4.1 算术运算符

```javascript
+ - * / %
```

### 4.2 一元运算符

只有一个操作数的运算符，它会直接修改原始变量的数据

```javascript
++ 自身加1（自增）
-- 自身减1（自减）
```

> 注意：一元操作符在变量前面，先进行自身的运算，再进行其它运算；；

> 注意：
>
> 1. 一元运算符在变量的前面，先进行自身运算，再进行其它运算
> 2. 一元运算符在变量的后面，先进行其它运算，再进行自身运算

### 4.3 逻辑运算符（布尔运算符）

```javascript
&& 与  两个操作数同时为 true，结果为 true，否则为 false
|| 或  两个操作数只要有一个为 true，结果为 true，否则为 false
!  非  取反
```

### 4.4 关系运算符

```javascript
<  >  <=  >=  ==  !=  ===  !==
```

> == 和 === 的区别：
>
> == 只比较值是否相等，=== 除了比较值，还比较类型是否相等

### 4.5 赋值运算符

注意与数学符号的差别

```javascript
=    +=   -=    /=    *=     %=
```

### 4.4 运算符优先级

> 左值：left value，简称 lval，指表达式只能出现在赋值运算符的左侧

优先级按照从高到低的顺序依次是：

1. () 优先级最高
2. 一元运算符：++   --   !
3. 算术运算符：先 *   /    %，后 +   -
4. 关系运算符：>    >=      <   <=
5. 相等运算符：==  !=   \===   !==
6. 逻辑运算符：先   &&   后    ||
7. 赋值运算符：=    +=   -=    /=    *=     %=

全量运算符表格

| 运算符                                                       | 操作                               | 结合性：<br />从左至右：L；从右至左：R | 结合性： | 期望操作数类型→结果类型 |
| ------------------------------------------------------------ | ---------------------------------- | -------------------------------------- | -------- | ----------------------- |
| ++                                                           | 前/后增量                          | R                                      | 1        | lval→num                |
| --                                                           | 前/后减量                          | R                                      | 1        | lval→num                |
| -                                                            | 求反                               | R                                      | 1        | num→num                 |
| +                                                            | 转换为数字                         | R                                      | 1        | num→num                 |
| ~                                                            | 按位求反                           | R                                      | 1        | int→int                 |
| !                                                            | 逻辑非                             | R                                      | 1        | bool→bool               |
| delete                                                       | 删除属性                           | R                                      | 1        | lval→bool               |
| typeof                                                       | 检测操作数类型                     | R                                      | 1        | any→str                 |
| void                                                         | 返回 undefined 值                  | R                                      | 1        | any→undef               |
| *、/、%                                                      | 乘、除、求余                       | L                                      | 2        | num,num→num             |
| +，-                                                         | 加，减                             | L                                      | 2        | num,num→num             |
| +                                                            | 字符串连接                         | L                                      | 2        | str,str→str             |
| <<                                                           | 左移位                             | L                                      | 2        | int,int→int             |
| \>\>                                                         | 有符号右移                         | L                                      | 2        | int,int→int             |
| <<<                                                          | 无符号左移                         | L                                      | 2        | int,int→int             |
| <，<=，>，>=                                                 | 比较数字顺序                       | L                                      | 2        | num,num→bool            |
| <，<=，>，>=                                                 | 比较在字母表中的顺序               | L                                      | 2        | str,str→bool            |
| instanceof                                                   | 测试对象类                         | L                                      | 2        | obj,func→bool           |
| in                                                           | 测试属性是否存在                   | L                                      | 2        | str,obj→bool            |
| ==                                                           | 判断相等                           | L                                      | 2        | any,any→bool            |
| !=                                                           | 判断不等                           | L                                      | 2        | any,any→bool            |
| ===                                                          | 判断恒等                           | L                                      | 2        | any,any→bool            |
| !==                                                          | 判断非恒等                         | L                                      | 2        | any,any→bool            |
| &                                                            | 按位与                             | L                                      | 2        | int,int→int             |
| ^                                                            | 按位异或                           | L                                      | 2        | int,int→int             |
| \|                                                           | 按位或                             | L                                      | 2        | int,int→int             |
| &&                                                           | 逻辑与                             | L                                      | 2        | any,any→any             |
| \|\|                                                         | 逻辑或                             | L                                      | 2        | any,any→any             |
| ?:                                                           | 条件运算符                         | R                                      |          |                         |
|                                                              | 变量赋值或对象属性赋值             | R                                      |          | lval,any→any            |
| *=，/=，%=，<br />+=，-=，&=，^=，<br />\|=，<<=，>>=，<br />>>>= | 运算且赋值                         | R                                      | 2        | lval,any→any            |
| ,                                                            | 忽略第一个操作数，返回第二个操作数 | L                                      | 2        | any,any→any             |

### 4.5 加法运算符

* 如果其中一个操作数是对象，则对象会遵循对象到原始值的转换规则转换为原始类值：日期对象通过 toString() 方法执行转换，其他对象则通过 valueOf() 方法执行转换。由于多数对象都不具备可用的 valueOf() 方法，因此他们会通过 toString() 方法来执行转换
* 在进行了对象到原始值的转换后，如果其中一个操作数是字符串的话，另一个操作数也会转换为字符串，然后进行字符串连接
* 否则，两个操作数都将转换为数字（或者 NaN），然后进行加法操作

## 5. 流程控制

程序的三种基本结构：

1. 顺序结构：从上到下执行的代码就是顺序结构，程序默认就是从上到下顺序执行的
2. 分支结构：根据不同的情况及判断，执行相应代码
3. 循环结构：重复执行一段代码

### 5.1 分支结构

#### 5.1.1 if 语句

```javascript
if (/* 条件表达式 */) {
	// 条件成立执行语句    
} else if (/* 条件表达式 */) {
  // 条件成立执行语句    
} else {
  // 以上条件都不成立执行语句
}   
```

> 可以写全，也可以只写其中的一部分，比如只写 if，只写 if ... else ...  等

#### 5.1.2 三元运算符

```javascript
表达式1 ? 表达式2 : 表达式3
```

1. 三元运算符的意思是：如果表达式 1 的运算结果为真，运算结果就是表达式 2 的值，如果为假，运算结果就是表达式 3 的值
2. 它是 ` if...else.. ` 的一种简化写法

#### 5.1.3 switch 语句

语法格式

``` javascript
switch (expression) {
  case 常量1:
    语句1;
    break;
  case 常量2:
    语句2;
    break;
  ...
  case 常量n:
    语句n；
    break;
  default:
    语句;
    break;
}
/**
* 执行过程：
* 获取表达式的值，和常量1比较，相同则执行语句1，遇到break跳出整个语句，结束
* 如果和常量1不匹配，则和值2比较，相同则执行代码2，遇到break跳出整个语句，结束
* 以后的执行都与上面的执行过程一样
* 如果和 case 中的常量都不匹配，则直接执行 default 中的语句，结束
**/
```

> 1. break 可以省略，如果省略，继续执行下一个 case/default
> 2. switch 在比较值时，使用的是全等操作符（===），因此不会发生类型转换（例如，字符 '10' 不等于数值 10）

### 5.2 循环结构

> 在 js 中，有三种循环：while, do..whild, for

#### 5.2.1 whild 语句

基本语法 

```javascript
// 当循环条件为 true 时，执行循环体。每次执行循环体之前，都要对循环条件进行重新判断，直到条件不成立，结束循环
// 当循环条件为 false 时，结束循环
while (循环条件) {
  // 循环体
}
```

#### 5.2.2 do..while 循环

基本语法

```javascript
do {
  // 循环体
} while (循环条件)
```

> 1. do..while 和 while 非常像，两者可以相互替代
> 2. do..whild 的特点是：不管条件是否成立，循环体都会执行一次

#### 5.2.3 for 循环

> while 和 do..while 一般用于无法确定次数的循环，for 一般在处理确定次数的循环时比较方便

基本语法

```javascript
for (初始化表达式1; 判断表达式2; 自变表达式3) {
  // 循环体
}
```

执行顺序：（直到判断表达式的结果为 false）

1. 初始化表达式
2. 判断表达式
3. 自变表达式
4. 循环体

#### continue 和 break

1. break：立刻跳出整个循环，即循环结束，开始执行循环后面的内容
2. continue：立即跳出当前循环，继续执行下一次循环

> 总结：
>
> 1. 代码的执行流程分为：顺序、分支、循环
> 2. 默认是顺序结构
> 3. 判断结构主要有：if..else，switch..case 两种
> 4. 循环结构主要有：while，do..while，for 三种
>    1. continue 和 break 用于跳出循环，注意它俩的区别

## 6. JS 中特殊的对象：数组

所谓数组，就是将多个元素（通常是同一类型）按一定顺序排列放到一个集合中，那么这个集合我们就称之为数组。

### 6.1 数组的创建

1. 字面量创建：

   ```javascript
   var a = []; // 空数组
   var b = [1, '2']; // 两个元素的数组
   ```

2. 构造函数创建：

   ```javascript
   var a = new Array(1, 'n', 3, 'k');
   ```

### 6.2 获取数组元素

使用：数组名[下标] 的方式获取数组元素的值，序号从 0 开始

```javascript
var arr = [1, 2, 3, 4];
console.log(arr[3]); // 打印出 4
```

## 7. 函数

定义：把一段相对独立的具有特定功能的代码块封装起来，形成一个独立实体，就是函数，起个名字（函数名），在后续开发中可以反复调用

### 7.1 函数的声明及调用

#### 7.1.1 声明

* 关键字声明

  ```javascript
  function 函数名() {
    // 函数体
  }
  ```

* 表达式声明

  ```javascript
  var f(函数名) = function() {
    
  }
  ```

> 注意：函数无论以哪种方式声明，里面的代码都不会被执行的，函数必须被调用，里面的代码才会被执行

#### 7.1.2 调用

调用方法：函数名()

> 调用一次，函数体就执行一次；一个函数可以被调用多次

### 7.2 参数

语法

```javascript
// 函数内部是一个封闭的环境，可以通过参数的方式，把外部的值传递给函数内部
// 带形参的函数声明
function 函数名(形参1, 形参2, 形参...) {
  // 函数体
}

// 带参数的函数调用
函数名(实参1, 实参2, 实参...);
```

**形参和实参**

1. 形式参数：在声明一个函数的时候，为了函数的功能更加灵活，有些值是固定不了的，对于这些固定不了的值，我们可以给函数设置参数。这个参数没有具体的值，仅仅起到一个占位置的作用，我们通常称之为形势参数，也叫形参
2. 实际参数：如果函数在声明时，设置了形参，那么在函数调用的时候就需要传入对应的参数，我们把传入的参数叫做实际参数，也叫实参

```javascript
function fn(a, b) {
  console.log(a + b);
}
var x = 5, y = 6;
fn(x, y);
// x,y 为实参，有具体的值
// 函数执行的时候会把 x，y 的值复制一份给函数内部的 a 和 b
// 函数内部的值是复制的新值，无法修改外部的 x、y 的值
```

> JS 在函数调用时，允许多传实参，就是实参个数可以比形参个数多

### 7.3 函数的返回值

> 当函数执行完时，并不是所有的时候都要把结果打印。我们期望函数给我们一些反馈（比如计算的结果返回进行后续的运算），这个时候可以让函数返回一些东西，也就是返回值。函数通过 return 返回一个值

语法：

```javascript
function f(形参, 形参) {
  // 代码
  // return 返回值
}

var res = f(实参, 实参);
```

> 1. 如果函数没有 return 语句，那么函数执行完成后接收到的返回值就是 undefined
> 2. 如果 return 之后什么值都没有写，函数执行害怕后接收到的返回值也是 undefined
> 3. 函数 return 之后的代码都将不再执行，函数调用结束

### 7.4 函数相关的其它事情

#### 7.4.1 匿名函数与自调用函数

> 匿名函数：没有名称的函数

 使用方法：将匿名函数赋值给一个变量，这样就可以通过变量进行调用

```javascript
var fun1 = function() {
  console.log(1);
}
fun1();
```

> 匿名函数如果没有任何变量来表示它，那么就不能直接调用来执行，因此可以通过匿名函数自调用的方式来执行

```javascript
(function() {
  alert(123);
})();
```

自执行函数（匿名函数自调用）的意义：防止全局变量污染。

#### 7.4.2 函数本身也是值

1. 回调

   ```javascript
   function f1(s) {
     var k = 123 + s;
     console.log(k);
     s();
   }
   
   var f2 = function() {
     console.log(222);
   }
   
   f1(f2);
   
   /* 打印结果：
      123function() {
      console.log(222);
      }
      222                      */
   ```

2. 闭包

   ```javascript
   function f1() {
     var a = 10;
     var f2 = function() {
       alert(2);
     }
     return f2;
   }
   
   var k = f1();
   k();
   ```

## 8. 作用域与 JS 代码的运行

> 作用域：变量可以起作用的范围和区域

### 8.1 全局变量和局部变量

* 全局变量与全局作用域

  在任何地方都可以访问的变量就是**全局变量**，全局变量所在的区域就是**全局作用域**

* 局部变量

  只在固定的代码片断内可访问到的变量，最常见的例如函数内部的变量，就是**局部变量**，局部变量所在的区域就是局部作用域（函数作用域）

> 1. 不使用 var 声明的变量是全局变量，不推荐使用
> 2. 变量退出作用域之后会销毁
> 3. 全局变量关闭网页或浏览器才会销毁

### 8.2 变量提升

```javascript
console.log(a); // undefined
var a = 2;
```

```javascript
console.log(a); // 控制台中会报一个 JS 脚本错误：a is not undefined
```

也就是说：在代码执行之前，变量已经在编译阶段就被声明了

### 8.3 变量作用域

1. 如果函数名与变量名相同，那么，函数声明将覆盖变量声明（不论先后）

### 8.4 词法作用域

1. 函数内部可以访问函数外部的变量，但是函数外部不可以访问函数内部的变量
2. 函数内部如果有变量，则优先使用内部的变量，如果函数内部没有，都会使用外部的变量

### 8.5 作用域链

1. 只有函数可以制造作用域，那么只要是代码，就至少有一个作用域，即全局作用域，凡是代码中有函数，那个这个函数就构成另外一个作用域，如果函数中还有函数，那么这个作用域中就又可以诞生一个作用域。
2. 将这样的所有的作用域列出来，可以有一个结构：函数内指向函数外的链式结构，就称作作用域链。
3. 当函数中使用某个变量时，优先在自己的作用域中查找；如果找不到，就会向上一层作用域中查找，……，一直向上查找，直到全局作用域，全局作用域还找不到就报错。这就是作用域链

## 9. 对象（Object）

### 三类对象、两类属性

* 内置对象（native object）：是由 ECMAScript 规范定义的对象或类。例如，数组、函数、日期和正则表达式都是内置对象
* 宿主对象（host object）：是由 JavavScript 解释器所嵌入的宿主环境（比如 Web 浏览器）定义的。客户端 JavaScript 中表示网页结构的 HTMLElement 对象均是宿主对象。既然宿主环境定义的方法可以当成普通的 JavaScript 函数对象，那么宿主对象也可以当成内置对象
* 自定义对象（user-defined object）：是由运行中的 JavaScript 代码创建的对象
* 自有属性（own property）：直接在对象中定义的属性
* 继承属性（inherited property）：在对象的原型对象中定义的属性

### 创建对象

* 对象直接量：若干键/值对组成的映射表，键/值对中间用冒号分隔，键值对之间用逗号分隔，整个用花括号括起来
  * 属性名可以是 JavaScript 标识符也可以是字符串直接量（包括空字符串）
  * 表达式的值可以是原始值也可以是对象
  * 对象直接量是一个表达式，这个表达式的每一次运算都创建并初始化一个**新的对象**；每次计算时，也都会重新计算**每个属性的值**
  * 都有同一个原型对象：Object.prototype
* 通过 new 创建对象：关键字 new 后跟随一个函数（构造函数）调用，构造函数用以初始化一个新创建的函数
  * 都有同一个原型对象：Object.prototype，通过 new Array() 创建的对象原型就是 Array.prototype，依次类推
* 原型：每一个 JavaScript 对象（null 除外）都和另一个对象相关联，即和原型相关联，每一个对象都从原型继承属性
* Object.create()：创建一个新对象，其中第一个参数就是这个对象的原型
  * 传入 null 来创建一个没有原型的对象，但这种方式创建的对象不会继承任何东西，甚至不包括基础方法
  * 传入 Object.prototype 来创建一个普通的空对象

### 9.1 什么是对象

**万物皆对象**

```javascript
现实生活中，万物皆对象，对象是一个具体的事物，一个具体的事物就会有行为和特征。
举例：一部车，一个手机
车是一类事务，门口停的那辆车才是对象
		特征：红色，四个轮子
    行为：驾驶，刹车
```

### 9.2 JavaScript 中的对象

```javascript
JavaScript 中的对象其实就是生活中对象的抽象
JavaScript 的对象是无序属性的集合
其属性可以包含基本值、对象、数组和函数
对象就是一组没有顺序的值
我们可以把 JavaScript 中的值想象成键值对，其中值可以是数据和函数
对象的行为和特征：
		特征：属性
    行为：方法
```

**事物的特征在对象中用属性来表示**

**事物的行为在对象中用方法来表示**

### 9.3 如何得到一个对象

* 字面量创建对象

  ```javascript
  var obj1 = {}; // 空对象
  var obj2 = {name: 'zs', age: 18, fly: function(){}}; // 声明一个对象并赋值，对象里面都是键值对
  ```

* 实例化方式声明对象（内置构造函数）

  ```javascript
  var obj1 = new Object();
  ```

* 自定义构造函数

  ```javascript
  function Fun() {
    
  }
  
  var fun = new Fun();
  ```

* 获取对象的属性或者方法

  ```javascript
  对象.属性名/方法() // 该方法用于属性名/方法名已知的情况下
  
  对象[变量] // 该方法用于使用变量代替属性名/方法名的情况下，比如循环
  ```

### 9.4 this 的指向

> JavaScript 中的 this 指向问题，比较复杂，有时候会让人难以捉摸，简单的，只需要记住以下两点就可以了：
>
> 1. **函数如果在某个对象下，this 就指向这个对象**
> 2. **函数如果被直接调用，this 指向 window 全局对象**
> 3. **this 运行在那个对象下，就指向哪个对象**

```javascript
var o1 = {
  name: '张三',
  f: function() {
    console.log(this.name);
  }
}

o1.f(); // 最终打印出：张三
```

### 9.5 对象的使用

* 对象的遍历与循环：

```javascript
for (键 in 对象)
  
var o1 = {
  name: '路飞',
  age: 15,
  sex: '男'
}

for (var k in o1)
  console.log(o1[k]);
```

* 删除对象的某一属性

```javascript
delete o1.age;
```

### 9.6 包装对象

```javascript
JavaScript 中有三种原始类型：数值、字符串、布尔
原始类型的数据在一定条件下可以自动转化为对象，这种情况就称为包装对象
也可以通过 String()，Number() 和 Boolean() 构造函数来显示创建包装对象
也就是说：原始值可以自动当作对象来调用，可以调用各种属性和方法
包装对象使用完成，会自动立即销毁
```

> 1. 创建对象有三种方法：字面量、new 关键字、自定义构造函数
> 2. 对象有属性和方法
> 3. this 指向当前对象
> 4. 使用 . 语法调用对象的属性及方法

## 10. 标准库对象（内置对象）

JavaScript 对象提供了很多个内置对象：Math / Array / Number / String / Boolean ...

对象只是带有 **属性** 和 **方法** 的特殊数据类型。

因此，JavaScript 的学习就是要记住对象的每个属性和方法怎么使用，代表什么含义。

学习、遇到问题、查找资料的地方：

[火狐开发者社区-web | MDN](https://developer.mozilla.org/zh-CN/docs/Web)

### 10.1 Math 对象

#### 10.1.1 使用

1. Math 是一个内置对象，它具有数学常数和函数的属性和方法
2. 与其他全局对象不同的是，Math 不是一个构造器
3. Math 的所有属性和方法都是静态的，跟数学有关的运算直接使用 Math 中的成员即可

#### 10.1.2 案例

获取 n ~ m 之间的随机整数：

```javascript
1. 公式：Math.floor(Math.random() * (m - n) + n)
2. Math.floor：向下取整
3. Math.random：获取 [0, 1) 之间的一个随机数
```

获取 10~20 之间的随机数：

```javascript
<script>
  var random = Math.random() * (20 - 10) + 10;
	var res = Math.floor(random);
	console.log(res);    
</script>
```

### 10.2 Date 对象（构造函数）

#### 10.2.1 使用

创建 Date 实例来处理日期和时间。Date 对象基于 1970 年 1 月 1 日（世界标准时间）起的毫秒数。

```javascript
// 获取当前时间，UTC 世界时间，距 1970 年 1 月 1 日（世界标准时间）起的毫秒数
var now = new Date();
console.log(now.valueOf()); // 获取距 1970 年 1 月 1 日（世界标准时间）起的毫秒数

Date 构造函数的参数：
1. 毫秒数   例如：1498099000356          new Date(1498099000356)
2. 日期格式字符串   例如：'2015-5-1'      new  Date('2015-5-1')
3. 年、月、日……    											new Date(2015, 4, 1) // 月份从 0 开始
```

* 获取日期的毫秒形式

  ```javascript
  var now = new Date();
  // valueOf 用于获取对象的原始值
  console.log(now.valueOf());
  
  // HTML5 中提供的方法，有兼容性问题
  var now = Date.now();
  
  // 不支持 HTML5 的浏览器，可以使用下面这种方式
  var now = + new Date(); // 调用 Date 对象的 valueOf()
  ```

* 日期格式化

  ```javascript
  toString()		// 转换为字符串
  valueOf()			// 获取毫秒值
  // 下面格式化日期的方法，在不同浏览器上可能表现不一致，一般不用
  toDateString()
  toTimeString()
  toLocalDateString()
  toLocalTimeString()
  ```

* 获取日期指定部分

  ```javascript
  getTime()			// 返回毫秒数和valueOf()结果一样，valueOf()内部调用的getTime()
  getSeconds()	// 返回 0 - 59
  getMinutes()	// 返回 0 - 59
  getHours()		// 返回 0 - 23
  getDay()			// 返回星期几  0-周日，6-周六
  getDate()			// 返回当月的第几天
  getMonth()		// 返回月份，从0开始
  getFullYear()	// 返回4位的年份，如2016
  ```

#### 10.2.2 案例

* 写一个函数，格式化日期对象，返回 yyyy-mm-dd HH:mm:ss 的格式

  ```javascript
  function formatDate(d) {
    // 如果 d 不是日期对象，返回
    if (!d instanceof Date) {
      return;
    }
    var year = d.getFullYear(),
        month = d.getMonth() + 1,
        date = d.getDate(),
        hour = d.getHours(),
        minute = d.getMinutes(),
        second = d.getSeconds();
    month = month < 10 ? '0' + month : month;
    date = date < 10 ? '0' + date : date;
    hour = hour < 10 ? '0' + hour : hour;
    minute = minute < 10 ? '0' + minute : minute;
    second = second < 10 ? '0' + second : second;
    return year + '-' + month + '-' + date + ' ' + hour + ':' + minute + ':' + second;
  }    
  ```

* 计算时间差，返回相差的天/时/分/秒

  ```javascript
  function getInterval(start, end) {
    var day, hour, minute, second, interval;
    interval = end - start;
    interval /= 1000;
    day = Math.round(interval / 60 / 60 / 24);
    hour = Math.round(interval / 60 / 60 % 24);
    minute = Math.round(interval / 60 % 60);
    second = Math.round(interval % 60);
    return {
      day: day,
      hour: hour,
      minute: minute,
      second: second
    };
  }
  ```

  

### 10.3 Array 对象

#### 10.3.1 数组对象的属性及方法

**length属性：返回数组的成员数量**

```javascript
var arr = ['a', 'b'];
console.log(arr.length); // 2
```

**数组对象的常用方法举例**

* push 方法用于在数组的末端添加一个或多个元素，并返回添加新元素后的数组长度。注意：该方法会改变原数组

  ```javascript
  var a = [];
  a.push(1); // 1
  a.push('a'); // 2
  a.push(true, {}); // 4
  console.log(a); // [1, 'a', true, {}]
  ```

* pop 方法用于删除数组最后的一个元素，并且返回该元素。注意：该方法会改变原数组

  ```javascript
  var arr = ['a', 'b', 'c'];
  arr.pop(); // c
  console.log(arr); // ['a', 'b']
  ```

* slice 方法用于提取原数组的一部分，返回一个新数组，原数组不变。

  它的第一个参数为起始位置（从 0 开始），第二个参数为终止位置（但该位置的元素本身不包含在内）。如果省略第二个参数，则一直返回到原数组的最后一个成员。

  ```javascript
  var arr = ['a', 'b', 'c', 'd', 'e'];
  console.log(arr.slice(0)); // ['a', 'b', 'c', 'd', 'e']
  console.log(arr.slice(1)); // ['b', 'c', 'd', 'e']
  console.log(arr.slice(1, 3)); // ['b', 'c']
  ```

* 返回数组的字符串表示形式

  ```javascript
  var arr = [1, 2, 3, 4];
  console.log(arr.toString()); // 1,2,3,4
  ```

  

#### 10.3.2 方法和属性

详情参见手册

### 10.4 String 对象

```javascript
var s = 'JavaScript';
// length 属性返回字符串的长度
var i = s.length;
// 返回参数在字符串中第一次出现的位置
var i = s.indexOf('b');
// 从原字符串中取出子字符串并返回，不改变原字符串
// 从下标第二个元素开始截取 4 个长度的字符串
var i = s.substr(2, 4);
// toLowerCase 方法用于将一个字符串全部转成小写
// toUpperCase 则是全部转成大写
var i = s.toLowerCase();
var i = s.toUpperCase();
// 用于替换匹配的字符串，只替换第一个匹配
var i = s.replace('a', 'b');
console.log(i);
```

## 课外知识

### JS 代码规范 & 编程风格

* 缩进：空格和 Tab 都可以，尽量使用一种，保持一致

  ```javascript
  两个空格和四个空格都行，尽量保持一致就行，但是使用四个空格的多一些
  ```

* 分号：尽量不要忘记，每一行的结束都要加分号

  ```javascript
  while 与 for 循环后面不要加分号
  if else、switch 等分支语句后面不要加分号
  关键字声明函数，后面不要加分号
  表达式声明函数，后面要加分号
  ```

  

  

