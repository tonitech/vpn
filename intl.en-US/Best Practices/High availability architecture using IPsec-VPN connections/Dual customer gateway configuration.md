# Dual customer gateway configuration {#concept_qrk_klg_xdb .concept}

You can deploy two local gateways and connect the two local gateways to a VPN Gateway to create two IPsec-VPN connections. In this way, you can implement an IPsec-VPN connection redundancy.

## Solution {#section_mtr_t5g_fhb .section}

As shown in the following figure, you can connect each of the two customer gateways to the VPN Gateway to create two IPsec-VPN tunnels. Then, you can enable health checks for the two IPsec-VPN tunnels and make sure that the two IPsec-VPN tunnels are negotiated successfully. After that, if a health check detects that one customer gateway is abnormal, the traffic switches to the other customer gateway automatically.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136913/155468801641592_en-US.png)

## Prerequisites {#section_oth_2mg_xdb .section}

Make sure that the following requirements are met before you begin:

-   The protocols IKEv1 and IKEv2 are supported by the gateway devices located at your on-premises data center, and static IP addresses are configured for the gateway devices.

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

**Note:** You can configure this option only after you enable the SSL-VPN feature.

    -   **Billing Cycle**: The billing cycle is set to **By Hour** by default.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136913/155468801641710_en-US.png)


Go back to the VPN Gateways page and select the **China \(Hangzhou\)** region to view the created VPN Gateway.

The initial status of a VPN Gateway is **Preparing**, which indicates the initialization of the VPN Gateway and may take up to two minutes to be completed. When the status of the VPN Gateway changes to **Normal**, it indicates that the VPN Gateway is ready to use.

**Note:** It usually takes one to five minutes to create a VPN Gateway.

## Step 2: Create two customer gateways {#section_upz_wmz_wdb .section}

Create two customer gateways and register the public IP addresses of the local gateway devices to the customer gateways. To do so, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **Customer Gateways**.
2.  Select the **China \(Hangzhou\)** region.
3.  Click **Create Customer Gateway**.
4.  Configure the customer gateway according to the following information:
    -   **Name**: Enter a name for the customer gateway to be created.

    -   **IP Address**: Enter the public IP address of the gateway device at the on-premises data center.

    -   **Description**: Enter a description of the customer gateway.

5.  On the Create Customer Gateway page, click **+ Add** to add another customer gateway.
6.  Click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136913/155468801641711_en-US.png)


## Step 3: Create two IPsec-VPN connections {#section_ty2_jnz_wdb .section}

Create two IPsec-VPN connections to connect the VPN Gateway with the two customer gateways. To do so, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select the **China \(Hangzhou\) region**.
3.  Click **Create IPsec Connection**.
4.  Configure the IPsec-VPN connection according to the following information and then click **OK**:
    -   **Name**: Enter a name for the IPsec-VPN connection.

    -   **VPN Gateway**: Select the created VPN Gateway.

    -   **Customer Gateway**: Select one of the two created customer gateways.

    -   **Local Network**: Enter the IP address range of the VPC to be connected with the on-premises data center. In this example, enter 192.168.0.0/16. To add multiple local networks, click **+ Add Local Network**.

        **Note:** Only IKE v2 supports multiple local networks.

    -   **Remote Network**: Enter the CIDR block of the on-premises data center to be connected with the VPC. In this example, enter 172.16.0.0/12. To add multiple remote networks, click **+ Add Remote Network**.

        **Note:** Only IKE v2 supports multiple local networks.

    -   **Effective Immediately**: Choose whether to delete the negotiated IPsec-VPN tunnel and re-initiate the negotiation.
        -   **Yes**: Re-initiates the negotiation immediately after the IPsec-VPN connection is created.
        -   **No**: Re-initiates the negotiation when traffic is detected in the tunnel.
    -   **Synchronize to VPN Route Table**: Choose whether to synchronize IPsec-VPN traffic routes to the VPN route table. We recommend that you select **Yes**.

-   **Yes**: The IPsec-VPN traffic routes are synchronized to the VPN route table after the IPsec-VPN connection is created.
-   **No**: The IPsec-VPN traffic routes are not synchronized to the VPN route table after the IPsec-VPN connection is created. You need to add gateway routes on the VPN Gateway page. For more information, see [网关路由概述](../../../../../reseller.en-US/User Guide/Manage a VPN Gateway/Configure routes of a VPN Gateway/VPN Gateway route overview.md#).
    -   **Pre-Shared Key**: Enter the pre-shared key. This value must be the same as that configured in the local gateway.

    -   **Health Check**: Enable the health check feature and enter the destination IP address, source IP address, retry interval, and retry times.

        Use the default configurations for other parameters.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136913/155468801641712_en-US.png)

5.  In the displayed dialog box, click **OK**.
6.  Find the target route entry, click **Publish** in the **Actions** column, and then in the displayed dialog box, click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136913/155468801641712_en-US.png)

7.  Repeat the preceding steps to create another IPsec-VPN connection that connects to the other customer gateway.

## Step 4: Configure the local gateways {#section_ptn_44z_wdb .section}

To configure the local gateways, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select the **China \(Hangzhou\)** region.
3.  Find the target IPsec-VPN connection and click **Download Configuration**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136913/155468801641714_en-US.png)

4.  Configure the local gateways by loading the downloaded IPsec-VPN connection configurations to the local gateway device. For more information, see [本地网关配置](../../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure local gateways/Configure an IPsec-VPN connection through a USG series Next-Generation Firewall device (Huawei).md#).

    The RemoteSubnet and LocalSubnet in the downloaded configurations are converse in operation of the local network and the remote network you configured when you create the IPsec-VPN connection. Specifically, from the perspective of VPN Gateway, the remote network is the on-premises data center and the local network is the VPC. However, from the perspective of the local gateway, LocalSubnet is the CIDR block of the on-premises data center and RemoteSubnet is the CIDR block of the VPC.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136913/155468801641715_en-US.png)


