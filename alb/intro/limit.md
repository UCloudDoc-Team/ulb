# 使用限制

## 服务节点
- 代理IP会从指定的子网地址空间内分配，需保证服务节点上配置的安全规则是将代理所在的子网网段设置为放行。

## HTTP报文头限制
ALB默认报文头大小为8K。配置时需确保HTTP报文头大小不超过8K，否则会造成实例无法正常工作。

## 产品配额
| 配额名称                | 配额    | 
| ------------------- | ------- | 
单实例可绑定EIP数|30|
单地域可创建实例数|200|
单实例可添加监听器数|50|
单实例可添加的转发规则数（不包括默认规则）|100|
单实例可添加服务节点数|300|

