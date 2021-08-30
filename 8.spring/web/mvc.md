基于Servlet API

基于Front Controller模式设计，DispatcherServlet提供了用于请求处理的共享算法，而请求映射、视图解析、异常处理等实际工作由可配置的委托组件执行

<img src="../.image/image-20210825155537374.png" alt="image-20210825155537374" style="zoom:50%;" />

### DispatcherServlet

注册

* web.xml
* WebApplicationInitializer
    * ServletContainerInitializer SPI 加载SpringServletContainerInitializer，用来处理WebApplicationInitializer
    * AbstractAnnotationConfigDispatcherServletInitializer



依赖：默认使用DispatcherServlet.properties中声明的依赖

* HandlerMapping：将请求映射到Handler
    * RequestMappingHandlerMapping
    * SimpleUrlHandlerMapping
* HandlerAdapter：帮助DispatcherServlet调用Handler
* HandlerExceptionResolver：Exception处理策略，如映射到Handler或HTML错误页面
* ViewResolver：将Handler返回的String解析为视图
* ThemeResolver
* MultipartResolver
* LocaleResolver，LocaleContextResolver
* FlashMapManager

请求处理流程

* 关联的WebApplicationContext通过DispatcherServlet.WEB_APPLICATION_CONTEXT_ATTRIBUTE放入Request Attribute
* 关联的LocaleResolver通过DispatcherServlet.LOCALE_RESOLVER_ATTRIBUTE放入Request Attribute
* 关联的ThemeResolver通过DispatcherServlet.THEME_RESOLVER_ATTRIBUTE放入Request Attribute
* 如果配置了MultipartResolver，并且请求中有Multipart，请求被处理为MultipartHttpServletRequest、
* 找到一个合适的Handler处理请求
* 视图渲染

路径匹配

* 基于去除contextPath和servletMapping前缀的路径寻找Handler

拦截

* HandlerInterceptor

异常

* ExceptionHandlerResolver
* 如果Handler抛出异常，被放入ExceptionHandlerResolver，返回
    * ModelAndView指向错误页面
    * 空ModelAndView
    * null如果无法处理，交给以一个ExceptionHandlerResolver处理

视图解析

* ViewResolver
* 针对JSP场景，需要配置InternalResourceViewResolver

