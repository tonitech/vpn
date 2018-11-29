# Configure a VPC-to-VPC connection {#concept_c4h_slz_wdb .concept}

This tutorial illustrates how to create an IPsec-connection over the IPsec-VPN tunnel to connect two VPCs.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15434965213319_en-US.png)

The following two VPCs under the same account are used as an example in this tutorial. The procedure of connecting two VPCs of different accounts is the same as connecting two VPCs under the same account. The only difference is that you must obtain the public IP address of the peer VPN Gateway and use this IP address to create a customer gateway.

|VPC name|VPC name|VPC ID|VPC ID|
|:-------|:-------|:-----|:-----|
|VPC1|172.25.0.0/12|vpc-xxxxz0|ECS1|
|VPC2|10.0.0.0/8|vpc-xxxxut|ECS2|

**Note:** VPN Gateways enable communication by creating an encrypted tunnel over the Internet, and thus the communication performance depends on the quality of Internet connection. If the requirement on the communication quality is high, you can use Express Connect. For more information, see [Interconnect two VPCs under the same account](../../../../reseller.en-US/Getting Started (New Console)/Interconnect two VPCs under the same account.md#) and [Establish an intranet connection between VPCs under different accounts](../../../../reseller.en-US/Getting Started (New Console)/Establish an intranet connection between VPCs under different accounts.md#).

## Prerequisites {#section_q3w_ylz_wdb .section}

The IP address ranges of these two VPCs are not in conflict.

## Step 1: Create two VPN Gateways {#section_vfk_2mz_wdb .section}

1.  Log on to the VPC console.
2.  In the left-hand navigation pane, click**VPN** \> **VPN Gateways** .
3.  On the VPN Gateways page, click **Create VPN Gateway**.
4.  On the purchase page, configure the VPN Gateway and complete the payment. In this tutorial, the VPN Gateway uses the following configurations:
    -   **Region**: Select the region of the VPN Gateway. In this tutorial, **China \(Hangzhou\)** is selected.

**Note:** Make sure that the VPC and the VPN Gateway are in the same region.

    -   **VPC**: Select the VPC to be connected.

    -   **Bandwidth specification**: Select a bandwidth specification. The bandwidth specification is the Internet bandwidth of the VPN Gateway.

    -   **IPsec-VPN**: Select whether to enable the IPsec-VPN feature.

    -   **SSL-VPN**: Select whether to enable the SSL-VPN feature. The SSL-VPN feature allows you to connect to a VPC from a single computer anywhere.

    -   **Concurrent SSL Connections**: Select the maximum number of clients you want to connect to simultaneously.

**Note:** You can only configure this option after you enables the SSL-VPN feature.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15434965213313_en-US.png)

5.  Repeat the preceding steps to create a VPN Gateway for the other VPC.

    The initial status of a VPN Gateway is Preparing. It changes to Normal in about 2 minutes. When it changes to Normal, it indicates that the VPN Gateway is ready to use. After the VPN Gateway is created, the system automatically assigns two Internet IPs.

    **Note:** It usually takes 1 to 5 minutes to create a VPN Gateway.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15434965223320_en-US.png)

    In this tutorial, the public IP addresses assigned are 121. XXX. XX.143 and 118. XXX. XX.149, as shown in the following table.

    |VPC|VPN Gateway|IP address|
    |:--|:----------|:---------|
    | Name: VPC1

 ID: vpc-xxxxz0

 IP address range: 172.16.0.0/12

 |vpn-xxxxxqwj|118.xxx.xx.149|
    | Name: VPC2

 ID: vpc-xxxxut

 IP address range: 10.0.0.0/8

 |vpn-xxxxxl5z|121. XXX. XX.143|


## Step 2: Create two customer gateways {#section_upz_wmz_wdb .section}

1.  In the left-hand navigation pane, click**VPN** \> **Customer Gateways** .
2.  Select the China \(Hangzhou\) region.
3.  On the Customer Gateways page, click **Create Customer Gateway**.
4.  Configure the customer gateway according to the following information:
    -   **Name**: Enter the name of the customer gateway.

    -   **IP Address**: Enter the public IP address of the VPN Gateway of the peer VPC.

    -   **Description**: Enter the description of the customer gateway.

