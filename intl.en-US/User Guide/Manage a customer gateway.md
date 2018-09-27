# Manage a customer gateway {#concept_gms_3xc_xdb .concept}

When using an IPsec-VPN connection to build a site-to-site connection, you must create a customer gateway. By creating a customer gateway, you can register the configurations of the local gateway to Alibaba Cloud. One customer gateway can be connected to multiple VPN Gateways.

## Create a customer gateway {#section_mwf_lxc_xdb .section}

Follow these steps to create a customer gateway:

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **Customer Gateways**.
3.  Select the region of the customer gateway.

    The customer gateway and the VPN Gateway you are connecting must be in the same region.

4.  On the Customer Gateways page, click Create Customer Gateway.
5.  Configure the customer gateway according to the following information.

    |Configuration|Description|
    |:------------|:----------|
    |Name| The name of the customer gateway.

 The name can contain 2-128 English letters, numbers, hyphens, or underlines, and must start with English letters.

 |
    |IP Address|The static public IP address configured for the gateway in the local data center.|
    |Description| The description of the customer gateway.

 The description can contain from 2 to 256 characters and cannot begin with http:// or https://.

 |

6.  \(Optional\) Click **+Add** to add another customer gateway.
7.  Click **OK**.

## Edit a customer gateway {#section_swf_lxc_xdb .section}

Follow these steps to edit the name and description of a customer gateway:

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **Customer Gateways**.
3.  Select the region of the target customer gateway.
4.  Click **Edit** in the **Actions** column of the target customer gateway.
5.  Modify the name and description of the customer gateway.

## Delete a user gateway {#section_vwf_lxc_xdb .section}

Follow these steps to delete a customer gateway:

**Note:** Before deleting a customer gateway, you must first delete the IPsec connection associated with the customer gateway.

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **Customer Gateways**.
3.  Select the region of the target customer gateway.
4.  Click **Delete** in the **Actions** column of the target customer gateway.
5.  In the displayed dialog box, click **OK**.

