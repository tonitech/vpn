# Scenarios {#concept_dqh_ysx_wdb .concept}

This topic describes scenarios that implement Alibaba Cloud VPN Gateway. VPN Gateway is an Internet-based service that securely and reliably connects enterprise data centers, office networks, and Internet terminals to Alibaba Cloud VPCs through encrypted channels. VPN Gateways provides flexible configurations to meet the demands of different scenarios.

## IPsec-VPN scenarios {#section_azx_ctx_wdb .section}

**Scenario one: Connect a VPC to an on-premises data center**

You can build a hybrid cloud environment by creating an IPsec-VPN tunnel to connect a VPC to your on-premises data center.

For more information, see [Configure an IPsec-VPN connection to connect a VPC to an on-premises data center](../../../../reseller.en-US/IPsec-VPN Quick Start/Create a site-to-site connection through IPsec-VPN.md#).

**Note:** The IP address range of the on-premises data center cannot conflict with that of the VPC, and a static public IP address must be configured for the VPN Gateway of the on-premises data center.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/15554652793235_en-US.png)

**Scenario two: Interconnect two VPCs**

You can use a VPN Gateway to create an IPsec-VPN tunnel to interconnect two VPCs.

For more information, see [Create an IPsec connection to interconnect two VPCs](../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure a VPC-to-VPC connection.md#).

**Note:** The VSwitch IP address ranges of the VPCs cannot conflict with each other.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/15554652793237_en-US.png)

**Scenario three: Achieve redundancy with multiple VPN connections**

One VPN Gateway is deployed at the Alibaba Cloud side and two customer gateways are deployed at the customer side.

The two customer gateways are connected to the VPN Gateway and an IPsec connection is established between each customer gateway and the VPN Gateway. The two IPsec connections are configured with health checks and have succeeded in negotiation. When a customer gateway is declared as unhealthy, traffic is automatically directed to the other customer gateway.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/155546527941013_en-US.png)

**Scenario four: Hub Spoke connection**

You can establish secure communications among multiple sites by using the Hub Spoke function to interconnect the sites through the VPN Gateway of the VPC.

For more information, see [Hub Spoke connection](../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure multi-site connections.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/155546528041054_en-US.png)

## SSL-VPN scenarios {#section_tvk_tcp_dhb .section}

You can connect a client to a VPC through an SSL-VPN tunnel to meet the needs of remote working. With SSL-VPN connections, you can securely access a VPC through the Internet at anytime, anywhere.

SSL-VPN connections support remote access from clients running varioaus operating systems, including Windows, Linux, Mac, IOS, and Android.

a

For more information, see [Linux client remote access](../../../../reseller.en-US/SSL-VPN Quick Start/Linux client remote access.md#), [Windows client remote access](../../../../reseller.en-US/SSL-VPN Quick Start/Window client remote access.md#) and [Mac client remote access](../../../../reseller.en-US/SSL-VPN Quick Start/Mac client remote access.md#).

**Note:** The IP address ranges of clients cannot conflict with the VSwitch IP address range of the VPC.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/15554652803238_en-US.png)

## Use IPsec-VPN and SSL-VPN together {#section_ynl_fbp_dhb .section}

You can establish both IPsec-VPN and SSL-VPN connections to expand your network topology. After the connections are established, clients can access both the VPC and the connected office networks.

**Note:** All private IP address ranges to be connected cannot conflict with each other.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/15554652803239_en-US.png)

