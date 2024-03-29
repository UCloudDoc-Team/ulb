# 开启日志

访问日志能够帮助你了解客户端的行为、地域分布，并提供访问路径信息，帮助排查故障。

> 1、仅请求代理类型CLB支持日志功能。
> 
> 2、日志管理本身不收取费用，但日志需存储在US3中，需支付对应使用费用。[US3产品价格](https://docs.ucloud.cn/ufile/bill/billing)
> 
> 3、开启日志后会有10%的性能损耗。

## 操作步骤

1、在CLB列表页点击**CLB名称**或者**详情**进入到实例详情页面。

2、在CLB概览页面，**基本信息**模块点击**日志管理**后面的编辑图标，开启**访问日志**。

![](/images/ulblog.png)

3、选择存储日志的US3存储空间和令牌，点击确认。

![](/images/ulblog2.png)


```
日志需要存储在本地域US3存储空间中，所以需先开启US3权限，并创建CLB实例所在地域的存储空间。

日志5分钟生成一个日志文件，并存储在所选的存储空间中。
```

## 日志解析

#### HTTP/HTTPS协议日志

内网CLB

```
192.168.5.198 - - [24/Feb/2021:17:33:21 +0800] 200 5068 18070 192.168.5.208:8080 "" "curl/7.29.0" - - 192.168.5.30:80 2 ms 3 ms "GET / HTTP/1.1"

客户端ip -- [本地时间] 状态码 服务端返回客户端的字节大小 客户端端口 CLB的ip:CLB的端口 "http_referer"(没有则为""或"-") "http_user_agent"(没有则为""或"-") ssl_version(没有则为-) ssl_ciphers(没有则为-) rs服务ip:rs服务端口 响应时间 请求时间 "请求"
```

外网CLB

外网有两种格式，差异在rs服务ip和rs服务端口那。

格式一：

```
117.50.92.198 - - [24/Feb/2021:18:19:19 +0800] 200 5068 35504 117.50.92.208:443 "" "curl/7.29.0" TLSv1.2 ECDHE-RSA-AES256-GCM-SHA384 rs_192.168.5.30:80_670054 2 ms 3 ms "GET / HTTP/1.1"

客户端ip -- [本地时间] 状态码 服务端返回客户端的字节大小 客户端端口 CLB的ip:CLB的端口 "http_referer"(没有则为""或"-") "http_user_agent"(没有则为""或"-") ssl_version(没有则为-) ssl_ciphers(没有则为-) rs名称(rs_rs服务ip:rs服务端口_编号) 响应时间 请求时间 "请求"
```

格式二：

```
117.50.92.198 - - [24/Feb/2021:18:19:19 +0800] 200 5068 35504 117.50.92.208:443 "" "curl/7.29.0" TLSv1.2 ECDHE-RSA-AES256-GCM-SHA384 192.168.5.30:80 2 ms 3 ms "GET / HTTP/1.1"

客户端ip -- [本地时间] 状态码 服务端返回客户端的字节大小 客户端端口 CLB的ip:CLB的端口 "http_referer"(没有则为""或"-") "http_user_agent"(没有则为""或"-") ssl_version(没有则为-) ssl_ciphers(没有则为-) rs服务ip:rs服务端口 响应时间 请求时间 "请求"
```

#### TCP协议日志

内网CLB
```
192.168.5.198 - - [25/Feb/2021:11:52:38 +0800] 5073 45508 192.168.5.238:80 192.168.5.30:80

客户端ip -- [本地时间] 服务端返回客户端的字节大小 客户端端口 CLB的ip:CLB的端口 rs服务ip:rs服务端口
```

外网CLB

外网有两种格式，差异在CLB的ip和CLB的端口以及rs服务ip和rs服务端口。

格式一：

```
117.50.92.198 - - [25/Feb/2021:11:52:38 +0800] 5073 45508 FE_106.75.33.238:80 rs_192.168.5.30:80_665936

客户端ip -- [本地时间] 服务端返回客户端的字节大小 客户端端口 服务名称(FE_服务ip:服务端口) rs名称(rs_rs服务ip:rs服务端口_编号)
```

格式二：

```
117.50.92.198 - - [25/Feb/2021:11:52:38 +0800] 5073 45508 106.75.33.238:80 192.168.5.30:80

客户端ip -- [本地时间] 服务端返回客户端的字节大小 客户端端口 CLB的ip:CLB的端口 rs服务ip:rs服务端口
```

