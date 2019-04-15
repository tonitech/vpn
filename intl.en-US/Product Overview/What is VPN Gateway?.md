# What is VPN Gateway? {#concept_r5s_gzv_wdb .concept}

VPN Gateway is an Internet-based service that securely and reliably connects enterprise data centers, office networks, and Internet terminals to Alibaba Cloud VPCs through encrypted channels. VPN Gateway provides both IPsec-VPN connection and SSL-VPN connection.

**Note:** Alibaba Cloud VPN Gateway does not support access to the Internet. The use of VPN Gateway is subject to local laws and policies.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13346/15552931716217_en-US.png)

## Features {#section_c4z_jsx_wdb .section}

VPN Gateway provides the following features:

-   IPsec-VPN

    IPsec-VPN provides site-to-site VPN connection. You can use IPsec-VPN to connect a VPC to an on-premises data center or interconnect two VPCs. IPsec-VPN supports the IKEv1 protocol and IKEv2 protocol. Therefore, any devices that support these two protocols can connect to Alibaba Cloud VPN Gateway, including devices from Huawei, H3C, Hillstone, Sangfor, Cisco ASA, Juniper, SonicWall, Nokia, IBM, and Ixia.

    For more information, see [Create a site-to-site connection through IPsec-VPN](../../../../../reseller.en-US/IPsec-VPN Quick Start/Create a site-to-site connection through IPsec-VPN.md#) and [Configure a VPC-to-VPC connection](../../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure a VPC-to-VPC connection.md#).

-   SSL-VPN

    You can create an SSL-VPN connection to connect a remote client to applications deployed in a VPC. When the deployment is complete, you only need to load a certificate in the client to initiate the connection.

    For more information, see [Linux client remote access](../../../../../reseller.en-US/SSL-VPN Quick Start/Linux client remote access.md#), [Window client remote access](../../../../../reseller.en-US/SSL-VPN Quick Start/Window client remote access.md#), and [Mac client remote access](../../../../../reseller.en-US/SSL-VPN Quick Start/Mac client remote access.md#).


## Benefits {#section_ts4_msx_wdb .section}

VPN Gateway offers the following benefits:

-   High security: You can use the IKE and IPsec protocols to encrypt data to ensure data security and reliability.

-   High availability: With active/standby hot backup, VPN Gateway automatically switches over to failover mode within seconds to ensure session continuity and service availability.

-   Low cost: The encrypted Internet-based channel of VPN Gateway is more cost-effective than a leased line.

-   Easy to use: VPN Gateway is ready for use after you purchase it, with no additional configurations required.


