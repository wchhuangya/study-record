[Toc]

# Request

## 获取请求消息数据

### 获取请求行数据

请求行：`GET /day14/demo1?name=zhangsan HTTP/1.1`

1. 获取请求方式（`GET`）：`String getMethod()` 
2. **获取虚拟目录**（`/day14`）：`String getContextPath()`
3. 获取 `servlet` 路径（`/demo1`）：`String getServletPath()`
4. 获取 `GET` 方式的请求参数（`name=zhangsan`）：`String getQueryString()`
5. **获取请求 `URI`**（`/day14/demo1`） ：`String getRequestURI()——返回/day14/demo1 ` ` String getRequestURL()——返回 http://localhost:8080/day14/demo1`
6. 获取协议及版本（`HTTP/1.1`）：`String getProtocol()`
7. 获取客户机的 `ip` 地址（返回 `IPV6 的地址`）：`String getRemoteAddress()`

### 获取请求头数据

1. **通过请求头的名称获取请求头的值**：`String getHeader(String name)`

   > 注意：name 不区分大小写
   >
   > 重要的两个头名称：
   >
   > 1. agent ：可以通过里面的值判断区分浏览器的类型
   > 2. referer ：可以获取访问来源的 url

2. 获取所有请求头名称：`Enumeration<String> getHeaderNames()`

### 获取请求体数据

请求体：只有 `POST` 方式才有请求体，在请求体中封装了 `POST` 请求的请求参数

1. 获取流对象

   1. 获取字符输入流，只能操作字符数据：`BufferReader getReader()`

      > 表单提交的数据，在请求体中，会封装为 key1=value1&key2=value2... 的形式

   2. 获取字节输入流，可以操作所有类型的数据：`ServletInputStream getInputStream()`

2. 从流对象中拿数据

## 其他功能

### 获取请求参数通用方法

`get` 和 `post` 都可以使用下列方法来获取请求参数：

1. 根据参数名称获取参数值：`String getParameter(String name)`
2. 根据参数名称获取参数的数组：`String[] getParameter(String name)`
3. 获取所有请求的参数名称：`Enumeration<String> getParameterNames()`
4. 获取所有参数的 `Map` 集合：`Map<String, String[]> getParameterMap()`

> 中文乱码问题：
>
> get 方式：tomcat 8 已经将 get 方式乱码问题解决了
>
> post 方式：会乱码，需要在获取参数前，设置 request 的编码：request.setCharacterEncoding("utf-8")

### 请求转发

一种在服务器内部的资源跳转方式。

1. 步骤
   1. 通过 `request` 对象获取请求转发器对象：`RequestDispatcher getRequestDispatcher(String path)`
   2. 使用 `RequestDispatcher` 对象进行转发：`forward(ServletRequest request，ServletResponse response)`
2. 特点
   1. 浏览器地址栏路径不发生变化
   2. 只能转发到当前的服务器内部的资源中
   3. 转发是一次请求，可以使用 `request` 对象来共享数据

### 共享数据

#### 域对象

域对象：一个有作用范围的对象，可以在范围内共享数据

`request` 域：代表一次请求的范围，一般用于请求转发的多个资源中共享数据

1. 存储数据：`setAttriibute(String name, Object object)`
2. 通过键获取值：`Object getAttribute(String name)`
3. 通过键移除键值对：`void removeAttribute(String name)`

### 获取 ServletContext



# 响应消息

1. 响应行

   1. 组成：协议/版本 相应状态码 状态码描述
   2. 响应状态码：服务器告诉客户端浏览器本次请求和响应的一个状态
      1. 状态码都是 3 为数字
      2. 分类：
         1. 1xx ：服务器接收客户端消息，但没有接收完成，等待一段时间后，发送 1xx 状态码
         2. 2xx ：成功
         3. 3xx ：重定向。例如：302（重定向），304（访问缓存）
         4. 4xx ：客户端错误。例如：404（请求路径没有对应的资源），405（请求方式没有对应的方法）
         5. 5xx ：服务器端错误。例如：500（服务器内部出现异常）

2. 响应头

   1. 格式：头名称：值

   2. 常见的响应头

      <img src="/Users/wchya/own/markdown/imgs/image-20200509222750078.png" alt="image-20200509222750078" style="zoom:50%;" />

      1. `Content-Type` ：服务器告诉客户端本次响应体数据格式以及编码格式
      2. `Content-disposition` ：服务器告诉客户端以什么格式打开响应体数据，取值：
         1. `in-line` ：默认值，在当前页面打开
         2. `attachment;filename=xxx` ：以附件形式打开响应体，文件下载

3. 响应空行
4. 响应体：传输的数据

# Response

用于设置响应消息。

## 设置响应行

格式：`HTTP/1.1 200 OK`

1. 设置状态码：`setStatus(int sc)`

## 设置响应头

1. `setHeader(String name, String value)`

## 设置响应体

步骤：

1. 获取输出流：
   1. 字符输出流：`PrintWriter getWriter()`
   2. 字节输出流：`ServletOutputStream getOutPutStream()`
2. 使用输出流，将数据输出到浏览器客户端



## 案例

### 重定向

1. 设置状态码，设置重定向路径

   ```java
   response.setStatus(302);
   response.setHeader("location", "/demo1");
   ```

   

2. 使用简单的方法，只设置重定向路径，方法会设置状态码

   ```java
   response.sendRedirect("/demo1");
   ```

#### 特点

1. 地址栏发生变化
2. 可以访问其他服务器的资源
3. 是两次请求，不能使用 `request` 来共享数据

### 路径写法

#### 相对路径

通过相对路径不能确定唯一资源。

如：`./index.html` ，即以 `.` 开头的路径

> 注意：相对路径的 ./ 可以省略，省略后默认会在当前资源的同级查找资源

规则：找到当前资源和目标资源之间的相对位置关系

* `./` 表示当前目录
* `../` 表示上一级目录

#### 绝对路径

通过绝对路径可以确定唯一资源。

如：`http://localhost:8080/day14/demo1` ，可以简写为：`/day14/demo1` ，所以说，绝对路径可以简单的认为是以 `/` 开头的路径

规则：判断定义的路径是给谁使用的，判断请求将来从那里发出

* 给客户端浏览器使用：需要加虚拟目录（项目的访问路径）
  * 建议虚拟目录动态获取：`request.getContextPath()`
* 给服务器使用：不需要加虚拟目录

### 服务器输出字符数据到浏览器

步骤：

1. 获取字符数据
2. 输出数据

> 解决乱码：
>
> 1. 告诉浏览器，服务器发送的消息数据体的编码，建议浏览器使用该编码解码：
>
>    response.setHeader("content-type", "text/html;charset=utf-8"); // 或者
>
>    response.setContentType("text/html;charset=utf-8");
>
> 2. 注意：在获取流之前进行字符编码的设置

#### 服务器输出字节数据到浏览器

步骤：

1. 获取字节数据
2. 输出数据

### 验证码

1. 本质：图片
2. 目的：防止恶意的表单注册

