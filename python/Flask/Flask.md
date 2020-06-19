[toc]

# 概述

`Flask` 是一个基于 `Python` 并且依赖于 `Jinja2` 模板引擎和 `Werkzeug WSGI` 服务的一个微型框架

# 框架模式

`MTV` ：

1. `M` —— `Models` ，模型层，负责数据库建模
2. `T` —— `Templates` ，模板层，用于处理用户显示的内容，如：`html`
3. `V` —— `Views` ，视图层，处理与用户交互的部分内容，处理用户的请求并给出响应

# 安装

`pip3 install flask`

查看已安装的 `flask` 的版本：在 `python`  的交互模式下输入：

```python
import flask
flask.__version__
```

# 路由

客户端将请求发送给 `Web` 服务器，`Web` 服务器再将请求发送给 `flask` 的程序实例，程序实例需要知道每个 `url `请求要运行那些代码，所以需要建立一个 `url` 到 `python` 函数的映射，处理 `url` 和函数之间关系的程序就是路由

在 `Flask` 中，路由是通过 `@app.route` 装饰器来表示的：

```python
@app.route('/')
def login():
  return 'xxx'
```

## 带参数的路由

### 基本带参路由

```python
@app.route('/show/<name>')
def show(name): # 函数参数 name 必须与路由中 <> 里配置的内容一样
  return 'xxx'
```

## 带多个参数的路由

```python
@app.route('/show/<name>/<age>')
def show(name, age): 
  return 'xxx'
```

## 指定参数类型的路由

```python
@app.rount('show/<name>/<int:age>')
def show(name, age):
  return 'xxx'

# <int:age> 表示 age 参数是一个整数的数值而并非默认的字符串，int: 是类型转换器
# 注意：如果路由中定义的是 int，但是在网址中传递的是 float，会匹配不到这个路由的		
```

### Flask 中所支持的类型转换器

| 类型转换器 | 作用                   |
| ---------- | ---------------------- |
| 缺省       | 字符串类型，但不能有 / |
| int:       | 整形                   |
| float:     | 浮点型                 |
| path:      | 字符串类型，可以有 /   |

## 多 URL 的路由匹配

允许在一个视图处理函数中设置多个 `URL` 路由规则

```python
@app.route('/')
@app.route('/index')
def index():
  return 'xxx'
```

## 路由中设置 http 请求方法

`Flask` 路由规则也允许设置对应的请求方法，只有将匹配上请求方法的路径交给视图处理函数去执行

```python
@app.route('/post', methods=['POST'])
def post():
  return 'xxx'

# 只有 post 请求方式允许访问 localhost:5000/post 地址
```

## URL 解析

### 正向解析

程序自动解析，根据 `@app.route()` 中的访问路径来匹配处理函数

### 反向解析

通过视图处理函数的名称自动生成视图处理函数的访问路径，`Flask` 中提供了 `url_for()` 函数，用于反向解析 `url`

```python
url_for()
	第一个参数：指向函数名（通过 @app.route() 修饰的函数）
  后续的参数们：对应要构建的 url 上的变量
  
@app.route('/')
def index():
  return 'Index'

@app.route('/show/<name>')
def show(name):
  return 'name: %s' % name

url_for('index')，结果为：/
url_for('show', name='张三丰')，结果：/show/张三丰
```

### 静态文件反向使用

`url_for('static', finlename='style.css')`

# 模板

模板是一个包含相应文件的文本（通常是 `.html` 文件），该文件中允许包含“占位变量”来表示动态的内容，其具体值在请求中才知道，“占位变量”最终会被真实的变量所替换。

模板最终也会被解析成响应的字符串，这一过程被称为“渲染”

`Flask` 实际上是使用 `Jinja2` 强大的引擎模板

## 设置

默认情况下，`Flask` 会在程序文件夹中的 `templates` 子文件夹中寻找模板

> 需要手动创建 templates 文件夹
>
> 'lorem' + tab键，自动生成一段英文

## 渲染

在视图函数中，通过 `return render_template('xxx.html', arg1=val1, arg2=val2, ..., argn=valn)` 将模板渲染成字符串再响应给客户端

参数：

1. 要渲染给客户端的 `html` 模板文件，`Flask` 自己会到 `templates` 文件夹下去找，找不到会抛出异常
2. 要传递给模板动态显式的变量占位符，如果没有动态的变量占位符，则可以省略

