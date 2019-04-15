# IPsec连接常见问题 {#concept_pkd_53h_xdb .concept}

## 1. IPsec连接状态为“第一阶段协商失败”怎么办？ {#section_gjl_v3h_xdb .section}

IPsec VPN第一阶段协商失败，可能与阿里云VPN网关同本地VPN网关的第一阶段配置参数不一致有关，可能的原因及解决方法如下：

-   **原因**：预共享密钥不一致。

    **对应日志**：

    ```
    invalid HASH_V1 payload length, decryption failed?
    could not decrypt payloads
    message parsing failed
    ```

    **解决方法**：设置一致的预共享密钥。

-   **原因**：IKE协议版本不一致。

    **对应日志**：

    ```
    parsed IKE_SA_INIT response 0 [ N(NO_PROP) ]
    received NO_PROPOSAL_CHOSEN notify error
    received AUTHENTICATION_FAILED error notify
    ```

    **解决方法**：设置一致的IKE协议版本，如建立IPsec连接的两端网关都设置为IKEv1版本或IKEv2版本。

-   **原因**：协商模式不一致。

    **对应日志**：

    ```
    received AUTHENTICATION_FAILED error notifyed
    ```

    **解决方法**：设置一致的协商模式，如建立IPsec连接的两端网关都设置为main或aggressive。

-   **原因**：LocalId或RemoteId不一致。

    **对应日志**：

    ```
    [IKE] IDir xxxx does not match to xxxx
    ```

    **解决方法**：设置一致的LocalId或RemoteId。

-   **原因**：加密、认证算法不一致。

    **解决方法**：确认两端网关的加密、认证算法，并设置一致。

-   **原因**：DH分组不一致。

    **解决方法**：设置一致的DH组，如建立IPsec连接的两端网关都将DH组设置为group2。

-   **原因**：对端网关不响应。

    **对应日志**：

    ```
    [IKE] sending retransmit 1 of request message ID 0, seq 1
    ```

    **解决方法**：确认对端网关是否异常。

-   **原因**：创建用户网关时，设置错误的公网IP。

    **对应日志**：

    ```
    received UNSUPPORTED_CRITICAL_PAYLOAD error notify
    ```

    **解决方法**：创建用户网关时，应设置本地网关的公网IP。


部分极端情况下，参数完全一致也无法协商成功，此时建议将两端的协商模式改为野蛮模式（aggressive）。

## 2. IPsec连接状态为“第二阶段协商失败”怎么办？ {#section_ijl_v3h_xdb .section}

IPsec连接第二阶段协商失败的可能原因及解决方法如下：

-   **原因**：感兴趣流不一致。

    **对应日志**：

    -   主模式

        ```
        received INVALID_ID_INFORMATION error notify
        ```

    -   野蛮模式

        ```
        received HASH payload does not match 
        integrity check failed
        ```

    **解决方法**：确认建立IPsec连接的两端网关的私网网段，并正确设置。

-   **原因**：加密算法或认证算法不一致。

    **对应日志**：

    ```
    parsed INFORMATIONAL_V1 request xxxx [ HASH N(NO_PROP) ]
    received NO_PROPOSAL_CHOSEN error notify
    ```

    **解决方法**：确认两端网关的加密、认证算法，并设置一致。

-   **原因**：DH分组不一致。

    **对应日志**：

    ```
    ESP:AES_CBC_256/HMAC_SHA1_96/MODP_1024/NO_EXT_SEQ
    ESP:AES_CBC_128/HMAC_SHA1_96/MODP_1024/NO_EXT_SEQ, 
    ESP:AES_CBC_128/AES_CBC_192/AES_CBC_256/3DES_CBC/BLOWFISH_CBC_256/HMAC_SHA2_256_128/HMAC_SHA2_384_192/HMAC_SHA2_512_256/HMAC_SHA1_96/AES_XCBC_96/HMAC_MD5_96/NO_EXT_SEQ
    no matching proposal found, sending NO_PROPOSAL_CHOSEN
    ```

    **解决方法**：设置一致的DH组。


## 3. 为什么IPsec连接状态为“第二阶段协商成功”，但VPC内的ECS实例无法访问本地IDC内的服务器？ {#section_kjl_v3h_xdb .section}

如果本地IDC内存在将公网IP作为私有IP使用的情况且ECS实例可以访问公网，需要提工单进行相关配置。否则请参考以下信息检查路由等相关配置：

-   检查VPC路由器上的路由配置。

-   检查本地IDC内的防火墙/iptables相关的设置，确认是否允许VPC的私网网段访问。


## 4. 为什么IPsec连接状态为“第二阶段协商成功”，但本地IDC内的服务器无法访问VPC内的ECS实例？ {#section_k41_w3h_xdb .section}

1.  检查本地IDC内的路由和ACL配置是否允许访问VPC的流量进入VPN隧道。

2.  检查ECS实例的安全组规则是否允许本地IDC中的私网网段访问。


## 5. 为什么IPsec连接状态为“第二阶段协商成功”，但是多网段场景下部分网段通信正常，部分网段通信不正常？ {#section_njl_v3h_xdb .section}

多网段场景下，建议使用IKE V2协议。

如果已经使用了IKE V2协议但问题仍然存在，建议检查本地IDC的VPN网关的SA状态，正常情况下只有一个SA，例如172.30.96.0/19 === 10.0.0.0/8 172.30.128.0/17。

如果存在多个SA说明本地IDC的VPN网关使用非标准的IKE V2协议，此时只能使用多个IPsec连接将各个网段连接起来。例如可以将IPsec连接：172.30.96.0/19 <=\> 10.0.0.0/8 172.30.128.0/17拆分为IPsec连接A：172.30.96.0/19 <=\> 10.0.0.0/8和IPsec连接B：172.30.96.0/19 <=\> 172.30.128.0/17。

**说明：** 拆分IPsec连接后由于两个IPsec连接需要共享第一阶段SA，所以两个IPsec连接的第一阶段协商参数需保持一致。

## 为什么IPsec连接状态为“第二阶段协商成功”，但IPSec VPN单向不通？ {#section_cjb_w3x_fhb .section}

**原因**：本地网关使用的是华为防火墙，且在出接口配置了nat enable，导致从该接口流出的所有数据包的源IP地址，都转换为该接口的IP地址。

**解决方法**：

1.  运行`nat disable`命令，关闭出接口的NAT功能。
2.  配置NAT策略。

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

    其中：

    192.168.0.0：本地网关的私网网段。

    192.168.1.0：VPC侧VPN网关的私网网段。

    Dialer0：本地网关的出接口。


