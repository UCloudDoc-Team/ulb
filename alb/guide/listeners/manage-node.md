# 服务节点
# 添加服务节点

在创建监听器之后，您可以根据业务需要随时对监听器的服务节点进行启用/禁用，新增，修改或删除等操作；

1. 登录应用型负载均衡ALB控制台。
2. 在顶部导航栏，选择ALB实例所属的地域。
3. 在ALB**实例**页面，找到目标ALB实例，点击实例ID。
4. 点击**监听器管理**页签，选择的目标监听器，进入监听器详情页。
5. 进入服务节点页签，点击添加节点。

![1713867004135](/images/1713867004135.png)

6. 在添加节点页面配置如下信息

| 配置项   | 说明                                                         |
| :------- | :----------------------------------------------------------- |
| 资源类型 | 选择后端节点的资源类型，支持选择云主机，物理云主机，虚拟网卡，内网IP |
| 所属VPC  | 后端节点所在的VPC                                            |
| 所属子网 | 后端节点所在的子网                                           |
| 监听端口 | 转发的端口                                                   |
| 可选资源 | 选择可以添加的资源类型                                       |

# 服务节点管理

在创建监听器之后，您可以根据业务需要随时对监听器的服务节点进行启用/禁用，新增，修改或删除等操作；

1. 登录应用型负载均衡ALB控制台。
2. 在顶部导航栏，选择ALB实例所属的地域。
3. 在ALB**实例**页面，找到目标ALB实例，点击实例ID。
4. 点击**监听器管理**页签，选择的目标监听器，进入监听器详情页。

![1713867074558](/images/1713867074558.png)

5. 点击服务节点页签。

启用节点：
1. 勾选选择需要启用的节点，在列表左上角，点击启用。
2. 找到需要启用的服务节点，在**操作**列点击**启动**，然后在弹出的对话框中，点击**确定**。

禁用节点
1. 勾选选择需要禁用的节点，在列表页左上角，点击禁用。
2. 找到需要禁用的服务节点，在**操作**列点击**禁用**，然后在弹出的对话框中，点击**确定**。

删除节点
1. 勾选选择需要删除的节点，在列表左上角，点击删除。
2. 找到需要删除的服务节点，在**操作**列点击**删除**，然后在弹出的对话框中，点击**确定**。

添加节点
1. 在节点列表页左上角，点击添加节点。
2. 在添加节点页面，根据需求选择一种节点类型，然后点击确定。