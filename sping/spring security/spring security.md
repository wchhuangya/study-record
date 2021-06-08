[Toc]

# 基础

## 使用 Maven 安装 Security

```xml
<!--支持独立（非Web）应用程序，方法级安全性和JDBC：-->
<dependency>
  <groupId>org.springframework.security</groupId>
  <artifactId>spring-security-core</artifactId>
</dependency>
<!--包含过滤器和相关的Web安全基础架构，可在Servlet环境中启用URL访问控制。-->
<dependency>
  <groupId>org.springframework.security</groupId>
  <artifactId>spring-security-web</artifactId>
</dependency>
<!--声明下面的依赖可以使用丰富的 Spring Security XML命名空间和注释-->
<!--Spring Security对于LDAP，ACL，CAS，OAuth和OpenID支持有自己的依赖项：Spring-Security-LDAP，Spring-Security-ACL，Spring-Security-CAS，Spring-Security-OAuth和Spring-Security-OpenID。-->
<dependency>
  <groupId>org.springframework.security</groupId>
  <artifactId>spring-security-config</artifactId>
</dependency>
```

## security 的两种配置文件写法

这种写法不需要在里面的元素上添加 `security:` 的前缀

```xml
<b:beans xmlns="http://www.springframework.org/schema/security"
         xmlns:b="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd
                  http://www.springframework.org/schema/security https://www.springframework.org/schema/security/spring-security.xsd">
    
  	<!--用于定义web相关权限控制-->
    <!--下面这句可以为我们自动生成登录页面，相当于下面内容的简写：
        <security:http>
          <security:form-login/>
          <security:http-basic/>
          <security:logout/>
       </security:http>
    -->
    <http auto-config="true">
        &lt;!&ndash;ROLE前缀是一个提示spring使用基于角色检查的标记&ndash;&gt;
        <intercept-url pattern="/**" access="hasRole('ROLE_USER')"/>
    </http>

    <authentication-manager>
        <authentication-provider>
            <user-service>
                <user name="user" password="user" authorities="ROLE_USER"/>
                <user name="admin" password="admin" authorities="ROLE_USER,ROLE_ADMIN"/>
            </user-service>
        </authentication-provider>
    </authentication-manager>
  
</b:beans>
```

第二种写法需要在前面写 `security:` 前缀

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:security="http://www.springframework.org/schema/security"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
          http://www.springframework.org/schema/beans/spring-beans.xsd
          http://www.springframework.org/schema/security
          http://www.springframework.org/schema/security/spring-security.xsd">

	<!--   <security:http>	spring过滤器链配置
					1）需要拦截什么资源
					2）什么资源什么角色权限
					3）定义认证方式HttpBasic、FormLogin(*)
					4）定义登录页面，定义登录请求地址，定义错误处理方式
	-->
	<security:http>
	
		<!-- 
			pattern 需要拦截资源
			access 拦截方式
				isFullyAuthenticated() 该资源需要认证才能访问
				isAnonymous()  只有匿名用户才可以访问，如果登录用户就不能访问了
				permitAll()    允许所有人访问
		 -->
		 
		<security:intercept-url pattern="/index" access="permitAll()"/>
		<security:intercept-url pattern="/userLogin" access="permitAll()"/>
		
		<security:intercept-url pattern="/product/add" access="hasRole('ROLE_ADMIN')"/>
		<security:intercept-url pattern="/product/update" access="hasRole('ROLE_ADMIN')"/>
		<security:intercept-url pattern="/product/delete" access="hasRole('ROLE_ADMIN')"/>
		<security:intercept-url pattern="/product/list" access="hasRole('ROLE_USER')"/>
		
		<security:intercept-url pattern="/**" access="isFullyAuthenticated()"/>
		<!--  <security:http-basic/>
					使用HttpBasic方式进行登录
		-->
		<!--<security:http-basic/>-->
		
		<!-- 
			login-page	自定义登录界面
			login-processing-url	登录请求地址
			authentication-success-handler-ref	自定义登录成功逻辑
			authentication-failure-handler-ref	自定义登录失败逻辑
		 -->
		<security:form-login login-page="/userLogin" login-processing-url="/securityLogin" default-target-url="/index" authentication-success-handler-ref="myAuthenticationSuccessHandler" authentication-failure-handler-ref="myAuthenticationFailtureHandler"/>
		
		
		<!-- 自定义权限不足处理 -->
		<security:access-denied-handler error-page="/error"/>
		
		
		<!-- 关闭Spring Security CSRF机制 -->
		<security:csrf disabled="true"/>
	</security:http>
	
	<!--  
		security:authentication-manager 认证管理器
			1）认证信息提供方式（账户名、密码、当前用户权限）
	
	-->
	 <security:authentication-manager>
        <security:authentication-provider user-service-ref="myUserDetailService">
         	<!-- 硬编码方式 -->
         	<!-- {MD5}e10adc3949ba59abbe56e057f20f883e -->
           	<!--  <security:user-service>
                <security:user name="admin" password="{noop}123456" authorities="ROLE_ADMIN"/>
                <security:user name="Lisi" password="{noop}123456" authorities="ROLE_USER"/>
            </security:user-service>-->
            
            
        </security:authentication-provider>
    </security:authentication-manager>

	<bean id="myUserDetailService" class="com.learn.security.security.MyUserDetailService"></bean>
	
	<bean id="myAuthenticationSuccessHandler" class="com.learn.security.security.MyAuthenticationSuccessHandler"></bean>
	
	<bean id="myAuthenticationFailtureHandler" class="com.learn.security.security.MyAuthenticationFailtureHandler"></bean>
