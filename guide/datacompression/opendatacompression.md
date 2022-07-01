# 开启数据压缩

当前数据压缩功能仅支持 **请求代理型 ULB 的 HTTP/HTTPS 协议**下的 gzip 压缩，开启后降低流量消耗。

> 数据压缩功能目前还只在部分地域进行公测，有需要请联系技术支持。

## 操作步骤

1、进入**VServer 管理页面**，点击**添加 VServer**或者**更改 VServer**，进行 VServer 配置设置。

2、协议选择**HTTP 或 HTTPS**，点击**数据压缩**后面的按钮，停留在状态**ON**。

![](/images/开启数据压缩.png)

3、如果您选择开启**数据压缩**，那么开启后请求头需要带有：

```
Accept-Encoding: gzip
```

则响应头会带有：

```
Content-Encoding: gzip
```

## 支持文件类型

数据压缩仅支持以下特定文件类型：

```
text/xml
text/plain
text/css
application/javascript
application/x-javascript
application/rss+xml
application/atom+xml
application/xml
application/json
```
