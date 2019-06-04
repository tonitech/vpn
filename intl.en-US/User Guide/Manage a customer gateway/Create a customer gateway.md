# Create a customer gateway {#task_llj_prx_bhb .task}

When using an IPsec-VPN connection to build a site-to-site connection, you must create a customer gateway. By creating a customer gateway, you can register the configurations of the local gateway to Alibaba Cloud. One customer gateway can be connected to multiple VPN Gateways.

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.  In the left-side navigation pane, choose **VPN** \> **Customer Gateways**. 
3.  Select the region of the target customer gateway. 

    **Note:** The customer gateway and the VPN Gateway you are connecting must be in the same region.

4.  On the Customer Gateways page, click Create Customer Gateway. 
5.  Configure the customer gateway according to the following information. 

    |Configuration|Description|
    |:------------|:----------|
    |Name| The name of the customer gateway.

 The name can contain 2-128 letters, numbers, hyphens, or underlines, and must start with English letters.

 |
    |IP Address|The static public IP address configured for the gateway in the local data center.|
    |Description| The description of the customer gateway.

 The description can contain from 2 to 256 characters and cannot begin with http:// or https://.

 |

6.  Optional. Click **+Add** to add another customer gateway. 
7.  Click **OK**. 

