{{indexmenu_n>4}}

# 报文转发模式服务节点配置

## 操作步骤

“报文转发模式”下，由于用户访问会经ULB直接透传，必须保证访问地址落在后端真实服务节点上，所以要将负载均衡的内/外网IP地址配置在后端服务节点中。配置方法如下。

### CentOS中的配置方法

1、创建虚拟网卡配置文件

```
# touch /etc/sysconfig/network-scripts/ifcfg-lo:1
```

2、获取网卡VIP 您可以在管理控制台概览页查看到我们的VIP，如下图所示

![](https://docs.ucloud.cn/_media/network/ulb/%E8%8E%B7%E5%8F%96vip.png)

如果您使用自动化脚本配置，我们建议您使用我们的API describe\_ulb获取您配置所需的VIP。如何调用此API请参考：

[获取负载均衡信息-DescribeULB](https://docs.ucloud.cn/api/ulb-api/describe_ulb)

内网ULB时，这里的$VIP即为负载均衡器的内网服务IP地址。外网ULB时，即为负载均衡器的外网服务IP地址（即EIP）。

3、将命令中得到的内容添加进"/etc/sysconfig/network-scripts/ifcfg-lo:1"中，即如下内容：

```
DEVICE=lo:1
IPADDR=$VIP
NETMASK=255.255.255.255
```

4、启动虚拟网卡

```
# ifup lo:1
```

### Ubuntu中的配置方法

1、获取服务IP地址 您可以在管理控制台概览页查看到对应的ULB服务IP地址，如下图所示

![](https://docs.ucloud.cn/_media/network/ulb/%E8%8E%B7%E5%8F%96vip.png)

若使用自动化脚本配置，可使用API describe\_ulb获取服务IP地址。如何调用此API请参考：

[获取负载均衡信息-DescribeULB](https://docs.ucloud.cn/api/ulb-api/describe_ulb)

内网ULB时，这里的$VIP即为负载均衡器的内网服务IP地址。外网ULB时，即为负载均衡器的外网服务IP地址（即EIP）。

2、将命令中得到的内容添加进"/etc/network/interfaces"中，即如下内容：

```
auto lo:1
iface lo:1 inet static
address $VIP
netmask 255.255.255.255
```

在Ubuntu系统中，/etc/network/interfaces文件本身存在内容，请勿清空。

3、启动虚拟网卡

```
# ifup lo:1
```

### Windows中的配置方法

1、添加lo接口

依次在“设备管理器”中选择"网络适配器"，并在菜单栏中点击“操作”→“添加过时硬件”→“安装我从手动列表安装的硬件”。并在厂商中选择"Microsoft"，网络适配器选择“Microsoft Loopback Adapter”（注意在windows8、windows server2012及更新版本中，“Microsoft Loopback Adapter”更名为“Microsoft KM-TEST 环回适配器”）。并点击下一步完成设备创建。

![](https://docs.ucloud.cn/_media/network/ulb/win1.png)

![](https://docs.ucloud.cn/_media/network/ulb/win2.png)

2、配置lo接口

在“网络和共享中心”中，选择更改适配器设置，并配置lo接口，配置内容如图片所示：

![](https://docs.ucloud.cn/_media/network/ulb/win3.png)

图中10.10.94.111的地址，即为负载均衡器的内网服务IP地址。

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

![](https://docs.ucloud.cn/_media/network/ulb/win4.png)

建议配置windows系统时通过VNC登陆进行操作，如以上操作未生效，可在执行完"netsh"后重启网卡或服务进行查看。

本质上讲，无论后端服务实例是何种操作系统，只要将负载均衡器的VIP配置到后端服务实例上即可。

 [[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
