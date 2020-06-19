[Toc]

# 概念

`web` 的三大组件之一

## 事件监听机制

### 事件

一件事情

### 事件源

事情发生的地方

### 监听器

一个对象

### 注册监听

将事件、事件源、监听器绑定在一起。当事件源发生某个事件后，执行监听器代码

# ServletContextListener

监听 `ServletContext` 对象的创建和销毁

## 方法

* `void contextDestroyed(ServletContextEvent sce)` ：`ServletContexxt` 对象销毁之前会调用该方法
* `void contextInitialized(ServletContextEvent sce)` ：`ServletContext` 对象创建之后会调用该方法

## 步骤

1. 定义一个类，实现 `ServletContextListener` 接口

2. 复写方法

3. 配置

   1. `web.xml`

      ```xml
      <listener>
      	<listener-class>com.ch.wchya.web.listener.ContextLoaderListener</listener-class>
      </listener>
      
      <!-- 指定初始化标签 -->
      <context-param>
      	<param-name>contextConfigLocation</param-name>
        <param-value>/WEB-INF/classes/applicationContext.xml</param-value>
        <!-- param 可以有多组 -->
      </context-param>
      ```

      

   1. 注解

      `@WebListener`

# 用处

1. 一般整个项目都需要使用的文件或者配置，使用 `Listener` 进行加载