{{indexmenu_n>1}}

# 添加VServer

## 操作步骤 

ULB实例创建完成后，可点击**详情**进入**VServer管理页面**添加VServer。

1，在VServer管理页面中点击**添加VServer**。

2，填写配置信息，进行VServer创建。详细配置说明见下方。

![](https://docs.ucloud.cn/_media/network/ulb/vserver%E5%BB%BA%E7%AB%8Btcp.png)


> 外网ULB，TCP协议支持“报文转发模式”与“请求代理模式”；内网ULB，TCP协议仅支持“报文转发模式“。


![](https://docs.ucloud.cn/_media/network/ulb/%E6%B7%BB%E5%8A%A0vserver-tcp.png)

## 配置说明

创建VServer监听器的选项包含以下内容：

|配置|说明|
|-|-|
|VServer名称|VServer名称，必填项。|
|协议和端口|监听器所监听的协议及端口，包含HTTP/HTTPS/TCP/UDP四种协议。|
|监听器类型|HTTP、HTTPS默认为请求代理模式，UDP默认为报文转发模式。|
|负载均衡算法|监听器对数据包的负载方式|
|服务节点	|一般情况，添加服务节点是需要在VServer监听器创建完成后再进行。 该选项提供了从其他VServer复制服务节点池配置的方法，以便利用原有配置快速创建。|
|服务会话保持|对于HTTP/HTTPS协议，使用默认/自定义关键词对用户登录态的保持。|
|连接保持时间|TCP请求代理模式下，或HTTP、HTTPS协议，可选择客户端请求连接的有效时间。可选时间范围[1-86400]秒|
|节点健康检查|根据所选协议不同，检查方式包含服务地址/端口检查和HTTP检查两种方式。|

[[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
