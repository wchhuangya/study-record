[toc]

<a id="start"></a>

# 快速开始

`Flask-SQLAlchemy` 使用起来很有趣，它对于一般的应用来说是难以置信的简单，对于大型应用来说它又比较容易进行扩展。有关完整的指南，请查看 `SQLAlchemy` 类 `API` 的说明文档。

## 最小化应用

在 `Flask` 应用中，一般的最常见情况就是：所有你需要做的只是创建 `Flask` 应用，加载配置选项，创建 `SQLAlchemy` 对象，并把应用当做参数传递给它。

`SQLAlchemy` 对象成功创建后，它就包含了来自于 `sqlalchemy` 和 `sqlalchemy.orm` 的所有功能和助手类。此外，它还提供了一个名为 `Model` 的类，该类是一个基类，基于它可以声明其他的模型：

```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql://user:pwd@localhost:3306/database'
db = SQLAlchemy(app)

class User(db.Model):
  id = db.Column(db.Integer, primary_key=True)
  username = db.Column(db.String(80), unique=True, nullable=False)
  email = db.Column(db.String(120), unique=True, nullable=False)
  
  def __repr__(self):
    return '<User %r>' % self.username
```

要创建初始的数据库，只需要在 `Python` 的交互式环境下引入上面的 `db` 对象，然后运行该对象的 `SQLAlchemy.create_all()` 方法，这样，就可以创建表和数据库了。

```python
>>> from yourapplication import db
>>> db.create_all()
```

执行完上面的程序，“嘣”的一声数据库就创建好了，接着，让我们添加一些数据吧：

```python
>>> from yourapplication import User
>>> admin = User(username='admin', email='admin@example.com')
>>> guest = User(username='guest', email='guest@example.com')
```

这时，这些数据还没有被添加到数据库中，我们接下来要这样做：

```python
>>> db.session.add(admin)
>>> db.session.add(guest)
>>> db.session.commit()
```

从数据库中获取数据简单的就像一一样：

```python
>>> User.query().all()
[<User u'admin'>, <User u'guest'>]
>>> User.query().filter_by(username='admin').first()
<User u'admin'>
```

注意：为什么从头到尾我们在 `User` 类中就没有定义 `__init__` 方法呢？这是因为 `SQLAlchemy` 给所有的模型类都添加了一个隐式的构造器，该构造器可以接受关键字参数，并把它们赋值给类里面列字段和关系。如果你出于某种考虑要重写这个构造器，强烈建议构造器参数使用双星号字段参数： `**kwargs` ，并在构造器的一开始调用父类的构造器，传递此参数来保护这种行为：

```python
class Foo(db.Model):
  # ...
  def __init__(**kwargs):
    super(Foo, self).__init__(**kwargs)
    # 做一些自定义的操作
```

## 简单的关系

`SQLAlchemy` 可以连接到关系型数据库，它比较擅长处理数据之间的关系。所以，下面的实例就展示了应用如何处理有关系的两张表：

```python
from datetime import datetime

class Post(db.Model):
  id = db.Column(db.Integer, primary_key=True)
  title = db.Column(db.String(80), nullable=False)
  body = db.Column(db.Text, nullable=False)
  pub_date = db.Column(db.DateTime, nullable=False, default=datetime.utcnow)
  
  category_id = db.Column(db.Integer, db.ForeignKey('category.id'), nullable=False)
  category = db.relationship('Category', backref=db.backref('posts', lazy=True))
  
  def __repr__(self):
        return '<Post %r>' % self.title

class Category(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(50), nullable=False)

    def __repr__(self):
        return '<Category %r>' % self.name
```

创建对象：

```python
>>> py = Category(name='Python')
>>> Post(title='Hello Python!', body='Python is pretty cool', category=py)
>>> p = Post(title='Snakes', body='Ssssssss')
>>> py.posts.append(p)
>>> db.session.add(py)
```

