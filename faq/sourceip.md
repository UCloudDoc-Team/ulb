

# ULB如何获取客户端的源地址？

ULB支持报文转发、请求代理两种类型。报文转发型支持TCP、UDP等协议，请求代理型支持HTTP、HTTPS、TCP等协议。

报文转发模式下，后端服务节点收到的请求的源地址就是实际的源地址。

请求代理模式下，HTTP/HTTPS协议中，ULB已经默认在报文头中添加了X-Forwarded-For、X-Forwarded-Proto和X-Forwarded-SrcPort，可以分别对应获取客户端的源地址、客户端与负载均衡之间的应用层协议和客户端端口。TCP协议无法返回源地址。


### 获取客户端源地址：
```
# Nginx示例
log_format  upstream  '$time_iso8601 $http_x_forwarded_for $host $upstream_response_time $request $status $upstream_addr';

# Apache示例
SetEnvIf REMOTE_ADDR "(.+)" CLIENTIP=$1
SetEnvIf X-Forwarded-For "^([0-9.]+)" CLIENTIP=$1
LogFormat "%{CLIENTIP}e %D %u %t \"%r\" %>s %O \"%{Referer}i\" \"%{User-Agent}i\"" trueip_combined
CustomLog logs/access_log trueip_combined

# tomcat 的server.xml文件修改如下参数：
    <Host name="localhost" appBase="webapps" 
        unpackWARs="true" autoDeploy="true"> 
        <Valve className="org.apache.catalina.valves.AccessLogValve" 
        directory="logs" 
        prefix="tomcat_access." 
        suffix=".log" 
       pattern="%{X-FORWARDED-FOR}i %l %u %t %r %s %b %D %q %{User-Agent}i %T" resolveHosts="false"/> 
</Host>
```
 
