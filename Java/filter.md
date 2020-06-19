[Toc]

# 作用

当访问服务器的资源时，过滤器可以将请求拦截下来，完成一些特殊的功能，也就是通用的功能，比如登录、统一编码处理、敏感字符过滤等

# 步骤

1. 定义一个类，实现接口 `Filter`
2. 复写方法
3. 配置拦截路径
   1. `web.xml`
   2. 注解：`WebFilter`

# web.xml 配置

```xml
<filter>
	<filter-name>demo1</filter-name>
  <filter-class>com.ch.wchya.filter.Demo1Filter</filter-class>
</filter>
<filter-mapping>
	<filter-name>demo1</filter-name>
  <!-- 拦截路径 -->
  <url-pattern>/*</url-pattern>
</filter-mapping>
```



# 过滤器执行流程

1. 执行过滤请
2. 执行放行后的资源
3. 回来执行过滤器放行代码下边的代码

# 过滤器生命周期方法

1. 服务器启动后会创建 `Filter` 对象，然后调用 `init` 方法，只执行一次，一般用于加载资源
2. 每一次拦截请求时会执行 `doFilter` 方法，会执行多次
3. 在服务器关闭后 `Filter` 对象被销毁，如果服务器正常关闭，会调用 `destory` 方法，只执行一次，一般用于释放资源

# 过滤器配置详解

## 拦截路径配置

1. 具体的资源路径：`/index.jsp` ，只有访问该资源时，过滤器才会被执行
2. 目录拦截：`/user/*` ，访问 `/user` 下的所有资源时，过滤器都会被执行
3. 后缀名拦截：`*.jsp` ，访问所有后缀名为 `jsp` 的资源时，过滤器都会被执行
4. 拦截所有资源：`/*` ，访问所有资源时，过滤器都会被执行

## 拦截方式配置

1. 注解配置：设置 `diispatchTypes` 属性
   1. `REQUEST` ：默认值，浏览器直接请求资源
   2. `FORWARD` ：转发访问资源
   3. `INCLUDE` ：包含访问资源
   4. `ERROR` ：错误跳转资源
   5. `ASYNC` ：异步访问资源
2. `web.xml`
   1. 在 `<filter-mapping>` 中配置 `<diapatcher></dispatcher>` 标签即可

# 过滤器链（配置多个过滤器）

## 执行顺序

如果有两个过滤器，过滤器 1 和过滤器 2，执行顺序如下：

1. 过滤器1
2. 过滤器2
3. 资源执行
4. 过滤器2
5. 过滤器1

## 先后顺序

1. 注解配置：按照类名的字符串比较规则进行比较，值小的先执行
   1. 如：`AFilter` 和 `BFilter` ，`AFilter` 先执行
2. `web.xml` ：谁的 `<filter-mapping>` 节点定义在上面，谁先执行

