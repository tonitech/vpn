# Manage a VPN Gateway {#concept_ipr_lvc_xdb .concept}

Create a VPN Gateway to enable SSL-VPN and IPsec-VPN connectivity. After a VPN Gateway is created, a public IP is allocated to it.

## Create a VPN gateway {#section_zv3_nyf_xdb .section}

Follow these steps to create a VPN gateway:

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **VPN Gateways**.
3.  On the VPN Gateways page, click Create VPN Gateway.
4.  Configure the VPN gateway according to the following information, and click **Buy Now**.

    |Configuration|Description|
    |:------------|:----------|
    |Region| Select the region of the VPN Gateway.

 If you want to use IPsec-VPN to connect a VPC to a local data center or other VPCs, make sure that the VPN Gateway and the VPC are in the same region.

 |
    |VPC|Select the VPC associated with the VPN Gateway.|
    |Bandwidth|Select the Internet bandwidth of the VPN Gateway. The bandwidth specification is the Internet bandwidth of the VPN gateway.|
    |IPsec-VPN| Enable IPsec-VPN.

 With IPsec-VPN enabled, you can create a site-to-site connection over the IPsec tunnel to connect a local data center to a VPC, or connect two VPCs.

 |
    |SSL-VPN| Enable SSL-VPN.

 With SSL-VPN enabled, you can create a point-to-site connection. The client can directly access the VPC from a remote location without configuring a client gateway.

 |
    |Purchase Duration|Select the purchase duration.|
    |Auto renew|Select whether to enable auto renew:    -   If VPN Gateway is billed monthly, renewal cycle is month.
    -   If VPN Gateway is billed yearly, the auto renewal cycle is year.
|


## Edit a VPN gateway {#section_hgl_kwc_xdb .section}

Follow these steps to edit the name and description of a VPN gateway:

1.  Log on to the VPC console.
2.  In the left-side navigation pane, click **VPN** \> **VPN Gateways**.
3.  On the VPN Gateways page, select the region of the VPN Gateway.
4.  Click **Edit** in the **Actions** column of the target VPN Gateway.

