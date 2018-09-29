# Use IPsec-VPN in the classic network {#task_wq5_y1g_xdb .task}

In the VPC network, you can create a site-to-site connection directly by using the IPsec-VPN function of VPN Gateway. However, to use VPN Gateway in the classic network, you must first configure the ClassicLink.

Before you begin, plan your network:

-   The IP address range of the local client or office must belong to the IP address range of the VPC, but cannot conflict with the IP address ranges of VSwitches in the VPC.

-   Plan the VPC for which a VPN gateway is created. If the ECS instances in the classic network do not need to communicate with ECS instances in the existing VPC, we recommend creating a new VPC.

-   You have created a VPC. The VPC must use the following IP address range or its subnet, and meet the corresponding requirements:

|VPC CIDR Block|Limitations|
|:-------------|:----------|
|172.16.0.0/12|There is no route entry destined for 10.0.0.0/8 in this VPC.|
|192.168.0.0/16| -   There is no route entry destined for 10.0.0.0/8 in this VPC.

-   A route, of which the destination CIDR block is 192.168.0.0/16 and the next hop is the private NIC, is added to the ECS instance of the classic network. You can use the provided script to add the route. Click [Here](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/58095/cn_zh/1502878832385/route192.zip) to download the route script.

**Note:** Before running the script, read the readme file in the script carefully.

 |


If you want to use VPN Gateway in the classic network, purchase a VPN Gateway for the VPC, and configure the IPsec-VPN function. After the configuration, the local data center or office site can access the VPC. Then, connect the VPC and the ECS instances in the classic network using the ClassicLink function. Once the private connection is established, the local office site can access the ECS instances in the classic network.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13372/15382112493604_en-US.png)

1.   Create an IPsec-VPN connection. For more information, see [Configure a site-to-site connection](../../../../reseller.en-US/IPsec-VPN Quick Start/Configure a site-to-site connection.md#).
2.   Create an SSL-VPN connection. For more information, see [Linux client remote access](../../../../reseller.en-US/SSL-VPN Quick Start/Linux client remote access.md#).
3.   Create a ClassicLink connection. For more information, see [Build a ClassicLink connection](../../../../reseller.en-US/User Guide/ClassicLink/Build a ClassicLink connection.md#).

