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

# 4. 标准表达式语法

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

学习了上面的工具集对象，我们就可以使用它们来改变 `home` 页面中日期的显示方式了。在 `HomeController` 中这样设置变量：

```java
SimpleDateFormat dateFormat = new SimpleDateFormat("dd MMMM yyyy");
Calendar cal = Calendar.getInstance();

WebContext ctx = new WebContext(request, servletContext, request.getLocale());
ctx.setVariable("today", dateFormat.format(cal.getTime()));

templateEngine.process("home", ctx, response.getWriter());
```

或者，也可以这样：

```java
WebContext ctx = 
    new WebContext(request, response, servletContext, request.getLocale());
ctx.setVariable("today", Calendar.getInstance());

templateEngine.process("home", ctx, response.getWriter());
```

然后，在视图层这样做日期的格式化：

```html
<p>
  Today is: <span th:text="${#calendars.format(today,'dd MMMM yyyy')}">13 May 2011</span>
</p>
```

## 4.3 选择表达式（*语法）

变量表达式不仅仅可以写成：`${}`，还可以写成：`*{}`

但是有一个重要的区别：星号语法是在选定的对象上计算表达式，而不是在整个上下文中。也就是说，只要没有选定对象，`$` 和 `*` 语法的作用完全相同

那么，什么是选定对象呢？选定对象就是 **使用 `th:object` 属性得到的表达式结果**。在 `userprofile.html` 页面中：

```html
<div th:object="${session.user}">
  <p>Name: <span th:text="*{firstName}">Sebastian</span>.</p>
  <p>Surname: <span th:text="*{lastName}">Pepper</span>.</p>
  <p>Nationality: <span th:text="*{nationality}">Saturn</span>.</p>
</div>
```

上面的代码等价于：

```html
<div>
  <p>Name: <span th:text="${session.user.firstName}">Sebastian</span>.</p>
  <p>Surname: <span th:text="${session.user.lastName}">Pepper</span>.</p>
  <p>Nationality: <span th:text="${session.user.nationality}">Saturn</span>.</p>
</div>
```

当然，`$` 语法和 `*` 语法可以混合使用：

```html
<div th:object="${session.user}">
  <p>Name: <span th:text="*{firstName}">Sebastian</span>.</p>
  <p>Surname: <span th:text="${session.user.lastName}">Pepper</span>.</p>
  <p>Nationality: <span th:text="*{nationality}">Saturn</span>.</p>
</div>
```

在使用选定对象时，在 `$` 表达式中，选定对象可以用 `#object` 这个表达式替代：

```html
<div th:object="${session.user}">
  <p>Name: <span th:text="${#object.firstName}">Sebastian</span>.</p>
  <p>Surname: <span th:text="${session.user.lastName}">Pepper</span>.</p>
  <p>Nationality: <span th:text="*{nationality}">Saturn</span>.</p>
</div>
```

正如之前据说，如果没有选定对象，`$` 语法和 `*` 语法是等价的：

```html
<div>
  <p>Name: <span th:text="*{session.user.name}">Sebastian</span>.</p>
  <p>Surname: <span th:text="*{session.user.surname}">Pepper</span>.</p>
  <p>Nationality: <span th:text="*{session.user.nationality}">Saturn</span>.</p>
</div>
```

## 4.4 超链接/URL

由于重要性，`url` 是 `web` 应用程序模板中的一等公民，`Thymeleaf` 标准方言对它们有特殊的语法，即 `@` 语法：`@{…}`

有不同的 `URL` 类型：

* 绝对地址：`http://www.thymeleaf.org`
* 相对地址：
  * 相对于页面：`user/login.html`
  * 相对于上下文：`/itemdetails?id=3`（服务端的上下文名称将会自动添加）
  * 相对于服务：`~/billing/processInvoice`（在同一个服务中，也可以把这种称为另一种上下文（应用级））
  * 相对于协议：`//code.jquery.com/jquery-2.0.3.min.js`

这些 `URL` 的转换和表达式的处理，都是由实现了 `org.thymeleaf.linkbuilder.ILinkBuilder` 接口的类所输出的，该接口已经注册到了使用的 `ITemplateEngine` 对象上了

默认情况下，该接口的单个实现是在类 `org.thymeleaf.linkbuilder` 中注册的。`StandardLinkBuilder`，它对离线(非 `web`)和基于 `Servlet API` 的 `web` 场景都足够了。其他场景(比如与非 `servletapi web` 框架的集成)可能需要链接构建器接口的特定实现

现在，我们来使用新的语法——`th:href` 属性：

```html
<!-- Will produce 'http://localhost:8080/gtvg/order/details?orderId=3' (plus rewriting) -->
<a href="details.html" 
   th:href="@{http://localhost:8080/gtvg/order/details(orderId=${o.id})}">view</a>

<!-- Will produce '/gtvg/order/details?orderId=3' (plus rewriting) -->
<a href="details.html" th:href="@{/order/details(orderId=${o.id})}">view</a>

<!-- Will produce '/gtvg/order/3/details' (plus rewriting) -->
<a href="details.html" th:href="@{/order/{orderId}/details(orderId=${o.id})}">view</a>
```

注意事项如下：

* `th:href`是一个修饰符属性：它将会计算 `URL` 链接的值，并把它设置给 `a` 标签的 `href` 属性
* `URL` 参数中可以使用表达式（例如上例中的 `orderId=${o.id}`），所需的 `url` 参数的解码操作会自动执行
* 如果需要多个参数，请使用逗号分隔：`@{/order/process(execId=${execId},execType='FAST')}`
* 也允许变量模板在 `URL` 路径中出现：`@{/order/{orderId}/details(orderId=${orderId})}`
* 相对路径的 `URL` 以 `/` 开头（如：`/order/details`），在地址的最前面会自动加上应用的上下文名称
* 如果没有启用 `cookie`，或者 `cookie` 的启用状态未知，就可以把 `;jsessionid=...` 添加到相对路径的后面，这样的话，`session` 就会被保留了。这种操作被叫做 `URL` 重写，`Thymeleaf` 允许通过使用 `Servlet API` 的 `response.encodeURL(...)` 机制，为每个 `URL` 进行重写，这是一种自主的重写
* 在模板中，也可以有静态的 `href` 原生属性和`th:href` 属性共存（可选），这样，当直接打开页面作为原型设计时，这些链接仍然可以发挥导航的作用

