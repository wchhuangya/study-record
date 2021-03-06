[Toc]

# 1. 基本概念

## 1.1 什么是认证

进入移动互联网时代，大家每天都在刷手机，常用的软件有微信、支付宝、头条等，下边拿微信来举例子说明认证相关的基本概念。在初次使用微信前需要注册成为微信用户，然后输入账号和密码即可登录微信，输入账号和密码登录微信的过程就是认证

系统为什么要认证？

认证是为了保护系统的隐私数据与资源，用户的身份合法方可访问该系统的资源

**认证**：用户认证就是判断一个用户的身份是否合法的过程，用户去访问系统资源时系统要求验证用户的身份信息，身份合法方可继续访问，不合法则拒绝访问。常见的用户身份认证方式有：用户名密码登录、二维码登录、手机短信登录、指纹认证等方式。

## 1.2 什么是会话

用户认证通过后，为了避免用户的每次操作都进行认证，可将用户的信息保存在会话中。会话就是系统为了保持当前用户的登录状态所提供的机制，常见的有基于 `session` 方式、基于 `token` 方式等

基于 `session` 的认证方式如下图：

[![R9hoP1.md.png](https://z3.ax1x.com/2021/06/19/R9hoP1.md.png)](https://imgtu.com/i/R9hoP1)

它的交互流程是，用户认证成功后，在服务端生成用户相关的数据保存在 `session`（当前会话）中，发给客户端的 `session_id` 存放到 `cookie` 中，这样用户客户端请求时带上 `session_id` 就可以验证服务端是否存在 `session` 数据，以此完成用户的合法校验；当用户退出系统或 `session` 过期销毁时，客户端的 `session_id` 也就无效了

基于 `token` 方式如下：

[![R9hjVH.md.png](https://z3.ax1x.com/2021/06/19/R9hjVH.md.png)](https://imgtu.com/i/R9hjVH)

它的交互流程是，用户认证成功后，服务端生成一个 `token` 发给客户端，客户端可以放到 `cookie` 或 `localStorage` 等存储中，每次请求时带上 `token`，服务端收到 `token` 通过验证后即可确认用户身份

基于 `session` 的认证方式由 `Servlet` 规范定制，服务端要存储 `session` 信息需要占用内存资源，客户端需要支持 `cookie`；基于 `token` 的方式则一般不需要服务端存储 `token`，并且不限制客户端的存储方式。如今移动互联网时代，更多类型的客户端需要接入系统，系统多是采用前后端分离的架构进行实现，所以基于 `token` 的方式更适合

## 1.3 什么是授权

还拿微信来兴趣例子，微信登录成功后用户即可使用微信的功能，比如，发红包、发朋友圏、添加好友等，没有绑定银行卡的用户是无法发送红包的，绑定银行卡的用户才可以发红包，发红包功能、发朋友圏功能都是微信的资源即功能资源，用户拥有发红包功能的权限才可以正常使用发送红包功能，拥有发朋友功能的权限才可以使用发朋友圏功能，这个根据用户的权限来控制用户使用资源的过程就是授权

为什么要授权？

认证是为了保证用户身份的合法性，授权则是为了更细粒丫的对隐私数据进行划分，授权是在认证通过后发生的，控制不同的用户能够访问不同的资源

**授权：**授权是用户认证通过根据用户的权限来控制用户访问资源的过程，拥有资源的访问权限则正常访问，没有权限则拒绝访问

## 1.4 授权的数据模型

如何进行授权即如何对用户访问资源进行控制，首先需要学习授权相关的数据模型

授权可简单理解为 `Who` 对 `What(which)` 进行 `How` 操作，包括如下：

`Who`，即主体（`Subject`），主体一般是指用户，也可以是程序，需要访问系统中的资源

`What`，即资源（`Resource`），如系统菜单、页面、按钮、代码方法、系统端口信息、系统订单信息等。系统菜单、页面、按钮、代码方法都属于系统功能资源，对于 `web` 系统每个功能资源通常对应一个 `URL`；系统端口信息、系统订单信息都属于实体资源（数据资源），实体资源由资源类型和资源实例组成，比如商品信息为资源类型，商品编号为 001 的商品为资源实例

`How`，权限/许可（`Permission`），规定了用户对资源的操作许可，权限离开资源没有意义，如用户查询权限、用户添加权限、某个代码方法的调用权限、编号为 001 的用户的修改权限等，通过权限可知用户对哪些资源都有哪些操作许可

主体、资源、权限关系如下图：

[![R9IZ3q.md.png](https://z3.ax1x.com/2021/06/19/R9IZ3q.md.png)](https://imgtu.com/i/R9IZ3q)

主体、资源、权限相关的数据模型如下：

* 主体（用户 `id`、账号、密码、……）
* 资源（资源 `id`、资源名称、访问地址、……）
* 权限（权限 `id`、权限标识、权限名称、资源 `id`、……）
* 角色（角色 `id`、角色名称、……）
* 角色和权限关系（角色 `id`、权限 `id`、……）
* 主体（用户）和角色关系（用户 `id`、角色 `id`、……）

主体（用户）、资源、权限关系如下图：

[![R9OcBq.md.png](https://z3.ax1x.com/2021/06/19/R9OcBq.md.png)](https://imgtu.com/i/R9OcBq)

通常企业开发中将资源和权限表合并为一张权限表，如下：

* 资源（资源 `id`、资源名称、访问地址、……）
* 权限（权限 `id`、权限标识、权限名称、资源 `id`、……）

合并为：

* 权限（权限 `id`、权限标识、权限名称、资源名称、资源访问地址、……）

修改后数据模型之间的关系如下图：

[![R9X9KA.md.png](https://z3.ax1x.com/2021/06/19/R9X9KA.md.png)](https://imgtu.com/i/R9X9KA)

## 1.5 RBAC

如何实现授权？业界通常基于 `RBAC` 实现授权

### 1.5.1 基于角色的访问控制

`RBAC` 基于角色的访问控制（`Role-Based Access Control`）是按角色进行授权，比如：主体的角色为总经理可以查询企业运营报表，查询员工工资信息等，访问控制流程如下：

```flow
op1=>operation: 查询员工信息
cnd=>condition: 判断主体是否具有总经理角色
op2=>operation: 无访问处理
（通常提示用户无权操作）
op3=>operation: 获取权限继续操作
op1->cnd
cnd(yes)->op3
cnd(no)->op2(down)
```

根据上图中的判断逻辑，授权代码可表示如下：

```java
if (主体.hasRole("总经理角色 id")) {
    查询工资
}
```

如果上图中查询工资所需要的角色变化为总经理和部门经理，此时就需要修改判断逻辑为 “判断用户的角色是否是总经理或部门经理”，修改代码如下：

```java
if (主体.hasRole("总经理角色 id") || 主体.hasRole("部门经理角色 id")) {
    查询工资
}
```

根据上边的例子发现，当需要修改角色的权限时就需要修改授权的相关代码，系统可扩展性差

### 1.5.2 基于资源的访问控制

`RBAC` 基于资源的访问控制（`Resource-Based Access Control`）是按资源（或权限）进行授权，比如：用户必须具有查询工资权限才可以查询员工工资信息等，访问控制流程如下：

```flow
op1=>operation: 查询工资信息
cnd=>condition: 判断主体是否拥有查询工资的权限
op2=>operation: 获取权限继续访问
op3=>operation: 无权访问处理
（通常提示用户无权操作）
op1->cnd
cnd(yes)->op2
cnd(no)->op3
```

根据上图的判断，授权代码可表示为：

```java
if (主体.hasPermission("查询工资权限标识")) {    
    查询工资
}
```

优点：系统设计时定义好查询工资的权限标识，即使查询工资所需要的角色变化为总经理和部门经理也不需要修改授权代码，系统可扩展性强

# 2. 基于 Session 的认证方式

## 2.1 认证流程

基于 `Session` 认证方式的流程是：用户认证成功后，在服务端生成用户相关的数据保存在 `Session`（当前会话），而发给客户端的 `session_id` 存放到 `cookie` 中，这样用客户端请求时带上 `session_id` 就可以验证服务端是否存在 `session` 数据，以此完成用户的合法校验。当用户退出系统或 `session` 过期销毁时，客户端的 `session_id` 也就无效了。下图是 `session` 认证方式的流程图：

![R9hoP1.md.png](https://z3.ax1x.com/2021/06/19/R9hoP1.md.png)

基于 `session` 的认证机制由 `Servlet` 规范定制，`Servlet` 容器已实现，用户通过 `HttpSession` 的操作方法即可实现，如下是 `HttpSession` 相关的操作 `API`：

| 方法                                           | 含义                        |
| ---------------------------------------------- | --------------------------- |
| `HttpSession getSession(Boolean create)`       | 获取当前 `HttpSession` 对象 |
| `void setAttribute(String name, Object value)` | 向 `session` 中存放对象     |
| `object getAttribute(String name)`             | 从 `session` 中获取对象     |
| `void removeAttribute(String name)`            | 移除 `session` 中对象       |
| `void invalidate()`                            | 使 `HttpSession` 失效       |
| 略……                                           |                             |

## 2.2 创建工程

本案例工程使用 `maven` 进行构建，使用 `SpringMVC`、`Servlet 3.0` 实现

### 2.2.1 创建 maven 工程

创建 `maven` 工程 `security-springmvc`，工程结构如下：

[![RiNvWj.png](https://z3.ax1x.com/2021/06/20/RiNvWj.png)](https://imgtu.com/i/RiNvWj)

`pom.xml` 文件内容如下：

```xml
<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">

  <parent>
    <artifactId>all</artifactId>
    <groupId>com.ch.wchya</groupId>
    <version>1.0-SNAPSHOT</version>
  </parent>

  <modelVersion>4.0.0</modelVersion>

  <artifactId>security-springmvc</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>war</packaging>

  <name>security-springmvc</name>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>11</maven.compiler.source>
    <maven.compiler.target>11</maven.compiler.target>
  </properties>

  <dependencies>

    <dependency>
      <groupId>com.ch.wchya</groupId>
      <artifactId>entity</artifactId>
      <version>1.0-SNAPSHOT</version>
    </dependency>

    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-webmvc</artifactId>
    </dependency>

    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>javax.servlet-api</artifactId>
      <scope>provided</scope>
    </dependency>
    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>jsp-api</artifactId>
      <scope>provided</scope>
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
      <groupId>org.projectlombok</groupId>
      <artifactId>lombok</artifactId>
      <scope>provided</scope>
    </dependency>

    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
  </dependencies>

  <build>
    <finalName>security-springmvc</finalName>
    <pluginManagement><!-- lock down plugins versions to avoid using Maven defaults (may be moved to parent pom) -->
      <plugins>
        <plugin>
          <artifactId>maven-clean-plugin</artifactId>
          <version>3.1.0</version>
        </plugin>
        <!-- see http://maven.apache.org/ref/current/maven-core/default-bindings.html#Plugin_bindings_for_war_packaging -->
        <plugin>
          <artifactId>maven-resources-plugin</artifactId>
          <version>3.0.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-compiler-plugin</artifactId>
          <version>3.8.0</version>
        </plugin>
        <plugin>
          <artifactId>maven-surefire-plugin</artifactId>
          <version>2.22.1</version>
        </plugin>
        <plugin>
          <artifactId>maven-war-plugin</artifactId>
          <version>3.2.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-install-plugin</artifactId>
          <version>2.5.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-deploy-plugin</artifactId>
          <version>2.8.2</version>
        </plugin>
      </plugins>
    </pluginManagement>
  </build>
</project>
```

### 2.2.2 Spring 容器配置

在 `config` 包下定义 `ApplicationConfig.java`，它对应 `web.xml` 中 `ContextLoaderListener` 的配置：

```java
@Configuration
@ComponentScan(basePackages = "com.ch.wchya.security.springmvc", excludeFilters = {@ComponentScan.Filter(type = FilterType.ANNOTATION, value = Controller.class)})
public class ApplicationContext {
    // 在此配置除了 Controller 的其它 bean，比如：数据库连接池，事务管理器，业务 bean 等
}
```

### 2.2.3 Servlet Context 容器配置

```java
@Configuration
@EnableWebMvc
@ComponentScan(basePackages = "com.ch.wchya.security.springmvc", includeFilters = {@ComponentScan.Filter(type = FilterType.ANNOTATION, value = Controller.class)})
public class WebConfig implements WebMvcConfigurer {

    @Autowired
    private SimpleAuthenticationInterceptor simpleAuthenticationInterceptor;

    @Bean
    public InternalResourceViewResolver viewResolver() {
        InternalResourceViewResolver viewResolver = new InternalResourceViewResolver();
        viewResolver.setPrefix("/WEB-INF/view/");
        viewResolver.setSuffix(".jsp");
        return viewResolver;
    }

    @Override
    public void addViewControllers(ViewControllerRegistry registry) {
        registry.addViewController("/").setViewName("login");
    }

    @Override
    public void addInterceptors(InterceptorRegistry registry) {
        registry.addInterceptor(simpleAuthenticationInterceptor).addPathPatterns("/r/**");
    }
}
```

### 2.2.4 启动 Spring 容器

> 路径：com.ch.wchya.security.springmvc.init

```java
public class SpringApplicationInitializer extends AbstractAnnotationConfigDispatcherServletInitializer {

    // spring 窗口，相当于加载 applicationContext.xml
    @Override
    protected Class<?>[] getRootConfigClasses() {
        return new Class[]{ApplicationContext.class};
    }

    // servletContext，相当于加载 spring-mvc.xml
    @Override
    protected Class<?>[] getServletConfigClasses() {
        return new Class[]{WebConfig.class};
    }

    // url-mapping
    @Override
    protected String[] getServletMappings() {
        return new String[]{"/"};
    }
}
```

## 2.3 实现认证功能

### 2.3.1 认证页面

在 `webapp/WEB-INF/view` 目录下定义认证页面 `login.jsp`，本安全只是测试认证流程，页面没有添加 `css` 样式，页面实现可填入用户名，密码，触发登录提交表单信息至 `/login`，内容如下：

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<html>
<head>
    <title>登录页面</title>
</head>
<body>
    <form action="/login" method="post">
        <label for="username">用户名：</label><input type="text" id="username" name="username"><br>
        <label for="password">密码：</label><input type="password" id="password" name="password"><br>
        <input type="submit" value="登录">
    </form>
</body>
</html>
```

### 2.3.2 认证接口

用户进入认证页面，输入账号和密码，点击登录，请求 `/login` 进行身份认证

1. 定义认证接口，此接口用于对传来的用户名、密码校验，若成功则返回该用户的详细信息，否则抛出错误异常：

   ```java
   public interface AuthenticationService {
       /**
        * 用户认证
        * @param authenticationRequest 用户认证请求：账号和密码
        * @return 认证成功的用户信息
        */
       User authentication(AuthenticationRequest authenticationRequest);
   }
   ```

   认证请求的实体：

   ```java
   @Data
   public class AuthenticationRequest {
       // 认证请求参数：账号、密码
       private String username;
       private String password;
   }
   ```

   认证成功后返回的用户详细信息，也就是当前登录用户的信息：

   ```java
   @Data
   @AllArgsConstructor
   public class User {
       // 用户身份信息
       private String id;
       private String username;
       private String password;
       private String fullname;
       private String mobile;
   }
   ```

2. 认证实现类，根据用户名查找用户信息，并校验密码，这里模拟了两个用户：

   ```java
   @Service("authenticationService")
   public class AuthenticationServiceImpl implements AuthenticationService {
       @Override
       public User authentication(AuthenticationRequest authenticationRequest) {
           if (authenticationRequest == null || StringUtils.isEmpty(authenticationRequest.getUsername()) || StringUtils.isEmpty(authenticationRequest.getPassword())) {
               throw new RuntimeException("用户名或密码为空");
           }
   
           // 根据账号去查询数据库，这里测试程序采用模拟方法
           User user = getUser(authenticationRequest.getUsername());
           if (user == null)
               throw new RuntimeException("查询不到该用户");
   
           if (!user.getPassword().equals(authenticationRequest.getPassword()))
               throw new RuntimeException("账号或密码错误");
           
           // 认证通过，返回用户身份信息
           return user;
       }
   
       // 模拟用户查询
       public User getUser(String username) {
           return userMap.get(username);
       }
   
       // 用户信息
       private Map<String, User> userMap = new HashMap<>();
       {
           userMap.put("zhangsan", new User("1010", "zhangsan", "123", "张三", "133443"));
           userMap.put("lisi", new User("1011", "lisi", "456", "李四", "144553"));
       }
   }
   ```

3. 登录 `controller`，对 `/login` 请求处理，它调用 `AuthenticationService` 完成认证并返回登录结果提示信息：

   ```java
   @RestController
   public class LoginController {
       @Autowired
       private AuthenticationService authenticationService;
   
       /**
        * 用户登录
        * @param authenticationRequest 登录请求
        * @return 登录成功后，返回用户信息
        */
       @RequestMapping(value = "/login", produces = "text/plain; charset=utf-8")
       public String login(AuthenticationRequest authenticationRequest) {
           User user = authenticationService.authentication(authenticationRequest);
           return user.getFullname() + " 登录成功";
       }
   }
   ```

4. 测试：启动项目，访问路径，进行测试

## 2.4 实现会话功能

会话是指用户登入系统后，系统会记住该用户的登录状态，它可以存在于系统连续操作直到退出系统的过程

认证的目的是对系统资源的保护，每次对资源的访问，系统必须得知道是认证在访问资源，才能对该请求进行合法性拦截。因此，在认证成功后，一般会把认证成功的用户信息放入 `session` 中，在后续的请求中，系统能够从 `session` 中获取到当前用户，用这样的方式来实现会话机制

1. 增加会话控制：首先 `User` 中定义一个 `SESSION_USER_KEY`，作为 `session` 中存放登录用户信息的 `key`

   ```java
   public static final String SESSION_USER_KEY = "_user";
   ```

   然后修改 `LoginController`，认证成功后，将用户信息放入当前会话。并增加用户登出方法，登出时将该 `session` 置为失效

2. 增加测试资源：修改 `LoginController`，增加测试资源，它从当前会话 `session` 中获取当前登录用户，并返回提示信息给前台

   ```java
   @GetMapping(value = "/r/r1", produces = "text/plain; charset=utf-8")
   public String r1(HttpSession session) {
       String fullname = null;
       Object user = session.getAttribute(User.SESSION_USER_KEY);
       if (user != null) {
           fullname = ((User) user).getFullname();
       } else {
           fullname = "匿名";
       }
       return fullname + " 访问资源1";
   }
   ```

## 2.5 实现授权功能

现在我们已经完成了用户身份凭证的校验以及登录的状态保持，并且我们也知道了如何获取当前登录用户（从 `session` 中获取）的信息，接下来，用户访问系统需要经过授权，即需要完成如下功能：

* 匿名用户（未登录用户）访问拦截：禁止匿名用户访问某些资源
* 登录用户访问拦截：根据用户的权限决定是否能访问某些资源

1. 增加权限数据

   为了实现这样的功能，我们需要在 `User` 里增加权限属性，用过表示该登录用户所拥有的权限，同时修改 `User` 的构造方法

   ```java
   @Data
   @AllArgsConstructor
   public class User {
       public static final String SESSION_USER_KEY = "_user";
       // 用户身份信息
       private String id;
       private String username;
       private String password;
       private String fullname;
       private String mobile;
       // 用户权限
       private Set<String> authorities;
   }
   ```

   并且在 `AuthenticationServiceImpl` 中为模拟用户初始化权限，其中张三给了 `p1` 权限，李四给了 `p2` 权限：

   ```java
   // 用户信息
   private Map<String, User> userMap = new HashMap<>();
   {
       Set<String> authorities1 = new HashSet<>();
       authorities1.add("p1");
       Set<String> authorities2 = new HashSet<>();
       authorities2.add("p2");
       userMap.put("zhangsan", new User("1010", "zhangsan", "123", "张三", "133443", authorities1));
       userMap.put("lisi", new User("1011", "lisi", "456", "李四", "144553", authorities2));
   }
   ```

2. 增加测试资源

   我们想实现针对不同的用户能访问不同的资源，前提是得有多个资源，因此在 `LoginController` 中增加测试资源 2：

   ```java
   @GetMapping(value = "/r/r2", produces = "text/plain; charset=utf-8")
   public String r2(HttpSession session) {
       String fullname = null;
       Object user = session.getAttribute(User.SESSION_USER_KEY);
       if (user != null) {
           fullname = ((User) user).getFullname();
       } else {
           fullname = "匿名";
       }
       return fullname + " 访问资源2";
   }
   ```

3. 实现授权拦截器

   在 `interceptor` 包下定义 `SimpleAuthenticationInterceptor` 拦截器，实现授权拦截：

   3.1 校验用户是否登录

   3.2 校验用户是否拥有操作权限

   ```java
   @Component
   public class SimpleAuthenticationInterceptor implements HandlerInterceptor {
       @Override
       public boolean preHandle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception {
           // 在这个方法中校验用户请求的 url 是否在用户的权限范围内
           Object object = request.getSession().getAttribute(User.SESSION_USER_KEY);
           if (object == null) {
               writeContent(response, "没有登录");
           }
           User user = (User) object;
           if (user.getAuthorities().contains("p1") && request.getRequestURI().contains("/r/r1")) {
               return true;
           }
           if (user.getAuthorities().contains("p2") && request.getRequestURI().contains("/r/r2")) {
               return true;
           }
   
           writeContent(response, "没有权限，拒绝访问");
           return false;
       }
   
       private void writeContent(HttpServletResponse response, String msg) throws IOException {
           response.setContentType("text/html; charset=utf-8");
           PrintWriter writer = response.getWriter();
           writer.write(msg);
           writer.close();
           response.resetBuffer();
       }
   }
   ```

   在 `WebConfig` 中配置拦截器，匹配 `/r/**` 的资源为受保护的系统资源，访问该资源的请求进入 `SimpleAuthenticationInterceptor` 拦截器：

   ```java
   @Autowired
   private SimpleAuthenticationInterceptor simpleAuthenticationInterceptor;
   
   @Override
   public void addInterceptors(InterceptorRegistry registry) {
       registry.addInterceptor(simpleAuthenticationInterceptor).addPathPatterns("/r/**");
   }
   ```

4. 测试：

   未登录情况下，`/r/r1` 与 `/r/r2` 均提示 “请先登录”

   张三登录情况下，由于张三有 `p1` 权限，因此可以访问 `/r/r1`，张三没有 `p2` 权限，访问 `/r/r2` 时提示 “权限不足

   李四登录情况下，由于李四有 `p2` 权限，因此可以访问 `/r/r2`，李四没有 `p1` 权限，访问 `/r/r1` 时提示 “权限不足

   测试结果全部符合预期结果

## 2.6 小结

基于 `session` 领证方式是一种常见的谁方式，至今还有非常多的系统在使用。我们在此小节使用 `Spring mvc` 技术对它进行简单实现，旨在让大家更清晰实在的了解用户认证、授权以及会话的功能意义及实现套路，也就是它们分别干了哪些事儿？大概需要怎么做？

而在正式生产项目中，我们往往会考虑使用第三方安全框架（如 `spring security、shiro` 等安全框架）来实现谁授权功能，因为这样做能一定程序提高生产力，提交软件标准化程度，另外往往这些框架的可扩展性考虑的非常全面。但是缺点也非常明显，这些通用化组件为了提高支持范围会增加很多可能我们不需要的功能，结构上也会比较抽象，如果我们不够了解它，一旦出现问题，将会很难定位

# 3. Spring Security 快速上手

## 3.1 Spring Security 介绍

`Spring Security` 是一个能够为基于 `Spring` 的企业应用系统提供声明式的安全访问控制解决方案的安全框架。由于它是 `Spring` 生态系统中的一员，因此它伴随着整个 `Spring` 生态系统不断修正、升级，在 `spring boot` 项目中加入 `spring security` 更是十分简单，使用 `spring security` 减少了为企业系统安全控制编写大量重复代码的工作

## 3.2 创建工程

### 3.2.1 创建 maven 工程

创建 `maven` 工程 `security-spring`，工程结构如下：

[![RibKJS.png](https://z3.ax1x.com/2021/06/20/RibKJS.png)](https://imgtu.com/i/RibKJS)

`pom.xml` 文件内容如下：

```xml
<?xml version="1.0" encoding="UTF-8"?>

<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">

  <parent>
    <artifactId>all</artifactId>
    <groupId>com.ch.wchya</groupId>
    <version>1.0-SNAPSHOT</version>
  </parent>

  <modelVersion>4.0.0</modelVersion>

  <artifactId>security-spring</artifactId>
  <version>1.0-SNAPSHOT</version>
  <packaging>war</packaging>

  <name>security-spring Maven Webapp</name>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    <maven.compiler.source>11</maven.compiler.source>
    <maven.compiler.target>11</maven.compiler.target>
  </properties>

  <dependencies>
    <dependency>
      <groupId>com.ch.wchya</groupId>
      <artifactId>entity</artifactId>
      <version>1.0-SNAPSHOT</version>
    </dependency>

    <dependency>
      <groupId>org.springframework</groupId>
      <artifactId>spring-webmvc</artifactId>
    </dependency>

    <dependency>
      <groupId>org.springframework.security</groupId>
      <artifactId>spring-security-web</artifactId>
    </dependency>
    <dependency>
      <groupId>org.springframework.security</groupId>
      <artifactId>spring-security-config</artifactId>
    </dependency>

    <dependency>
      <groupId>javax.servlet</groupId>
      <artifactId>javax.servlet-api</artifactId>
      <scope>provided</scope>
    </dependency>

    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.11</version>
      <scope>test</scope>
    </dependency>
  </dependencies>

  <build>
    <finalName>security-spring</finalName>
    <pluginManagement><!-- lock down plugins versions to avoid using Maven defaults (may be moved to parent pom) -->
      <plugins>
        <plugin>
          <artifactId>maven-clean-plugin</artifactId>
          <version>3.1.0</version>
        </plugin>
        <!-- see http://maven.apache.org/ref/current/maven-core/default-bindings.html#Plugin_bindings_for_war_packaging -->
        <plugin>
          <artifactId>maven-resources-plugin</artifactId>
          <version>3.0.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-compiler-plugin</artifactId>
          <version>3.8.0</version>
        </plugin>
        <plugin>
          <artifactId>maven-surefire-plugin</artifactId>
          <version>2.22.1</version>
        </plugin>
        <plugin>
          <artifactId>maven-war-plugin</artifactId>
          <version>3.2.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-install-plugin</artifactId>
          <version>2.5.2</version>
        </plugin>
        <plugin>
          <artifactId>maven-deploy-plugin</artifactId>
          <version>2.8.2</version>
        </plugin>
      </plugins>
    </pluginManagement>
  </build>
</project>
```

### 3.2.2 Spring 容器配置

同 `security-springmvc` 项目：

```java
@Configuration
@ComponentScan(basePackages = "com.ch.wchya.security.spring", excludeFilters = {@ComponentScan.Filter(type = FilterType.ANNOTATION, value = Controller.class)})
public class ApplicationContext {
    // 在此配置除了 Controller 的其它 bean，比如：数据库连接池、事务管理器、业务 bean 等
}
```

> 注意：`basePackages` 的内容有变化

### 3.2.3 Servlet Context 配置

与 `security-springmvc` 项目相比，删除了很多内容，尤其是 `spring-security` 会自己实现拦截器，不再需要我们手动注册的那种拦截器了：

```java
@Configuration
@EnableWebMvc
@ComponentScan(basePackages = "com.ch.wchya.security.spring", includeFilters = {@ComponentScan.Filter(type = FilterType.ANNOTATION, value = Controller.class)})
public class WebConfig implements WebMvcConfigurer {

    @Override
    public void configureViewResolvers(ViewResolverRegistry registry) {
        InternalResourceViewResolver viewResolver = new InternalResourceViewResolver();
        viewResolver.setPrefix("/WEB-INF/views");
        viewResolver.setSuffix(".jsp");
        registry.viewResolver(viewResolver);
    }
}
```

### 3.2.4 加载 Spring 容器

同 `security-springmvc` 项目：

```java
public class SpringApplicationInitializer extends AbstractAnnotationConfigDispatcherServletInitializer {
    @Override
    protected Class<?>[] getRootConfigClasses() {
        return new Class[]{ApplicationContext.class};
    }

    @Override
    protected Class<?>[] getServletConfigClasses() {
        return new Class[]{WebConfig.class};
    }

    @Override
    protected String[] getServletMappings() {
        return new String[]{"/"};
    }
}
```

## 3.3 认证

### 3.3.1 认证页面

`Spring Security` 默认提供认证页面，不需要额外开发

[![RibPRe.png](https://z3.ax1x.com/2021/06/20/RibPRe.png)](https://imgtu.com/i/RibPRe)

### 3.3.2 安全配置

`Spring Security` 提供了用户名密码登录、退出、会话管理等认证功能，只需要配置即可使用

1. 在 `config` 包下定义 `WebSecurityConfig`，安全配置的内容包括：用户信息、密码编码器、安全拦截机制

   ```java
   @EnableWebSecurity
   public class WebSecurityConfig extends WebSecurityConfigurerAdapter {
   
       // 定义用户信息服务（查询用户信息）
       @Bean
       public UserDetailsService userDetailsService() {
           InMemoryUserDetailsManager manager = new InMemoryUserDetailsManager();
           manager.createUser(User.withUsername("zhangsan").password("123").authorities("p1").build());
           manager.createUser(User.withUsername("lisi").password("456").authorities("p2").build());
           return manager;
       }
   
       // 定义密码编码器
       @Bean
       public PasswordEncoder passwordEncoder() {
           return NoOpPasswordEncoder.getInstance();
       }
   
       // 安全拦截机制（最重要）
       @Override
       protected void configure(HttpSecurity http) throws Exception {
           http.authorizeRequests()
                   .antMatchers("/r/**").authenticated()    //  所有/r/**的请求必须认证通过
                   .anyRequest().permitAll()                //  除了/r/**，其它的请求可以访问
                   .and()
                   .formLogin()                             // 允许表单登录
                   .successForwardUrl("/login-success");    // 自定义登录成功的页面地址
       }
   }
   ```

   在 `userDetailsService()` 方法中，我们返回了一个 `UserDetailService` 给 `spring` 容器，`sprign security` 会使用它来获取用户信息。我们暂时使用 `InMemoryUserDetailsManager` 实现类，并在其中分别创建了 `zhangsan、lisi` 两个用户，设置密码和权限

   在 `configure()` 中，我们通过 `HttpSecurity` 设置了安全拦截规则，其中包含了以下内容：

   1.1 `url` 匹配 `/r/**` 的资源，经过认证后才能访问

   1.2 其它 `url` 完全开放

   1.3 支持 `form` 表单认证，认证成功后转身 `/login-success`

   关于 `HttpSecurity` 的配置清单请参考附录 `HttpSecurity`

2. 加载 `WebSecurityConfig`

   修改 `SpringApplicationInitializer` 的 `getRootConfigClasses()` 方法，添加 `WebSecurityConfig.class`

   ```java
   @Override
   protected Class<?>[] getRootConfigClasses() {
       return new Class[]{ApplicationContext.class, WebSecurityConfig.class};
   }
   ```

### 3.3.2 Spring Security 初始化

`Spring Security` 初始化，这里有两种情况：

* 若当前环境没有使用 `Spring` 或者 `Spring mvc`，则需要将 `WebSecurityConfig`（`Spring Security` 的配置类）传入超类，以确保获取配置，并创建 `spring context`

  在 `init` 包下定义 `SpringSecurityApplicationInitializer`：

  ```java
  public class SpringSecurityApplicationInitializer extends AbstractSecurityWebApplicationInitializer {
    public SpringSecurityApplicationInitializer() {
      super(WebSecurityConfig.class);
    }
  }
  ```

* 相反，若当前环境已经使用 `spring`，我们应该在现有的 `springContext` 中注册 `spring security`（上一步已经将 `WebSecurityConfig` 加载至 `rootcontext`），此方法可以什么都不做

在 `init` 包下定义 `SpringSecurityApplicationInitializer`：

```java
public class SpringSecurityApplicationInitializer extends AbstractSecurityWebApplicationInitializer {
  public SpringSecurityApplicationInitializer() {
    // super(WebSecurityConfig.class); 如果是上面说的第一种情况，去掉这句的注释
  }
}
```

### 3.2.3 默认根路径请求

在 `WebConfig.java` 中添加默认请求根路径跳转到 `/login`，此 `url` 为 `spring security` 提供：

```java
// 默认 url 根路径跳转到 /login, 此 url 为 spring security 提供
@Override
public void addViewControllers(ViewControllerRegistry registry) {
  registry.addViewController("/").setViewName("redirect:/login");
}
```

`spring security` 默认提供的登录页面

### 3.2.4 认证成功页面

在安全配置中，认证成功将跳转到 `/login-success`，代码如下：

```java
@Override
protected void configure(HttpSecurity http) throws Exception {
    http.authorizeRequests()
            .antMatchers("/r/**").authenticated()    //  所有/r/**的请求必须认证通过
            .anyRequest().permitAll()                          //  除了/r/**，其它的请求可以访问
            .and()
            .formLogin()                                        // 允许表单登录
            .successForwardUrl("/login-success");               // 自定义登录成功的页面地址
}
```

`spring security` 支持 `form` 表单认证，认证成功后转身 `/login-success`

在 `LoginController` 中定义 `/login-success`：

```java
@RequestMapping(value = "/login-success", produces = "text/plain; charset=utf-8")
public String loginSuccess() {
    return "登录成功";
}
```

### 3.2.5 测试

1. 启动项目：

   ![RibPRe.png](https://z3.ax1x.com/2021/06/20/RibPRe.png)

   页面会根据 `WebConfig` 中 `addViewController` 配置的规则，跳转至 `/login`，`/login` 是 `spring security` 提供的登录页面

2. 登录

   输入错误的用户名、密码：

   [![RiOmIx.png](https://z3.ax1x.com/2021/06/20/RiOmIx.png)](https://imgtu.com/i/RiOmIx)

   输入正确的用户名、密码，登录成功

3. 退出

   请求 `/logout` 退出

   [![RiOIOJ.png](https://z3.ax1x.com/2021/06/20/RiOIOJ.png)](https://imgtu.com/i/RiOIOJ)

   退出后来到登录页面

   [![RiXkff.png](https://z3.ax1x.com/2021/06/20/RiXkff.png)](https://imgtu.com/i/RiXkff)

## 3.4 授权

实现授权需要对用户的访问进行拦截校验，校验用户的权限是否可以操作指定的资源，`spring security` 默认提供授权实现方法

在 `LoginController` 添加 `/r/r1` 或 `/r/r2`

```java
@GetMapping(value = "/r/r1", produces = "text/plain; charset=utf-8")
public String r1() {
    return "访问资源1";
}

@GetMapping(value = "/r/r2", produces = "text/plain; charset=utf-8")
public String r2() {
    return "访问资源2";
}
```

修改 `WebSecurityConfig` 的内容，添加授权代码：

```java
@Override
protected void configure(HttpSecurity http) throws Exception {
    http.authorizeRequests()
            .antMatchers("/r/r1").hasAuthority("p1")
            .antMatchers("/r/r2").hasAuthority("p2")
            .antMatchers("/r/**").authenticated()    //  所有/r/**的请求必须认证通过
            .anyRequest().permitAll()                          //  除了/r/**，其它的请求可以访问
            .and()
            .formLogin()                                        // 允许表单登录
            .successForwardUrl("/login-success");               // 自定义登录成功的页面地址
}
```

测试：

* 登录成功
* 访问 `/r/r1` 和 `/r/r2`，有权限则正常访问，否则返回 403（拒绝访问）

## 3.5 小结

通过快速上手，使用 `Spring Security` 实现了认证和授权，`Spring security` 提供了基于账号和密码的认证方式，通过安全配置即可实现请求拦截，授权功能，`Spring Security` 能完成的不仅仅是这些

# 4. Spring Security 应用详解

## 4.1 集成 SpringBoot

### 4.1.1 SpringBoot 介绍

`Spring Boot` 是一套 `Spring` 的快速开发框架，基于 `Spring 4.0` 设计，使用 `Spring Boot` 开发可以避免一些繁琐的工程搭建和配置，同时它集成了大师的常用框架，快速导入依赖包，避免依赖包的冲突。基本上常用的开发框架都支持 `Spring Boot` 开发，例如：`MyBatis、Dubbo` 等，`Spring` 家族更是如此，例如：`Spring cloud、Spring mvc、Spring Security` 等，使用 `Spring Boot` 开发可以大大提高生产率，所以 `Spring Boot` 的使用率非常高

本章讲解如何通过 `Spring Boot` 开发 `Spring Security` 应用，`Spring Boot` 提供 `Spring-boot-starter-security` 用于开发 `Spring Security` 应用

### 4.1.2 创建 Maven 工程







## 4.2 工作原理

### 4.2.1 结构总览

`Spring Security` 所解决的问题就是案例访问控制，而案例访问控制功能其实就是对所有进入系统的请求进行拦截，校验每个请求是否能够访问它所期望的资源。根据前边知识的学习，可以通过 `Filter` 或 `AOP` 等技术来实现，`Spring Security` 对 `Web` 资源的保护是靠 `Filter` 实现的，所以从这个 `Filter` 来入手，逐步深入 `Spring Security` 原理

当初始化 `Spring Security`时，会创建一个名为 `SpringSecurityFilterChain` 的 `Servlet` 过滤器，类型为：`org.springframework.security.web.FilterChainProxy`，它实现了 `javax.servlet.Filter`，因此外部的请求会经过此类，下图是 `Spring Security` 过滤器链结构图：

[![Rm4FgO.md.png](https://z3.ax1x.com/2021/06/23/Rm4FgO.md.png)](https://imgtu.com/i/Rm4FgO)

`FilterChainProxy` 是一个代理，真正起作用的是 `FilterChainProxy` 中 `SecurityFilterChain` 所包含的各个 `Filter`，同时这些 `Filter` 作为 `Bean` 被 `Spring` 管理，它们是 `Spring Security` 核心，各有各的职责，但他们并不直接处理用户的 **认证**，也不直接处理用户的 **授权**，而是把它们交给了认证管理器（`AuthenticationManager`）和决策管理器（`AccessDecisionManager`）进行处理，下图是 `FilterChainProxy` 相关类的 `UML` 图示：

[![Rm5pLQ.md.png](https://z3.ax1x.com/2021/06/23/Rm5pLQ.md.png)](https://imgtu.com/i/Rm5pLQ)

`Spring Security` 功能的实现主要是由一系列过滤器链相互配合完成



















