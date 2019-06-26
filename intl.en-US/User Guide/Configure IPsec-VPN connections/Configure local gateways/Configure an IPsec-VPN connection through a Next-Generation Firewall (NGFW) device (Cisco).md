# Configure an IPsec-VPN connection through a Next-Generation Firewall \(NGFW\) device \(Cisco\) {#concept_h4z_jdd_xdb .concept}

This topic takes a Next-Generation Firewall \(NGFW\) device from Cisco as an example to show how to configure the VPN settings to connect an on-premises data center to Alibaba Cloud VPC. When using IPsec-VPN to create a site-to-site connection, you must configure the local gateway according to the IPsec-VPN connection configured for the Alibaba Cloud VPN Gateway.

The following table lists the network configurations of the VPC and the on-premises data center used in this example.

|Configuration|Example value|
|:------------|:------------|
|VPC|VSwitch CIDR block|192.168.10.0/24, 192.168.11.0/24|
|Public IP address of the gateway|47. xxx. xxx.161|
|On-premises data center|Intranet CIDR block|10.10.10.0/24|
|Public IP address of the firewall|124. xxx. xxx.171|

**Note:** If the on-premises data center is associated with multiple CIDR blocks that need to connect with a VPC, we recommend that you create an equivalent number of IPsec-VPN connections on Alibaba Cloud so that each CIDR block of the on-premises data center is connected with a VPC CIDR block.

## Configure an IKEv1 VPN {#section_d12_sfd_xdb .section}

 **Prerequisites** 

