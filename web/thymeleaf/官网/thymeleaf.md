[Toc]

# 1. 简介

## 1.1 Thymeleaf 是什么

`Thymeleaf` 是一个现代化的服务端 `Java` 模板引擎，可以用于 `Web` 应用，也可以用于独立的环境，它能够处理 `HTML、XML、JavaScript、CSS`，甚至是解释型文本

`Thymeleaf` 的目标是提供一个优雅地、高度可维护的模板创建方式。为了实现这一目的，它构建了自然模板的概念，以便用不影响模板被用作设计原型的方式将自己的逻辑注入到模板文件中。这样的方式会增强设计与开发团队之间的沟通，架起桥梁来消除团队之间的鸿沟

从一开始，`Thymeleaf` 在思想中始终以 `Web` 标准为约束在进行设计——尤其是 `HTML5`—— 如果有需要，可以创建完全的验证模板

## 1.2 Thymeleaf 可以处理的模板类型

`Thymeleaf` 可以处理 6 种模板模式，真的是开箱即用，下面的每种类型都被叫做 **模板模式**：

* `HTML`
* `XML`
* `Text`
* `JavaScript`
* `CSS`
* `Raw`

上面的类型中，两种是标记型模板模式（`HTML、XML`），三种是文本模板模式（`Text、JavaScript、CSS`），一种是无操作模板模式（`Raw`）

`HTML` 模板模式将允许任何类型的 `HTML` 输入，包括 `HTML5，HTML 4和XHTML`。 并且在输出时，无论是否执行良好的验证，都将会最大程度的遵守模板代码/结构

`XML` 模板模式将允许 `XML` 输入。 在这种情况下，期望代码将是格式良好的——没有未关闭的标签，没有未引用的属性等——如果发现违规，解析器将抛出异常。 请注意，不会执行验证（针对DTD或XML模式）。

文本模板模式将允许使用非标记性质、可以使用特殊语法的模板。 此类模板的示例可能是文本电子邮件或模板文档。 请注意，`HTML` 或 `XML` 模板也可以作为文本处理，在这种情况下，它们将不会被解析为标记，并且每个标记，`doctype，commit`，等将被视为纯粹的文本

`JavaScript` 模板模式将允许在 `Thymeleaf` 应用程序中处理 `JavaScript` 文件。 这意味着能够以同样的方式在`HTML` 文件中完成 `JavaScript` 文件中的模型数据，但是不包括 `JavaScript` 的特殊集成，例如专门的逃逸或自然脚本。 `JavaScript` 模板模式被视为文本模式，因此使用与文本模板模式相同的特殊语法。

`CSS` 模板模式将允许处理 `Thymeleaf` 应用程序的 `CSS` 文件。 类似于 `JavaScript` 模式，`CSS` 模板模式也是文本模式，并使用文本模板模式的特殊处理语法

原始模板模式根本不会处理模板。 它意味着用于将未受影响的资源（文件，`URL`，响应等）插入正在处理的模板中。 例如，`HTML` 格式中的外部不受控制的资源可以将其包含在应用程序模板中，这些资源包含的任何 `Thymeleaf` 都不会被执行

## 1.3 方言：标准方言

`Thymeleaf` 是一个非常易于扩展的模板引擎（实际上它可以被称为模板引擎框架），可以自定义模板的处理程序，甚至达到精细的级别

应用逻辑到一个标记制品（标签、文本、评论、或者在模板不标记时只有一些点位符）的对象被叫做 `processor` ——这些都是方面的一般组成。开箱即用，`Thymeleaf` 的核心类库提供了一种称为 `Standard Dialect` 的方言，对大数据使用者来说，这已经足够了

> 请注意，方言实际上没有处理器，并且完全由其他种类的工件组成，但处理器绝对是最常见的用例。

本教程涵盖了标准方言。 在下文中，即使未明确提及，涉及的每个属性和语法功能都由此方言定义

