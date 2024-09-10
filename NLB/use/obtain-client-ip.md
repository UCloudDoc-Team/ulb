# 使用 Toa 获取源 IP

NLB 目前支持通过 Toa 获取客户端源 IP，使用 Toa 模块需要在 NLB 的 Listener 和 RealServer 主机上分别进行配置。

## **前提条件**

- 创建一个 NLB，创建一个 Listener 端口为 80
- 创建一台 云主机，本文以 centos7 为例
- 将云主机挂载在 NLB 下

## **操作流程**

### 一、打开 NLB Toa 功能

1. 点击监听器管理、更改配置

![图片注释](/images/image.png)

2. 打开 Toa 功能，提交更新

![图片注释](/images/image (1).png)

3. 可以在此处查看 Toa 是否开启

![图片注释](/images/image (2).png)

### 二、RealServer 主机安装 Toa 模块

1. Toa 模块获取：
2. 将 toa.ko 文件上传至 RealServer
3. 安装 toa 模块

```Plain
# 安装 Toa 模块
insmod toa.ko

# 查看安装是否成功
lsmod | grep toa

# 卸载 Toa 模块
rmmod toa
```

### 三、检查 Toa 是否生效

使用 nginx 可以快捷查看源 IP，判断 Toa 是否生效。

1. 安装 nginx

```Plain
yum install -y nginx
```

1. 启动 nginx，默认监听 80 端口

```Plain
systemctl start nginx
```

1. 查找 nginx access.log 文件位置

```Plain
find / -name access.log
```

1. 监听文件内容

```Plain
watch cat /var/log/nginx/access.log
```

如果安装成功，此处可以正确看到 client 端 IP

![图片注释](/images/image (3).png)