-   An IPsec-VPN connection is created in an Alibaba Cloud VPC. For more information, see [Create an IPsec-VPN connection](reseller.en-US/User Guide/Configure IPsec-VPN connections/Manage an IPsec-VPN connection/Create an IPsec-VPN connection.md#).

-   The configuration of the IPsec-VPN connection is downloaded. For more information, see [Download the configuration of an IPsec-VPN connection](reseller.en-US/User Guide/Configure IPsec-VPN connections/Manage an IPsec-VPN connection/Download the configuration of an IPsec-VPN connection.md#). The configurations in the following table are used in this example.

|Protocol|Configuration|Example value|
|:-------|:------------|:------------|
|IKE|Authentication Algorithm|SHA-1|
|Encryption Algorithm|AES-128|
|DH Group|group 2|
|IKE Version|IKE v1|
|SA Life Cycle|86400|
|Negotiation Mode|main|
|PSK|123456|
|IPsec|Authentication Algorithm|SHA-1|
|Authentication Algorithm|AES-128|
|DH Group|group 2|
|IKE Version|IKE v1|
|SA Life Cycle|86400|
|Negotiation Mode|esp|


 **Procedure** 

To load customer gateway configurations to the NGFW device from Cisco, follow these steps:

1.  Log on to the CLI of the NGFW device.
2.  Configure the isakmp policy.

    ```
    crypto isakmp policy 1 
    authentication pre-share 
    encryption aes
    hash sha 
    group  2
    lifetime 86400
    ```

3.  Configure the pre-shared key.

    ```
    crypto isakmp key 123456 address 47.xxx.xxx. 161
    ```

4.  Configure the IPsec protocol.

    ```
    crypto ipsec transform-set ipsecpro64 esp-aes esp-sha-hmac 
    mode tunnel
    ```

5.  Configure the Access Control List \(ACL\) and define the data flow to be protected.

    **Note:** If multiple CIDR blocks are configured in the local gateway device, you need to add ACL policies for each CIDR block.

    ```
    access-list 100 permit ip 10.10.10.0 0.0.0.255 192.168.10.0 0.0.0.255
    access-list 100 permit ip 10.10.10.0 0.0.0.255 192.168.20.0 0.0.0.255
    ```

6.  Configure IPsec policies.

    ```
    crypto map ipsecpro64 10 ipsec-isakmp
    set peer 47.xxx.xxx. 161
    set transform-set ipsecpro64
    set pfs group2
    match address 100
    ```

7.  Apply IPsec policies.

    ```
    interface g0/0
    crypto map ipsecpro64
    ```

8.  Configure static routes.

    ```
    ip route 192.168.10.0 255.255.255.0 47.xxx.xxx. 161
    ip route 192.168.20.0 255.255.255.0 47.xxx.xxx. 161
    ```

9.  Test the connectivity.

    You can perform a connectivity test by using a host in Alibaba Cloud that is connected to a host in your on-premises data center.


## Configure an IKEv2 VPN {#section_uxm_djd_xdb .section}

 **Prerequisites** 

-   An IPsec-VPN connection is created in an Alibaba Cloud VPC. For more information, see [Create an IPsec-VPN connection](reseller.en-US/User Guide/Configure IPsec-VPN connections/Manage an IPsec-VPN connection/Create an IPsec-VPN connection.md#).

-   The configurations of the IPsec-VPN connection are downloaded. For more information, see [Download the configuration of an IPsec-VPN connection](reseller.en-US/User Guide/Configure IPsec-VPN connections/Manage an IPsec-VPN connection/Download the configuration of an IPsec-VPN connection.md#). The configurations in the following table are used in this example.

    |Protocol|Configuration|Example value|
    |:-------|:------------|:------------|
    |IKE|Authentication Algorithm|SHA-1|
    |Encryption Algorithm|AES-128|
    |DH Group|group 2|
    |IKE Version|IKE v2|
    |SA Life Cycle|86400|
    |PRF Algorithm|SHA-1|
    |PSK|123456|
    |IPsec|Authentication Algorithm|SHA-1|
    |Encryption Algorithm|AES-128|
    |DH Group|group 2|
    |IKE Version|IKE v2|
    |SA Life Cycle|86400|
    |Negotiation Mode|esp|


## Procedure {#section_r5v_dfd_xdb .section}

To load customer gateway configurations to the NGFW device from Cisco, follow these steps:

1.  Log on to the CLI of the NGFW device.
2.  Configure the phase one IKE algorithm.

    ```
    crypto ikev2 proposal daemon 
    encryption aes-cbc-128
    integrity sha1
    group 2
    ```

3.  Configure IKE v2 policies and apply the proposal.

    ```
    crypto ikev2 policy ipsecpro64_v2
    proposal daemon
    ```

4.  Configure the pre-shared key.

    ```
    crypto ikev2 keyring ipsecpro64_v2 
    peer vpngw 
    address 47.xxx.xxx. 161
    pre-shared-key 0 123456
    ```

5.  Configure the identity authentication.

    ```
    crypto ikev2 profile ipsecpro64_v2
    match identity remote address 47.xxx.xxx. 161 255.255.255.255
    identity local address 10.10.10.1 
    authentication remote pre-share     
    authentication local pre-share 
    keyring local ipsecpro64_v2
    ```

6.  Configure the IPsec security protocol.

    ```
    crypto ipsec transform-set ipsecpro64_v2 esp-aes esp-sha-hmac
    mode tunnel
    ```

7.  Configure the ACL \(access control list\) and define the data stream to be protected.

    **Note:** If multiple CIDR blocks are configured in the local gateway device, you need to add ACL policies for each CIDR block.

    ```
    access-list 100 permit ip 10.10.10.0 0.0.0.255 192.168.10.0 0.0.0.255
    access-list 100 permit ip 10.10.10.0 0.0.0.255 192.168.20.0 0.0.0.255
    ```

8.  Configure IPsec policies.

    ```
    crypto map ipsecpro64_v2 10 ipsec-isakmp
    set peer 47.xxx.xxx. 161
    set transform-set ipsecpro64_v2 
    set ikev2-profile ipsecpro64_v2
    match address 100
    ```

9.  Apply IPsec policies.

    ```
    interface g0/1
    crypto map ipsecpro64_v2
    ```

10. Configure static routes.

    ```
    ip route 192.168.10.0 255.255.255.0 47.xxx.xxx. 161
    ip route 192.168.20.0 255.255.255.0 47.xxx.xxx. 161
    ```

11. Test the connectivity.

    You can perform a connectivity test by using a host in Alibaba Cloud that is connected to a host in your on-premises data center.


