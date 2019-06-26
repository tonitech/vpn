# Scenarios {#concept_dqh_ysx_wdb .concept}

VPN Gateway is an Internet-based service that securely and reliably connects enterprise data centers, office networks, and Internet terminals to Alibaba Cloud VPCs through encrypted channels. VPN Gateways provides flexible configurations to meet the demands of different scenarios.

## Connect a VPC to an on-premises data center {#section_v0g_a9b_r8d .section}

You can connect an on-premises data center to a VPC to build a hybrid cloud through the following two ways:

The route-based IPsec-VPN not only facilitates the configuration and maintenance of VPN policies, but also provides flexible traffic routing methods. For more information, see [Establish a connection between a VPC and an on-premises data center](../../../../reseller.en-US/IPsec-VPN Quick Start/Establish a connection between a VPC and an on-premises data center.md#).

**Note:** To establish a VPN connection between a VPC and an on-premises data center, the IP address ranges of the on-premises data center and the VPC cannot conflict with each other, and a static public IP address must be configure for the gateway device of the on-premises data center.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/15615116423235_en-US.png)

## Interconnect two VPCs {#section_jz4_4al_z1g .section}

You can rapidly interconnect two VPCs through IPsec-VPN.

The route-based IPsec-VPN not only facilitates the configuration and maintenance of VPN policies, but also provides flexible traffic routing methods. For more information, see [Establish a connection between two VPCs](../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Establish a connection between two VPCs.md#).

**Note:** The IP address ranges of the VPCs cannot conflict with each other.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/156151164347477_en-US.png)

## Connect a remote client to a VPC {#section_t7t_4ws_hrt .section}

You can connect a client to a VPC through an SSL-VPN tunnel to meet the needs of remote working. With SSL-VPN connections, you can securely access a VPC through the Internet at anytime, anywhere.

SSL-VPN connections support remote access from clients running Windows, Linux, Mac, IOS, or Android operating system.

For more information, see [Linux client remote connection](../../../../reseller.en-US/SSL-VPN Quick Start/Remote access from a Linux client.md#), [Windows client remote connection](../../../../reseller.en-US/SSL-VPN Quick Start/Remote access from a Window client.md#), and [Mac client remote connection](../../../../reseller.en-US/SSL-VPN Quick Start/Remote access from a Mac client.md#).

**Note:** The IP address ranges of the clients cannot conflict with the IP address range of the VSwitch in the VPC.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/156151164347480_en-US.png)

## Hub Spoke connection {#section_8i6_jqj_rfx .section}

You can establish secure communications among multiple sites by using the Hub Spoke function to interconnect the sites through the VPN Gateway of the VPC. Hub Spoke can meet the needs of large enterprises to establish intranet communication between office sites.

For more information, see [Hub Spoke connection](../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure multi-site connections.md#).

 ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/156151164341054_en-US.png) 

## Use IPsec-VPN and SSL-VPN together {#section_n4g_e8z_804 .section}

You can use IPsec-VPN and SSL-VPN connections together to expand your network topology. Once the connections are established, the client can access the applications deployed in the connected VPC, and can also access the applications deployed in the connected office sites.

**Note:** All private IP address ranges to be connected cannot conflict with one another.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/156151164347485_en-US.png)

