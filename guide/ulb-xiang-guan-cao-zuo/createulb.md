{{indexmenu_n>1}}

# 创建ULB

### 操作步骤

1、进入**负载均衡 ULB**页面。

![](https://static.ucloud.cn/3cfa285670e74d2fae692cac88014f2c.png)

2，点击**创建负载均衡**进行ULB实例创建。

![](https://docs.ucloud.cn/_media/network/ulb/ulb2.png)

3、填写配置信息，进行ULB实例创建。详细配置说明见下方。

![](https://docs.ucloud.cn/_media/network/ulb/%E5%88%9B%E5%BB%BAulb-%E5%90%AB%E9%98%B2%E7%81%AB%E5%A2%99.png)

4，点击**立即购买**，即创建成功。

![](https://static.ucloud.cn/e4e5e58fdddd49fc80b6cd2fb3d08572.png)

### 配置说明

|配置|说明|
|-|-|
|地域|ULB所属的地域。选定地域后，只能添加该地域的后端服务节点。|
|业务组|ULB所属的管理业务组。|
|所属VPC|ULB所属的VPC网络。选定VPC后，后端服务节点只能添加同VPC下的云资源。|
|网络模式|分为内网、外网两种模式。详细说明可参考（如何加相对路径），其中内网，ULB对外提供服务的地址为内网IP地址。而外网，ULB对外提供服务的地址为外网弹性IP。|
|所属子网|选择内网后，需选择所属子网。从该子网中分配内网IP地址作为ULB对外提供服务的IP地址。|
|弹性IP|选择外网后，需要配置外网弹性IP作为ULB对外提供服务的IP地址。可选择“新购”或“现有”外网弹性IP。|
|计费方式|选择“新购”外网弹性IP时，需选择IP计费方式。可选带宽、流量、共享带宽等。|
|带宽|选择“新购”外网IP时，需选择IP的带宽值。|
|外网防火墙|外网模式下，可绑定外网防火墙进行访问控制。可选不绑定、绑定。|

[[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
