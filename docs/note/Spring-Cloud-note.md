# Spring Cloud学习笔记

## 1. 单体架构和分布式架构

分布式架构：根据业务功能对系统进行拆分，每个业务模块作为独立项目开发，称为一个服务。

分布式架构需要考虑的问题：

- 服务拆分力度如何？
- 服务集群地址如何维护？
- 服务之间如何实现远程调用？
- 服务健康状态如何感知？

## 2. 微服务

微服务是一种经过良好架构设计的**分布式**架构方案

微服务架构特征：

* 单一职责：微服务拆分粒度更小，每个服务都对应唯一的业务能力，做到单一职责，避免重复业务开发。
* 面向服务：微服务对外暴露业务接口。
* 自治：团队独立、技术独立、数据独立、部署独立。
* 隔离性强：服务调用做好隔离、容错、降级，避免出现级联问题。

微服务技术框架：Spring Cloud和阿里巴巴的Dubbo

## 3. Eureka注册中心

- EnrekaServer：
  - 记录服务信息
  - 心跳监控
- EnrekaClient：
  - Provider：
    - 注册自己的信息到EurekaServer
    - 每隔30秒向EurekaServer发送心跳
  - Consumer：
    - 根据服务名称从EnrekaServer拉取服务列表
    - 基于服务列表做负载均衡，选中一个微服务后发起远程调用

## 4. Nacos注册中心 & 配置中心

Nacos 是阿里巴巴的产品，现在是 Spring Cloud 的一个组件。相比于 Eureka 功能更加丰富，在国内受欢迎程度较高。

Windows 启动命令(standalone 代表着单机模式运行，非集群模式):
```
startup.cmd -m standalone
```

http://192.168.17.1:8848/nacos/index.html
账号：nacos
密码：nacos

## 5. 统一网关 Gateway

网管功能：
- 身份认证和权限校验
- 服务路由、负载均衡
- 请求限流

Spring Cloud 中网关的实现包括两种：
- gateway
- zuul

Zuul 是基于 Servlet 实现，属于阻塞式编程。
Spring Cloud Gateway 是基于 Spring5 中提供的 WebFlux 实现，属于响应式编程的实现，具备更好的性能。

