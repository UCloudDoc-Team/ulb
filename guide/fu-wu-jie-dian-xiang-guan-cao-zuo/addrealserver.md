{{indexmenu_n>1}}

# 添加服务节点

VServer监听器创建完毕后，需要为VServer添加服务节点，才可使负载均衡正式对外提供服务。 

## 操作步骤

进入**VServer管理页面**，点击**服务节点**，进行服务节点管理。

1，VServer管理-服务节点页面，点击**添加节点**。

![](https://static.ucloud.cn/db3e5c210e184820bf3263813620d2bb.png)

2，弹窗中进行以下选择。

![](https://static.ucloud.cn/9e30eac4e08b487c800e93d56b9f0f08.png)

| 配置 | 说明 |
| - | - |
| 所属子网 | 服务节点所属的子网。可选全部子网或指定子网。 |
| 资源类型 | 服务节点的资源类型。包括云主机、物理云主机、容器。 |
| 监听端口 | 服务节点的监听端口。服务节点端口有以下限制:如果VServer监听器类型为七层ULB或者四层ULB的请求代理模式，则相同后端服务节点可添加不同端口，实现同一IP不同服务实例；如采用四层ULB的UDP协议及TCP报文转发模式，则后端服务节点的端口必须与VServer监听端口保持一致。 |
| 可选资源 | 根据所选择的信息，展示出当前可添加的服务节点资源。 |

3，在可选资源列表中，选中需要添加资源的**勾选框**，并移入右侧带添加节点列表中。

![](https://static.ucloud.cn/47c3c32ad1a0451a81662a25767fea87.png)

4，点击**确定**即完成节点添加。

![](https://static.ucloud.cn/ca55ac7d3cec46c281c409093303c787.png)

 [[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]


