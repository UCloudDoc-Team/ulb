{{indexmenu_n>1}}

# 证书格式

## 格式要求

当前证书支持两种上传方式，第一种是直接上传证书文件，第二种是手动填写证书文本信息。

### 直接上传文件

如果您选择直接上传证书文件，那么需要准备好以下文件：

* 必选，网站的证书文件（cer/crt/pem格式），文件的文本格式如下：

```
-----BEGIN MY CERTIFICATE-----
...
-----END MY CERTIFICATE-----
```

* 必选，私钥文件（key文件），文件的文本格式如下：

```
-----BEGIN RSA PRIVATE KEY-----
... 
-----END RSA PRIVATE KEY-----
```

* 可选，中间证书、根证书（证书链，cer/crt/pem格式），文件的文本格式如下：

```
-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----
-----BEGIN CERTIFICATE-----
...
-----END CERTIFICATE-----
```

您提供的证书需要去除口令保护。您在上传证书或手动填写证书时，请确保证书格式正确，如果校验格式错误，则会添加证书不成功。

### 手动填写证书

如果您选择手动填写证书，则文本需要依次包含以下字段：私钥、网站证书、中间证书、根证书等，格式参考如下（在复制时请核对证书的完整性）：

```
-----BEGIN RSA PRIVATE KEY-----
... 
-----END RSA PRIVATE KEY-----
-----BEGIN MY CERTIFICATE-----
...
-----END MY CERTIFICATE-----
-----BEGIN MY CERTIFICATE-----
...
-----END MY CERTIFICATE-----
```

若您的证书为其他格式，建议您使用openssl工具进行格式转换。

DER转PEM：

证书转化：openssl x509 -inform der -in certificate.cer -out certificate.pem 

私钥转化：openssl rsa -inform DER -outform PEM -in privatekey.der -out privatekey.pem

[[https://github.com/UCloudDocs/UCloud-document/issues/3|{{https://static.ucloud.cn/e7fec9d74c744c448d757fad04fe1bcb.png}}]]
