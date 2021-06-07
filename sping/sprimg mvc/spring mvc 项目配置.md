[Toc]



# xml 配置

## 最小配置

`mvc.xml` ：该文件可以任意起名，因为它的存放位置最终在 `web.xml` 中要进行配置

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

    <!--扫描指定包下的注解-->
    <context:component-scan base-package="com.ch.wchya.security.controller"/>

    <!--启用注解-->
    <mvc:annotation-driven/>

    <!---配置前端解析器。
         当在controller的方法中返回字符串时（并且方法没有@ResponseBody注解），springmvc会将返回的字符串添加
         下面配置中的 prefix 和 suffix，然后按照拼接后的结果查找页面
    -->
    <bean id="viewResolver" class="org.springframework.web.servlet.view.InternalResourceViewResolver">
        <property name="prefix" value="/WEB-INF/views/"/>
        <property name="suffix" value=".html"/>
    </bean>

    <!--将静态资源的处理经由 Spring MVC 框架交回 Web 应用服务器处理-->
    <mvc:default-servlet-handler/>

</beans>
```

> `mvc:default-servlet-hanlder` 知识点更详细内容可参见：[笔记：dispatcher-servlet.xml 配置](wiz://open_document?guid=7e9a3f94-4917-4527-8cbb-6c6d18243444&kbguid=&private_kbguid=e15be5f7-6ae9-11e0-be61-3e8f14b55176)

`web.xml`：该文件中主要配置将所有视图都交由 `springmvc` 的前端解析器

```xml

<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_3_1.xsd"
         version="3.1">

  <servlet>
    <servlet-name>mvc</servlet-name>
    <servlet-class>org.springframework.web.servlet.DispatcherServlet</servlet-class>
    <init-param>
      <param-name>contextConfigLocation</param-name>
      <param-value>classpath:mvc.xml</param-value>
    </init-param>
    <load-on-startup>1</load-on-startup>
  </servlet>
  <servlet-mapping>
    <servlet-name>mvc</servlet-name>
    <url-pattern>/</url-pattern>
  </servlet-mapping>
</web-app>
```

> `idea` 自动生成的 `web.xml` 文件使用的 2.2 版本，应该使用 3.1 版本，具体区别见：[web.xml 文件配置](wiz://open_document?guid=fba6bf4f-b10a-4046-b939-b508ef544d3c&kbguid=&private_kbguid=e15be5f7-6ae9-11e0-be61-3e8f14b55176)

## 接入 logback 日志

1. 导入 `logback jar` 包

    ```xml
    <dependency>
      <groupId>ch.qos.logback</groupId>
      <artifactId>logback-classic</artifactId>
    </dependency>
    ```
    
2. 在类路径下增加 `logback.xml` 配置文件

    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <!--scan:当此属性设置为true时，配置文件如果发生改变，将会被重新加载，默认值为true-->
    <!--scanPeriod:设置监测配置文件是否有修改的时间间隔，如果没有给出时间单位，默认单位是毫秒。当scan为true时，此属性失效，默认的时间间隔为1分钟-->
    <!--debug:当此属性设置为true时，将打印出logback内部日志信息，实时查看logback运行状态，默认值为false-->
    <configuration scan="true" scanPeriod="60 seconds" debug="true">
        <!--定义变量，可通过 ${log.path} 和 ${CONSOLE_LOG_PATTERN} 得到变量值-->
        <property name="log.path" value="/Users/wchya/project/logs/logback"/>
        <property name="CONSOLE_LOG_PATTERN" value="%d{yyyy-MM-dd HH:mm:ss.SSS} |-[%-5p] in %logger.%M[line-%L] -%m%n"/>
        <property name="file_name" value="security"/>
        <property name="log_level" value="debug"/>
        <!--输出到控制台-->
        <appender name="CONSOLE" class="ch.qos.logback.core.ConsoleAppender">
            <!--Threshold=即最低日志级别，此appender输出大于等于对应级别的日志（当然还要满足root中定义的最低级别）-->
            <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
                <level>${log_level}</level>
            </filter>
            <encoder>
                <!--日志格式（引用变量）-->
                <Pattern>${CONSOLE_LOG_PATTERN}</Pattern>
                <!--设置字符集-->
                <charset>UTF-8</charset>
            </encoder>
        </appender>
        <!--滚动追加到文件中-->
        <appender name="file" class="ch.qos.logback.core.rolling.RollingFileAppender">
            <!--正在记录的日志文件的路径及文件名-->
            <file>${log.path}/${file_name}.log</file>
            <!--Threshold=即最低日志级别，此appender输出大于等于对应级别的日志（当然还要满足root中定义的最低级别）-->
            <filter class="ch.qos.logback.classic.filter.ThresholdFilter">
                <level>${log_level}</level>
            </filter>
            <!--日志文件输出格式-->
            <encoder>
                <pattern>${CONSOLE_LOG_PATTERN}</pattern>
                <charset>UTF-8</charset><!--设置字符集-->
            </encoder>
            <!--日志记录器的滚动策略，按日期，按大小记录
                        文件超过最大尺寸后，会新建文件，然后新的日志文件中继续写入
                        如果日期变更，也会新建文件，然后在新的日志文件中写入当天日志-->
            <rollingPolicy class="ch.qos.logback.core.rolling.TimeBasedRollingPolicy">
                <!--新建文件后，原日志改名如下 %i=文件序号，i从0开始-->
                <fileNamePattern>${log.path}/${file_name}-%d{yyyy-MM-dd}.%i.log</fileNamePattern>
                <!--每个日志文件的最大体量-->
                <timeBasedFileNamingAndTriggeringPolicy class="ch.qos.logback.core.rolling.SizeAndTimeBasedFNATP">
                    <maxFileSize>1mb</maxFileSize>
                </timeBasedFileNamingAndTriggeringPolicy>
                <!--日志文件保留天数，1=只保留昨天的归档日志文件，不设置则保留所有日志-->
                <!--<maxHistory>1</maxHistory>-->
            </rollingPolicy>
        </appender>
    
        <root level="${log_level}">
            <appender-ref ref="CONSOLE"/>
            <appender-ref ref="file"/>
        </root>
    </configuration>
    ```



