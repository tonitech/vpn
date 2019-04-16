# Create a site-to-site connection through IPsec-VPN {#concept_c4h_slz_wdb .concept}

This topic describes how to create a site-to-site VPN connection through IPsec-VPN to connect an Alibaba Cloud VPC with an on-premises data center.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/155538150342201_en-US.png)

## Prerequisites {#section_q3w_ylz_wdb .section}

You must meet the following requirements before creating an IPsec-VPN connection:

-   The protocols IKEv1 and IKEv2 are supported by the gateway device located at the on-premises data center, and a static IP address is configured for the gateway device.

-   The IP address ranges used by the VPC and the on-premises data center do not conflict with each other.


## Step 1: Create a VPN Gateway {#section_vfk_2mz_wdb .section}

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**.
3.  Click **Create VPN Gateway**.
4.  On the purchase page, configure the VPN Gateway and complete the payment. In this example, use the following configurations:
    -   **Region**: Select the region of the VPN Gateway. In this example, select **China \(Hangzhou\)**.

**Note:** In an actual scenario, make sure that the VPC and the VPN Gateway are in the same region.

    -   **Name**: Enter a name for the VPN Gateway to be created.

    -   **VPC**: Select the VPC to be connected.

    -   **Peak Bandwidth**: Select a peak bandwidth. The bandwidth is the Internet bandwidth of the VPN Gateway.

    -   **IPsec-VPN**: Select whether to enable the IPsec-VPN feature.

    -   **SSL-VPN**: Select whether to enable the SSL-VPN feature.

    -   **SSL connections**: Select the maximum number of clients you want to connect to simultaneously.

**Note:** You can only configure this option after you enable the SSL-VPN feature.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/155538150342203_en-US.png)

    -   **Billing Cycle**: The billing cycle is set to **By Hour** by default.

Go back to the VPN Gateways page and select the **China \(Hangzhou\)** region to view the created VPN Gateway.

The initial status of a VPN Gateway is **Preparing**, which indicates the initialization of the VPN Gateway and may take up to two minutes to be completed. When the status of the VPN Gateway changes to **Normal**, it indicates that the VPN Gateway is ready to use.

**Note:** It usually takes 1 to 5 minutes to create a VPN Gateway.

## Step 2: Create a customer gateway {#section_upz_wmz_wdb .section}

1.  In the left-side navigation pane, choose **VPN** \> **Customer Gateways**.
2.  Select the **China \(Hangzhou\)** region.
3.  Click **Create Customer Gateway**.
4.  Configure the customer gateway according to the following information, and then click **OK**.
    -   **Name**: Enter a name for the customer gateway to be created.

    -   **IP Address**: Enter the public IP address configured for the gateway device of the on-premises data center.

    -   **Description**: Enter a description of the customer gateway.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15553815033314_en-US.png)

        You can also click **+** to add multiple customer gateways.


## Step 3: Create an IPsec-VPN connection {#section_ty2_jnz_wdb .section}

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select the **China \(Hangzhou\)** region.
3.  Click **Create IPsec Connection**.
4.  Configure the IPsec-VPN connection according to the following information and then click **OK**:
    -   **Name**: Enter a name for the IPsec-VPN connection.

    -   **VPN Gateway**: Select the created VPN Gateway.

    -   **Customer Gateway**: Select the created customer gateway.

    -   **Local Network**: Enter the IP address range of the VPC to be connected with the on-premises data center. In this example, enter 192.168.0.0/16. To add multiple local networks, click **+ Add Local Network**.

        **Note:** Only IKE v2 supports multiple local networks.

    -   **Remote Network**: Enter the CIDR block of the on-premises data center to be connected with the VPC. In this example, enter 172.16.0.0/12. To add multiple local networks, click **+ Add Remote Network**.

        **Note:** Only IKE v2 supports multiple local networks.

    -   **Effective Immediately**: Choose whether to delete the negotiated IPsec-VPN tunnel and re-initiate the negotiation.
        -   **Yes**: Re-initiates the negotiation immediately after the IPsec-VPN connection is created.
        -   **No**: Re-initiates the negotiation when traffic is detected in the tunnel.
    -   **Synchronize to VPN Route Table**: Choose whether to synchronize IPsec-VPN traffic routes to the VPN route table. We recommend that you select **Yes**.

-   **Yes**: The IPsec-VPN traffic routes are synchronized to the VPN route table after the IPsec-VPN connection is created.
-   **No**: The IPsec-VPN traffic routes are not synchronized to the VPN route table after the IPsec-VPN connection is created. You need to add gateway routes on the VPN Gateway page.
    -   **Pre-Shared Key**: Enter a pre-shared key. This value must be the same as that configured in the local gateway.

        Use the default configurations for other parameters.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15553815033315_en-US.png)

5.  In the displayed dialog box, click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/155538150342211_en-US.png)

6.  Find the target route entry, click **Publish** in the **Actions** column, and then in the displayed dialog box, click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/155538150342213_en-US.png)


## Step 4: Configure the local gateway {#section_ptn_44z_wdb .section}

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select the **China \(Hangzhou\)** region.
3.  Find the target IPsec-VPN connection and click **Download Configuration**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/155538150342207_en-US.png)

4.  Configure the local gateway accordingly. For more information, see [本地网关配置](../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure local gateways/Configure an IPsec-VPN connection through a USG series Next-Generation Firewall device (Huawei).md#).

    The RemoteSubnet and LocalSubnet in the download configuration are the opposite of the local network and the remote network when creating an IPsec-VPN connection. From the perspective of VPN Gateway, the remote network is the on-premises data center and the local network is the VPC.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15553815033317_en-US.png)


## Step 5: Test the connectivity {#section_ojw_ylz_wdb .section}

Log on to an ECS instance that does not have a public IP address in the target Alibaba Cloud VPC. Then, ping the private IP address of a host in your on-premises data center to test if the VPC and the on-premises data center can communicate with each other.

