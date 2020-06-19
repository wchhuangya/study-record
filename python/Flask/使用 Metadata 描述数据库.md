[Toc]

本章节主要讨论基本的 `Table` 、`Column` 和 `Metadata` 对象

元数据实体的集合存储在对象中，这个对象叫做 `Metadata`

```python
from sqlalchemy import *
metadata = Metadata()
```

`Metadata` 是一个容器，在它的里面使用描述的方法保存着数据库中许多不同的元素

比如说要表示一张表，就要使用 `Table` 类。该类中有两个主要的参数：表名，与表关联的 `Metadata` 对象。剩下的可选参数大都是用于描述类信息的 `Column` 对象

```python
user = Table('user', metadata,
            Column('user_id', Integer, primary_key=True),
            Column('user_name', String(16), nullable=False),
            Column('email_address', String(60)),
            Column('nickname', String(50), nullable=False)
       )
```

上面描述了一个名为 `User` 的表，它包含四列。表的主键由 `user_id` 列构成。可以为多个列分配 `primary_key=True` 标志，该标志表示多列主键，称为复合主键。

还请注意，每一列都使用与泛化类型(如 `Integer` 和 `String`)对应的对象来描述其数据类型。`SQLAlchemy` 具有数十种不同级别的特性，以及创建自定义类型的能力。

# 访问表和列

元数据对象包含我们与其关联的所有模式结构。它支持访问这些表对象的几种方法，例如 `sorted_tables` 访问器，它按照外键依赖关系的顺序返回每个 `Table` 对象的列表(也就是说，每个表都先于它所引用的表)：

```python
>>> for t in metadata.sorted_tables:
...    print(t.name)
users
addresses
```

在大多数情况下，单个表对象已经显式声明，这些对象通常作为应用程序中的模块级变量直接访问。一旦定义了一个表，它就有一组完整的访问器，这些访问器允许检查它的属性。下面是一个表的定义：

```python
employees = Table('employees', metadata,
    Column('employee_id', Integer, primary_key=True),
    Column('employee_name', String(60), nullable=False),
    Column('employee_dept', Integer, ForeignKey("departments.department_id"))
)
```

注意：此表中使用的 `ForeignKey` 对象——该构造定义了对远程表的引用，并在定义 `ForeignKeys` 中对其进行了充分描述。访问有关此表的信息的方法包括：

```python
# access the column "EMPLOYEE_ID":
employees.columns.employee_id

# or just
employees.c.employee_id

# via string
employees.c['employee_id']

# iterate through all columns
for c in employees.c:
    print(c)

# get the table's primary key columns
for primary_key in employees.primary_key:
    print(primary_key)

# get the table's foreign key objects:
for fkey in employees.foreign_keys:
    print(fkey)

# access the table's MetaData:
employees.metadata

# access the table's bound Engine or Connection, if its MetaData is bound:
employees.bind

# access a column's name, type, nullable, primary key, foreign key
employees.c.employee_id.name
employees.c.employee_id.type
employees.c.employee_id.nullable
employees.c.employee_id.primary_key
employees.c.employee_dept.foreign_keys

# get the "key" of a column, which defaults to its name, but can
# be any user-defined string:
employees.c.employee_name.key

# access a column's table:
employees.c.employee_id.table is employees

# get the table related by a foreign key
list(employees.c.employee_dept.foreign_keys)[0].column.table
```

# 创建和删除数据库表

假设你正在使用一个全新的数据库，如果你一旦定义了一些 `Table` 对象，那么你可能要做的一件事就是为这些表及其相关结构发出 `CREATE` 语句(顺便说一句，如果你已经有了一些首选的方法，比如数据库中包含的工具或现有的脚本系统--如果是这样的话，可以跳过本节-- `SQLAlchemy` 不需要使用它来创建你的表)。

发出 `CREATE` 的通常方法是对元数据对象使用 `create_all()` 。该方法将发出查询，首先检查每个表是否存在，如果找不到，则发出 `CREATE` 语句：

```python
engine = create_engine('sqlite:///:memory:')

metadata = MetaData()

user = Table('user', metadata,
    Column('user_id', Integer, primary_key=True),
    Column('user_name', String(16), nullable=False),
    Column('email_address', String(60), key='email'),
    Column('nickname', String(50), nullable=False)
)

user_prefs = Table('user_prefs', metadata,
    Column('pref_id', Integer, primary_key=True),
    Column('user_id', Integer, ForeignKey("user.user_id"), nullable=False),
    Column('pref_name', String(40), nullable=False),
    Column('pref_value', String(100))
)

SQLmetadata.create_all(engine)
```

`create_all()` 在表之间创建外键约束，这些约束通常与表定义本身相一致，因此它还按表的依赖顺序生成表。有一些选项可以更改此行为，以便使用 `ALTERTABLE`。

使用 `drop_all()` 方法类似地实现了删除所有表。此方法与 `create_all()` 完全相反——首先检查每个表的存在，然后按依赖关系的相反顺序删除表。

创建和删除单个表可以通过 `Table` 的 `create()` 和 `drop()` 方法来完成。默认情况下，这些方法的问题就是不管表是否存在，都会去创建或删除表：

```python
engine = create_engine('sqlite:///:memory:')

meta = MetaData()

employees = Table('employees', meta,
    Column('employee_id', Integer, primary_key=True),
    Column('employee_name', String(60), nullable=False, key='name'),
    Column('employee_dept', Integer, ForeignKey("departments.department_id"))
)
employees.create(engine)
```

`drop()` 方法：

```python
employees.drop(engine)
```

想要启用 “首先检查表是否存在” 的逻辑，需要给 `create()` 和  `drop()` 方法添加 `checkfirst=True` 这个参数

```python
employees.create(engine, checkfirst=True)
employees.drop(engine, checkfirst=False)
```

# 通过迁移改变 schema

虽然 `SQLAlchemy` 直接支持为模式构造发出 `CREATE` 和 `DROP` 语句，但通常通过 `ALTER`语句以及其他特定于数据库的构造来更改这些构造的能力超出了 `SQLAlchemy` 本身的范围。虽然可以很容易地发出 `ALTER` 语句和类似的手工语句，例如将字符串传递给 `Connection.Execute()` 或使用 `DDL` 构造，但使用模式迁移工具自动维护与应用程序代码相关的数据库模式是一种常见的做法。

`SQLAlchemy` 项目为此目的提供了 `Alembic` 迁移工具。`alembic` 具有高度自定义的环境和极简的使用模式，支持诸如事务性 `DDL`、自动生成“候选”迁移、生成 `SQL` 脚本的“脱机”模式以及对分支解析的支持。

`alembic` 取代 `SQLAlchemy` 迁移项目，该项目是 `SQLAlchemy` 的原始迁移工具，现在被认为是遗留的。