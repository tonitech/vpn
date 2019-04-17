# Tutorial overview {#concept_d52_4lz_wdb .concept}

This section includes a tutorial that illustrates how to use IPsec-VPN to connect a VPC to a local data center. This section also includes a tutorial that illustrates how to use IPsec-VPN to connect two VPCs.

## Prerequisites {#section_jwb_plz_wdb .section}

Before creating a site-to-site VPN connection, make sure the following conditions are met:

-   The gateway device of the local data center support IKEv1 and ikev2 protocols.

    IPsec-VPN supports IKEv1 and IKEv2 protocols. Any device that supports these two protocols can connect to Alibaba Cloud VPN Gateway. Supported devices include: Huawei, H3C, SANGFOR, Cisco ASA, Juniper, SonicWall, Nokia, IBM, and Ixia.

-   A static IP address is configured for the local gateway.

-   The IP address ranges of the VPC and local data center to be connected do not conflict with each other.


## Create a site-to-site connection {#section_lwb_plz_wdb .section}

To use IPsec-VPN to connect different sites, you must:

1.  Create a VPN Gateway with IPsec-VPN enabled.

    Up to 10 IPsec connections can be established within a VPN Gateway.

2.  Create a customer gateway.

    By creating a customer gateway, you can upload the configuration of the local gateway to the Alibaba Cloud. A customer gateway can be connected to multiple VPN Gateways.

3.  Create an IPsec connection.

    Create an IPsec connection to connect the VPN Gateway and customer gateway to establish an encrypted communication tunnel.

4.  Configure the local gateway.

    Configure the local gateway according to the IPsec connection configurations. For more information, see [../../../../dita-oss-bucket/SP\_74/DNVPN11870506/EN-US\_TP\_13367.md\#](../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure local gateways/Configure H3C firewall.md#) and [../../../../dita-oss-bucket/SP\_74/DNVPN11870506/EN-US\_TP\_13369.md\#](../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure local gateways/Configure strongSwan.md#).

5.  Configure the route and security groups.

    Finally, you must configure corresponding routing in the VPC to complete the data transmission.


