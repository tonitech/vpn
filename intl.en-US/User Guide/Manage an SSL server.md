# Manage an SSL server {#concept_iqb_f1d_xdb .concept}

To create a point-to-site connection, you must create an SSL server to specify the network that you want to connect.

## Create an SSL server {#section_gcz_31d_xdb .section}

Follow these steps to create an SSL server:

1.  In the left-side navigation pane, click **VPN** \> **SSL Servers**.
2.  On the SSL Servers page, select a region.
3.  Click Create SSL Server.
4.  Configure the SSL server according to the following information, and click **OK**.

    |Configuration|Description|
    |:------------|:----------|
    |**Name**| The name of the SSL server.

 The name can contain 2-128 English letters, numbers, hyphens, or underlines, and must start with English letters.

 |
    |**VPN Gateway**| The associated VPN gateway.

 Make sure that you have enabled the SSL-VPN function.

 |
    |**Local Network**| The local network is the IP address range to be accessed by the client through SSL-VPN. It can be the IP address range of a VPC, a VSwitch, a local data center connected to a VPC through a leased line, or a cloud service such as RDS or OSS.

 Click **Add Local Network** to add more local networks.

 **Note:** The subnet mask of the local network must be /16 to /29.

 |
    |**Client Subnet**| The client subnet is the IP address range of which an IP address will be allocated to the virtual network card of the client. The client uses the allocated IP address to access the local network. It is not the existing intranet IP address range of the client.

 **Note:** Make sure that the client subnet and the local network do not conflict with each other.

 |
    |**Advanced Configuration**|
    |**Protocol**|The protocol used by the SSL connection: UDP or TCP. We recommend that you use the UDP protocol.|
    |**Port**|The port used by the SSL connection. The default value is 1194.|
    |**Encryption Algorithm**|The encryption algorithm used by the SSL connection: AES-128-CBC, AES-192-CBC, or AES-256-CBC|
    |**Enable Compression**|Whether to enable compression.|


## Edit an SSL server {#section_pcz_31d_xdb .section}

Follow these steps to edit an SSL server:

1.  In the left-side navigation pane, click **VPN** \> **SSL Servers**.
2.  On the SSL Servers page, select the region of the target SSL server.
3.  Click **Edit** in the **Actions** column of the target SSL server.

## Delete an SSL server {#section_rcz_31d_xdb .section}

Follow these steps to delete an SSL server:

1.  In the left-side navigation pane, click **VPN** \> **SSL Servers**.
2.  On the SSL Servers page, select the region of the target SSL server.
3.  Click **Delete** in the **Actions** column of the target SSL server.
4.  In the displayed dialog box, click **OK**.

