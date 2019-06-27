# Implement an active/standby configuration by using VPN Gateway and Express Connect {#concept_mgb_qxf_xdb .concept}

This topic describes how to implement an active/standby configuration by using a VPN Gateway and a physical connection of Express Connect to improve the availability of your applications.

You can connect your on-premises data center to an Alibaba Cloud VPC through both a physical connection and an IPsec-VPN connection.

-   When the physical connection works normally, the traffic between the on-premises data center and the VPC is forwarded through the physical connection.
-   When the physical connection is abnormal, the traffic between the on-premises data center and the VPC is directed to the IPsec-VPN tunnel.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136915/156161396541822_en-US.png)

## Prerequisites {#section_n4r_fqp_fhb .section}

A physical connection is created to allow intercommunication between your on-premises data center and the VPC.

For more information, see [Connect an on-premises IDC to a VPC through a physical connection](../../../../../reseller.en-US/Getting Started (New Console)/Connect an on-premises IDC to a VPC through a physical connection.md#).

## Step 1: Create a VPN Gateway {#section_jjp_86p_ey9 .section}

To create a VPN Gateway, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**.
3.  On the VPN Gateways page, click **Create VPN Gateway**.
4.  On the purchase page, configure the VPN Gateway according to the following information and click **Buy Now**.
    -    **Name**: Enter the name of the VPN Gateway.
    -    **Region**: Select the region to which the VPN Gateway belongs.

        **Note:** Make sure that the VPC and the VPN Gateway are in the same region.

    -    **VPC**: Select the VPC to be connected.
    -    **Peak Bandwidth**: Select a bandwidth. The bandwidth is the Internet bandwidth of the VPN Gateway.
    -    **IPsec-VPN**: Select whether to enable the IPsec-VPN feature.
    -    **SSL-VPN**: Select whether to enable the SSL-VPN feature. The SSL-VPN feature allows you to connect to a VPC from a computer anywhere.
    -    **SSL connections**: Select the maximum number of clients you want to connect to simultaneously.

        **Note:** You can only configure this option after you enable the SSL-VPN feature.

    -    **Billing Cycle**: Select the validity period of the purchase.
5.  Go back to the VPN Gateways page to view the created VPN Gateway.

    The initial status of a VPN Gateway is Preparing. It changes to Normal in about two minutes. When it changes to Normal, it indicates that the VPN Gateway is ready to use.

    **Note:** It usually takes 1 to 5 minutes to create a VPN Gateway.


## Step 2: Create a customer gateway {#section_upz_wmz_wdb .section}

Create a customer gateway and register the public IP address of the local gateway to the customer gateway. To do so, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **Customer Gateways**.
2.  Select a region.
3.  On the Customer Gateways page, click **Create Customer Gateway**.
4.  On the Create Customer Gateway page, configure the customer gateway according to the following information, and click **OK**.
    -    **Name**: Enter a customer gateway name.
    -    **IP Address**: Enter the public IP address of the local gateway.
    -    **Description**: Enter a description of the customer gateway.

## Step 3: Create an IPsec-VPN connection {#section_ty2_jnz_wdb .section}

To create an IPsec-VPN connection, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select a region.
3.  On the IPsec Connections page, click **Create IPsec Connection**.
4.  Configure the IPsec-VPN connection according to the following information and click **OK**.
    -    **Name**: Enter the name of the IPsec-VPN connection.
    -    **VPN Gateway**: Select the created VPN Gateway.
    -    **Customer Gateway**: Select the created customer gateway.
    -    **Local Network**: Enter the IP address range of the VPC to which the selected VPN Gateway belongs.
    -    **Destination CIDR Block**: Enter the CIDR block of the local data center.
    -    **Effective Immediately**: Select whether to start the negotiation immediately.
        -   Yes: Start the negotiation immediately once the configuration is complete.
        -   No: Start the negotiation only when traffic is detected in the tunnel.
    -    **Pre-Shared Key**: Enter a pre-shared key. This value must be the same as the one configured in the local gateway.
    -    **Health Check**: Enable health checks and enter the destination IP address, source IP address, retry interval, and number of retries.

        Use the default configurations for other parameters.


## Step 4: Configure the local gateway {#section_zqs_g2p_z1x .section}

To configure the local gateway, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select a region.
3.  On the IPsec Connections page, find the target IPsec-VPN connection, and click **Download Configuration** in the **Actions** column.
4.  Configure the local gateway accordingly. For more information, see [Local gateway configuration](../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure local gateways/Configure an IPsec-VPN connection through a USG series Next-Generation Firewall device (Huawei).md#).

    The items RemoteSubnet and LocalSubnet in the downloaded configurations operate converse to the setup of the local network and the remote network you configured when you create the IPsec-VPN connection. Specifically, from the perspective of VPN Gateway, the remote network is the on-premises data center and the local network is the VPC. However, from the perspective of the local gateway, LocalSubnet is the CIDR block of the on-premises data center and RemoteSubnet is the CIDR block of the VPC.


## Step 5: Configure a route for the VPN Gateway {#section_bn6_4s3_9tw .section}

To configure a route of the VPN Gateway, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**.
2.  Select the region of the target VPN Gateway.
3.  On the VPN Gateways page, find the target VPN Gateway and click the instance ID in the Instance ID/Name column.
4.  On the Destination-based Routing page, click **Add Route Entry**.
5.  On the Add Route Entry page, configure a destination-based route according to the following information, and click **OK**.
    -    **Destination CIDR Block**: Enter the private CIDR block of the on-premises data center.
    -    **Next Hop**: Select the target IPsec-VPN connection instance.
    -    **Publish to VPC**: Select whether to publish the new route to the VPC route table. In this example, select Yes.
    -    **Weight**: Select a weight. In this tutorial, select 100.

## Step 6: Configure health checks for the VBR of the physical connection {#section_bkr_hnp_fhb .section}

Configure health checks for the Virtual Border Router \(VBR\) of the physical connection to make sure that the status of the physical connection can be checked by the VPC and traffic can be directed to the IPsec-VPN connection when the physical connection fails.

For more information, see [Configure health checks](../../../../../reseller.en-US/Common Configurations/Configure health checks.md#).

## Step 7: Configure the local gateway {#section_j23_4pp_fhb .section}

Configure an active route and a standby route that point to the VPC on the local gateway device, and enable the health check function for the physical connection. In this way, when the physical connection fails, traffic is forwarded to the IPsec-VPN connection.

