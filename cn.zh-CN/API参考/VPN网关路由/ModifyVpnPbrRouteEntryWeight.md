# ModifyVpnPbrRouteEntryWeight {#doc_api_Vpc_ModifyVpnPbrRouteEntryWeight .reference}

调用ModifyVpnPbrRouteEntryWeight接口修改VPN策略路由的权重值。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyVpnPbrRouteEntryWeight&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyVpnPbrRouteEntryWeight|要执行的操作，取值：**ModifyVpnPbrRouteEntryWeight**。

 |
|NewWeight|Integer|是|100|要设置的权重值，取值：**0**|**100**。

 |
|NextHop|String|是|vco-bp15oes1py4i66rmd\*\*\*\*|策略路由的下一跳。

 |
|RegionId|String|是|cn-hangzhou|VPN策略路由所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouteDest|String|是|10.0.0.0/24|策略路由的目标网段。

 |
|RouteSource|String|是|192.168.1.0/24|策略路由的源网段。

 |
|VpnGatewayId|String|是|vpn-bp1a3kqjiiq9legfx\*\*\*\*|VPN网关的ID。

 |
|Weight|Integer|是|0|VPN策略路由在修改之前设置的权重值，取值：**0**|**100**。

 |
|ClientToken|String|否|d7d24a21-f4ba-4454-9173-b3828dae492b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。

 |
|OverlayMode|String|否|Ipsec|覆盖模式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|5BE01CD7-5A50-472D-AC14-CA181C5C03BE|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ModifyVpnPbrRouteEntryWeight
&NewWeight=100
&NextHop=vco-bp15oes1py4i66rmd****	
&RegionId=cn-hangzhou
&RouteDest=10.0.0.0/24
&RouteSource=192.168.1.0/24
&VpnGatewayId=vpn-bp1a3kqjiiq9legfx****
&Weight=100
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyVpnPbrRouteEntryWeightResponse>
        <RequestId>5BE01CD7-5A50-472D-AC14-CA181C5C03BE</RequestId>
</ModifyVpnPbrRouteEntryWeightResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"E82612A9-CB90-4D7E-B394-1DB7F6509B29"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|400|Resource.QuotaFull|The quota of resource is full|资源配额已达上限。|
|404|InvalidVpnGatewayInstanceId.NotFound|The specified vpn gateway instance id does not exist.|指定的 VPN 网关不存在，请您检查 VPN 网关是否正确。|
|400|VpnGateway.Configuring|The specified service is configuring.|服务正在配置中，请您稍后再试。|
|400|VpnGateway.FinancialLocked|The specified service is financial locked.|该服务已欠费，请您先充值再操作。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

