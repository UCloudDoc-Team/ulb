# 安全策略

安全策略功能提供配置**TLS协议最低版本**和**加密算法套件**的能力，在创建和配置HTTPS监听时，支持绑定特定的安全策略，从而实现必要的安全需求。

安全策略分为原生策略，预定义策略和自定义策略。

> 安全策略功能目前还只在部分地域进行公测，如果ULB实例还未公测，将无法绑定使用创建好的安全策略，有需要请联系技术支持。

## 原生策略

在 VServer 不绑定任何安全策略的情况下，系统将使用自带的原生策略。目前系统的原生策略是：**TLS协议最低版本**为`TLSv1`，最高可能支持到`TLSv1.2`或`TLSv1.3`（受限于ULB底层使用的OpenSSL版本），**加密算法套件**为OpenSSL语法格式`ALL:!NULL:!aNULL:!DSS:!RC4:!RC2:!EXP:!LOW`。

## 预定义策略

预定义策略不可编辑和删除，目前支持八种预定义策略，具体差异见下表：

|                               | security-tls12s          | security-tls11s          | security-tls10s          | security-tls12m          | security-tls11m          | security-tls10m          |
| ----------------------------- | ------------------------ | ------------------------ | ------------------------ | ------------------------ | ------------------------ | ------------------------ |
|                               | TLS最低版本1.2，安全性高 | TLS最低版本1.1，安全性高 | TLS最低版本1.0，安全性高 | TLS最低版本1.2，安全性中 | TLS最低版本1.1，安全性中 | TLS最低版本1.0，安全性中 |
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

> 说明：
>
> 1、TLS协议版本最高可支持到 TLSv1.3，如果协商使用 TLSv1.3，其对应的默认加密套件为：
>
> - TLS_AES_128_GCM_SHA256
> - TLS_AES_256_GCM_SHA384
> - TLS_CHACHA20_POLY1305_SHA256
>
> 2、除了上表中的六个预定义策略，还有以下两个，其**加密算法套件**与原生策略一致：
>
> - security-tls12o，仅TLS版本改动，最低版本1.2
> - security-tls11o，仅TLS版本改动，最低版本1.1
>
> 3、预定义策略中安全性高的策略，其支持的加密套件在ULB的环境中，等同于语法 `ALL:!NULL:!aNULL:!DSS:!RC4:!RC2:!EXP:!LOW:!SSLv3:!CAMELLIA:!ARIA:!3DES:!DH:!DHE:!RSA`。
>
> 4、预定义策略中安全性中的策略，其支持的加密套件在ULB的环境中，等同于语法 `ALL:!NULL:!aNULL:!DSS:!RC4:!RC2:!EXP:!LOW:!SSLv3:!CAMELLIA:!ARIA:!3DES:!DH:!DHE`。

## 自定义策略

您可以通过组合**TLS协议最低版本**和**加密算法套件**来定义自己需要的策略。

**TLS协议最低版本**可配置的范围是`TLSv1`，`TLSv1.1`，`TLSv1.2`。

**加密算法套件**可配置的范围参见预定义策略里表格的第一列。
