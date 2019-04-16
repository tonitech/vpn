# Dual IPsec-VPN tunnel configuration {#concept_qrk_klg_xdb .concept}

This topic describes how to establish two IPsec-VPN tunnels with a VPN Gateway to implement active and standby tunnels. This configuration is suitable for when your local gateway has two public IP addresses.

## Overview {#section_km4_rsq_fhb .section}

You can connect a VPN Gateway with two public IP addresses \(in this example, they are labeled as IP1 and IP2\) to establish two IPsec-VPN connections, and enable health checks. Afterwards, you can set the weights of the corresponding two routes to set one route as the active route and the other route as the standby route. In this way, when the IP1-based Internet link is normal, all traffic between the on-premises data center and the VPC is forwarded only through this connection because it is the active tunnel. When the IP1-based Internet link is abnormal, all traffic between the on-premises data center and the VPC is directed to the standby tunnel.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155539447342233_en-US.png)

## Prerequisites {#section_oth_2mg_xdb .section}

-   The protocols IKEv1 and IKEv2 are supported by the gateway device located at the on-premises data center, and a static IP address is configured for the gateway device.

-   The IP address ranges used by the VPC and the on-premises data center do not conflict with each other.


## Step 1: Create a VPN Gateway {#section_vfk_2mz_wdb .section}

To create a VPN Gateway, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**.
3.  Click **Create VPN Gateway**.
4.  On the purchase page, configure the VPN Gateway and complete the payment. In this example, use the following configurations:
    -   **Region**: Select the region of the VPN Gateway. In this example, select **China \(Hangzhou\)**.

**Note:** In an actual scenario, make sure that the VPC and the VPN Gateway are in the same region.

    -   **Name**: Enter a name for the VPN Gateway to be created.

    -   **VPC**: Select the VPC to be connected.

    -   **Peak Bandwidth**: Select a peak bandwidth. The bandwidth is the Internet bandwidth of the VPN Gateway.

    -   **IPsec-VPN**: Choose whether to enable the IPsec-VPN feature. In this example, select **Enable**.

    -   **SSL-VPN**: Choose whether to enable the SSL-VPN feature.

    -   **SSL connections**: Select the maximum number of clients you want to connect to simultaneously.

**Note:** You can only configure this option after you enable the SSL-VPN feature.

    -   **Billing Cycle**: The billing cycle is set to **By Hour** by default.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155539447342221_en-US.png)


Go back to the VPN Gateways page, select the **China \(Hangzhou\)** region to view the created VPN Gateway.

The initial status of a VPN Gateway is **Preparing**, which indicates the initialization of the VPN Gateway and may take up to two minutes to be completed. When the status of the VPN Gateway changes to **Normal**, it indicates that the VPN Gateway is ready to use.

**Note:** It usually takes 1 to 5 minutes to create a VPN Gateway.

## Step 2: Create two customer gateways {#section_upz_wmz_wdb .section}

Create two customer gateways and register the two public IP addresses of the local gateway to the customer gateways. To do so, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **Customer Gateways**.
2.  Select the **China \(Hangzhou\)** region.
3.  Click **Create Customer Gateway**.
4.  Configure the customer gateway according to the following information:
    -   **Name**: Enter a name for the customer gateway to be created.

    -   **IP Address**: Enter one of the two public IP addresses of the gateway device at the on-premises data center.

    -   **Description**: Enter a description of the customer gateway.

5.  On the Create Customer Gateway page, click **+ Add** to add another customer gateway.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155539447342234_en-US.png)


## Step 3: Create two IPsec-VPN connections {#section_ty2_jnz_wdb .section}

Create two IPsec-VPN connections to connect the VPN Gateway with the two customer gateways. To do so, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select the **China \(Hangzhou\)**region.
3.  Click **Create IPsec Connection**.
4.  Configure the IPsec-VPN connection according to the following information and then click **OK**:
    -   **Name**: Enter a name for the IPsec-VPN connection to be created.

    -   **VPN Gateway**: Select the created VPN Gateway.

    -   **Customer Gateway**: Select one of the two created customer gateways.

    -   **Local Network**: Enter the IP address range of the VPC to be connected with the on-premises data center. In this example, enter 192.168.0.0/16. To add multiple local networks, click **+ Add Local Network**.

        **Note:** Only IKE v2 supports multiple local networks.

    -   **Remote Network**: Enter the CIDR block of the on-premises data center to be connected with the VPC. In this example, enter 172.16.0.0/12. To add multiple remote networks, click **+ Add Remote Network**.

        **Note:** Only IKE v2 supports multiple remote networks.

    -   **Effective Immediately**: Choose whether to delete the negotiated IPsec-VPN tunnel and re-initiate the negotiation.
        -   **Yes**: Re-initiates the negotiation immediately after the IPsec-VPN connection is created.
        -   **No**: Re-initiates the negotiation when traffic is detected in the tunnel.
    -   **Synchronize to VPN Route Table**: Choose whether to synchronize IPsec-VPN traffic routes to the VPN route table. We recommend that you select **Yes**.

-   **Yes**: The IPsec-VPN traffic routes are synchronized to the VPN route table after the IPsec-VPN connection is created.
-   **No**: The IPsec-VPN traffic routes are not synchronized to the VPN route table after the IPsec-VPN connection is created. You need to add gateway routes on the VPN Gateway page. For more information, see [VPN Gateway route overview](../../../../reseller.en-US/User Guide/Manage a VPN Gateway/Configure routes of a VPN Gateway/VPN Gateway route overview.md#).
    -   **Pre-Shared Key**: Enter the pre-shared key. This value must be the same as that configured in the local gateway.

    -   **Health Check**: Enable the health check feature and enter the destination IP address, source IP address, retry interval, and retry times.

        Use the default configurations for other parameters.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155539447342235_en-US.png)

5.  In the displayed dialog box, click **OK**.
6.  Find the target route entry, click **Publish** in the **Actions** column, and then in the displayed dialog box, click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155539447342236_en-US.png)

7.  Repeat the preceding steps to create another IPsec-VPN connection that connects to the other customer gateway.

## Step 4: Configure the local gateway {#section_ptn_44z_wdb .section}

To configure the local gateway, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select the **China \(Hangzhou\)** region.
3.  Find the target IPsec-VPN connection and click **Download Configuration**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155539447342237_en-US.png)

4.  Configure the local gateway accordingly. For more information, see [Configure local gateways](../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure local gateways/Configure an IPsec-VPN connection through a USG series Next-Generation Firewall device (Huawei).md#).

    The RemoteSubnet and LocalSubnet in the downloaded configurations are the converse in the actual operations of the local network and the remote network you configured when you create the IPsec-VPN connection. Specifically, from the perspective of VPN Gateway, the remote network is the on-premises data center and the local network is the VPC. However, from the perspective of the local gateway, LocalSubnet is the CIDR block of the on-premises data center and RemoteSubnet is the CIDR block of the VPC.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155539447342238_en-US.png)


## Step 5: Set route weights {#section_d44_shv_fhb .section}

To set route weights, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**.
2.  Select the region of the target VPN Gateway.
3.  Find the target VPN Gateway, and click the instance ID.
4.  On the **Policy-based Routing** tab page, find the target policy-based route and click **Edit** in the **Actions** column.
5.  In the displayed dialog box, set the weight to **100**.
6.  Repeat the preceding steps to set the weight of the other route to **0**.

