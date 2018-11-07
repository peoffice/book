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
* 服务发现组件具备：
> 1. 服务注册表
> 2. 服务注册与服务发现
> 3. 服务检查
> 4. Eureka、Consul和Zookeeper
* Eureka
> 1. Eureka High Level Architecture 
> ![Eureka High Level Architecture](https://github.com/peoffice/book/blob/master/spring_cloud_docker_microservices_images/eureka_high_level.png)

##### 5.使用Ribbon实现客户端负载均衡
* Ribbon
> 1. Ribbon是Netflix发布的负载均衡器，它有助于控制HTTP和TCP客户端的行为。
> 2. 为Ribbon配置服务提供者地址列表之后，Ribbon就可以基于某种负载均衡算法，自动地帮助服务消费者去请求
> 3. 使用架构图
> ![使用架构图](https://github.com/peoffice/book/blob/master/spring_cloud_docker_microservices_images/ribbon_load_balance.png)

##### 6.使用Feign实现声明式REST调用
* Feign
> Feign是Netflix开发的声明式、模板化的HTTP客户端，其灵感来自Retrofit、JAXRS-2.0以及WebSocket等

##### 7.使用Hystrix实现微服务的容错处理
* 雪崩效应
> 我们通常把“基础服务故障”导致“级联故障”的现象称为雪崩效应，它描述的是提供者不可用导致消费者不可用，并将不可用逐渐放大的过程
* 如何容错
> 1. 为网络请求设置超时
> 2. 使用断路器模式
* Hystrix
> Hystrix是由Netflix开源的一个延迟和容错库，用于隔离访问远程系统、服务或者第三方库，防止级联失败，从而提升系统的可用性与容错性。Hystrix主要通过如下几点实现延迟和容错
>> 1.  包裹请求：使用HystrixCommand（或H也是听日先Observable Command）包裹对依赖的调用逻辑，每个命令在独立的线程中执行
>> 2. 跳闸机制：当某服务的错误率超过一定阈值时，Hystrix可以自动或者手动跳闸，停止请求该服务一段时间
>> 3. 资源隔离：Hystrix为每个依赖都维护了一个小型的线程池（或者信号量）。如果该线程池已满，发往该依赖的请求就被立即拒绝，而不是排队等候，从而加速失败判定
>> 4. 监控：Hystrix可以近乎实时地监控运行指标和配置的变化，例如成功、失败、超时以及被拒绝的请求等
>> 5. 回退机制：当请求失败、超时、被拒绝、或当断路器打开时，执行回退逻辑，回退逻辑可有开发人员自行控制，例如返回一个缺省值
>> 6. 自我修复：断路器打开一段时间后，会自动进入“半开”状态。

##### 8.使用Zuul构建微服务网关
* 客户端直接与微服务通信问题
> 1. 客户端会多次请求不同的微服务，增加了客户端的复杂性
> 2. 存在跨域请求，在一定场景下处理相对复杂
> 3. 认证复杂
> 4. 难以重构
> 5. 某些服务可能使用了防火墙/浏览器不友好的协议,直接访问会有一定的困难
* Zuul（核心是一系列的过滤器）
> 1. 身份认证与安全
> 2. 审查与监控
> 3. 动态路由
> 4. 压力测试
> 5. 负载分配
> 6. 静态响应处理
> 7. 多区域弹性


##### 9.使用Spring Cloud Config统一管理微服务配置
* 微服务的配置管理需求
> 1. 集中管理配置：一个使用微服务架构的应用系统可能会包含成百上千个微服务，因此需要集中管理配置
> 2. 不同环境不同配置
> 3. 运行期间可动态调整
> 4. 配置修改后可自动更新

* Spring Cloud Config
> 1. Spring Cloud Config为分布式系统外部化配置提供了服务器端和客户端的支持，它包括Config Server和Config Client部分
> 2. Config Server是一个可横向扩展、集中式的配置服务器，它用于集中管理应用程序各个环境下的配置，默认使用Git存储配置内容
> 3. Config Client是Config Server的客户端，可用于操作存储在Config Server中的配置属性
> 4. Spring Cloud Config架构图
> ![ Spring Cloud Config架构图](https://github.com/peoffice/book/blob/master/spring_cloud_docker_microservices_images/spring_cloud_config.png)

##### 10.使用Spring Cloud Sleuth实现微服务跟踪
* 微服务跟踪的原因（分布式计算的八大误区）
> 1. 网络可靠
> 2. 延迟为零
> 3. 带宽无限
> 4. 网络绝对安全
> 5. 网络拓扑不会改变
> 6. 必须有一名管理员
> 7. 传输成本为零
> 8. 网络同质化
* Spring Cloud Sleuth术语
> span（跨度）基本工作单元
> trace(跟踪)：一组共享“root span”的span组成的树状结构称为trace
> annotation(标注)：用来记录事件的存在
>> CS(Client Sent客户端发送)
>> SR（Server Received服务端接收）
>> SS(Server Sent服务端发送)
>> CR（Client Received客户端接收）
* ELK
> 一款非常流行的日志分析系统
* Zipkin
> 1. Twitter开源的分布式跟踪系统，基于Dapper的论文设计而来
> 2. 主要功能是收集系统的时序数据，从而追踪微服务架构的系统延时等问题

##### 11.使用Spring Cloud常见问题与总结

##### 12.Docker入门
* Docker架构图
> ![ Docker架构图](https://github.com/peoffice/book/blob/master/spring_cloud_docker_microservices_images/docker.png)

##### 13.将微服务运行在Docker上
* Docker常用指令
> 1. Add复制文件
> 2. ARG设置构建参数
> 3. CMD容器启动命令
> 4. COPY复制文件
> 5. EnTRYPOINT入口点
> 6. ENV设置环境变量
> 7. EXPOSE声明暴露的端口
> 8. FROM指定基础镜像
> 9. LABEL为镜像添加元数据
> 10. MAINTAINER指定维护者的信息
> 11. RUN执行命令
> 12. USER设置用户
> 13. VOLUMN指定挂载点
> 14. WORKDIR指定工作目录
> 15. 其他：STOPSINGAL,HEALTHCHECk,SHELL等

##### 14.使用Docker Compose编排微服务
* Docker Compose
> Compse是一个用于定义和运行多容器Docker应用程序的工具，前身是Fig。它非常适合用在开发、测试、构建CI工作流等场景
* Docker Compose基本步骤
> 1. 使用Dockerfile（或其他方式）定义应用程序环境，以便在任何地方重现该环境
> 2. 在docker-compose.yml文件中定义组成应用程序服务，以便各个服务在一个隔离的环境中运行
> 3. 运行docker-compose up命令，启动并运行整个应用程序
* docker-compose.yml常用命令
> 1. build：配置构建时的选项，Compose会利用它自动构建镜像
> 2. command：覆盖容器启动后默认执行的命令
> 3. dns：配置dns服务器
> 4. dns_search：配置DNS的搜索域，可以是一个值，也可以是一个列表
> 5. environment：环境变量设置，可使用数组或字典两种方式
> 6. env_file：从文件中获取环境变量，可指定一个文件路径或路径列表
> 7. expose：暴露端口，只将端口暴露给连接的服务，而不暴露给宿主机
> 8. external_links：连接到docker-compose.yml外部的容器，甚至并非Compose管理的容器，特别是提供共享或公共服务的容器
> 9. image：指定镜像名称或镜像ID
> 10. links：连接到其他服务的容器。
> 11. networks
> 12. network_mode：设置网络模式
> 13. ports：暴露端口信息
> 14. volumes：卷挂载路径设置
> 15. volume_from：从另一个服务或容器挂载卷
* docker-compose常用命令
> 1. build：构建或重新构建服务
> 2. help：查看指定命令的帮助文档
> 3. kill：通过发送SIGKILL信号停止指定服务的容器
> 4. logs：查看服务的日志输出
> 5. port：打印绑定的公共端口
> 6. ps：列出所有容器
> 7. pull：下载服务镜像
> 8. rm：删除指定服务的容器
> 9. run：在一个服务上执行一个命令
> 10. scale：设置指定服务运行的容器的个数，以service=num的形式指定
> 11. start：启动指定服务以存在的容器
> 12. stop：停止以运行的容器
> 13. up：构建、创建、重新创建、启动、连接服务的相关容器，所有连接的服务都会启动，除非它们已经运行














