# Add a policy-based route {#task_cvt_j5x_bhb .task}

After creating an IPsec connection, you can manually add a policy-based route. In this way, traffic is forwarded based on both the source IP address and the destination IP address.

1.   Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.   In the left-side navigation pane, choose **VPN** \> **VPN Gateways**. 
3.   Select the region of the target VPN Gateway. 
4.   On the VPN Gateways page, find the target VPN Gateway and click the instance ID in the Instance ID/Name column. 
5.   On the Policy-based Routing page, click **Add Route Entry**. 
6.   On the Add Route Entry page, configure a policy-based route according to the following information and click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    | **Destination CIDR Block** |Enter the private CIDR block of the on-premises data center.|
    | **Source CIDR Block** |The private CIDR block of the VPC.|
    | **Next Hop Type** |Select IPsec-VPN connection.|
    | **Next Hop** |Select the target IPsec connection instance.|
    | **Publish to VPC** |Select whether to publish the new route entry to the VPC route table.     -   \(Recommended\) Yes: Publish the new route entry to the VPC route table.
    -   No: Do not publish the new route entry to the VPC route table.
 **Note:** If you select No, after you add a policy-based route, you also need to publish the route in the policy-based route table.

 |
    | **Weight** |Select a weight. Valid values:     -   100
    -   0
 The larger the weight, the higher the routing priority.

 |


