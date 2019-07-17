{{indexmenu_n>30}}

# ULB的会话保持是如何实现的？

## 请求代理

请求代理模式下（HTTP、HTTPS），会话保持功能是利用cookie实现的。ULB会向源端写cookie，并根据请求带有的cookie信息，直接将请求送给对应的后端主机。服务端插入指, 由负载均衡生成cookie的key. 用户定义指由用户指定特征cookie的key.

* **Cookie插入**：选择自动生成key，客户端的cookie插入操作都由ULB来分配和管理。
* **用户指定Cookie插入**：用户可自定义key，ULB使用客户的key来分配和管理对客户端进行的Cookie插入操作

> TCP协议的请求代理模式，不支持会话保持。


## 报文转发

报文转发模式下（TCP、UDP），会话保持功能是基于IP地址的会话保持。ULB会将来自同一IP地址的访问请求转发到同一台后端云服务器进行处理。

 [[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
