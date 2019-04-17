# Update to routing methods supported by IPsec-VPN connections {#concept_w3s_24z_ghb .concept}

VPN Gateway now supports route-based IPsec-VPN connections in addition to policy-based IPsec-VPN connections. The updates do not apply to SSL-VPN connections.

## Change details {#section_wvs_g4z_ghb .section}

You can find the following changes in the console:

-   Two routing methods are available in the details page of a VPN Gateway.

    -   **Policy-based Routing**: Traffic is forwarded based on source IP addresses and destination IP addresses.
    -   **Destination-based Routing**: Traffic is forwarded only based on destination IP addresses.
    **Note:** Currently, only policy-based routing and destination-based routing are supported in the console. Support for dynamic routing is in development.

-   The route table of a VPN Gateway can be synchronized to the VPC route table automatically or manually.

## Change an existing VPN Gateway to route-based IPsec-VPN {#section_nts_34z_ghb .section}

Existing VPN Gateways do not support the route-based IPsec-VPN function and route tables are unavailable in the console. If you need this function, open a ticket.

Newly created VPN Gateways support the route-based IPsec-VPN function by default. You can view the route table in the details page of a VPN Gateway.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/150978/155546564842114_en-US.png)

