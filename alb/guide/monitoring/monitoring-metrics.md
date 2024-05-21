# ALB监控项说明

当您的ALB遇到请求超时、流量限速等网络问题，或您希望深入了解ALB的负载状况与性能表现时，可以通过监控ALB的关键指标，实现实时追踪、精准分析和迅速定位问题，从而确保服务的稳定与高效运行。

# 实例监控（内网）

| 监控项           | 说明                                         |
| :--------------- | :------------------------------------------- |
| 内网入向带宽监控 | 客户端通过内网访问负载均衡实例所用的带宽均值 |
| 内网出向带宽     | 负载均衡访问内网所用的带宽均值。             |
| 内网出向发包数   | 负载均衡通过内网向客户端发送的数据包数量。   |
| 内网入向发包数   | 客户端通过内网向负载均衡发送的数据包数量。   |

# 实例监控（外网）

| 监控项         | 说明                                             |
| :------------- | :----------------------------------------------- |
| 网络入口       | 客户端通过外网访问负载均衡所用的带宽均值。       |
| 网络出口       | 负载均衡访问外网所用的带宽均值。                 |
| 入口带宽使用率 | 客户端通过外网访问负载均衡所用的带宽利用率。     |
| 出口带宽使用率 | 负载均衡访问外网所用的带宽使用率。               |
| 出向峰值带宽   | 负载均衡访问外网所用的带宽峰值。                 |
| 入向峰值带宽   | 客户端通过外网访问负载均衡所用的带宽峰值。       |
| 出向发包数     | 负载均衡通过外网向客户端发送的数据包数量。       |
| 入向发包数     | 客户端通过外网向负载均衡发送的数据包数量。       |
| 出向丢包数     | 负载均衡访问外网时丢弃的数据包。                 |
| 入向丢包数     | 客户端通过外网访问负载均衡时丢弃的数据包。       |
| 出向丢包百分比 | 负载均衡访问客户端时丢弃的数据包占总出包量的占比 |
| 入向丢包百分比 | 客户端访问负载均衡时丢弃的数据包占总出包量的占比 |

# 监听器监控

| 监控项           | 说明                                                   |
| :--------------- | :----------------------------------------------------- |
| Listener 连接数  | 从客户端到监听器上的活跃连接数                         |
| 新建连接数       | 从客户端到监听器上的新建连接数。                       |
| HTTP 2XX         | 负载均衡返回 2xx 状态码的个数                          |
| HTTP 3XX         | 负载均衡返回 3xx 状态码的个数                          |
| HTTP 4XX         | 负载均衡返回 4xx 状态码的个数                          |
| HTTP 5XX         | 负载均衡返回 5xx 状态码的个数                          |
| HTTP其他返回码   | 负载均衡返回 除5xx，3xx，2xx，4xx之外其他 状态码的个数 |
| 每秒请求数       | 负载均衡的请求数。                                     |
| 节点失效百分比   | 监听器的健康检查异常个数占总节点数的百分比             |
| 平均请求时间     | 负载均衡的平均请求时间                                 |
| 后端平均响应时间 | 负载均衡后端服务节点的平均响应时间                     |