当然，如果用户在利用库的高级功能的同时想定义自己的处理逻辑，可以创建自己的方言（即使是对标准的扩展）。 `Thymeleaf` 也可以配置为一次使用多个方言

> 官方 thymeleaf-spring3 和  thymeleaf-spring4 都定义了一个称为 “SpringStandard” 的方言，它与标准方言相同，但具有更好的适应性，可以更好地利用 spring 框架中的某些功能（例如 ，通过使用 Spring 表达语言或SpringEL 而不是 OGNL）。 因此，如果你是一个 Spring MVC 用户，就不会浪费时间，就像所学习的几乎所有内容都将在你的 Spring 应用程序中使用。

标准方言的大多数处理器都是属性处理器。 这甚至允许浏览器在处理之前正确显示 `HTML` 模板文件，因为它们将简单地忽略附加属性。 例如，使用标记库的 `JSP` 可以包含代码片段，而不由浏览器直接显示：

```html
<form:inputText name="userName" value="${user.name}" />
```

`Thymeleaf` 标准方言可以让我们实现相同的功能：

```html
<input type="text" name="userName" value="James Carrot" th:value="${user.name}" />
```

上面的代码不仅可以通过浏览器正确显示，还允许我们（可选地）指定它的值属性（`James Carrot`），将在浏览器中静态打开时显示 `value` 属性的值，然后该值将由在模板处理期间评估 `$ {user.name}` 时产生的值来代替

这有助于设计师和开发人员在相同的模板文件上工作，并减少将静态原型转换为工作模板文件所需的工作。 这样做的能力是一个名为 `Natural` 模板的功能

# 2. 优势

