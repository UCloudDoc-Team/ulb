
# 负载均衡 ULB

负载均衡ULB（UCloud Load Balancer）提供业务流量自动分发服务，通过将流量按需转发至后端多个云资源来提升业务系统的处理能力，并通过健康检查消除单点故障，提高业务系统可用性。即开即用，按需付费。

负载均衡ULB产品族包含：应用型负载均衡ALB、传统型负载均衡CLB。网络型负载均衡NLB即将上线。

* 产品动态
  * [新功能发布记录](ulb/releasenotes/newfunctions)
* 应用型负载均衡ALB
  * 产品简介
    * [产品介绍](/ulb/alb/intro/whatisalb)
    * [产品功能](/ulb/alb/intro/function)
    * [技术架构](/ulb/alb/intro/architecture)
    * [性能指标](/ulb/alb/intro/performance)
    * [使用限制](/ulb/alb/intro/limit)
  * 计费说明
    * [产品定价](/ulb/alb/buy/charge)
    * [回收策略](/ulb/alb/buy/recyle)
  * 操作指南
    * 实例
      *  [创建和管理ALB实例]( ulb/alb/guide/instance/create-instance.md )
    * 监听器
      *  [监听器管理]( ulb/alb/guide/listeners/manage-listeners.md )
      *  [服务节点]( ulb/alb/guide/listeners/manage-node.md )
      *  [内容转发]( ulb/alb/guide/listeners/forwarding.md )
      *  [监听证书]( ulb/alb/guide/listeners/certificates.md )
    * 安全管理
      *  [TLS安全策略]( ulb/alb/guide/security-management/tls-security-policies.md )
      *  [安全规则]( ulb/alb/guide/security-management/safety-rules.md )
      *  [证书管理]( ulb/alb/guide/security-management/manage-certificates.md )
    * 监控
      *  [监控项说明]( ulb/alb/guide/monitoring/monitoring-metrics.md )
      *  [查看监控信息]( ulb/alb/guide/monitoring/view-alb-monitoring.md )
    * 日志
      *  [操作日志]( ulb/alb/guide/logs/audit-logs.md )
      *  [访问日志]( ulb/alb/guide/logs/access-logs.md )
  * 最佳实践
    * [使用ALB挂载跨域VPC的云服务器](ulb/alb/use/use-instance.md)
* 传统型负载均衡CLB
  * 产品简介
    * [产品简介](/ulb/intro/whatisulb)
    * [产品功能](/ulb/intro/function)
    * [技术架构](/ulb/intro/architecture)
    * [性能指标](/ulb/intro/performance)
    * [使用限制](/ulb/intro/limit)
  * 购买指南
    * [产品定价](/ulb/fast/price)
    * 产品选型
        * [负载均衡类型/网络模式](/ulb/fast/createulb/networktype)
        * [负载均衡算法](/ulb/fast/createulb/algorithm)
* 网络型负载均衡NLB
  * 产品简介
    * [产品介绍](/ulb/NLB/intro/whatisnlb)
    * [功能特性](/ulb/NLB/intro/function)
    * [使用限制](/ulb/NLB/intro/limit)
  * 计费说明
    * [计费规则](/ulb/NLB/buy/charge)
    * [回收策略](/ulb/NLB/buy/recyle)
  * 操作指南
    * 实例
      * [创建和管理网络型负载均衡实例](/ulb/NLB/guide/instance/create-instance.md)
    * 监听器
      * [监听器概述](ulb/NLB/guide/listeners/whatlisteners.md)
      * [监听器管理](ulb/NLB/guide/listeners/manage-listeners.md)
      * [服务节点](ulb/NLB/guide/listeners/manage-node.md )
    * [操作日志](ulb/NLB/guide/audit-logs.md)
  * 最佳实践
    * [使用NLB挂载跨地域VPC的服务节点](ulb/NLB/use/use-instance.md)

​    
​    
​    

