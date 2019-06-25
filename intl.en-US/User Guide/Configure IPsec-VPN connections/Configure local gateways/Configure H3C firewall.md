# Configure H3C firewall {#task_snz_rc2_xdb .task}

When using IPsec-VPN to create a site-to-site connection, you must configure the local gateway according to the IPsec connection configured for the Alibaba Cloud VPN Gateway. This document takes H3C firewall as an example to show how to configure the VPN settings.

-   Make sure you have configured IPsec connections. For more information, see [Establish a connection between a VPC and an on-premises data center](../../../../reseller.en-US/IPsec-VPN Quick Start/Establish a connection between a VPC and an on-premises data center.md#).

-   After you create an IPsec-VPN connection, download the configurations of the IPsec-VPN connection. For more information, see [EN-US\_TP\_13359.md\#](reseller.en-US/User Guide/Configure IPsec-VPN connections/Manage an IPsec-VPN connection/Create an IPsec-VPN connection.md#).

    In this tutorial, the configurations of the IPsec-VPN connection are as follows:

    -   IPsec-VPN configuration

|Configurations|Value|
|:-------------|:----|
|IKE|Authentication Algorithm|sha1|
|Encryption Algorithm|aes|
|DH Group|group2|
|IKE Version|ikev1|
|SA Life Cycle \(seconds\)|86400|
|Negotiation Mode|main|
|PSK|h3c|
|IPsec|Authentication Algorithm|sha1|
|Encryption Algorithm|aes|
|DH Group|group2|
|IKE Version|ikev1|
|SA Life Cycle \(seconds\)|86400|

    -   Network configurations

|Configuration|Value|
|:------------|:----|
|VPC|Private CIDR block|192.168.10.0/24|
|Public IP address of VPN Gateway|101.xxx.xxx.127|
|On-premises data center|Private CIDR block|192.168.66.0/24|
|Public IP address of local gateway|122.xxx.xxx.248|
|Uplink public port|Reth 1|
|Downlink private port|G 2/0/10|


1.  Log on to the firewall Web page and choose **Network** \> **VPN** \> **IPsec** \> **Policy**.
2.  Configure the H3C firewall IPsec policy based on the IPsec configurations of the Alibaba Cloud VPN Gateway. Click **Add** in the **Protected Data Stream** list, set the IP address range of the on-premises data center as the source IP address and the IP address range of the VPC as the destination IP address.
3.  Choose **IKE Proposal** \> **Create**. Configure the IKE proposal according to the IKE configurations of the Alibaba Cloud VPN Gateway.
4.  Choose **Network** \> **VPN** \> **IPsec** \> **Policy**.
5.  Select the new IPsec policy and click **Advanced Configuration**. 

    Configure the IPsec protocol according to the information of the IPsec connection configured for the Alibaba Cloud VPN Gateway.

6.  Choose **Policy** \> **Security Policy** \> **Create** to create the uplink security policy and downlink security policy. 

    The security policy configuration from the Alibaba Cloud VPC to the on-premises data center is shown in the following figure.

    The security policy configuration from the on-premises data center to the Alibaba Cloud VPC is shown in the following figure.

7.  Choose **Network** \> **Route** \> **Static Route**.
8.  Add the default route, set the uplink interface as the next hop of the outbound traffic. In this tutorial, no configuration is required.