和消息语法（`#{}`）一样，`URL` 也可以是另外一个表达式的结果：

```html
<a th:href="@{${url}(orderId=${o.id})}">view</a>
<a th:href="@{'/details/'+${user.login}(orderId=${o.id})}">view</a>
```

### home 页面的菜单

既然我们知道了如何创建链接 `url`，那么在主页中为站点中的其他一些页面添加一个小菜单怎么样?

```html
<p>Please select an option</p>
<ol>
  <li><a href="product/list.html" th:href="@{/product/list}">Product List</a></li>
  <li><a href="order/list.html" th:href="@{/order/list}">Order List</a></li>
  <li><a href="subscribe.html" th:href="@{/subscribe}">Subscribe to our Newsletter</a></li>
  <li><a href="userprofile.html" th:href="@{/userprofile}">See User Profile</a></li>
</ol>
```

### 相对于服务端根目录的 URL

可以使用附加语法创建相对于服务器根路径（而不是相对于上下文根路径）的 `url`，以便链接到同一服务器中的不同上下文。这些 `url` 将被指定为 `@{~/path/to/something}`

## 4.5 片断

片段表达式是表示标记的片段，并在模板中移动它们的一种简单方法。这允许我们复制它们，将它们作为参数传递给其他模板，等等

最常见的用法是使用 `th:insert` 或 `th:replace` 来插入片段：

```html
<div th:insert="~{commons :: main}">...</div>
```

它们可以在任何地方使用，就像变量一样：

```html
<div th:with="frag=~{footer :: #main/text()}">
  <p th:insert="${frag}">
</div>
```

在本教程的后面有一个完整的章节专门介绍模板布局，包括片段表达式的更深入解释

## 4.6 字面值

### 文本字面值

文本字面量指的是在单引号之间的字符串。它们可以包含任何字符，但是应该使用 `\'` 转义单引号

```html
<p>
  Now you are looking at a <span th:text="'working web application'">template file</span>.
</p>
```

### 数字字面值

就是数字

```html
<p>The year is <span th:text="2013">1492</span>.</p>
<p>In two years, it will be <span th:text="2013 + 2">1494</span>.</p>
```

### 布尔字面值

有两个值：`true`、`false`

```html
<div th:if="${user.isAdmin()} == false"> ...
```

在这个例子中，`== false` 被写在大括号外，因此 `Thymeleaf` 负责处理它。如果它被写在大括号里，它将是`OGNL/SpringEL` 引擎的责任：

```html
<div th:if="${user.isAdmin() == false}"> ...
```

### null 字面值

```html
<div th:if="${variable.something} == null"> ...
```

### 字面值标记

数值型、布尔型和空型字面值实际上是字面值标记的一种特殊情况。  

这些标记允许在标准表达式中进行一些简化。它们的工作原理与文本文字（`'…'`）完全相同，但它们只允许字母（`A-Z` 和 `A-Z`）、数字（`0-9`）、括号（`[` 和 `]`）、点（`.`）、连字符（`-`）和下划线（`_`），没有空格，没有逗号，等等。  

标记不需要任何引号包围它们。所以我们可以这样做：

```html
<div th:class="content">...</div>
```

而不是底下这种：

```html
<div th:class="'content'">...</div>
```

## 4.7 文本连接

文本，无论它们是文字，还是对变量或消息表达式求值的结果，都可以使用 `+` 操作符轻松连接：

```html
<span th:text="'The name of the user is ' + ${user.name}">
```

## 4.8 文本替换

文字替换允许对包含变量值的字符串进行简单格式化，而不需要对文本使用：`'…' + '...'.` 这样的操作

文本替换必须用竖线 `|` 包围，如：

```html
<span th:text="|Welcome to our application, ${user.name}!|">
```

等价于：

```html
<span th:text="'Welcome to our application, ' + ${user.name} + '!'">
```

文本替换可以结合其它类型的表达式一起使用：

```html
<span th:text="${onevar} + ' ' + |${twovar}, ${threevar}|">
```

> 只有变量和消息表达式(`${…},{…}， #{…}`) 被允许在 `|…|` 里进行文字替换。其他字面值(`'…'`)、布尔/数字标记、条件表达式等都不能。

## 4.9 算术运算符

`+、-、*、/、%` 这些算术运算符都可以使用：

```html
<div th:with="isEven=(${prodStat.count} % 2 == 0)">
```

注意，这些操作符也可以应用于 `OGNL` 变量表达式本身（在这种情况下，将由 `OGNL` 执行，而不是 `Thymeleaf` 标准表达式引擎）:

```html
<div th:with="isEven=${prodStat.count % 2 == 0}">
```

注意：一些操作符存在别名 `div(/)、mod(%)`

## 4.10 比较运算符

表达式中的值可以使用 `>、<、>=、<=` 符号进行比较，而 `==` 和 `!=` 操作符可以用于检查是否相等(或是否不等)。注意，`XML`规定 `<` 和 `>` 符号不应该在属性值中使用，因此应该使用转义字符：`&lt;、&gt;`

```html
<div th:if="${prodStat.count} &gt; 1">
<span th:text="'Execution mode is ' + ( (${execMode} == 'dev')? 'Development' : 'Production')">
```

这些都可以使用别名：`>`,`<`,`>=`,`<=`(`gt`,`lt`,`ge`,`le`)`==`, `!=` (`eq`, `ne`)

## 4.11 条件表达式

条件表达式的意思是只计算两个表达式中的一个，这取决于对一个条件求值的结果(它本身是另一个表达式)

让我们看一个示例片段(引入另一个属性修饰符 `th:class`):

```html
<tr th:class="${row.even}? 'even' : 'odd'">
  ...
</tr>
```

条件表达式的三个部分（`condition、then、else`）本身都是表达式，这意味着它们可以是变量(`${…}, *{...}`)， 消息 (`#{...}`)， `url (@{...}) `或文字(`…`)

```html
<tr th:class="${row.even}? (${row.first}? 'first' : 'even') : 'odd'">
  ...
</tr>
```

`else` 表达式也可以省略，在这种情况下，如果条件为 `false`，则返回空值

