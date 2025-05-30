
- [概览](/ulb/README)
- 应用型负载均衡ALB
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
- 网络型负载均衡NLB
  * 产品简介
    * [产品介绍](/ulb/NLB/intro/whatisnlb)
    * [功能特性](/ulb/NLB/intro/function)
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
    *  [使用TOA功能获取源IP](ulb/NLB/use/obtain-client-ip.md)
    *  [使用Proxy获取源IP](ulb/NLB/use/obtain-client-ip-proxy.md)
- 传统型负载均衡CLB
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
  * 操作指南
    * CLB
      * [CLB](/ulb/guide/ulb/createulb)
      * [服务节点查询](/ulb/guide/ulb/querybackend)
    * [VServer](/ulb/guide/vserver/createvserver) 
    * 服务节点
      * [服务节点](/ulb/guide/realserver/addrealserver)
      * [报文转发模式服务节点配置](/ulb/guide/realserver/editrealserver)
    * [内容转发](/ulb/guide/forwardpolicy/addrule)
    * 证书
      * [证书格式](/ulb/guide/certificate/certificateformat)
      * [证书管理](/ulb/guide/certificate/addcertificate)
    * 安全策略
      * [安全策略说明](/ulb/guide/securitypolicy/securitypolicy)
      * [安全策略管理](/ulb/guide/securitypolicy/addsecuritypolicy)
    * [外网防火墙](/ulb/guide/firewall/bindfirewall)
    * 日志管理
      * [开启日志](/ulb/guide/log/openlog)
      * [关闭日志](/ulb/guide/log/closelog)
    * 监控指标
      * [获取监控指标](/ulb/guide/ulbmonitor/getmonitoring)
     * 数据压缩
       *  [开启数据压缩]( /ulb/guide/datacompression/opendatacompression.md )
    * CLB迁移指导
      *  [IP迁移]( /ulb/guide/migrate/ipmigrate.md )
      *  [配置迁移]( /ulb/guide/migrate/configuremigration.md)
  * 常见问题
    * 工作原理相关
      * [会话保持是如何实现的？](/ulb/faq/session)
      * [VServer的运行状态是指什么？](/ulb/faq/vserverstatus)
      * [连接空闲超时的原理？](/ulb/faq/idletimeout)
      * [健康检查机制是如何工作的？](/ulb/faq/ulbhealthcheck)
    * 使用相关
      * [如何获取客户端的源地址？](/ulb/faq/sourceip)
      * [服务节点收到大量内网IP的访问是否正常？](/ulb/faq/intranetip)
      * [如何禁止某些源地址访问后端服务节点？](/ulb/faq/firewall)
      * [轮询算法能否使所有服务节点请求数均衡？](/ulb/faq/pollingalgorithm)
      * [服务器是否会宕机？](/ulb/faq/ulbserver)
      * [错误码有哪些？](/ulb/faq/errorcode)
      * [VServer端口和服务节点端口是否必须一致？](/ulb/faq/vserverport)
    * 测试相关
      * [内网报文转发的IP地址为何无法ping通？](/ulb/faq/ping)
      * [压测时为何会出现连接失败？](/ulb/faq/pressuretest)
    * [关于53端口封禁的说明](/ulb/faq/53port)
- 产品动态
  * [新功能发布记录](ulb/releasenotes/newfunctions)
  * [2023-9-27 【CLB 产品调整公告】](ulb/releasenotes/updates)
  * [2024-4-18 【ALB 产品支持SNI功能】](ulb/releasenotes/alb-sni.md)
  * [2024-6-25 【ALB 产品支持挂载跨域VPC云服务器】](ulb/releasenotes/alb-vpc.md)
  * [2024-8-1 【NLB 产品公测上线 】](ulb/releasenotes/nlb_release.md)
  * [2024-9-26 【CLB 产品支持一键迁移ALB 】](ulb/releasenotes/clb7_migrate.md)
  * [2024-12-10 【ALB产品转发规则新增动作类型 】](ulb/releasenotes/alb_forwarding_upadte.md)
- API工具

  * [UAPI简介](/ulb/api/uapi)


​    
