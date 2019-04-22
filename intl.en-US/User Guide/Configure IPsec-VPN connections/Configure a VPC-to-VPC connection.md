# Configure a VPC-to-VPC connection {#concept_c4h_slz_wdb .concept}

This topic describes how to create an IPsec-VPN connection over the IPsec-VPN tunnel to connect two VPCs.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15558973473319_en-US.png)

Two VPCs under the same account \(labeled VPC1 and VPC2\) are used as an example in this topic. The procedure of connecting two VPCs of different accounts is the same as that of connecting two VPCs under the same account. The only difference is that you must obtain the public IP address of the peer VPN Gateway and then use this IP address to create a customer gateway.

|VPC name|VPC CIDR block|VPC ID|ECS instance name|
|:-------|:-------------|:-----|:----------------|
|VPC1|172.25.0.0/12|vpc-xxxxz0|ECS1|
|VPC2|10.0.0.0/8|vpc-xxxxut|ECS2|

**Note:** VPN Gateway enables communication by creating an encrypted tunnel over the Internet, which means the communication performance depends on the quality of the Internet connection. If you have high requirements regarding the communication quality, you can use Express Connect. For more information, see [Interconnect two VPCs under the same account](../../../../../reseller.en-US/Getting Started (New Console)/Interconnect two VPCs under the same account.md#) and [Interconnect two VPCs under different accounts](../../../../../reseller.en-US/Getting Started (New Console)/Interconnect two VPCs under different accounts.md#).

## Prerequisites {#section_q3w_ylz_wdb .section}

The IP address ranges of the two VPCs do not conflict with each other.

## Step 1: Create two VPN Gateways {#section_vfk_2mz_wdb .section}

1.  Log on to the VPC console.
2.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**.
3.  Click **Create VPN Gateway**.
4.  Configure the VPN Gateway and complete the payment. In this example, use the following configurations:
    -   **Region**: Select the region of the VPN Gateway. In this example, select **China \(Hangzhou\)**.

**Note:** Make sure that the VPC and the VPN Gateway are in the same region.

    -   **VPC**: Select the VPC to be connected.

    -   **Peak Bandwidth**: Select a bandwidth value. The bandwidth is the Internet bandwidth of the VPN Gateway.

    -   **IPsec-VPN**: Select **Enable**.

    -   **SSL-VPN**: Select whether to enable the SSL-VPN feature. The SSL-VPN feature allows you to connect to a VPC from a single computer anywhere.

    -   **SSL connections**: Select the maximum number of clients you want to connect to simultaneously.

**Note:** You can only configure this option after you enable the SSL-VPN feature.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15558973473313_en-US.png)

5.  Repeat the preceding steps to create a VPN Gateway for the other VPC.

    The initial status of a VPN Gateway is Preparing. It changes to Normal in about two minutes. When it changes to Normal, it indicates that the VPN Gateway is ready to use. After the two VPN Gateways are created, the system automatically assigns two Internet IP addresses.

    **Note:** It usually takes 1 to 5 minutes to create a VPN Gateway.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15558973473320_en-US.png)

    In this example, the public IP addresses assigned are 121. XXX. XX.143 and 118. XXX. XX.149, as shown in the following table.

    |VPC|VPN Gateway|IP address|
    |:--|:----------|:---------|
    | Name: VPC1

 ID: vpc-xxxxz0

 IP address range: 172.16.0.0/12

 |vpn-xxxxxqwj|118.xxx.xx.149|
    | Name: VPC2

 ID: vpc-xxxxut

 IP address range: 10.0.0.0/8

 |vpn-xxxxxl5z|121.xxx.xx.143|


## Step 2: Create two customer gateways {#section_upz_wmz_wdb .section}

1.  In the left-side navigation pane, choose **VPN** \> **Customer Gateways**.
2.  Select the **China \(Hangzhou\)** region.
3.  On the Customer Gateways page, click **Create Customer Gateway**.
4.  Configure the customer gateway according to the following information:
    -   **Name**: Enter a name for the customer gateway to be created.

    -   **IP Address**: Enter the public IP address of the VPN Gateway of the peer VPC.

    -   **Description**: Enter a description of the customer gateway.

