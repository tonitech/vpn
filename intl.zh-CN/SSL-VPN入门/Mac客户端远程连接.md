# Mac客户端远程连接 {#concept_a1t_jvz_wdb .concept}

本文以Mac客户端为例介绍如何通过VPN网关拨号接入VPC。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13356/15434968023332_zh-CN.png)

## 开始之前 {#section_wwc_lvz_wdb .section}

在部署VPN网关前，确保您的环境满足以下条件：

-   本地设备和VPC的私网IP地址段不能相同，否则无法通信。

-   客户端必须能访问Internet。


## 步骤一 创建VPN网关 {#section_gw4_1wz_wdb .section}

1.  登录VPC管理控制台。
2.  在左侧导航栏，单击**VPN** \> **VPN网关** 。
3.  在VPN网关页面，单击**创建VPN网关**。
4.  在购买页面，配置VPN网关，完成支付。本操作中VPN网关的配置如下：
    -   **地域**：选择VPN网关的地域。本操作中选择**华东1（杭州）**。

**说明：** 确保VPC的地域和VPN网关的地域相同。

    -   **专有网络**： 选择要连接的VPC。

    -   **带宽规格**：选择一个带宽规格。带宽规格是VPN网关所具备的公网带宽。

    -   **IPsec-VPN**： 选择是否开启IPsec-VPN功能，IPsec-VPN功能适用于站点到站点的连接，可以根据您的实际需要选择开启。

    -   **SSL-VPN**： 选择是否开启SSL-VPN功能。SSL-VPN功能允许您从任何位置的单台计算机连接到专有网络。本操作选择**开启**。

    -   **SSL并发连接数**： 选择您需要同时连接的客户端最大规格。

**说明：** 本选项只有在选择开启了SSL-VPN功能后才可配置。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13354/15434968023325_zh-CN.png)

5.  返回VPN网关页面，选择华东1地域，查看创建的VPN网关。

    刚创建好的VPN网关的状态是准备中，约两分钟左右会变成正常状态。正常状态就表明VPN网关完成了初始化，可以正常使用了。

    **说明：** VPN网关的创建一般需要1-5分钟。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13354/15434968023326_zh-CN.png)


## 步骤二 创建SSL服务端 {#section_txk_4wz_wdb .section}

1.  在专有网络的左侧导航栏，单击**VPN** \> **SSL服务端**。
2.  单击**创建SSL服务端**。本操作中SSL服务端的配置如下：
    -   **名称**：输入SSL服务端的名称。

    -   **VPN网关**：选择步骤一中创建的VPN网关。

    -   **本端网段**：以CIDR地址块的形式输入要连接的网络。单击**添加本端网段**添加多个本端网段，本端网段可以是任何VPC或交换机的网段，也可以是本地网络的网段。

    -   客户端网段：以CIDR地址块的形式输入客户端连接服务端时使用的IP地址。

    -   高级配置：使用默认高级配置。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13354/15434968023327_zh-CN.png)


## 步骤三 创建客户端证书 {#section_ddh_5wz_wdb .section}

1.  在专有网络的左侧导航栏，单击**VPN** \> **SSL客户端**。
2.  单击**创建SSL客户端证书**。
3.  在创建客户端证书对话框，输入客户端证书名称并选择对应的SSL服务端，然后单击**确定**。

4.  在SSL客户端页面，找到已创建的客户端证书，然后单击**下载**下载生成的客户端证书。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13354/15434968023328_zh-CN.png)


## 步骤四 客户端配置 {#section_zny_zwz_wdb .section}

1.  执行以下命令安装OpenVPN客户端。

    ```
    brew install openvpn
    ```

    **说明：** 如果尚未安装homebrew，先安装homebrew。

2.  将步骤三中下载的证书解压拷贝到配置目录并建立连接：
    1.  备份默认配置文件，然后执行以下命令删除默认配置文件：

        ```
        rm /usr/local/etc/openvpn/*
        ```

    2.  执行以下命令将文件拷贝到配置目录：

        ```
        cp cert_location /usr/local/etc/openvpn/
        ```

        `cert_location`是步骤三中下载的证书路径，比如：/Users/example/Downloads/certs6.zip

    3.  执行以下命令解压证书文件：

        ```
        cd  /usr/local/certificates 
        unzip /usr/local/etc/openvpn/certs6.zip
        ```

    4.  执行以下命令发起连接：

        ```
        sudo /usr/local/opt/openvpn/sbin/openvpn --config /usr/local/etc/openvpn/config.ovpn
        ```


## 步骤五 连接测试 {#section_kxc_lvz_wdb .section}

在客户端ping已连接的VPC内的一台ECS实例，测试连通性。

**说明：** 确保测试的ECS实例的安全组规则允许客户端远程连接。详情参考[安全组规则的典型应用](../../../../intl.zh-CN/用户指南/安全组/安全组规则的典型应用.md#)。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13354/15434968023329_zh-CN.png)

