# Configure an IPsec-VPN connection through a USG series Next-Generation Firewall device \(Huawei\) {#concept_h4z_jdd_xdb .concept}

This topic describes how to configure an IPsec-VPN connection through a USG series Next-Generation Firewall device from Huawei \(known as USG series Huawei device\) to connect an on-premises data center. When you use IPsec-VPN to establish a site-to-site connection, you need to configure your local gateway devices after configuring Alibaba Cloud VPN Gateway.

Alibaba Cloud VPN Gateway supports the standard IKEv1 and IKEv2 protocols. Therefore, all devices that support these two protocols can connect to Alibaba Cloud VPN Gateway \(such as devices from Huawei, H3C, Hillstone, Sangfor, Cisco ASA, Juniper, SonicWall, Nokia, IBM, and Ixia\).

The following sections take a USG series device from Huawei as an example to describe the network scenario and the following table describes the corresponding network configurations.

|Network configuration|Example value|
|:--------------------|:------------|
|VPC|CIDR block of the VSwitch|192.168.10.0/24, 192.168.11.0/24|
|Public IP address of the VPN Gateway|47.xx.xx.10|
|On-premises data center|CIDR block of the intranet|10.10.10.0/24|
|Public IP address of the firewall|124.xx.xx.215/26|
|Upstream Internet interface|10GE1/0/0|
|Downstream intranet interface|10GE1/0/1|

**Note:** If the on-premises data center is associated with multiple CIDR blocks that need to connect with a VPC, we recommend that you create an equivalent number of IPsec-VPN connections on Alibaba Cloud so that each CIDR block of the on-premises data center is connected with a VPC CIDR block.

## Configure an IKEv1 VPN {#section_d12_sfd_xdb .section}

 **Prerequisites** 

-   An IPsec-VPN connection is created in an Alibaba Cloud VPC. For more information, see [EN-US\_TP\_13359.md\#](reseller.en-US/User Guide/Configure IPsec-VPN connections/Manage an IPsec-VPN connection/Create an IPsec-VPN connection.md#).

-   The configuration of the IPsec-VPN connection is downloaded. The configurations in the following table are used in this example.

|Protocol|Configuration|Example value|
|:-------|:------------|:------------|
|IKE|Authentication Algorithm|SHA-1|
|Encryption Algorithm|AES-128|
|DH Group|group 2|
|IKE Version|IKE v1|
|SA Life Cycle|86400|
|Negotiation Mode|main|
|PSK|123456|
|IPsec|Authentication Algorithm|SHA-1|
|Encryption Algorithm|AES-128|
|DH Group|group 2|
|IKE Version|IKE v1|
|SA Life Cycle|86400|
|Negotiation Mode|esp|


 **Procedure** 

To load customer gateway configurations to the USG series Huawei device, follow these steps:

1.  Go to the Huawei firewall management page. Choose **Network** \> **Interface** \> **Interface List**. Add the upstream Internet interface 10GE1/0/0 to the **untrust** security zone and set the public IP address; add the downstream intranet interface 10GE1/0/1 to the trust security zone, and then set the private IP address.
2.  Choose **Policy** \> **Security Policy** \> **Add** to create a security policy.
3.  Choose **Network** \> **IPsec** \> **IPsec Policy List** \> **Add**. Configure the peer site according to the following information:
    -    **Local Interface**: Select the upstream Internet interface. In this example, select 10GE1/0/0.

    -    **Peer Address**: Enter the public IP address of the VPN Gateway. In this example, enter 47.xx.xx. 10.

    -   Pre-Shared Key: The pre-shared key is the same as the PSK at the Alibaba Cloud side. In this example, enter 123456.

4.  On the Data Flow to Be Encrypted page, click **Add**. Add the data flow to be encrypted for all VSwitch CIDR blocks in the VPC according to the following information:
    -    **Source Address/Address-Set**: Enter the private IP address segment of the on-premises data center. In this example, enter 10.10.10.0/24.

    -    **Destination Address/Address-Set**: Enter the VSwitch IP address segment of the VPC. In this example, enter 192.168.10.0/24 and 192.168.11.0/24.

5.  On the IKE/IPSec Protocol page, click **Advanced**. Configure IKE protocol parameters based on the IPsec-VPN connection configurations that you downloaded.
6.  On the IPsec Parameters page, configure the IPSec protocol parameters based on the IPsec connection configurations that you downloaded.
7.  Choose **Network** \> **Route** \> **Static Route** \> **Static Route List** \> **Add** to configure static routes for the firewall. When you add a default route, the next hop is the public IP address of the firewall. When you add a route to the VPC, the next hop is the public IP address of the VPN Gateway.

## Configure an IKEv2 VPN {#section_uxm_djd_xdb .section}

 **Prerequisites** 

-   An IPsec-VPN connection is created in the Alibaba Cloud VPC.

-   The configuration of the IPsec-VPN connection is downloaded. The configurations in the following table are used in this example.

    |Protocol|Configuration|Example value|
    |:-------|:------------|:------------|
    |IKE|Authentication Algorithm|SHA-1|
    |Encryption Algorithm|AES-128|
    |DH Group|group 2|
    |IKE Version|IKE v2|
    |SA Life Cycle|86400|
    |PRF Algorithm|SHA-1|
    |PSK|123456|
    |IPsec|Authentication Algorithm|SHA-1|
    |Encryption Algorithm|AES-128|
    |DH Group|group 2|
    |IKE Version|Ike v2|
    |SA Life Cycle|86400|
    |Negotiation Mode|esp|


## Procedure {#section_r5v_dfd_xdb .section}

To load customer gateway configurations to USG series Huawei device, follow these steps:

1.  Go to the Huawei firewall management page. Choose **Network** \> **Interface** \> **Interface List**. Add the upstream Internet interface 10GE1/0/0 to the **untrust** security zone and set the public IP address; add the downstream intranet interface 10GE1/0/1 to the **trust** security zone, and then set the private IP address.
2.  Choose **Policy** \> **Security Policy** \> **Add** to create a security policy.
3.  Choose **Network** \> **IPsec** \> **IPsec Policy List** \> **Add**. Configure the peer site according to the following information:
    -    **Local Interface**: Select the firewall upstream Internet interface. In this example, select 10GE1/0/0.

    -    **Peer Address**: Enter the public IP address of the Alibaba Cloud VPN Gateway. In this example, enter 47.xx.xx. 10.

    -   Pre-Shared Key: The pre-shared key is the same as the PSK at the Alibaba Cloud side. In this example, enter 123456.

4.  On the Data Flow to Be Encrypted page, click **Add**. Add the data flow to be encrypted for all VSwitch CIDR blocks in the VPC according to the following information:
    -    **Source Address/Address-Set**: Enter the private IP address segment of the on-premises data center. In this example, enter 10.10.10.0/24.

    -    **Destination Address/Address-Set**: Enter the VSwitch IP address segment of the VPC. In this example, enter 192.168.10.0/24 and 192.168.11.0/24.

5.  On the IKE/IPSec Protocol page, click **Advanced**. Configure IKE parameters based on the IPsec-VPN connection configurations that you downloaded.
6.  On theIPsec Parameters page, configure the IPSec protocol parameters based on the IPsec connection that you downloaded.
7.  Choose **Network** \> **Route** \> **Static Route** \> **Static Route List** \> **Add** to configure static routes for the firewall. Among them, when you add a default route, the next one is the public network IP of the firewall; when adding a route to a VPC, jump to the public IP of the VPN gateway.

