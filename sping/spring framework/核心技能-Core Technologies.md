[Toc]

> Version 5.2.6 RELEASE

该文档涵盖了 `Spring` 框架中必不可少的所有技术。

其中最重要的是 `Spring` 框架的控制反转(`IoC`)容器。在彻底处理 `Spring` 框架的 `IoC` 容器之后，将对 `Spring` 的面向切面编程(`AOP`)技术进行全面的介绍。`Spring` 框架有自己的 `AOP`框架，在概念上易于理解，并且成功地解决了 `Java` 企业编程中 `AOP` 需求的 80%的痛点。

本文还介绍了 `Spring` 与 `AspectJ` 的集成(目前在特性方面是最丰富的--当然还有 `Java` 企业空间中最成熟的 `AOP` 实现)。

# 1. IoC 容器

本章介绍 `Spring` 的反转控制( `IoC` )容器。

## 1.1 介绍 IoC 容器和 Bean
本章介绍了控制反转( `IoC` )原理的 `Spring` 框架实现。 `IoC` 也称为依赖注入( `DI` )。它是一个过程，对象仅通过构造函数、工厂方法的参数或在从工厂方法构造或返回对象实例后在对象实例上设置的属性来定义它们的依赖关系(即与它们一起工作的其他对象)。然后，容器在创建 `bean` 时注入这些依赖项。从根本上说，这个过程是 `bean` 本身的逆(因此是名称、控制反转)，它通过使用类的直接构造或服务定位器模式等机制来控制其依赖项的实例化或位置。

`org.springfraamework.beans` 和 `org.springframework.context`  包是 `SpringFramework` 的 `IoC` 容器的基础。 `BeanFactory` 接口提供了能够管理任何类型对象的高级配置机制。 `ApplicationContext` 是 `BeanFactory` 的一个子接口，子接口添加了如下的内容：

* 更容易与 `Spring` 的 `AOP` 特性集成
* 消息资源处理（用于国际化）
* 事件发布
* 特定于应用层的上下文，例如用于 `web` 应用程序的 `WebApplicationContext`

简而言之， `BeanFactory` 提供了配置框架和基本功能， `ApplicationContext` 添加了更多特定于企业的功能。 `ApplicationContext` 是 `BeanFactory` 的一个完整的超集，在本章中专门用于描述 `Spring` 的 `IoC` 容器。有关使用 `BeanFactory` 而不是 `ApplicationContext` 的更多信息，请参见 `BeanFactory` 。

在 `Spring` 中，构成应用程序主干并由 `SpringIoC` 容器管理的对象称为 `bean` 。 `bean` 是由 `SpringIoC` 容器实例化、组装和以其他方式管理的对象。否则， `bean` 只是应用程序中许多对象之一。 `bean` 及其之间的依赖关系反映在容器使用的配置元数据中。

## 1.2 容器概述

`org.springframework.context.ApplicationContext` 接口表示 `SpringIoC` 容器，负责实例化、配置和组装 `bean` 。容器通过读取配置元数据获取关于要实例化、配置和组装哪些对象的说明。配置元数据以 `XML` 、 `Java` 注释或 `Java` 代码表示。它允许你表示组成应用程序的对象以及这些对象之间的丰富相互依赖关系。

`Spring` 提供了几个 `ApplicationContext` 接口的实现。在独立应用程序中，常见的做法是创建 `ClassPathXmlApplicationContext` 或 `FileSystemXmlApplicationContext` 的实例。虽然 `XML` 一直是定义配置元数据的传统格式，但你可以指示容器使用 `Java` 注释或代码作为元数据格式，方法是提供少量 `XML` 配置以声明性地启用对这些附加元数据格式的支持。

在大多数应用程序场景中，不需要使用显式的用户代码来实例化 `SpringIoC` 容器的一个或多个实例。例如，在 `Web` 应用程序场景中，应用程序 `web.xml` 文件中简单的大约 8 行模板 `Web` 描述符 `XML` 通常就足够了（请参阅方便的 `ApplicationContext` 实例化用于 `Web` 应用程序）。如果你使用 `Spring Tools for Eclipse` （一个 `Eclipse` 驱动的开发环境），那么只需点击几下鼠标或按一下键，就可以很容易地创建这个样板配置。

下图显示了 `Spring` 如何工作的。应用程序类与配置元数据组合在一起，这样在创建和初始化 `ApplicationContext` 之后，你就拥有了一个完全配置和可执行的系统或应用程序：

![](index_files/c8d97c64-0c60-4518-8771-fbc2b2b089b2.jpg)

### 1.2.1 配置元数据

如上图表所示， `SpringIoC` 容器使用一种配置元数据形式。此配置元数据表示作为应用程序开发人员如何告诉 `Spring` 容器实例化、配置和组装应用程序中的对象。

传统上，配置元数据是以简单直观的 `XML` 格式提供的，这是本章的大部分内容用来传达 `SpringIoC` 容器的关键概念和特性的。

> 基于 `XML` 的元数据并不是唯一允许的配置元数据形式。 `SpringIoC` 容器本身与实际写入配置元数据的格式完全解耦。如今，许多开发人员为他们的 `Spring` 应用程序选择了基于 `Java` 的配置。

有关在 `Spring` 容器中使用其他形式的元数据的信息，请参阅：

* 基于注释的配置： `Spring 2.5` 引入了对基于注解的配置元数据的支持。
* 基于 `Java` 的配置：从 `Spring 3.0` 开始， `SpringJavaConfig` 项目提供的许多特性成为核心 `Spring` 框架的一部分。因此，可以使用 `Java` 而不是 `XML` 文件在应用程序类外部定义 `bean` 。要使用这些新特性，请参阅 `@Configuration` 、 `@Bean` 、 `@Import` 和 `@DependsOn` 注释。

`Spring` 配置包括容器必须管理的至少一个，通常是多个 `bean` 定义。基于 `XML` 的配置元数据将这些 `bean` 配置为 `<bean/>` 元素在顶层 `<bean/>` 元素中。 `Java` 配置通常在 `@Configuration` 类中使用 `@Bean` 注释的方法。

