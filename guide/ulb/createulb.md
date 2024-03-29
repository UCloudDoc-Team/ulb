# 负载均衡CLB

进入**负载均衡 ULB**页面，点击**传统型负载均衡**标签页。

## 创建CLB

1、点击**创建负载均衡**进行CLB实例创建。

2、填写配置信息，进行CLB实例创建。详细配置说明见下方。

![](/images/createulb2.png)

3、点击**立即购买**，即创建成功。

### 配置说明

|配置|说明|
|---|---|
|地域|所属地域。选定地域后，只能添加该地域的后端服务节点。|
|负载均衡类型|分为请求代理型和报文转发型，请求代理型支持HTTP、HTTPS、TCP协议，报文转发型支持TCP、UDP协议，详见[负载均衡类型/网络模式](https://docs.ucloud.cn/ulb/fast/createulb/networktype)|
|网络模式|分为内网、外网两种模式。其中内网，CLB对外提供服务的地址为内网IP地址。而外网，CLB对外提供服务的地址为外网弹性IP。|
|所属VPC|所属VPC网络。选定VPC后，后端服务节点只能添加同VPC下的云资源。|
|所属子网|选择内网后，需选择所属子网。从该子网中分配内网IP地址作为CLB对外提供服务的IP地址。|
|弹性IP(EIP)|选择外网后，需要配置外网弹性IP作为CLB对外提供服务的IP地址。可选择“新购”或“现有”外网弹性IP。|
|计费方式|选择“新购”外网弹性IP时，需选择外网带宽的计费方式。可选带宽、流量、共享带宽等。详见[外网弹性IP-计费方式简介](https://docs.ucloud.cn/unet/eip/introduction)。|
|带宽|选择“新购”外网IP时，需选择外网带宽值。|
|外网防火墙|外网模式下，可绑定外网防火墙进行访问控制。可选不绑定、绑定。|
|实例名称|实例名称。|
|业务组|所属的管理业务组。|

## 删除CLB

删除CLB实例后，绑定的EIP会被一并删除。
> 若EIP需要保留，可先解绑，再删除实例。

## 修改名称及备注

CLB列表页，点击名称列的**修改名称及备注。**

### 配置说明

1、**资源名称**，必填项，不修改默认为当前的名称。

2、**备注**，非必填项，不填写即为空。


## 更改业务组

列表页选定资源后，点击操作中的**更改业务组**操作。可选择已有的业务或新建业务组。

同时支持批量更改业务组，选中需要更改业务组的资源，点击批量更换业务组操作。


## 弹性外网IP（EIP）

外网类型的CLB实例，可对绑定EIP进行以下操作。更多操作可前往外网弹性IP控制台进行操作。
> 外网CLB，至少需要绑定一个外网弹性IP（EIP）才能正常对外提供服务，绑定EIP的上限为20个。


### 绑定EIP 

1、列表页选定外网CLB资源后，点击操作中的**绑定弹性IP**，下拉框中选择已有的EIP。若当前无EIP，可前往外网弹性IP页面申请。

2、列表页选定外网CLB资源后，点击**详情**进入概览页。外网弹性IP卡片，可查看当前已绑定的EIP详细信息。


### 解绑EIP 

1、列表页选定外网CLB资源后，点击**详情**进入概览页。外网弹性IP卡片，选定需要解绑的EIP，点击**解绑**。

2、批量解绑CLB绑定的EIP，可前往外网弹性IP页面操作。




