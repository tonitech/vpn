# IPsec-VPN connections FAQ {#concept_pkd_53h_xdb .concept}

## 1. What do I do if the IPsec-VPN connection status is “Phase 1 of IKE Tunnel Negotiation Failed”? {#section_gjl_v3h_xdb .section}

A negotiation failure during IKE phase one negotiation may be caused by inconsistent parameters between the phase one configuration of the Alibaba Cloud VPN Gateway and that of the local gateway. Possible causes and corresponding solutions are provided in the following table.

|Cause|Solution|Log|
|-----|--------|---|
|The pre-shared keys are inconsistent.|Use the same pre-shared key when you create the IPsec-VPN connection and configure the local gateway.| ``` {#codeblock_w1j_y5z_sef}
invalid HASH_V1 payload length, decryption failed?
could not decrypt payloads
message parsing failed
```

 |
|The IKE protocol versions are inconsistent.|Use the same IKE version. For example, you can set the IKE version to IKEv1 or IKEv2 for both ends of the IPsec-VPN connection.| ``` {#codeblock_0bb_yx8_yfz}
parsed IKE_SA_INIT response 0 [ N(NO_PROP) ]
received NO_PROPOSAL_CHOSEN notify error
received AUTHENTICATION_FAILED error notify
```

 |
|The negotiation modes are inconsistent.|Use the same negotiation mode. For example, you can set the negotiation mode to main or aggressive for both ends of the IPsec-VPN connection.| ``` {#codeblock_vgt_rm1_9gp}
received AUTHENTICATION_FAILED error notifyed
```

 |
|The LocalIds or RemoteIds are inconsistent.|Use the same LocalId and RemoteId.| ``` {#codeblock_dzl_4ns_2sn}
[IKE] IDir xxxx does not match to xxxx
```

 |
|The encryption or authentication algorithms are inconsistent.|Use the same encryption and authentication algorithms for both ends of the IPsec-VPN connection.|None|
|The DH groups are inconsistent.|Use the same DH group. For example, you can set the DH group to group2 for both ends of the IPsec-VPN connection.|None|
|The peer-end gateway does not respond.|Make sure that the peer-end gateway is normal.| ``` {#codeblock_qqc_vcf_etg}
[IKE] sending retransmit 1 of request message ID 0, seq 1
```

 |
|An invalid public IP address is set when you create the customer gateway.|Set a valid public IP address of the local gateway when you create the customer gateway.| ``` {#codeblock_bq1_d88_44o}
received UNSUPPORTED_CRITICAL_PAYLOAD error notify
```

 |

In some extreme cases, the negotiation fails even when the parameters are completely consistent. In this situation, we recommend that you change the negotiation mode to the aggressive mode.

## 2. What do I do if the IPsec-VPN connection status is “Phase 2 of IKE Tunnel Negotiation Failed”? {#section_ijl_v3h_xdb .section}

Possible causes for an IKE phase two negotiation failure, and corresponding solutions, are provided in the following table.

|Cause|Solution|Log|
|-----|--------|---|
|The local network and remote network parameters configured in the Alibaba Cloud VPN Gateway are inconsistent with those configured in the local gateway.|Check the CIDR blocks that are configured for both ends of the IPsec-VPN connection and make sure that they are set correctly.| -   **main** mode

    ``` {#codeblock_kdp_t8m_4q0}
received INVALID_ID_INFORMATION error notify
    ```

-   **aggressive** mode

    ``` {#codeblock_jof_uv2_zo2}
received HASH payload does not match 
integrity check failed
    ```


 |
|The encryption or authentication algorithms are inconsistent.|Check the encryption and authentication algorithms that are configured for both ends of the IPsec-VPN connection and make sure that you use the same encryption and authentication algorithms.| ``` {#codeblock_y0m_so7_x1i}
parsed INFORMATIONAL_V1 request xxxx [ HASH N(NO_PROP) ]
received NO_PROPOSAL_CHOSEN error notify
```

 |
