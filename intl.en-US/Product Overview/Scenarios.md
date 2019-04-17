# Scenarios {#concept_dqh_ysx_wdb .concept}

## Site-to-site connections {#section_azx_ctx_wdb .section}

You can build a hybrid cloud environment by creating an IPsec-VPN tunnel to connect a VPC to your local data center.

**Note:** IPsec connections require that the IP address ranges of the local data center and the VPC do not conflict with each other. And a static, public IP is configured for the local gateway device.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/15554636203235_en-US.png)

## Multi-site connections {#section_czx_ctx_wdb .section}

You can create multiple IPsec connections to connect multiple sites to a VPC. With the VPN-Hub function provided by VPN Gateway, each site not only communicates with the VPC, but can also communicate with each other. VPN-Hub meets the needs of large enterprises to establish an intranet communications between various sites.

**Note:** IPsec connections require that the IP address ranges of each site cannot conflict with the IP address range of the VPC to be connected.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/15554636203236_en-US.png)

**VPC-to-VPC connections**

You can create a connection between two VPCs over an IPsec-VPN tunnel.

**Note:** The IP address ranges of the VPCs cannot conflict with each other.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/15554636203237_en-US.png)

## Point-to-site connections {#section_fzx_ctx_wdb .section}

You can connect a client to a VPC over the SSL-VPN tunnel to meet the needs of working remotely. With SSL-VPN connections, you can securely access applications deployed in a VPC wherever Internet access is available.

SSL-VPN connections support remote access from the clients of various operating systems, including Windows, Linux, Mac, IOS, and Android.

**Note:** The IP address range of a client used to access a VPC cannot conflict with the IP address range of the VPC.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/15554636203238_en-US.png)

## IPsec-VPN and SSL-VPN connections {#section_hzx_ctx_wdb .section}

You can combine the IPsec and SSL-VPN connections to expand your network topology. Once connections are established, the client can access the applications deployed in the connected VPC, and can also access the applications deployed in the connected office sites.

**Note:** All private IP address ranges to be connected cannot conflict with one another.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/15554636213239_en-US.png)

## Multinational intranet connections \(VPN Gateway and Express Connect\) {#section_jzx_ctx_wdb .section}

Multinational enterprises can use Express Connect to connect two VPCs with low latency and use VPN Gateway to connect local sites at low cost to build secure and reliable intranet connections.

**Note:** All private IP address ranges to be connected cannot conflict with one another.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13347/15554636213240_en-US.png)

