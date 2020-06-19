[Toc]

# web 服务器软件

* 服务器：安装了服务其软件的计算机
* 服务器软件：接受用户的请求，处理请求，做出响应
* `web` 服务器软件：接受用户的请求，处理请求，做出响应
  * 在 `web` 服务器软件中，可以部署 `web` 项目，让用户通过浏览器来访问这些项目

# 常见的 java 相关的 web 服务器软件

* `webLogic` ：`oracle` 公司，大型的 `JavaEE` 服务器，支持所有的 `JavaEE` 规范，收费
* `webSphere` ：
* `JBOSS` ：
* `Tomcat` ：`Apache` 基金组织，中小型的 `JavaEE` 服务器，仅仅支持少量的 `JavaEE` 规范，开源的，免费的

> JavaEE ：Java 语言在企业级开发中使用的技术规范的综合，一共规定了 13 项大的规范

# 部署项目的方式

* 直接将项目放到 `webapps` 目录下即可

  * 项目的访问路径：`http://localhost:端口/虚拟目录` ，虚拟目录是指非 `ROOT` 的项目目录名称，`ROOT` 项目目录在访问时，不需要添加虚拟目录名称
  * 简化部署：将项目打成一个 `war` 包，再将 `war` 包放置到 `webapp` 目录下，`war` 会自动进行解压

* 配置 `conf/server.xml` 文件

  * 在 `<host>` 标签体中配置

    `<Context docBase="D:\hello" path="/hehe" />`

    `docBase` ：项目存放的路径

    `path` ：虚拟目录

* 在 `conf\Catalina\localhost` 创建任意名称的 `xml` 文件，在文件中编写

  * `<Context docBase="D:\hello" />`

    虚拟目录：`xml` 文件的名称

# Java 动态项目的目录结构

-- 项目的根目录

​	-- WEB-INF 目录

​		-- `web.xml` ：`web` 项目的核心配置文件

​		-- `classes` 目录：放置字节码文件的目录

​		-- `lib` 目录：放置依赖的 `jar` 包