```html
<tr th:class="${row.even}? 'alt'">
  ...
</tr>
```

## 4.12 默认值表达式

默认表达式是一种特殊类型的条件值，没有 `then` 部分。它相当于某些语言(如 `Groovy`)中的 `Elvis` 运算符，允许指定两个表达式：如果第一个表达式的值不为 `null`，则使用第一个，如果为 `null`，则使用第二个

让我们在用户简介页面中看看它的实际用法：

```html
<div th:object="${session.user}">
  ...
  <p>Age: <span th:text="*{age}?: '(no age specified)'">27</span>.</p>
</div>
```

如你所见，默认值表达式的操作符是 `?:`，仅当计算 `*{age}` 的结果为 `null` 时，才使用默认值（在本例中是文字值）。因此，这等价于:

```html
<p>Age: <span th:text="*{age != null}? *{age} : '(no age specified)'">27</span>.</p>
```

和条件值一样，它们可以嵌套表达式

```html
<p>
  Name: 
  <span th:text="*{firstName}?: (*{admin}? 'Admin' : #{default.username})">Sebastian</span>
</p>
```

## 4.13 无操作标记

无操作标记由下划线（`_`）表示。  这个标记背后的想法是：指定一个表达式的期望结果是什么都不做，也就是说，就像可处理属性（例如：`th:text`）根本不存在那样做。  在其他可能性中，这允许开发人员使用原型文本作为默认值。例如，不需要这样：

```html
<span th:text="${user.name} ?: 'no user authenticated'">...</span>
```

我们可以直接使用 `no user authenticated`作为原型文本，从设计的角度来看，这将导致代码更加简洁和通用：

```html
<span th:text="${user.name} ?: _">no user authenticated</span>
```

## 4.14 数据的转换和格式化

`Thymeleaf` 为变量（`${…}`）和选择（`*{…}`）表达式定义了双括号语法，允许我们通过配置的转换服务应用数据转换

基本上是这样的：

```html
<td th:text="${{user.lastAccessDate}}">...</td>
```

注意到这里的双大括号了吗： `${{...}}`，这指示 `Thymeleaf` 将 `user.lastAccessDate` 表达式的结果传递给转换服务，并要求它在编写结果之前执行格式化操作(转换为 `String`)。

假设  `user.lastAccessDate` 是 `java.util.Calendar` 类型，如果转换服务（实现了 `IStandardConversionService` 接口）已经注册了，并且包含了从 `Calendar -> String` 的可用转换，那它就会被应用

`IStandardConversionService` （`StandardConversionService类`）的默认实现只是在任何转换为 `String` 的对象上执行 `. tostring()`。有关如何注册自定义转换服务实现的更多信息，请参阅配置的更多部分。

> 官方的 `Thymeleaf -spring3` 和 `Thymeleaf -spring4` 集成包透明地将 `Thymeleaf` 的转换服务机制与`Spring` 自己的转换服务基础设施集成在一起，这样在 `Spring` 配置中声明的转换服务和格式化器将自动提供给 `${{…}}` 和 `{{…}}` 表达式。

## 4.15 预处理

除了所有这些用于表达式处理的特性外，`Thymeleaf` 还具有预处理表达式的特性

预处理是在正常执行之前执行的表达式，允许对最终将被执行的表达式进行修改

预处理表达式与普通表达式完全一样，但是被双下划线包围（如 `__${expression}__`）

假设我们有一个 `i18n Messages_fr`。属性条目包含一个调用特定于语言的静态方法的 `OGNL` 表达式，如：

```properties
article.text=@myapp.translator.Translator@translateToFrench({0})
```

还有 `Messages_es.properties equivalent`：

```properties
article.text=@myapp.translator.Translator@translateToSpanish({0})
```

我们可以创建一个标记片段，根据区域设置计算一个表达式或另一个表达式。为此，我们将首先选择表达式(通过预处理)，然后让 `Thymeleaf` 执行它：

```html
<p th:text="${__#{article.text('textVar')}__}">Some text here...</p>
```

注意，对于法语语言环境，预处理步骤将创建以下等效内容：

```html
<p th:text="${@myapp.translator.Translator@translateToFrench(textVar)}">Some text here...</p>
```

预处理字符串 `__` 在属性中可以使用 `\_\_` 进行转义

# 5. 设置属性的值

本章将解释在标记中设置(或修改)属性值的方法

## 5.1 设置任意属性的值

假设我们的网站发布了一份时事通讯，我们希望用户能够订阅它，因此我们创建了一个带有表单的 `/WEB-INF/templates/subscribe.html` 模板：

```html
<form action="subscribe.html">
  <fieldset>
    <input type="text" name="email" />
    <input type="submit" value="Subscribe!" />
  </fieldset>
</form>
```

与 `Thymeleaf` 一样，这个模板一开始更像是一个静态原型，而不是 `web` 应用程序的模板。首先，表单中的 `action` 属性静态地链接到模板文件本身，因此没有地方可以重写有用的 `URL`。其次，提交按钮中的 `value` 属性使其显示英文文本，但我们希望将其国际化

于是，输入 `th:attr` 属性，以及更改设置它的标记的属性值的能力：

```html
<form action="subscribe.html" th:attr="action=@{/subscribe}">
  <fieldset>
    <input type="text" name="email" />
    <input type="submit" value="Subscribe!" th:attr="value=#{subscribe.submit}"/>
  </fieldset>
</form>
```

这个概念非常简单：`th:attr` 只是接受一个将值赋给属性的表达式。创建了相应的控制器和消息文件后，处理该文件的结果将是：

```html
<form action="/gtvg/subscribe">
  <fieldset>
    <input type="text" name="email" />
    <input type="submit" value="¡Suscríbe!"/>
  </fieldset>
</form>
```

除了新的属性值之外，还可以看到应用程序上下文名称已经自动添加到 `/gtvg/subscribe` 中 `URL` 的值中，如前一章所述

但是，如果我们想一次设置多个属性怎么办？`XML` 规则不允许在一个标签中设置一个属性两次，所以 `th:attr` 将接受一个逗号分隔的赋值列表，例如：

```html
<img src="../../images/gtvglogo.png" 
     th:attr="src=@{/images/gtvglogo.png},title=#{logo},alt=#{logo}" />
```

上面的代码会输出：

