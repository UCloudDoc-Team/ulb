# 产品简介

## 网络型负载均衡NLB简介
网络型负载均衡NLB（Network Load Balancer ）是专门面向TCP/UDP协议推出的新一代四层负载均衡，支持超高性能和丰富的功能，支持全端口，跨域挂载等高级功能。

### 产品组成

- NLB负载均衡实例：接受来自客户端的流量并将请求转发到一个或多个后端服务器。
- 监听器：每个监听器需要您配置的协议和端口监听来自客户端的请求，以及设置流量如何进行分发等。不同监听器用于处理不同的业务流量，根据您定义的转发策略将请求转发到一个后端服务节点。
- 服务节点：真实处理客户端流量后端服务器，服务节点可以是云服务器实例、弹性网卡或IP地址。

### 产品优势

- 简单易用

NLB相比传统的CLB，无需深入服务节点进行额外配置，即开即用，减少您操作的复杂程度。

- 丰富特性

NLB作为业务入口可以流量入口，同时处理海量并发连接，同时提供全端口、跨域挂载等高级特性，满足您更多的业务场景。

- 高可用

底层采用多层的容灾架构设计，通过集群容灾、会话保持、健康检查等机制保障实例的可用性，同时支持挂载跨地域服务节点，为业务进行保驾护航。