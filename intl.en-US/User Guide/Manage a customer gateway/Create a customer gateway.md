# Create a customer gateway {#task_llj_prx_bhb .task}

When you use an IPsec-VPN connection to connect a VPC to an on-premises data center or connect two VPCs, you must create a customer gateway. By creating a customer gateway, you can register the local gateway to Alibaba Cloud and connect the customer gateway to the VPN Gateway. A customer gateway can be connected to multiple VPN Gateways.

1.   Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.   In the left-side navigation pane, click **VPN** \> **Customer Gateways**. 
3.   Select the region to which the target customer gateway belongs. 

    **Note:** The customer gateway and the VPN Gateway you are connecting must be in the same region.

4.   On the Customer Gateways page, click Create Customer Gateway. 
5.   On the Create Customer Gateway page, configure the customer gateway according to the following information. 

    |Configuration|Description|
    |:------------|:----------|
    | **Name** | The name of the customer gateway.

 The name must be 2 to 128 letters in length and can contain numbers, hyphens, or underscores. It must start with a letter.

 |
    | **IP Address** |The static public IP address configured for the gateway device of the on-premises data center.|
    | **Description** | The description of the customer gateway.

 The description must be 2 to 256 characters in length. It cannot begin with http:// or https://.

 |

6.   Optional. Click **+Add** to add another customer gateway. 
7.   Click **OK**. 

