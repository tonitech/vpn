# Add a destination-based route {#task_ekx_wcj_fhb .task}

After creating an IPsec-VPN connection, you can manually add a destination-based route. In this way, traffic is forwarded according to the specified destination IP address.

1.   Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.   In the left-side navigation pane, choose **VPN** \> **VPN Gateways**. 
3.   Select the region of the target VPN Gateway. 
4.   On the VPN Gateways page, find the target VPN Gateway and click the instance ID in the Instance ID/Name column. 
5.   On the Destination-based Routing page, click **Add Route Entry**. 
6.   On the Add Route Entry page, configure a destination-based route according to the following information, and click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    | **Destination CIDR Block** |Enter the private CIDR block of the on-premises data center.|
    | **Next Hop Type** |Select IPsec connection.|
    | **Next Hop** |Select the target IPsec-VPN connection instance.|
    | **Publish to VPC** |Select whether to publish the new route entry to the VPC route table.     -   \(Recommended\) Yes: Publish the new route entry to the VPC route table.
    -   No: Do not publish the new route entry to the VPC route table.
 **Note:** If you select No, after you add the destination-based route, you must also publish the route entry in the destination-based route table.

 |
    | **Weight** |Select a weight. Valid values:     -   100
    -   0
 The larger the weight, the higher the routing priority.

 |