如上所示，没有把 `Post` 对象添加到 `session` 中，这是因为 `Category` 是 `session`  的一部分，当 `Category` 被添加时，所有与它相关联的对象也都会被添加，在这些关联对象创建之前或之后调用 `db.session.add()` 方法都可以。关联关系的创建可以在关系的任意一方进行——也就是说，可以在 `Category` 中创建一个 `Post`，也可以在 `Category` 的 `Post` 列表中添加一项。

让我们打印一下 `Post` 。因为关系被设置为 `lazy-loaded` ，因此，会从数据库中读取 `Post` 数据，但是，你不会注意到这究竟有什么不同——因为从数据库读取列表的速度实在是太快了：

```python
>>> py.posts
[<Post 'Hello Python!'>, <Post 'Snakes'>]
```

虽然延迟加载一种关系是非常快的，但当你最终在循环中触发多个对象的额外查询时，它很容易成为一个主要的瓶颈。对于这种情况，`SQLAlchemy` 允许你在查询级别重写加载策略。如果你想要一个查询来加载所有类别及其帖子，你可以这样做：

```python
>>> from sqlalchemy.orm import joinedload
>>> query = Category.query.options(joinedload('posts'))
>>> for category in query:
...     print category, category.posts
<Category u'Python'> [<Post u'Hello Python!'>, <Post u'Snakes'>]
```

如果希望获得该关系的查询对象，可以使用 `WITH_PARY()` 。例如，让我们排除关于 `Snake` 的帖子：

```python
>>> Post.query.with_parent(py).filter(Post.title != 'Snakes').all()
[<Post 'Hello Python!'>]
```

## 要点

关于 `SQLAlchemy` ，你需要掌握以下要点：

1. `SQLAlchemy` 可以做以下的事情：
   1. 包含 `sqlalchemy` 和 `sqlalchemy orm` 的所有函数和类
   2. `session`  ：预先配置好的作用域会话
   3. `metadata`
   4. `engine`
   5. `SQLAlchemy.create.all()` 、 `SQLAlchemy.drop.all()` ：通过模型对象创建和删除所有的表
   6. `Model` ：一个配置好的模型类的基类
2. `Model` 基类的行为就像是一个普通的 `Python` 类，但是它关联着一个 `query` 属性，可以用来查询模型的数据
3. 必须得提交 `session` ，但是在请求的最后可以不用移除 `session` ，`Flask-SQLAlchemy` 会替你做这件事情的

# 上下文环境介绍

如果你只打算在单应用中使用，那你大可以跳过这一章。只需要把你的应用实例传给 `SQLAlchemy` ，按照正常的设置就可以。但是，如果你想在几个应用中使用，或者在函数中动态创建应用，那你需要好好地阅读本篇。

如果把应用定义在一个函数中，但是 `SQLAlchemy` 对象是全局的，那么，`SQLAlchemy` 对象如何能知道应用是那个呢？答案就是 `init_app()` 函数：

```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

db = SQLAlchemy()

def create_app():
  app = Flask(__name__)
  db.init_app(app)
  return app
```

上面代码的功能就是：让 `app` 准备与 `SQLAlchemy` 协同一起工作。但是这只是准备，其实还没有真正的把 `SQLAlchemy` 绑定到你的应用上，这是因为程序中可能会有两个或者更多的应用被创建。

那么，`SQLAlchemy` 是如何了解你的应用程序的呢？那就是你必须设置一个应用程序上下文。如果你是在 `Flask` 视图函数或 `CLI` 命令行中工作，则会自动发生这种情况。但是，如果你在交互式 `shell` 中工作，则必须自己进行操作(请参见创建应用程序上下文)。

如果尝试在上下文之外执行数据库操作，会出现下面的错误：

`No application found. Either work inside a view function or push an application context.`

简而言之，就是做了下面的事情：

```python
>>> from yourapp import create_app
>>> app = create_app()
>>> app.app_context().push()
```

或者，使用 `with` 语句来处理设置和删除：

```python
def my_function():
    with app.app_context():
        user = db.User(...)
        db.session.add(user)
        db.session.commit()
```

`Flask-SQLAlchemy` 中的一些函数也可以选择地接受要操作的应用程序：