```html
<img src="/gtgv/images/gtvglogo.png" title="Logo de Good Thymes" alt="Logo de Good Thymes" />
```

## 5.2 给指定的属性设置值

现在，你可能会这样想：

```html
<input type="submit" value="Subscribe!" th:attr="value=#{subscribe.submit}"/>
```

这是一段很难看的写法。在属性值中指定赋值可能非常实用，但这并不是创建模板的最优雅的方式

`Thymeleaf` 同意你的观点，这就是为什么 `th:attr` 很少在模板中使用。通常，将使用其他 `th:*` 属性，其任务是设置特定的标签属性（而不是像 `th:attr` 这样的任何属性）

例如，要设置 `value` 属性，使用 `th:value`：

```html
<input type="submit" value="Subscribe!" th:value="#{subscribe.submit}"/>
```

这个看起来好多了！让我们尝试对 `form` 标签中的 `action` 属性做同样的操作：

```html
<form action="subscribe.html" th:action="@{/subscribe}">
```

还记得我们之前在 `home.html` 中添加的 `th:href` 吗？它们完全是同一种属性：

```html
<li><a href="product/list.html" th:href="@{/product/list}">Product List</a></li>
```

有很多类似的属性，每一个都针对一个特定的 `HTML5` 属性：

| 列一                    | 列二                  | 列三                |
| ----------------------- | --------------------- | ------------------- |
| `th:abbr`               | `th:accept`           | `th:accept-charset` |
| `th:accesskey`          | `th:action`           | `th:align`          |
| `th:alt`                | `th:archive`          | `th:audio`          |
| `th:autocomplete`       | `th:axis`             | `th:background`     |
| `th:bgcolor`            | `th:border`           | `th:cellpadding`    |
| `th:cellspacing`        | `th:challenge`        | `th:charset`        |
| `th:cite`               | `th:class`            | `th:classid`        |
| `th:codebase`           | `th:codetype`         | `th:cols`           |
| `th:colspan`            | `th:compact`          | `th:content`        |
| `th:contenteditable`    | `th:contextmenu`      | `th:data`           |
| `th:datetime`           | `th:dir`              | `th:draggable`      |
| `th:dropzone`           | `th:enctype`          | `th:for`            |
| `th:form`               | `th:formaction`       | `th:formenctype`    |
| `th:formmethod`         | `th:formtarget`       | `th:fragment`       |
| `th:frame`              | `th:frameborder`      | `th:headers`        |
| `th:height`             | `th:high`             | `th:href`           |
| `th:hreflang`           | `th:hspace`           | `th:http-equiv`     |
| `th:icon`               | `th:id`               | `th:inline`         |
| `th:keytype`            | `th:kind`             | `th:label`          |
| `th:lang`               | `th:list`             | `th:longdesc`       |
| `th:low`                | `th:manifest`         | `th:marginheight`   |
| `th:marginwidth`        | `th:max`              | `th:maxlength`      |
| `th:media`              | `th:method`           | `th:min`            |
| `th:name`               | `th:onabort`          | `th:onafterprint`   |
| `th:onbeforeprint`      | `th:onbeforeunload`   | `th:onblur`         |
| `th:oncanplay`          | `th:oncanplaythrough` | `th:onchange`       |
| `th:onclick`            | `th:oncontextmenu`    | `th:ondblclick`     |
| `th:ondrag`             | `th:ondragend`        | `th:ondragenter`    |
| `th:ondragleave`        | `th:ondragover`       | `th:ondragstart`    |
| `th:ondrop`             | `th:ondurationchange` | `th:onemptied`      |
| `th:onended`            | `th:onerror`          | `th:onfocus`        |
| `th:onformchange`       | `th:onforminput`      | `th:onhashchange`   |
| `th:oninput`            | `th:oninvalid`        | `th:onkeydown`      |
| `th:onkeypress`         | `th:onkeyup`          | `th:onload`         |
| `th:onloadeddata`       | `th:onloadedmetadata` | `th:onloadstart`    |
| `th:onmessage`          | `th:onmousedown`      | `th:onmousemove`    |
| `th:onmouseout`         | `th:onmouseover`      | `th:onmouseup`      |
| `th:onmousewheel`       | `th:onoffline`        | `th:ononline`       |
| `th:onpause`            | `th:onplay`           | `th:onplaying`      |
| `th:onpopstate`         | `th:onprogress`       | `th:onratechange`   |
| `th:onreadystatechange` | `th:onredo`           | `th:onreset`        |
| `th:onresize`           | `th:onscroll`         | `th:onseeked`       |
| `th:onseeking`          | `th:onselect`         | `th:onshow`         |
| `th:onstalled`          | `th:onstorage`        | `th:onsubmit`       |
| `th:onsuspend`          | `th:ontimeupdate`     | `th:onundo`         |
| `th:onunload`           | `th:onvolumechange`   | `th:onwaiting`      |
| `th:optimum`            | `th:pattern`          | `th:placeholder`    |
| `th:poster`             | `th:preload`          | `th:radiogroup`     |
| `th:rel`                | `th:rev`              | `th:rows`           |
| `th:rowspan`            | `th:rules`            | `th:sandbox`        |
| `th:scheme`             | `th:scope`            | `th:scrolling`      |
| `th:size`               | `th:sizes`            | `th:span`           |
| `th:spellcheck`         | `th:src`              | `th:srclang`        |
| `th:standby`            | `th:start`            | `th:step`           |
| `th:style`              | `th:summary`          | `th:tabindex`       |
| `th:target`             | `th:title`            | `th:type`           |
| `th:usemap`             | `th:value`            | `th:valuetype`      |
| `th:vspace`             | `th:width`            | `th:wrap`           |
| `th:xmlbase`            | `th:xmllang`          | `th:xmlspace`       |

## 5.3 一次设置多个值

有两个非常特殊的属性：`th:alt-title` 和 `th:lang-xmllang`，可以用于同时将两个属性设置为相同的值。具体是这样的：

* `th:alt-title`：同时设置 `alt、title` 属性
* `th:lang-xmllang`：同时设置 `lang、xmllang` 属性

对于我们的 `GTVG` 主页，这将允许我们替换以下内容：

