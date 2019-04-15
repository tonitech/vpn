# Juniper防火墙配置 {#concept_h4z_jdd_xdb .concept}

使用IPsec-VPN建立站点到站点的连接时，在配置完阿里云VPN网关后，您还需在本地站点的网关设备中进行VPN配置。本文以Juniper防火墙为例介绍如何在本地站点中加载VPN配置。

## 前提条件 {#section_zc5_l4c_ghb .section}

-   已经在阿里云VPC内创建了IPsec连接。详细说明，请参见[创建IPsec连接](intl.zh-CN/用户指南/配置IPsec-VPN/管理IPsec连接/创建IPsec连接.md#)。

-   已经下载了IPsec连接的配置。详细说明，请参见[下载IPsec连接配置](intl.zh-CN/用户指南/配置IPsec-VPN/管理IPsec连接/下载IPsec连接配置.md#)。

    本操作的IPsec连接配置如下表所示。

    -   IPsec协议信息

|配置|示例值|
|:-|:--|
|IKE|认证算法|md5|
|加密算法|3des|
|DH分组|group2|
|IKE版本|IKE v1|
|生命周期|86400|
|协商模式|main|
|PSK|123456|
|IPsec|认证算法|md5|
|加密算法|des|
|DH分组|group2|
|IKE版本|IKE v1|
|生命周期|28800|

    -   网络配置信息

|配置|示例值|
|:-|:--|
|VPC配置|私网CIDR|192.168.1.0/24|
|网关公网IP|47.xxx.xxx.56|
|IDC网络配置|私网CIDR|192.168.18.0/24|
|网关公网IP|122.xxx.xxx.248|


## 操作步骤 {#section_u2t_z4c_ghb .section}

完成以下操作，在Juniper防火墙中加载用户网关的配置：

1.  登录防火墙设备的命令行配置界面。
2.  配置基本网络、安全域和地址簿信息。

    ```
    set security zones security-zone trust address-book address net-cfgr_192-168-18-0--24 192.168.18.0/24
    set security zones security-zone vpn address-book address net-cfgr_192-168-1-0--24 192.168.1.0/24
    ```

3.  配置IKE策略。

    ```
    set security ike policy ike-policy-cfgr mode main
    set security ike policy ike-policy-cfgr pre-shared-key ascii-text "123456"
    ```

4.  配置IKE网关、出接口和协议版本。

    ```
    set security ike gateway ike-gate-cfgr ike-policy ike-policy-cfgr
    set security ike gateway ike-gate-cfgr address 47.xxx.xxx.56
    set security ike gateway ike-gate-cfgr external-interface ge-0/0/3
    set security ike gateway ike-gate-cfgr version v1-only
    ```

5.  配置IPsec策略。

    ```
    set security ipsec policy ipsec-policy-cfgr proposal-set standard
    ```

6.  应用IPsec策略。

    ```
    set security ipsec vpn ipsec-vpn-cfgr ike gateway ike-gate-cfgr
    set security ipsec vpn ipsec-vpn-cfgr ike ipsec-policy ipsec-policy-cfgr
    set security ipsec vpn ipsec-vpn-cfgr bind-interface st0.0
    set security ipsec vpn ipsec-vpn-cfgr establish-tunnels immediately
    set security ipsec policy ipsec-policy-cfgr perfect-forward-secrecy keys group2
    ```

7.  配置出站策略。

    ```
    set security policies from-zone trust to-zone vpn policy trust-vpn-cfgr match source-address net-cfgr_192-168-18-0--24
    set security policies from-zone trust to-zone vpn policy trust-vpn-cfgr match destination-address net-cfgr_192-168-1-0--24
    set security policies from-zone trust to-zone vpn policy trust-vpn-cfgr match application any
    set security policies from-zone trust to-zone vpn policy trust-vpn-cfgr then permit
    ```

8.  配置入站策略。

    ```
    set security policies from-zone vpn to-zone trust policy vpn-trust-cfgr match source-address net-cfgr_192-168-1-0--24
    set security policies from-zone vpn to-zone trust policy vpn-trust-cfgr match destination-address net-cfgr_192-168-18-0--24
    set security policies from-zone vpn to-zone trust policy vpn-trust-cfgr match application any
    set security policies from-zone vpn to-zone trust policy vpn-trust-cfgr then permit
    ```