返回值：

1. 字符串

## 语法

### 变量

变量是一种特殊的占位符，用于告诉模板引擎该位置的值是从渲染模板时的数据中来获取的

#### 多参数传值

```python
@app.route('/')
def index():
  return render_template('xxx.html', name='sf.zh', age=18)

# name 和 age 就是要传递到 xxx.html 中的变量

# 模板接受如下：
姓名：{{name}}
年龄：{{age}}
```

#### 字典传值

```python
@app.route('/')
def index():
  dic = {
    'name': 'sf.zh',
    'age': 18
  }
  return render_template('xxx.html', params=dic)

# 使用 params 变量名将字典传入模板

# 模板接受如下：
姓名：{{params.name}}
年龄：{{param.age}}
```

#### 双星号字典传值

```python
@app.route('/')
def index():
  dic = {
    'name': 'sf.zh',
    'age': 18
  }
  return render_template('xxx.html', **dic)

# 用 ** 将字典拆解后传入模板

# 模板接受如下：
姓名：{{name}}
年龄：{{age}}
```

#### 字典传值的另外一种写法

```python
@app.route('/')
def show():
  name = 'zhangsan'
  age = 20
  return render_template('index.html', params=locals() 或者 **locals())
```

### 过滤器

过滤器允许在变量输出显示之前改变变量的值

```python
{{变量|过滤器}}
```

#### Jinja2 变量过滤器

| 过滤器名   | 说明                           |
| ---------- | ------------------------------ |
| capitalize | 首字符变大写，其他字符变小写   |
| lower      | 把值转换成小写                 |
| upper      | 把值转换成大写                 |
| title      | 把值中的每个单词的首字符变大写 |
| trim       | 把值两端的空格去掉             |

### 控制结构

#### if 结构

```html
{% if name %}
	<h1>欢迎：{{name}}</h1>
{% else %}
	<h1>没有欢迎的人喽！</h1>
{% endif %}
```

#### for 结构

```python
{% for 变量 in 元组|列表|字典 %}

{% endfor %}
```

#### 宏

使用 `{% macro %}` 标签声明宏

```html
<!-- 声明 -->
{% macro show(str) %}
	<h1>{{str}}</h1>
{% endmacro %}

<!-- 调用 -->
{{show(name)}}
```

> 为了方便宏的重复使用，允许将宏放在单独的模板文件中声明定义：
>
> 1. 创建 macro.html
> 2. 在使用的网页中，在使用之前，使用 {% import 'macro.html' as macro %}，导入 macro.html
> 3. 使用：{{macro.show(参数)}}

### 模板的包含

在多处重复使用的模板可以放在单独的文件中，可以被其他的模板所包含（引用）

`{% include 'xxx.html' %}`

### 模板的继承

模板的继承类似于类的继承，如果在一个模板中出现的大量内容是另外一个模板的话，那么就可以使用继承的方式来简化开发。

```python
# 父模板，需要定义出那些内容在字模板中是可以被重写的
{% block 块名 %}
	# 1. 可以在子模板中被重写的内容
  # 2. 在符模板中正常显示，没有任何影响
{% endblock %}

# 子模板
{% extends '父模板名称' %} # 完成继承
{% block 块名 %}  
	{{super()}} # 调用父模板的内容（可以调用，也可以不调用）
	# 覆盖、重写父模板中的同名内容
{% endblock %}

# 允许通过 {{super()}} 来调用父模板中的内容
{{super()}}
```

## 静态文件

在 `Flask` 中不能与服务器动态交互的文件都是静态文件

### 保存位置

所有静态文件都保存在项目文件中的 `static` 文件夹中

### 访问方法

在访问静态文件的时候需要通过 `/static/` 资源路径进行访问 

`<img src="/static/xxx">`

### 反向解析

`url_for('static', filename='<file_path>')`

## 自定义错误文件

`404` 的错误处理（其他的相应码处理类似）：

```python
@app.errorhandler(404)
def page_not_fount(e):
  return render.template('xxx.html'), 404
```

# 配置

```python
app = Flask(__name__, template_folder='xxx', static_url_path='/xx/', static_folder='/xx', debug=True)

# template_folder ：设置模板的保存路径
# static_url_path ：设置静态文件的访问路径（映射到 Web 中的访问路径）
# static_folder ：设置静态文件存储的文件夹（映射到项目中的目录名称）
# debug ：是否开启调试模式
```