```html
<img src="../../images/gtvglogo.png" 
     th:attr="src=@{/images/gtvglogo.png},title=#{logo},alt=#{logo}" />
```

替换为这样：

```html
<img src="../../images/gtvglogo.png" 
     th:src="@{/images/gtvglogo.png}" th:title="#{logo}" th:alt="#{logo}" />
```

或者这样：

```html
<img src="../../images/gtvglogo.png" 
     th:src="@{/images/gtvglogo.png}" th:alt-title="#{logo}" />
```

## 5.4 后缀或前缀

`Thymeleaf` 还提供了 `th:attrappend` 和 `th:attrprepend` 属性，它们将计算结果 `append`（后缀）或 `prepend`（前缀）到现有属性值。  例如，你可能想要在一个上下文变量中存储要添加（不是设置，只是添加）到一个按钮的 `CSS` 类的名称，因为要使用的特定 `CSS` 类将依赖于用户以前所做的一些事情：

```html
<input type="button" value="Do it!" class="btn" th:attrappend="class=${' ' + cssStyle}" />
```

如果你把 `cssStyle` 变量设置为 `warning` 来处理这个模板，将会得到：

```html
<input type="button" value="Do it!" class="btn warning" />
```

在标准方言中还有两个特定的附加属性：`th:classappend` 和 `th:styleappend` 属性，它们用于向元素添加 `CSS` 类或样式片段，而不覆盖现有的样式：

```html
<tr th:each="prod : ${prods}" class="row" th:classappend="${prodStat.odd}? 'odd'">
```

> `th:each` 是迭代属性，在后面有详细讲解

## 5.5 固定的布尔值属性

`HTML` 有布尔属性的概念，属性没有值，出现一个表示值是“真”。在 `XHTML` 中，这些属性只取 1 个值，即它本身

例如：`checked`

```html
<input type="checkbox" name="option2" checked /> <!-- HTML -->
<input type="checkbox" name="option1" checked="checked" /> <!-- XHTML -->
```

标准方言包含的属性允许你通过评估一个条件来设置这些属性，如果评估为 `true`，属性将被设置为它的固定值，如果评估为 `false`，属性将不会被设置：

```html
<input type="checkbox" name="active" th:checked="${user.active}" />
```

标准方言中存在以下固定的布尔值属性：

| 第一列              | 第二列         | 第三列          |
| ------------------- | -------------- | --------------- |
| `th:async`          | `th:autofocus` | `th:autoplay`   |
| `th:checked`        | `th:controls`  | `th:declare`    |
| `th:default`        | `th:defer`     | `th:disabled`   |
| `th:formnovalidate` | `th:hidden`    | `th:ismap`      |
| `th:loop`           | `th:multiple`  | `th:novalidate` |
| `th:nowrap`         | `th:open`      | `th:pubdate`    |
| `th:readonly`       | `th:required`  | `th:reversed`   |
| `th:scoped`         | `th:seamless`  | `th:selected`   |

## 5.6 将值设置给一个任意属性（默认属性处理器）

`Thymeleaf` 提供了一个默认属性处理器，允许我们设置任何属性的值，即使在标准方言中没有为它定义特定的`th:*` 处理器：

```html
<span th:whatever="${user.name}">...</span>
```

最终会生成：

```html
<span whatever="John Apricot">...</span>
```

## 5.7 支持 html5 友好的属性和元素名称

也可以使用完全不同的语法，以更友好的方式将处理程序应用到模板上：

```html
<table>
    <tr data-th-each="user : ${users}">
        <td data-th-text="${user.login}">...</td>
        <td data-th-text="${user.name}">...</td>
    </tr>
</table>
```

`data-{prefix}-{name}` 语法是 `HTML5` 中编写自定义属性的标准方法，而不要求开发人员使用任何命名空间名称，如 `th:*`。`Thymeleaf` 使此语法自动适用于所有方言(不仅仅是标准方言)

还有一种指定自定义标记的语法：`{prefix}-{name}`，它遵循 `W3C` 自定义元素规范(较大的 `W3C Web Components` 规范的一部分)。例如，这可以用于 `th:block` 元素(也可以是 `th-block`)，这将在后面的小节中解释

重要提示：**此语法是对名称空间的补充**

# 6. 迭代

到目前为止，我们已经创建了一个主页，一个用户简介页，还有一个让用户订阅我们时事通讯的页面……但是我们的产品呢？为此，我们需要一种方法来遍历集合中的项，以构建我们的产品页面

## 6.1 迭代入门

为了在 `/WEB-INF/templates/product/list.html` 页面中显示产品，我们将使用一个表格。每一个我们的产品将显示在一行(`< tr >` 元素),所以我们需要为我们的模板创建一个模板行——该模板行将举例说明我们希望每个产品该如何显示，然后指示 `Thymeleaf` 重复每个产品一次

标准方言为我们提供了一个属性：`th:each`

### 使用 th:each

对于我们的产品列表页面，我们需要一个控制器方法来从服务层检索产品列表，并将其添加到模板上下文：

```java
public void process(
        final HttpServletRequest request, final HttpServletResponse response,
        final ServletContext servletContext, final ITemplateEngine templateEngine)
        throws Exception {
    
    ProductService productService = new ProductService();
    List<Product> allProducts = productService.findAll(); 
    
    WebContext ctx = new WebContext(request, response, servletContext, request.getLocale());
    ctx.setVariable("prods", allProducts);
    
    templateEngine.process("product/list", ctx, response.getWriter());
    
}
```

然后我们将使用模板中的 `th:each` 来遍历产品列表：

```html
<!DOCTYPE html>

<html xmlns:th="http://www.thymeleaf.org">

  <head>
    <title>Good Thymes Virtual Grocery</title>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
    <link rel="stylesheet" type="text/css" media="all" 
          href="../../../css/gtvg.css" th:href="@{/css/gtvg.css}" />
  </head>

  <body>

    <h1>Product list</h1>
  
    <table>
      <tr>
        <th>NAME</th>
        <th>PRICE</th>
        <th>IN STOCK</th>
      </tr>
      <tr th:each="prod : ${prods}">
        <td th:text="${prod.name}">Onions</td>
        <td th:text="${prod.price}">2.41</td>
        <td th:text="${prod.inStock}? #{true} : #{false}">yes</td>
      </tr>
    </table>
  
    <p>
      <a href="../home.html" th:href="@{/}">Return to home</a>
    </p>

  </body>

</html>
```

