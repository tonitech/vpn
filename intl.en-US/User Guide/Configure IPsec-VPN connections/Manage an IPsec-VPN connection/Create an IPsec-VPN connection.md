# Create an IPsec-VPN connection {#task_llj_prx_bhb .task}

This topic describes how to create an IPsec-VPN connection. After creating a VPN Gateway and a customer gateway, you can create an IPsec-VPN connection to establish an encrypted tunnel for communication.

1.   Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.   In the left-side navigation pane, choose **VPN** \> **IPsec Connections**. 
3.   Select a region. 
4.   On the IPsec Connections page, click **Create IPsec Connection**. 
5.   On the Create IPsec Connection page, configure the IPsec-VPN connection according to the following information and click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    | **Name** | Enter the name of the IPsec-VPN connection.

 The name must be 2 to 128 characters in length and can contain letters, numbers, hyphens, or underscores. It must start with a letter.

 |
    | **VPN Gateway** |Select the VPN Gateway to connect.|
    | **Customer Gateway** |Select the customer gateway to connect.|
    | **Advanced Configuration: IKE Configurations** |
    | **Pre-Shared Key** |Enter the pre-shared key used for the authentication between the VPN Gateway and the customer gateway. By default, it is an automatically generated value. But you can also specify a pre-shared key.|
    | **Version** |Select the IKE version to use. Compared with IKEv1, IKEv2 simplifies the SA negotiation process and provides better support for multiple-CIDR-block scenarios. We recommend that you select the IKE V2 protocol.|
    | **Negotiation Mode** |Select the negotiation mode of the IKEv1.     -   Main mode: The negotiation process features high security.
    -   Aggressive mode: The negotiation is fast and the success rate of negotiation is high.
 After the negotiation succeeds, the information transmission security is the same for the two modes.|
    | **Encryption Algorithm** |Select an encryption algorithm used by phase one negotiation from the following options: aes, aes192, aes256, des, and 3des.|
    | **Authentication Algorithm** |Select an authentication algorithm used by phase one negotiation from the following options: sha1, md5, sha256, sha384, and sha512.|
    | **DH Group** |Select a Diffie-Hellman key exchange algorithm used by phase one negotiation.|
    | **SA Life Cycle \(seconds\)** |Set the SA lifecycle for phase one negotiation. The default value is 86,400 seconds.|
    | **LocalId** |It is the identification of the VPN Gateway used for phase one negotiation. The default value is the public IP address of the VPN Gateway. If you set the LocalId in the FQDN format, we recommend that you change the negotiation mode to the aggressive mode.|
    | **RemoteId** |It is the identification of the customer gateway used for the first-stage negotiation. The default value is the public IP address of the customer gateway. If you set the RemoteId in the FQDN format, we recommend that you change the negotiation mode to the aggressive mode.|
    | **Advanced Configuration: IPSec Configurations** |
    | **Encryption Algorithm** |Select the encryption algorithm of phase two negotiation. Valid values: aes, aes192, aes256, des, or 3des.|
    | **Authentication Algorithm** |Select an authentication algorithm used by phase two negotiation. Valid values: sha1, md5, sha256, sha384, and sha512.|
    | **DH Group** |Select a Diffie-Hellman key exchange algorithm used by phase two negotiation.     -   If you select any group that are not disabled, the PFS feature is enabled by default \(perfect forward secrecy\), so the key must be updated for each renegotiation and PFS must be enabled on the client.
    -   For clients that do not support PFS, select Disabled.
 |
    | **SA Life Cycle \(seconds\)** |Set the SA lifecycle for phase two negotiation. Default value: 86,400s.|
    | **Health Check** |
    | **Destination IP** |The IP address of the on-premises data center that the VPC can communicate with through the IPsec-VPN connection.|
    | **Source IP** |The IP address of the VPC that the on-premises data center can communicate with through the IPsec-VPN connection.|
    | **Retry Interval** |The length of time before a health check is retried. Unit: second.|
    | **Retry Times** |The number of times to attempt sending health check packets.|


