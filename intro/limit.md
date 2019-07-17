[前往 Github](https://github.com/UCloudDocs/UCloud-document/tree/master/network/ulb)

{{indexmenu_n>9}}

# 使用限制

## 路由配置

为保证 ULB 能够正确的将数据转发到后端服务节点上，需要确保 ULB 后端服务节点的防火墙／路由能够允许对应网段的访问，否则可能会造成该主机无法正常提供服务。

ULB 在各个区域的网段见[公共服务网段](https://docs.ucloud.cn/network/vpc/limit)。

## HTTP报文头限制

ULB的默认报文头大小为8K。配置时需确保HTTP报文头大小不超过8K，否则会造成ULB无法正常工作。

 [[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
