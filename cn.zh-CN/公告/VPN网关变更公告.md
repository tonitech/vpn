# VPN网关变更公告 {#concept_w3s_24z_ghb .concept}

为了提供更灵活的流量路由方式，VPN网关由基于策略的IPsec-VPN变更为基于路由的IPsec-VPN。本次变更对SSL-VPN无影响。

## VPN网关变更详情 {#section_wvs_g4z_ghb .section}

基于路由的IPsec-VPN对当前VPN网关的产品形态有如下变化：

-   VPN网关详情页中存在两种路由表。

    -   策略路由：基于源IP和目的IP进行更精确的路由转发。
    -   目的路由：仅基于目的IP进行路由转发。
    **说明：** 目前，VPN网关详情页中仅支持配置策略路由和目的路由，后续会支持配置动态路由。

-   VPN网关的路由表支持自动或手动将路由条目同步到VPC路由表。

## 变更存量VPN网关 {#section_nts_34z_ghb .section}

存量VPN网关不支持基于路由的IPsec-VPN功能。如有需要，请提交工单。

您新建的VPN网关，默认支持基于路由的IPsec-VPN功能。您可以在VPN网关详情页中查看如下路由表：

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/150978/155529385542114_zh-CN.png)