教程中出现的代码等素材，都可以在 [这里](https://github.com/thymeleaf/thymeleafexamples-gtvg) 找到

## 2.1 杂货铺网站

为了更好地解释 `Thymeleaf` 处理模板的概念，本教程演示使用的应用程序，可以通过项目的网站进行下载

此应用程序是虚拟杂货铺的网站，并将为我们展示 `Thymeleaf` 的许多功能

开始之前，需要为应用创建一些实体对象：

* `Products`：商品
* `Customers`：顾客
* `Orders`：订单
* `Comments`：评论

[![2ciwuT.png](https://z3.ax1x.com/2021/06/09/2ciwuT.png)](https://imgtu.com/i/2ciwuT)

应用程序有一个非常简单的服务层，由包含方法的服务对象组成：

```java
public class ProductService {

    ...

    public List<Product> findAll() {
        return ProductRepository.getInstance().findAll();
    }

    public Product findById(Integer id) {
        return ProductRepository.getInstance().findById(id);
    }
    
}
```

在 `Web` 层，应用程序有一个过滤器，依赖于请求的 `URL` 地址，它将请求委托向给启用了 `Thymeleaf` 的命令：

```java
private boolean process(HttpServletRequest request, HttpServletResponse response)
        throws ServletException {
    
    try {

        // This prevents triggering engine executions for resource URLs
        if (request.getRequestURI().startsWith("/css") ||
                request.getRequestURI().startsWith("/images") ||
                request.getRequestURI().startsWith("/favicon")) {
            return false;
        }

        
        /*
         * Query controller/URL mapping and obtain the controller
         * that will process the request. If no controller is available,
         * return false and let other filters/servlets process the request.
         */
        IGTVGController controller = this.application.resolveControllerForRequest(request);
        if (controller == null) {
            return false;
        }

        /*
         * Obtain the TemplateEngine instance.
         */
        ITemplateEngine templateEngine = this.application.getTemplateEngine();

        /*
         * Write the response headers
         */
        response.setContentType("text/html;charset=UTF-8");
        response.setHeader("Pragma", "no-cache");
        response.setHeader("Cache-Control", "no-cache");
        response.setDateHeader("Expires", 0);

        /*
         * Execute the controller and process view template,
         * writing the results to the response writer. 
         */
        controller.process(
                request, response, this.servletContext, templateEngine);
        
        return true;
        
    } catch (Exception e) {
        try {
            response.sendError(HttpServletResponse.SC_INTERNAL_SERVER_ERROR);
        } catch (final IOException ignored) {
            // Just ignore this
        }
        throw new ServletException(e);
    }
    
}
```

`IGTVGController` 接口如下：

```java
public interface IGTVGController {

    public void process(
            HttpServletRequest request, HttpServletResponse response,
            ServletContext servletContext, ITemplateEngine templateEngine);    
    
}
```

现在需要做的就是创建 `IGTVGController` 接口的实现，从 `service` 中获取数据，然后使用 `ITemplateEngine` 对象处理模板

最终，显示如下：

<img src="https://www.thymeleaf.org/doc/tutorials/3.0/images/usingthymeleaf/gtvg-view.png"/>

下面，我们仔细探究一下模板引擎是如何被实例化的

## 2.2 创建和配置模板引擎

上面的过滤器代码包含了 `process()` 方法：

```java
ITemplateEngine templateEngine = this.application.getTemplateEngine();
```

这就意味着 `GTVGApplication` 类负责创建和配置 `Thymeleaf` 应用中最重要的一个对象：**模板引擎** 实例（实现了 `ITemplateEngine` 接口）

`org.thymeleaf.TemplateEngine` 对象的实例化：

```java
public class GTVGApplication {
  
    
    ...
    private final TemplateEngine templateEngine;
    ...
    
    
    public GTVGApplication(final ServletContext servletContext) {

        super();

        ServletContextTemplateResolver templateResolver = 
                new ServletContextTemplateResolver(servletContext);
        
        // HTML is the default mode, but we set it anyway for better understanding of code
        templateResolver.setTemplateMode(TemplateMode.HTML);
        // This will convert "home" to "/WEB-INF/templates/home.html"
        templateResolver.setPrefix("/WEB-INF/templates/");
        templateResolver.setSuffix(".html");
        // Template cache TTL=1h. If not set, entries would be cached until expelled
        templateResolver.setCacheTTLMs(Long.valueOf(3600000L));
        
        // Cache is set to true by default. Set to false if you want templates to
        // be automatically updated when modified.
        templateResolver.setCacheable(true);
        
        this.templateEngine = new TemplateEngine();
        this.templateEngine.setTemplateResolver(templateResolver);
        
        ...

    }

}
```

配置 `TemplateEngine` 对象有很多种方法，但是代码中这为数不多的几行，已经把必须的步骤都展示给我们了

## 2.3 模板解析器

```java
ServletContextTemplateResolver templateResolver = 
        new ServletContextTemplateResolver(servletContext);
```

模板解析器其实就是实现了 `Thymeleaf` 接口 `org.thymeleaf.templateresolver.ITemplateResolver` 的类：

```java
public interface ITemplateResolver {

    ...
  
    /*
     * Templates are resolved by their name (or content) and also (optionally) their 
     * owner template in case we are trying to resolve a fragment for another template.
     * Will return null if template cannot be handled by this template resolver.
     */
    public TemplateResolution resolveTemplate(
            final IEngineConfiguration configuration,
            final String ownerTemplate, final String template,
            final Map<String, Object> templateResolutionAttributes);
}
```

这些对象负责确定我们的模板将如何访问，并且在此 `GTVG` 应用程序中，`org.thymeleaf.templaterSolver.servletContextTemplaterSolver` 意味着我们将从 `Servlet` 上下文中作为资源检索我们的模板文件：应用程序范围内的 `javax .servlet.servletContext` 对象，在每个 `Java Web` 应用程序中存在，它可以从 `Web` 应用程序 `root` 中解析资源。

但只有这些还是不够的，还需要在它的上面设置一些配置参数。 首先，模板模式：

```java
templateResolver.setTemplateMode(TemplateMode.HTML);
```

`HTML` 是 `ServletContextTemplaterSolver` 的默认模板模式，这样的好处是：会清楚的知道代码文件发生的事情

```java
templateResolver.setPrefix("/WEB-INF/templates/");
templateResolver.setSuffix(".html");
```

前缀和后缀修改了我们将传递给引擎的模板名称以获取要使用的实际资源名称。 	

使用此配置，模板名称“产品/列表”将对应于：

```java
servletContext.getResourceAsStream("/WEB-INF/templates/product/list.html")
```

作为可选项，通过 `CachettLMS` 属性，在模板解析器处配置解析模板可以生存在缓存中的时间量：

```java
templateResolver.setCacheTTLMs(3600000L);
```

如果达到最大高速缓存大小，则达到 `TTL` 之前仍然可以从缓存中启动模板，并且它是当前缓存的最旧的条目。

> 可以通过实现 `ICacheManager` 接口或通过修改 `StandardCacheManager` 对象来管理默认缓存来定义缓存行为和大小。

关于模板解析器要了解的东西还很多，但是，我们接下来要模板引擎对象的创建了

## 2.4 模板引擎

模板引擎对象是 `org.thymeleaf.itemplingengine` 接口的实现。 这些实现之一是由 `Thymeleaf` 核心提供：`org.thymeleaf.templingeNgine`，我们在此创建一个实例：

```java
templateEngine = new TemplateEngine();
templateEngine.setTemplateResolver(templateResolver);
```

相当简单，不是吗？ 我们所需要的只是创建一个实例并将模板解析器设置为它。

模板解析器是唯一需要的参数，尽管稍后将涵盖许多其他（消息解析器，缓存大小等）。 但是现在，这就是我们所需要的。

我们的模板引擎现在准备就绪，我们可以开始使用 `Thymeleaf` 创建我们的页面。

# 3. 使用文本

## 3.1 多语言版本的 welcome

我们的第一个任务就是创建杂货铺网站的首页。

该页面的第一个版本是极其的简单：只是一个标题和欢迎的文字。`/WEB-INF/templates/home.html`：

```html
<!DOCTYPE html>

<html xmlns:th="http://www.thymeleaf.org">

  <head>
    <title>Good Thymes Virtual Grocery</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <link rel="stylesheet" type="text/css" media="all" 
          href="../../css/gtvg.css" th:href="@{/css/gtvg.css}" />
  </head>

  <body>
  
    <p th:text="#{home.welcome}">Welcome to our grocery store!</p>
  
  </body>

</html>
```

需要注意到的第一件事是此文件是可以由任何浏览器正确显示的 `HTML5`，因为它不包含任何非 `HTML` 标记（浏览器忽略他们不理解的所有属性，如 `Th：xxx`）。

但是，此模板并不是一个有效的 `HTML5` 文档，因为文件中使用的这些非标准属性在 `TH：*` 表单中不允许使用`HTML5` 规范。 实际上，我们甚至将 `XMLNS` 添加到 `<HTML>` 标记，绝对是非 `HTML5`：

```html
<html xmlns:th="http://www.thymeleaf.org">
```

这对模板处理没有任何影响，但是作为一种声明，可以防止 `IDE` 抱怨所有这些 `TH` 的命名空间所定义的属性。

那么如果我们想制作这个符合 `HTML5` 规范的模板该怎么办？ 非常简单：在属性名上使用 `data-` 前缀，而不是冒号（:)：

```html
<!DOCTYPE html>

<html>

  <head>
    <title>Good Thymes Virtual Grocery</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <link rel="stylesheet" type="text/css" media="all" 
          href="../../css/gtvg.css" data-th-href="@{/css/gtvg.css}" />
  </head>

  <body>
  
    <p data-th-text="#{home.welcome}">Welcome to our grocery store!</p>
  
  </body>

</html>
```

`HTML5` 规范允许自定义的数据前缀属性，因此，在上面的此代码中，我们的模板将是一个有效的 `HTML5` 文档。

> 这两个符号的写法都是完全等同的和可互换的，但为了简单和代码样本的简单性，本教程将使用命名空间表示法（`TH：`）。 此外，`TH：*` 符号更普遍，允许在每个 `Thymeleaf ` 模板模式（`XML，文本......`）中允许，而数据符号仅在 `HTML` 模式下允许。

### 使用 th:text 和外部化文本

外部化文本是将模板代码的片段从模板文件中提取，以便它们可以保存在单独的文件中（通常是 `oproperties` 文件），并且它们可以轻松地替换为以其他语言编写的等效文本（一个名为 `Internationalization` 或 `Simply I18N`）的等效文本 。 外部化文本碎片通常称为“消息”。

消息始终具有标识它们的键，`Thymeleaf` 允许指定文本应与 `＃{...}` 语法对应的特定消息：

```html
<p th:text="#{home.welcome}">Welcome to our grocery store!</p>
```

我们可以在这里看到的实际上是 `Thymeleaf` 特标准方言的两个不同的功能：

* `TH：TEXT` 属性，它对表达式进行计算，得出值，并把值设置到标签的主体内容中，在替换 `Welcome to our grocery store!` 这段文字时更有效率
* 在标准表达式语法中指定的 `＃{home.welcome}` 表达式指示 `th：text` 属性应该是与我们正在处理模板的那个语言环境对应的 `home.welcome` 键的值

那么，到底什么是外部化文本？

在 `Thymeleaf` 中，外部化文本的位置是可配置的，并且，它也依赖于项目中使用的 `org.thymeleaf.messageresolver.IMessageResolver` 接口的实现。一般情况下，将使用 `*.properties` 文件，当然，如果有需求，我们可以创建自己的实现，例如，从数据库获取信息

但是，在初始化期间，还没有为我们的模板引擎指定消息解析器，也就是说，现在应用使用的是 **标准的信息解析器**，是由 `org.thymeleaf.messageresolver.StandardMessageResolver` 实现的

标准的信息解析器期望在与 `/WEB-INF/templates/home.html` 同级的的文件夹下，找到名称相同，后缀为 `.properties` 的文件，并从中找到信息，文件可能的位置如下：

* 英语：`/WEB-INF/templates/home_en.properties`
* 西班牙语：`/WEB-INF/templates/home_es.properties`
* 葡萄牙语（巴西）：`/WEB-INF/templates/home_pt_BR.properties`
* 默认文本（如果没有匹配到）：`/WEB-INF/templates/home.properties`

下面是 `home_es.properties` 文件内的部分内容：

```properties
home.welcome=¡Bienvenido a nuestra tienda de comestibles!
```

要让 `Thymeleaf` 处理自己的模板，以上就是我们所要做的所有事情了。下面，让我们创建首页对应的 `Controller`

### 上下文

在这里，我们将创建实现了 `IGTVGController` 接口的类 `HomeController`：

```java
public class HomeController implements IGTVGController {

    public void process(
            final HttpServletRequest request, final HttpServletResponse response,
            final ServletContext servletContext, final ITemplateEngine templateEngine)
            throws Exception {
        
        WebContext ctx = 
                new WebContext(request, response, servletContext, request.getLocale());
        
        templateEngine.process("home", ctx, response.getWriter());
        
    }

}
```

代码中的第一件事情就是上下文的创建。`Thymeleaf` 的上下文是实现了 `org.thymeleaf.context.IContex` 接口的对象，在模板被执行期间，该上下文中包含了一个变量 `Map` ，该 `Map` 中存放的是所有需要的数据，当然，上下文中还有外部化文本中必须用到的本地化配置的字符

```java
public interface IContext {

    public Locale getLocale();
    public boolean containsVariable(final String name);
    public Set<String> getVariableNames();
    public Object getVariable(final String name);
    
}
```

下面的代码是接口的实现版本，也就意味着这段代码可以在基于 `ServletAPI` 的 `web` 应用（比如 `SpringMVC`）中运行：

```java
public interface IWebContext extends IContext {
    
    public HttpServletRequest getRequest();
    public HttpServletResponse getResponse();
    public HttpSession getSession();
    public ServletContext getServletContext();
    
}
```

在 `Thymeleaf` 的核心类库中，为这些接口每个都提供了具体的实现：

* `org.thymeleaf.context.Context` 实现了 `IContext` 接口
* `org.thymeleaf.context.WebContext` 实现了 `IWebContext` 接口

和你在 `Controller` 中看到的一样，`WebContext` 正是我们所使用的。事实上，这是因为要使用 `ServletContextTemplateResolver`， 必须要求上下文实现 `IWebContext`

```java
WebContext ctx = new WebContext(request, response, servletContext, request.getLocale());
```

构造器方法的四个参数中，只有三个参数是必须的，这是因为如果没有指定本地化参数，将会使用系统默认的本地化参数（但在真实的应用环境中，千万不要让它发生）

在模板中，可以从 `WebContext` 获取请求参数、`request、session、application` 对象的属性：

* `${x}` ：将从 `Thymeleaf` 上下文，或从 `request` 属性中获取 `x`
* `${param.x}`：将返回 `request` 中 `x` 参数的值（可能是多值）
* `${session.x}`：将返回 `session` 的属性 `x` 的值
* `${application.x}`：将返回 `servlet` 上下文中属性 `x` 的值

### 执行模板引擎

随着上下文对象的准备完毕，现在就可以使用上下文调用模板引擎来处理模板了（通过名称），并把结果传递给 `response writer`，这样就可以通过响应流进行输出了：

```java
templateEngine.process("home", ctx, response.getWriter());
```

下面是使用西班牙本地化的结果：

```html
<!DOCTYPE html>

<html>

  <head>
    <title>Good Thymes Virtual Grocery</title>
    <meta content="text/html; charset=UTF-8" http-equiv="Content-Type"/>
    <link rel="stylesheet" type="text/css" media="all" href="/gtvg/css/gtvg.css" />
  </head>

  <body>
  
    <p>¡Bienvenido a nuestra tienda de comestibles!</p>

  </body>

</html>
```

## 3.2 变量和文本更多的内容

### 非转义文本

`home` 页面最简单的版本看起来已经完成了，但是这里面还有一些问题没有考虑到……比如说下面的信息应该如何处理？

```properties
home.welcome=Welcome to our <b>fantastic</b> grocery store!
```

如果按照先前的模板执行，将会得到如下的结果：

```html
<p>Welcome to our &lt;b&gt;fantastic&lt;/b&gt; grocery store!</p>
```

这和我们的预期明显不一样，这是因为要在浏览器中显示，因此 `<b>`被转义了

这是 `th:text` 属性的默认行为。如果你想要停留 `html` 标签的原样不对其进行转义，那你需要使用另一个属性：`th:utext`：

```html
<p th:utext="#{home.welcome}">Welcome to our grocery store!</p>
```

输出如下：

```html
<p>Welcome to our <b>fantastic</b> grocery store!</p>
```

### 变量的使用和显示

现在，我们要在页面中添加更多的内容。例如：在欢迎文字的下方，显示一下日期，效果如下：

```html
Welcome to our fantastic grocery store!

Today is: 12 july 2010
```

首先，需要修改 `Controller`，把日期添加为一个上下文的变量

```java
public void process(
            final HttpServletRequest request, final HttpServletResponse response,
            final ServletContext servletContext, final ITemplateEngine templateEngine)
            throws Exception {
        
    SimpleDateFormat dateFormat = new SimpleDateFormat("dd MMMM yyyy");
    Calendar cal = Calendar.getInstance();
        
    WebContext ctx = 
            new WebContext(request, response, servletContext, request.getLocale());
    ctx.setVariable("today", dateFormat.format(cal.getTime()));
        
    templateEngine.process("home", ctx, response.getWriter());
        
}
```

就这样，在上下文中添加了一个名为 `today` 的 `String` 类型的变量，现在，把它显示到模板中：

```html
<body>

  <p th:utext="#{home.welcome}">Welcome to our grocery store!</p>

  <p>Today is: <span th:text="${today}">13 February 2011</span></p>
  
</body>
```

如你所见，在上面的代码中仍然使用的 `th:text` 属性（这是合适的，因为我们想替换整个标签的内容），但是语法上稍稍有些不一样，这次，没有使用 `#{}` （消息表达式 ），使用了 `${}`。这是 **变量表达式**，它包含了 `OGNL` 表达式（`Object Graph Navigation Language`），上面讨论过，这会在上下文变量 `Map` 中执行

`${today}` 的意思是：“给我名为 `today` 变量的值”。这样的表达式会更加复杂（如：`${user.name}` 就是获取 `user` 变量的 `getName()` 方法的值）

属性值会有非常多的可能：消息、变量表达式等，下一节将带你一探究竟。

# 标准表达式语法

先停下杂货铺网站的创建，休息一下，学习 `Thymeleaf` 语法中最重要的部分：`Thymeleaf` 标准表达式语法

上面，已经看到了两种可用的语法：信息表达式（`#{}`）、变量表达式（`${}`）：

```html
<p th:utext="#{home.welcome}">Welcome to our grocery store!</p>

<p>Today is: <span th:text="${today}">13 february 2011</span></p>
```

当然，还有一些其它的类型

首先，快速的浏览一下标准表达式元素：

* 变量表达式：`${}`
* 选择变量表达式：`*{}`
* 信息表达式：`#{}`
* `URL` 连接表达式：`@{}`
* 片断表达式：`~{}`

字面量：

* 文本字面值：`'one text'`，`'Another One!'`
* 数字字面值：`0`，`34`，`3.0`，`12.3`
* 布尔字面值：`true`，`false`
* `Null` 字面值：`null`
* 文字标记：`one`，`sometext`，`main`

文本操作：

* 字符串连接符：`+`
* 文本替换：`|The name is ${name}|`

数学操作符：

* 二元操作符：`+、-、*、/、%`
* 减号（一元操作符）：`-`

布尔操作符：

* 二元操作符：`and、or`
* 取反（一元操作符）：`!、not`

比较和相等：

* 比较：`>、>=、<、<=`（`gt、ge、lt、le`）
* 相等性操作符：`==、!=`（`eq、ne`）

条件操作符：

* `if-then`：`(if) ? (then)`
* `if-then-else`：`(if) ? (then) : (else)`
* 默认值：`(value) ?: (defaultvalue)`

特殊的标识：

* 无操作：`_`

以上这些操作符都可以组合或是嵌套使用：

```html
'User is of type ' + (${user.isAdmin()} ? 'Administrator' : (${user.type} ?: 'Unknown'))
```

## 4.1 消息

我们已经知道了，`#{}` 消息表达式可以这样使用：

```html
<p th:utext="#{home.welcome}">Welcome to our grocery store!</p>
```

本地化文本如下：

```properties
home.welcome=¡Bienvenido a nuestra tienda de comestibles!
```

但是，有个问题我们还没有考虑到：如果信息不是静态的该怎么办？例如，我们可以知道某个时刻访问网站的用户是谁，并且想用它的名字来问候他，如下所求：

```html
<p>¡Bienvenido a nuestra tienda de comestibles, John Apricot!</p>
```

这就意味着我们需要在消息中添加变量：

```properties
home.welcome=¡Bienvenido a nuestra tienda de comestibles, {0}!
```

通过 `java.text.MessageFormat` 标准语法指定了参数，这就意味着你可以使用 `java.text.*` 包下的类，来引入一个 `number` 类型的参数，或是一个 `date` 类型的参数

为了给参数指定值，需要在 `HTTP session` 中指定一个名为 `user` 的属性，可以这样做：

```html
<p th:utext="#{home.welcome(${session.user.name})}">
  Welcome to our grocery store, Sebastian Pepper!
</p>
```

> ​	注意：这里 `th:utext` 的使用意味着格式化的信息将不会被转义。示例中假设 `user.name` 已经转义过了

多个参数之间，使用 **逗号** 分隔

消息键的值也可以是变量：

```html
<p th:utext="#{${welcomeMsgKey}(${session.user.name})}">
  Welcome to our grocery store, Sebastian Pepper!
</p>
```

## 4.2 变量

你是否已经注意到：事实上，`${}` 表达式实际上是包含在上下文中的变量 `Map` ，使用 `OGNL` 表达式执行的结果

> 在使用了 `Spring MVC` 的应用程序中，`OGNL` 将被替换为 `Spring EL`，但是，它们俩个的语法是非常的相似（实际上，大多数常见的案例是出奇的一致）

通过 `OGNL` 语法可知，下面代码中的表达式：

```html
<p>Today is: <span th:text="${today}">13 february 2011</span>.</p>
```

实际等价于：

```java
ctx.getVariable("today");
```

但是，`OGNL` 允许我们创建更为强大的表达式：

```html
<p th:utext="#{home.welcome(${session.user.name})}">
  Welcome to our grocery store, Sebastian Pepper!
</p>
```

实际上是通过执行下面的语句获得变量的值：

```java
((User) ctx.getVariable("session").get("user")).getName();
```

`getter` 方法只是 `OGNL` 语法的一部分：

```java
/*
 * Access to properties using the point (.). Equivalent to calling property getters.
 */
${person.father.name}

/*
 * Access to properties can also be made by using brackets ([]) and writing 
 * the name of the property as a variable or between single quotes.
 */
${person['father']['name']}

/*
 * If the object is a map, both dot and bracket syntax will be equivalent to 
 * executing a call on its get(...) method.
 */
${countriesByCode.ES}
${personsByName['Stephen Zucchini'].age}

/*
 * Indexed access to arrays or collections is also performed with brackets, 
 * writing the index without quotes.
 */
${personsArray[0].name}

/*
 * Methods can be called, even with arguments.
 */
${person.createCompleteName()}
${person.createCompleteNameWithSeparator('-')}
```

### 基本对象表达式

当基于上下文变量计算 `OGNL` 表达式时，表达式可以使用某些内置的对象，这样会让表达式更加灵活。这些内置的对象会被每一个 `OGNL` 标准所引用，使用 `#` 语法就可以：

* `#ctx`：上下文对象
* `#vars`：变量上下文
* `#local`：本地化上下文
* `#request`：（只存在于 `web` 上下文中）`HttpServletRqeust` 对象
* `#response`：（只存在于 `web` 上下文中）`HttpServletResponse` 对象
* `#session`：（只存在于 `web` 上下文中）`HttpSession` 对象
* `#ServletContext`：（只存在于 `web` 上下文中）`ServletContext` 对象

利于这些对象，就可以这样写代码了：

```html
Established locale country: <span th:text="${#locale.country}">US</span>.
```

详情参见 [附录A]()

### 表达式实用程序集对象

除了上面说的基本对象外，`Thymeleaf` 还给我们提供了一系列的实用工具集对象，用于帮助我们在表达式中执行一些常用的任务

- `#execInfo`: 正在处理的模板信息
- `#messages`: 在变量表达式中，获取外部化消息的方法，同样，可以通过 `#{}` 语法获取
- `#uris`: 用于转义 `URLs/URIs` 内容的方法
- `#conversions`: 用于执行配置约定服务（如果有的话）的方法
- `#dates`: 用于 `java.util.Date` 对象的方法：格式化，成分提取等
- `#calendars`: 类似于 `#dates`，但是对应的是 `java.util.Calendar` 对象
- `#numbers`: 用于格式化数字对象的方法
- `#strings`: 用于 `String` 对象的方法：包含，以...开头，预附加/追加等
- `#objects`: 用于一般 `Object` 的方法
- `#bools`: 用于布尔计算的方法
- `#arrays`: 用于数据的方法
- `#lists`: 用于列表的方法
- `#sets`: 用于集合的方法
- `#maps`: 用于 `Map` 的方法
- `#aggregates`: 在数组或集合上创建聚合的方法
- `#ids`: 用于处理可能重复出现的 `id` 属性（例如：迭代的结果中）

详情请参见 [附录B]()

### 在 home 页面对日期进行重新格式化



















