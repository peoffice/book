##### 1.微服务架构概述
* 单体应用的问题
> 1. 复杂性高
> 2. 技术债务
> 3. 部署频率低
> 4. 可靠性差
> 5. 扩展能力受限
> 6. 阻碍技术创新
* 微服务
> 微服务架构风格是一种将一个单一应用程序开发为一组小型服务的方法，每个服务运行在自己的进程中，服务间通信采用轻量级通信机制（通常用HTTP资源API)
* 微服务架构优点
> 1. 易于开发和维护
> 2. 单个微服务启动较快
> 3. 技术栈不受限
> 4. 局部修改容易部署
> 5. 按需伸缩
* 微服务架构缺点
> 1. 运维要求较高
> 2. 分布式固有的复杂性
> 3. 接口调整成本高
> 4. 重复劳动
* 微服务的设计原则
> 1. 单一职责原则
> 2. 服务自治原则
> 3. 轻量级通信原则
> 4. 微服务粒度
* 推荐阅读
> 1. 《Domain Driven Design Quickly》
* 技术选型
> 1. 框架：Spring Cloud，Dubbo，Dropwizard，Armada
> 2. 运行平台：PC Server，阿里云，AWS云，Docker

##### 2.微服务开发框架——Spring Cloud
* 云原生：可以简单地理解为面向云环境的软件架构
> 1. 《Cloud Native Application》
> 2. 《十二要素应用宣言（12-factor Apps）》
* Spring Cloud特点
> 1. 约定优于配置
> 2. 适用于各种环境
> 3. 隐藏了组件的复杂性，并提供声明式、无xml的配置方式
> 4. 开箱即用，快速启动
> 5. 轻量级的组件
> 6. 组件丰富，功能齐全
> 7. 选型中立、丰富
> 8. 灵活

##### 3.开始使用Spring Cloud实战微服务
* 技术储备
> 1. 语言基础：Java
> 2. Spring Boot：轻量级微服务框架
> 3. 项目管理与构建工具：Maven或Gradle
* Spring Boot Actuator
> Spring Boot Actuator提供了很多监控端点。可使用http://{ip}:{port}/{endpoint}的形式访问这些端点

##### 4.微服务注册与发现
##### 5.使用Ribbon实现客户端负载均衡
##### 6.使用Feign实现声明式REST调用
##### 7.使用Hystrix实现微服务的容错处理
##### 8.使用Zuul构建微服务网关
##### 9.使用Spring Cloud Config统一管理微服务配置
##### 10.使用Spring Cloud Sleuth实现微服务跟踪
##### 11.使用Spring Cloud常见问题与总结
##### 12.Docker入门
##### 13.将微服务运行在Docker上
##### 14.使用Docker Compose编排微服务