这些 `bean` 定义对应于构成应用程序的实际对象。通常，你定义服务层对象、数据访问对象（ `DAO` ）、表示层对象（如 `Struts`   `Action` 实例）、数据访问对象（如 `Hibernate`   `SessionFacels` ）、 `JMS` 队列等。通常，在容器中不配置细粒度域对象，因为创建和加载域对象通常是 `DAOS` 和业务逻辑的责任。但是，你可以使用 `Spring` 与 `AspectJ` 的集成来配置在 `IoC` 容器控制之外创建的对象。参见使用 `AspectJ` 与 `Spring` 一起注入域对象。

下面的示例显示了基于 `XML` 的配置元数据的基本结构：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="..." class="...">
        <!-- collaborators and configuration for this bean go here -->
    </bean>

    <bean id="..." class="...">
        <!-- collaborators and configuration for this bean go here -->
    </bean>

    <!-- more bean definitions go here -->

</beans>
```

* `id` 属性是标识单个 `bean` 定义的字符串
* `class` 属性定义 `bean` 的类型，并使用完全限定的类名

`id` 属性的值引用协作对象。本例中未显示用于引用协作对象的 `XML` 。有关更多信息，请参见“依赖关系”。

### 1.2.2 实例化容器

提供给 `ApplicationContext` 构造函数的位置路径或路径是允许容器从各种外部资源（如本地文件系统、 `Java`   `CLASSPATH` 等）加载配置元数据的资源字符串。

```java
ApplicationContext context = new ClassPathXmlApplicationContext("services.xml", "daos.xml");
```

> 在了解了 `Spring` 的 `IoC` 容器之后，你可能想了解更多关于 `Spring` 的资源抽象（如参考资料中所描述的），它提供了从 `URI` 语法定义的位置读取 `InputStream` 的方便机制。特别是，资源路径用于构造应用程序上下文，如应用程序上下文和资源路径中所描述的那样。

下面的示例显示服务层对象（ `services.xml` ）配置文件：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">

    <!-- services -->

    <bean id="petStore" class="org.springframework.samples.jpetstore.services.PetStoreServiceImpl">
        <property name="accountDao" ref="accountDao"/>
        <property name="itemDao" ref="itemDao"/>
        <!-- additional collaborators and configuration for this bean go here -->
    </bean>

    <!-- more bean definitions for services go here -->

</beans>
```

下面的示例显示数据访问对象 `daos.xml` 文件：

```xmml
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.springframework.org/schema/beans
        https://www.springframework.org/schema/beans/spring-beans.xsd">

    <bean id="accountDao"
        class="org.springframework.samples.jpetstore.dao.jpa.JpaAccountDao">
        <!-- additional collaborators and configuration for this bean go here -->
    </bean>

    <bean id="itemDao" class="org.springframework.samples.jpetstore.dao.jpa.JpaItemDao">
        <!-- additional collaborators and configuration for this bean go here -->
    </bean>

    <!-- more bean definitions for data access objects go here -->

</beans>
```

在前面的示例中，服务层由 `PetStoreServiceImpl` 类和 `JpaAccountDAO` 和 `JpaItemDAO` 类型的两个数据访问对象（基于 `JPA` 对象-关系映射标准）组成。 `PropertyName` 元素引用 `JavaBean` 属性的名称， `ref` 元素引用另一个 `bean` 定义的名称。 `id` 和 `ref` 元素之间的链接表示协作对象之间的依赖关系。有关配置对象依赖项的详细信息，请参阅依赖项。

#### 组合基于 `xml` 的配置元数据

让 `bean` 定义跨越多个 `XML` 文件可能很有用。通常，每个单独的 `XML` 配置文件都表示体系结构中的逻辑层或模块。

你可以使用应用程序上下文构造函数从所有这些 `XML` 片段加载 `bean` 定义。此构造函数采用多个资源位置，如上一节所示。或者，使用一个或多个 `<import/>`；元素的出现来从另一个或多个文件加载 `bean` 定义。下面的示例演示如何做到这一点：

```xml
<beans>
    <import resource="services.xml"/>
    <import resource="resources/messageSource.xml"/>
    <import resource="/resources/themeSource.xml"/>

    <bean id="bean1" class="..."/>
    <bean id="bean2" class="..."/>
</beans>
```

在前面的示例中，外部 `bean` 定义是从三个文件加载的： `services.xml` 、 `messageSource.xml` 和 `emeSource.xml` 。所有位置路径都相对于执行导入的定义文件，因此 `services.xml` 必须位于与导入文件相同的目录或类路径位置，而 `messageSource.xml` 和 `emeSource.xml` 必须位于导入文件位置以下的资源位置。如你所见，前面的斜杠将被忽略。但是，考虑到这些路径是相对的，最好不要使用斜杠。根据 `SpringSchema` ，正在导入的文件的内容（包括顶层 `<bean/>` 元素）必须是有效的 `XMLbean` 定义。

> 可以（但不建议）使用相对 `../` 路径引用父目录中的文件。这样做会创建对当前应用程序之外的文件的依赖关系。特别是，不建议对 `classpath` ： `URL` （例如， `classpath` ： `.services.xml` ）引用，其中运行时解析过程选择“最近”的类路径根，然后查看其父目录。 `Classpath` 配置更改可能导致选择不同的、不正确的目录。
你可以始终使用完全限定的资源位置，而不是相对路径：例如，文件： `C` ：/ `config` / `services.xml` 或 `classpath` ：/ `config` / `services.xml` 。但是，请注意，你正在将应用程序的配置耦合到特定的绝对位置。通常最好对这些绝对位置保持一个间接性-例如，通过“${…​}”占位符在运行时针对 `JVM` 系统属性进行解析。

命名空间本身提供导入指令功能。 `Spring` 提供的 `XML` 命名空间（例如，上下文和 `util` 名称空间）提供了除普通 `bean` 定义之外的其他配置功能。

#### Groovy Bean 定义 DSL

作为外部化配置元数据的另一个示例，也可以在 `Spring` 的 `GroovyBean` 定义 `DSL` 中表示 `bean` 定义，正如 `Grails` 框架所知道的那样。通常，这种配置位于“ `.groovy` ”文件中，其结构如下面的示例所示：

