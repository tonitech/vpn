# VPN网关FAQ {#concept_dxq_m3h_xdb .concept}

## 1. VPN网关是否支持经典网络？ {#section_sdq_n3h_xdb .section}

不支持。VPN网关仅支持专有网络，如果您想在经典网络中使用VPN网关，需要在专有网络中开启ClassicLink功能，详情参见[在经典网络中使用IPsec-VPN](../cn.zh-CN/最佳实践/在经典网络中使用IPsec-VPN.md#)。

## 2. 本地站点通过IPsec-VPN接入VPC的前提条件是什么？ {#section_tdq_n3h_xdb .section}

需要一个静态公网IP和一个支持IKEv1和IKEv2协议的网关设备，详情参见[配置站点到站点连接](../cn.zh-CN/IPsec-VPN入门/配置站点到站点连接.md#)。

## 3. 跨地域VPC是否可以通过VPN网关互通？ {#section_udq_n3h_xdb .section}

可以，详情参见[配置VPC到VPC连接](../cn.zh-CN/IPsec-VPN入门/配置VPC到VPC连接.md#)。

## 4. 支持的本地网关设备型号？ {#section_vdq_n3h_xdb .section}

阿里云VPN网关支持标准的IKEv1和IKEv2协议。因此，只要支持这两种协议的设备都可以和云上VPN网关互连，比如华为、华三、山石、深信服、Cisco ASA、Juniper、SonicWall、Nokia、IBM 和 Ixia等。详情参见[本地网关配置](../cn.zh-CN/最佳实践/本地网关配置.md#)。

## 5. 是否支持SSL-VPN？ {#section_wdq_n3h_xdb .section}

支持，详情参见[SSL-VPN](https://help.aliyun.com/document_detail/65282.html)。

## 6. 每个VPN网关可以建立多少个IPsec连接？ {#section_xdq_n3h_xdb .section}

每个VPN网关最多可以支持10个IPsec连接且无例外。如需要更多数量的IPsec连接，请创建多个VPN网关。

## 7. 是否可以通过VPN网关访问Internet？ {#section_ydq_n3h_xdb .section}

不可以。VPN网关仅提供私网接入VPC功能，不提供Internet访问的功能。

## 8. VPC互通流量是否经过Internet？ {#section_zdq_n3h_xdb .section}

不经过。通过VPN实现跨地域VPC互访，流量经过阿里云骨干网，不经过Internet。

## 9. 是否支持在一个IPsec连接中配置多个对端网段？ {#section_a2q_n3h_xdb .section}

支持。每个网段之间用逗号分隔，且建议用IKEv2连接。

## 10. 是否可以降低VPN网关配置？ {#section_b2q_n3h_xdb .section}

可以，请提交工单。

## 11. SSL-VPN发布前购买的VPN网关实例是否可以使用SSL-VPN功能？ {#section_c2q_n3h_xdb .section}

SSL-VPN发布前购买的VPN网关实例无法直接开启SSL-VPN功能，需要提工单到“VPN产品组”申请。

相关文档