5.  Repeat the preceding steps to create another customer gateway by using the public IP address of the other VPN Gateway.

    After creating two customer Gateways, the relationships between the VPCs, VPN Gateways, and customer gateways are as follows:

    |VPC|VPN Gateway|IP address|Customer gateway|
    |:--|:----------|:---------|:---------------|
    | Name: VPC1

 ID: vpc-xxxxz0

 IP address range: 172.16.0.0/12

 |vpn-xxxxxqwj|121.xxx.xx.143|user\_VPC1|
    | Name: VPC2

 ID: vpc-xxxxut

 IP address range: 10.0.0.0/8

 |vpn-xxxxxl5z|118.xxx.xx.149|user\_VPC|


## Step 3: Create two IPsec-VPN connections {#section_ty2_jnz_wdb .section}

After creating the VPN Gateways and the customer gateways, you must create two IPsec-VPN connections to build the VPN channels:

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select the **China \(Hangzhou\)** region.
3.  Click **Create IPsec Connection**.
4.  Configure the IPsec-VPN connection according to the following information and then click **OK**.
    -   **Name**: Enter a name for the IPsec-VPN connection to be created.

    -   **VPN Gateway**: Select the created VPN Gateway. In this example, select the VPN Gateway vpn-xxxxxqwj of VPC1.

    -   **Customer Gateway**: Select the customer gateway created by using the public IP address of the peer VPN Gateway. In this example, select the customer gateway user\_VPC2 of VPC2.

    -   **Local Network**: Enter the IP address range of the VPC to which the selected VPN Gateway belongs. In this example, enter the IP address range of VPC1, 172.16.0.0/12. To add multiple local networks, click **+ Add Local Network**.

        **Note:** Only IKE V2 supports multiple local networks.

    -   **Remote Network**: Enter the IP address range of the peer VPC. In this example, enter the IP address range of VPC2, 10.0.0.0/8. To add multiple remote networks, click **+ Add Remote Network**.

        **Note:** Only IKE V2 supports multiple remote networks.

    -   **Effective Immediately**: Choose whether to delete the negotiated IPsec-VPN tunnel and re-initiate the negotiation.
        -   **Yes**: Re-initiates the negotiation immediately after the IPsec-VPN connection is created.
        -   **No**: Re-initiates the negotiation when traffic is detected in the tunnel.
    -   **Synchronize with the VPN Route Table**: Choose whether to synchronize IPsec-VPN traffic routes to the VPN route table. We recommend that you select **Yes**.

-   **Yes**: The IPsec-VPN traffic routes are synchronized to the VPN route table after the IPsec-VPN connection is created.
-   **No**: The IPsec-VPN traffic routes are not synchronized to the VPN route table after the IPsec-VPN connection is created. You need to add gateway routes on the VPN Gateway page. For more information, see [VPN Gateway route overview](reseller.en-US/User Guide/Manage a VPN Gateway/Configure routes of a VPN Gateway/VPN Gateway route overview.md#).
    -   **Pre-Shared Key**: Enter a pre-shared key. In this example, enter 123456. This value must be the same as that configured in the other IPsec-VPN connection.

    -   **Health Check**: Enable the health check function and enter the destination IP address, source IP address, retry interval, and retry times.

5.  In the displayed dialog box, click **OK**.
6.  Find the target route entry, click **Publish** in the **Actions** column, and then in the displayed dialog box, click **OK**.
7.  Repeat the preceding steps to create another IPsec-VPN connection.

    In this example, the IPsec-VPN connection configurations of VPC1 are as follows:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15558973473321_en-US.png)

    In this example, the IPsec-VPN connection configurations of VPC2 are as follows:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15558973473322_en-US.png)


## Step 4: Verify the connection {#section_ojw_ylz_wdb .section}

Log on to ECS1, and then ping the private IP address of ECS2 to check whether the connection is established.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15558973473323_en-US.png)