```python
>>> from yourapp import db, create_app
>>> db.create_all(app=create_app())
```

# 配置

以下配置值存在于 `Flask-SQLAlchemy` 中。`Flask-SQLAlchemy` 从你的主 `Flask` 配置中加载这些值，可以以各种方式填充这些值。请注意，其中一些不能在引擎创建后进行修改，因此请确保尽早进行配置，而不是在运行时对它们进行修改。

## 配置项

目前，下面的配置项列表都可以被插件识别：

| 配置项                         | 解释                                                         |
| ------------------------------ | ------------------------------------------------------------ |
| SQLALCHEMY_DATABASE_URI        | 连接数据库使用的 URI ：<br />`sqlite:////tmp/test.db`<br />`mysql://username:password@server:port/db` |
| SQLALCHEMY_BINDS               | 将绑定键映射到 `SQLAlchemy` 连接 `URI` 的字典。有关绑定的详细信息，请参阅多数据库绑定 |
| SQLALCHEMY_                    | 如果设置为 `True`，`SQLAlchemy` 将记录向 `stderr` 发出的所有语句，这对于调试非常有用。 |
| SQLALCHEMY_RECORD_QUERIES      | 可用于显式禁用或启用查询记录。查询记录自动发生在调试或测试模式下。有关更多信息，请参见 `get_debug_queries()`。 |
| SQLALCHEMY_NATIVE_UNICODE      | 可用于显式禁用本机 `Unicode` 支持。这对于某些数据库适配器(比如`Ubuntu` 版本上的 `PostgreSQL` )来说是必需的，当与指定无编码数据库的不正确的数据库默认值一起使用时。<br />2.4 版本过期，将在 3.0 版本移除 |
| SQLALCHEMY_POOL_SIZE           | 数据库池的大小。默认为引擎的默认值(通常为5)。<br />2.4 版本过期，将在 3.0 版本移除 |
| SQLALCHEMY_POOL_TIMEOUT        | 指定池的连接超时(秒)<br />2.4 版本过期，将在 3.0 版本移除    |
| SQLALCHEMY_POOL_RECYCLE        | 自动回收连接的秒数。对于MySQL来说，这是必需的，默认情况下，它会在空闲8小时后移除连接。注意，如果使用 `MySQL`，则 `Flask-SQLAlchemy` 会自动将其设置为2小时。一些后端可能使用不同的默认超时值。有关超时的详细信息，请参阅超时。<br />2.4 版本过期，将在 3.0 版本移除 |
| SQLALCHEMY_MAX_OVERFLOW        | 控制池达到最大大小后可以创建的连接数。当这些附加连接返回到池时，它们将被断开并丢弃。<br />2.4 版本过期，将在 3.0 版本移除 |
| SQLALCHEMY_TRACK_MODIFICATIONS | 如果设置为 `True`，则 `Flack-SQLAlchemy` 将跟踪对象的修改并发出信号。默认值为 `None`，它支持跟踪，但会发出警告，表示将来默认情况下它将被禁用。这需要额外的内存，如果不需要，应该禁用。 |
| SQLALCHEMY_ENGINE_OPTIONS      | 要发送到 `create_engine()` 的关键字 `args` 的字典。还请参阅`SQLAlchemy` 的 `Engine_Options`。 |

## URI 连接格式

有关连接 `URI` 的完整列表，请转到(支持的数据库)下的 `SQLAlchemy` 文档。这里显示了一些常见的连接字符串。

`SQLAlchemy` 将引擎的源指定为 `URI`，并结合可选的关键字参数来指定引擎的选项。`URI` 的形式是：

`dialect+driver://username:password@host:port/database`

字符串中的许多部分是可选的。如果没有指定驱动程序，则选择默认驱动程序(在这种情况下，请确保不包括 `+`)。

`Postgres` :

```shell
postgresql://scott:tiger@localhost/mydatabase
```

`MySQL` :

```
mysql://scott:tiger@localhost/mydatabase
```

`Oracle` :

```
oracle://scott:tiger@127.0.0.1:1521/sidname
```

