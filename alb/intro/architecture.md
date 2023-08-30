# 技术架构

## 应用型负载均衡ALB
ALB是专门面向HTTP、HTTPS等应用层负载场景的负载均衡服务，基于Nginx开发，可以同时接收内网和外网流量。架构如下图：
![架构图](/images/albarchitecture.png)
ALB采用集群部署，单个集群至少4台服务器（海外集群至少2台服务器）。租户底层共用服务器，但是采用Docker进行资源隔离和CPU的隔离。ALB可以同时包含一个VIP（虚拟IP）和多个EIP，采用的是Proxy模式（即Fullnat模式）。收到Client的请求之后，ALB将client到ALB VIP（虚拟IP）或EIP的连接，转化为ALB的proxy IP到Backend（服务节点）实际IP的连接。因此Backend（服务节点）无法直接看到Client ip，只能通过X-Forwarded-For（HTTP模式）获取。另外，节点健康检查模块是集成在ALB进程中的，因此不需要额外的节点健康检查模块。

ALB的内网流量利用ECMP+ BGP实现高可用，ALB服务器通过Quagga与上联交换机建立BGP连接。同集群下的多台服务器，将向上联交换机发起相同的VIP（虚拟IP）宣告。这样上联交换机会根据ECMP算法，将流量负载均衡到集群中的各台服务器上。当有服务器发生异常时，三秒内BGP会中断，从而将故障服务器踢出集群，保证服务仍然可以正常工作。

ALB的流量是从公网进入时，Client访问请求代理ALB的流量进入UCloud POP点，进入UVER（UCloud Virtual Edge Router）。UVER是UCloud自研的公网流量计算中心，能够从业务库中获知所有的EIP的下一跳信息，通过BGP引流后，将EIP的流量建立隧道送到相应的下一跳。一个ALB的EIP会落到ALB集群中的所有服务器上，因此UVER将这部分流量，按照一致性哈希算法送到ALB集群各个服务器中。

在ALB中，集群健康检查模块将定时探测服务器的存活状态，如果发现服务器有问题，则将通知UVER，将异常服务器剔除，从而保证高可用。同样的，ALB集群也是跨可用区高可用的。
