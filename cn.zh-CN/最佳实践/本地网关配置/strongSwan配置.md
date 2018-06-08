# strongSwan配置 {#concept_vyy_15f_xdb .concept}

使用IPsec-VPN建立站点到站点的连接时，在配置完阿里云VPN网关后，您还需在本地站点的网关设备中进行VPN配置。本文以strongSwan为例介绍如何在本地站点中加载VPN配置。

本文以strongSwan为例介绍如何在本地站点中加载VPN配置。本操作中作为示例的配置信息如下：

-   阿里云VPC的网段是192.168.10.0/24

-   本地IDC的网段是172.16.2.0/24

-   strongSwan的公网IP地址是59.110.165.70


![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13369/3583_zh-CN.png)

## 前提条件 {#section_tpp_k5f_xdb .section}

-   确保您已经在阿里云VPC内创建了IPsec连接，详情参见[配置站点到站点连接](https://help.aliyun.com/document_detail/65072.html)。

-   创建IPsec连接后，获取的IPsec配置信息，详情参见[IPsec连接管理](https://help.aliyun.com/document_detail/65288.html)。


## 安装strongSwan {#section_qzg_m5f_xdb .section}

1.  运行以下命令安装strongSwan。

    ```
    # yum install strongswan
    ```

2.  运行以下命查看安装的软件版本。

    ```
    # strongswan version
    ```


## 配置strongSwan {#section_gnc_4vf_xdb .section}

1.  运行以下命令打开ipsec.conf配置文件。

    ```
    # vi /etc/strongswan/ipsec.conf
    ```

2.  参考以下配置，更改ipsec.conf的配置。

    ```
    # ipsec.conf - strongSwan IPsec configuration file
     # basic configuration
     config setup
         uniqueids=never
     conn %default
         authby=psk
         type=tunnel
     conn tomyidc
         keyexchange=ikev1
         left=59.110.165.70
         leftsubnet=172.16.2.0/24
         leftid=59.110.165.70（IDC网关设备的公网IP）
         right=119.23.227.125
         rightsubnet=192.168.10.0/24
         rightid=119.23.227.125（VPN网关的公网IP）
         auto=route
         ike=aes-sha1-modp1024
         ikelifetime=86400s
         esp=aes-sha1-modp1024
         lifetime=86400s
         type=tunnel
    ```

3.  配置ipsec.secrets文件。
    1.  运行以下命令打开配置文件。

        ```
        # vi /etc/strongswan/ipsec.secrets
        ```

    2.  添加如下配置。

        ```
        59.110.165.70 119.23.227.125 : PSK yourpassword
        ```

4.  打开系统转发配置。

    ```
    # echo 1 > /proc/sys/net/ipv4/ip_forward
    ```

    更多场景配置样例，参见[场景配置样例](https://strongswan.org/documentation.html)。

5.  执行以下命令启动strongSwan服务。

    ```
    # systemctl enable strongswan
    # systemctl start strongswan
    ```

6.  设置IDC客户端到strongSwan网关及网关下行到客户端路由。

