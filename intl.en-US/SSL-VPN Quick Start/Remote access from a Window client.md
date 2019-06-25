# Remote access from a Window client {#concept_a1t_jvz_wdb .concept}

This topic describes how to use SSL-VPN to access a VPC from a remote computer of the Windows operating system.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13355/15614257513330_en-US.png)

## Prerequisites {#section_u0m_4z7_796 .section}

Before deploying the VPN Gateway, make sure that the following conditions are met:

-   The IP address ranges of the VPC and the remote computer are not in conflict.
-   The client can access the Internet.

## Step 1: Create a VPN Gateway {#section_jpu_p26_m1h .section}

To create a customer gateway, follow these steps:

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**.
3.  On the VPN Gateways page, click **Create VPN Gateway**.
4.  On the purchase page, configure the VPN Gateway according to the following information and click **Buy Now**.
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
5.  Go back to the VPN Gateways page, select China \(Hangzhou\) region to view the created VPN Gateway.

    The initial status of a VPN Gateway is Preparing. It changes to Normal in about 2 minutes. When it changes to Normal, it indicates that the VPN Gateway is ready to use.

    **Note:** It usually takes 1-5 minutes to create a VPN Gateway.


## Step 2: Create an SSL server {#section_djh_986_lm0 .section}

Follow these steps to create an SSL server:

1.  In the left-side navigation pane, click **VPN** \> **SSL Servers**.
2.  Select the target region.
3.  On the SSL Servers page, click **Create SSL Server**.
4.  On the Create SSL Server page, configure the SSL server according to the following information and click **OK**.
    -   **Name**: Enter a name for the SSL server.
    -   **VPN Gateway**: Select the created VPN Gateway.
    -   **Local Network**: Enter the CIDR block of the network to be connected. Click **Add Local Network** to add multiple local networks. The local network can be the CIDR block of any VPC or VSwitch, or the CIDR block of the local network.
    -   **Client Subnet**: Enter the IP addresses used by the client to connect the server in the form of CIDR block.
    -   **Advanced Configuration**: Use the default advanced configuration.

## Step 3: Create and download an SSL client certificate {#section_g6t_zpt_h4f .section}

1.  In the left-side navigation pane, click **VPN** \> **SSL Clients**.
2.  Select the target region.
3.  On the SSL Clients page, click **Create Client Certificate**.
4.  On the Create Client Certificate page, enter a name, and then select the corresponding SSL server. Click **OK**.
5.  On the SSL Clients page, find the created SSL client certificate, and then click **Download** in the **Actions** column.

## Step 4: Configure the Windows client {#section_azr_zfq_g2b .section}

To configure a Linux client, follow these steps:

**Note:** You need to run the client as an administrator.

1.  Download and install the OpenVPN client.
2.  Extract the client certificate downloaded in step 3 and copy the extracted certificate to the /etc/openvpn/conf/ directory.
3.  Click **Connect** to initiate the connection.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13355/15614257513331_en-US.png)


## Step 5: Verify the connection {#section_3vm_nbi_aye .section}

On the client, ping the private IP address of an ECS instance in the connected VPC network to verify the connection.

**Note:** Make sure that the security group rules of the ECS instance allow remote access. For more information, see [Scenarios](../../../../reseller.en-US/Security/Security groups/Scenarios.md#).

