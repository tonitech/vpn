# IPsec connections {#concept_pkd_53h_xdb .concept}

## 1. What should I do if the IPsec connection status is “Phase 1 of IKE Tunnel Negotiation Failed”? {#section_gjl_v3h_xdb .section}

Most reasons for the negotiation failure in the first phase are due to inconsistent parameter configurations. Pay careful attention to parameter configurations between the first-phase configuration of the Alibaba Cloud VPN gateway and the local VPN gateway. Possible reasons for the negotiation failure in the first phase include:

-   The pre-shared keys are inconsistent.

-   The IKE protocol versions are inconsistent.

-   The negotiation modes are inconsistent.

-   The LocalIds or RemoteIds are inconsistent.

-   The encryption or authentication algorithms are inconsistent.

-   The DH groups are inconsistent. For some devices, you must manually specify the parameter.

-   The VPN gateway on the local data center has not enabled NAT traversal.


In some extreme cases, the negotiation fails even when the parameters are completely consistent. In this situation, we recommend that you change the negotiation mode to the aggressive mode.

## 2. What should I do if the IPsec connection status is “Phase 2 of IKE Tunnel Negotiation Failed”? {#section_ijl_v3h_xdb .section}

Potential reasons of the negotiation failure in the second phase include:

-   The local network/remote network configured in the Alibaba Cloud VPN gateway is inconsistent with that configured in the VPN gateway of the local data center. For some local VPN gateways, you can use ACL to configure the local network/remote network. At this time, you must refer to related operation manuals.

-   The encryption or authentication algorithms are inconsistent.

-   The DH groups are inconsistent. For some devices, you must manually specify the parameter.


## 3. Why the IPsec connection status is “Phase 2 of IKE Tunnel Negotiation Succeeded”, but ECS instances in the VPC cannot access servers in the local data center? {#section_kjl_v3h_xdb .section}

If the local data center uses a public IP as a private IP and ECS instances in the local data center can access the Internet. You can refer to the following information to check route configurations:

-   Check route configurations on the VRouter.

-   Check firewall/iptables configurations of the local data center and make sure that accesses from the private networks of the VPC are allowed.


## 4. Why the IPsec connection status is “Phase 2 of IKE Tunnel Negotiation Succeeded”, but servers in the local data center cannot access ECS instances in the VPC? {#section_k41_w3h_xdb .section}

1.  Check if the routing and ACL configurations in the local data center allow traffic destined for the VPC to enter the VPN tunnel.

2.  Check if security group rules of the ECS instances allow accesses from the private networks of the local data center.


## 5. Why the IPsec connection status is “Phase 2 of IKE Tunnel Negotiation Succeeded”, but in multi-network scenarios some networks can communicate normally while some networks cannot? {#section_njl_v3h_xdb .section}

In multi-network scenarios, we recommend that you use the IKE V2 protocol.

If you have used the IKE V2 protocol but the problem persists, we recommend that you check the SA \(Security Association\) status of the VPN gateway of the local data center. Normally there is only one SA. For example, 172.30.96.0/19 === 10.0.0.0/8 172.30.128.0/17.

If there are multiple SAs, the VPN gateway of the local data center is using a non-standard IKE V2 protocol. At this time, you can only use multiple IPsec connections to connect the networks. For example, you can split the IPsec connection 172.30.96.0/19 <=\> 10.0.0.0/8 172.30.128.0/17 to IPsec connection A 172.30.96.0/19 <=\> 10.0.0.0/8 and IPsec connection B: 172.30.96.0/19 <=\> 172.30.128.0/17.

**Note:** Because two separated IPsec connections must share the first-phase SA, the first-phase negotiation parameters of the two IPsec connections must be consistent.

