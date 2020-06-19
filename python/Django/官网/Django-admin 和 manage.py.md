[Toc]

`Django-admin` 是 `Django` 用于管理任务的命令行实用工具。这份文件概述了它所能做的一切。

此外，在每个 `Django` 项目中都会自动创建 `Manage.py`。它执行与 `Django-admin` 相同的操作，但也设置`Django_set_Module` 环境变量，以便它指向项目的 `setings.py` 文件。

如果你通过 `pip` 安装 `Django`，则 `Django-admin` 脚本应该在系统路径上。如果它不在系统路径上，可以在 `Python` 安装中的 `Site-Packages/Django/bin` 中找到它。考虑将其从路径上的某个位置(如 `/usr/local/bin` )进行符号链接。

对于没有符号链接功能的 `Windows` 用户，可以将 `Django-admin.exe` 复制到现有路径上的某个位置，或者编辑路径设置(在“设置-控制面板-系统-高级-环境.”下)若要指向其安装位置，请执行以下操作。

通常，在处理一个 `Django` 项目时，使用 `Manage.py` 比 `Django-admin` 更容易。如果需要在多个 `Django` 设置文件之间切换，请使用 `Django-admin With Django_SETIONS_MODUD` 或 `--SETION` 命令行选项。

整个文档中的命令行示例使用 `Django-admin` 保持一致，但任何示例也可以使用 `Manage.py` 或 `python-mDjango`。

# 用法

```shell
$ django-admin <command> [options]
$ manage.py <command> [options]
$ python -m django <command> [options]
```

`command` 应该是本文档中列出的 `command` 之一。`options` 是可选的，应该是给定 `command` 可用选项的零或多个。

# 获取运行时帮助

1. `django-admin help` ：运显示使用信息和每个应用程序提供的 `command` 列表

2. `django-admin help --commands` ：显示所有可用的 `command` 列表
3. `django-admin help <command>` ：显示所给命令的描述和可用 `option` 的列表

# 应用名称

许多命令都会列出“应用程序名称”。`app名称` 是包含模型的包的基本名称。例如，如果安装的应用程序包含字符串 `mysite.blog`，则应用程序名为 `Blog` 。

# 确定版本

`django-admin version` ：用于显示当前 `Django` 的版本

# 显示调试输出

使用 `--verbosity` 来指定 `django-admin` 输出到控制台中的调试信息和通知信息的数量

# 可用的 command

## check

