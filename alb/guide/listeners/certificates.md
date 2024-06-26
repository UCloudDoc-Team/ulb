# 监听证书

在创建HTTPS监听时，支持用户绑定HTTPS证书。

# 绑定证书

1. 登录应用型负载均衡ALB控制台。
2. 在顶部菜单栏，选择ALB实例的所属地域。
3. 选择以下一种方法，打开监听配置。
   1. 在**实例列表**页面，在目标实例**操作**列点击**监听器管理**。
   2. 在**实例列表**页面，点击目标实例ID或者详情。在**监听器管理**页签，进入监听器详情页。
4. 在**监听器详情**页面，选择监听证书页签。

![1713862970075](/images/1713862970075.png)

5. 点击左上角**绑定证书**，在绑定证书页面选择需要添加的证书，点击确定。

# 解绑证书

在创建HTTPS监听时选择的证书为默认证书，默认正式仅支持更换，不支持解绑。

1. 登录应用型负载均衡ALB控制台。
2. 在顶部菜单栏，选择ALB实例的所属地域。
3. 选择以下一种方法，打开监听配置。
   1. 在**实例列表**页面，在目标实例**操作**列点击**监听器管理**。
   2. 在**实例列表**页面，点击目标实例ID或者详情。在**监听器管理**页签，进入监听器详情页。
4. 在**监听器详情**页面，选择监听证书页签。
5. 选择自己需要解绑的证书，点击**解绑**按钮。

![1713863517491](/images/1713863517491.png)

​	6. 在弹出的确认解绑弹窗中，点击确定按钮，即可完成解绑。

# SNI证书

HTTPS监听器支持绑定多个证书，实现同一个监听器根据多个域名自动选择证书来完成HTTPS认证和访问后端的诉求。负载均衡收到HTTPS请求后，会根据域名去查找证书，如果找到域名对应的证书，则返回该证书；如果没有找到域名对应的证书，则返回默认证书。

## 使用限制

- 一个实例最多支持绑定25个SNI证书，不包含默认证书。
- 一个证书只能绑定监听器一次，不能重复绑定。

## SNI证书匹配规则

- 如果客户端发出的请求与证书列表中的一个证书匹配，则ALB将选择此证书。如果客户端发出的请求与证书列表中的多个证书匹配，则负载均衡器根据绑定的时间来判断优先级，绑定时间最新的证书，优先级越高。
- 如果没有匹配到对应域名的证书，则会匹配默认证书，默认证书，不支持删除，仅支持更改绑定。