5.  Repeat these steps to create another customer gateway using the public IP address of the other VPN Gateway.

    After creating two customer Gateways in this tutorial, the relationship between VPC, VPN Gateways and customer gateways are as follows:

    |VPC|VPN Gateway|IP address|customer gateway|
    |:--|:----------|:---------|:---------------|
    | Name: VPC1

 ID: vpc-xxxxz0

 IP address range: 172.16.0.0/12

 |vpn-xxxxxqwj|121.xxx.xx.143|user\_VPC1|
    | Name: VPC2

 ID：vpc-xxxxut

 IP address range: 10.0.0.0/8

 |vpn-xxxxxl5z|118.xxx.xx.149|user\_VPC|


## Step 3: Create two IPsec connections {#section_ty2_jnz_wdb .section}

After creating the VPN Gateways and the customer gateways, you must create two IPsec connections to build the VPN channels:

1.  In the left-hand navigation pane, click**VPN** \> **IPsec Connections**.
2.  Select the China \(Hangzhou\) region.
3.  On the IPsec Connections page, click **Create IPsec Connection**.
4.  Configure the IPsec connection according to the following information:
    -   **Name**: Enter a name for the IPsec connection.

    -   **VPN Gateway**: Select the created VPN Gateway. In this tutorial, the VPN Gateway vpn-xxxxxqwj of VPC1 is selected.

    -   **Customer Gateway**: Select the customer gateway created by using the public IP address of the peer VPN Gateway. In this tutorial, the customer gateway user\_VPC2 of VPC2 is selected.

        .

    -   **Local Network**: Enter the IP address range of the VPC to which the selected VPN Gateway belongs. In this tutorial, the IP address range 172.16.0.0/12 of VPC1 is entered.

    -   **Remote Network**: Enter the IP address range of the peer VPC. In this tutorial, the IP address range 10.0.0.0/8 of VPC2 is entered.

    -   **Pre-Shared Key**: Enter a pre-shared key. In this tutorial, 123456 is entered. This value must be the same as configured in the other IPsec connection.

5.  Repeat these steps to create another IPsec connection.

    In this tutorial, the IPsec connection configurations of VPC1 are as follows:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15434965223321_en-US.png)

    In this tutorial, the IPsec connection configurations of VPC2 are as follows:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15434965223322_en-US.png)


## Step 4: Configure routes {#section_k1m_cpz_wdb .section}

1.  In the left-side navigation pane, click **Route Tables**.
2.  Select the region to which the connected VPC belongs. In this tutorial, the China \(Hangzhou\) region is selected.
3.  Find VPC1 and click **Manage**.
4.  On the Route Tables page, click **Add Route Entry**.
5.  Configure the route entry according to the following information and then click **OK**.
    -   **Destination CIDR Block**: Enter the IP address range of the peer VPC. In this tutorial, the IP address range 10.0.0.0/8 of VPC2 is entered.

    -   **Next Hop Type**: Select VPN Gateway.

    -   **VPN Gateway**: Select the VPN Gateway deployed in the local VPC. In this tutorial, the VPN Gateway created for VPC1 is selected.

6.  Repeat these steps to add a route entry for VPC2. In the route entry, the destination CIDR block is 172.16.0.0/12, and the next hop is the VPN Gateway of VPC2.

    In this tutorial, the route configurations are as follows:

    |VPC|Destination CIDR block|Next hop type|Next hop|
    |:--|:---------------------|:------------|:-------|
    |VPC1|10.0.0.0/8|VPN Gateway|The VPN Gateway created in this tutorial for VPC1 is vpn-xxxxxqwj.|
    |VPC2|172.25.0.0/12|VPN Gateway|The VPN Gateway created in this tutorial for VPC2 is vpn-xxxxxl5z.|


## Step 5: Verify the connection {#section_ojw_ylz_wdb .section}

Log on to the ECS1, and then ping the private IP address of the ECS2 to check whether the connection is established.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13352/15434965223323_en-US.png)

