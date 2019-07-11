# Add a destination-based route {#task_ekx_wcj_fhb .task}

This topic describes how to add a destination-based route. After you add a destination-based route, you can forward traffic by using the specified destination IP address.

1.   Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.   In the left-side navigation pane, choose **VPN** \> **VPN Gateways**. 
3.   Select the region of the target VPN Gateway. 
4.   On the VPN Gateways page, find the target VPN Gateway and click the instance ID in the Instance ID/Name column. 
5.  On the Destination-based Routing tab, click **Add Route Entry**.
6.  On the Add Route Entry page, configure a destination-based route, and then click **OK**. The following table describes the parameters. 

    |Configuration|Description|
    |:------------|:----------|
    |**Destination CIDR Block**|Enter the private CIDR block to be accessed.|
    |**Next Hop Type**|Select IPsec Connection.|
    |**Next Hop**|Select the target IPsec-VPN connection instance.|
    |**Publish to VPC**|Select whether to publish the new route entry to the VPC route table.     -   Yes \(Recommended\): Publish the new route entry to the VPC route table.
    -   No: Do not publish the new route entry to the VPC route table.
 **Note:** If you select No, you must also publish the route entry in the destination-based route table after you add the destination-based route.

 |
    |**Weight**|Select a weight. Valid values:     -   100: high priority
    -   0: low priority
 **Note:** Destination-based routes with the same destination CIDR block cannot be configured with a weight of 100 at the same time.

 |