```groovy
beans {
    dataSource(BasicDataSource) {
        driverClassName = "org.hsqldb.jdbcDriver"
        url = "jdbc:hsqldb:mem:grailsDB"
        username = "sa"
        password = ""
        settings = [mynew:"setting"]
    }
    sessionFactory(SessionFactory) {
        dataSource = dataSource
    }
    myService(MyService) {
        nestedBean = { AnotherBean bean ->
            dataSource = dataSource
        }
    }
}
```

这种配置风格在很大程度上等同于 `XMLbean` 定义，甚至支持 `Spring` 的 `XML` 配置命名空间。它还允许通过 `importBeans` 指令导入 `XMLbean` 定义文件。

### 1.2.3 使用容器

`ApplicationContext` 是高级工厂的接口，它能够维护不同 `bean` 及其依赖项的注册表。通过使用方法 `T getBean(String name, Class<T> requdType` ），你可以检索 `bean` 的实例。

`ApplicationContext` 允许你读取 `bean` 定义并访问它们，如下例所示：

```java
// create and configure beans
ApplicationContext context = new ClassPathXmlApplicationContext("services.xml", "daos.xml");

// retrieve configured instance
PetStoreService service = context.getBean("petStore", PetStoreService.class);

// use configured instance
List<String> userList = service.getUsernameList();
```

使用 `Groovy` 配置，引导看起来非常相似。它有一个不同的上下文实现类，它是 `Groovy` 感知的（但也理解 `XMLbean` 定义）。下面的示例显示了 `Groovy` 配置：

```groovy
ApplicationContext context = new GenericGroovyApplicationContext("services.groovy", "daos.groovy");
```

最灵活的变体是 `GenericApplicationContext` 和读取器委托--例如， `XML` 文件的 `XmlBeanDefinitionReader` ，如下面的示例所示：

```java
GenericApplicationContext context = new GenericApplicationContext();
new XmlBeanDefinitionReader(context).loadBeanDefinitions("services.xml", "daos.xml");
context.refresh();
```

还可以为 `Groovy` 文件使用 `GroovyBeanDefinitionReader` ，如下例所示：

```groovy
GenericApplicationContext context = new GenericApplicationContext();
new GroovyBeanDefinitionReader(context).loadBeanDefinitions("services.groovy", "daos.groovy");
context.refresh();
```

你可以在同一个 `ApplicationContext` 上混合和匹配这些读取器委托，从不同的配置源读取 `bean` 定义。

然后可以使用 `getBean` 检索 `bean` 的实例。 `ApplicationContext` 接口还有一些其他方法来检索 `bean` ，但理想情况下，应用程序代码不应该使用它们。实际上，应用程序代码应该根本不调用 `getBean()` 方法，因此根本不依赖 `SpringAPI` 。例如， `Spring` 与 `Web` 框架的集成为控制器和 `JSF` 托管 `bean` 等各种 `Web` 框架组件提供了依赖注入，允许你通过元数据（例如自动装配注释）声明对特定 `bean` 的依赖。

## 1.3 Bean 概述

 `SpringIoC` 容器管理一个或多个 `bean` 。这些 `bean` 是使用你提供给容器的配置元数据创建的（例如，以 `XML` 的 `<bean/>` 定义的形式）。

在容器本身中，这些 `bean` 定义表示为 `BeanDefinition` 对象，这些对象包含（除其他信息外）以下元数据：

* 包的完全限定类名：通常，定义的 `bean` 的实际实现类
* `bean` 行为配置元素，它们说明 `bean` 在容器中的行为方式（范围、生命周期回调等等）
* 对 `bean` 执行其工作所需的其他 `bean` 的引用。这些引用也称为协作者或依赖项
* 在新创建的对象中设置的其他配置设置--例如，池的大小限制或在管理连接池的 `bean` 中使用的连接数

此元数据转换为组成每个 `bean` 定义的一组属性。下表描述了这些属性：

| 属性 | 在哪里解释
| - | -
| class | 实例化 Bean
| name | <a href="#beanNaming">Bean 的命名</a>
| scope | Bean 的作用域
| constructor arguments | 依赖注入
| properties | 依赖注入
| autowiring mode | Autowiring Collaborators
| lazy initialization mode | 延迟初始化 Bean
| initialization method | 初始化回调
| destruction method | 销毁方法回调

除了包含有关如何创建特定 `bean` 的信息的 `bean` 定义之外， `ApplicationContext` 实现还允许注册容器外创建的现有对象（由用户创建）。这是通过 `getBeanFactory` （）方法访问 `ApplicationContext` 的 `BeanFactory` 来完成的，该方法返回 `BeanFactory` 的 `DefaultListableBeanFactory` 实现。 `DefaultListableBeanFactory` 通过 `RegistrerSingleton` （ `.` ）支持此注册。和寄存器- `BeanDefinition` （ `..` ）方法。但是，典型的应用程序只使用通过常规 `bean` 定义元数据定义的 `bean` 。

> `bean` 元数据和手动提供的单例实例需要尽早注册，以便容器在自动装配和其他内省步骤中对它们进行适当的推理。虽然在某种程度上支持重写现有元数据和现有的单例实例，但在运行时注册新 `bean` （同时使用对工厂的实时访问）不受官方支持，可能导致并发访问异常、 `bean` 容器中的不一致状态，或者两者兼而有之。

### <a id="beanNaming">1.3.1 Bean 的命名</a>

每个 `bean` 都有一个或多个标识符。这些标识符在承载 `bean` 的容器中必须是唯一的。 `bean` 通常只有一个标识符。然而，如果它需要一个以上，额外的可以被视为别名。

在基于 `XML` 的配置元数据中，可以使用 `id` 属性、 `name` 属性或两者来指定 `bean` 标识符。 `id` 属性允许你精确地指定一个 `id` 。通常，这些名称都是字母数字（“ `myBean` ”、“ `omeService` ”等），但它们也可以包含特殊字符。如果要为 `bean` 引入其他别名，还可以在 `name` 属性中指定它们，以逗号（，）、分号（；）或空白分隔。作为历史记录，在 `Spring 3.1` 之前的版本中， `id` 属性被定义为 `xsd` ： `id` 类型，这限制了可能的字符。从 3.1 开始，它被定义为 `xsd` ： `string` 类型。注意， `bean id` 唯一性仍然由容器强制执行，尽管不再由 `XML` 解析器强制执行。

