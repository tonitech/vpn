# Window client remote access {#concept_a1t_jvz_wdb .concept}

This document illustrates how to use SSL-VPN to connect a VPC from a remote computer with the Windows operating system.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13354/15397751453324_en-US.png)

## Prerequisites {#section_kyr_zfq_g2b .section}

Before deploying the VPN gateway, make sure that the following conditions are met:

-   The IP address ranges of the VPC and the remote computer are not in conflict.

-   The client can access the Internet.


## Step 1: Create a VPN gateway {#section_myr_zfq_g2b .section}

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **VPN Gateways**.
3.  On the VPN Gateways page, click **Create VPN Gateway**.
4.  On the purchase page, configure the VPN gateway and complete the payment. In this tutorial, the VPN gateway uses the following configurations:
    -   **Region**: Select the region of the VPN gateway. In this tutorial, **China \(Hangzhou\)** is selected.

**Note:** Make sure that the VPC and the VPN gateway are in the same region.

    -   **VPC**: Select the VPC to be connected.

    -   **Bandwidth specification**: Select a bandwidth specification. The bandwidth specification is the Internet bandwidth of the VPN gateway.

    -   **IPsec-VPN**: Select whether to enable the IPsec-VPN feature. The IPSec-VPN feature applies to site-to-site connections and can be enabled according to your actual needs.

    -   **SSL-VPN**:  Select whether to enable the SSL-VPN feature. The SSL-VPN feature allows you to connect to a VPC from a single computer anywhere. In this tutorial, select **Enable**.

    -   **Concurrent SSL Connections**: Select the maximum number of clients you want to connect to simultaneously.

**Note:** You can only configure this option after you enables the SSL-VPN feature.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13354/15397751453325_en-US.png)

5.  Go back to the VPN Gateways page, select China \(Hangzhou\) region to view the created VPN Gateway.

    The initial status of a VPN Gateway is Preparing. It changes to Normal in about 2 minutes. When it changes to Normal, it indicates that the VPN Gateway is ready to use.

    **Note:** It usually takes 1-5 minutes to create a VPN Gateway.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13354/15397751453326_en-US.png)


## Step 2: Create an SSL server {#section_syr_zfq_g2b .section}

1.  In the left-hand navigation pane, click **VPN** \> **SSL Servers**.
2.  Click **Create SSL Server**. In this tutorial, the configurations of the SSL server is as follows:
    -   **Name**: Enter a name for the SSL server.

    -   **VPN Gateway**: Select the created VPN Gateway.

    -   **Local Network**: Enter the CIDR block of the network to be connected. Click **Add Local Network** to add multiple local networks. The local network can be the CIDR block of any VPC or VSwitch, or the CIDR block of the local network.

    -   Client Subnet: Enter the IP addresses used by the client to connect the server in the form of CIDR block.

    -   Advanced Configuration: Use the default advanced configuration.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13354/15397751453327_en-US.png)


## Step 3: Create a client certificate {#section_xyr_zfq_g2b .section}

1.  In the left-side navigation pane, click **VPN** \> **SSL Clients**.
2.  Click **Create Client Certificate**.
3.  On the Create Client Certificate page, enter a name, and then select the corresponding SSL server. Click **OK**.

4.  On the SSL Clients page, find the created SSL client certificate, and then click **Download**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13354/15397751453328_en-US.png)


## Step 4: Configure Mac clients {#section_azr_zfq_g2b .section}

**Note:** You need to run the client as an administrator.

1.  Download and install the OpenVPN client.
2.  Extract the client certificates downloaded in step 3 and copy the certificates to the /etc/openvpn/conf/ directory.
3.  Click **Connect** to initiate the connection.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13355/15397751453331_en-US.png)


## Step 5: Verify the connection {#section_dzr_zfq_g2b .section}

On the client, ping the private IP address of an ECS instance in the connected VPC network to verify the connection.

**Note:** Make sure that the security rule of the ECS instance allow remote access. For more information, see [Add security group rules](https://help.aliyun.com/document_detail/58746.html).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13354/15397751453329_en-US.png)

