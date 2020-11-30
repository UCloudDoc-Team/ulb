# 名词解释

## ULB

ULB服务实例，通过创建监听器（VServer），并将添加后端服务节点（RealServer），以实现流量均衡与服务容错的功能。
![](/images/吃瓜.gif)
![](/images/同九，吾不及汝秀.jpg)

## VServer

ULB监听器，每个VServer是一组负载均衡前端端口配置。包含协议、端口、负载算法、会话保持、客户端超时等。
![](/images/今天星期五.jpg)

![](/images/今天星期五.gif)

![](/images/今天星期五.png)

## RealServer/RS

真实服务节点，由云主机内网IP+云主机端口组成的后端服务实例。

![](/images/真好，又可以加班了.gif)


![](/images/今天星期五.png)

## 服务IP地址

外网ULB，提供服务的IP地址为外网弹性IP（EIP）。

![](/images/今天星期五.gif)

内网ULB，提供服务的IP地址为内网IP地址。


