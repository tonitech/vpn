# Add policy-based routes {#task_cvt_j5x_bhb .task}

This topic describes how to add policy-based routes. If you do not synchronize IPsec connection routes to the VPN route table while creating an IPsec connection, you can manually add policy-based routes to the VPN Gateway.

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**. 
3.  Select the region of the target VPN Gateway. 
4.  Find the target VPN Gateway and click the instance ID in the Instance ID/Name column. 
5.  On the Policy-Based Route Table tab page, click **Add Route Entry**. 
6.  Configure a policy-based route, and then click **OK**. The following table describes the parameter settings. 

    |Configuration|Description|
    |:------------|:----------|
    |Destination CIDR Block|Enter the private CIDR block of the on-premises data center.|
    |Source CIDR Block|Enter the private CIDR block of the VPC.|
    |Next Hop|Select the target IPsec connection.|
    |Advertise to VPC|Select whether to advertise the route to the route table of the VPC.    -   \(Recommended\) Yes: Advertise the route to the route table of the VPC.
    -   No: Do not advertise the route to the route table of the VPC.
**Note:** If you select do not advertise the route to the VPC, you need to advertise the route in the policy-based route table after adding the route.

|
    |**Weight**|Select a weight: Valid values:    -   100
    -   0
The larger the weight, the higher the priority.

|