你不需要为 `bean` 提供名称或 `ID` 。如果没有显式提供名称或 `id` ，容器将为该 `bean` 生成唯一的名称。但是，如果你希望通过使用 `ref` 元素或 `ServiceLocator` 样式查找来按名称引用该 `bean` ，则必须提供一个名称。不提供名称的动机与使用 `inner bean` 和 `autowiring collaborators` 有关。

#### Bean 的命名约定

约定是在命名 `bean` 时使用标准 `Java` 约定，例如字段名。也就是说， `bean` 名以小写字母开头，后面是驼峰式命名。此类名称的示例包括 `accountManager` 、 `accountService` 、 `userDao` 、 `loginController` 等。命名 `bean` 可以使你的配置更易于阅读和理解。

另外，如果你使用 `SpringAOP` ，那么在向一组按名称相关的 `bean` 应用通知时，它会有很大帮助。

> 使用类路径中的组件扫描， `Spring` 按照前面描述的规则为未命名的组件生成 `bean` 名称：从本质上讲，获取简单的类名并将其初始字符转换为小写。然而，在（不寻常的）特例中，当有多个字符，并且第一和第二字符都是大写时，原始的大小写被保留。这些规则与 `java.beans.Introspector.decapitalization` （ `Spring` 在这里使用的）定义的规则相同。

#### 在 Bean 定义之外对 Bean 进行混叠

在 `bean` 定义本身中，你可以为 `bean` 提供多个名称，方法是使用 `id` 属性指定的最多一个名称和 `name` 属性中任何其他名称的组合。这些名称可以是相同 `bean` 的等效别名，并且在某些情况下非常有用，例如让应用程序中的每个组件通过使用特定于该组件本身的 `bean` 名称来引用公共依赖项。

然而，指定 `bean` 实际定义的所有别名并不总是足够的。有时需要为在其他地方定义的 `bean` 引入别名。在大型系统中，这种情况通常是这样的：配置在每个子系统之间被分割，每个子系统都有自己的一组对象定义。在基于 `XML` 的配置元数据中，可以使用 `<alias/>` 元素来完成这一任务。下面的示例演示如何做到这一点：

```xml
<alias name="fromName" alias="toName"/>
```

在这种情况下，在使用这个别名定义之后，名为 `fromName` 的 `bean` （在同一个容器中）也可以称为 `toName` 。

例如，子系统 `A` 的配置元数据可能引用了名为 `subsystemA-dataSource` 的 `DataSource` 。子系统 `B` 的配置元数据可能引用了名为 `subsystemB-dataSource` 的 `DataSource` 。在组合使用这两个子系统的主应用程序时，主应用程序以 `myApp-dataSource` 的名称引用 `DataSource` 。要让所有三个名称都引用同一个对象，可以将以下别名定义添加到配置元数据中：

```xml
<alias name="myApp-dataSource" alias="subsystemA-dataSource"/>
<alias name="myApp-dataSource" alias="subsystemB-dataSource"/>
```

现在，每个组件和主应用程序都可以通过惟一的名称引用 `DataSource` ，并且保证不会与任何其他定义发生冲突（实际上是创建名称空间），但它们引用的是同一个 `bean` 。

#### Java 配置

如果使用 `Javaconfiguration`，可以使用 `@Bean` 注释来提供别名。有关详细信息，请参见使用 `@Bean` 注释。

### 1.3.2 实例化 Bean

`bean` 定义本质上是创建一个或多个对象的方法。当询问时，容器将查看命名 `bean` 的具体类，并使用该 `bean` 定义封装的配置元数据来创建（或获取）实际对象

如果使用基于 `XML` 的配置元数据，则需要在 `<bean/>` 元素的 `class` 属性中指定对象的类型（或类）。这个类属性（在内部，它是 `BeanDefinition` 实例上的 `Class` 属性）通常是强制性的。（有关异常，请参见使用实例工厂方法和 `Bean` 定义继承进行实例化。）你可以通过以下两种方式之一使用 `Class` 属性：

* 通常，在容器本身通过反射调用其构造函数直接创建 `bean` 的情况下，指定要构造的 `bean` 类，这与使用 `new` 操作符的 `Java` 代码相当
* 要指定包含用于创建对象的静态工厂方法的实际类，在较不常见的情况下，容器调用类上的静态工厂方法来创建 `bean` 。调用静态工厂方法返回的对象类型可能是同一个类，也可能是另一个类。

#### 内部类命名

如果要为静态嵌套类配置 `bean` 定义，则必须使用嵌套类的二进制名称。

例如，如果在 `com.example` 包中有一个名为 `Something` 的类，而这个类有一个名为 `OtherThing` 的静态嵌套类，那么 `bean` 定义上的类属性的值将是 `com.example.SomeThing$OtherThing` 。

注意使用名称中的 `$` 字符将嵌套类名与外部类名分开。

#### 使用构造器实例化

通过构造函数方法创建 `bean` 时，所有普通类都可以使用 `Spring` 并与 `Spring` 兼容。也就是说，正在开发的类不需要实现任何特定的接口，也不需要以特定的方式进行编码。仅仅指定 `bean` 类就足够了。但是，根据特定 `bean` 使用的 `IoC` 类型，你可能需要一个默认（空）构造函数。

`SpringIoC` 容器几乎可以管理你希望它管理的任何类。它不仅限于管理真正的 `JavaBeans` 。大多数 `Spring` 用户更喜欢实际的 `JavaBeans` ，它只有一个默认（无参）构造函数和适当的 `setters` 和 `getter` ，它们都是按照容器中的属性建模的。你还可以在容器中拥有更多奇特的非 `bean` 样式类。例如，如果你需要使用绝对不符合 `JavaBean` 规范的遗留连接池， `Spring` 也可以管理它。

使用基于 `XML` 的配置元数据，你可以按照以下方式指定 `bean` 类：

