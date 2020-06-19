[Toc]

让我们通过示例开始学习。

本系列教程将带领你创建一个基本的投票应用。

该应用分为两部分：

1. 用于民众浏览投票结果和进行投票的网站
2. 用于管理员添加、修改、删除投票的后台管理网站

本教程假设你已经安装了 `Django` 。使用下面的命令可以知道自己的机器上是否已经安装了 `Django` ：

`python3 -m django --version`

如果 `Django` 已经成功安装，控制台上将会打印出已经安装的 `Django` 版本。如果还没有安装，将会打印出错误的提示：`No module named django`

本教程是基于 `Django 3.0` 编写的，该版本的 `Django` 支持 `Python 3.6` 及更高版本。

# 创建项目

如果这是你首次使用 `Django` ，那你就得处理一些初步的设置。也就是说，你需要自动生成一些代码，用于建立一个 `Django` 项目 —— 该项目是 `Django` 一个实例的设置集合，包含数据库配置，`Django` 特有的选项 和一些应用特有的设置。

在命令行中，使用 `cd` 命令进入一个你想用来存放代码的目录，然后运行下面的命令：

`$ django-admin startproject mysite` 

上面的命令将会在当前的目录下创建一个名为 `mysite` 的目录。

> 注意：
>
> ​	需要避免在内置 Python 或 Django 组件之后命名项目。特别是，这意味着应该避免使用像 Django (这将与 Django 本身发生冲突)或 test (与内置的 Python 包相冲突)之类的名称。

>应该把代码放到哪里？
>
>​	如果你原来是开发简单旧PHP的(不使用现代框架)，那么你可能已经习惯于将代码放在 Web 服务器的文档根目录下(比如/var/www)。和 Django 在一起你不会那么做的。将这些 Python 代码放入 Web 服务器的文档根目录中并不是一个好主意，因为这可能会让人们在 Web 上查看您的代码，这样不安全！
>
>​	确保把你的代码放在文档根目录之外的目录下，例如：/home/mycode

下面是刚刚创建的项目结构

```
mysite
├── manage.py
└── mysite
    ├── __init__.py
    ├── asgi.py
    ├── settings.py
    ├── urls.py
    └── wsgi.py
```

1. 最外层的 `mysite` 根目录是应用的容器，它的名字对于 `Django` 来说并不重要，你可以把它重命名为任何你喜欢的合法名字

2. `manage.py` ：命令行实用程序，可以让你以不同的方式与 `Django` 项目进行交互

   > 这里需要看原文，有对 manage.py 文件的说明还没有翻译

3. 内层的 `mysite` 目录是应用真正的 `Python` 包名，你在导入任何东西时都需要用到它

4. `mysite/__init__.py` ：一个空的文件，用于告诉 `Python` 应该把这个目录当成一个 `Package` 包

5. `mysite/settings.py` ：`Django` 项目的配置文件

   > 这里需要看原文，有对 settings.py 文件的说明还没有翻译

6. `mysite/urls.py` ：`Django` 项目的 `url` 声明，就像是网站的目录

   > 这里需要看原文，有对 url dispatcher 文件的说明还没有翻译

7. `mysite/asgi.py` ：`Django` 项目运行在 `ASGI` 兼容的 `Web` 服务器上的入口

   > 这里需要看原文，有对 ASGI 部署的说明还没有翻译

8. `mysite/wsgi.py` ：`Django` 项目运行在 `WSGI` 兼容的 `Web` 服务器上的入口

   > 这里需要看原文，有对 WSGI 部署的说明还没有翻译

# 用于开发的简易服务器

现在来确认一下 `Django` 项目是否真的创建成功了。确认之前，请将命令行的目录切换到外层的 `mysite` 目录，然后运行下面的命令：

`python3 manage.py runserver`

应该会看到如下的输出：

```shell
Watching for file changes with StatReloader
Performing system checks...

System check identified no issues (0 silenced).

You have 17 unapplied migration(s). Your project may not work properly until you apply the migrations for app(s): admin, auth, contenttypes, sessions.
Run 'python manage.py migrate' to apply them.

April 08, 2020 - 01:08:41
Django version 3.0.5, using settings 'mysite.settings'
Starting development server at http://127.0.0.1:8000/
Quit the server with CONTROL-C.
```

> 忽略有关未应用最新数据库迁移的警告：You have ... apply them，稍后我们处理。

你已经启动了 `Django` 开发的服务器，这是一个使用纯 `Python` 编写的轻量级 `Web` 服务器。在 `Django` 中已经包含了服务器，因此你可以快速的开始开发工作，不用去管生产服务器的配置（这个和 `Apache` 是一样的），除非你已经准备要发布了。

**千万不要** 将这个服务器用于和生产环境相关的任何地方。这个服务器只是为了开发而设计的(我们在 `Web` 框架方面是专家，在 `Web` 服务器方面并不是)

现在，服务器正在运行，浏览器访问 https://127.0.0.1:8000/。你将会看到一个“祝贺”页面，随着一只火箭发射，服务器已经运行了。

