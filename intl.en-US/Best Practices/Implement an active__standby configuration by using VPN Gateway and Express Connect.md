# Implement an active/standby configuration by using VPN Gateway and Express Connect {#concept_mgb_qxf_xdb .concept}

This topic describes how to implement an active/standby configuration by using a VPN Gateway and a physical connection of Express Connect to improve the availability of your applications.

You can connect your on-premises data center to an Alibaba Cloud VPC through both a physical connection and an IPsec-VPN connection.

-   When the physical connection works normally, the traffic between the on-premises data center and the VPC is forwarded through the physical connection.
-   When the physical connection is abnormal, the traffic between the on-premises data center and the VPC is directed to the IPsec-VPN tunnel.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136915/155468806641822_en-US.png)

## Prerequisites {#section_n4r_fqp_fhb .section}

A physical connection is created to allow intercommunication between your on-premises data center and the VPC.

For more information, see [物理专线接入](../../../../../reseller.en-US/Getting Started (New Console)/Connect an on-premises IDC to a VPC through a physical connection.md#).

## Step 1: Create a VPN Gateway {#section_vfk_2mz_wdb .section}

To create a VPN Gateway, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**.
3.  Click **Create VPN Gateway**.
4.  On the purchase page, configure the VPN Gateway and complete the payment. In this example, use the following configurations:
    -   **Region**: Select the region of the VPN Gateway to be created. In this example, select **China \(Hangzhou\)**.

**Note:** In an actual scenario, make sure that the VPC and the VPN Gateway are in the same region.

    -   **Name**: Enter a name for the VPN Gateway to be created.

    -   **VPC**: Select the VPC to be connected.

    -   **Peak Bandwidth**: Select a peak bandwidth. The bandwidth is the Internet bandwidth of the VPN Gateway.

    -   **IPsec-VPN**: Choose whether to enable the IPsec-VPN feature. In this example, select **Enable**.

    -   **SSL-VPN**: Choose whether to enable the SSL-VPN feature.

    -   **SSL connections**: Select the maximum number of clients you want to connect to simultaneously.

**Note:** You can only configure this option after you enable the SSL-VPN feature.

    -   **Billing Cycle**: The billing cycle is set to **By Hour** by default.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155468806742221_en-US.png)


Go back to the VPN Gateways page, and select the **China \(Hangzhou\)** region to view the created VPN Gateway.

The initial status of a VPN Gateway is **Preparing**, which indicates the initialization of the VPN Gateway and may take up to two minutes to be completed. When the status of the VPN Gateway changes to **Normal**, it indicates that the VPN Gateway is ready to use.

**Note:** It usually takes 1 to 5 minutes to create a VPN Gateway.

## Step 2: Create a customer gateway {#section_upz_wmz_wdb .section}

Create a customer gateway and register the public IP address of the local gateway to the customer gateway. To do so, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **Customer Gateways**.
2.  Select the **China \(Hangzhou\)** region.
3.  Click **Create Customer Gateway**.
4.  Configure the customer gateway according to the following information:
    -   **Name**: Enter a name for the customer gateway to be created.

    -   **IP Address**: Enter the public IP address of the gateway device located at the on-premises data center.

    -   **Description**: Enter a description of the customer gateway.


## Step 3: Create an IPsec-VPN connection {#section_ty2_jnz_wdb .section}

Create an IPsec-VPN connection to connect the VPN Gateway with the customer gateway. To do so, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select the **China \(Hangzhou\)** region.
3.  Click **Create IPsec Connection**.
4.  Configure the IPsec-VPN connection according to the following information and then click **OK**.
    -   **Name**: Enter a name for the IPsec-VPN connection to be created.

    -   **VPN Gateway**: Select the created VPN Gateway.

    -   **Customer Gateway**: Select the created customer gateway.

    -   **Local Network**: Enter the IP address range of the VPC to be connected with the on-premises data center. In this example, enter 192.168.0.0/16. To add multiple local networks, click **+ Add Local Network**.

        **Note:** Only IKE v2 supports multiple local networks.

    -   **Remote Network**: Enter the CIDR block of the on-premises data center to be connected with the VPC. In this example, enter 172.16.0.0/12. To add multiple remote networks, click **+ Add Remote Network**.

        **Note:** Only IKE v2 supports multiple remote networks.

    -   **Effective Immediately**: Choose whether to delete the negotiated IPsec-VPN tunnel and re-initiate the negotiation.
        -   **Yes**: Re-initiates the negotiation immediately after the IPsec-VPN connection is created.
        -   **No**: Re-initiates the negotiation when traffic is detected in the tunnel.
    -   **Synchronize to VPN Route Table**: Choose whether to synchronize IPsec-VPN traffic routes to the VPN route table. We recommend that you select **Yes**.

-   **Yes**: The IPsec-VPN traffic routes are synchronized to the VPN route table after the IPsec-VPN connection is created.
-   **No**: The IPsec-VPN traffic routes are not synchronized to the VPN route table after the IPsec-VPN connection is created. You need to add gateway routes on the VPN Gateway page. For more information, see [网关路由概述](../../../../../reseller.en-US/User Guide/Manage a VPN Gateway/Configure routes of a VPN Gateway/VPN Gateway route overview.md#).
    -   **Pre-Shared Key**: Enter the pre-shared key. This value must be the same as that configured in the local gateway.

    -   **Health Check**: Enable the health check feature and enter the destination IP address, source IP address, retry interval, and retry times.

        Use the default configurations for other parameters.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155468806742235_en-US.png)

5.  In the displayed dialog box, click **OK**.
6.  Find the target route entry, click **Publish** in the **Actions** column, and then in the displayed dialog box, click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155468806742236_en-US.png)


## Step 4: Configure the local gateway {#section_ptn_44z_wdb .section}

To configure the local gateway, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select the **China \(Hangzhou\)** region.
3.  Find the target IPsec-VPN connection and click **Download Configuration**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155468806742237_en-US.png)

4.  Configure the local gateway based on the downloaded configurations of the IPsec-VPN connection. For more information, see [本地网关配置](../../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure local gateways/Configure an IPsec-VPN connection through a USG series Next-Generation Firewall device (Huawei).md#).

    The items RemoteSubnet and LocalSubnet in the downloaded configurations operate converse to the setup of the local network and the remote network you configured when you create the IPsec-VPN connection. Specifically, from the perspective of VPN Gateway, the remote network is the on-premises data center and the local network is the VPC. However, from the perspective of the local gateway, LocalSubnet is the CIDR block of the on-premises data center and RemoteSubnet is the CIDR block of the VPC.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136912/155468806742238_en-US.png)


## Step 5: Configure health checks for the VBR of the physical connection {#section_bkr_hnp_fhb .section}

Configure health checks for the Virtual Border Router \(VBR\) of the physical connection to make sure that the status of the physical connection can be checked by the VPC and traffic can be directed to the IPsec-VPN connection when the physical connection fails.

For more information, see [配置健康检查](../../../../../reseller.en-US/User Guide (New Console)/Configure health checks.md#).

## Step 6: Configure the physical connection device {#section_j23_4pp_fhb .section}

Configure an active route and a standby route to direct to the VPC on the physical connection device, and enable the health check function for the physical connection. In this way, when the physical connection fails, traffic is forwarded to the IPsec-VPN connection.

