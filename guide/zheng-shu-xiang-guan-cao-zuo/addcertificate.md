{{indexmenu_n>2}}

# 添加证书

证书管理将证书存储在ULB证书管理系统中，用于HTTPS协议。

> 证书不可跨Region使用。若多地域均需要使用，则多个地域均需要上传证书。


## 操作步骤

进入**负载均衡 ULB页面**，点击**证书管理**。 

1、点击**添加证书**，弹出添加证书弹窗。

![](https://static.ucloud.cn/c5bfababbcf24c8baf65fc2b914eefe7.png)

2、需要填写以下信息

|配置|说明|
|-|-|
|证书名称	|证书名称，必填项。|
|证书内容|如果选择本地上传证书，选择您本地的授权证书，包括.crt文件与.key文件。如果选择手动输入证书，则需要在输入框中手动填写证书，证书格式见证书格式要求（相对路径）|
|证书格式|授权证书(.crt文件)：证书机构下发的公钥文件。授权证书(.key文件)：证书机构下发的私钥文件|CA机构证书(.crt文件)：证书机构证明自身是权威机构的证明|


[[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
