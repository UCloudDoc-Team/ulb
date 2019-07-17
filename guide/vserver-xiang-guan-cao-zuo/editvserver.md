{{indexmenu_n>3}}

# 更改VServer配置

进入**VServer管理页面**，可进行VServer配置更改。

### 操作步骤

1，右侧基本信息模块，点击**更改设置**。

![](https://static.ucloud.cn/d756aed9104b47dbad5438d2f0f225f5.png)

2，弹出更改VServer的弹窗，即可进行VServer配置更改。可更改的配置如下，不修改的配置仍保持不变。

![](https://static.ucloud.cn/1598e21f7e224fffb09fe920af2e7130.png)

|配置|说明|
|-|-|
|VServer名称|VServer名称，必填项。|
|负载均衡算法|监听器对数据包的负载方式。|
|服务会话保持|对于HTTP/HTTPS协议，使用默认/自定义关键词对用户登录态的保持。|
|连接保持时间|TCP请求代理模式下，或HTTP、HTTPS协议，可选择客户端请求连接的有效时间。可选时间范围[1-86400]秒|
|节点健康检查|根据所选协议不同，检查方式包含服务地址/端口检查和HTTP检查两种方式。|

[[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
