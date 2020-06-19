[Toc]

# 基本概念

是官方（`sun` 公司）定义的一套操作所有关系型数据库的规则，即接口。各个数据库厂商去实现这套接口，提供数据库驱动 `jar` 包。我们可以使用这套接口（`JDBC`）编程，真正执行的代码是驱动 `jar` 包中的实现类。

# 步骤

1. 导入驱动 `jar` 包
   1. 赋值 `mysql-connector=java-x.x.x-bin.jar` 到项目的 `libs` 目录下
   2. 在 `libs` 上 `右键 -> Add as Library`
2. 注册驱动
3. 获取数据库连接对象 `Connection`
4. 定义 `sql`
5. 获取执行 `sql` 语句的对象 `Statement`
6. 执行 `sql` ，接受返回结果
7. 处理结果
8. 释放资源

# 对象详解

## DriverManager

驱动管理对象。主要功能：

* 注册驱动

  * `public static void registerDriver(Driver driver)throws SQLException` : 注册给定的驱动程序 

  * 在写代码的时候使用：`Class.forName("com.mysql.jdbc.Driver")`

    > mysql 5 之后的驱动 jar 包可以省略注册驱动的步骤

* 获取数据库连接

  * `public static Connection getConnection(String url, String user, String password) throws SQLException` ：尝试建立与给定数据库URL的连
  * `url` ：指定连接的路径。如果连接的是本机 `mysql` 服务器，并且 `mysql` 服务默认端口是 3306，则 `url` 可以简写为：`jdbc:mysql:///数据库名`

## Connection

数据库连接对象。可以管理数据库事务：

* 开启事务：`setAutoCommit(boolean autoCommit)` ，设置该方法的参数为 `false` ，即开启事务
* 提交事务：`commit()`
* 回滚事务：`rollback()`

## Statement

执行 `sql` 的对象。

## ResultSet

结果集对象，封装查询结果

* `boolean next()` ：游标向下移动一行，判断当前是否是最后一行末尾（是否有数据），如果是，返回 `false` ，如果不是，返回 `true`
* `getXxx(参数)` 
  * `Xxx` 代表数据类型，如 `getInt()  getSting()` 等
  * 参数
    * `int` ：代表列的编号（从 1 开始），如 `getString(1)` 
    * `String` ：代表列的名称，如 `getDouble("balance")`
* 使用步骤
  1. 游标向下移动一行：`while (rs.next()) {// 有数据，获取数据}`
  2. 判断是否有数据
  3. 获取数据

## PreparedStatement

执行 `sql` 的对象。

`sql` 注入：在拼接 `sql` 时，有一些 `sql` 的特殊关键字与字符串的拼接，会造成安全性的问题

预编译 `sql` ：参数使用 ？作为占位符

使用步骤：

1. 导入驱动
2. 注册驱动
3. 获取数据库连接对象 `Connection`
4. 定义 `sql` ，`sql` 的参数使用占位符，如：`select * from user where username = ? and password = ?`
5. 获取执行 `sql` 语句的对象 `PreparedStatement` ，使用方法：`Connection.preparedStatement(sql)`
6. 给 ？赋值，使用：`setXxx(参数1，参数2)` ，参数 1 指 ？的位置编号，从 1 开始，参数 2 指 ？的值
7. 执行 `sql` 接受返回结果，不需要传递 `sql` 语句
8. 处理结果
9. 释放资源

# 事物

一个包含多个步骤的业务操作，如果这个业务操作被事务管理，则这多个步骤要么同时成功，要么同时失败。

## 使用 Connection 对象管理事物

* 开启事务：`setAutoCommit(boolean autoCommit)` ，设置该方法的参数为 `false` ，即开启事务。在执行 `sql` 之前开启事务
* 提交事务：`commit()` ，当所有 `sql` 都执行完提交事务
* 回滚事务：`rollback()` ，在 `catch` 中回滚事务

# 数据库连接池

数据库连接池，就是一个容器，存放数据库连接的容器。

当系统初始化好后，容器被创建，容器中会申请一些连接对象，当用户来访问数据库时，从容器中获取连接对象，用户访问完之后，会将连接对象归还给容器。

## 好处

1. 节约资源
2. 用户访问高效

## 实现

* 标准接口：`javax.sql.DataSource`
* 一般由数据库厂商来实现

## c3p0

1. 导入 `jar` 包（两个）：`c3p0-x.x.x.x.jar` 、`mchange-commons-java-x.x.x.jar`
   * 不要忘记导入数据库驱动的 `jar` 包
2. 定义配置文件
   * 名称：`c3p0.properties` 或者 `c3p0-config.xml`
   * 路径：直接将文件放在 `src` 目录下即可

3. 创建核心对象——数据库连接池对象：`ComboPooledDataSource`
4. 获取连接：`getConnection`

## Druid

1. 导入 `jar` 包：`druid-x.x.x.jar`
2. 定义配置文件
   * 是 `properties` 形式的
   * 可以叫任意名称，可以放在任意目录下
3. 使用 `Properties` 加载配置文件
4. 通过工厂获取数据库连接池对象：`DruidDataSourceFactory`
5. 获取连接：`getConnection`

# Spring JDBC

`Spring` 框架对 `JDBC` 的简单封装，提供了一个 `JDBCTemplate` 对象简化 `JDBC` 的开发。

1. 导入 `jar` 包

   <img src="/Users/wchya/own/markdown/imgs/image-20200506210601820.png" alt="image-20200506210601820" style="zoom:50%;" />

2. 创建 `JdbcTemplate` 对象，依赖于数据源 `DataSource`

   * `JdbcTemplate jdbcTemplate = new JdbcTemplate(ds);`

3. 调用 `JdbcTemplate` 的方法来完成 `CRUD` 的操作

   * `update()` ：执行 `DML` 语句（增删改语句）
   * `queryForMap()` ：查询结果将结果集封装为 `map` 集合，将列名作为 `key` ，将值作为 `map` ，将这条记录封装为一个 `Map`
     * 注意：这个查询结果的长度只能是 1
   * `queryForList()` ：查询结果将结果集封装为 `list` 集合
     * 将每一条结果封装为一个 `Map` 集合，再将 `Map` 集合装载到 `List` 集合中
   * `query()` ：查询结果，将结果封装为 `JavaBean` 对象
     * 参数为 `RowMapper` ，一般我们使用 `BeanPropertyRowMapper` 实现类，可以完成数据到 `JavaBean` 的自动封装 `new BeanPropertyRowMapper<类型>(类型.class)`
     * 注意：在使用 `BeanPropertyRowMapper` 时，要求类型都是对象，不能是简单数据类型，比如：应该定义为 `Interger` ，不能使用 `int`
   * `queryForObject()` ：查询结果，将结果封装为对象
     * 一般用于聚合函数的查询



















