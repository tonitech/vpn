# Mac客户端远程连接 {#concept_a1t_jvz_wdb .concept}

本文以Mac客户端为例介绍如何通过VPN网关拨号接入VPC。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13356/15608267963332_zh-CN.png)

## 开始之前 {#section_w4p_dyd_r46 .section}

在部署VPN网关前，确保您的环境满足以下条件：

-   本地设备和VPC的私网IP地址段不能相同，否则无法通信。
-   客户端必须能访问Internet。

## 步骤一 创建VPN网关 {#section_sys_znq_hia .section}

完成以下操作，创建用户网关。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。
2.  在左侧导航栏，单击**VPN** \> **VPN网关** 。
3.  在VPN网关页面，单击**创建VPN网关**。
4.  在购买页面，根据以下信息配置VPN网关，然后单击**立即购买**完成支付。
    -   **实例名称**：输入VPN网关的实例名称。
    -   **地域**：选择VPN网关的地域。

        **说明：** 确保VPC的地域和VPN网关的地域相同。

    -   **VPC**： 选择要连接的VPC。
    -   **带宽规格**：选择一个带宽规格。带宽规格是VPN网关所具备的公网带宽。
    -   **IPsec-VPN**： 选择是否开启IPsec-VPN功能，IPsec-VPN功能可以将本地数据中心与VPC或不同的VPC之间进行连接。
    -   **SSL-VPN**： 选择开启SSL-VPN功能。SSL-VPN功能允许您从任何位置的单台计算机连接到VPC。
    -   **SSL连接数**： 选择您需要同时连接的客户端最大规格。

        **说明：** 本选项只有在选择开启了SSL-VPN功能后才可配置。

    -   **计费周期**：选择购买时长。
5.  返回VPN网关页面，查看创建的VPN网关。

    刚创建好的VPN网关的状态是准备中，约两分钟左右会变成正常状态。正常状态就表明VPN网关完成了初始化，可以正常使用了。

    **说明：** VPN网关的创建一般需要1-5分钟。


## 步骤二 创建SSL服务端 {#section_26c_rya_uu2 .section}

完成以下操作，创建SSL服务端。

1.  在左侧导航栏，单击**VPN** \> **SSL服务端**。
2.  选择SSL服务端的地域。
3.  在SSL服务端页面，单击**创建SSL服务端**。
4.  在创建SSL服务端页面，根据以下信息配置SSL服务端，然后单击**确定**。
    -   **名称**：输入SSL服务端的名称。
    -   **VPN网关**：选择已创建的VPN网关。
    -   **本端网段**：以CIDR地址块的形式输入要连接的网络。单击**添加本端网段**添加多个本端网段，本端网段可以是任何VPC或交换机的网段，也可以是本地网络的网段。
    -   **客户端网段**：以CIDR地址块的形式输入客户端连接服务端时使用的网段。
    -   **高级配置**：使用默认高级配置。

## 步骤三 创建并下载SSL客户端证书 {#section_fxv_d8h_jui .section}

1.  在左侧导航栏，单击**VPN** \> **SSL客户端**。
2.  选择SSL客户端的地域。
3.  在SSL客户端页面，单击**创建SSL客户端证书**。
4.  在创建客户端证书页面，输入客户端证书名称并选择对应的SSL服务端，然后单击**确定**。
5.  在SSL客户端页面，找到已创建的客户端证书，然后单击**操作**列下的**下载**。

## 步骤四 客户端配置 {#section_zny_zwz_wdb .section}

完成以下操作，配置Mac客户端。

1.  执行以下命令安装OpenVPN客户端。

    ``` {#codeblock_qkn_kto_qhx}
    brew install openvpn
    ```

    **说明：** 如果尚未安装homebrew，先安装homebrew。

2.  将步骤三中下载的证书解压拷贝到配置目录并建立连接：
    1.  备份默认配置文件。
    2.  执行以下命令删除默认配置文件：

        ``` {#codeblock_sh8_nuk_16d}
        rm /usr/local/etc/openvpn/*
        ```

    3.  执行以下命令将文件拷贝到配置目录：

        ``` {#codeblock_62o_4n4_62j}
        cp cert_location /usr/local/etc/openvpn/
        ```

        `cert_location`是步骤三中下载的证书路径，比如：/Users/example/Downloads/certs6.zip。

    4.  执行以下命令解压证书文件：

        ``` {#codeblock_p1d_5r8_cyx}
        cd  /usr/local/certificates 
        unzip /usr/local/etc/openvpn/certs6.zip
        ```

    5.  执行以下命令发起连接：

        ``` {#codeblock_aid_8qz_538}
        sudo /usr/local/opt/openvpn/sbin/openvpn --config /usr/local/etc/openvpn/config.ovpn
        ```


## 步骤五 连接测试 {#section_m1a_qx3_345 .section}

在客户端ping已连接的VPC内的一台ECS实例，测试连通性。

**说明：** 确保测试的ECS实例的安全组规则允许客户端远程连接。详细信息，请参见[安全组应用案例](../../../../cn.zh-CN/安全/安全组/安全组应用案例.md#)。

