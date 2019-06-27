# Establish a connection between two VPCs {#concept_c4h_slz_wdb .concept}

This topic describes how to create an IPsec-VPN connection to connect two VPCs.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15616141423319_en-US.png)

Two VPCs under the same account \(labeled VPC1 and VPC2\) are used as an example in this topic. The procedure of connecting two VPCs of different accounts is the same as that of connecting two VPCs under the same account. The only difference is that you must obtain the public IP address of the peer VPN Gateway and use this IP address to create a customer gateway.

|VPC name|VPC CIDR block|VPC ID|ECS instance name|
|:-------|:-------------|:-----|:----------------|
|VPC1|172.25.0.0/12|vpc-xxxxz0|ECS1|
|VPC2|10.0.0.0/8|vpc-xxxxut|ECS2|

**Note:** VPN Gateway enables communication by creating an encrypted tunnel over the Internet, which means the communication performance depends on the quality of the Internet connection. If you have high requirements regarding the communication quality, you can use Express Connect. For more information, see [../../../../dita-oss-bucket/SP\_72/DNexpressconnect1847151/EN-US\_TP\_13830.md\#](../../../../reseller.en-US/Peering connections/Interconnect two VPCs under the same account.md#) and [../../../../dita-oss-bucket/SP\_72/DNexpressconnect1847151/EN-US\_TP\_13829.md\#](../../../../reseller.en-US/Peering connections/Interconnect two VPCs under different accounts.md#).

## Before you begin {#section_q3w_ylz_wdb .section}

The IP address ranges of the two VPCs do not conflict with each other.

## Step 1: Create two VPN Gateways {#section_vfk_2mz_wdb .section}

To create a VPN Gateway, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**.
3.  On the VPN Gateways page, click **Create VPN Gateway**.
4.  On the purchase page, configure the VPN Gateway according to the following information, and click **Buy Now**.
    -   **Name**: Enter the name of the VPN Gateway.
    -   **Region**: Select the region to which the VPN Gateway belongs.

        **Note:** Make sure that the VPC and the VPN Gateway are in the same region.

    -   **VPC**: Select the VPC to be connected.
    -   **Peak Bandwidth**: Select a bandwidth. The bandwidth is the Internet bandwidth of the VPN Gateway.
    -   **IPsec-VPN**: Select whether to enable the IPsec-VPN feature.
    -   **SSL-VPN**: Select whether to enable the SSL-VPN feature. The SSL-VPN feature allows you to connect to a VPC from a computer anywhere.
    -   **SSL connections**: Select the maximum number of clients you want to connect to simultaneously.

        **Note:** You can only configure this option after you enable the SSL-VPN feature.

    -   **Billing Cycle**: Select the validity period of the purchase.
5.  Repeat the preceding steps to create a VPN Gateway for the other VPC.

    The state of the newly created VPN gateway is in preparation and changes to normal for about two minutes or so. When it changes to Normal, it indicates that the VPN Gateway is ready to use. When the VPN gateway is created, the system automatically assigns two public IP addresses.

    **Note:** It usually takes 1 to 5 minutes to create a VPN Gateway.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15616141423320_en-US.png)

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

To create a customer gateway, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **Customer Gateways**.
2.  Select a region.
3.  On the Customer Gateways page, click **Create Customer Gateway**.
4.  On the Create Customer Gateway page, configure the customer gateway according to the following information, and click **OK**.
    -   **Name**: Enter a customer gateway name.
    -   **IP Address**: Enter the public IP address of the local gateway.
    -   **Description**: Enter a description of the customer gateway.
5.  Repeat the preceding steps to create another customer gateway by using the public IP address of the other VPN Gateway.

    After creating two customer Gateways, the relationship among VPCs, VPN Gateways, and customer gateways is as follows:

    |VPC|VPN Gateway|IP address|customer gateway|
    |:--|:----------|:---------|:---------------|
    | Name: VPC1

 ID: vpc-xxxxz0

 IP address range: 172.16.0.0/12

 |vpn-xxxxxqwj|121.xxx.xx.143|user\_VPC1|
    | Name: PC2

 ID: vpc-xxxxut

 IP address range: 10.0.0.0/8

 |vpn-xxxxxl5z|118.xxx.xx.149|user\_VPC|


## Step 3: Create two IPsec-VPN connections {#section_ty2_jnz_wdb .section}

After creating the VPN Gateways and the customer gateways, you must create two IPsec-VPN connections to build the VPN channels:

1.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
2.  Select a region.
3.  On the IPsec Connections page, click **Create IPsec Connection**.
4.  On the Create IPsec Connection page, configure the IPsec-VPN connection according to the following information and click **OK**.
    -   **Name**: Enter a name for the IPsec-VPN connection.
    -   **VPN Gateway**: Select the created VPN Gateway. In this example, select the VPN Gateway vpn-xxxxxqwj of VPC1.
    -   **Customer Gateway**: Select the created customer gateway. In this example, select the customer gateway user\_VPC2 of VPC2.
    -   **Local Network**: Enter the CIDR block of the VPC to which the selected VPN Gateway belongs. In this example, enter the CIDR block 172.16.0.0/12 of VPC1.
    -   **Remote Network**: Enter the CIDR block of the peer VPC. In this example, enter the CIDR block 10.0.0.0/8 of VPC2.
    -   **Effective Immediately**: Select whether to start the negotiation immediately.
        -   Yes: Start the negotiation immediately once the configuration is complete.
        -   No: Start the negotiation only when traffic is detected in the tunnel.
    -   **Pre-Shared Key**: Enter a pre-shared key. In this example, enter 1234567. This value must be the same as that configured in the other IPsec-VPN connection.
    -   **Health Check**: Enable health checks and enter the destination IP address, source IP address, retry interval, and number of retries.

        Use the default configurations for other parameters.

5.  Repeat the preceding steps to create an IPsec-VPN connection for the other VPC.

## Step 4: Configure a route for each VPN Gateway {#section_3n7_3pd_963 .section}

To configure a route for a VPN Gateway, follow these steps:

1.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**.
2.  Select the region of the target VPN Gateway.
3.  On the VPN Gateways page, find the target VPN Gateway and click the instance ID in the Instance ID/Name column.
4.  On the Destination-based Routing page, click **Add Route Entry**.
5.  On the Add Route Entry page, configure the destination-based route according to the following information and click **OK**.
    -   **Destination CIDR Block**: Enter the private CIDR block of VPC2.
    -   **Next Hop**: Select the target IPsec-VPN connection instance.
    -   **Publish to VPC**: Select whether to publish the new route to the VPC route table. In this example, select Yes.
    -   **Weight**: Select a weight. In this example, select 100.
6.  Repeat the preceding steps to configure a route for the other VPN Gateway.

## Step 5: Test the connection {#section_ojw_ylz_wdb .section}

Log on to ECS1, and then ping the private IP address of ECS2 to check whether the connection is established.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15616141433323_en-US.png)

