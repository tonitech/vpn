# 在经典网络中使用IPsec-VPN {#task_wq5_y1g_xdb .task}

您可以直接在专有网络中使用VPN网关通过IPSec-VPN功能建立站点到站点的连接。如果要在经典网络中使用VPN网关，需要配置ClassicLink。

首先在开始前，需要做好网络规划：

-   本地客户端、办公点的私网网段必须属于VPC的私网网段，且不能和VPC内交换机的网段冲突，否则无法通信。

-   规划VPN网关所在的VPC，即云上VPN网关的网络环境，如果经典网络ECS不需要和已有VPC内的ECS通信，建议新建VPC用于经典网络的VPN连接。

-   您已经创建了一个VPC。VPC必须使用下表中的网段或其子集，满足对应的约束条件：

|VPC网段|限制|
|:----|:-|
|172.16.0.0/12|该VPC中不存在目标网段为10.0.0.0/8的自定义路由条目。|
|192.168.0.0/16| -   该VPC中不存在目标网段为10.0.0.0/8的自定义路由条目。

-   需要在经典网络ECS实例中增加192.168.0.0/16指向私网网卡的路由。您可以使用提供的脚本添加路由，单击[此处](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/attach/58095/cn_zh/1502878832385/route192.zip)下载路由脚本。

**说明：** 在运行脚本前，请仔细阅读脚本中包含的readme文件。

 |


如果想在经典网络中使用VPN网关，首先在VPC内购买VPN网关，配置IPsec-VPN后IDC或者办公点可以接入VPC。然后经典网络ECS通过ClassicLink功能连接到VPC，再通过VPC中转实现本地办公点访问经典网络ECS。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13372/15481770783604_zh-CN.png)

1.   建立线下站点到VPC的IPsec-VPN连接。 详情参见[配置站点到站点连接](../../../../../cn.zh-CN/IPsec-VPN入门/配置站点到站点连接.md#)。
2.   建立线下客户端到VPC的SSL-VPN连接。 详情参见[Linux客户端远程连接](../../../../../cn.zh-CN/SSL-VPN入门/Linux客户端远程连接.md#)。
3.   建立ClassicLink连接。 详情参见[建立ClassicLink连接](../../../../../cn.zh-CN/用户指南/ClassicLink/建立ClassicLink连接.md#)。

