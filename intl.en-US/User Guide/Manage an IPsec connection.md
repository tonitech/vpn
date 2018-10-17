# Manage an IPsec connection {#concept_hpr_byc_xdb .concept}

After creating a VPN Gateway and a customer gateway, you can create an IPsec connection. The IPsec connection allows you to connect the VPN Gateway and the customer gateway, thus establishing a VPN tunnel.

## Create an IPsec connection {#section_mxd_fyc_xdb .section}

Follow these steps to create an IPsec connection:

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **IPsec Connections**.
3.  On the IPsec Connections page, select the region of the IPsec connection.
4.  Click **Create IPsec connection**.
5.  Configure the IPsec connection according to the following information and click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**Name**| Enter the name of the IPsec connection.

 The name can contain 2-128 English letters, numbers, hyphens, or underlines, and must start with English letters.

 |
    |**VPN Gateway**|Select the VPN Gateway to connect.|
    |**Customer Gateway**|Select the customer gateway to connect.|
    |**Local Network**|Enter the IP address range of the VPC to be connected with the local data center, which is used for second-stage negotiation. You can enter multiple IP address ranges and separate them by commas. For example, 192.168.1.0/24, 192.168.2.0/24.**Note:** If multiple IP address ranges are entered, the IKEv2 must be selected.

|
    |**Remote Network**|Enter the IP address range of the local data center to be connected with the VPC. This is used for second-stage negotiation. You can enter multiple IP address ranges and separate them by commas. For example, 172.10.1.0/24,172.10.2.0/24.**Note:** If multiple IP address ranges are entered, the IKEv2 must be selected.

|
    |**Effective Immediately**|Choose whether to delete the established IPsec tunnel and restart the negotiation.    -   Yes: Start the negotiation immediately once the configuration is complete.
    -   No: Start the negotiation only when there is incoming traffic.
|
    |**Advanced Configuration: IKE Configurations**|
    |**Pre-Shared Key**|Enter the pre-shared key used for the authentication between the VPN Gateway and the customer gateway. By default, it is an automatically generated value. But you can enter a specific pre-shared key.|
    |**Version**|Select the IKE version to use. Compared with IKEv1, IKEv2 simplifies the SA negotiation process and provides better support for multiple-CIDR-block scenarios. We recommend that you select the IKE V2 protocol.|
    |**Negotiation Mode**|Select the negotiation mode of the IKEv1.    -   Main mode: The negotiation process features high security.
    -   Aggressive mode: The negotiation is fast and the success rate of negotiation is high.
After the negotiation succeeds, the information transmission security is the same for the two modes.|
    |**Encryption Algorithm**|Select an encryption algorithm used by first-stage negotiation from the following options: aes, aes192, aes196, des, and 3des|
    |**Authentication Algorithm**|Select an authentication algorithm used by first-stage negotiation from the following options: sha1 or md5|
    |**DH Group**|Select a Diffie-Hellman key exchange algorithm used by first-stage negotiation.|
    |**SA Life Cycle \(seconds\)**|Set the SA lifecycle for the first-stage negotiation. The default value is 86,400 seconds.|
    |**LocalId**|It is the identification of the VPN Gateway used for the first-stage negotiation. The default value is the public IP address of the VPN Gateway. If you set the LocalId in the FQDN format, we recommend that you change the negotiation mode to the aggressive mode.|
    |**RemoteId**|It is the identification of the customer gateway used for the first-stage negotiation. The default value is the public IP address of the customer gateway. If you set the RemoteId in the FQDN format, we recommend that you change the negotiation mode to the aggressive mode.|
    |**Advanced Configuration: IPSec Configuration**|
    |**Encryption Algorithm**|Select the encryption algorithm of second-stage negotiation from the following options: aes, aes192, aes196, des, or 3des.|
    |**Authentication Algorithm**|Select an authentication algorithm used by second-stage negotiation from the following options: sha1 or md5|
    |**DH Group**|Select a Diffie-Hellman key exchange algorithm used by second-stage negotiation.    -   If you select any group that are not disabled, the PFS feature is enabled by default \(perfect forward secrecy\), so the key must be updated for each renegotiation and PFS must be enabled on the client.
    -   For clients that do not support PFS, select Disabled.
|
    |**SA Life Cycle \(seconds\)**|Set the SA lifecycle for the second-stage negotiation. The default value is 86,400 seconds.|


## Download the configuration {#section_ayd_fyc_xdb .section}

After the IPsec connection is configured and the negotiation succeeds, you can download the IPsec connection configuration and configure the local gateway. For more information, see [Local gateway configurations](https://help.aliyun.com/document_detail/60045.html).

Follow these steps to download the IPsec connection configuration:

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **IPsec Connections**.
3.  On the IPsec Connections page, select the region of the target IPsec connection.
4.  Click **Download Config** in the **Actions** column of the target IPsec connection.

    The RemoteSubnet and LocalSubnet in the download configuration are opposite to the local network and the remote network when creating an IPsec connection. From the perspective of VPN Gateway, the remote network is the local IDC and the local network is the VPC; while from the perspective of local IDC, the remote network is the VPC and the local network is the local IDC.

    For example, if you set the local network to 192.168.0.0/16 and the remote network to 10.0.0.0/8 in an IPsec connection, the downloaded IPsec connection configuration is as follows:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13351/15397759313317_en-US.png)


## Edit an IPsec connection {#section_eyd_fyc_xdb .section}

Follow these steps to edit an IPsec connection:

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **IPsec Connections**.
3.  On the IPsec Connections page, select the region of the target IPsec connection.
4.  Click **Edit** in the **Actions** column of the target IPsec connection.

## Delete an IPsec connection {#section_gyd_fyc_xdb .section}

Follow these steps to delete an IPsec connection:

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **IPsec Connections**.
3.  On the IPsec Connections page, select the region of the target IPsec connection.
4.  Click **Delete** in the **Actions** column of the target IPsec connection.
5.  In the displayed dialog box, click **OK**.

## View IPsec connection logs {#section_jyd_fyc_xdb .section}

You can view the IPsec connection logs for the previous month. You can troubleshoot IPsec connection errors by analyzing the connection logs. The maximum time range is 10 minutes.

Follow these steps to view IPsec connection logs:

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **IPsec Connections**.
3.  On the IPsec Connections page, select the region of the target IPsec connection.
4.  Click **View Logs** in the **Actions** column of the target IPsec connection.
5.  On the displayed page, configure the time range of the logs to view.