`SQLite (note that platform path conventions apply)`:

```python
# Unix/Mac (note the four leading slashes)
sqlite:////absolute/path/to/foo.db
# Windows (note 3 leading forward slashes and backslash escapes)
sqlite:///C:\\absolute\\path\\to\\foo.db
# Windows (alternative using raw string)
r'sqlite:///C:\absolute\path\to\foo.db'
```

## 使用自定义的 Metadata 和 命名约定

你可以选择使用自定义元数据对象构造 `SQLAlchemy` 对象。除此之外，你还可以与 `SQLAlchemy0.9.2` 或更高版本一起指定自定义约束命名约定。这样做对于处理数据库迁移非常重要(例如，如这里所述，使用 `alembic`)。下面是一个例子，正如 `SQLAlchemy` 文档所建议的：

```python
from sqlalchemy import MetaData
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

convention = {
    "ix": 'ix_%(column_0_label)s',
    "uq": "uq_%(table_name)s_%(column_0_name)s",
    "ck": "ck_%(table_name)s_%(constraint_name)s",
    "fk": "fk_%(table_name)s_%(column_0_name)s_%(referred_table_name)s",
    "pk": "pk_%(table_name)s"
}

metadata = MetaData(naming_convention=convention)
db = SQLAlchemy(app, metadata=metadata)
```

## 超时

某些数据库后端可能会施加不同的非活动连接超时，这会干扰 `Flask-SQLAlchemy` 的连接池。

默认情况下，`MariaDB` 被配置为有600秒的超时。这通常是很难调试的，生产环境只有像2013这样的例外：`Lost connection to MySQL server during query`

如果使用连接超时较低的后端(或预先配置的数据库作为服务)，则建议将 `SQLALCHEMY_PORECURE_ARECURE`设置为小于后端超时的值。

# 声明模型

通常，`Flask-SQLAlchemy` 的行为就像从声明扩展中选出的已经配置好的声明基类。因此，我们建议阅读`SQLAlchemy` 文档以获得完整的参考。但是，这里也记录了最常见的用例：

时刻要在脑海中保持清醒的事情：

1. 所有模型的基本类型称为 `db.Model`。它存储在你必须创建的 `SQLAlchemy` 实例中
2. `SQLAlchemy` 中需要的某些部件在 `Flask-SQLAlchemy` 中是可选的。例如，除非重写，否则将自动为你设置表名。它派生自转换为小写的类名，并将 `CamelCase` 转换为 `camel_case`。若要重写表名，请设置`__tablename__` 这个类属性。

## 简单示例

```python
class User(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(80), unique=True, nullable=False)
    email = db.Column(db.String(120), unique=True, nullable=False)

    def __repr__(self):
        return '<User %r>' % self.username
```

使用 `db.Column()` 方法定义列。列的名称是指定给它的名称。如果要在表中使用不同的名称，可以提供一个可选的第一个参数，该参数是具有所需列名的字符串。主键被标记为 `PRIMARY_KEY=True`。可以将多个键标记为主键，在这种情况下，它们成为复合主键。

上面代码中的第一个参数就是列的类型。可以直接提供，也可以调用方法来进一步对它们进行定制(比如提供长度)。以下类型是最常见的类型：

| 类型名         | Python类型         | 说明                        |
| -------------- | ------------------ | --------------------------- |
| Integer        | int                | 普通整数，32位              |
| SmallInteger   | int                | 小范围整数，通常是16位      |
| BigInteger     | int或long          | 不限精度的整数              |
| Float          | float              | 浮点数                      |
| Numeric        | decimal.Decimal    | 定点数                      |
| String(length) | str                | 变长字符串                  |
| Text           | str                | 变长字符串，经过了优化      |
| Unicode        | unicode            | 变长 Unicode 字符串         |
| UnicodeText    | unicode            | 优化后的变长 Unicode 字符串 |
| Boolean        | bool               | 布尔值                      |
| Date           | datetime.date      | 日期                        |
| Time           | dateTime.time      | 时间                        |
| DateTime       | datetimie.datetime | 日期和时间                  |

