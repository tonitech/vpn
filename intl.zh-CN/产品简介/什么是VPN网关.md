# 什么是VPN网关 {#concept_r5s_gzv_wdb .concept}

VPN网关是一款基于Internet，通过加密通道将企业数据中心、企业办公网络、或Internet终端和阿里云专有网络（VPC）安全可靠连接起来的服务。VPN网关提供IPsec-VPN连接和SSL-VPN连接。

**说明：** 阿里云VPN网关在国家相关政策法规内提供服务，不提供访问Internet功能。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13431/15554635043233_zh-CN.png)

## 功能 {#section_c4z_jsx_wdb .section}

VPN网关提供IPsec-VPN和SSL-VPN功能：

-   IPsec-VPN

    IPsec-VPN提供站点到站点的VPN连接，您可以使用IPsec-VPN将本地数据中心和专有网络连接起来，或连接两个VPC。IPsec-VPN支持IKEv1和IKEv2协议。只要支持这两种协议的设备都可以和阿里云VPN网关互连，比如华为、华三、山石、深信服、Cisco ASA、Juniper、SonicWall、Nokia、IBM 和 Ixia等。

    详情参见[建立站点到站点连接](../../../../intl.zh-CN/IPsec-VPN入门/建立站点到站点连接.md#)和[../../../../dita-oss-bucket/SP\_74/DNVPN11815583/ZH-CN\_TP\_13352.md\#](../../../../intl.zh-CN/用户指南/配置IPsec-VPN/配置VPC到VPC连接.md#)。

-   SSL-VPN

    您可以使用SSL-VPN功能从客户端远程接入VPC中部署的应用和服务。部署完成后，您仅需要在客户端中加载证书发起连接即可。

    详情参见[Linux客户端远程连接](../../../../intl.zh-CN/SSL-VPN入门/Linux客户端远程连接.md#)、[Windows客户端远程连接](../../../../intl.zh-CN/SSL-VPN入门/Windows客户端远程连接.md#)和[Mac客户端远程连接](../../../../intl.zh-CN/SSL-VPN入门/Mac客户端远程连接.md#)。


## 产品优势 {#section_ts4_msx_wdb .section}

VPN网关有以下优势：

-   安全：使用IKE和IPsec协议对传输数据进行加密，保证数据安全可靠。

-   高可用：采用双机热备架构，故障时秒级切换，保证会话不中断，业务无感知。

-   成本低：基于Internet建立加密通道，比建立专线更便宜，快速构建混合云。

-   配置简单：开通即用，配置实时生效，快速完成部署。


