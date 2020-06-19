[Toc]

# 环境搭建

1. 创建 `maven` 工程并导入 `mybatis` 的坐标

   ```xml
   <dependency>
     <groupId>org.mybatis</groupId>
     <artifactId>mybatis</artifactId>
     <version>3.4.5</version>
   </dependency>
   ```

   

2. 创建实体类和 `dao` 的接口

3. 创建 `mybatis` 的主配置文件：`SqlMapConfig.xml`

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE configuration
           PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
           "http://mybatis.org/dtd/mybatis-3-config.dtd">
   <!--mybatis的主配置文件-->
   <configuration>
       <!--配置环境-->
       <environments default="mysql">
           <!--配置mysql的环境-->
           <environment id="mysql">
               <!--配置数据的类型-->
               <transactionManager type="JDBC"></transactionManager>
               <!--配置数据源，也叫连接池-->
               <dataSource type="POOLED">
                   <property name="driver" value="com.mysql.jdbc.Driver"/>
                   <property name="url" value="jdbc:mysql://localhost:3306/travel"/>
                   <property name="username" value="wchya"/>
                   <property name="password" value="root"/>
               </dataSource>
           </environment>
       </environments>
   
       <!--指定映射配置文件的位置，映射配置文件指的是每个dao独立的配置文件-->
     	<!-- 注意：下面的 .xml 后缀一定不能丢 -->
       <mappers>
           <mapper resource="com/ch/wchya/mybatis/dao/IUserDao.xml"/>
       </mappers>
   </configuration>
   ```

   

4. 在 `resources` 目录下根据 `IUserDao` 的包路径，创建相应的文件夹

5. 创建映射配置文件：`IUserDao.xml`

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE mapper
           PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
           "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
   
   <mapper namespace="com.ch.wchya.mybatis.dao.IUserDao">
   
       <!--配置查询所有-->
       <select id="findAll" resultType="com.ch.wchya.mybatis.domain.User">
           select * from user
       </select>
   </mapper>
   ```

   

注意事项：

1. 创建 `IUserDao.xml` 和 `IUserDao.java` 时，名称是为了和我们之前的知识保持一致。在 `mybatis` 中，把持久层的操作接口名称和映射文件叫做：`Mapper` ，所以 `IUserDao` 和 `IUserMapper` 是一样的
2. 在 `idea` 中创建目录的时候和包是不一样的（包需要创建一次 `com.ch.wchya` ，同样的目录操作只会创建一层目录 `com.ch.wchya` ）
3. `mybatis` 的映射配置文件位置必须和 `dao` 接口的包结构相同
4. 映射配置文件的 `mapper` 标签的 `namespace` 属性的取值必须是 `dao` 接口的全限定类名
5. 映射配置文件的操作配置，`id` 属性的取值必须是 `dao` 接口的方法名

当我们遵从了上面的三、四、五点之后，在开发中就无须再写 `dao` 的实现类

# 入门案例

1. 读取配置文件
2. 创建 `SqlSessionFactory` 工厂
3. 使用工厂生产 `SqlSession` 对象
4. 使用 `SqlSession` 创建 `Dao` 接口的代理方法
5. 使用代理对象执行方法
6. 释放资源

# 注解方式

1. 创建 `SqlMapConfig.xml` 配置文件

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE configuration
           PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
           "http://mybatis.org/dtd/mybatis-3-config.dtd">
   <!--mybatis的主配置文件-->
   <configuration>
       <!--配置环境-->
       <environments default="mysql">
           <!--配置mysql的环境-->
           <environment id="mysql">
               <!--配置数据的类型-->
               <transactionManager type="JDBC"></transactionManager>
               <!--配置数据源，也叫连接池-->
               <dataSource type="POOLED">
                   <property name="driver" value="com.mysql.jdbc.Driver"/>
                   <property name="url" value="jdbc:mysql://localhost:3306/travel"/>
                   <property name="username" value="wchya"/>
                   <property name="password" value="root"/>
               </dataSource>
           </environment>
       </environments>
   
       <!--如果使用注解来配置的话，此处应该使用class属性指定被注解的 dao 全限定类名-->
       <mappers>
           <mapper class="com.ch.wchya.mybatis.dao.IUserDao"/>
       </mappers>
   </configuration>
   ```

   

2. 在 `IUserDao` 中给方法添加注解

   ```java
   public interface IUserDao {
   
       @Select("select * from user")
       List<User> findAll();
   }
   ```

   