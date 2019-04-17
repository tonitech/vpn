# VPN Gateway route overview {#concept_zlb_mvx_bhb .concept}

This topic describes policy-based routes and destination-based routes. If you do not synchronize IPsec connection routes to the route table of a VPN Gateway while creating an IPsec connection, you can manually add policy-based routes or destination-based routes to the VPN Gateway.

The route-based IPsec-VPN enables you to easily configure and maintain VPN policies and provides flexible routing methods for directing traffic. You must synchronize IPsec-VPN connection routes to the VPN route table while creating an IPsec connection.

If you do not synchronize IPsec-VPN connection routes, you can add the following types of routes to a VPN Gateway:

-   Policy-based routes
-   Destination-based routes

## Policy-based routes {#section_rwn_rpj_fhb .section}

If you enable policy-based routes, traffic is directed based on the specified source IP address and destination IP address.

For more information, see [Add policy-based routes](reseller.en-US/User Guide/Manage a VPN Gateway/Configure routes of a VPN Gateway/Add policy-based routes.md#).

**Note:** Policy-based routes take priority over destination-based routes.

## Destination-based routes {#section_khb_z14_fhb .section}

If you enable destination-based routes, traffic is directed based on the destination IP address only.

For more information, see [Add destination-based routes](reseller.en-US/User Guide/Manage a VPN Gateway/Configure routes of a VPN Gateway/Add destination-based routes.md#).

