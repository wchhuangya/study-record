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
    
</b:beans>
```
