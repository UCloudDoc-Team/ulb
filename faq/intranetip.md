{{indexmenu_n>10}}

# 服务节点收到大量内网IP的访问是否正常？

收到的大量内网IP的访问是正常的。 ULB在请求代理模式下，对后端服务节点转发请求时，使用的是 ULB的内网代理IP。

例如，用户在北京二的后端云主机访问日志中发现大量来自 10.10.251.0/24 网段的访问，即为北京二 ULB 的内网代理 IP。 

ULB 在各个区域的代理IP网段见[公共服务网段](https://docs.ucloud.cn/network/vpc/limit)。

[[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
