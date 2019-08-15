{{indexmenu_n>6}}


# 名词解释

### ULB

ULB服务实例，通过创建监听器（VServer），并将添加后端服务节点（RealServer），以实现流量均衡与服务容错的功能

### VServer

ULB监听器，每个VServer是一组负载均衡前端端口配置。包含协议、端口、负载算法、会话保持、客户端超时等。

### RealServer

真实服务节点，由云主机内网IP+云主机端口组成的后端服务实例。

### 服务IP地址

外网ULB，提供服务的IP地址为外网弹性IP（EIP）。

内网ULB，提供服务的IP地址为内网IP地址。

 [[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]

