# 创建ULB


### 操作步骤

1、进入**负载均衡 ULB**页面。

![](/images/createulb01.png)

2、点击**创建负载均衡**进行ULB实例创建。

3、填写配置信息，进行ULB实例创建。详细配置说明见下方。

![](/images/createulb2.png)

4、点击**立即购买**，即创建成功。

![](/images/createulb3.png)


### 配置说明

|配置|说明|
|---|---|
|地域|ULB所属的地域。选定地域后，只能添加该地域的后端服务节点。|
|负载均衡类型|分为请求代理型和报文转发型，请求代理型支持HTTP、HTTPS、TCP协议，报文转发型支持TCP、UDP协议，详见[ULB：负载均衡类型/网络模式](https://docs.ucloud.cn/ulb/fast/createulb/networktype)|
|网络模式|分为内网、外网两种模式。其中内网，ULB对外提供服务的地址为内网IP地址。而外网，ULB对外提供服务的地址为外网弹性IP。|
|所属VPC|ULB所属的VPC网络。选定VPC后，后端服务节点只能添加同VPC下的云资源。|
|所属子网|选择内网后，需选择所属子网。从该子网中分配内网IP地址作为ULB对外提供服务的IP地址。|
|弹性IP(EIP)|选择外网后，需要配置外网弹性IP作为ULB对外提供服务的IP地址。可选择“新购”或“现有”外网弹性IP。|
|计费方式|选择“新购”外网弹性IP时，需选择外网带宽的计费方式。可选带宽、流量、共享带宽等。详见[外网弹性IP-计费方式简介](https://docs.ucloud.cn/unet/eip/introduction)。|
|带宽|选择“新购”外网IP时，需选择外网带宽值。|
|DDos攻击防护|防护功能由全球清洗产品提供，支持对攻击流量进行分布式的清洗，可抵御百G级别的大流量攻击。更多信息：[控制台-全球清洗](https://console.ucloud.cn/anycastclean/manage?type=manage&id=true)，[文档-全球清洗](https://docs.ucloud.cn/uantiddos/uanycastclean/overview)|
|外网防火墙|外网模式下，可绑定外网防火墙进行访问控制。可选不绑定、绑定。|
|实例名称|ULB实例名称。|
|业务组|ULB所属的管理业务组。|


