# 证书管理

在配置ALB的HTTPS监听器时，您需要选择在证书管理页面添加您购买的证书，或者上传第三方签发的证书来保证您监听器的认证业务可以正常使用

# 使用限制

## 格式要求

当前证书支持两种上传方式，第一种是直接上传证书文件，第二种是手动填写证书文本信息。

# 添加证书

1. 登录应用型负载均衡ALB控制台。
2. 在负载均衡二级TAB栏，点击证书管理页签，进入证书列表页。
3. 在证书列表页，点击左上角添加证书。

![1713869130694](/images/1713869130694.png)

4. 目前支持添加三种来源的证书。

| 证书来源 | 说明                                                         |
| :------- | :----------------------------------------------------------- |
| USSL导入 | 证书管理支持直接从**证书管理 USSL**导入已经购买或者托管的证书。 |
| 本地导入 | 证书管理支持导入本地的SSL证书，上传证书的授权文件即可，如果您选择直接上传证书文件，那么需要准备好以下文件，网站的证书文件（cer/crt/pem格式）、私钥文件（key文件）、（可选）中间证书/根证书（证书链，cer/crt/pem格式） |
| 手动输入 | ULB证书管理支持手动输入，如果您选择手动填写证书，则文本需要依次包含以下字段：私钥、网站证书、中间证书、根证书等。 |

## 本地导入

![1713869162553](/images/1713869162553.png)

如果您选择直接上传证书文件，那么需要准备好以下文件：

- 必选，网站的证书文件（cer/crt/pem格式），文件的文本格式如下：

```Plaintext
-----BEGIN MY CERTIFICATE-----
...
-----END MY CERTIFICATE-----CopyErrorSuccess
```

- 必选，私钥文件（key文件）

数字签名算法为RSA的文件的文本格式如下：

```Plaintext
-----BEGIN RSA PRIVATE KEY-----
... 
-----END RSA PRIVATE KEY-----CopyErrorSuccess
```

数字签名算法为ECDSA的文件的文本格式如下，EC PARAMETERS为可选：

```Assembly
-----BEGIN EC PARAMETERS-----
... 
-----END EC PARAMETERS-----
-----BEGIN EC PRIVATE KEY-----
... 
-----END EC PRIVATE KEY-----CopyErrorSuccess
```

- 可选，中间证书、根证书（证书链，cer/crt/pem格式），文件的文本格式如下：

```Plaintext
-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----CopyErrorSuccess
```

您提供的证书需要去除口令保护。您在上传证书或手动填写证书时，请确保证书格式正确，如果校验格式错误，则会添加证书不成功。

## 手动输入

![1713869184540](/images/1713869184540.png)

如果您选择手动填写证书，则文本需要依次包含以下字段：私钥、网站证书、中间证书、根证书等。

数字签名算法为RSA格式参考如下（在复制时请核对证书的完整性）：

```Plaintext
-----BEGIN RSA PRIVATE KEY-----
... 
-----END RSA PRIVATE KEY-----
-----BEGIN MY CERTIFICATE-----
...
-----END MY CERTIFICATE-----
-----BEGIN MY CERTIFICATE-----
...
-----END MY CERTIFICATE-----CopyErrorSuccess
```

数字签名算法为ECDSA格式参考如下（在复制时请核对证书的完整性）：

```Plaintext
-----BEGIN EC PRIVATE KEY-----
... 
-----END EC PRIVATE KEY-----
-----BEGIN MY CERTIFICATE-----
...
-----END MY CERTIFICATE-----
-----BEGIN MY CERTIFICATE-----
...
-----END MY CERTIFICATE-----CopyErrorSuccess
```

若您的证书为其他格式，建议您使用openssl工具进行格式转换。

DER转PEM：

证书转化：openssl x509 -inform der -in certificate.cer -out certificate.pem

私钥转化（RSA证书）：openssl rsa -inform DER -outform PEM -in privatekey.der -out privatekey.pem

私钥转化（ECDSA证书）：openssl ec -inform DER -outform PEM -in privatekey.der -out privatekey.pem

# 删除证书

1. 登录应用型负载均衡ALB控制台。
2. 在负载均衡二次TAB栏，点击证书管理页签，进入证书列表页。
3. 在证书列表页，在目标证书的操作类，点击删除，或者勾选需要删除的目标证书左上的删除证书

![1713869561798](/images/1713869561798.png)

4. 在弹出的删除弹窗内，点击确定。

# 更换绑定证书

证书在绑定到监听器后，为避免证书过期对您的服务产生影响，建议在证书过期前更换证书。

## 更换监听器的证书

ULB支持在两种方式更换监听证书，如您仅单独更换某个监听器绑定的默认证书，可以参照如下方式。

1. 登录应用型负载均衡ALB控制台。
2. 在负载均衡控制台，选择**证书管理**TAB页 。
3. 在**实例列表**页面，找到目标实例，点击实例ID，进入实例详情页。
4. 点击**监听器管理**页签，在目标监听器详情页点击**监听证书**。
5. 在**监听证书**页签，在默认证书的操作列，点击**更改绑定**。

![1713869640690](/images/1713869640690.png)

6. 在更换证书弹窗，选择需要更换的证书，点击确定。

如您需要批量更换绑定的证书，可以参照如下方式。

1. 登录应用型负载均衡ALB控制台。
2. 在顶部菜单栏处，选择实例所属的地域。
3. 在**证书管理**页签，找到需要更换的**目标证书**。
4. 在目标证书的操作栏，点击详情，进入证书详情页。
5. 选择监听器管理，点击左上角**全部更改绑定**。

![1713869719257](/images/1713869719257.png)

6. 选择需要更换的证书，点击确定。