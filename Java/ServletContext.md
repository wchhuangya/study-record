[Toc]

# 基本概念

代表整个 `web` 应用，可以和程序的容器（服务器）来通信。

1. 可以通过 `request` 对象获取：`reqeust.getServletContext()`
2. 通过 `HttpServlet` 对象获取：`this.getServletContext()`

# 功能

## 获取文件的 MIME 类型

`MIME` 类型：在互联网通信过程中定义的一种文件数据类型，格式：`大类型/小类型` ，如 `text/html` ，`image/jpg` 等

1. 获取文件类型：`String getMimeType(String file)`

## 域对象

范围：所有用户所有请求的数据

## 获取文件的真实路径

`String getRealPath("String path")`

## 文件下载

超链接指向的资源如果能够被浏览器解析，则在浏览器中显示，如果不能解析，则弹出下载提示框。

步骤：

1. 定义页面，编辑超链接的 `href` 属性，指向 `servlet` ，传递资源名称 `filename`
2. 定义 `servlet` 
   1. 获取文件名称
   2. 使用字节输入流加载文件到内存中
   3. 指定 `response` 的 `header` ：`content-disposition:attachment;filename=xxx`
   4. 将数据写出到 `response` 输出流

中文文件名称问题解决思路：

1. 获取客户端使用的浏览器版本信息
2. 根据不同的版本信息，设置 `filename` 的编码方式不同

