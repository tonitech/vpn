# Configure an IPsec-VPN connection through an SRX series Services Gateway firewall device from Juniper {#concept_h4z_jdd_xdb .concept}

This topic takes an SRX series Services Gateway firewall device from Juniper as an example to show how to configure the VPN settings to connect an on-premises data center to Alibaba Cloud VPC. When using IPsec-VPN to create a site-to-site connection, you must configure the local gateway according to the IPsec-VPN connection configured for the Alibaba Cloud VPN Gateway.

## Prerequisites {#section_zc5_l4c_ghb .section}

-   An IPsec-VPN connection is created in an Alibaba Cloud VPC. For more information, see [Create an IPsec-VPN connection](reseller.en-US/User Guide/Configure IPsec-VPN connections/Manage an IPsec-VPN connection/Create an IPsec-VPN connection.md#).

-   The configuration of the IPsec-VPN connection is downloaded. For more information, see [Download the configuration of an IPsec-VPN connection](reseller.en-US/User Guide/Configure IPsec-VPN connections/Manage an IPsec-VPN connection/Download the configuration of an IPsec-VPN connection.md#).

    The IPsec-VPN connection configurations in the following table are used in this example.

    -   IPsec protocol

|Configuration|Example value|
|:------------|:------------|
|IKE|Authentication Algorithm|md5|
|Encryption Algorithm|3des|
|DH Group|group2|
|IKE Version|IKE v1|
|SA Life Cycle|86400|
|Negotiation Mode|main|
|PSK|123456|
|IPsec|Authentication Algorithm|md5|
|Encryption Algorithm|des|
|DH Group|group2|
|IKE Version|IKE v1|
|SA Life Cycle|28800|

    -   Network configurations

|Network configuration|Example value|
|:--------------------|:------------|
|VPC|CIDR block of the VSwitch|192.168.1.0/24|
|Public IP address of the gateway|47.xxx.xxx.56|
|On-premises data center|CIDR block of the intranet|192.168.18.0/24|
|Public IP address of the gateway|122.xxx.xxx.248|


## Procedure {#section_u2t_z4c_ghb .section}

To load customer gateway configurations to the Juniper firewall device, follow these steps:

1.  Log on to the CLI of the firewall device.
2.  Configure the basic network, security zone, and address book.

    ```
    set security zones security-zone trust address-book address net-cfgr_192-168-18-0--24 192.168.18.0/24
    set security zones security-zone vpn address-book address net-cfgr_192-168-1-0--24 192.168.1.0/24
    ```

3.  Configure IKE policies.

    ```
    set security ike policy ike-policy-cfgr mode main
    set security ike policy ike-policy-cfgr pre-shared-key ascii-text "123456"
    ```

4.  Configure the IKE gateway, outbound interface, and protocol version.

    ```
    set security ike gateway ike-gate-cfgr ike-policy ike-policy-cfgr
    set security ike gateway ike-gate-cfgr address 47.xxx.xxx.56
    set security ike gateway ike-gate-cfgr external-interface ge-0/0/3
    set security ike gateway ike-gate-cfgr version v1-only
    ```

5.  Configure IPsec policies.

    ```
    set security ipsec policy ipsec-policy-cfgr proposal-set standard
    ```

6.  Apply IPsec policies.

    ```
    set security ipsec vpn ipsec-vpn-cfgr ike gateway ike-gate-cfgr
    set security ipsec vpn ipsec-vpn-cfgr ike ipsec-policy ipsec-policy-cfgr
    set security ipsec vpn ipsec-vpn-cfgr bind-interface st0.0
    set security ipsec vpn ipsec-vpn-cfgr establish-tunnels immediately
    set security ipsec policy ipsec-policy-cfgr perfect-forward-secrecy keys group2
    ```

7.  Configure outbound policies.

    ```
    set security policies from-zone trust to-zone vpn policy trust-vpn-cfgr match source-address net-cfgr_192-168-18-0--24
    set security policies from-zone trust to-zone vpn policy trust-vpn-cfgr match destination-address net-cfgr_192-168-1-0--24
    set security policies from-zone trust to-zone vpn policy trust-vpn-cfgr match application any
    set security policies from-zone trust to-zone vpn policy trust-vpn-cfgr then permit
    ```

8.  Configure inbound policies.

    ```
    set security policies from-zone vpn to-zone trust policy vpn-trust-cfgr match source-address net-cfgr_192-168-1-0--24
    set security policies from-zone vpn to-zone trust policy vpn-trust-cfgr match destination-address net-cfgr_192-168-18-0--24
    set security policies from-zone vpn to-zone trust policy vpn-trust-cfgr match application any
    set security policies from-zone vpn to-zone trust policy vpn-trust-cfgr then permit
    ```