# 请求和相应

## 请求对象 —— request

`request` 里面封装了所有与请求相关的信息，如：请求消息头，请求路径，请求数据……

`Flask` 中，请求信息被封装到了 `request` 对象中 ：`from Flask import request`

### 常用成员

1. `scheme` ：获取请求方案（协议）
2. `method` ：获取本次请求的请求方式
3. `request.args` ：获取使用 `get` 请求方式提交的数据
4. `request.form` ：获取使用 `post` 请求方式提交的数据
5. `request.values` ：获取 `get` 和 `post` 请求方式提交的数据（通用的）
6. `request.cookies` ：获取 `cookies` 中的信息
7. `request.headers` ：获取请求消息头的信息
8. `request.path` ：获取请求的 `url` 地址
9. `request.files` ：获取用户上传的文件
10. `request.full_path` ：获取请求的完整路径
11. `request.url` ：获取访问地址

### 获取请求的数据

#### get 请求

`get` 请求的数据是放在 `QueryString` 中的，`request.args` 封装的就是 `get` 请求的数据，类型为字典

#### post 请求

`post` 请求的数据是放在 `form` 中的，`request.form` 封装的就是 `post` 请求的数据，类型为字典

## 响应对象 —— response

响应对象就是要响应给客户端的内容，可以是普通字符串，可以是模板或者是重定向

1. 构建响应对象，再响应给客户端。响应对象可以包含相应的字符串，同时也可以实现其他的相应操作。在 `Flask` 中，使用 `make_response()` 构建响应对象。

   > 注意：不是响应字符串，而是响应对象

   ```python
   from flask import make_response
   ...
   resp = make_response('相应内容')
   # 实现其他的相应操作，如：添加 cookies 等
   return resp
   ```

2. 重定向：有服务端通知客户端重新向新的地址发送请求

   ```python
   from flask import redirect
   ...
   resp = redirect('重定向地址')
   return resp
   ```

   > 重定向的本质：
   >
   > 1. 浏览器客户端访问 A 链接，A 连接处理完成后使用重定向通知浏览器
   > 2. 浏览器收到服务端重定向的请求后，会再次访问重定向请求指定的地址
   >
   > 也就是说，重定向发起了两次请求

## 文件上传

1. 服务器端通过 `request.files` 获取上传的文件：`f = request.files['文件框name的属性值']`
2. 通过：`f.save('保存路径')` 将文件保存到指定的目录处，通过：`f.filename` 获取文件名称

> 注意：
>
> 1. 提交方式必须为 post
> 2. enctype 属性必须设置为 multipart/form-data
> 3. 保存文件的目录必须存在，程序不会自动创建，文件夹不存在会报错
> 4. 大数据量上传的时候（如：超大文件），就不能使用网页上传了（主要是由于 http 协议不支持），需要使用单独的上传工具（C/S 版的）

# 模型

模型是根据数据库中表的结构创建出来的 `class` 。每一张表在编程语言中就是一个 `class` ，表中的每一个列，到编程语言中就是 `class` 的一个属性

## ORM

`ORM : Object Relational Mapping` 关系对象映射

### 三大特征

1. 数据表（`table`）到编程类（`class`）的映射：数据库中的每一张表对应到编程语言中，都有一个类。在 `ORM` 中，允许将数据表自动生成一个类，也允许将类自动生成一张表
2. 数据类型的映射：将数据库表中的字段以及数据类型对应到编程语言中类的属性，在 `ORM` 中，允许将数据库表中的字段和数据类型自动映射到编程语言中，也允许将类中的属性和类型也映射到数据库表中
3. 关系映射：将数据库中表之间的关系也对应到编程语言中类之间的关系，数据库表的关系：一对一（主外键关联，外键需要添加唯一性约束），一对多（主外键关联），多对多（）

### 优点

1. 提高了开发的效率
2. 能够省略庞大的数据访问层，即便不用 `sql` 编码也能完成对数据的 `CRUD` 操作

### 定义模型

#### 安装 SQLAlchemy

```shell
pip3 install SQLAlchemy
pip3 install flask-sqlalchemy
```

#### 创建数据库

#### 配置数据库

