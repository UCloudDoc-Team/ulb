[前往 Github](https://github.com/UCloudDocs/UCloud-document/tree/master/network/ulb)

{{indexmenu_n>7}}

# 性能指标

## ULB性能指标

* 每秒新建连接数（CPS）：每秒新建连接的数量，体现处理新增连接的能力。
* 最大并发连接数：每秒连接的总数量，体现并发处理连接的能力。
* 每秒处理包量（PPS）：每秒钟转发的包量，体现包转发速率。
* 最大吞吐量：可支持的带宽。
* 每秒请求量（QPS）：每秒查询的数量，QPS对于ULB不是核心指标，真正消耗性能的是CPS。短连接情况，QPS=CPS；长连接情况，QPS>CPS。

| 产品 | 模式 | 每秒新建连接（cps）| 最大并发连接（个） | 最大吞吐量（bps） | 每秒处理包量(pps) |
| - | - | - | - | - | - |
| 外网ULB | 四层 | 600,000 | 100,000,000 | 30G | 18,000,000 |
| 外网ULB | 七层 | 40,000（4,000 ssl） | 300,000 | 800M | 400,000 |
| 内网ULB | 四层 | 600,000 | 100,000,000 | 30G | 21,000,000 |

 [[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
