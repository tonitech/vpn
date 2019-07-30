# Mac客户端 {#concept_qrk_klg_xdb .concept}

本文将介绍如何使用VPN网关的SSL-VPN功能从Mac客户端远程访问部署在经典网络中的云资源。

如果您已经配置了SSL-VPN，您仅需要根据文档中步骤五的步骤将经典网络中的ECS实例连接到VPC即可实现通过SSL-VPN远程接入经典网络的需求。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13374/3605_zh-CN.png)

## 前提条件 {#section_oth_2mg_xdb .section}

在开始之前，确保您的环境满足以下条件：

-   客户端能访问Internet。

-   使用SSL-VPN功能，需要切换至新控制台，详情参见[新控制台切换](https://help.aliyun.com/document_detail/66173.html?spm=a2c4g.11186623.2.3.KK5rNc)。

-   建议您创建一个新的VPC，并将VPC的网段设置为172.16.0.0/12。如果您选择用已有的VPC，VPC必须满足下表中的约束条件：

|VPC网段|限制|
|:----|:-|
|172.16.0.0/12|该VPC中不存在目标网段为10.0.0.0/8的自定义路由条目。您可以在VPC控制台的路由表详情页面查看已添加的路由条目。

|
|192.168.0.0/16| -   该VPC中不存在目标网段为10.0.0.0/8的自定义路由条目。

-   需要在经典网络ECS实例中增加192.168.0.0/16指向私网网卡的路由。您可以使用提供的脚本添加路由，单击[此处](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/58095/cn_zh/1502878832385/route192.zip)下载路由脚本。

**说明：** 在运行脚本前，请仔细阅读脚本中包含的readme文件。

 |


## 步骤一 创建VPN网关 {#section_sj5_kmg_xdb .section}

如果您是经典网络，在VPC内购买的VPN网关配合ClassicLink功能也可以在经典网络中使用。

完成以下操作，创建VPN网关：

1.  登录新版[VPC管理控制台](https://vpcnext.console.aliyun.com)。
2.  在左侧导航栏，单击**VPN** \> **VPN网关** 。
3.  在VPN网关页面，单击**创建VPN网关**。
4.  在购买页面，配置VPN网关，完成支付。本操作中VPN网关的配置如下：
    -   **地域**：选择VPN网关的地域。本操作中选择**华东1（杭州）**。

**说明：** 确保VPC的地域和VPN网关的地域相同。

    -   **专有网络**： 选择要连接的VPC。

    -   **带宽规格**：选择一个带宽规格。带宽规格是VPN网关所具备的公网带宽。

    -   **IPsec-VPN**： 选择是否开启IPsec-VPN功能，IPsec-VPN功能适用于站点到站点的连接，可以根据您的实际需要选择开启。

    -   **SSL-VPN**： 选择是否开启SSL-VPN功能。本操作选择**开启**。

    -   **SSL并发连接数**： 选择您需要同时连接的客户端最大规格。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13374/3606_zh-CN.png)

5.  返回VPN网关页面，查看创建的VPN网关。

    刚创建好的VPN网关的状态是准备中，约两分钟左右会变成正常状态。正常状态就表明VPN网关完成了初始化，可以正常使用了。

    **说明：** VPN网关的创建一般需要1-5分钟。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13374/3607_zh-CN.png)


## 步骤二 创建SSL服务端 {#section_v4f_2mg_xdb .section}

完成以下操作，创建SSL服务端：

1.  在专有网络的左侧导航栏，单击**VPN** \> **SSL服务端**。
2.  单击**创建SSL服务端**。本操作中SSL服务端的配置如下：
    -   **名称**：输入SSL服务端的名称。

    -   **VPN网关**：选择步骤一中创建的VPN网关。

    -   **本端网段**：**以CIDR地址块的形式输入要连接的经典网络ECS实例的内网网段**。单击**添加本端网段**添加多个本端网段。

        在本例中，本端网段为10.1.0.0/16和10.2.0.0/16。

        **说明：** 如果新建ECS实例的IP地址不在已配置的本端网段内，需要添加对应的本端网段。

    -   **客户端网段**：**以CIDR地址块的形式输入客户端连接服务端时使用的IP地址。该客户端网段必须是VPN网关所在的VPC的网段的子集。**

        在本例中，客户端网段为172.16.10.0/24。

        **说明：** 客户端网段不是您本地的客户端现有的地址，而是用来分配给客户端通过SSL VPN访问的IP地址。

    -   **高级配置**：使用默认高级配置。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13374/3608_zh-CN.png)


## 步骤三 创建客户端证书 {#section_zw2_24g_xdb .section}

完成以下操作，创建客户端证书：

1.  在专有网络的左侧导航栏，单击**VPN** \> **SSL客户端** 。
2.  单击**创建SSL客户端证书**。
3.  在创建客户端证书对话框，输入客户端证书名称并选择对应的SSL服务端，然后单击**确定**。
4.  在SSL客户端页面，找到已创建的客户端证书，然后单击**下载**下载生成的客户端证书。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13374/3609_zh-CN.png)


## 步骤四 客户端配置 {#section_qdz_j4g_xdb .section}

完成以下操作，配置客户端：

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
        unzip /usr/local/etc/openvpn/certs6.zip
        ```

    4.  执行以下命令发起连接：

        ```
        sudo /usr/local/opt/openvpn/sbin/openvpn --config /usr/local/etc/openvpn/config.ovpn
        ```


## 步骤五 建立ClassicLink连接 {#section_sk4_n4g_xdb .section}

完成以下操作，建立ClassicLink连接：

1.  登录专有网络管理控制台。
2.  选择目标专有网络的地域，然后单击目标专有网络的ID链接。
3.  在专有网络详情页面，单击**开启ClassicLink**。
4.  在弹出的对话框，单击**确定**。
5.  登录ECS管理控制台。
6.  在左侧导航栏，单击**实例**。
7.  选择一个或多个目标经典网络的ECS实例，单击**更多** \> **连接专有网络** 。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13374/3610_zh-CN.png)

8.  在弹出的对话框中选择目标VPC，单击**确定**。
9.  在左侧导航栏，单击**网络和安全** \> **安全组** 。
10. 在安全组列表页面，单击**内网入方向**页签，然后单击**添加安全组规则**。按照如下配置添加安全组规则：
    -   **规则方向**：入方向

    -   **授权策略**：允许

    -   **协议类型**：全部

    -   **授权类型**：地址段访问

    -   **授权对象**：输入需要通过VPN网关访问本ECS实例的私网地址，如172.16.3.44/32。

        在Mac终端执行ifconfig命令，在返回的网络配置信息中找到类似`inet 172.16.10.6 --> 172.16.10.5 netmask 0xffffffff`的信息，其中`172.16.10.6`就是客户端IP（安全组中配置的授权对象）。

        **说明：** 如果无法通过VPN网关访问ECS实例，可能是客户端IP发生了变化，您需要重新添加安全组规则。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13375/3614_zh-CN.png)

11. 返回ECS管理控制台，单击右侧的配置图标，在弹出的对话框中选中**连接状态**，然后单击**确定**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13374/3611_zh-CN.png)

12. 查看ECS实例的连接状态。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13374/3612_zh-CN.png)

    配置完成后，您就可以从Linux客户端访问已连接的经典网络ECS实例中部署的应用了。


