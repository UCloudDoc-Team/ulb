#  VServer

## 添加Vserver
### 操作步骤 

CLB实例创建完成后，可点击**详情**进入**VServer管理页面**添加VServer。

1、在VServer管理页面中点击**添加VServer**。

2、填写配置信息，进行VServer创建。详细配置说明见下方。

![](/images/vserver%E5%BB%BA%E7%AB%8Btcp.png)


### 配置说明

创建VServer监听器的选项包含以下内容：

|配置|说明|
|---|---|
|VServer名称|VServer名称，必填项。|
|协议和端口|监听器所监听的协议及端口，包含HTTP/HTTPS/TCP/UDP四种协议。|
|负载均衡算法|监听器对数据包的负载方式。|
|服务节点	|一般情况，添加服务节点是需要在VServer监听器创建完成后再进行。 该选项提供了从其他VServer复制服务节点池配置的方法，以便利用原有配置快速创建。|
|服务会话保持|对于HTTP/HTTPS协议，使用默认/自定义关键词对用户登录态的保持。对于TCP(报文转发)/UDP，默认连接超时时间为900s。开启/关闭会话保持功能后，当前长连接可能会中断重连。开启会话保持后，可以设定会话保持时间，会话保持时间、连接超时时间均为该设定值。|
|连接保持时间|TCP请求代理模式下，或HTTP、HTTPS协议，可选择客户端请求连接的有效时间。可选时间范围[1-86400]秒。|
|节点健康检查|健康检查类型。UDP协议支持端口检查、PING检查和UDP检查；TCP协议支持端口检查；HTTP/HTTPS协议支持端口检查和HTTP检查。详细的健康检查原理、规则及使用场景见[健康检查](/ulb/faq/ulbhealthcheck)。|



## 删除VServer

### 操作步骤

进入**VServer管理页面**。

### 删除单个VServer

1、选择需要删除的VServer，点击左侧的**VServer名称**。

2、右侧概览信息中，点击**删除VServer**即可完成删除。

![](https://static.ucloud.cn/fc91a84b6c364c8fb7aefddd3812c3c9.png)


## 更改VServer配置

进入**VServer管理页面**，可进行VServer配置更改。

### 操作步骤

1、右侧基本信息模块，点击**更改设置**。

![](https://static.ucloud.cn/d756aed9104b47dbad5438d2f0f225f5.png)

2、弹出更改VServer的弹窗，即可进行VServer配置更改。可更改的配置如下，不修改的配置仍保持不变。

![](https://static.ucloud.cn/1598e21f7e224fffb09fe920af2e7130.png)

### 配置说明

|配置|说明|
|---|---|
|VServer名称|VServer名称，必填项。|
|负载均衡算法|监听器对数据包的负载方式。|
|服务会话保持|对于HTTP/HTTPS协议，使用默认/自定义关键词对用户登录态的保持。|
|连接保持时间|TCP请求代理模式下，或HTTP、HTTPS协议，可选择客户端请求连接的有效时间。可选时间范围[1-86400]秒|
|节点健康检查|根据所选协议不同，检查方式包含服务地址/端口检查和HTTP检查两种方式。|

