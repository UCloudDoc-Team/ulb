{{indexmenu_n>100}}


# VServer端口和服务节点端口是否必须一致？

不一定要保持一致，如要实现ULB报文转发监听端口和后端服务器监听端口不一致，可以通过服务节点内配置IpTables端口转发规则实现，具体步骤如下：

1、修改/etc/sysctl.conf配置文件，设置 net.ipv4.ip\_forward = 1 默认是0。  
2、关闭防火墙 service iptables stop。  
3、配置规则：

```
iptables -t nat -A PREROUTING –d $vip_ip -p tcp --dport $ulb4_port  -j DNAT --to-destination $vip_ip:$vm_port
```

其中：$vip\_ip指负载均衡器的内网服务IP地址，$ulb4\_port指ulb4的监听端口，$vm\_port为后端服务器的监听端口 例：负载均衡器的内网服务IP地址为：10.10.10.10，ulb\_4监听端口为80，后端服务器监听端口为8101，则规则为：

```
iptables -t nat -A PREROUTING -d 10.10.10.10 -p tcp --dport 80 -j DNAT --to-destination 10.10.10.10:8101
```

4、保存配置：service iptables save  
5、启动iptables ：service iptables start

[[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