```python
from flask import Flask
from flask_sqlalchemy import SQLAlchemy

app = Flask(__name__)

# app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql://username=root:P@ssw0rd.@localhost:3306/fllask'
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql://username=root:P@ssw0rd.@localhost:3306/fllask'

# 创建 SQLAlchemy 的实例
db = SQLAlchemy(app)

# db 是 SQLAlchemy 的实例，表示程序正在使用的数据库，同时也获得了 SQLAlchemy 中的所有功能

if __name__ == '__main__':
  app.run(debug=True)
```

#### 模型

模型是数据库中的表在编程语言中的体现，其本质就是一个 `Python` 的对象（可称为：模型类或实体类），类中的属性要与数据库表中的列相对应

```python
# 创建模型类（注意：下文中全部大写的东西，在实际的开发中是需要被替换为实际的东西）
class MODELNAME(db.Model):
  __tablename__ = 'TABLENAME'
  COLUMN_NAME = db.Column(db.TYPE, OPTIONS)
  
  
# MODELNAME ：定义模型类名称，根据表名设定
# TABLENAME ：映射到数据库中表的名字
# COLUMN_NAME ：属性名，映射到表中列的名字
# db.TYPE ：映射到列的数据类型
# OPTIONS ：列选项
```

##### 列类型

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

`OPTIONS` 选项

| 选项名      | 说明                             |
| ----------- | -------------------------------- |
| primary_key | 设置为 True 则表示该列为主键     |
| unique      | 设置为 True 则表示该列的值唯一   |
| index       | 设置为 True 则表示该列要创建索引 |
| nullable    | 设置为 True 则表示该列允许为空   |
| default     | 为该列设置默认值                 |

#### 数据库操作

```python
# 不用手动写 session.commit() 方法
app.config['SQLALCHEMY_COMMIT_ON_TEARDOWN'] = Ture

# 插入
db.session.add(Models)
db.session.commit()

# 

# 与数据相关的所有操作都需要交给 session 去做
```

#### 查询

1. `db.session.query()` ：该函数会返回一个 `Query` 对象，类型为 `BaseQuery` ，包含了指定实体类对应的表中的所有数据；该函数也可以接受多个参数，参数表示的是要查询哪个实体。

2. 查询执行函数：目的在查询的基础上得到最终想要的结果，`db.session.query(...).查询执行函数`

   | 查询执行函数    | 说明                                                   |
   | --------------- | ------------------------------------------------------ |
   | all()           | 以列表的方式返回查询的所有结果                         |
   | first()         | 返回查询中的第一个结果，如果没有结果，则返回 None      |
   | first_all_404() | 返回查询中的第一个结果，如果没有结果，则终止并返回 404 |
   | count()         | 返回查询结果的数量                                     |

3. 查询过滤器函数：在查询的基础上，筛选部分列出来。`db.session.query(...).查询过滤器函数.查询执行函数`

   | 查询过滤器函数 | 说明                                              | 示例                                                         |
   | -------------- | ------------------------------------------------- | ------------------------------------------------------------ |
   | filter()       | 按指定条件进行过滤（多表，单表，定值，不定值...） | db.session.query(Users).filter(Users.age>30).all()<br />db.session.query(Users).filter(Users.age>30, Users.id>5).all()<br />db.session.query(Users).filter(or_(条件1，条件2，...)).all()<br />db.session.query(Users).filter(Users.id==5).first()<br />db.session.query(Users).filter(Users.email.like('%w%')).all()<br />db.session.query(Users).filter(Users.id.in\_([1, 2, 3])).all() |
   | filter_by()    | 按等值条件进行过滤                                | db.session.query(Users).filter_by(Users.id=5).first()        |
   | limit()        | 按限制行数获取                                    | db.session.query(Users).limit(5).all()<br />db.session.query(Users).limit(3).offset(1).all() |
   | order_by()     | 根据指定条件进行排序                              | db.session.query(Users).order_by('id desc').all()            |
   | group_up()     | 根据指定条件进行分组                              | db.session.query(Users.age).group_by('age').all()            |

#### 删除

1. 查询要删除的实体：

   `user = db.session.query(Users).filter_by(id=5).first()`

2. 根据所提供的删除方法将信息删除

   de.session.delete(user)

#### 修改

1. 查：

   `user = Users.query.filter_by(id=1).firist()`

2. 改：

   ```python
   user.username = 'xxx'
   user.age = 40
   ```

3. 保存：

   `de.session.add(user)` 注意：如果修改的id不存在，就变成保存了