## 一对多关系

最常见的关系是一对多的关系。由于关系是在建立关系之前声明的，所以可以使用字符串引用尚未创建的类(例如，如果 `Person` 定义了一个和 `Address` 的关系，这个关系将在后面的文件中声明)。

关系用 `Relationship()`  函数表示。然而，外键必须使用  `ForeignKey` 类来另外声明：

```python
class Person(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(50), nullable=False)
    addresses = db.relationship('Address', backref='person', lazy=True)

class Address(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    email = db.Column(db.String(120), nullable=False)
    person_id = db.Column(db.Integer, db.ForeignKey('person.id'),
        nullable=False)
```

`db.Relationship()` 是做什么的？该函数返回一个可以执行多项任务的新属性。在本例中，我们告诉它指向 `Address` 类并加载其中的多个。它如何知道这将返回多个地址？因为 `SQLAlchemy` 从声明中猜测了一个有用的缺省值。如果想拥有一对一的关系，可以将 `uselist=false` 传递给 `Relationship()`。

由于没有名称或没有关联地址的电子邮件地址的人没有任何意义，所以 `nullable=false` 告诉 `SQLAlchemy` 将该列创建为 `NOTNULL` 。这在主键列中是隐含的，但最好为所有其他列指定它，以便向处理代码的其他人员清楚地表明，你确实想要一个可空的列，而不是忘记添加它。

那么，`Backref` 和 `lazy` 意味着什么呢？`backref` 是在 `Address` 类上声明新属性的简单方法。然后，还可以使用 `my_address.Person` 来获取该地址对应的那个人。`lazy` 定义了 `SQLAlchemy` 何时从数据库加载数据：

1. `select/True`(这是默认的，但显式比隐式好)意味着 `SQLAlchemy` 将使用标准 `SELECT` 语句一次加载数据。
2. `joined/false` 告诉 `SQLAlchemy` 使用 `JOIN` 语句在与父查询相同的查询中加载关系。
3. `subquery` 的工作方式类似于 `joined`，但 `SQLAlchemy` 将使用子查询。
4. `Dynamic` 是特殊的，如果有很多项，并且总是希望向它们应用额外的 `SQL` 筛选器，那么它就会很有用。
5. `SQLAlchemy` 将返回另一个查询对象，可以在加载这些项之前进一步细化它，而不是加载项。请注意，在查询时不能将其转换为不同的加载策略，因此避免使用此策略以支持 `lazy=True` 通常是一个好主意。
6. 可以使用 `Address.query.withParent(User)` 创建与动态 `user.AddressRelationship` 等价的查询对象，同时仍然能够在必要时对关系本身使用延迟或急切的加载。

可以通过使用 `backref()` 函数为 `backrefs` 定义 `lazy` 状态：

```python
class Person(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(50), nullable=False)
    addresses = db.relationship('Address', lazy='select', backref=db.backref('person', lazy='joined'))
```

## 多对多关系

如果想要使用多对多的关系，则需要定义一个用于该关系的助手表。对于此助手表，强烈建议不要使用模型，而是使用实际表：

```python
tags = db.Table('tags',
    db.Column('tag_id', db.Integer, db.ForeignKey('tag.id'), primary_key=True),
    db.Column('page_id', db.Integer, db.ForeignKey('page.id'), primary_key=True)
)

class Page(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    tags = db.relationship('Tag', secondary=tags, lazy='subquery',   				     backref=db.backref('pages', lazy=True))

class Tag(db.Model):
    id = db.Column(db.Integer, primary_key=True)
```

在这里，我们将 `Page.tag` 配置为在加载 `Page` 之后立即加载，但是它使用了一个单独的查询。这在检索一个页面时总是会产生两个查询，但是当查询多个页面时，将不会得到其他查询。

另一方面，标签的页面列表是很少需要的。例如，在检索特定页面的标记时，不需要该列表。因此，`backref` 被设置为延迟加载，第一次访问它将触发一个查询，以获取该标记的页面列表。如果需要在该列表上应用进一步的查询选项，可以切换到 `Dynamic` 策略(有上述缺点)，也可以使用 `Page.query.With_PARY(SomeTag)` 获取查询对象，然后与动态关系中的查询对象一样使用它。

