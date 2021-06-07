[Toc]

# 方言

标准方言包括：`Standard` 和 `SpringStandard`，定义了一组功能，功能可以满足大多数的情况，它将以 `th` 前缀开头的属性。

## 标准表达式语法

### 变量表达式

`${...}`

变量表达式是 `OGNL` 表达式，或者是 `Spring EL`。如果集成了 `Spring` 的话，可以在上下文变量中执行，看起来像这样：

`${session.user.name}`

### 选择表达式

`*{...}`

选择表达式与变量表达式很像，区别在于它们是在当前选择的对象而不是整个上下文变量映射上执行，所作用的对象由 `th:object` 属性指定，例如：

```html
<div th:object="${book}">
  ...
  <span th:text="*{title}">...</span>
  ...
</div>
```

上面的代码等价于：

```
{
  // th:object="${book}"
  final Book selection = (Book) context.getVariable("book");
  // th:text="*{title}"
  output(selection.getTitle());
}
```

### 消息（i18n）表达式

`#{...}`



### 链接表达式

`@{...}`



### 片段表达式

`~{...}`



### 文字和操作

有很多类型的文字和操作可用，它们分别如下：

- 文字
  - 文本文字，例如：`'one text'`, `'Another one!'`,`…`
    - 使用单引号的三种方式：
      - 反斜杠转义：`<a th:onclick="'xadmin.add_tab(\'Search\',\'' + @{/app/xx} + '\')'">链接名</a>` 的最终结果是：`<a onclick="xadmin.add_tab('Search','/app/xx')" >链接名</a>`
      - 单引号转义：变量表达式中，单引号是转义符。`<a th:onclick="${'xadmin.add_tab(''Search'','''} + @{/app/xx} + ${''')'}">链接名</a>` 的最终结果是：`<a onclick="xadmin.add_tab('Search','/app/xx')" >链接名</a>`
      - 使用文本替换输出单引号：文本替换表达式允许出现单引号，且不需要转义。`<a th:onclick="|xadmin.add_tab('Search',' @{/app/xx}')|">链接名</a>` 的最终结果是：`<a onclick="xadmin.add_tab('Search','/app/xx')" >链接名</a>`
  - 数字文字，例如：`0`,`10`, `314`, `31.01`, `112.83`,`…`
  - 布尔文字，例如：`true`,`false`
    - 布尔值的比较，如果写在 `{}` 大括号之内，会由 `Thymeleaf` 做处理，否则，是由 `OGNL/SpringEL` 引擎负责处理
  - Null文字，例如：`Null`
  - 文字标记，例如：`one`, `sometext`, `main`,`…`
    - 只允许使用 **大小写字母、数字、小/中括号、连字符、下划线**
    - 没有空白
    - 没有逗号
- 文本操作
  - 字符串连接：`+`
  - 文字替换：`|The name is ${name}|`
    - 可以容易地格式化包含变量值的字符串，而不需要使用 `'...' + '...'` 这样的拼接
- 算术运算
  - 二进制操作：`+`, `-`, `*`, `/`, `%`
    - 存在文本别名的运算符：`div(/)、mod(%)`
  - 减号(一元运算符)：`-`
- 布尔运算
  - 二进制运算符，`and`,`or`
  - 布尔否定(一元运算符)：`!`,`not`
- 比较和相等
  - 比较运算符：`>`,`<`,`>=`,`<=`(`gt`,`lt`,`ge`,`le`)
  - 相等运算符：`==`, `!=` (`eq`, `ne`)
- 条件操作符
  - `If-then`：`(if) ? (then)`
    - 如果条件为 `false`，返回 `null` 值
  - `If-then-else`：`(if) ? (then) : (else)`
  - `Default`： `(value) ?: (defaultvalue)`
    - `Default` 为 `null`，则使用 `defaultvalue`

### 表达式预处理

表达式预处理的部分被定义在 `__` 之间，这部分会先被执行，例如：

`#{select.__${sel.code}__}`

### 无标记操作

无操作标记由下划线符号（`_`）表示。表示什么也不做，这允许开发人员使用原型中的文本默认值：

```html
<span th:text="${user.name} ?: _">no user authenticated</span>
```

## 标准 URL 语法

`Thymeleaf` 提供了一种在 `Web` 应用程序中轻松创建 `URL` 的方法，以便它们包含任何所需的 `URL` 工作

### 绝对网址

绝对 `URL` 用于创建到其它服务器的链接，它们需要指定一个协议名称（`http:// 或 https://`）开头：

```html
<a th:href="@{https://www.yiibai.com/thymeleaf/}">
```

上面链接不会被修改，除非在服务器上配置了URL重写过滤器，并在`HttpServletResponse.encodeUrl(...)`方法中执行修改。最后生成的 `HTML` 代码如下：

```html
<a href="https://www.yiibai.com/thymeleaf/">
```

### 上下文相关 URL

最常用的 `URL` 类型是上下文相关的。 这些 `URL` 是一旦安装在服务器上，`URL` 就会与 `Web` 应用程序根目录相关联。 例如，如果将一个名称为 `myapp.war` 的文件部署到一个 `Tomcat` 服务器中，那么应用程序一般是通过`URL`：`http://localhost:8080/myapp`来访问，`myapp`就是上下文名称。

与上下文相关的URL以`/`字符开头：

```html
<a th:href="@{/order/list}">
```

如果应用程序访问URL为：`http://localhost:8080/myapp`，则此 `URL` 将输出:

```html
<a href="/myapp/order/list">
```

### 与服务器相关 URL

服务器相关的 `URL` 与上下文相关的 `URL` 非常相似，只是它们不假定 `URL` 要链接到应用程序上下文中的资源，因此允许链接到同一服务器中的不同上下文:

```html
<a th:href="@{~/billing-app/showDetails.html}">
```

当前应用程序的上下文将被忽略，因此尽管应用程序部署在`http:// localhost:8080 / myapp`，但该 `URL` 将输出:

```html
<a href="/billing-app/showDetails.html">
```

### 协议相关 URL

与协议相关的 `URL` 实际上是绝对的 `URL`，它将保持用于显示当前页面的协议(`HTTP，HTTPS`)。 它们通常用于包括样式，脚本等外部资源:

```html
<script th:src="@{//scriptserver.example.net/myscript.js}">...</script>
```

它将呈现与上面一致的URL(URL重写除外)，如:

```html
<script src="//scriptserver.example.net/myscript.js">...</script>
```

### 添加参数

如何向使用`@{...}`表达式创建的URL添加参数？ 这也很简单:

```html
<a th:href="@{/order/details(id=3)}">

```

上面示例代码，最终将输出为:

```html
<a href="/order/details?id=3">
```

也可以添加几个参数，用逗号分隔它们:

```html
<a th:href="@{/order/details(id=3,action='show_all')}">
```

上面代码将输出结果为:

```html
<!-- 注意＆符号在标签属性中进行HTML转义... -->
<a href="/order/details?id=3&action=show_all">
```

还可以使用正常参数的路径变量的形式包含参数，但在URL的路径中指定一个占位符:

```html
<a th:href="@{/order/{id}/details(id=3,action='show_all')}">
```

上面输出结果为:

```html
<a href="/order/3/details?action=show_all">
```















