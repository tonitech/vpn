# VPN Gateway {#concept_dxq_m3h_xdb .concept}

## 1. Does VPN Gateway support the classic network? {#section_sdq_n3h_xdb .section}

No. VPN Gateway supports only the VPC network. If you want to use VPN Gateway in the classic network, you must enable the ClassicLink function in VPC. For more information, see [Use IPsec-VPN in the classic network](../../../../intl.en-US/Best Practices/Use IPsec-VPN in the classic network.md#).

## 2. What are the prerequisites for a local site to access VPC through the IPsec-VPN function? {#section_tdq_n3h_xdb .section}

A static public IP and a gateway supporting the IKEv1 and IKEv2 protocols are required. For more information, see [Configure a site-to-site connection](../../../../intl.en-US/IPsec-VPN Quick Start/Configure a site-to-site connection.md#).

## 3. Can VPCs in different regions use VPN Gateway to achieve intercommunication? {#section_udq_n3h_xdb .section}

Yes. For more information, see [Configure a VPC-to-VPC connection](../../../../intl.en-US/IPsec-VPN Quick Start/Configure a VPC-to-VPC connection.md#).

## 4. Which local gateways does VPN Gateway support? {#section_vdq_n3h_xdb .section}

IPsec connections support IKEv1 and IKEv2 protocols. Therefore, any device that supports these two protocols can connect to Alibaba Cloud VPN Gateway. These devices include those from Huawei, H3C, Cisco, ASN, Juniper, SonicWall, Nokia, IBM, and Ixia. For more information, see [Local gateway configurations](../../../../intl.en-US/Best Practices/Local gateway configurations.md#).

## 5. Does VPN Gateway support SSL-VPN? {#section_wdq_n3h_xdb .section}

Yes. For more information, see [SSL-VPN](https://help.aliyun.com/document_detail/65282.html).

## 6. How many IPsec connections can be created for each VPN Gateway? {#section_xdq_n3h_xdb .section}

Each VPN Gateway can support up to 10 IPsec connections. If you want more IPsec connections, create more VPN Gateways.

## 7. Can I use VPN Gateway to access the Internet? {#section_ydq_n3h_xdb .section}

No. VPN Gateway only provides intranet access to VPCs. It does not provide access to the Internet.

## 8. Does the traffic between two VPCs connected by VPN Gateway go through the Internet? {#section_zdq_n3h_xdb .section}

No. When two VPCs in different regions achieve intercommunication through VPN Gateway, the traffic goes through the Alibaba Cloud network instead of the Internet.

## 9. Can I configure multiple remote networks in one IPsec connection? {#section_a2q_n3h_xdb .section}

Yes. You can separate the networks by commas. We recommend that you use the IKEv2 protocol.

## 10. Can I downgrade the VPN Gateway configuration? {#section_b2q_n3h_xdb .section}

Yes. You can submit a ticket to downgrade the configuration.

## 11. Can a VPN Gateway instance purchased before the launching of the SSL-VPN function use this function? {#section_c2q_n3h_xdb .section}

You cannot directly enable the SSL-VPN function on a VPN Gateway instance purchased before the launching of this function. You and must open a ticket if you want to enable the SSL-VPN function in this situation.

