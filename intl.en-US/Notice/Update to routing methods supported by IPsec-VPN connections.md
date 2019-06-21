# Update to routing methods supported by IPsec-VPN connections {#concept_w3s_24z_ghb .concept}

VPN Gateway now supports route-based IPsec-VPN connections in addition to policy-based IPsec-VPN connections. The updates do not apply to SSL-VPN connections.

## Change details {#section_wvs_g4z_ghb .section}

You can find the following changes in the console:

Two routing methods are available in the details page of a VPN Gateway.

-   Policy-based Routing: Traffic is forwarded based on both the source IP address and destination IP address.
-   Destination-based Routing: Traffic is forwarded only based on the destination IP address.

**Note:** Currently, only policy-based routing and destination-based routing are supported in the console. Support for dynamic routing is in development.

## Enable route-based IPsec-VPN on an existing VPN Gateway {#section_nts_34z_ghb .section}

Existing VPN Gateways do not support the route-based IPsec-VPN function and route tables are unavailable in the console. If you need this function, open a ticket.

Newly created VPN Gateways support the route-based IPsec-VPN function by default. You can view the route table in the details page of a VPN Gateway.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/150978/156108592342114_en-US.png)

