# TLS安全策略

当您部署的业务需要对互联网用户提供服务时，一般情况下会使用HTTPS加密以确保数据的安全传输。针对HTTPS场景，安全策略功能提供配置TLS协议最低版本和加密算法套件的能力，在创建和配置HTTPS监听时，支持绑定自定义的安全策略，保证您业务的安全，从而实现必要的安全需求。

# 预定义策略

预定义策略不支持编辑和删除，目前支持的八种预定义策略支持的加密套件和TLS协议参见下表。

| 策略名称                   | TLS协议最低版本 | 支持的加密套件                                               |
| -------------------------- | --------------- | ------------------------------------------------------------ |
| 原生策略                   | TLSv1           | OpenSSL语法格式`ALL:!NULL:!aNULL:!DSS:!RC4:!RC2:!EXP:!LOW`   |
| TLS最低版本1.2，安全性高   | TLSv1.2         | ECDHE-ECDSA-AES128-CCMECDHE-ECDSA-AES128-CCM8ECDHE-ECDSA-AES128-GCM-SHA256ECDHE-ECDSA-AES128-SHAECDHE-ECDSA-AES128-SHA256ECDHE-ECDSA-AES256-CCMECDHE-ECDSA-AES256-CCM8ECDHE-ECDSA-AES256-GCM-SHA384ECDHE-ECDSA-AES256-SHAECDHE-ECDSA-AES256-SHA384ECDHE-ECDSA-CHACHA20-POLY1305ECDHE-RSA-AES128-GCM-SHA256ECDHE-RSA-AES128-SHAECDHE-RSA-AES128-SHA256ECDHE-RSA-AES256-GCM-SHA384ECDHE-RSA-AES256-SHAECDHE-RSA-AES256-SHA384ECDHE-RSA-CHACHA20-POLY1305 |
| TLS最低版本1.1，安全性高   | TLSv1.1         | ECDHE-ECDSA-AES128-CCMECDHE-ECDSA-AES128-CCM8ECDHE-ECDSA-AES128-GCM-SHA256ECDHE-ECDSA-AES128-SHAECDHE-ECDSA-AES128-SHA256ECDHE-ECDSA-AES256-CCMECDHE-ECDSA-AES256-CCM8ECDHE-ECDSA-AES256-GCM-SHA384ECDHE-ECDSA-AES256-SHAECDHE-ECDSA-AES256-SHA384ECDHE-ECDSA-CHACHA20-POLY1305ECDHE-RSA-AES128-GCM-SHA256ECDHE-RSA-AES128-SHAECDHE-RSA-AES128-SHA256ECDHE-RSA-AES256-GCM-SHA384ECDHE-RSA-AES256-SHAECDHE-RSA-AES256-SHA384ECDHE-RSA-CHACHA20-POLY1305 |
| TLS最低版本1.0，安全性高   | TLSv1           | ECDHE-ECDSA-AES128-CCMECDHE-ECDSA-AES128-CCM8ECDHE-ECDSA-AES128-GCM-SHA256ECDHE-ECDSA-AES128-SHAECDHE-ECDSA-AES128-SHA256ECDHE-ECDSA-AES256-CCMECDHE-ECDSA-AES256-CCM8ECDHE-ECDSA-AES256-GCM-SHA384ECDHE-ECDSA-AES256-SHAECDHE-ECDSA-AES256-SHA384ECDHE-ECDSA-CHACHA20-POLY1305ECDHE-RSA-AES128-GCM-SHA256ECDHE-RSA-AES128-SHAECDHE-RSA-AES128-SHA256ECDHE-RSA-AES256-GCM-SHA384ECDHE-RSA-AES256-SHAECDHE-RSA-AES256-SHA384ECDHE-RSA-CHACHA20-POLY1305 |
| TLS最低版本1.2，安全性中   | TLSv1.2         | AES128-CCMAES128-CCM8AES128-GCM-SHA256AES128-SHA256AES256-CCMAES256-CCM8AES256-GCM-SHA384AES256-SHA256ECDHE-ECDSA-AES128-CCMECDHE-ECDSA-AES128-CCM8ECDHE-ECDSA-AES128-GCM-SHA256ECDHE-ECDSA-AES128-SHAECDHE-ECDSA-AES128-SHA256ECDHE-ECDSA-AES256-CCMECDHE-ECDSA-AES256-CCM8ECDHE-ECDSA-AES256-GCM-SHA384ECDHE-ECDSA-AES256-SHAECDHE-ECDSA-AES256-SHA384ECDHE-ECDSA-CHACHA20-POLY1305ECDHE-RSA-AES128-GCM-SHA256ECDHE-RSA-AES128-SHAECDHE-RSA-AES128-SHA256ECDHE-RSA-AES256-GCM-SHA384ECDHE-RSA-AES256-SHAECDHE-RSA-AES256-SHA384ECDHE-RSA-CHACHA20-POLY1305 |
| TLS最低版本1.1，安全性中   | TLSv1.1         | AES128-CCMAES128-CCM8AES128-GCM-SHA256AES128-SHA256AES256-CCMAES256-CCM8AES256-GCM-SHA384AES256-SHA256ECDHE-ECDSA-AES128-CCMECDHE-ECDSA-AES128-CCM8ECDHE-ECDSA-AES128-GCM-SHA256ECDHE-ECDSA-AES128-SHAECDHE-ECDSA-AES128-SHA256ECDHE-ECDSA-AES256-CCMECDHE-ECDSA-AES256-CCM8ECDHE-ECDSA-AES256-GCM-SHA384ECDHE-ECDSA-AES256-SHAECDHE-ECDSA-AES256-SHA384ECDHE-ECDSA-CHACHA20-POLY1305ECDHE-RSA-AES128-GCM-SHA256ECDHE-RSA-AES128-SHAECDHE-RSA-AES128-SHA256ECDHE-RSA-AES256-GCM-SHA384ECDHE-RSA-AES256-SHAECDHE-RSA-AES256-SHA384ECDHE-RSA-CHACHA20-POLY1305 |
| TLS最低版本1.0，安全性中   | TLSv1           | AES128-CCMAES128-CCM8AES128-GCM-SHA256AES128-SHA256AES256-CCMAES256-CCM8AES256-GCM-SHA384AES256-SHA256ECDHE-ECDSA-AES128-CCMECDHE-ECDSA-AES128-CCM8ECDHE-ECDSA-AES128-GCM-SHA256ECDHE-ECDSA-AES128-SHAECDHE-ECDSA-AES128-SHA256ECDHE-ECDSA-AES256-CCMECDHE-ECDSA-AES256-CCM8ECDHE-ECDSA-AES256-GCM-SHA384ECDHE-ECDSA-AES256-SHAECDHE-ECDSA-AES256-SHA384ECDHE-ECDSA-CHACHA20-POLY1305ECDHE-RSA-AES128-GCM-SHA256ECDHE-RSA-AES128-SHAECDHE-RSA-AES128-SHA256ECDHE-RSA-AES256-GCM-SHA384ECDHE-RSA-AES256-SHAECDHE-RSA-AES256-SHA384ECDHE-RSA-CHACHA20-POLY1305 |
| 仅TLS版本改动，最低版本1.2 | TLSv1.2         | -                                                            |
| 仅TLS版本改动，最低版本1.1 | TLSv1.1         | -                                                            |

