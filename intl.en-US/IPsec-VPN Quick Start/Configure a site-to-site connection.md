# Configure a site-to-site connection {#concept_c4h_slz_wdb .concept}

This document illustrates how to create a site-to-site connection to connect a VPC with a local data center.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15434965013312_en-US.png)

## Prerequisites {#section_q3w_ylz_wdb .section}

You must meet the following requirements before creating an IPsec connection:

-   Check the gateway device in the local data center. Alibaba Cloud VPN gateways support standard IKEv1 and IKEv2 protocols. Any device that supports these two protocols can connect to Alibaba Cloud VPN Gateway. Supported devices include: Huawei, H3C, Cisco, ASN, Juniper, SonicWall, Nokia, IBM, and Ixia.

-   A static public IP address is configured for the local gateway.

-   The IP address ranges of the VPC and local data center to be connected do not conflict with each other.


## Step 1: Create a VPN Gateway {#section_vfk_2mz_wdb .section}

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **VPN Gateways**.
3.  On the VPN Gateways page, click **Create VPN Gateway**.
4.  On the purchase page, configure the VPN gateway and complete the payment. In this tutorial, the VPN gateway uses the following configurations:
    -   **Region**: Select the region of the VPN gateway. In this tutorial, **China \(Hangzhou\)** is selected.

**Note:** Make sure that the VPC and the VPN gateway are in the same region.

    -   **VPC**: Select the VPC to be connected.

    -   **Bandwidth specification**: Select a bandwidth specification. The bandwidth specification is the Internet bandwidth of the VPN gateway.

    -   **IPsec-VPN**: Select whether to enable the IPsec-VPN feature.

    -   **SSL-VPN**: Select whether to enable the SSL-VPN feature. The SSL-VPN feature allows you to connect to a VPC from a single computer anywhere.

    -   **Concurrent SSL Connections**: Select the maximum number of clients you want to connect to simultaneously.

**Note:** You can only configure this option after you enables the SSL-VPN feature.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15434965013313_en-US.png)

5.  Go back to the VPN Gateways page, select **China \(Hangzhou\)** region to view the created VPN Gateway.

    The initial status of a VPN Gateway is Preparing. It changes to Normal in about 2 minutes. When it changes to Normal, it indicates that the VPN Gateway is ready to use.

    **Note:** It usually takes 1-5 minutes to create a VPN Gateway.


## Step 2: Create a customer gateway {#section_upz_wmz_wdb .section}

1.  In the left-side navigation pane, click **VPN** \> **Customer Gateways**.
2.  Click the China \(Hangzhou\) region.
3.  On the Customer Gateways page, click **Create Customer Gateway**.
4.  Configure the customer gateway according to the following information:

    -   **Name**: Enter a customer gateway name.

    -   **IP Address**: Enter the public IP configured for the local gateway. In this tutorial, 211.167.68.68 is used.

    -   **Description**: Enter the description of the customer gateway.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15434965023314_en-US.png)

5.  On the Create Customer Gateway page, click **Add +** to add multiple customer gateways.

## Step 3: Create an IPsec connection {#section_ty2_jnz_wdb .section}

1.  In the left-side navigation pane, click **VPN** \> **IPsec Connections**.
2.  Select the China \(Hangzhou\) region.
3.  On the IPsec Connection page, click **Create IPsec Connection**.
4.  Configure the IPsec connection according to the following information:
    -   **Name**: Enter a name for the IPsec connection.

    -   **VPN Gateway**: Select the created VPN Gateway.

    -   **Customer Gateway**: Select the created customer gateway.

    -   **Local Network**: Enter the IP address range of the VPC. In this tutorial, 192.168.0.0/16 is used.

    -   **Remote Network**: Enter the CIDR block of the local data center. In this tutorial, 172.16.0.0/12 is used.

    -   **Pre-Shared Key**: Enter a pre-shared key. This value must be the same as the one configured in the local gateway.

        Use the default configuration for other options.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15434965023315_en-US.png)


## Step 4: Configure the local gateway {#section_ptn_44z_wdb .section}

1.  In the left-side navigation pane, click **VPN** \> **IPsec Connections**.
2.  Select the China \(Hangzhou\) region.
3.  Find the target IPsec connection and click **Download Config**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15434965023316_en-US.png)

4.  Configure the local gateway accordingly. For more information, see [Configure H3C firewall](../../../../reseller.en-US/Best Practices/Local gateway configurations/Configure H3C firewall.md#) and [Configure strongSwan](../../../../reseller.en-US/Best Practices/Local gateway configurations/Configure strongSwan.md#).

    The RemoteSubnet and LocalSubnet in the download configuration are the opposite of the local network and the remote network when creating an IPsec connection. From the perspective of VPN Gateway, the remote network is the local IDC and the local network is the VPC.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15434965023317_en-US.png)


## Step 5: Configure the route {#section_k1m_cpz_wdb .section}

1.  In the left-side navigation pane, click **Route Tables**.
2.  Select the region to which the connected VPC belongs. In this tutorial, the China \(Hangzhou\) region is selected.
3.  Find the target VPC and click **Manage**.
4.  On the Route Tables page, click **Add route entry**.
5.  Configure the route entry according to the following information, and then click **OK**.
    -   **Destination CIDR Block**: Enter the IP address range of the local IDC. In this tutorial, 172.16.0.0/12 is used.

    -   **Next Hop Type**: Select VPN Gateway.

    -   **VPN Gateway**: Select the created VPN gateway.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15434965023318_en-US.png)


## Step 6: Verify the connection {#section_ojw_ylz_wdb .section}

Log on to an ECS instance \(without a public IP\) in the connected VPC network. Ping the private IP address of a server in the local data center to check whether the connection is established.