|The DH groups are inconsistent.|Set the same DH groups for both ends of the IPsec-VPN connection.| ``` {#codeblock_vs8_pls_vxm}
ESP:AES_CBC_256/HMAC_SHA1_96/MODP_1024/NO_EXT_SEQ
ESP:AES_CBC_128/HMAC_SHA1_96/MODP_1024/NO_EXT_SEQ, 
ESP:AES_CBC_128/AES_CBC_192/AES_CBC_256/3DES_CBC/BLOWFISH_CBC_256/HMAC_SHA2_256_128/HMAC_SHA2_384_192/HMAC_SHA2_512_256/HMAC_SHA1_96/AES_XCBC_96/HMAC_MD5_96/NO_EXT_SEQ
no matching proposal found, sending NO_PROPOSAL_CHOSEN
```

 |

## 3. What do I do if the IPsec-VPN connection status is “Phase 2 of IKE Tunnel Negotiation Succeeded”, but ECS instances in the VPC cannot access servers in the on-premises data center? {#section_kjl_v3h_xdb .section}

If the on-premises data center uses a public IP address as a private IP address and ECS instances can access the Internet, you need to open a ticket to adjust the configurations. Additionally, you can check the route configurations as follows:

-   Check route configurations on the VRouter.

-   Check firewall/iptables configurations of the on-premises data center and make sure that access from the private networks of the VPC are allowed.


## 4. What do I do if the IPsec-VPN connection status is “Phase 2 of IKE Tunnel Negotiation Succeeded”, but servers in the on-premises data center cannot access ECS instances in the VPC? {#section_k41_w3h_xdb .section}

Check the configurations by referring to the following information:

1.  Check if the routing and ACL configurations in the on-premises data center allow traffic destined for the VPC to enter the VPN tunnel.

2.  Check if security group rules of the ECS instances allow access from the private networks of the on-premises data center.


## 5. Why the IPsec-VPN connection status is “Phase 2 of IKE Tunnel Negotiation Succeeded”, but in my multi-network scenario some networks can communicate normally while some networks cannot? {#section_njl_v3h_xdb .section}

Usually, the IKE V2 protocol is not being used. In multi-network scenarios, we recommend that you use the IKE V2 protocol.

If you have used the IKE V2 protocol but the problem persists, we recommend that you check the SA \(Security Association\) status of the gateway of the on-premises data center. Normally only one SA exists. For example, 172.30.96.0/19 === 10.0.0.0/8 172.30.128.0/17.

If multiple SAs exist, the gateway of the on-premises data center is using a non-standard IKE V2 protocol. As a result, you can only use multiple IPsec-VPN connections to connect the networks. For example, you can split the IPsec-VPN connection 172.30.96.0/19 <=\> 10.0.0.0/8 172.30.128.0/17 to IPsec-VPN connection A 172.30.96.0/19 <=\> 10.0.0.0/8 and IPsec-VPN connection B: 172.30.96.0/19 <=\> 172.30.128.0/17.

**Note:** Because two separated IPsec-VPN connections must share the first-phase SA, the first-phase negotiation parameters of the two IPsec-VPN connections must be consistent.

## 6. Why is my IPsec-VPN connection through my USGX series NGFW device from Huawei abnormal even though its status is “Phase 2 of IKE Tunnel Negotiation Succeeded” ? {#section_cjb_w3x_fhb .section}

**Cause**: The Huawei firewall device has NAT enabled at the outbound interface, which means the IP addresses of all packets sent from the outbound interface are converted to the IP address of this interface.

**Solution**:

1.  Run the `nat disable` command to disable the NAT function.
2.  Configure NAT policies.

    ```
    nat-policy interzone trust untrust outbound
    policy 0
    action no-nat
    policy source 192.168.0.0 mask 24
    policy destination 192.168.1.0 mask 24
    policy 1 
    action source-nat
    policy source 192.168.0.0 mask 24
    easy-ip Dialer0
    ```

    Where:

    192.168.0.0 is the intranet CIDR block of the local gateway.

    192.168.1.0 is the intranet CIDR block of the VPN Gateway.

    Dialer0 is the outbound interface of the local gateway.