```xml
<bean id="exampleBean" class="examples.ExampleBean"/>

<bean name="anotherExample" class="examples.ExampleBeanTwo"/>
```

有关在构造对象之后向构造函数提供参数(如果需要)和设置对象实例属性的机制的详细信息，请参阅注入依赖项。

#### 静态工厂方法实例化

在用静态工厂方法创建 `bean` 时，使用 `class` 属性指定包含静态工厂方法的类，并使用名为 `factory-method` 的属性指定工厂方法本身的名称。你应该能够调用此方法（如后面所述，带有可选参数），并返回一个活动对象，该对象随后被视为是通过构造函数创建的。这种 `bean` 定义的一个用途是在遗留代码中调用静态工厂。

下面的 `bean` 定义指定通过调用工厂方法来创建 `bean` 。定义没有指定返回对象的类型（类），只指定包含工厂方法的类。在本例中， `createInstance()` 方法必须是静态方法。下面的示例演示如何指定工厂方法：

```xml
<bean id="clientService"
    class="examples.ClientService"
    factory-method="createInstance"/>
```

下面的示例显示了使用前面的 `bean` 定义的类：

```java
public class ClientService {
    private static ClientService clientService = new ClientService();
    private ClientService() {}

    public static ClientService createInstance() {
        return clientService;
    }
}
```

#### 使用实例工厂方法实例化

类似于通过静态工厂方法进行实例化，使用实例工厂方法实例化是从容器中调用现有 `bean` 的非静态方法来创建新 `bean` 。若要使用此机制，请将 `class` 属性保留为空，并在工厂 `bean` 属性中指定当前（或父或祖先）容器中的 `bean` 名称，该容器包含要调用以创建对象的实例方法。使用 `factory-method` 属性设置工厂方法本身的名称。下面的示例演示如何配置这样的 `bean` ：

```xml
<!-- the factory bean, which contains a method called createInstance() -->
<bean id="serviceLocator" class="examples.DefaultServiceLocator">
    <!-- inject any dependencies required by this locator bean -->
</bean>

<!-- the bean to be created via the factory bean -->
<bean id="clientService"
    factory-bean="serviceLocator"
    factory-method="createClientServiceInstance"/>
```

下面的示例显示了使用相应的类：

```java
public class DefaultServiceLocator {

    private static ClientService clientService = new ClientServiceImpl();

    public ClientService createClientServiceInstance() {
        return clientService;
    }
}
```

一个工厂类也可以包含多个工厂方法，如下例所示：

```xml
<bean id="serviceLocator" class="examples.DefaultServiceLocator">
    <!-- inject any dependencies required by this locator bean -->
</bean>

<bean id="clientService"
    factory-bean="serviceLocator"
    factory-method="createClientServiceInstance"/>

<bean id="accountService"
    factory-bean="serviceLocator"
    factory-method="createAccountServiceInstance"/>
```

下面的示例显示了相应的类：

```java
public class DefaultServiceLocator {

    private static ClientService clientService = new ClientServiceImpl();

    private static AccountService accountService = new AccountServiceImpl();

    public ClientService createClientServiceInstance() {
        return clientService;
    }

    public AccountService createAccountServiceInstance() {
        return accountService;
    }
}
```

> 在 `Spring` 文档中，“工厂 `bean` ”是指在 `Spring` 容器中配置并通过实例或静态工厂方法创建对象的 `bean` 。相反， `FactoryBean` （注意大写）是 `Spring 特定的` 的 `FactoryBean` 实现类。

#### 确定 Bean 的运行时类型

要确定特定 `bean` 的运行时类型并不容易。 `bean` 元数据定义中的指定类只是一个初始类引用，可能与声明的工厂方法组合在一起，或者是一个 `FactoryBean` 类，它可能导致 `bean` 的不同运行时类型，或者在实例级工厂方法（该方法通过指定的工厂名称解析）的情况下根本不被设置。此外， `AOP` 代理可以使用基于接口的代理包装 `bean` 实例，该代理有限地公开目标 `bean` 的实际类型（只是其实现的接口）。

查找特定 `bean` 的实际运行时类型的推荐方法是对指定 `bean` 进行 `BeanFactory.getType` 调用。这将考虑到上述所有情况，并返回 `BeanFactory.getBean` 调用将返回的对象类型。

## 1.4 依赖

典型的企业应用程序不包含单个对象（或者 `Spring` 术语中的 `bean` ）。即使最简单的应用程序也有几个对象协同工作，以表示最终用户认为是一个连贯的应用程序。本节将介绍如何定义多个单独存在的 `bean` 定义，再到一个完全实现的应用程序，在这个应用程序中，对象协作以实现目标。

### 1.4.1 依赖注入

依赖注入（ `DI` ）是一个过程，在此过程中，对象仅通过构造函数参数、工厂方法的参数或在从工厂方法中构造或返回对象实例后在对象实例上设置的属性来定义它们的依赖项（即与其一起工作的其他对象）。然后，容器在创建 `bean` 时注入这些依赖项。从根本上说，这个过程是 `bean` 本身的逆（因此是名称、控制反转），它通过使用类的直接构造或 `ServiceLocator` 模式来控制其依赖项的实例化或位置。

使用 `DI` 原则，代码更加简洁，当对象提供依赖项时，解耦更有效。对象不查找其依赖项，也不知道依赖项的位置或类。因此，你的类变得更容易测试，特别是当依赖项位于接口或抽象基类上时，这些类允许在单元测试中使用存根或模拟实现。

#### 基于构造器的依赖注入

基于构造函数的 `DI` 是通过容器调用具有多个参数的构造函数来完成的，每个参数代表一个依赖项。调用带有特定参数的静态工厂方法来构造 `bean` 几乎是等价的，本讨论以类似的方式处理构造函数和静态工厂方法的参数。下面的示例显示了只能通过构造函数注入注入依赖项的类：

```java
public class SimpleMovieLister {

    // the SimpleMovieLister has a dependency on a MovieFinder
    private MovieFinder movieFinder;

    // a constructor so that the Spring container can inject a MovieFinder
    public SimpleMovieLister(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }

    // business logic that actually uses the injected MovieFinder is omitted...
}
```

