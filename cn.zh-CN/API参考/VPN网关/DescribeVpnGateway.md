# DescribeVpnGateway {#doc_api_951815 .reference}

调用DescribeVpnGateway接口查询指定VPN网关的详细信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpnGateway)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVpnGateway|要执行的操作。

 取值：**DescribeVpnGateways**。

 |
|RegionId|String|是|cn-shanghai|VPN网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpnGatewayId|String|是|vpn-bp1q8bgx4xnkm2ogj0fiu|VPN网关的ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VpnGatewayId|String|vpn-bp1q8bgx4xnkm2ogj0fiu|VPN网关的ID。

 |
|VpcId|String|vpc-23rsxdfxxxxxxxxxxxxxx|VPN网关所属VPC的ID。

 |
|VSwitchId|String|vsw-bp1y9ovl1cu9ou4tvma0l|VPN网关所属交换机的ID。

 |
|InternetIp|String|116.62.222.28|公网IP地址。

 |
|CreateTime|Long|1495382400000|VPN网关的创建时间。

 |
|EndTime|Long|1495382400000|VPN网关的到期时间。

 |
|Spec|String|5|VPN网关的规格。

 |
|Name|String|vpngatewayname|VPN网关的名称。

 |
|Description|String|vpngatewaydescription|VPN网关的描述信息。

 |
|Status|String|init|VPN网关的状态。

 |
|BusinessStatus|String|Normal|VPN网关的付费状态。

 |
|ChargeType|String|PayByTraffic|付费类型。

 |
|IpsecVpn|String|enable|是否开启了IPsec-VPN功能。

 |
|RequestId|String|DE77A7F3-3B74-41C0-A5BC-CAFD188C28B6|请求ID。

 |
|SslMaxConnections|Long|5|最大SSL-VPN并发连接用户数的规格。

 |
|SslVpn|String|enable|是否开启了SSL-VPN功能。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeVpnGateway
&RegionId=cn-shanghai
&VpnGatewayId=vpn-bp1q8bgx4xnkm2ogj0fiu
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVpnGatewayResponse>
  <Status>active</Status>
  <VpnGatewayId>vpn-bp1q8bgx4xnkm2ogj0fiu</VpnGatewayId>
  <Spec>5M</Spec>
  <BusinessStatus>Normal</BusinessStatus>
  <RequestId>98C99F30-A3D2-42E1-AC75-0C882FBE92F7</RequestId>
  <CreateTime>1492753580000</CreateTime>
  <InternetIp>116.62.69.64</InternetIp>
  <EndTime>1495382400000</EndTime>
  <VSwitchId>vsw-bp1y9ovl1cu9ou4tvma0l</VSwitchId>
  <VpcId>vpc-bp1ub1yt9cvakoelj1y9c</VpcId>
</DescribeVpnGatewayResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Status":"active",
	"VpnGatewayId":"vpn-bp1q8bgx4xnkm2ogj0fiu",
	"Spec":"5M",
	"BusinessStatus":"Normal",
	"RequestId":"E98A9651-7098-40C7-8F85-C818D1EBBA85",
	"CreateTime":1492753580000,
	"InternetIp":"116.62.69.64",
	"EndTime":1495382400000,
	"VSwitchId":"vsw-bp1y9ovl1cu9ou4tvma0l",
	"VpcId":"vpc-bp1ub1yt9cvakoelj1y9c"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|404|InvalidVpnGatewayInstanceId.NotFound|The specified vpn gateway instance id does not exist.|指定的 VPN 网关不存在，请您检查 VPN 网关是否正确。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

