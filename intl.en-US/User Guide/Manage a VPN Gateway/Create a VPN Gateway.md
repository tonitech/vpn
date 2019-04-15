# Create a VPN Gateway {#task_llj_prx_bhb .task}

To enable the SSL-VPN or IPsec-VPN function, you must create a VPN Gateway. After a VPN Gateway is created, a public IP address is allocated to it.

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**. 
3.  Click Create VPN Gateway. 
4.  Configure the VPN Gateway according to the following information and then click **Buy Now**. 

    |Configuration|Description|
    |:------------|:----------|
    |Region| Select a region.

 If you want to use the IPsec-VPN function to connect a VPC to a local data center or to another VPC, make sure that the VPN Gateway and the VPCs are in the same region.

 |
    |Name|Optional. The name of the VPN Gateway.The name must be 2 to 128 characters in length and can contain letters, numbers, periods \(.\), underscores \(\_\) and hyphens \(-\). The name must start with a letter.

|
    |VPC|Select the VPC associated with the VPN Gateway.|
    |Peak Bandwidth|Select the Internet bandwidth of the VPN Gateway.|
    |IPsec-VPN| Select whether to enable the IPsec-VPN function.

 With IPsec-VPN enabled, you can create a site-to-site connection over the IPsec tunnel to connect an on-premises data center to a VPC, or interconnect two VPCs.

 |
    |SSL-VPN| Select whether to enable the SSL-VPN function.

 With SSL-VPN enabled, you can create a point-to-site connection. After the connection is created, the client can directly access the VPC from a remote location without the need to configure a client gateway.

 |
    |Billing Cycle|Select the validity period of the subscription.|
    |Auto Renew|Select whether to automatically renew the service:    -   Purchase on a monthly basis: The auto renewal cycle is one month.
    -   Purchase on a yearly basis: The auto renewal cycle is one year.
|