注意，这个类没有什么特别之处。它是一个 `POJO`，它不依赖于容器特定的接口、基类或注释。

#### 构造器参数解析

构造函数参数解析匹配是通过使用参数类型来实现的。如果 `bean` 定义的构造函数参数中不存在潜在的歧义，则在 `bean` 定义中定义构造函数参数的顺序是当 `bean` 被实例化时将这些参数提供给适当的构造函数的顺序。考虑以下示例：

```java
package x.y;

public class ThingOne {

    public ThingOne(ThingTwo thingTwo, ThingThree thingThree) {
        // ...
    }
}
```

假设 `ThingTwo` 和 `ThingThree` 类与继承无关，则不存在潜在的歧义。因此，以下配置工作正常，你不需要在 `<constructor-arg/>` 元素中显式地指定构造函数参数索引或类型。

```java
<beans>
    <bean id="beanOne" class="x.y.ThingOne">
        <constructor-arg ref="beanTwo"/>
        <constructor-arg ref="beanThree"/>
    </bean>

    <bean id="beanTwo" class="x.y.ThingTwo"/>

    <bean id="beanThree" class="x.y.ThingThree"/>
</beans>
```

当引用另一个 `bean` 时，类型是已知的，并且可以进行匹配（如前面的示例所示）。当使用简单类型（如 `<value>true</value>`）时， `Spring` 无法确定值的类型，因此在没有帮助的情况下无法按类型匹配。考虑以下代码：

```java
package examples;

public class ExampleBean {

    // Number of years to calculate the Ultimate Answer
    private int years;

    // The Answer to Life, the Universe, and Everything
    private String ultimateAnswer;

    public ExampleBean(int years, String ultimateAnswer) {
        this.years = years;
        this.ultimateAnswer = ultimateAnswer;
    }
}
```

##### 构造器参数类型匹配

在前面的场景中，如果通过使用 `type` 属性显式指定构造函数参数的类型，容器可以使用类型匹配和简单类型。如下例所示：

```xml
<bean id="exampleBean" class="examples.ExampleBean">
    <constructor-arg type="int" value="7500000"/>
    <constructor-arg type="java.lang.String" value="42"/>
</bean>
```

##### 构造器参数索引匹配

可以使用 `index` 属性显式指定构造函数参数的索（从 0 开始），如下例所示：

```xml
<bean id="exampleBean" class="examples.ExampleBean">
    <constructor-arg index="0" value="7500000"/>
    <constructor-arg index="1" value="42"/>
</bean>
```

除了解决多个简单值的歧义外，指定索引还可以解决构造函数具有两个相同类型的参数的歧义。

##### 构造器参数名称匹配

还可以使用构造函数参数名称进行值消歧，如下面的示例所示：

```xml
<bean id="exampleBean" class="examples.ExampleBean">
    <constructor-arg name="years" value="7500000"/>
    <constructor-arg name="ultimateAnswer" value="42"/>
</bean>
```

请记住，要使这项工作不受限制，必须在启用调试标志的情况下编译代码，以便 `Spring` 可以从构造函数中查找参数名。如果不能或不希望使用调试标志编译代码，则可以使用 `@ConstructorProperties` 的 `JDK` 注释显式命名构造函数参数。然后，示例类必须如下所示：

```java
package examples;

public class ExampleBean {

    // Fields omitted

    @ConstructorProperties({"years", "ultimateAnswer"})
    public ExampleBean(int years, String ultimateAnswer) {
        this.years = years;
        this.ultimateAnswer = ultimateAnswer;
    }
}
```

#### 基于 setter 的依赖注入

基于 `setter` 的 `DI` 是在调用非参数构造函数或非参数静态工厂方法来实例化 `bean` 之后，在 `bean` 上调用 `setter` 方法来完成的。

下面的示例显示了一个只能通过使用纯 `setter` 注入进行依赖注入的类。这个类是传统的 `Java` 。它是一个 `POJO` ，它不依赖于容器特定的接口、基类或注释。

```java
public class SimpleMovieLister {

    // the SimpleMovieLister has a dependency on the MovieFinder
    private MovieFinder movieFinder;

    // a setter method so that the Spring container can inject a MovieFinder
    public void setMovieFinder(MovieFinder movieFinder) {
        this.movieFinder = movieFinder;
    }

    // business logic that actually uses the injected MovieFinder is omitted...
}
```

对于它管理的 `bean` ， `ApplicationContext` 支持基于构造函数的 `DI` 和基于 `setter` 的 `DI` 。它还支持基于 `setter` 的 `DI` ，因为已经通过构造函数方法注入了一些依赖项。你可以以 `BeanDefinition` 的形式配置依赖项，你可以将它与 `PropertyEditor` 实例结合使用，以将属性从一种格式转换为另一种格式。但是，大多数 `Spring` 用户并不直接使用这些类（即以编程的方式），而是使用 `XMLbean` 定义、带注释的组件（即带有 `@Component` 、 `@Controller` 等注释的类）或基于 `Java` 的 `@Configuration` 类中的 `@Bean` 方法。然后将这些源内部转换为 `BeanDefinition` 实例，并用于加载整个 `SpringIoC` 容器实例。

> ​                              **基于构造器的 DI 还是基于 setter 的 DI ？**
>
> 由于可以混合基于构造函数的 `DI` 和基于 `setter` 的 `DI` ，因此使用构造函数进行强制依赖关系和用于可选依赖项的 `setter` 方法或配置方法是一个很好的经验规则。注意，在 `setter` 方法上使用 `@Required` 注释可以使属性成为必需的依赖项；但是，构造函数注入加上参数的编程验证更好。
>
> `Spring Team` 通常提倡构造函数注入，因为它允许你将应用程序组件实现为不可变对象，并确保所需的依赖项不是空的。此外，构造函数注入的组件总是以完全初始化状态返回给客户端（调用）代码。顺便提一句，大量的构造函数参数是一种糟糕的代码气味，这意味着类可能有太多的责任，应该进行重构，以更好地解决关注点的适当分离问题。
>
> `setter` 注入应该主要用于可选的依赖项，这些依赖项可以在类中分配合理的默认值。否则，必须在代码使用依赖项的任何地方执行非空检查。 `setter` 注入的一个好处是 `setter` 方法使该类的对象能够在以后重新配置或重新注入。因此，通过 `JMXMBean` 进行管理是 `setter` 注入的一个引人注目的用例。
>
> 使用对特定类最有意义的 `DI` 样式。有时，在处理你没有源的第三方类时，会为你做出选择。例如，如果第三方类不公开任何 `setter` 方法，则构造函数注入可能是惟一可用的 `DI` 形式。