## 更换端口

默认情况下，`runserver` 命令会将服务器设置为监听本机内部 `IP` 的 `8000` 端口。

如果想更换服务器的监听端口，请使用命令行参数：

`python3 manage.py runserver 8080`

如果你想要修改服务器监听的 `IP`，在端口之前输入新的 `IP` 地址：

`python3 manage.py runserver ip:8080`

> 会自动重新加载的服务器：
>
> ​	用于开发的服务器在需要的情况下会对每一次的访问请求重新载入一遍 Python 代码。所以你不需要为了让修改的代码生效而频繁的重新启动服务器。然而，一些动作，比如添加新文件，将不会触发自动重新加载，这时你得自己手动重启服务器。

# 创建投票应用

现在你的开发环境已经配置好了，可以开始干活了。

在 `Django` 中，每一个应用都是一个 `Python` 包，并且遵循着相同的约定。`Django` 自带一个工具，可以帮你生成应用的基础目录结构，这样你就能专心写代码，而不是创建目录了。

> 项目 VS 应用
>
> ​	项目和应用有什么区别？应用是一个专门做某件事的网络应用程序——比如博客系统，或者公共记录的数据库，或者小型的投票程序。项目则是一个网站使用的配置和应用的集合。项目可以包含很多个应用。应用可以被很多个项目使用。

应用可以存放在任何 `Python path` 中定义的路径。在这个教程中，我们将在你的 `manage.py` 同级目录下创建投票应用。这样它就可以作为顶级模块导入，而不是 `mysite` 的子模块。

请确定你现在处于 `manage.py` 所在的目录下，然后运行这行命令来创建一个应用：

`python3 manage.py startapp polls`

这将会创建一个 `polls` 目录，它的目录结构大致如下：

```shell
polls
├── __init__.py
├── admin.py
├── apps.py
├── migrations
│   └── __init__.py
├── models.py
├── tests.py
└── views.py
```

以上的目录包括了投票应用的全部内容。

## 创建第一个视图

让我们开始编写第一个视图吧。打开 `polls/views.py`，把下面这些 `Python` 代码输入进去：

这是 `Django` 中最简单的视图。如果想看见效果，我们需要将一个 `URL` 映射到它——这就是我们需要 `URLconf `的原因了。

为了创建 `URLconf`，请在 `polls` 目录里新建一个 `urls.py` 文件。你的应用目录现在看起来应该是这样：

```shell
polls
├── __init__.py
├── admin.py
├── apps.py
├── migrations
│   └── __init__.py
├── models.py
├── tests.py
├── urls.py
└── views.py
```

在 `polls/urls.py` 中，输入如下代码：

```python
from django.urls import path

from . import views

urlpatterns = [
    path('', views.index, name='index'),
]
```

下一步是要在根 `URLconf` 文件中指定我们创建的 `polls.urls` 模块。在 `mysite/urls.py` 文件的 `urlpatterns` 列表里插入一个 `include()`， 如下：

```python
from django.contrib import admin
from django.urls import include, path

urlpatterns = [
    path('polls/', include('polls.urls')),
    path('admin/', admin.site.urls),
]
```

函数 `include()` 允许引用其它 `URLconfs`。每当 `Django` 遇到 `include()` 时，它会截断与此项匹配的 `URL` 的部分，并将剩余的字符串发送到 `URLconf` 以供进一步处理。

我们设计 `include()` 的理念是使其可以即插即用。因为投票应用有它自己的 `URLconf( polls/urls.py` )，他们能够被放在 `/polls/` ， `/fun_polls/` ，`/content/polls/`，或者其他任何路径下，这个应用都能够正常工作。

> 何时使用 include()
>
> ​	当包括其它 URL 模式时你应该总是使用 `include()` ， `admin.site.urls` 是唯一例外

你现在把 `index` 视图添加进了 `URLconf`。通过以下命令验证是否正常工作：

`python manage.py runserver`

在浏览器访问 http://localhost:8000/polls/，你应该能够看见 `Hello, world. You're at the polls index.` ，这是你在 `index` 视图中定义的。

函数 `path()` 具有四个参数，两个必须参数：`route` 和 `view`，两个可选参数：`kwargs`和 `name`。现在，是时候来研究这些参数的含义了。

1. `route` ：是一个匹配 `URL` 的准则（类似正则表达式）。当 `Django` 响应一个请求时，它会从 `urlpatterns` 的第一项开始，按顺序依次匹配列表中的项，直到找到匹配的项
2. `view` ：当 `Django` 找到了一个匹配的准则，就会调用这个特定的视图函数，并传入一个 `HttpRequest`对象作为第一个参数，被“捕获”的参数以关键字参数的形式传入。稍后，我们会给出一个例子
3. `kwargs` ：任意个关键字参数可以作为一个字典传递给目标视图函数。本教程中不会使用这一特性
4. `name` ：为 `URL` 取名能使你在 `Django` 的任意地方唯一地引用它，尤其是在模板中。这个有用的特性允许你只改一个文件就能全局地修改某个 `URL` 模式。

