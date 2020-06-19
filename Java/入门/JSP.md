[Toc]

# 概念

`Java Server Pages` ：`Java` 服务器端页面。可以把它理解为：一个特殊的页面，即可以定义 `html` 标签，又可以定义 `Java` 代码，用于简化书写。

# 原理

`JSP` 本质上就是一个 `Servlet` 。

# 脚本

`JSP` 定义 `Java` 代码的方式。

## <% 代码 %>

定义 `Java` 代码，可以定义变量、流程控制语句等，在 `Service` 方法中可以定义什么，该脚本中就可以定义什么

## <%! 代码 %>

定义的 `Java` 代码，在 `JSP` 转换后的 `Java` 类的成员位置。用的非常少，因为在 `Servlet` 中不建议定义成员变量，可能会应发线程安全问题

## <%= 代码 %>

定义的 `Java` 代码，会输出到页面上，即输出语句中可以定义什么，该脚本就可以定义什么



# 语法

## 指令

* 作用：用于配置 `JSP` ，导入资源文件
* 格式：`<%@ 指令名称 属性名1="属性值1" 属性名2="属性值2" ... %>`
* 分类：
  * `page` ：配置 `JSP` 页面的
    * `contentType` ：等同于 `response.setContentType()` ，用于：
      * 设置响应体的 `mime` 类型及字符集
      * 设置当前 `JSP` 页面的编码（只能是高级的 `IDE` 才能生效，如果使用低级工具，则需要使用 `pageEncoding` 来设置当前页面的字符集）
    * `language` ：指的是 `JSP` 使用的语言
    * `buffer` ：缓冲区的大小，默认是 `8KB`
    * `import` ：用来导入 `JSP` 页面需要用到的包
    * `errorPage` ：错误页面。当前页面发生异常后，会自动跳转到指定的错误页面
    * `isErrorPage` ：表示当前的页面是否是错误页面。默认值是 `false` ，如果设置为 `true` ，就可以在 `JSP` 页面上获取 `exception` 对象，该对象包含了发生异常的信息，可以将其记录在日志中
    * `isELIgnored` ：设置是否支持 `EL` 表达式，默认是 `true`
  * `include` ：用于包含页面，导入页面的资源文件
  * `taglib` ：导入标签库
    * 导入 `jstl` 库：
      * 导入 `jstl jar` 包
      * `<%@taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>`



## 注释

1. `HTML` 注释：`<!--  -->` ，只能注释 `HTML` 代码片段
2. `JSP` 注释：`<%--  --%>` ，可以注释所有，注释后的内容不会被发送到客户端浏览器，推荐使用



# 内置对象

`JSP` 内置对象：在 `JSP` 页面中不需要获取和创建，可以直接使用的对象。

`JSP` 中一共有 9 个内置对象：

| 变量名      | 真是类型            | 作用                                         |
| ----------- | ------------------- | -------------------------------------------- |
| pageContext | PageContext         | 当前页面共享数据，还可以获取其他八个内置对象 |
| request     | HttpServletRequest  | 一次请求访问的多个资源（转发）               |
| session     | HttpSession         | 一次会话的多个请求间                         |
| application | ServletContext      | 所有用户间共享数据                           |
| response    | HttpServletResponse | 响应对象                                     |
| page        | Object              | 当前页面（Servlet）的对象                    |
| out         | JspWriter           | 输出对象，数据输出到页面上                   |
| config      | ServletConfig       | Servlet 的配置对象                           |
| exception   | Throwable           | 异常对象                                     |



## pageContext

`PageContext` 对象

## request

`HttpServletRequest` 对象

## session

`HttpSession` 对象

## application

`ServletContext` 对象

## response

`HttpServletResponse` 对象

## page

`Object` 类型

## out

`JspWriter` 对象，字符输出流对象，可以将数据输出到页面上，和 `response.getWriter()` 类似

> out.write() 与 response.getWriter() 的区别：
>
> ​	在 tomcat 服务器真正给客户端做出响应之前，会先找 response 缓冲区数据，再找 out 缓冲区数据，即 response.getWriter() 数据输出永远在 out.write() 方法之前
>
> ​	建议在 JSP 中使用 out.write() 方法进行数据的输出

## config

`ServletConfig` 对象

## exception

`Throwable` 对象

# EL 表达式

`Expression Language` 表达式语言，用于替换和简化 `JSP` 页面中 `Java` 代码的编写。

## 语法

`${表达式}`

> JSP 默认支持 EL 表达式

## 忽略 EL 表达式

1. 在 `page` 指令中设置 `isELIgnored` 属性值为 `true` ，设置后该页面的所有 `EL` 表达式均不起作用
2. 在 `EL` 表达式最前面的 `$` 前添加 `\` 符号，用于将单个的 `EL` 表达式置为失效

## 运算

### 运算符

#### 算术运算符

`+  -  *  /(div)  %(mod)`

### 比较运算符

`>  <  >=  <=  ==  !=`

### 逻辑运算符

`&&(and)  ||(or)  !(not)`

### 空运算符

`empty` ，用于判断字符串、集合、数组对象是否为 `null` ，并且长度是否为 0

## 获取值

`EL` 表达式只能从域对象中获取值

### 语法1

`${域名称.键名}`

### 域名称

1. `pageScore` ：`pageContext`
2. `requestScore` ：`request`
3. `sessionScore` ：`session`
4. `applicationScore` ：`application（ServletContext）`

### 语法2

`${键名}` ，表示依次从最小的域中查找是否有该键对应的值，直到找到为止

### 获取对象的值

`${域名称.键名.属性名}` ：本质上会调用对象的 `getter` 方法

### 获取 List 的值

`${域名称.键名[索引]}` ：注意，如果列表的索引越界，不会报错，会打印一个空字符串

### 获取 Map 的值

`${域名称.键名.key名称}`  或者

`${域名称.键名["key名称"]}` 

## 隐式对象

`EL` 表达式中有 11 个隐式对象，需要重点注意的是：`pageContext`

* 获取 `JSP` 其他八个内置对象

# JSTL 标签

`JavaServer Pages Tag Library` ：`JSP` 标准标签库，用于简化和替换 `JSP` 页面上的 `Java` 代码。

## 使用步骤

1. 导入 `jstl` 相关的 `jar` 包
2. 引入标签库：`<% taglib %>`
3. 使用标签

## 常用标签

### if

相当于 `Java` 代码中的 `if` 语句

1. 属性：
   * `test` ：必须属性，接受 boolean 表达式
     * 如果表达式为 `true` ，则显示 `if` 标签体内容，如果为 `false` ，则不显示标签体内容
     * 一般情况下，`test` 属性值会结合 `el` 表达式一起使用
   * 注意：
     * `c:if` 标签没有 `else` 情况，想要 `else` 情况，则可以再定义一个 `c:if` 标签

### choose

相当于 `Java` 代码中的 `switch` 语句

1. 使用 `choose` 标签声明，相当于 `switch` 声明
2. 使用 `when` 标签做判断，相当于 `case`
3. 使用 `otherwise` 标签做其他情况的声明，相当于 `default`

### foreach

相当于 `Java` 代码中的 `for` 语句，属性：

* `begin` ：开始值
* `end` ：结束值
* `var` ：临时变量
* `step` ：步长
* `varStatus` ：循环状态对象
  * `index` ：容器中元素的索引，从 0 开始
  * `count` ：循环次数，从 1 开始
* `items` ：容器对象



