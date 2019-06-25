# What is VPN Gateway? {#concept_r5s_gzv_wdb .concept}

VPN Gateway is an Internet-based service that securely and reliably connects enterprise data centers, office networks, and Internet terminals to Alibaba Cloud VPCs through encrypted channels. VPN Gateway supports both IPsec-VPN connection and SSL-VPN connection.

**Note:** Alibaba Cloud VPN Gateway provides services according to national policies and laws and does not provide the function of accessing the Internet.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13346/15614304166217_en-US.png)

## Function {#section_c4z_jsx_wdb .section}

VPN Gateway provides the following features:

-   IPsec-VPN

    The route-based IPsec-VPN not only facilitates the configuration and maintenance of VPN policies, but also provides flexible traffic routing methods.

    You can use IPsec-VPN to connect a VPC to an on-premises data center or connect two VPCs. IPsec-VPN supports IKEv1 and IKEv2 protocols. Therefore, any devices that support these two protocols can connect to Alibaba Cloud VPN Gateway, including devices from Huawei, H3C, Hillstone, SANGFOR, Cisco ASA, Juniper, SonicWall, Nokia, IBM, and Ixia.

    For more information, see [Establish a connection between a VPC and an on-premises data center](../../../../reseller.en-US/IPsec-VPN Quick Start/Establish a connection between a VPC and an on-premises data center.md#) and [Establish a connection between two VPCs](../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Establish a connection between two VPCs.md#).

-   SSL-VPN

    You can create an SSL-VPN connection to connect a remote client to applications deployed in a VPC. When the deployment is complete, you only need to load the certificate in the client to initiate the connection.

    For more information, see [Remote access from a Linux client](../../../../reseller.en-US/SSL-VPN Quick Start/Remote access from a Linux client.md#), [Remote access from a Window client](../../../../reseller.en-US/SSL-VPN Quick Start/Remote access from a Window client.md#), and [Remote access from a Mac client](../../../../reseller.en-US/SSL-VPN Quick Start/Remote access from a Mac client.md#).


## Benefits {#section_ts4_msx_wdb .section}

VPN Gateway offers the following benefits:

-   High security: You can use the IKE and IPsec protocols to encrypt data to ensure data security and reliability.
-   High availability: With active/standby hot backup, VPN Gateway automatically switches over to the failover mode within seconds to ensure session continuity and service availability.
-   Low cost: The encrypted Internet-based channel of VPN Gateway is more cost-effective than a leased line.
-   Easy to use: VPN Gateway is ready for use after you purchase it, with no additional configurations required.