# 选择、插入、删除

已经学会了声明模型，现在，是时候来从数据库查询数据了。本章将使用在 <a href="#start">快速开始</a> 章节创建的模型。

## 插入记录

在查询之前，我们必须得插入一些数据。所有的模型都有一个构造器，就是为了以防类的创建者忘记。构造器只能由你使用，就连内部的 `SQLAlchemy` 也不能使用，因此，如何定义它们完全取决于你。

插入数据需要三步：

1. 创建 `Python` 对象
2. 把它添加到 `session` 中
3. 提交 `session`

上面说的 `session` 不是 `Flask session` ，而是 `Flask SQLAlchemy session` ，它本质上是数据库事务的增强版本，下面是使用方式：

```python
>>> from yourapp import User
>>> me = User('admin', 'admin@example.com')
>>> db.session.add(me)
>>> db.session.commit()
```

在将对象添加到会话之前，`SQLAlchemy` 基本上不会将其添加到事务中。这很好，因为你仍然可以放弃更改。例如，考虑在页面上创建 `POST` 请求，但是你只希望将这个 `post` 请求传递给模板以进行预览呈现，而不是将其存储在数据库中。

然后，`add()` 函数调用添加对象。它将为数据库发出 `INSERT` 语句，但由于事务仍未提交，你将无法立即获得 `ID`。如果执行提交，将会获得一个 `ID`：

```python
>>> me.id
1
```

## 删除记录

删除和插入操作非常类似，只需要把 `add()` 方法换成 `delete()` 方法：

```python
>>> db.session.delete(me)
>>> db.session.commit()
```

## 查询记录

那么，如何从数据库中获取数据呢？为此，`Flask-SQLAlchemy` 为 `Model` 类提供了一个查询属性。在访问它时，将在所有记录上获得一个新的查询对象。然后，可以使用 `Filter()` 之类的方法来过滤记录，然后再用 `ALL()` 或 `First()` 触发 `SELECT`。如果想使用主键，也可以使用 `get()`。

假设数据库中有如下的数据：

| id   | username | email             |
| ---- | -------- | ----------------- |
| 1    | admin    | admin@example.com |
| 2    | peter    | peter@example.com |
| 3    | guest    | guest@example.com |

通过 `username` 检索用户：

```python
>>> peter = User.query.filter_by(username='peter').first()
>>> peter.id
2
>>> peter.email
u'peter@example.org'
```

同样的操作，但是传入一个不存在的 `username` ，结果就会返回 `None` ：

```python
>>> missing = User.query.filter_by(username='missing').first()
>>> missing is None
True
```

通过一个更复杂的表达式来查询一组用户：

```python
>>> User.query.filter(User.email.endswith('@example.com')).all()
[<User u'admin'>, <User u'guest'>]
```

查询结果以用户名排序：

```python
>>> User.query.order_by(User.username).all()
[<User u'admin'>, <User u'guest'>, <User u'peter'>]
```

限制查询结果条数：

```python
>>> User.query.limit(1).all()
[<User u'admin'>]
```

使用主键查询：

```python
>>> User.query.get(1)
<User u'admin'>
```

## 通过视图查询

你写的视图可能会因为入口缺失而返回一个 404 错误。这是一个常见的提示，`Flask-SQLAlchemy` 提供了能获取详细错误信息的助手方法。可以使用 `get_or_404()` 来替代 `get()` ，使用 `first_or_404()` 来替代 `first()` ，使用这两个方法就会引发 404 错误，而不是只返回 `None` 。

```python
@app.route('/user/<username>')
def show_user(username):
    user = User.query.filter_by(username=username).first_or_404()
    return render_template('show_user.html', user=user)
```

当然，如果你想给这次中断添加一个描述信息，你可以把它传到参数里面：

```python
>>> User.query.filter_by(username=username).first_or_404(description='There is no data with {}'.format(username))
```