预定义策略差异对比，参见下表

|                               | TLS最低版本1.2，安全性高 | TLS最低版本1.1，安全性高 | TLS最低版本1.0，安全性高 | TLS最低版本1.2，安全性中 | TLS最低版本1.1，安全性中 | TLS最低版本1.0，安全性中 |
| ----------------------------- | ------------------------ | ------------------------ | ------------------------ | ------------------------ | ------------------------ | ------------------------ |
| ECDHE-ECDSA-AES128-CCM        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-ECDSA-AES128-CCM8       | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-ECDSA-AES128-GCM-SHA256 | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-ECDSA-AES128-SHA        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-ECDSA-AES128-SHA256     | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-ECDSA-AES256-CCM        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-ECDSA-AES256-CCM8       | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-ECDSA-AES256-GCM-SHA384 | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-ECDSA-AES256-SHA        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-ECDSA-AES256-SHA384     | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-ECDSA-CHACHA20-POLY1305 | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-RSA-AES128-GCM-SHA256   | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-RSA-AES128-SHA          | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-RSA-AES128-SHA256       | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-RSA-AES256-GCM-SHA384   | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-RSA-AES256-SHA          | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-RSA-AES256-SHA384       | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| ECDHE-RSA-CHACHA20-POLY1305   | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        | ✔                        |
| AES128-CCM                    |                          |                          |                          | ✔                        | ✔                        | ✔                        |
| AES128-CCM8                   |                          |                          |                          | ✔                        | ✔                        | ✔                        |
| AES128-GCM-SHA256             |                          |                          |                          | ✔                        | ✔                        | ✔                        |
| AES128-SHA256                 |                          |                          |                          | ✔                        | ✔                        | ✔                        |
| AES256-CCM                    |                          |                          |                          | ✔                        | ✔                        | ✔                        |
| AES256-CCM8                   |                          |                          |                          | ✔                        | ✔                        | ✔                        |
| AES256-GCM-SHA384             |                          |                          |                          | ✔                        | ✔                        | ✔                        |
| AES256-SHA256                 |                          |                          |                          | ✔                        | ✔                        | ✔                        |

