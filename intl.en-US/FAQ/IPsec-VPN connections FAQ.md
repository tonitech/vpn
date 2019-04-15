# IPsec-VPN connections FAQ {#concept_pkd_53h_xdb .concept}

## 1. What do I do if the IPsec-VPN connection status is “Phase 1 of IKE Tunnel Negotiation Failed”? {#section_gjl_v3h_xdb .section}

A negotiation failure during IKE phase one negotiation may be caused by inconsistent parameters between the phase one configuration of the Alibaba Cloud VPN gateway and that of the local gateway. Possible causes and corresponding solutions are provided as follows:

-   **Cause**: The pre-shared keys are inconsistent.

    **Log**:

    ```
    invalid HASH_V1 payload length, decryption failed?
    could not decrypt payloads
    message parsing failed
    ```

    **Solution**: Use the same pre-shared key when you create the IPsec-VPN connection and configure the local gateway.

-   **Cause**: The IKE protocol versions are inconsistent.

    **Log**:

    ```
    parsed IKE_SA_INIT response 0 [ N(NO_PROP) ]
    received NO_PROPOSAL_CHOSEN notify error
    received AUTHENTICATION_FAILED error notify
    ```

    **Solution**: Use the same IKE version. For example, you can set the IKE version to IKEv1 or IKEv2 for both ends of the IPsec-VPN connection.

-   **Cause**: The negotiation modes are inconsistent.

    **Log**:

    ```
    received AUTHENTICATION_FAILED error notifyed
    ```

    **Solution**: Use the same negotiation mode. For example, you can set the negotiation mode to main or aggressive for both ends of the IPsec-VPN connection.

-   **Cause**: The LocalIds or RemoteIds are inconsistent.

    **Log**:

    ```
    [IKE] IDir xxxx does not match to xxxx
    ```

    **Solution**: Use the same LocalId and RemoteId.

-   **Cause**: The encryption or authentication algorithms are inconsistent.

    **Solution**: Use the same encryption and authentication algorithms for both ends of the IPsec-VPN connection.

-   **Cause**: The DH groups are inconsistent.

    **Solution**: Use the same DH group. For example, you can set DH group to group2 for both ends of the IPsec-VPN connection.

-   **Cause**: The peer-end gateway does not respond.

    **Log**:

    ```
    [IKE] sending retransmit 1 of request message ID 0, seq 1
    ```

    **Solution**: Make sure that the peer-end gateway is normal.

-   **Cause**: An invalid public IP address is set when you create the customer gateway.

    **Log**:

    ```
    received UNSUPPORTED_CRITICAL_PAYLOAD error notify
    ```

    **Solution**: Set a valid public IP address of the local gateway when you create the customer gateway.


In some extreme cases, the negotiation fails even when the parameters are completely consistent. In this situation, we recommend that you change the negotiation mode to the aggressive mode.

## 2. What do I do if the IPsec-VPN connection status is “Phase 2 of IKE Tunnel Negotiation Failed”? {#section_ijl_v3h_xdb .section}

Possible causes for an IKE phase two negotiation failure, and corresponding solutions, are provided as follows:

-   **Cause**: The local network and remote network parameters configured in the Alibaba Cloud VPN Gateway are inconsistent with those configured in the local gateway.

    **Log**:

    -   **main** mode

        ```
        received INVALID_ID_INFORMATION error notify
        ```

    -   **aggressive** mode

        ```
        received HASH payload does not match 
        integrity check failed
        ```

    **Solution**: Check the CIDR blocks configured for both ends of the IPsec-VPN connection and make sure that they are correctly set.

-   **Cause**: The encryption or authentication algorithms are inconsistent.

    **Log**:

    ```
    parsed INFORMATIONAL_V1 request xxxx [ HASH N(NO_PROP) ]
    received NO_PROPOSAL_CHOSEN error notify
    ```

    **Solution**: Check the encryption and authentication algorithms configured for both ends of the IPsec-VPN connection and make sure that you use the same encryption and authentication algorithms.

-   **Cause**: The DH groups are inconsistent.

    **Log**:

    ```
    ESP:AES_CBC_256/HMAC_SHA1_96/MODP_1024/NO_EXT_SEQ
    ESP:AES_CBC_128/HMAC_SHA1_96/MODP_1024/NO_EXT_SEQ, 
    ESP:AES_CBC_128/AES_CBC_192/AES_CBC_256/3DES_CBC/BLOWFISH_CBC_256/HMAC_SHA2_256_128/HMAC_SHA2_384_192/HMAC_SHA2_512_256/HMAC_SHA1_96/AES_XCBC_96/HMAC_MD5_96/NO_EXT_SEQ
    no matching proposal found, sending NO_PROPOSAL_CHOSEN
    ```

    **Solution**: Set the same DH groups for both ends of the IPsec-VPN connection.


## 3. Why the IPsec-VPN connection status is “Phase 2 of IKE Tunnel Negotiation Succeeded”, but ECS instances in the VPC cannot access servers in the on-premises data center? {#section_kjl_v3h_xdb .section}

If the on-premises data center uses a public IP as a private IP and ECS instances in the on-premises data center can access the Internet. You can see the following information to check route configurations:

-   Check route configurations on the VRouter.

-   Check firewall/iptables configurations of the on-premises data center and make sure that accesses from the private networks of the VPC are allowed.


## 4. Why the IPsec-VPN connection status is “Phase 2 of IKE Tunnel Negotiation Succeeded”, but servers in the on-premises data center cannot access ECS instances in the VPC? {#section_k41_w3h_xdb .section}

1.  Check if the routing and ACL configurations in the on-premises data center allow traffic destined for the VPC to enter the VPN tunnel.

2.  Check if security group rules of the ECS instances allow accesses from the private networks of the on-premises data center.


## 5. Why the IPsec-VPN connection status is “Phase 2 of IKE Tunnel Negotiation Succeeded”, but in multi-network scenarios some networks can communicate normally while some networks cannot? {#section_njl_v3h_xdb .section}

In multi-network scenarios, we recommend that you use the IKE V2 protocol.

If you have used the IKE V2 protocol but the problem persists, we recommend that you check the SA \(Security Association\) status of the gateway of the on-premises data center. Normally only one SA exists. For example, 172.30.96.0/19 === 10.0.0.0/8 172.30.128.0/17.

If multiple SAs exist, the gateway of the on-premises data center is using a non-standard IKE V2 protocol. At this time, you can only use multiple IPsec-VPN connections to connect the networks. For example, you can split the IPsec-VPN connection 172.30.96.0/19 <=\> 10.0.0.0/8 172.30.128.0/17 to IPsec-VPN connection A 172.30.96.0/19 <=\> 10.0.0.0/8 and IPsec-VPN connection B: 172.30.96.0/19 <=\> 172.30.128.0/17.

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


