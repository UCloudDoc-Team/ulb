

# 获取监控指标

## 操作步骤

进入**负载均衡 ULB页面**，选择需要查看的ULB实例，进入**详情**。

### ULB监控

1，进入概览页面，**外网ULB**会在显示绑定在ULB上EIP的详细信息和监控信息。

![](/images/ulbmonitor_new1.png)

### VServer监控

进入VServer管理页面，选中VServer，右侧概览页面显示监控信息。

不同类型VServer支持的监控指标如下：

| 监控指标\VServer监听协议 | HTTPS | HTTP | TCP（请求代理）|TCP（报文转发）| UDP |指标说明|
| --- | --- | --- | --- | --- | --- |--- |
| 新建连接数（个/s）| √  | √ | √ | √ | √ | VServer每秒新建连接个数|
| VServer连接数（个/s） | √  | √ | √ | √ | √ | VServer已有连接数 |
| 网卡入包量(个/s) | ×  | × | × | √| √ | VServer每秒入包量 |
| 网络入口(bps) | ×  | × | × | √ | √ | VServer每秒入流量 |
| HTTP 2XX(个/s) | √  | √ | × | × | × | VServer每秒返回的2XX状态码数量|
| HTTP 3XX(个/s) | √  | √ | × | × | × | VServer每秒返回的3XX状态码数量 |
| HTTP 4XX(个/s) | √  | √ | × | × | × | VServer每秒返回的4XX状态码数量 |
| HTTP 5XX(个/s) | √  | √ | × | × | × |VServer每秒返回的5XX状态码数量  |
| HTTP其他返回码(个/s) | √  | √ | × | × | × | VServer每秒返回的其他状态码数量 |







