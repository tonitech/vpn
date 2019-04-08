# Create an SSL server {#task_llj_prx_bhb .task}

This topic describes how to create an SSL server. To use the SSL-VPN function to establish a point-to-site connection, you must first create an SSL server.

A VPN Gateway is created and the SSL-VPN function is enabled on it. For more information, see [Create a VPN Gateway](reseller.en-US/User Guide/Manage a VPN Gateway/Create a VPN Gateway.md#).

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.  In the left-side navigation pane, choose **VPN** \> **SSL Servers**. 
3.  On the SSL Servers page, select the target region. 
4.  Click Create SSL Server. 
5.  Configure the SSL server and click **OK**. The following table describes the parameter settings. 

    |Configuration|Description|
    |:------------|:----------|
    |**Name**| The name of the SSL server.

 The name must be 2 to 128 characters in length and can contain letters, numbers, hyphens \(-\), and underscores \(\_\). The name must start with a letter.

 |
    |**VPN Gateway**| The associated VPN Gateway.

 Make sure that you have enabled the SSL-VPN function.

 |
    |**Local Network**| The IP address range to be accessed by the client through SSL-VPN. It can be the IP address range of a VPC, a VSwitch, an on-premises data center connected to a VPC through a leased line, or a cloud service such as RDS or OSS.

 Click **Add Local Network** to add more local networks.

 **Note:** The subnet mask of the local network must be in the range of /16 to /29.

 |
    |**Client Subnet**| The IP address range from which an IP address will be allocated to the virtual network card of the client. It is not the existing intranet IP address range of the client. When the client accesses the local end, the client uses the IP address allocated from the client subnet by the VPN Gateway to access the local network.

 **Note:** The client subnet and the local network cannot conflict with each other.

 |
    |**Advanced Configuration**|
    |**Protocol**|The protocol used by the SSL connection. Valid values: UDP | TCP. We recommend that you use the UDP protocol.|
    |**Port**|The port used by the SSL connection. Default value: 1194.|
    |**Encryption Algorithm**|The encryption algorithm used by the SSL connection. Valid values: AES-128-CBC | AES-192-CBC | AES-256-CB|
    |**Enable Compression**|Specifies whether to enable compression.|


