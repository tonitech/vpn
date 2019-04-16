# Tutorial introduction {#concept_d52_4lz_wdb .concept}

This topic describes how to create a site-to-site VPN connection through IPsec-VPN.

## Prerequisites {#section_jwb_plz_wdb .section}

Before creating a site-to-site VPN connection, make sure the following conditions are met:

-   The protocols IKEv1 and IKEv2 are supported by the gateway device located at the on-premises data center, and a static IP address is configured for the gateway device.

-   The IP address ranges used by the VPC and the on-premises data center do not conflict with each other.


## Procedure {#section_lwb_plz_wdb .section}

The following figure shows the procedure of establishing a site-to-site VPN connection through IPsec-VPN.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13350/155538267242184_en-US.png)

1.  Create a VPN Gateway.

    Enable the IPsec-VPN function. Up to 10 IPsec-VPN connections can be established in a VPN Gateway.

2.  Create a customer gateway.

    Create a customer gateway, and then upload the configuration of the local gateway to Alibaba Cloud. A customer gateway can be connected to multiple VPN Gateways.

3.  Create an IPsec-VPN connection.

    Create an IPsec-VPN connection to implement an encrypted communication tunnel between your on-premises data center and the VPN Gateway. We recommend that you synchronize the route entries of the data flow that needs to be encrypted to the VPN route table.

4.  Configure the local gateway.

    Configure the local gateway according to the IPsec-VPN connection configurations. For more information, see [本地CPE配置](../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure local gateways/Configure an IPsec-VPN connection through a USG series Next-Generation Firewall device (Huawei).md#).

5.  Test the connectivity.

    Log on to an ECS instance that does not have a public IP address in the target Alibaba Cloud VPC. Then, ping the private IP address of a host in your on-premises data center to test if the VPC and the on-premises data center can communicate with each other.


