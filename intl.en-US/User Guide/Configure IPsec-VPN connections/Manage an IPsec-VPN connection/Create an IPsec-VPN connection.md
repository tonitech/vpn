# Create an IPsec-VPN connection {#task_llj_prx_bhb .task}

This topic describes how to create an IPsec-VPN connection. After creating a VPN Gateway and a customer gateway, you can create an IPsec-VPN connection to establish an encrypted tunnel for communication.

1.  Log on to the [VPC console](https://vpcnext.console.aliyun.com/nat/). 
2.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**. 
3.  On the IPsec Connections page, select the region of the IPsec-VPN connection. 
4.  Click **Create IPsec connection**. 
5.  Configure the IPsec-VPN connection according to the following information and click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    |**Name**| Enter the name of the IPsec-VPN connection.

 The name can contain 2 to 128 English letters, numbers, hyphens, or underscores, and must start with English letters.

 |
    |**VPN Gateway**|Select the VPN Gateway to connect.|
    |**Customer Gateway**|Select the customer gateway to connect.|
    |**Local Network**|Enter the IP address range of the VPC to be connected with the on-premises data center, which is used for second-stage negotiation. You can enter multiple IP address ranges and separate them by commas. For example, 192.168.1.0/24, 192.168.2.0/24.**Note:** If multiple IP address ranges are entered, the IKEv2 must be selected.

|
    |**Remote Network**|Enter the IP address range of the on-premises data center to be connected with the VPC. This is used for second-stage negotiation. You can enter multiple IP address ranges and separate them by commas. For example, 172.10.1.0/24,172.10.2.0/24.**Note:** If multiple IP address ranges are entered, the IKEv2 must be selected.

|
    |**Effective Immediately**|Choose whether to delete the established IPsec-VPN tunnel and restart the negotiation.    -   Yes: Start the negotiation immediately once the configuration is complete.
    -   No: Start the negotiation only when there is incoming traffic.
|
    |**Synchronize to VPN Route Table**|Choose whether to synchronize IPsec-VPN traffic routes to the VPN route table. We recommend that you select yes.    -   Yes: The IPsec-VPN traffic routes are synchronized to the VPN route table after the IPsec-VPN connection is created.
    -   No: The IPsec-VPN traffic routes are not synchronized to the VPN route table after the IPsec-VPN connection is created. You need to add gateway routes on the VPN Gateway page. For more information, see [添加网关路由](intl.en-US/User Guide/Manage a VPN Gateway/Configure routes of a VPN Gateway/Add policy-based routes.md#).
|
    |**Advanced Configuration: IKE Configurations**|
    |**Pre-Shared Key**|Enter the pre-shared key used for the authentication between the VPN Gateway and the customer gateway. By default, it is an automatically generated value. But you can enter a specific pre-shared key.|
    |**Version**|Select the IKE version to use. Compared with IKEv1, IKEv2 simplifies the SA negotiation process and provides better support for multiple-CIDR-block scenarios. We recommend that you select the IKE V2 protocol.|
    |**Negotiation Mode**|Select the negotiation mode of the IKEv1.    -   Main mode: The negotiation process features high security.
    -   Aggressive mode: The negotiation is fast and the success rate of negotiation is high.
After the negotiation succeeds, the information transmission security is the same for the two modes.|
    |**Encryption Algorithm**|Select an encryption algorithm used by first-stage negotiation from the following options: aes, aes192, aes256, des, and 3des.|
    |**Authentication Algorithm**|Select an authentication algorithm used by first-stage negotiation from the following options: sha1, md5, sha256, sha384, and sha512.|
    |**DH Group**|Select a Diffie-Hellman key exchange algorithm used by first-stage negotiation.|
    |**SA Life Cycle \(seconds\)**|Set the SA lifecycle for the first-stage negotiation. The default value is 86,400 seconds.|
    |**LocalId**|It is the identification of the VPN Gateway used for the first-stage negotiation. The default value is the public IP address of the VPN Gateway. If you set the LocalId in the FQDN format, we recommend that you change the negotiation mode to the aggressive mode.|
    |**RemoteId**|It is the identification of the customer gateway used for the first-stage negotiation. The default value is the public IP address of the customer gateway. If you set the RemoteId in the FQDN format, we recommend that you change the negotiation mode to the aggressive mode.|
    |**Advanced Configuration: IPsec Configuration**s|
    |**Encryption Algorithm**|Select the encryption algorithm of second-stage negotiation from the following options: aes, aes192, aes256, des, or 3des.|
    |**Authentication Algorithm**|Select an authentication algorithm used by second-stage negotiation from the following options: sha1, md5, sha256, sha384, and sha512.|
    |**DH Group**|Select a Diffie-Hellman key exchange algorithm used by second-stage negotiation.    -   If you select any group that are not disabled, the PFS feature is enabled by default \(perfect forward secrecy\), so the key must be updated for each renegotiation and PFS must be enabled on the client.
    -   For clients that do not support PFS, select Disabled.
|
    |**SA Life Cycle \(seconds\)**|Set the SA lifecycle for the second-stage negotiation. The default value is 86,400 seconds.|
    |**Health Check**|
    |**Destination IP**|The IP address of the on-premises data center that the VPC can communicate with through the IPsec-VPN connection.|
    |**Source IP**|The IP address of the VPC that the on-premises data center can communicate with through the IPsec-VPN connection.|
    |**Retry Interval**|The length of time before a health check is retried. Unit: second.|
    |**Retry Times**|The number of times to attempt sending health check packets.|