</beans>
```

## 约定

### CSRF/XSRF

默认地，为了防止 `CSRF` 攻击，`spring security` 的 `xml` 配置中，对于注销操作的要求是：

* `HTTP` 方法必须是 `POST` 类型
* `CSRF` 的 `token` 必须添加到 `request` 域中，这样，你在 `ServletRqeust` 请求中，可以通过属性 `_csrf.token` 来获取 `token` 的值，可以通过 `_csrf.parameterName` 来获取 `key` 值

> `CSRF` ：`Cross-site request forgery`，跨站请求伪造， 是一种挟制用户在当前已登录的 `Web` 应用程序上执行非本意的操作的攻击方法
>
> 它利用了 `web` 中用户身份验证的一个漏洞：**简单的身份验证只能保证请求发自某个用户的浏览器，却不能保证请求本身是用户自愿发出的**。 
>
> 防御措施：
>
> 令牌同步模式、检查 `Referer` 字段、添加校验 `token`

# 项目

## 最小项目——java配置

`com.ch.wchya.security.config.SecurityConfig.java` 文件，该类的作用：

* 为应用的每一个 `URL` 都添加认证
* 生成登录表单
* 可以让 用户名为：`user`，密码为：`password` 的用户登录
* 可以让用户注销

```java
package com.ch.wchya.security.config;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.security.config.annotation.authentication.builders.AuthenticationManagerBuilder;
import org.springframework.security.config.annotation.web.configuration.EnableWebSecurity;

@EnableWebSecurity
public class SecurityConfig {

  	/**
     * configureGlobal 这个方法名叫什么真的不要紧，但是，类上一定要有 @EnableWebSecurity、@EnableGlobalMethodSecurity、@EnableGlobalAuthentication
     * 这三个注解中的任一一个，用于配置 AuthenticationManagerBuilder
     */
    @Autowired
    public void configureGlobal(AuthenticationManagerBuilder auth) throws Exception {
        auth
            .inMemoryAuthentication()
                .withUser("user").password("{noop}password").roles("USER");
    }
}
```

`com.ch.wchya.security.config.SecurityWebApplicationInitializer.java` 文件

```java
package com.ch.wchya.security.config;

import org.springframework.security.web.context.AbstractSecurityWebApplicationInitializer;

/**
 * 该类做了下面的事情：
 * 1. 为应用的每个 URL 自动注册名为 springSecurityFilterChain 的过滤器
 * 2. 添加一个 ContextLoaderListener，用于加载 SecurityConfig
 */
public class SecurityWebApplicationInitializer extends AbstractSecurityWebApplicationInitializer {
    public SecurityWebApplicationInitializer() {
        super(SecurityConfig.class);
    }
}
```

`index.jsp` 文件

```jsp
<%@ page contentType="text/html;charset=UTF-8" language="java" %>
<%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
<html>
<head>
    <title>Title</title>
</head>
<body>
    <a href="/student/index">学生页面</a>
    Hello <b><c:out value="${pageContext.request.remoteUser}"/></b>
    <p>
        <c:url var="logoutUrl" value="/logout"/>
        <form class="form-inline" action="${logoutUrl}" method="post">
            <input type="submit" value="Log out" />
            <input type="hidden" name="${_csrf.parameterName}" value="${_csrf.token}"/>
        </form>
    </p>
</body>
</html>
```

## 最小项目——xml配置

`webapp/WEB-INF/spring/security.xml`

```
<b:beans xmlns="http://www.springframework.org/schema/security"
         xmlns:b="http://www.springframework.org/schema/beans"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://www.springframework.org/schema/beans https://www.springframework.org/schema/beans/spring-beans.xsd
                  http://www.springframework.org/schema/security https://www.springframework.org/schema/security/spring-security.xsd">

    <http />

    <user-service>
        <user name="user" password="{noop}password" authorities="ROLE_USER"/>
    </user-service>

