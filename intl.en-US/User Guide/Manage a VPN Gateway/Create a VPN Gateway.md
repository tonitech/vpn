# Create a VPN Gateway {#task_llj_prx_bhb .task}

To enable the IPsec-VPN or SSL-VPN function, you must create a VPN Gateway. After a VPN Gateway is created, a public IP address is allocated to it.

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc).
2.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**.
3.   On the VPN Gateways page, click Create VPN Gateway. 
4.   On the purchase page, configure the VPN Gateway according to the following information, and then click **Buy Now**. 

    |Configuration|Description|
    |:------------|:----------|
    | **Name** |Optional. The name of the VPN Gateway. The name must be 2 to 128 characters in length and can contain letters, numbers, periods \(.\), underscores \(\_\) and hyphens \(-\). The name must start with a letter.

 |
    | **Region** | Select the region of the VPN Gateway.

 If you want to use IPsec-VPN to connect a VPC to an on-premises data center or other VPCs, make sure that the VPN Gateway and the VPC are in the same region.

 |
    | **VPC** |Select the VPC associated with the VPN Gateway.|
    | **Bandwidth** |Select the bandwidth of the VPN Gateway. The bandwidth is the Internet bandwidth of the VPN Gateway.|
    | **IPsec-VPN** |Select whether to enable the IPsec-VPN function. With IPsec-VPN enabled, you can establish a secure connection between an on-premises data center and a VPC or between two VPCs.

 |
    | **SSL-VPN** | Select whether to enable the SSL-VPN function.

 With SSL-VPN enabled, you can create a point-to-site connection. After the connection is created, the client can directly access the VPC from a remote location without the need to configure a client gateway.

 |
    | **SSL connections** |Select the maximum number of clients you want to connect to simultaneously. **Note:** You can only configure this option after you enable the SSL-VPN feature.

 |
    | **Billing Cycle** |Select the validity period of purchase.|
    | **Auto Renew** |Select whether to enable auto renewal:     -   If VPN Gateway is billed monthly, the auto renewal cycle is one month.
    -   If VPN Gateway is billed yearly, the auto renewal cycle is one year.
 |


