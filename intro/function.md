[前往 Github](https://github.com/UCloudDocs/UCloud-document/tree/master/network/ulb)

{{indexmenu_n>3}}

# 产品功能

## 功能概览

| 产品功能 | 外网ULB | 内网ULB | 描述 |
| - | - | - |- |
| 四层转发（TCP／UDP） | ✔ | ✔ |  |
| 七层转发（HTTP／HTTPS） | ✔ | — |  |
| 负载均衡算法 | 轮询、源地址哈希、加权轮询、最小连接 | 轮询、源地址哈希、一致性哈希、最小连接 |  |
| 健康检查 | ✔ | ✔ | 根据规则对后端服务节点进行健康检查，自动隔离异常服务节点，一旦发现问题，迅速将问题节点切换，确保服务可用性。 |
| 会话保持 | ✔ | ✔ | 支持会话保持，用户可将其请求转发到同一台后端服务节点上。 |
| 跨可用区容灾 | ✔ | ✔ | 支持绑定不同可用区的后端服务节点，实现跨可用区容灾 |
| 外网防火墙 | ✔ | — | 支持绑定外网防火墙，实现对访问源端的黑白名单管理 |
| 域名转发 | ✔ | — | 支持按照访问域名和URL转发流量到不同的后端节点 |
| 证书管理 | ✔ | — | 支持HTTPS证书管理 |
| SSL Offloading | ✔ | — | 支持HTTPS SSL Offloading |
| WebSocket | ✔ | ✔ | 支持WebSocket协议 |
| IPv6地址支持 | ✔ | — | 支持转发IPv6流量 |
| HTTP/2 | — | — | 暂不支持HTTP/2 |
| 重定向 | — | — | 暂不支持HTTP访问重定向至HTTPS |
| 双向认证 | — | — | 暂不支持HTTPS双向认证 |

 [[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]


