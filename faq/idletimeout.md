{{indexmenu_n>90}}

# 连接空闲超时的原理？

对客户端向ULB发送的请求，ULB将维护两个连接。一个连接指向客户端，另一个连接指向后端RS。

超过连接空闲超时期限后，如果没有发送或接收任何数据，ULB将关闭连接。 

ULB中默认打开连接保持，默认连接保持时间为60秒。例如在第一次发包后连接将会保持60秒，如果距上一次发包60秒内没有新的TCP包，连接将会断开。 用户可以根据自己的业务需要设置连接空闲超时的阈值。

目前具有连接空闲超时的协议有HTTP、HTTPS、TCP的请求代理模式。

[[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
