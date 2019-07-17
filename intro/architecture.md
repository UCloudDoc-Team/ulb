
[前往 Github](https://github.com/UCloudDocs/UCloud-document/tree/master/network/ulb)


{{indexmenu_n>5}}

# 技术架构

ULB（UCloud Load Balancer）提供流量分发的能力，保证业务可扩展和高可用。支持内网和外网两种场景，支持请求代理和报文转发两种转发模式。下文将分别介绍ULB的的请求代理（下简称ULB7）和报文转发模式（下简称ULB4）的基本架构。

## 内网ULB4

内网ULB4是基于DPDK技术自研的。单台服务器可以提供超过3000万并发连接，1000万 pps，10G线速转发能力。采用集群部署，单个集群至少4台服务器。利用ECMP+ BGP实现高可用。

内网ULB4采用了类似于DR的转发模式。内网负载均衡转发示意图如下：

![](https://static.ucloud.cn/860b15cd48ec4d099e47886928b832e2.png)

如上图，同一个集群的ULB4通过向其上联的接入交换机宣告相同的VIP，而接入交换机配置了ECMP算法，因此可将流量负载均衡到多台服务器上，从而够成了集群。当某些ULB4发生转发异常的时候，BGP报文转发也会停止转发，在三秒之内该ULB4服务器就会被剔出集群，从而保证高可用，同时集群健康检查模块也将发出告警，使得工程师介入处理。此外同一个ULB4集群的服务器都是跨可用区分布的，从而保证集群跨可用区高可用。

此外，ULB4中还有个模块负载后端节点的健康检查（目前仅支持tcp端口探测），并上报给ulb4manager和ULB4转发服务器。ULB4转发服务器收到Client的业务报文后，将从状态正常的后端节点中选择一个，修改目的mac后打隧道送到后端节点，注意其中的源IP和目的IP都是不变的。此时，后端节点必须在LO扣绑定ULB4的虚拟IP地址，并监听服务，才能正确处理报文，并将回包直接单播送回给Client。这是一个典型的DR过程。因此内网ULB4可以直接看到Client的源IP。

## 外网ULB4

外网ULB4与内网ULB4类似，同样是基于DPDK技术自研的。单台服务器可以提供超过3000万并发连接，1000万 pps，10G线速转发能力。采用集群部署，单个集群至少4台服务器。利用ECMP+ BGP实现高可用。同样的，它采用了类似于DR的转发模式。外网负载均衡转发示意图如下：

![](https://static.ucloud.cn/117279d9aac8448f9688d5ca5c282b94.png)

与内网ULB4不同的是，外网流量是从公网进来的。Client访问ULB4的流量进入UCloud POP点，进入UVER（UCloud Virtual Edge Router）。UVER是UCloud自研的公网流量计算中心，它能够从业务库中获知所有的EIP的下一跳信息，通过BGP引流后，将EIP的流量打隧道送到相应的下一跳。一个ULB4的EIP会落到ULB4集群中的所有服务器上，因此UVER将这部分流量，按照一致性哈希算法负载均衡送到集群各个服务器中。后续的流程与内网ULB4类似。Backend节点中需要将ULB的EIP绑定在LO，并监听服务，而回程报文将直接送到UVER，并通过internet返回Client。

在外网ULB4中，集群健康检查模块将定时探测服务器的存活状态，如果发现服务器有问题，则将通知UVER，将异常服务器剔除，从而保证高可用。同样的，外网ULB4集群也是跨可用区高可用的。

## 外网ULB7

ULB7基于Haproxy开发，单个实例可以支持超过40w pps，2Gbps，以及至少40万并发连接。ULB利用CPU的亲和性，实现核的隔离和资源控制。

![](https://static.ucloud.cn/c5131ef063c54fddbce7b26aaf281992.png)

与ULB4采用的DR模式不同，ULB7采用的是Proxy模式，也就是Fullnat模式。收到Client的请求之后，ULB7将client到ULB7 EIP的连接，转化为ULB7的proxy ip到Backend实际ip的连接。因此Backend无法直接看到Client ip。另外，健康检查模块是集成在ULB7进程中的，因此不需要额外的节点健康检查模块。

同样的，在外网ULB7中，集群健康检查模块将定时探测服务器的存活状态，如果发现服务器有问题，则将通知UVER，将异常服务器剔除，从而保证高可用。同样的，外网ULB7集群也是跨可用区高可用的。

## 模式比对

相对于ULB7，ULB4转发能力更强，适合与追求转发性能的场景。而ULB7则可以对七层数据进行处理，可以进行SSL的卸载，执行域名转发、路径转发等功能，并且后端节点不需要额外配置VIP。

 [[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]

