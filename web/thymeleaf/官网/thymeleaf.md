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