**说明：**

1、TLS协议版本最高可支持到 TLSv1.3，如果协商使用 TLSv1.3，其对应的默认加密套件为：

- TLS_AES_128_GCM_SHA256
- TLS_AES_256_GCM_SHA384
- TLS_CHACHA20_POLY1305_SHA256

2、除了上表中的六个预定义策略，还有以下两个，其加密算法套件与原生策略一致：

- security-tls12o，仅TLS版本改动，最低版本1.2
- security-tls11o，仅TLS版本改动，最低版本1.1

3、预定义策略中安全性高的策略，其支持的加密套件在ALB的环境中，等同于语法

```
ALL:!NULL:!aNULL:!DSS:!RC4:!RC2:!EXP:!LOW:!SSLv3:!CAMELLIA:!ARIA:!3DES:!DH:!DHE:!RSA
```

4、预定义策略中安全性中的策略，其支持的加密套件在ALB的环境中，等同于语法

```
ALL:!NULL:!aNULL:!DSS:!RC4:!RC2:!EXP:!LOW:!SSLv3:!CAMELLIA:!ARIA:!3DES:!DH:!DHE
```

# 自定义策略

您可以通过组合TLS协议最低版本和加密算法套件来定义自己需要的策略。

## 创建自定义策略

1. 登录应用型负载均衡ALB控制台。
2. 选择**安全策略管理**。

![1713869926651](/images/1713869926651.png)

3. 在**安全策略列表**页面，点击**创建安全组策略**。

4. 在**创建安全策略**对话框中，完成以下参数配置，配置完成后点击**新建**。

| 配置项          | 说明                                                         |
| :-------------- | :----------------------------------------------------------- |
| 名称            | 输入自定义策略名称。                                         |
| TLS协议最低版本 | TLS协议最低版本，必填项，支持可选的 TLS 版本为 TLSv1，TLSv1.1，TLSv1.2 |
| 加密算法套件    | 选择TLS版本支持的加密算法套件。                              |

![1713869964897](/images/1713869964897.png)

5. 自定义策略创建完成后，可以在创建HTTPS监听时的高级设置中选择配置自定义策略。

## 删除单个自定义策略

1. 登录应用型负载均衡ALB控制台。
2. 选择**安全策略管理**。

![1713870024455](D:\需求\产品文档\ALB\ulb\ulb\ulb\ulb\ulb\images\1713870024455.png)

3. 在**安全策略列表**页面，选择需要删除的自定义安全策略，点击**删除**。

4. 在二次确认弹窗中，确认是否是要删除的安全策略。

5. 点击确定，完成删除操作。

## 批量删除自定义安全策略

1. 登录应用型负载均衡ALB控制台。
2. 选择**安全策略管理**。

![1713870108036](D:\需求\产品文档\ALB\ulb\ulb\ulb\ulb\ulb\images\1713870108036.png)

3. 在**安全策略列表**页面，批量选中需要删除的安全策略左侧的勾选框，点击上方的删除。

4. 在二次确认弹出弹窗中，确认是否是要删除的安全策略。

5. 点击**确定**，完成删除操作。

如您想删除自定义策略，需先解绑VServer，才能进行删除操作。

## 编辑自定义安全策略

您可以根据实际的业务需要，对自定义安全组策略进行更新。

1. 登录应用型负载均衡ALB控制台。
2. 选择**安全策略管理**。

3. 在**安全策略列表**页面，选择需要编辑的自定义策略，点击操作栏的编辑；

![1713870172291](/images/1713870172291.png)

4. 在编辑安全组策略弹窗中设置如下信息；

| 配置项          | 说明                                                         |
| :-------------- | :----------------------------------------------------------- |
| 名称            | 输入自定义策略名称。                                         |
| TLS协议最低版本 | TLS协议最低版本，必填项，支持可选的 TLS 版本为 TLSv1，TLSv1.1，TLSv1.2 |
| 加密算法套件    | 选择TLS版本支持的加密算法套件。                              |

1. 修改后点击确定，完成编辑操作。