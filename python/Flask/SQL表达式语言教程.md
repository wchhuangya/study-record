[Toc]

`SQLAlchemy` 表达式语言提供了一个使用 `Python` 构造的，表示关系型数据库结构和表达式的系统。这些构造被建模成尽可能接近底层数据库的构造，同时提供了数据库后端之间各种实现差异的少量抽象。虽然构造试图用一致的结构表示后端之间的等效概念，但它们并不隐藏特定后端子集特有的有用概念。因此，表达式语言提供了一种编写后端中性 `SQL` 表达式的方法，但不试图强制要求表达式是后端中性的。

表达式语言与 `Object Relational Mapper` 形成了对比，后者是构建在表达式语言之上的一个独特的 `API`。在对象关系教程中引入的 `ORM` 提出了一种高级抽象的使用模式，它本身就是表达式语言应用使用的一个例子，而表达式语言则提供了一个直接表示关系数据库原语结构的系统。

虽然 `ORM` 的使用模式和表达语言之间存在重叠，但它们之间的相似之处比最初可能出现的情况要浅得多。一种方法是从用户定义的域模型的角度来处理数据的结构和内容，该模型是透明地从其底层存储模型中持久化和刷新的。另一种方法是从文字模式和 `SQL` 表达式表示的角度来处理它，它们被显式地组合成数据库单独使用的消息。

成功的应用程序可以完全使用表达式语言构建，尽管应用程序需要定义自己的系统，将应用程序概念转换为单个数据库消息和单个数据库结果集。或者，在高级场景中，使用 `ORM` 构建的应用程序可以在需要特定数据库交互的特定领域中直接使用表达式语言。

下面的教程是 `doctest` 格式，这意味着每个 `>>>` 行表示可以在 `Python` 命令提示符下键入的内容，下面的文本表示预期的返回值。本教程没有先决条件。

# 版本检查

快速检查一下自己使用的版本，本教程需要至少：1.3 的版本

```python
>>> import sqlalchemy
>>> sqlalchemy.__version__
1.3.0
```

# 连接

在本教程中，我们将使用只是内存中的 `SQLite` 数据库。这是一种简单的测试方法，无需在任何地方定义实际的数据库。使用 `create_engine()` 就可以连接：

```python
>>> from sqlalchemy import create_engine
>>> engine = create_engine('sqlite:///:memory:', echo=True)
```

`echo` 标志是设置 `SQLAlchemy` 日志记录的快捷方式，它通过 `Python` 的标准日志模块完成。启用它后，我们将看到生成的所有 `SQL`。如果您正在学习本教程，并且希望生成更少的输出，请将其设置为 `false`。本教程将对弹出窗口后面的 `SQL` 进行格式化，这样它就不会妨碍我们；只需单击 `SQL` 链接就可以看到生成了什么。

`create_engine()` 的返回值是 `Engine` 的一个实例，它表示数据库的核心接口，通过处理数据库和正在使用的`DBAPI` 的详细信息的方言进行调整。在本例中，`SQLite` 方言将解释 `Python` 内置 `sqlite 3` 模块的指令。

第一次调用像 `Engine.Execute()` 或 `Engine.Connection()` 这样的方法时，引擎会建立到数据库的真正 `DBAPI` 连接，然后使用数据库发出 `SQL`。

> 连接延迟：
>
> ​	最初由 `create_engine()` 方法返回的 `Engine` 对象，并不是一创建就去连接数据库的，只有当它第一次执行数据库的任务时才会真正去连接

# 定义和创建表

`SQL` 表达式语言在大多数情况下是针对表列构造表达式的。在 `SQLAlchemy` 中，列通常由名为 `Column` 的对象表示，而且在所有情况下，列都与 `Table` 相关联。表对象及其关联子对象的集合称为数据库元数据。在本教程中，我们将显式地列出几个 `Table` 对象，但请注意，`SA` 还可以从现有数据库自动“导入”一组表对象(此过程称为表反射)。

我们使用类似于常规 `SQL CREATETABLE` 语句的 `Table` 构造来定义所有表都在一个名为元数据的目录中。我们将创建两个表，一个表示应用程序中的“用户”，另一个表示“用户”表中的每一行的零或多个“电子邮件地址”：

```python
>>> from sqlalchemy import Table, Column, Integer, String, MetaData, ForeignKey
>>> metadata = MetaData()
>>> users = Table('users', metadata,
...     Column('id', Integer, primary_key=True),
...     Column('name', String),
...     Column('fullname', String),
... )

>>> addresses = Table('addresses', metadata,
...   Column('id', Integer, primary_key=True),
...   Column('user_id', None, ForeignKey('users.id')),
...   Column('email_address', String, nullable=False)
...  )
```

