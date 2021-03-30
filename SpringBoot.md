## 微服务阶段

javase:OOP

mysql:持久化

html+css+js+jquery+框架：视图，框架不熟练，css不好；

Javaweb:独立开发MVC三层架构的网站了：原始

ssm:框架：简化了我们的开发流程，配置也开始复杂

**=============以上打war包，在tomcat中运行===============**

spring再简化：springboot-jar:内嵌tomcat，微服务架构！

服务越来越多：springcloud;

## 1.需要学习的东西

**springboot**

- springboot是什么
- 配置如何编写（.yaml）
- 自动装配原理（重要）
- 集成web开发：业务的核心
- 集成数据库Druid
- 分布式开发：Dubbo（RPC）+zookeeper平台
- swagger：接口文档
- 扩展
  - 任务调度，异步任务，邮件发送等
  - SpringSecurity：相似的还有shiro
- 中间插播Linux

**springcloud**

- 微服务
- springcloud入门
- Restful风格
- Eureka服务注册与发现
- Nginx:负载均衡
- HyStrix:容灾机制
- Zuul：路由网关
- Springcloud config : git

## 2. 简介

`什么是Spring`

Spring是一个开源框架，2003年兴起的一个轻量级的Java开发框架，作者： Rod Johnson

**Spring是为了解决企业级应用开发的复杂性而创建的，简化开发。**

`Spring是如何简化Java开发的`

为了降低Java开发的复杂性， Spring采用了以下4种关键策略：

 1、基于POJO的轻量级和最小侵入性编程；

 2、通过1OC，依赖注入（D1)和面向接口实现耦合；

 3、基于切面（AOP）和惯例进行声明式编程；

 4、通过切面和模版减少样式代码。

`什么是Springboot`

​		学过 javaweb的同学就知道，开发一个web应用，从最初开始接触 Servlet结合 Tomcat，跑出一个Hello World程序，是要经历特別多的步骤；后来就用了框架 Struts，再后来是 SpringMVC，到了现在的 Springboot，过一两年又会有其他web框架出现；不知道你们有没经历过框架不断的演进，然后自己开发项目所有的技术也再不断的变化、改造，反正我是都经历过了，哈哈。言归正传，什么是Spring Boot呢，就是一个 javaweb的开发框架，和 SpringMVC类似，对比其他 javaweb框架的好处，官方说是简化开发，约定大于配置，you can' just run，能迅速的开发web应用，几行代码开发一个http接口。

​		所有的技术框架的发展似乎都道循了一条主线规律：从一个复杂应用场景衍生一种规范框架，人们只需要进行各种配置而不需要自己去实现它，这时候强大的配置功能成了优点；发展到一定程度之后，人们根据实际生产应用情况，选取其中实用功能和设计精华，重构出一些轻量级的框架；之后为了提高开发效率，嫌弃原先的各类配置过于麻烦，于是开始提倡“约定大于配置”，进而行生出一些一站式的解决方案。

		是的这就是ava企业级应用->J2EE-> spring-> spring boot的过程。
​		随着 Spring不断的发展，涉及的领域越来越多，项目整合开发需要配合各种各样的文件，慢慢变得不那么易用简单，违背了最初的理念，甚至人称配置地狱。 Spring Boot正是在这样的一个背最下被抽象出来的开发框架，目的为了让大家更容易的使用 Spring、更容易的集成各种常用的中间件、开源软件；

​		Spring Boot基于 Spring开发， Spirng Boot本身并不提供 Spring框架的核心特性以及扩展功能，只是用于快速、敏捷地开发新一代基于 Spring框架的应用程序。也就是说，它并不是用来替代Spring的解決方案，而是和 Spring框架紧密结合用于提升Spring开发者体验的工具。 SpringBoot以**约定大于配置的核心思想**，默认帮我们进行了很多设置，多数 Spring Boot应用只需要很少的Spring 配置。同时它集成了大量常用的第三方库配置（例如 Redis、 Mongodb、Jpa、RabbitMQ、 Quartz等等）， Spring Boot应用中这些第三方库几乎可以零配置的开箱即用。

**SpringBoot优点**

- 为所有Spring开发者更快的入门
- **开箱即用**，提供各种默认配置来简化项目配置
- 内嵌式容器简化web项目
- 没有冗余代码生成和XML配置的要求

`什么是微服务`

论文：https://martinfowler.com/articles/microservices.html#ComponentizationViaServices

### 3.第一个SpringBoot环境

- jdk1.8
- maven 3.6.1
- springboot:最新版
- IDEA

官方：提供了一个快速生成的网站，IDEA

- 官网创建，idea导入
- idea直接创建











