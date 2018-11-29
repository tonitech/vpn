# Configure strongSwan {#concept_vyy_15f_xdb .concept}

When using IPsec-VPN to create a site-to-site connection, you must configure the local gateway according to the IPsec connection configured for the Alibaba Cloud VPN gateway. This article takes strongswan as an example to show you how to load a VPN configuration in a local site.

This document takes strongSwan as an example to show how to configure the VPN settings. The configurations used in this tutorial are as follows:

-   The IP address range of the Alibaba Cloud VPC is 192.168.10.0/24.

-   The IP address range of the local data center is 172.16.2.0/24.

-   The public IP of strongSwan is 59.110.165.70.


![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13369/15434982953583_en-US.png)

## Prerequisites {#section_tpp_k5f_xdb .section}

-   Make sure you have configured IPsec connections. For more information, see [Configure a site-to-site connection](../../../../reseller.en-US/IPsec-VPN Quick Start/Configure a site-to-site connection.md#).

-   After you create an IPsec connection, download the configurations of the created IPsec connection. For more information, see [Manage an IPsec connection](../../../../reseller.en-US/User Guide/Manage an IPsec connection.md#).


## Install strongSwan {#section_qzg_m5f_xdb .section}

1.  Run the following command to install strongSwan.

    ```
    # yum install strongSwan
    ```

2.  Run the following to view the installed software version.

    ```
    # strongswan version
    ```


## Configure strongSwan {#section_gnc_4vf_xdb .section}

1.  Run the following command to open the ipsec.conf file.

    ```
    # vi /etc/strongswan/ipsec.conf
    ```

2.  Refer to the following configurations to update the ipsec.conf file.

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
         leftid=59.110.165.70 (Public IP of the loca gateway)
         right=119.23.227.125
         rightsubnet=192.168.10.0/24
         rightid=119.23.227.125 (Public IP of the VPN Gateway)
         auto=route
         ike=aes-sha1-modp1024
         ikelifetime=86400s
         esp=aes-sha1-modp1024
         lifetime=86400s
         type=tunnel
    ```

3.  Configure the ipsec.secrets file.
    1.  Run the following command to open the configuration file.

        ```
        # vi /etc/strongswan/ipsec.secrets
        ```

    2.  Add the following configuration.

        ```
        59.110.165.70 119.23.227.125 : PSK yourpassword
        ```

4.  Enable system forwarding.

    ```
    # echo 1 > /proc/sys/net/ipv4/ip_forward
    ```

    For more configuration examples for different scenarios, see [Configuration examples for different scenarios](https://strongswan.org/documentation.html).

5.  Run the following command to start the strongSwan service.

    ```
    # systemctl enable strongswan
    # systemctl start strongswan
    ```

6.  Configure two routings in strongSwan. One is used to route the requests destined for the IDC client to strongSwan. The other one is used to route the requests destined for strongSwan to your IDC client.