`prod : ${prods}` 属性意味着：`${prods}` 结果中的每一个元素，都在模板的这个片断中重复，片断中把每个元素的值赋值给一个变量 `pord`

* 把 `${prods}` 叫做 **被迭代的表达式** 或者 **被迭代的变量**
* 把 `prod` 叫做 **迭代表达式** 或者 **迭代变量**

注意：`prod` 迭代变量的范围是 `<tr>` 元素内部，也就意味着对于它内部的 `<td>` 标签是可用的

### 可迭代的值

 `list` 类不是 `Thymeleaf` 中唯一可用于迭代的值。有一组相当完整的对象被认为是可由 `th:each` 属性迭代的：

* 任何实现 `java.util.Iterable` 的对象
* 任何实现 `java.util.Enumeration` 的对象
* 任何实现 `java.util` 的对象
* 迭代器，其值将在迭代器返回时使用，而不需要将所有值缓存到内存中
* 任何实现 `java.util.Map` 的对象
* 在迭代映射时，`iter` 变量将属于 `java.util.Map.Entry` 类
* 任何数组
* 任何都将被视为包含对象本身的单值列表的其他对象

## 6.2 保持迭代状态

当使用 `th:each` 时，`Thymeleaf` 提供了一种用于跟踪迭代状态的机制：状态变量

状态变量定义在 `th:` 每个属性中，包含以下数据：

* 当前迭代索引，从 0 开始。这就是 `index` 属性
* 当前迭代索引，从 1 开始。这是 `count` 属性
* 迭代变量中的元素总数。这就是 `size` 属性
* 每个迭代的iter变量。这是 `current` 属性
* 当前迭代是偶数还是奇数。这些是 `even/odd` 布尔性质
* 当前迭代是否是第一个迭代。这是 `first` 布尔属性
* 当前迭代是否为最后一个迭代。这是 `last` 布尔属性

```html
<table>
  <tr>
    <th>NAME</th>
    <th>PRICE</th>
    <th>IN STOCK</th>
  </tr>
  <tr th:each="prod,iterStat : ${prods}" th:class="${iterStat.odd}? 'odd'">
    <td th:text="${prod.name}">Onions</td>
    <td th:text="${prod.price}">2.41</td>
    <td th:text="${prod.inStock}? #{true} : #{false}">yes</td>
  </tr>
</table>
```

状态变量（在本例中是 `iterStat`）在 `th` 中定义：每个属性将其名称写在 `iter` 变量本身之后，用逗号分隔。就像 `iter` 变量一样，`status` 变量也被限定在包含 `th:each` 属性的标记所定义的代码片段中

让我们看一下处理模板的结果：

```html
<!DOCTYPE html>

<html>

  <head>
    <title>Good Thymes Virtual Grocery</title>
    <meta content="text/html; charset=UTF-8" http-equiv="Content-Type"/>
    <link rel="stylesheet" type="text/css" media="all" href="/gtvg/css/gtvg.css" />
  </head>

  <body>

    <h1>Product list</h1>
  
    <table>
      <tr>
        <th>NAME</th>
        <th>PRICE</th>
        <th>IN STOCK</th>
      </tr>
      <tr class="odd">
        <td>Fresh Sweet Basil</td>
        <td>4.99</td>
        <td>yes</td>
      </tr>
      <tr>
        <td>Italian Tomato</td>
        <td>1.25</td>
        <td>no</td>
      </tr>
      <tr class="odd">
        <td>Yellow Bell Pepper</td>
        <td>2.50</td>
        <td>yes</td>
      </tr>
      <tr>
        <td>Old Cheddar</td>
        <td>18.75</td>
        <td>yes</td>
      </tr>
    </table>
  
    <p>
      <a href="/gtvg/" shape="rect">Return to home</a>
    </p>

  </body>
  
</html>
```

请注意，我们的迭代状态变量工作得很好，只对奇数行建立奇数 `CSS` 类。  如果你没有明确设置一个状态变量，`Thymeleaf` 会通过添加 `Stat` 到迭代变量名来为你创建一个状态变量：

```html
<table>
  <tr>
    <th>NAME</th>
    <th>PRICE</th>
    <th>IN STOCK</th>
  </tr>
  <tr th:each="prod : ${prods}" th:class="${prodStat.odd}? 'odd'">
    <td th:text="${prod.name}">Onions</td>
    <td th:text="${prod.price}">2.41</td>
    <td th:text="${prod.inStock}? #{true} : #{false}">yes</td>
  </tr>
</table>
```

## 6.3 通过数据懒加载进行最优化

有时我们可能想要优化数据集合的检索（例如从数据库），以便这些集合只有在真正要使用时才被检索

> 实际上，这可以应用于任何数据块，但是考虑到内存集合可能具有的大小，检索要迭代的集合是该场景中最常见的情况

为了支持这一点，`Thymeleaf` 提供了一种延迟加载上下文变量的机制。实现 `ILazyContextVariable` 接口的上下文变量——很可能是通过扩展其 `LazyContextVariable` 默认实现——将在执行时被解析。例如：

```java
context.setVariable(
     "users",
     new LazyContextVariable<List<User>>() {
         @Override
         protected List<User> loadValue() {
             return databaseRepository.findAllUsers();
         }
     });
```

这个变量可以在不知道其惰性的情况下使用，例如：

```html
<ul>
  <li th:each="u : ${users}" th:text="${u.name}">user name</li>
</ul>
```

但与此同时，如果条件在如下代码中求值为 `false`，则永远不会被初始化（其 `loadValue()` 方法永远不会被调用）

```html
<ul th:if="${condition}">
  <li th:each="u : ${users}" th:text="${u.name}">user name</li>
</ul>
```

# 7. 条件判断

## 7.1 简单条件：if、unless

有时，需要模板的一个片段只出现在满足特定条件的结果中

例如，假设我们希望在产品表中显示一列，列中包含每个产品的评论数量，如果有评论，则显示到该产品评论详细信息页面的链接

为了做到这一点，我们将使用 `th:if` 属性：

