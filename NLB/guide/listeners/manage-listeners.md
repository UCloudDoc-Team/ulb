# 监听器管理

## 创建UDP监听器

1. 登录网络型负载均衡NLB控制台。

2. 在顶部导航栏，选择NLB实例的所属地域。

3. 选择以下一种方法，打开监听配置。

   - 在**实例列表**页面，在目标实例**操作**列点击**监听器管理**。

   - 在**实例列表**页面，点击目标实例ID或者详情。在**监听器管理**页签，点击**添加**。
4. 在**创建监听器**页面，完成以下配置，然后点击**确认**。

| 配置项       | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| 协议         | 选择一种负载均衡协议，本示例选择UDP协议                      |
| 端口         | 支持全端口监听和单端口监听<br />**全端口**<br />选择是否开启全端口功能。开启全端口功能后，您只需要输入端口范围，NLB可以对监听端口段的所有端口进行监听，并将监听端口上接收到的请求直接转发至后端服务器的对应端口。<br />**监听端口**<br />输入监听端口，用来接收请求并向后端服务器进行请求转发的监听端口 |
| 负载均衡算法 | 选择负载均衡算法<br />1.轮询：接收到新的UDP连接后, 依次转给每个后端服务节点。<br />2.加权轮询：接收到新的UDP连接后，将根据您指定的后端服务节点的不同权重，按照概率分配给各个服务节点。<br />3.原地址哈希：根据源目的IP，使用一致性哈希算法的结果选择后端服务节点。<br />4.最小连接数：受到新的UDP连接后，会实时统计CLB到后端服务节点的连接数，选择连接数最低的服务节点建立新连接并发送数据。<br />5.加权最小连接数：了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的连接数。 |
| 服务会话保持 | 选择是否开启或关闭会话保持。默认情况下，NLB会将每个客户端请求分别分发至不同的后端服务器上。当您开启了会话保持功能后，会话保持可以使来自同一客户端的请求被转发至同一台后端服务器上，方便后端服务器维护状态信息及向客户端提供持续服务； |
| 节点健康检查 | 本文选择UDP协议，仅支持端口检查，使用后端服务器的端口进行健康检查。开启全端口转发后，健康检查端口需指定特定端口。 |
| 监听器名称   | 自定义监听器的名称。                                         |
| 备注         | 自定义监听器的备注信息。                                     |

## 创建UDP监听器

1. 登录网络型负载均衡NLB控制台。
2. 在顶部导航栏，选择NLB实例的所属地域。
3. 选择以下一种方法，打开监听配置。
   - 在**实例列表**页面，在目标实例**操作**列点击**监听器管理**。
   - 在**实例列表**页面，点击目标实例ID或者详情。在**监听器管理**页签，点击**添加**。
4. 在**创建监听器**页面，完成以下配置，然后点击**确认**。

| 配置项       | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| 协议         | 选择一种负载均衡协议，本示例选择UDP协议                      |
| 端口         | 支持全端口监听和单端口监听<br />**全端口**<br />支持全端口监听和单端口监听**全端口**选择是否开启全端口功能。开启全端口功能后，您只需要输入端口范围，NLB可以对监听端口段的所有端口进行监听，并将监听端口上接收到的请求直接转发至后端服务器的对应端口。<br />**监听端口**<br />输入监听端口，用来接收请求并向后端服务器进行请求转发的监听端口。 |
| 负载均衡算法 | 选择负载均衡算法<br />1.轮询：接收到新的UDP连接后, 依次转给每个后端服务节点。<br />2.加权轮询：接收到新的UDP连接后，将根据您指定的后端服务节点的不同权重，按照概率分配给各个服务节点。<br />3.原地址哈希：根据源目的IP，使用一致性哈希算法的结果选择后端服务节点。<br />4.最小连接数：受到新的UDP连接后，会实时统计CLB到后端服务节点的连接数，选择连接数最低的服务节点建立新连接并发送数据。<br />5.加权最小连接数：了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的连接数。 |
| 服务会话保持 | 选择是否开启或关闭会话保持。默认情况下，NLB会将每个客户端请求分别分发至不同的后端服务器上。当您开启了会话保持功能后，会话保持可以使来自同一客户端的请求被转发至同一台后端服务器上，方便后端服务器维护状态信息及向客户端提供持续服务； |
| 节点健康检查 | 本文选择UDP协议。<br />**端口检查**：使用后端服务器的端口进行健康检查。开启全端口转发后，健康检查端口需指定特定端口。<br />**Png检查**：使用Ping方式探测后端节点联通性。<br />**UDP检查**：向服务节点发送UDP请求报文，根据设置的报文判断节点是否正常。 |
| 监听器名称   | 自定义监听器的名称。                                         |
| 备注         | 自定义监听器的备注信息。                                     |

## 修改监听器

1. 登录应用型负载均衡NLB控制台。
2. 在顶部导航栏，选择NLB实例所属的地域。
3. 在NLB列表页面，找到目标NLB实例，点击实例ID，进入实例详情页。
4. 点击**监听器管理**，找到目标监听，选择以下一种方法，修改监听基本信息。
   a. 点击目标监听，在**监听器详情**页签的**基本信息**区域，点击**更改配置**。
   b. 在左侧监听器列表，选择需要编辑的监听器，点击右上角的编辑按钮，进入编辑页面。
5. 在**编辑监听器**弹窗中，您可以根据业务的需要修改监听器的配置信息，然后点击**确定，**即可完成对监听器的修改

## 删除监听器

1. 登录应用型负载均衡NLB控制台。
2. 在顶部菜单栏，选择NLB实例所属的地域。
3. 在NLB**实例**页面，找到目标NLB实例，点击实例ID。
4. 点击**监听器管理**页签，找到目标监听器，然后在右上角选择**删除**。
5. 在弹出的删除监听器弹窗中，点击**确定**。