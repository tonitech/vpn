# VPN Gateway {#concept_r5s_gzv_wdb .concept}

Alibaba Cloud VPN Gateway is an internet-based service that connects enterprises' data centers and office networks with Alibaba Cloud VPCs in a secure and reliable manner through encrypted channels. The VPN Gateway provides the IPsec-VPN connection and the SSL-VPN connection.

**Note:** Note: Alibaba Cloud VPN gateway provides services in accordance with the relevant national policies and regulations. It does not provide Internet access function.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13346/15397471786217_en-US.png)

## Functions {#section_c4z_jsx_wdb .section}

The VPN Gateway provides IPSEC-VPN and SSL-VPN capabilities:

-   IPsec-VPN

    IPsec-VPN provides a VPN connection from the site to the site, you can connect a local data center with a private network using IPsec-VPN, or connect two vpcs. IPsec-VPN supports IKEv1 protocol and IKEv2 protocol. Any devices supporting the two protocols can connect to the VPN Gateway of Alibaba Cloud, such as Huawei, Huasan, Hillstone, Sinfor, Cisco ASA, Juniper, SonicWall, Nokia, IBM, Ixia and so on.

    For more information, see [Configure a site-to-site connection](https://help.aliyun.com/document_detail/65072.html) and [Configure a VPC-to-VPC connection](https://help.aliyun.com/document_detail/65073.html).

-   SSL-VPN

    You can use the SSL-VPN feature to remotely access applications and services deployed in a VPC from the client. When the deployment is complete, you only need to load the certificate in the client to initiate the connection.

    For more information, see [Windows client remote access](https://help.aliyun.com/document_detail/64994.html), [Mac client remote access](https://help.aliyun.com/document_detail/65068.html) and [Linux client remote access](https://help.aliyun.com/document_detail/65075.html).


## Product Advantage {#section_ts4_msx_wdb .section}

VPN gateways have the following advantages:

-   Security: the transmission data is encrypted using Ike and IPSec protocol to ensure the security and reliability of the data.

-   High Availability: the use of dual-machine thermal standby architecture, the failure of the second-level switching, to ensure that the session is not interrupted, business has no perception.

-   Low Cost: it is cheaper to establish an encrypted channel based on the Internet than to build a dedicated line, and quickly build a hybrid cloud.

-   Configuration is simple: provisioning is available, the configuration takes effect in real time, and the deployment is completed quickly.