```html
<table>
  <tr>
    <th>NAME</th>
    <th>PRICE</th>
    <th>IN STOCK</th>
    <th>COMMENTS</th>
  </tr>
  <tr th:each="prod : ${prods}" th:class="${prodStat.odd}? 'odd'">
    <td th:text="${prod.name}">Onions</td>
    <td th:text="${prod.price}">2.41</td>
    <td th:text="${prod.inStock}? #{true} : #{false}">yes</td>
    <td>
      <span th:text="${#lists.size(prod.comments)}">2</span> comment/s
      <a href="comments.html" 
         th:href="@{/product/comments(prodId=${prod.id})}" 
         th:if="${not #lists.isEmpty(prod.comments)}">view</a>
    </td>
  </tr>
</table>
```

这里有很多东西要看，所以让我们关注最重要的一行：

```html
<a href="comments.html"
   th:href="@{/product/comments(prodId=${prod.id})}" 
   th:if="${not #lists.isEmpty(prod.comments)}">view</a>
```

这将创建一个到评论页面的链接（带有`URL /product/comments`），其中 `prodId` 参数设置为产品的 `id`，但仅在产品有评论的情况下

让我们来看看生成的结果：

```html
<table>
  <tr>
    <th>NAME</th>
    <th>PRICE</th>
    <th>IN STOCK</th>
    <th>COMMENTS</th>
  </tr>
  <tr>
    <td>Fresh Sweet Basil</td>
    <td>4.99</td>
    <td>yes</td>
    <td>
      <span>0</span> comment/s
    </td>
  </tr>
  <tr class="odd">
    <td>Italian Tomato</td>
    <td>1.25</td>
    <td>no</td>
    <td>
      <span>2</span> comment/s
      <a href="/gtvg/product/comments?prodId=2">view</a>
    </td>
  </tr>
  <tr>
    <td>Yellow Bell Pepper</td>
    <td>2.50</td>
    <td>yes</td>
    <td>
      <span>0</span> comment/s
    </td>
  </tr>
  <tr class="odd">
    <td>Old Cheddar</td>
    <td>18.75</td>
    <td>yes</td>
    <td>
      <span>1</span> comment/s
      <a href="/gtvg/product/comments?prodId=4">view</a>
    </td>
  </tr>
</table>
```

完美！这正是我们想要的。  注意：`if` 属性不仅仅只会计算布尔条件。它的功能远不止于此，它将按照以下规则将指定的表达式计算为 `true` ：

* 如果 `value` 不为空
  * 如果 `value` 是一个布尔值且为真
  * 如果 `value` 是一个数字且非零
  * 如果 `value` 是一个字符且不为零
  * 如果 `value` 是一个字符串且不是 `false`，` off` 或 `no` 
  * 如果 value不是布尔值，则为数字、字符或字符串
* 如果 `value` 为 `null`，则 `th: If` 的值为 `false`

另外，`th:if` 有一个逆属性 `th:unless`，我们可以在前面的例子中使用它，而不是在 `OGNL` 表达式中使用 `not`：

```html
<a href="comments.html"
   th:href="@{/comments(prodId=${prod.id})}" 
   th:unless="${#lists.isEmpty(prod.comments)}">view</a>
```

## 7.2 switch 语句

还有一种方法可以有条件地显示内容，使用等价于 `Java` 中的 `switch` 结构： `th:switch / th:case` 属性集

```html
<div th:switch="${user.role}">
  <p th:case="'admin'">User is an administrator</p>
  <p th:case="#{roles.manager}">User is a manager</p>
</div>
```

 注意，一旦一个 `th:case` 属性被赋值为 `true`，同一 `switch` 上下文中其他的 `th:case` 属性就被赋值为 `false`

默认选项指定为 `th:case="*"`：

```html
<div th:switch="${user.role}">
  <p th:case="'admin'">User is an administrator</p>
  <p th:case="#{roles.manager}">User is a manager</p>
  <p th:case="*">User is some other thing</p>
</div>
```

# 8. 布局模板

## 8.1 包含模板片断

### 定义和引用片断

在我们的模板中，我们通常希望包含来自其他模板的部分，比如页脚、页眉、菜单……

为了做到这一点，`Thymeleaf` 需要我们定义这些部分，被叫做“片段”，用于包含，可以使用 `th:fragment`属性

假设我们想要向所有的杂货页面添加一个标准的版权页脚，因此我们创建了一个 `/WEB-INF/templates/footer.html` 文件，其中包含以下代码：

```html
<!DOCTYPE html>

<html xmlns:th="http://www.thymeleaf.org">

  <body>
  
    <div th:fragment="copy">
      &copy; 2011 The Good Thymes Virtual Grocery
    </div>
  
  </body>
  
</html>
```

上面的代码定义了一个名为 `copy` 的片段，我们可以很容易地使用 `th:insert` 或 `th:replace` 属性之一将其包含在我们的主页中（还有 `th:include`，但是自 `Thymeleaf 3.0` 以来不再推荐使用）：

```html
<body>

  ...

  <div th:insert="~{footer :: copy}"></div>
  
</body
```

