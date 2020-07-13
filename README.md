# 负载均衡 ULB

 ULB （UCloud Load Balancer）是UCloud提供的负载均衡服务。可以在多台云主机间实现应用程序流量的自动分配，并通过健康检查实现故障自动切换，提高业务可用性，提高资源利用率。

* 产品简介
    * [什么是ULB](/ulb/intro/whatisulb)
    * [产品功能](/ulb/intro/function)
    * [技术架构](/ulb/intro/architecture)
    * [性能指标](/ulb/intro/performance)
    * [使用限制](/ulb/intro/limit)
* 购买指南
    * [产品定价](/ulb/fast/price)
    * 产品选型
        * [ULB：网络模式](/ulb/fast/createulb/networktype)
        * [VServer：监听器协议／类型](/ulb/fast/createulb/vservertype)
        * [负载均衡算法](/ulb/fast/createulb/algorithm)
* 操作指南
    * ULB
        * [创建ULB](/ulb/guide/ulb/createulb)
        * [删除ULB](/ulb/guide/ulb/deleteulb)
        * [编辑ULB](/ulb/guide/ulb/editulb)
        * [绑定/解绑EIP](/ulb/guide/ulb/eip)
    * VServer哈
    
        * [添加VServer](/ulb/guide/vserver/createvserver)
        * [删除VServer](/ulb/guide/vserver/deletevserver)
        * [更改VServer配置](/ulb/guide/vserver/editvserver)
    * 服务节点
        * [添加服务节点](/ulb/guide/realserver/addrealserver)
        * [删除服务节点](/ulb/guide/realserver/deleterealserver)
        * [禁用服务节点](/ulb/guide/realserver/disablerealserver)
        * [报文转发模式服务节点配置](/ulb/guide/realserver/editrealserver)
    * 内容转发
        * [添加内容转发规则](/ulb/guide/forwardpolicy/addrule)
        * [删除内容转发规则](/ulb/guide/forwardpolicy/deleterule)
        * [管理内容转发规则](/ulb/guide/forwardpolicy/editrule)
    * 证书
        * [证书格式](/ulb/guide/certificate/certificateformat)
        * [添加证书](/ulb/guide/certificate/addcertificate)
        * [使用证书](/ulb/guide/certificate/use)
        * [更换证书](/ulb/guide/certificate/replacecertificate)
        * [删除证书](/ulb/guide/certificate/deletecertificate)
    * 外网防火墙
        * [绑定防火墙](/ulb/guide/firewall/bindfirewall)
        * [更换防火墙](/ulb/guide/firewall/updatefirewall)
        * [解绑防火墙](/ulb/guide/firewall/unbindfirewall)
    * 监控指标
        * [获取监控指标](/ulb/guide/ulbmonitor/getmonitoring)
* 常见问题
    * 工作原理相关
        * [ULB的会话保持是如何实现的？](/ulb/faq/session)
        * [VServer的运行状态是指什么？](/ulb/faq/vserverstatus)
        * [连接空闲超时的原理？](/ulb/faq/idletimeout)
        * [ULB健康检查机制是如何工作的？](/ulb/faq/ulbhealthcheck)
    * 使用相关
        * [ULB如何获取客户端的源地址？](/ulb/faq/sourceip)
        * [服务节点收到大量内网IP的访问是否正常？](/ulb/faq/intranetip)
        * [如何禁止某些源地址访问后端服务节点？](/ulb/faq/firewall)
        * [轮询算法能否使所有服务节点请求数均衡？](/ulb/faq/pollingalgorithm)
        * [ULB服务器是否会宕机？](/ulb/faq/ulbserver)
        * [ULB错误码有哪些？](/ulb/faq/errorcode)
        * [VServer端口和服务节点端口是否必须一致？](/ulb/faq/vserverport)
    * 测试相关
        * [内网ULB的IP地址为何无法ping通？](/ulb/faq/ping)
        * [对ULB压测时为何会出现连接失败？](/ulb/faq/pressuretest)
* [名词解释](/ulb/glossary)
* [新功能发布记录](/ulb/newfunctions)    
* API工具
    * [UAPI简介](/ulb/api/uapi)  
    
    
    
    
        





