![Spring 核心特性](../.image/Spring 核心特性.png)

### 核心特性

spring-core、spring-beans、spring-context、spring-context-indexer

1. IoC：
3. i18n
4. Events
5. Resources
6. Validation
7. Data Binding
8. Type Conversion
9. Spring EL：spring-expression 
9. AOP：spring-aop，spring-aspects

### 测试

spring-test

* Mock Objects
* TextContext Framework
* SpringMVC Test
* WebTestClient

### 数据存储

1. JDBC：spring-jdbc、spring-r2dbc
2. 事务抽象：spring-tx
3. DAO支持
4. O/R Mapping：spring-orm
5. XML Marshalling：spring-oxm

### Web

* spring-web
* Servlet
    * MVC：spring-webmvc
    * WebSocket：spring-websocket
    * SockJS
* Reactive
    * WebFlux：spring-webflux
    * WebSocket：spring-websocket
    * WebClient

### 技术整合

1. 缓存抽象Caching、Java邮件客户端Email、本地调度Scheduling：spring-context-support

1. 远程调用Remoting
2. 本地任务Tasks
3. JMX
4. JCA
5. JMS：spring-jms
6. Logging：spring-jcl
7. javaagent：spring-instrument
8. 自定义消息处理：spring-message

### 简化Java开发

* 基于 POJO 的轻量级和最小侵入性编程

* 通过依赖注入和面向接口实现松耦合

* 基于切面和惯例进行声明式编程

* 通过切面和模板减少样板式代码

### BeanFactory和ApplicationContext

BeanFactory提供了先进的配置机制，能管理所有类型的对象

ApplicationContext除了提供IOC能力，还提供了更多特性，如AOO、Environment、i18n、Event、Resource

ApplicationContext注解驱动、事件驱动、模块驱动

BeanFactory不对配置格式或注解做限制，而是通过BeanDefinitionReader或BeanPostProcessor进行扩展

ApplicationContext既继承了BeanFactory，内部又组合了一个BeanFactory实例

BeanFactory Bean是延迟加载，ApplicationContext会将单例Bean提前初始化

BeanPostProcessor和BeanFactoryPostProcessor，BeanFactory需要手动注册，ApplicationContext则是自动注册





