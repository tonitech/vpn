# DescribeVpnGateways {#doc_api_951814 .reference}

调用DescribeVpnGateways接口查询已创建的VPN网关。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpnGateways)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVpnGateways|要执行的操作。

 取值：**DescribeVpnGateways**。

 |
|RegionId|String|是|cn-hangzhou|VPN网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|BusinessStatus|String|否|Normal|VPN网关的付费状态。

 取值： **Normal | FinancialLocked**

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |
|Status|String|否|init|VPN网关的状态，取值：

 -   init
-   provisioning
-   active
-   updating
-   deleting

 |
|VpcId|String|否|vpc-bp1ub1yt9cvakoelj1y9c|VPN网关所属VPC的ID。

 |
|VpnGatewayId|String|否|vpn-bp1q8bgx4xnkm2ogj0fiu|VPN网关的ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VpnGateways| | |VPN网关的详细信息。

 |
|└VpnGatewayId|String|vpn-bp1q8bgx4xnkm2ogj0fiu|VPN网关的ID。

 |
|└VpcId|String|vpc-bp1ub1yt9cvakoelj1y9c|VPN网关所属VPC的ID。

 |
|└VSwitchId|String|vsw-bp1y9ovl1cu9ou4tvma0l|VPN网关所属交换机的ID。

 |
|└InternetIp|String|116.62.69.xxx|VPN网关的公网IP。

 |
|└CreateTime|Long|1515383700000|VPN网关的创建时间。

 |
|└EndTime|Long|1518105600000|VPN网关的到期时间。

 |
|└Spec|String|5M|VPN网关的带宽峰值。

 |
|└Name|String|test|VPN网关的名称。

 |
|└Description|String|test|VPN网关的描述。

 |
|└Status|String|active|VPN网关的状态。

 |
|└BusinessStatus|String|Normal|VPN网关的状态。

 |
|└ChargeType|String|Prepay|计费类型。

 |
|└IpsecVpn|String|enable|是否开启了IPSec-VPN功能。

 |
|└SslMaxConnections|Long|5|允许连接的最大SSL-VPN客户端。

 |
|└SslVpn|String|enable|是否开启了SSL-VPN功能。

 |
|TotalCount|Integer|1|列表条条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|当前分页包含的条目数。

 |
|RequestId|String|DF11D6F6-E35A-41C3-9B20-6FC8A901FE65|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeVpnGateways
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVpnGatewaysResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <VpnGateways>
    <VpnGateway>
      <Status>active</Status>
      <VpnGatewayId>vpn-bp1q8bgx4xnkm2ogj0fiu</VpnGatewayId>
      <BusinessStatus>Normal</BusinessStatus>
      <Spec>5M</Spec>
      <CreateTime>1492753580000</CreateTime>
      <InternetIp>116.62.69.xxx</InternetIp>
      <EndTime>1495382400000</EndTime>
      <VSwitchId>vsw-bp1y9ovl1cu9ou4tvma0l</VSwitchId>
      <VpcId>vpc-bp1ub1yt9cvakoelj1y9c</VpcId>
    </VpnGateway>
  </VpnGateways>
  <RequestId>DF11D6F6-E35A-41C3-9B20-6FC8A901FE65</RequestId>
</DescribeVpnGatewaysResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":10,
	"VpnGateways":{
		"VpnGateway":[
			{
				"Status":"active",
				"VpnGatewayId":"vpn-bp1q8bgx4xnkm2ogj0fiu",
				"Spec":"5M",
				"BusinessStatus":"Normal",
				"CreateTime":1492753580000,
				"InternetIp":"116.62.69.xxx",
				"EndTime":1495382400000,
				"VSwitchId":"vsw-bp1y9ovl1cu9ou4tvma0l",
				"VpcId":"vpc-bp1ub1yt9cvakoelj1y9c"
			}
		]
	},
	"RequestId":"B2CD1315-CA2B-47B1-9DA5-8F1D69C48E82"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

