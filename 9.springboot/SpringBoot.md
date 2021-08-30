将Spring和第三方库进行整合，创建可运行的、独立的、生产级的基于Spring的应用程序

为快速启动且最小配置的Spring应用设计

### 特性

1. 创建独立的Spring应用
2. 内嵌Tomcat、Jetty、Undertow等Web容器，不需要部署War文件
3. 提供Starter依赖管理
4. 条件满足时自动装配Spring或第三方类库
5. 提供Production-ready特性，如指标信息Metrics、健康检查及外部化配置
6. 绝无代码生成，不需要XML配置

3、6主要通过Maven和Spring Framework的方式实现，因此SpringBoot的主要特性可总结为以下五点：

1. SpringApplication
2. 内嵌Web容器
3. 自动装配
4. 外部化配置
5. Actuator



### 独立的Spring应用

spring-boot-maven-plugin，可执行jar

* BOOT-INF
    * classes：项目的类文件和资源文件
    * lib：第三方jar包
* META-INF：应用相关的原信息，如MANIFEST.MF
* org.springframework.boot.loader：启动类，加载BOOT-INF
    * ExecutableArchiveLauncher
    * JarLauncher：可执行Jar
    * WarLanucher：可执行War

通过URLStreamHandler自定义实现Jar Handler

maven-war-plugin 3.x之后不必须web.xml

### Starter

spring-boot-starter-parent ----> parent is ---->   spring-boot-dependencies

包含许多使项目快速启动和运行所需的依赖项

命名规范

* 官方：spring-boot-starter-*  
* 第三方:*-spring-boot-starter

包里没有代码  只管理依赖

功能启用和依赖管理

### 嵌入式Web容器

Servlet

* Tomcat
* Jetty
* Undertow

Reactive

* Netty Web Server：通过Reactor+Netty
* Servlet3.1+异步

spring-boot-starter-web和spring-boot-starter-webflux同时存在时，webflux会被忽略



### 自动装配

基于类路径Jar包自动装配

@EnableAutoConfiguration

@SpringBootApplication

META-INF/spring.factories

> org.springframework.boot.autoconfig.EnableAutoConfiguration=\
>
> org.springframework.boot.autoconfig.aop.AopAutoConfiguration



### Production-Ready

外部化配置

Actuator



### 通用约定

1. 注解扫描的包目录为启动类所在的包路径

2. 配置文件约定为classpath下的application.yml或application.properties

3. web开发的文件放在classpath，访问的顺序依次是

   >/META-INF/resources-->resources-->static-->public

4. web开发中页面模板，约定放在classpath目录的templates目录下



