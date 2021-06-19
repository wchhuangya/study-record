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

### 2.2.2 Spring 容器配置

在 `config` 包下定义 `ApplicationConfig.java`，它对应 `web.xml` 中 `ContextLoaderListener` 的配置：

```java
@Configuration
@ComponentScan(basePackages = "com.ch.wchya.security.springmvc", excludeFilters = {@ComponentScan.Filter(type = FilterType.ANNOTATION, value = Controller.class)})
public class ApplicationContext {
    // 在此配置除了 Controller 的其它 bean，比如：数据库连接池，事务管理器，业务 bean 等
}
```

























