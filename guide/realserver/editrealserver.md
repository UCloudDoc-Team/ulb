# 报文转发模式服务节点配置

“报文转发模式”下，由于用户访问会经ULB直接透传，必须保证访问地址落在后端真实服务节点上，所以要将负载均衡的内/外网IP地址配置在后端服务节点中。配置方法如下。


### CentOS/Ubuntu配置方法

| 操作系统                     | 云主机未使用cloud init                                       | 云主机未使用cloud init                                       |
| ---------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| CentOS 7及以下               | 1、创建虚拟网卡配置文件：<br>```touch /etc/sysconfig/network-scripts/ifcfg-lo:1``` <br>2、在/etc/sysconfig/network-scripts/ifcfg-lo:1增加以下配置：（若ULB绑定多个EIP，则多个EIP均需要配置）<br>```DEVICE=lo:1```<br>```IPADDR=$VIP```<br>```NETMASK=255.255.255.255```<br>3、启动虚拟网卡：<br>```ifup lo:1``` | UserData中添加以下内容：[UserData说明](https://docs.ucloud.cn/uhost/guide/metadata/userdata)<br/>```#/bin/bash```<br/> ```echo -e "DEVICE=lo:1\nIPADDR=$VIP\nNETMASK=255.255.255.255"  > /etc/sysconfig/network-scripts/ifcfg-lo:1```<br/>```ifup lo:1``` |
| CentOS 8及以上               | 1、安装network-scripts：<br>```yum install network-scripts -y```<br>2、创建虚拟网卡配置文件：<br>```touch /etc/sysconfig/network-scripts/ifcfg-lo:1``` <br>3、在/etc/sysconfig/network-scripts/ifcfg-lo:1增加以下配置：（若ULB绑定多个EIP，则多个EIP均需要配置）<br>```DEVICE=lo:1```<br>```IPADDR=$VIP```<br>```NETMASK=255.255.255.255``` <br>4、启动虚拟网卡<br>```ifup lo:1``` | UserData中添加以下内容：[UserData说明](https://docs.ucloud.cn/uhost/guide/metadata/userdata)<br/>```#!/bin/bash```<br/>```yum install network-scripts -y```<br/> ```echo -e "DEVICE=lo:1\nIPADDR=$VIP\nNETMASK=255.255.255.255"  > /etc/sysconfig/network-scripts/ifcfg-lo:1```<br/>```ifup lo:1``` |
| Ubuntu16.04                  | 1、在/etc/network/interfaces中追加以下配置：<br>```auto lo:1```<br>```iface lo:1 inet static```<br>```address $VIP```<br>```netmask 255.255.255.255```<br />2、启动虚拟网卡<br/>```sudo /etc/init.d/networking restart``` | UserData中添加以下内容：[UserData说明](https://docs.ucloud.cn/uhost/guide/metadata/userdata)<br/>```#!/bin/bash```<br/> ```echo -e "auto lo:1\niface lo:1 inet static\naddress $VIP\nnetmask 255.255.255.255">>/etc/network/interfaces```<br/>```sudo /etc/init.d/networking restart``` |
| Ubuntu18.04<br />Ubuntu20.04 | 1、在/etc/netplan/目录下创建网卡配置文件：<br /> ```sudo touch lo-cloud-init.yaml```<br />2、在文件lo-cloud-init.yaml中增加以下配置（注意每行缩进）：<br/>```network:```<br/>```ethernets:```<br/>```lo:```<br/>```addresses:```<br/>```- $vip/32```<br/>3、使配置生效<br/>```sudo netplan apply``` | UserData中添加以下内容：[UserData说明](https://docs.ucloud.cn/uhost/guide/metadata/userdata)（注意每行缩进）<br/>```#!/bin/bash```<br/>```sudo touch lo-cloud-init.yaml```<br/>```sudo echo -e "network:\n    ethernets:\n        lo:\n            addresses:\n            - $VIP/32" > /etc/netplan/lo-cloud-init.yaml```<br/>```sudo netplan apply```  |


#### 获取网卡VIP

1，内网ULB时，这里的$VIP即为负载均衡器的内网服务IP地址。
![](/images/%E8%8E%B7%E5%8F%96vip.png)

2，外网ULB时，即为负载均衡器的外网服务IP地址（即EIP）。
![](/images/ulb-vip.png)

如果您使用自动化脚本配置，我们建议您使用我们的API describe\_ulb获取您配置所需的VIP。如何调用此API请参考：

[获取负载均衡信息-DescribeULB](https://docs.ucloud.cn/api/ulb-api/describe_ulb)


### Windows配置方法

1、添加lo接口

依次在“设备管理器”中选择"网络适配器"，并在菜单栏中点击“操作”→“添加过时硬件”→“安装我从手动列表安装的硬件”。并在厂商中选择"Microsoft"，网络适配器选择“Microsoft Loopback Adapter”（注意在windows8、windows server2012及更新版本中，“Microsoft Loopback Adapter”更名为“Microsoft KM-TEST 环回适配器”）。并点击下一步完成设备创建。

![](/images/windows1.png)

![](/images/windows2.png)

2、配置lo接口

内网ULB时，lo接口的IP即为负载均衡器的内网服务IP地址。
![](/images/%E8%8E%B7%E5%8F%96vip.png)

外网ULB时，lo接口的IP为负载均衡器的外网服务IP地址（即EIP）。
![](/images/ulb-vip.png)

然后在“网络和共享中心”中，选择更改适配器设置，并配置lo接口，配置内容如图片所示：

![](/images/windows3.png)

3、激活lo接口

在“cmd”中执行以下命令，其中$LOCAL代表本地接口名称，$LO代表回环接口名称。

```
@echo off
netsh interface ipv4 set interface "$LOCAL" weakhostreceive=enabled
netsh interface ipv4 set interface "$LOCAL" weakhostsend=enabled
netsh interface ipv4 set interface "$LO" weakhostreceive=enabled
netsh interface ipv4 set interface "$LO" weakhostsend=enabled 
Pause
```

执行效果如图所示

![](/images/win4.png)

建议配置windows系统时通过VNC登陆进行操作，如以上操作未生效，可在执行完"netsh"后重启网卡或服务进行查看。

本质上讲，无论后端服务实例是何种操作系统，只要将负载均衡器的VIP配置到后端服务实例上即可。

