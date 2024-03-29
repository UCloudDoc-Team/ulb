

# 监听器协议

## 协议

监听器的协议分为四层协议和七层协议。四层协议包括TCP和UDP。七层协议包括HTTP和HTTPS。

### 四层协议(TCP／UDP)

根据IP地址加端口号来做负载均衡，进行处理后转发至后端服务节点。

* UDP协议：只需要根据服务IP地址与端口进行负载均衡，对可靠性要求不高，无需差错恢复和数据重传的业务。
* TCP协议：只需根据服务IP地址与端口进行负载均衡，对可靠性要求高，需要在传输数据前先进行握手，保证数据可靠性的业务。

### 七层协议(HTTP/HTTPS)

在四层的基础上，考虑应用层的特征，除了IP地址加端口还可根据七层的URL等信息来进行负载均衡。 

* HTTP协议：不但需要对服务IP地址与端口进行监听，还需要根据应用层内容进行负载均衡，如URL等，但对安全要求不高的业务。
* HTTPS协议：不但需要对服务IP地址与端口进行监听，还需要根据应用层内容进行负载均衡，如URL等，对安全要求高，需要加密的业务。

### 选择建议

* 若业务无需针对应用层的信息做负载均衡，仅需监听服务IP地址与端口，可选择报文转发型CLB。
* 对性能要求较高，可选择报文转发型CLB。
* 如需根据URL、域名等应用层信息来进行负载均衡，或需要HTTP的健康探测，或需要HTTPS SSL卸载，则可选择请求代理型CLB。