</b:beans>
```

`resources/mvc.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xmlns:context="http://www.springframework.org/schema/context"
       xmlns:tx="http://www.springframework.org/schema/tx"
       xmlns:mvc="http://www.springframework.org/schema/mvc"
       xmlns:aop="http://www.springframework.org/schema/aop"
       xsi:schemaLocation="http://www.springframework.org/schema/beans
        http://www.springframework.org/schema/beans/spring-beans.xsd
        http://www.springframework.org/schema/context 
        http://www.springframework.org/schema/context/spring-context.xsd 
        http://www.springframework.org/schema/tx 
        http://www.springframework.org/schema/tx/spring-tx.xsd
        http://www.springframework.org/schema/mvc 
        http://www.springframework.org/schema/mvc/spring-mvc.xsd
        http://www.springframework.org/schema/aop 
        http://www.springframework.org/schema/aop/spring-aop.xsd">

    <context:component-scan base-package="com.ch.wchya.security.controller"/>

    <mvc:annotation-driven/>

    <bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/views/"/>
        <property name="suffix" value=".html"/>
    </bean>

    <mvc:default-servlet-handler/>

</beans>
```

`webapp/WEB-INF/web.xml`

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
         version="3.1">

  <!--把定义了根应用上下文的 xml 文件位置，指定给 ContextLoaderListener-->
  <context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>/WEB-INF/spring/security.xml</param-value>
  </context-param>

  <servlet>
    <servlet-name>mvc</servlet-name>
    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
    <init-param>
      <param-name>contextConfigLocation</param-name>
      <param-value>classpath:mvc.xml</param-value>
    </init-param>
  </servlet>
  <servlet-mapping>
    <servlet-name>mvc</servlet-name>
    <url-pattern>/</url-pattern>
  </servlet-mapping>

  <!--spring security 配置-->
  <!--把springSecurityFilterChain过滤器注册给应用的每一个URL-->
  <filter>
    <filter-name>springSecurityFilterChain</filter-name>
    <filter-class>org.springframework.web.filter.DelegatingFilterProxy</filter-class>
  </filter>
  <filter-mapping>
    <filter-name>springSecurityFilterChain</filter-name>
    <url-pattern>/*</url-pattern>
  </filter-mapping>

  <!--在启动时，加载web应用的根应用上下文。随后，通过 WebApplicationContextUtils.getWebApplicationContext(servletContext) 方法，应用根上下文可用 -->
  <listener>
    <listener-class>org.springframework.web.context.ContextLoaderListener</listener-class>
  </listener>
</web-app>
```

`jsp` 文件同 `最小项目——java配置`

## 自定义登录表单

> 本示例基于上一个示例

`HttpSecurity` 里配置方法的默认配置如下：

```java
protected void configure(HttpSecurity http) throws Exception {
  http
    	.authorizeRequests()
    			.anyRequest().authenticated() // ①
    			.and()
    	.formLogin()											// ②
    			.and()
    	.httpBasic();											// ③
}

// 上面的默认配置确认了以下几件事情：
// ①. 每个请求都需要认证过的用户才能访问
// ②. 支持基于表单的认证
// ③. 支持 Http 的基本认证
```

打开上个示例的 `SecurityConfig` 类，在里面添加方法：

```java
@Override
protected void configure(HttpSecurity http) throws Exception {
    http
        .authorizeRequests()
            .anyRequest().authenticated()
            .and()
        .formLogin()
            .loginPage("/login");
}

// 代码中的最后一句：.loginPage("/login") 告诉 Security：
// 1. 如果需要认证，把网页重定向到 /login
// 2. 当 /login 被访问时，应用程序负责对页面进行渲染
// 3. 如果认证失败，把网页重定向到 /login?error（这是因为还没有对 error 页面进行指定）
// 4. 当 /login?error 被访问时，应用程序负责对页面进行渲染
// 5. 如果成功注销，把网页重定向到 /login?logout（这是因为还没有对 注销 页面进行指定）
// 6. 当 /login?logout 被访问时，应用程序负责对页面进行渲染
```

写到这里，如果开始启动服务，在大多数浏览器下，会得到一个 `This webpage has a redirect loop` 的错误，为什么呢？

问题的原因是：`Spring Security` 正在保护我们自定义登录页面的访问，下面是对错误表现的一个简单描述：

* 对网站的访问请求
* `Spring Security` 发现我们未进行身份验证
* 直接访问 `/login` 地址
* 浏览器请求 `/login` 地址
* `Spring Security` 发现我们未进行身份验证
* 直接访问 `/login` 地址
* ...

修正这个问题的办法也很简单，只要告诉 `Spring Security` 任何人都可以访问 `/login` 这个地址就可以了。

```java
@Override
protected void configure(HttpSecurity http) throws Exception {
    http
        .authorizeRequests()
            .anyRequest().authenticated()
            .and()
        .formLogin()
            .loginPage("/login")
            .permitAll(); // 新增这一句即可
}
```

按照上面这样修改后，再启动服务器，新的问题来了：`Error resolving template "login"`













