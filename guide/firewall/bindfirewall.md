{{indexmenu_n>1}}

# 绑定防火墙

ULB可以绑定防火墙，实现对源地址的访问控制。

> 目前防火墙仅仅对请求代理模式下的VServer生效。该功能仍在灰度中，如有需求可联系技术支持。


## 操作步骤

1，进入**负载均衡 ULB页面，**选择需要绑定防火墙的ULB实例，进入**VServer管理页面**。

2，点击**外网防火墙，**进入外网防火墙页面。

3，点击**立即绑定**，选择需要选择的防火墙。

![](https://static.ucloud.cn/d685f475443c4a6680f4f14049c5a97c.png)

4，点击**确定**，完成绑定。 

> 请注意：防火墙规则仅仅对ULB请求代理模式下的VServer生效。请务必保证防火墙规则中放行了该VServer的相应端口。同时，ICMP相关规则是不生效的。


5，绑定完成后，将展示防火墙的相关信息。

 [[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
