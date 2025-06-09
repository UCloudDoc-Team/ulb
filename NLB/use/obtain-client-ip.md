# 最佳实践

## **使用TOA功能获取源IP**

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

![图片注释](/images/image1.png)

3. 可以在此处查看 Toa 是否开启

![图片注释](/images/image2.png)

### 二、RealServer 主机安装 Toa 模块

<mark>注意事项</mark>

* 如果是⾮root⽤户，需拥有sudo权限。
* 建议您先在测试环境中执⾏本⽂的操作，观察环境稳定后再在正式环境中进⾏配置。
* 如果您的操作系统中⾃带TOA模块，建议您提前备份，如果出现重启失败，可以切换到原有内核执⾏系统恢复。
* ⽹络连接通过TOA模块转换，TOA模块是部署在旁路的，因此对⽹络性能⼏乎没有影响。
* Linux升级内核后，会导致现有TOA模块不匹配，因此每次升级内核都需要重新编译、安装TOA模块。
* **Ubuntu 18.04 镜像请先升级内核**

```bash
$ mkdir kernel
$ cd kernel

$ wget http://gpu.cn-bj.ufileos.com/linux-headers-4.15.1-041501-generic_4.15.1-041501.201802031831_amd64.deb
$ wget http://gpu.cn-bj.ufileos.com/linux-headers-4.15.1-041501_4.15.1-041501.201802031831_all.deb
$ wget http://gpu.cn-bj.ufileos.com/linux-image-4.15.1-041501-generic_4.15.1-041501.201802031831_amd64.deb

$ sudo dpkg -i *.deb
$ sudo reboot
$ uname -r
4.15.1-041501-generic
```

#### 方案一：直接获取 toa.ko (推荐)

**CentOS 下载链接**

* Centos 8.4 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS8_4U/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS8_4U/toa.ko)
* Centos 8.3 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS8_3U/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS8_3U/toa.ko)
* Centos 8.2 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS8_2U/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS8_2U/toa.ko)
* Centos 8.0 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS8_0U/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS8_0U/toa.ko)
* Centos 7.9 标准：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_9/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_9/toa.ko)
* Centos 7.9 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko)
* Centos 7.8 标准：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_8/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_8/toa.ko)
* Centos 7.8 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko)
* Centos 7.6 标准：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_6/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_6/toa.ko)
* Centos 7.6 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko)
* Centos 7.5 标准：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7\_1%267\_2%267\_3%267\_5/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_1%267_2%267_3%267_5/toa.ko)
* Centos 7.5 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko)
* Centos 7.4 标准：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_4/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_4/toa.ko)
* Centos 7.4 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko)
* Centos 7.3 标准：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7\_1%267\_2%267\_3%267\_5/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_1%267_2%267_3%267_5/toa.ko)
* Centos 7.3 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko)
* Centos 7.2 标准：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7\_1%267\_2%267\_3%267\_5/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_1%267_2%267_3%267_5/toa.ko)
* Centos 7.2 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_xU/toa.ko)
* Centos 7.1 标准：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7\_1%267\_2%267\_3%267\_5/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_1%267_2%267_3%267_5/toa.ko)
* Centos 7.0 标准：[https://nlb.cn-sh2.ufileos.com/toa/CentOS7_0/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS7_0/toa.ko)
* Centos 6.10 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS6_xU/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS6_xU/toa.ko)
* Centos 6.9 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS6_xU/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS6_xU/toa.ko)
* Centos 6.5 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS6_xU/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS6_xU/toa.ko)
* Centos 6.4 快杰：[https://nlb.cn-sh2.ufileos.com/toa/CentOS6_xU/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/CentOS6_xU/toa.ko)

**Ubuntu 下载链接**

* Ubuntu 24.04 快杰：[https://nlb.cn-sh2.ufileos.com/toa/Ubuntu24_04U/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/Ubuntu24_04U/toa.ko)
* Ubuntu 22.04 快杰：[https://nlb.cn-sh2.ufileos.com/toa/Ubuntu22_04U/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/Ubuntu22_04U/toa.ko)
* Ubuntu 20.04 快杰：[https://nlb.cn-sh2.ufileos.com/toa/Ubuntu20_04U/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/Ubuntu20_04U/toa.ko)
* Ubuntu 18.04 标准：[https://nlb.cn-sh2.ufileos.com/toa/Ubuntu18_04/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/Ubuntu18_04/toa.ko)
* Ubuntu 18.04 快杰：[https://nlb.cn-sh2.ufileos.com/toa/Ubuntu14\_04U%2616\_04U%2618\_04U/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/Ubuntu14_04U%2616_04U%2618_04U/toa.ko)
* Ubuntu 16.04 标准：[https://nlb.cn-sh2.ufileos.com/toa/Ubuntu16_04/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/Ubuntu16_04/toa.ko)
* Ubuntu 16.04 快杰：[https://nlb.cn-sh2.ufileos.com/toa/Ubuntu14\_04U%2616\_04U%2618\_04U/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/Ubuntu14_04U%2616_04U%2618_04U/toa.ko)
* Ubuntu 14.04 快杰：[https://nlb.cn-sh2.ufileos.com/toa/Ubuntu14\_04U%2616\_04U%2618\_04U/toa.ko](https://nlb.cn-sh2.ufileos.com/toa/Ubuntu14_04U%2616_04U%2618_04U/toa.ko)

#### 2.2 方案二：自行编译

1. 下载 toa 源码：[https://nlb.cn-sh2.ufileos.com/toa/TOA.zip](https://nlb.cn-sh2.ufileos.com/toa/TOA.zip)
2. 确认云主机已安装 gcc 和 make
3. 在 toa.h、toa.c、Makefile 所在文件夹下执行 make 命令
4. 找到生成的 toa.ko 文件

#### 2.2.1 FAQ-1 编译过程缺少依赖

**CentOS**

1. 下载链接：[https://archive.kernel.org/centos-vault/](https://archive.kernel.org/centos-vault/)
2. 下载镜像版本号对应的 kernel-headers 以及 kernel-devel
3. 可以使用`uname -r`命令查看镜像版本号

**Ubuntu**

1. 下载链接：[https://archive.ubuntu.com/ubuntu/pool/main/l/linux/](https://archive.ubuntu.com/ubuntu/pool/main/l/linux/)
2. 下载镜像版本号对应的 linux-headers (包括`linux-headers-{{version}}_all.deb`以及`linux-headers-{{version}}_amd64.deb`)

**示例**

``` bash
$ rpm -ivh kernel-headers-4.18.0-305.3.1.el8_4.x86_64.rpm
$ yum install perl-interpreter
$ rpm -ivh kernel-devel-4.18.0-305.3.1.el8_4.x86_64.rpm

$ rpm -qa kernel-devel
kernel-devel-4.18.0-305.3.1.el8_4.x86_64
```

### 2.3 安装 toa 模块

```bash
# 安装 toa 模块
$ insmod toa.ko

# 查看安装是否成功
$ lsmod | grep toa

# 卸载 toa 模块
$ rmmod toa
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

![图片注释](/images/image3.png)

