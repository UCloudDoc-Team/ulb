# 最佳实践

# **通过ProxyProtocol协议获取客户端真实IP**

网络型负载均衡NLB支持后端服务器获取客户端真实IP地址。在创建监听器时开启Proxy协议，后端服务节点即可获取客户端真实IP地址。

# **Proxy Protocol**说明

Proxy Protocol是一种通信协议，用于在代理服务器和后端服务器之间传递客户端的原始网络连接信息。

一般情况下，代理服务器在转发客户端请求到后端服务器时会重写请求头部，将客户端的源IP地址和端口等信息替换为代理服务器自身的信息。这样后端服务器就无法获得客户端的真实网络连接信息。

而使用Proxy Protocol，代理服务器在转发请求时将客户端的原始网络连接信息封装在请求头部中，发送给后端服务器。后端服务器通过解析Proxy Protocol头部，就可以获得客户端的真实网络连接信息，包括源IP地址、源端口以及传输协议等。

通过使用Proxy Protocol，后端服务器可以准确获取客户端的原始网络连接信息，从而进行更准确的日志记录、访问控制、流量监控等操作。

- 开启Proxy Protocol功能，需要后端服务节点都支持该协议才能正常使用。如果后端服务节点不具备解析Proxy Protocol协议能力，直接开启该功能，会导致后端服务解析异常，从而影响服务可用性。
- NLB监听支持通过Proxy Protocol携带原始连接信息（源IP、目的IP、源端口、目的端口等）并添加到TCP或UDP数据头中。
- NLB仅支持Proxy Protocol v2版本。Proxy Protocol v2版本支持多种传输协议，如TCP和UDP，更多信息，请参见[The PROXY protocol](https://www.haproxy.org/download/1.8/doc/proxy-protocol.txt)。

# 操作步骤

## 步骤一：NLB监听器开启**Proxy Protocol**

1. 登录网络型负载均衡NLB控制台，选择目标实例
2. 单击实例ID。在实例详情页面，单击**监听器管理**页签，找到目标监听，单击更改配置。
3. 在监听器编辑页面，可**开启ProxyProtocol**。

## **步骤二：为后端服务器配置Proxy Protocol**

CentOS 7.9操作系统、Nginx 1.20.1 版本配置为例

1. 登录后端服务器，执行`nginx -t`命令查看配置文件所在路径。默认通常为 `/etc/nginx/nginx.conf`，具体请以实际环境为准。
2. 修改配置文件中的Proxy Protocol内容并保存，修改点可参考下方说明。

```Nginx
http {# 确保设置$proxy_protocol_addr，该变量用于记录客户端真实IPlog_format  main  '$proxy_protocol_addr - $remote_addr- $remote_user [$time_local] "$request" ''$status $body_bytes_sent "$http_referer" ''"$http_user_agent" "$http_x_forwarded_for"';# 以80监听端口为例，增加proxy_protocol字段server {listen 80   proxy_protocol;#...
  }
}
```

1. 执行`sudo nginx -s reload`命令，重新加载Nginx配置文件。

Ubuntu 22.04操作系统、Nginx 1.20.1 版本配置为例

1. 登录服务器，执行 sudo nginx -t 命令检查配置文件路径。输出中会显示主配置文件路径（通常为 `/etc/nginx/nginx.conf`），而 `server` 块可能位于 `/etc/nginx/sites-available/` 下的子文件（如 `default`）。
2. 修改Nginx配置，编辑主配置文件，sudo nano /etc/nginx/nginx.conf 在 `http` 块内修改 `log_format`，添加 `$proxy_protocol_addr` 变量：

```Nginx
http {log_format main '$proxy_protocol_addr - $remote_addr - $remote_user [$time_local] "$request" ''$status $body_bytes_sent "$http_referer" ''"$http_user_agent" "$http_x_forwarded_for"';# 其他配置...}
```

1. 编辑Server配置文件，sudo nano /etc/nginx/sites-available/default 在需要启用Proxy Protocol的 `server` 块中，修改 `listen` 指令

```Nginx
server {
    listen 80 proxy_protocol;   # 启用Proxy Protocol（HTTP）
    listen [::]:80 proxy_protocol;
    # 其他配置...
}
```

1. 检查配置并重载Nginx，

测试配置语法，sudo nginx -t ， 若输出 `syntax is ok` 和 `test is successful` 表示配置正确。

重新加载Nginx：

```Nginx
sudo systemctl reload nginx
# 或使用传统命令
sudo nginx -s reload
```

## 步骤三：**验证后端服务器可获取客户端真实IP**

当Nginx作为后端服务节点时，您可以通过检查Nginx日志来判断是否成功获取到了客户端的真实IP地址。

Nginx日志文件默认路径为：`/var/log/nginx/access.log`

每行日志中，`$proxy_protocol_addr`变量对应的IP地址即为客户端真实IP地址。