# What is VPN Gateway? {#concept_r5s_gzv_wdb .concept}

VPN Gateway is an Internet-based service that securely and reliably connect enterprise data centers, enterprise office networks or Internet terminals to Alibaba Cloud VPCs through encrypted channels. VPN Gateway supports both IPsec-VPN connection and SSL-VPN connection.

**Note:** Alibaba Cloud VPN Gateway provides services according to national policies and laws and does not provide the function of accessing the Internet.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13346/15434964156217_en-US.png)

## Features {#section_c4z_jsx_wdb .section}

VPN Gateway provides the following features:

-   IPsec-VPN

    IPsec-VPN provides site-to-site VPN connection. You can use IPsec-VPN to connect a VPC to a local data center or connect two VPCs. IPsec-VPN supports IKEv1 protocol and IKEv2 protocol. Any device that supports these two protocols can connect to Alibaba Cloud VPN Gateway. Devices supporting both protocols include those from Huawei, H3C, Hillstone, Sangfor, Cisco, ASA, Juniper, SonicWall, Nokia, IBM, and Ixia.

    For more information, see [Configure a site-to-site connection](../../../../reseller.en-US/IPsec-VPN Quick Start/Configure a site-to-site connection.md#) and [Configure a VPC-to-VPC connection](../../../../reseller.en-US/IPsec-VPN Quick Start/Configure a VPC-to-VPC connection.md#).

-   SSL-VPN

    You can create an SSL-VPN connection to connect a remote client to applications deployed in a VPC. When the deployment is complete, you only need to load the certificate in the client to initiate the connection.

    For more information, see [Linux client remote access](../../../../reseller.en-US/SSL-VPN Quick Start/Linux client remote access.md#), [Windows client remote access](../../../../reseller.en-US/SSL-VPN Quick Start/Windows client remote access.md#), and [Mac client remote access](../../../../reseller.en-US/SSL-VPN Quick Start/Mac client remote access.md#).


## Benefits {#section_ts4_msx_wdb .section}

VPN Gateway offers the following benefits:

-   High security: You can use IKE and IPsec protocols to encrypt transmitted data to ensure data security and reliability.

-   High availability: Using the active/standby hot backup architecture, VPN Gateway automatically goes into the failover mode within one second. This will have minimal effect on the processing of client data.

-   Low cost: The Internet-based encrypted channel is more cost-effective than the leased line so that you can rapidly build a hybrid cloud.

-   Easy to use: Out-of-the-box configurations that take effect immediately allow you to rapidly complete the deployment.


