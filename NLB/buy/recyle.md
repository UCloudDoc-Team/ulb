# 回收策略

本文主要介绍网络型负载均衡NLB回收及通知流程，避免因资源过期回收对业务产生影响。

## 按月/按年购买资源

当您的资源过期前3天：给您设置的通知接收人发送资源即将过期预警；

当您的资源过期当天：给您设置的通知接收人发送资源已过期通知；

当您的资源过期后3天：给您设置的通知接收人发送资源即将被停服提醒；

当您的资源过期后10天：给您设置的通知接收人发送资源即将被回收提醒，当天对资源执行回收操作（回收后的资源不可找回，请及时续费）。

## 按时购买资源

当您的资源过期后当天：发送已过期提醒；

当您的资源过期第1天：发送资源即将被回收通知；

当您的资源过期后第2天：发送回收通知，并回收资源。

