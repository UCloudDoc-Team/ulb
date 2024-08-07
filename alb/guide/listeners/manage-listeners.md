# 监听器管理

# 创建HTTP监听器

监听器是用于检查来自客户端的连接请求。如果您的业务需要对数据内容进行识别，可以添加一个HTTP监听器，转发来自客户端HTTP协议的请求。

1. 登录应用型负载均衡ALB控制台。
2. 在顶部导航栏，选择ALB实例的所属地域。
3. 选择以下一种方法，打开监听配置。
   1. 在**实例列表**页面，在目标实例**操作**列点击**监听器管理**。
   2. 在**实例列表**页面，点击目标实例ID或者详情。在**监听器管理**页签，点击**添加监听**。

![1713866179936](/images/1713866179936.png)

4. 在**创建监听器**页面，完成以下配置，然后点击**确认**。

| 配置项       | 说明                                                         |
| :----------- | :----------------------------------------------------------- |
| 协议         | 选择监听的协议类型，本示例选择HTTP                           |
| 端口         | 输入用来接收请求并向后端服务器进行请求转发的监听端口，端口范围为1~65535。同一个ALB实例内，监听端口不能重复。 |
| 负载均衡算法 | 选择一种负载均衡的调度算法： 轮询：将用户的请求轮流分配给后端服务器。源地址：相同的源地址的客户端会调度到相同的后端服务器；加权轮询：将用户的请求轮流分配给后端服务器，权重值越高的后端服务器，被轮询到的次数也越多。最小连接：根据后端服务器的连接数转发用户请求，当前连接数越小的后端服务器被轮询到的次数也越多主备：将后端服务器分为主节点和备节点，用户的请求会分配给主节点，当主节点异常后，才会将用户的请求转发到备节点。 |
| 服务节点     | 支持稍后设置服务节点和复制当前实例下其他监听器的服务节点     |
| 服务会话保持 | 选择是否开启或关闭会话保持。默认情况下，ALB会将每个客户端请求分别分发至不同的后端服务器上。当您开启了会话保持功能后，会话保持可以使来自同一客户端的请求被转发至同一台后端服务器上，方便后端服务器维护状态信息及向客户端提供持续体验；自动生成KEY：客户端第一次访问时，ALB会在set-cookie响应头中返回Cookie，在是会话保持期间，客户端携带此Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器上。用户定义KEY：当ALB发现用户自定义了Cookie，将会对原来的Cookie进行重写，会话保持期间携带重写后的Cookie进行访问，ALB会将请求定向转发给之前记录的后端服务器。 |
| 连接空闲超时 | 指定连接空闲超时时间，默认取值范围为60秒；在超时时间内一直没有访问请求，ALB会暂时中断当前连接，直到下一次请求来临时重新建立新的连接。 |
| 节点健康检查 | 选择节点健康检查的方式；端口检查：使用后端服务器的端口进行健康检查。HTTP检查：发送HEAD请求模拟浏览器的访问行为来检查服务器应用是否健康。 |
| 数据压缩     | 开启该配置会对gzip文件类型进行压缩。                         |
| 重定向       | 开启后，访问当前监听器的请求将被强制跳转为访问目的监听器的请求。 |
| 监听器名称   | 输入监听器名称。                                             |
| 备注         | 输入监听器的备注信息。                                       |

# 创建HTTPS监听器

如果您的应用数据传输有安全性的需求，您可以创建使用加密连接的HTTPS监听器，用于转发来自HTTPS协议的请求，可以有效保障数据传输的机密性和完整性。

1. 登录应用型负载均衡ALB控制台。
2. 在顶部导航栏，选择ALB实例的所属地域。
3. 选择以下一种方法，打开监听配置。
   1. 在**实例列表**页面，在目标实例**操作**列点击**监听器管理**。
   2. 在**实例列表**页面，点击目标实例ID或者详情。在**监听器管理**页签，点击**添加监听**。

![1713866215318](/images/1713866215318.png)

4. 在**创建监听器**页面，完成以下配置，然后点击**确认**。