注意：`th:insert` 需要一个片段表达式（`~{…}`)，这是一个引用片段的表达式。在上面的例子中，它是一个简单的片段表达式，(`~{，}`）封装是完全可选的，所以上面的代码等价于：

```html
<body>

  ...

  <div th:insert="footer :: copy"></div>
  
</body>
```

### 片断的特殊语法

 片段表达式的语法非常简单。有三种不同的格式：

* 包括在名为 `templatename` 的模板上应用指定的标记选择器所产生的片段。注意，选择器可以仅仅是一个片段名，所以你可以像上面的 `~{footer:: copy}` 那样简单地指定 `~{templatename::fragmentname}`

  > 标记选择器语法由底层的 `attparser` 解析库定义，类似于 `XPath` 表达式或 `CSS` 选择器。更多信息请参见附录 `C`

* `~{templatename}` 包含名为 `templatename` 的完整模板

  > 注意你在 `th:insert/th:replace` 标签中使用的模板名称必须是可以被模板引擎当前使用的模板解析器解析的

* 从同一个模板中插入一个片段，匹配选择器。如果在表达式出现的模板上没有找到，则将模板调用（插入）的堆栈遍历到最初处理的模板（根），直到选择器在某个级别上匹配为止

上面例子中的 `templatename` 和 `selector` 都可以是完全功能的表达式（甚至是条件表达式）

```html
<div th:insert="footer :: (${user.isAdmin}? #{footer.admin} : #{footer.normaluser})"></div>
```

再次注意周围的 `~{…}` 在 `th:insert/th:replace` 中是可选的

片段可以包含任何 `th:*` 属性。一旦片段被包含到目标模板中（具有 `th:insert/th:replace` 属性的片段），这些属性将被计算，它们将能够引用在目标模板中定义的任何上下文变量

> 这种处理片段的方法的一大优点是：可以在具有完整甚至有效的标记结构的页面中编写可以被浏览器完美显示的片段，同时仍然保留让 `Thymeleaf` 将它们包含到其他模板中的能力

### 不使用 th:fragment 的片断引用

多亏了标记选择器的强大功能，我们可以包含不使用任何 `th:fragment` 属性的片段。它甚至可以是来自完全不了解 `Thymeleaf` 的不同应用程序的标记代码：

```html
...
<div id="copy-section">
  &copy; 2011 The Good Thymes Virtual Grocery
</div>
...
```

我们可以通过引用它的 `id` 属性来简单的引用这个片断，以类似于 `CSS` 选择器的方式：

```html
<body>

  ...

  <div th:insert="~{footer :: #copy-section}"></div>
  
</body>
```

### th:insert 和 th:replace 及 th:include 之间的区别

`th:insert` 和 `th:replace`（和 `th:include`, 3.0以后不推荐）之间有什么区别?  

* `Th:insert` 是最简单的：它将简单地插入指定的片段作为其宿主标记的主体
* `th:replace` 实际上用指定的片段替换了它的宿主标记
* `Th:include` 类似于 `Th:insert`，但不是插入片段，它只插入片段的内容

看下面这样一个 `HTML` 片段：

```html
<footer th:fragment="copy">
  &copy; 2011 The Good Thymes Virtual Grocery
</footer>
```

在宿主标签 `<div>` 中包含三次：

```html
<body>

  ...

  <div th:insert="footer :: copy"></div>

  <div th:replace="footer :: copy"></div>

  <div th:include="footer :: copy"></div>
  
</body>
```

最终生成的内容是：

```html
<body>

  ...

  <div>
    <footer>
      &copy; 2011 The Good Thymes Virtual Grocery
    </footer>
  </div>

  <footer>
    &copy; 2011 The Good Thymes Virtual Grocery
  </footer>

  <div>
    &copy; 2011 The Good Thymes Virtual Grocery
  </div>
  
</body>
```

## 8.2 可参数化的片断签名

为了为模板片段创建一个更像函数的机制，用 `th:fragment` 定义的片段可以指定一组参数：

```html
<div th:fragment="frag (onevar,twovar)">
    <p th:text="${onevar} + ' - ' + ${twovar}">...</p>
</div>
```

这种写法需要使用 `th:insert` 或 `th:replace` 这两种语法中的一种来调用：

```html
<div th:replace="::frag (${value1},${value2})">...</div>
<div th:replace="::frag (onevar=${value1},twovar=${value2})">...</div>
```

注意，在最后一个写法中顺序并不重要：

```html
<div th:replace="::frag (twovar=${value2},onevar=${value1})">...</div>
```

### 无参片断中的局部变量

即使片段没有像这样定义参数：

```html
<div th:fragment="frag">
    ...
</div>
```

我们也可以使用上面指定的第二种语法来调用参数（只能使用第二种）：

```html
<div th:replace="::frag (onevar=${value1},twovar=${value2})">
```

这等价于 `th:replace` 和 `th:with` 的结合：

```html
<div th:replace="::frag" th:with="onevar=${value1},twovar=${value2}">
```

请注意，对于片段的局部变量的这种规范——无论它是否有参数签名——不会导致上下文在执行之前被清空。片段仍然能够访问调用模板中使用的每个上下文变量，就像它们当前一样

### th:assert 用于模板内断言

`assert` 属性可以指定一个逗号分隔的表达式列表，该表达式应该被求值，并为每次求值生成 `true`，否则将引发异常

```html
<div th:assert="${onevar},(${twovar} != 43)">...</div>
```

这对于在片段签名处验证参数非常方便：

```html
<header th:fragment="contentheader(title)" th:assert="${!#strings.isEmpty(title)}">...</header>
```

## 8.3 灵活的布局：不仅仅是片断插入

多亏了片段表达式，我们可以为片段指定参数，这些片段不是文本、数字、`bean` 对象，而是标记片段

这允许我们以一种方式创建片段，这样它们就可以被来自调用模板的标记所丰富，从而产生一个非常灵活的模板布局机制

注意下面片段中 `title` 和 `links` 变量的使用：

```html
<head th:fragment="common_header(title,links)">

  <title th:replace="${title}">The awesome application</title>

  <!-- Common styles and scripts -->
  <link rel="stylesheet" type="text/css" media="all" th:href="@{/css/awesomeapp.css}">
  <link rel="shortcut icon" th:href="@{/images/favicon.ico}">
  <script type="text/javascript" th:src="@{/sh/scripts/codebase.js}"></script>

  <!--/* Per-page placeholder for additional links */-->
  <th:block th:replace="${links}" />

</head>
```

现在，可以这样调用：

```html
...
<head th:replace="base :: common_header(~{::title},~{::link})">

  <title>Awesome - Main</title>

  <link rel="stylesheet" th:href="@{/css/bootstrap.min.css}">
  <link rel="stylesheet" th:href="@{/themes/smoothness/jquery-ui.css}">

</head>
...
```

结果将使用我们的调用模板中的实际 `<title>` 和 `<link>` 标记作为标题和链接变量的值，从而导致我们的片段在插入期间正在自定义： 

```html
...
<head>

  <title>Awesome - Main</title>

  <!-- Common styles and scripts -->
  <link rel="stylesheet" type="text/css" media="all" href="/awe/css/awesomeapp.css">
  <link rel="shortcut icon" href="/awe/images/favicon.ico">
  <script type="text/javascript" src="/awe/sh/scripts/codebase.js"></script>

  <link rel="stylesheet" href="/awe/css/bootstrap.min.css">
  <link rel="stylesheet" href="/awe/themes/smoothness/jquery-ui.css">

</head>
...
```

















