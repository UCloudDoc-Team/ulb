{{indexmenu_n>11}}

# 如何禁止某些源地址访问后端服务节点？

ULB支持防火墙功能，使用方式如下：

* 创建负载均衡的时候绑定防火墙，或在ULB的详情页中，进入“外网防火墙”tab页面进行防火墙的绑定。

注意：

* 防火墙仅对“请求代理”模式下的VServer生效。

* 在配置防火墙的过程中，如果需要对某个请求代理模式的VServer进行白名单/黑名单限制，需配置防火墙中VServer对应端口的允许/拒绝策略。由于防火墙的默认行为是拒绝，因此配置防火墙的时候请务必添加VServer相应端口的相应源地址放行规则，避免影响业务。

该功能正在灰度中。


[[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
