`starter` 是一系列便利的依赖描述符，这些描述符可以被包含在项目中。这样，你就获得了 `spring` 和相关技能一站式的商店了，你不需要通过样例代码来获取技能，也不需要对依赖描述符进行复制粘贴。例如，如果你想使用 `spring` 和 `jpa` 数据库，只要在项目中包含 `spring-boot-starter-data-jpa` 这一个依赖就可以了

`starter` 包含了项目创建和快速运行的许多依赖，并且支持依赖传递的管理

> 名字包含了什么？
>
> 官方的 `starter` 遵循着一种类似的命名格式：`spring-boot-starter-*` ，`*` 这里指的是某种特定的应用类型。当你需要查找某种 `starter` 时，这种命名方式非常有用。在许多集成了 `maven` 的 `ide` 中，都可以通过名称来搜索依赖。例如，在配置好的 `eclipse` 或者安装了 `spring` 工具插件，就可以在 `pom` 编辑器中按下 `ctrl + space` ，并且键入 `spring-boot-starter` 来查找完整的列表
>
> 正如在 `创建自己的 starter` 章节中所讲述的那样，第三方的 `starter` 的命名不应该由 `spring-boot` 开始，因为它是为 `spring boot` 官方构建所保留的。相反，第三方 `starter` 应该使用项目的名称作为开头。例如，有一个第三方 `starter` 的项目叫做 `thirdpartyproject` ，那么，它的命名就可以是：`thirdpartyproject-spring-boot-starter`

由 `spring boot` 提供的 `starter` 的 `group` 都是 `org.springframework.boot`