#### 依赖解决过程

容器执行 `bean` 依赖解析，如下所示：

* 使用描述所有 `bean` 的配置元数据创建和初始化 `ApplicationContext` 。配置元数据可以由 `XML` 、 `Java` 代码或注释指定
* 对于每个 `bean` ，其依赖项以属性、构造函数参数或静态工厂方法的参数的形式表示（如果你使用它而不是普通的构造函数）。当 `bean` 实际创建时，这些依赖项将提供给 `bean` 
* 每个属性或构造函数参数都是要设置的值的实际定义，或者是对容器中另一个 `bean` 的引用
* 每个作为值的属性或构造函数参数都从其指定的格式转换为该属性或构造函数参数的实际类型。默认情况下， `Spring` 可以将以字符串格式提供的值转换为所有内置类型，例如 `int` 、 `long` 、 `string` 、 `boole` 等等

`Spring` 容器在创建容器时验证每个 `bean` 的配置。但是，在实际创建 `bean` 之前，不会设置 `bean` 属性本身。单例作用域并设置为预实例化（默认）的 `bean` 是在创建容器时创建的。作用域在 `Bean`   `Scopes` 中定义。否则，只有在被请求时才会创建 `bean` 。创建 `bean` 可能会导致创建 `bean` 图，因为 `bean` 的依赖项及其依赖项（等等）被创建和分配。请注意，这些依赖项之间的匹配可能会出现很晚--也就是说，在第一次创建受影响的 `bean` 时。

> ​                                        **循环依赖**
>
> 如果主要使用构造函数注入，则可以创建不可解决的循环依赖场景。
>
> 例如： `A` 类需要通过构造函数注入 `B` 类的实例， `B` 类需要 `A` 类通过构造函数注入的实例。如果你为类 `A` 和 `B` 配置 `bean` 以相互注入， `SpringIoC` 容器将在运行时检测这个循环引用，并抛出一个 `BeanCurrentlyInCreationException` 。
>
> 一种可能的解决方案是编辑由 `setter` 而不是构造函数配置的某些类的源代码。或者，避免构造函数注入，只使用 `setter` 注入。换句话说，尽管不建议这样做，但你可以使用 `setter` 注入配置循环依赖项。
>
> 与典型的情况不同（没有循环依赖关系）， `bean`   `A` 和 `bean`   `B` 之间的循环依赖要求在完全初始化自身之前将其中一个 `bean` 注入另一个 `bean` （典型的鸡和蛋场景）。

通常，你可以信任 `Spring` 做正确的事。它在容器加载时检测配置问题，例如对不存在的 `Bean` 的引用和循环依赖项。在实际创建 `bean` 时， `Spring` 设置属性并尽可能晚地解决依赖关系。这意味着，如果创建对象或其依赖项之一有问题，则正确加载的 `Spring` 容器以后可以在你请求对象时生成异常-例如，由于缺少或无效的  `Bean` 引发异常属性。某些配置问题的这种潜在的延迟可见性是为什么 `ApplicationContext` 默认情况下，实现会实例化单例 `bean` 。在实际需要这些 `bean` 之前，要花一些前期时间和内存来创建它们，你会在创建 `bean` 时发现配置问题 `ApplicationContext` ，而不是稍后发现。你仍然可以覆盖此默认行为，以便单例 `bean` 延迟初始化，而不是预先实例化。

如果不存在循环依赖关系，则在将一个或多个协作 `bean` 注入到依赖 `bean` 中时，每个协作 `bean` 都将在注入到依赖 `bean` 中之前被完全配置。这意味着，如果 `bean`   `A` 依赖于 `bean`   `B` ，则 `Spring`   `IoC` 容器会在对 `bean`   `A` 调用 `setter` 方法之前完全配置 `beanB` 。换句话说，实例化了 `bean` （如果它不是预先实例化的单例） ），设置其依赖项，并调用相关的生命周期方法（例如已配置的 `init` 方法 或 `InitializingBean` 回调方法）。

#### 依赖注入的例子

以下示例将基于 `XML` 的配置元数据用于基于 `setter` 的 `DI` 。 `Spring`   `XML` 配置文件的一小部分指定了一些 `bean` 定义，如下所示：

```xml
<bean id="exampleBean" class="examples.ExampleBean">
    <!-- setter injection using the nested ref element -->
    <property name="beanOne">
        <ref bean="anotherExampleBean"/>
    </property>

    <!-- setter injection using the neater ref attribute -->
    <property name="beanTwo" ref="yetAnotherBean"/>
    <property name="integerProperty" value="1"/>
</bean>

<bean id="anotherExampleBean" class="examples.AnotherBean"/>
<bean id="yetAnotherBean" class="examples.YetAnotherBean"/>
```

`ExampleBean` 类如下：

```java
public class ExampleBean {

    private AnotherBean beanOne;

    private YetAnotherBean beanTwo;

    private int i;

    public void setBeanOne(AnotherBean beanOne) {
        this.beanOne = beanOne;
    }

    public void setBeanTwo(YetAnotherBean beanTwo) {
        this.beanTwo = beanTwo;
    }

    public void setIntegerProperty(int i) {
        this.i = i;
    }
}
```

在前面的示例中，声明了 `setter` 以与 `XML` 文件中指定的属性匹配。以下示例使用基于构造函数的 `DI` ：

