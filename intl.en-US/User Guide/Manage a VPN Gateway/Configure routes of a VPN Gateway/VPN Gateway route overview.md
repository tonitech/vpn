# VPN Gateway route overview {#concept_zlb_mvx_bhb .concept}

After you create an IPsec-VPN connection, you must manually add a VPN Gateway route.

The route-based IPsec-VPN enables you to easily configure and maintain VPN policies, and provides flexible ways for routing traffic.

You can add the following two types of routes for a VPN Gateway:

-   Policy-based routes.
-   Destination-based routes.

## Policy-based route {#section_rwn_rpj_fhb .section}

If a policy-based route is used, traffic is forwarded based on both the source IP address and the destination IP address.

For more information, see [Add policy-based routes](reseller.en-US/User Guide/Manage a VPN Gateway/Configure routes of a VPN Gateway/Add a policy-based route.md#).

**Note:** Policy-based routes take precedence over destination-based routes.

## Destination-based route {#section_khb_z14_fhb .section}

If a destination-based route is used, traffic is forwarded based only on the destination IP address.

For more information, see [Add Destination-based routes](reseller.en-US/User Guide/Manage a VPN Gateway/Configure routes of a VPN Gateway/Add a destination-based route.md#).

