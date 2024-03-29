# 绑定/解绑安全策略

当前安全策略功能仅支持在请求代理型 ULB 下HTTPS协议的 VServer 中使用。

> 安全策略功能目前还只在部分地域进行公测，如果ULB实例还未公测，将无法绑定使用创建好的安全策略，有需要请联系技术支持。

## 绑定安全策略

1、进入**VServer 管理页面**，点击**添加 VServer**或者**更改 VServer**，进行 VServer 配置设置。

2、协议选择**HTTPS**，点击**安全策略**后面的下拉框，选择预定义或自定义的安全策略。

![](/images/绑定安全策略.png)

## 解绑安全策略

1、进入**VServer 管理页面**，点击**更改 VServer**，进行 VServer 配置设置。

2、点击**安全策略**后面的下拉框，选择**原生策略**，即可解绑已经绑定的预定义或自定义的安全策略。原生策略详见[安全策略](/ulb/guide/securitypolicy/securitypolicy)。

![](/images/解绑安全策略.png)

## 解绑全部VServer

1、进入**负载均衡 ULB**页面，点击**安全策略管理**。

2、选择需要解绑的安全策略，点击**解绑全部 VServer**。

![](/images/解绑全部VServer.png)

3、弹出弹窗展示选中的安全策略信息，确认是否是要解绑该安全策略的全部VServer。

4、点击**确定**，完成解绑操作。
