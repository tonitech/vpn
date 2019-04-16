# Download the configuration of an IPsec-VPN connection {#task_czy_ttz_bhb .task}

This topic describes how to download the configuration of an IPsec-VPN connection. After creating an IPsec-VPN connection, you can download the configuration of the connection and load the configuration to local gateway devices.

At least one IPsec-VPN connection is created. For more information, see [Create an IPsec-VPN connection](reseller.en-US/User Guide/Configure IPsec-VPN connections/Manage an IPsec-VPN connection/Create an IPsec-VPN connection.md#).

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, choose **VPN** \> **IPsec Connections**.
3.  On the IPsec Connections page, select the region of the target IPsec-VPN connection.
4.  Find the target connection, and click **Download Configuration** in the **Actions** column. 

    **Note:** The RemoteSubnet and LocalSubnet in the downloaded configuration are opposite to the local network and the remote network when creating an IPsec-VPN connection. From the perspective of VPN Gateway, the remote network is the on-premises data center and the local network is the VPC whereas from the perspective of the on-premises data center, the remote network is the VPC and the local network is the on-premises data center.