| 配置项       | 说明                                                         |
| :----------- | :----------------------------------------------------------- |
| 协议         | 选择监听的协议类型，本示例选择HTTPS                          |
| 启用HTTP 2.0 | 选择是否开启HTTP 2.0。                                       |
| SSL证书      | 选择SSL证书，如果您有多域名访问或挂载多个服务器证书的需求，配置完HTTPS监听后，您可以选择为该HTTPS监听添加扩展证书 |
| 端口         | 输入用来接收请求并向后端服务器进行请求转发的监听端口，端口范围为1~65535。同一个ALB实例内，监听端口不能重复。 |
| 负载均衡算法 | 选择一种负载均衡的调度算法： 轮询：将用户的请求轮流分配给后端服务器。源地址：相同的源地址的客户端会调度到相同的后端服务器；加权轮询：将用户的请求轮流分配给后端服务器，权重值越高的后端服务器，被轮询到的次数也越多。最小连接：根据后端服务器的连接数转发用户请求，当前连接数越小的后端服务器被轮询到的次数也越多主备：将后端服务器分为主节点和备节点，用户的请求会分配给主节点，当主节点异常后，才会将用户的请求转发到备节点。 |
| 服务节点     | 支持稍后设置服务节点和复制当前实例下其他监听器的服务节点     |
| 安全策略     | 选择需要绑定的安全策略，更多信息，请参见[TLS安全策略](https://docs.ucloud.cn/ulb/guide/securitypolicy/securitypolicy)。 |
| 服务会话保持 | 选择是否开启或关闭会话保持。默认情况下，ALB会将每个客户端请求分别分发至不同的后端服务器上。当您开启了会话保持功能后，会话保持可以使来自同一客户端的请求被转发至同一台后端服务器上，方便后端服务器维护状态信息及向客户端提供持续体验；自动生成KEY：客户端第一次访问时，ALB会在set-cookie响应头中返回Cookie，在是会话保持期间，客户端携带此Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器上。用户定义KEY：当ALB发现用户自定义了Cookie，将会对原来的Cookie进行重写，会话保持期间携带重写后的Cookie进行访问，ALB会将请求定向转发给之前记录的后端服务器。 |
| 连接空闲超时 | 指定连接空闲超时时间，默认取值范围为60秒；在超时时间内一直没有访问请求，ALB会暂时中断当前连接，直到下一次请求来临时重新建立新的连接。 |
| 节点健康检查 | 选择节点健康检查的方式；端口检查：使用后端服务器的端口进行健康检查。HTTP检查：发送HEAD请求模拟浏览器的访问行为来检查服务器应用是否健康。 |
| 数据压缩     | 开启该配置会对gzip文件类型进行压缩。                         |
| 监听器名称   | 输入监听器名称。                                             |
| 备注         | 输入监听器的备注信息。                                       |

# 修改监听器

1. 登录应用型负载均衡ALB控制台。
2. 在顶部导航栏，选择ALB实例所属的地域。
3. 在ALB列表页面，找到目标ALB实例，点击实例ID，进入实例详情页。
4. 点击**监听器管理**，找到目标监听，选择以下一种方法，修改监听基本信息。
   1. 点击目标监听，在**监听器详情**页签的**基本信息**区域，点击**更改配置**。

![1713866278323](/images/1713866278323.png)

​			2. 在左侧监听器列表，选择需要编辑的监听器，点击右上角的编辑按钮，进入编辑页面

![1713866330274](/images/1713866330274.png)

1. 在**编辑监听器**对话框中，您可以根据业务的需要修改监听器的配置信息，然后点击**保存，**即可完成对监听器的修改

# 删除监听器

1. 登录应用型负载均衡ALB控制台。
2. 在顶部菜单栏，选择ALB实例所属的地域。
3. 在ALB**实例**页面，找到目标ALB实例，点击实例ID。
4. 点击**监听器管理**页签，找到目标监听器，然后在右上角选择**删除**。

![1713866368201](/images/1713866368201.png)

5. 在弹出的删除监听器对话框中，点击**确定**。