```xml
<bean id="exampleBean" class="examples.ExampleBean">
    <!-- constructor injection using the nested ref element -->
    <constructor-arg>
        <ref bean="anotherExampleBean"/>
    </constructor-arg>

    <!-- constructor injection using the neater ref attribute -->
    <constructor-arg ref="yetAnotherBean"/>

    <constructor-arg type="int" value="1"/>
</bean>

<bean id="anotherExampleBean" class="examples.AnotherBean"/>
<bean id="yetAnotherBean" class="examples.YetAnotherBean"/>
```

下面是对应的 `ExampleBean` 类：

```java
public class ExampleBean {

    private AnotherBean beanOne;

    private YetAnotherBean beanTwo;

    private int i;

    public ExampleBean(
        AnotherBean anotherBean, YetAnotherBean yetAnotherBean, int i) {
        this.beanOne = anotherBean;
        this.beanTwo = yetAnotherBean;
        this.i = i;
    }
}
```

`Bean` 定义中指定的构造函数参数用作的构造函数的参数 `ExampleBean` 。

现在考虑这个示例的一个变体，在该变体中，不是使用构造函数，而是告诉 `Spring` 调用 `static` 工厂方法以返回对象的实例：

```xml
<bean id="exampleBean" class="examples.ExampleBean" factory-method="createInstance">
    <constructor-arg ref="anotherExampleBean"/>
    <constructor-arg ref="yetAnotherBean"/>
    <constructor-arg value="1"/>
</bean>

<bean id="anotherExampleBean" class="examples.AnotherBean"/>
<bean id="yetAnotherBean" class="examples.YetAnotherBean"/>
```

以下示例显示了相应的 `ExampleBean` 类：

```java
public class ExampleBean {

    // a private constructor
    private ExampleBean(...) {
        ...
    }

    // a static factory method; the arguments to this method can be
    // considered the dependencies of the bean that is returned,
    // regardless of how those arguments are actually used.
    public static ExampleBean createInstance (
        AnotherBean anotherBean, YetAnotherBean yetAnotherBean, int i) {

        ExampleBean eb = new ExampleBean (...);
        // some other operations...
        return eb;
    }
}
```

`static` 工厂方法的参数由 `<constructor-arg/>` 元素提供，就好像实际使用了构造函数一样。 `factory` 方法返回的类的类型不必与包含 `staticfactory` 方法的类具有相同的类型（尽管在此示例中是）。实例（非静态）工厂方法可以以本质上相同的方式使用（除了使用 `factory` - `bean` 属性代替 `class` 属性之外），因此在此不讨论这些细节。

### 依赖注入和配置的详解

#### 直接值（原始值，String等）

#### 引用其他 Bean（协作）

#### 内部 Bean

#### 集合

#### Null 和 空字符串

#### xml 中 p 命名空间的简写

#### xml 中 c 命名空间的简写

# 5. 面向切面编程

面向切面编程（`AOP`）是面向对象编程的一种方式，它提供了另外一种思考程序结构的方式。`OOP` 中模块化的关键单位是 “类”，然而，`AOP` 中模块化的关键单位是 “切面”。切面可以使关注点模块化（例如事务管理），这种方式可以横切多个类型和对象（这些关注点通常被称为 `AOP` 哲学中的 “横切” 问题）

`Spring` 的一个关键组件就是 `AOP` 框架，而 `Spring IoC` 容器并不依赖于 `AOP`（这就意味着如果你不想使用 `AOP`，那你就只使用 `Spring IoC` 就可以了），`AOP` 是 `Spring IoC` 的一种补充，提供了一个非常棒的中间件解决方案。

>Spring 通过使用基于 xml 的方法或 @AspectJ 注释样式提供简单而强大的写作自定义切面的方式。 这两个风格都提供所有类型的 advice 和使用 AspectJ Pointcut 语言，同时仍然使用 Spring AOP 进行编织。

在 `Spring` 框架中，`AOP` 被用于：

* 提供声明式的企业服务，最重要的服务莫过于 **声明事务管理服务**
* 可以让用户实现自定义的切面，在 `OOP` 模式中补充 `AOP` 模式的使用

## 5.1 概念

让我们从定义一些 `AOP` 的概念和术语开始。这些元素不是 `Spring` 所特有的。不幸的是，`AOP` 的术语不是特别的直观。但是，如果 `Spring` 使用了自己的术语，一定会有着更多的混淆。

* `Aspect（切面）`：涉及了多个类的模块化的聚集，在企业级 `Java` 应用中，事务管理是一个很好的示例。在 `Spring AOP` 中，`Aspect（切面）` 由一个常规的类实现，这个类要么配置在 `xml` 文件中，要么使用 `@Aspect` 注解
* `Join point(连接点)`：程序执行期间的一个点，例如方法执行或异常处理。在 `Spring AOP` 中，一个 `join point（连接点）` 总是代表着一个方法的执行
* `Advice（增强）`：在某个特定的 **连接点** 上，由 **切面** 采取的行动。`advice（增强）` 的不同类型包括：`around、before、after`（增强类型在后面有讨论）在许多 `AOP` 框架中，包括 `Spring`，将 `advice（增强）` 模块化为一个拦截器，并围绕着 **连接点** 维护着一个拦截器链









- Pointcut: A predicate that matches join points. Advice is associated with a pointcut expression and runs at any join point matched by the pointcut (for example, the execution of a method with a certain name). The concept of join points as matched by pointcut expressions is central to AOP, and Spring uses the AspectJ pointcut expression language by default.
- Introduction: Declaring additional methods or fields on behalf of a type. Spring AOP lets you introduce new interfaces (and a corresponding implementation) to any advised object. For example, you could use an introduction to make a bean implement an `IsModified` interface, to simplify caching. (An introduction is known as an inter-type declaration in the AspectJ community.)
- Target object: An object being advised by one or more aspects. Also referred to as the “advised object”. Since Spring AOP is implemented by using runtime proxies, this object is always a proxied object.
- AOP proxy: An object created by the AOP framework in order to implement the aspect contracts (advise method executions and so on). In the Spring Framework, an AOP proxy is a JDK dynamic proxy or a CGLIB proxy.
- Weaving: linking aspects with other application types or objects to create an advised object. This can be done at compile time (using the AspectJ compiler, for example), load time, or at runtime. Spring AOP, like other pure Java AOP frameworks, performs weaving at runtime.
