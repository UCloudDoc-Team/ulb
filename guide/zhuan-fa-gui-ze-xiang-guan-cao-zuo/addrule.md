{{indexmenu_n>1}}

# 添加内容转发规则

HTTP/HTTPS协议下，VServer支持根据转发策略匹配域名或访问路径，能够将匹配请求转发到后端特定主机，对后端服务节点进行精细化管理默认情况下，会存在一条叫做**默认规则**的策略，该策略在所有请求均未匹配成功时生效，会按照通常的转发规则进行转发。

> TCP/UDP协议暂不支持内容转发策略。


## 操作步骤

进入**VServer管理页面**，点击**内容转发**，进行内容转发规则管理。

1，点击**添加规则**，弹出添加规则弹窗。

![](https://static.ucloud.cn/b094d66652b0429d9371919d5ebe9c5d.png)


2，**转发规则**。转发规则分为“域名转发”与“路径转发”两种，这两种转发方式均可使用正则表达式或通配符进行描述，如“www.\[123\].demo.com”或“/path/img/\*.jpg”，创建规则时规则内容不可为空。

3，**可选节点**。每条规则均需要与已有的服务节点进行关联，选择需要关联的节点。

4，点击**确认**，即完成添加转发规则

![](https://static.ucloud.cn/21e20e38813d4d95b6c8b105f951bf50.png)

[[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]

