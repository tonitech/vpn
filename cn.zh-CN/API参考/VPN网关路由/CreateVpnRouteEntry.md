# CreateVpnRouteEntry {#doc_api_Vpc_CreateVpnRouteEntry .reference}

调用CreateVpnRouteEntry创建VPN目的路由。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=CreateVpnRouteEntry&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateVpnRouteEntry|要执行的操作，取值：**CreateVpnRouteEntry**。

 |
|NextHop|String|是|vco-bp15oes1py4i66rmd\*\*\*\*|目的路由的下一跳。

 |
|PublishVpc|Boolean|是|true|是否发布目的路由到VPC，取值：

 -   **true**：发布目的路由到VPC。
-   **false**：不发布目的路由到VPC。

 |
|RegionId|String|是|cn-hangzhou|VPN目的路由所在的地域。您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RouteDest|String|是|10.0.0.0/24|目的路由的目标网段。

 |
|VpnGatewayId|String|是|vpn-bp1a3kqjiiq9legfx\*\*\*\*|VPN网关的ID。

 |
|Weight|Integer|是|0|目的路由的权重值，取值：**0**|**100**。

 |
|ClientToken|String|否|d7d24a21-f4ba-4454-9173-b3828dae492b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过64个ASCII字符。

 |
|OverlayMode|String|否|Ipsec|覆盖模式。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CreateTime|Long|1492747187000|VPN目的路由的创建时间。

 |
|NextHop|String|vco-bp15oes1py4i66rmd\*\*\*\*|目的路由的下一跳。

 |
|OverlayMode|String|Ipsec|覆盖模式。

 |
|RequestId|String|5BE01CD7-5A50-472D-AC14-CA181C5C03BE|请求ID。

 |
|RouteDest|String|10.0.0.0/24|目的路由的目标网段。

 |
|State|String|published|VPN目的路由的状态。

 |
|VpnInstanceId|String|vpn-bp1cmw7jh1nfe43m9\*\*\*\*|VPN网关的ID。

 |
|Weight|Integer|0|目的路由的权重值，取值：**0**|**100**。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreateVpnRouteEntry
&NextHop=vco-bp15oes1py4i66rmd****	
&PublishVpc=true
&RegionId=cn-hangzhou
&RouteDest=10.0.0.0/24
&VpnGatewayId=vpn-bp1a3kqjiiq9legfx****
&Weight=0
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateVpnRouteEntryResponse>
	  <RouteDest>10.0.0.0/24</RouteDest>
	  <VpnInstanceId>vpn-bp1cmw7jh1nfe43m9****</VpnInstanceId>
	  <OverlayMode>Ipsec</OverlayMode>
	  <State>published</State>
	  <Weight>100</Weight>
	  <CreateTime>1563873294331</CreateTime>
	  <NextHop>vco-bp1tui07ob10fmuro****</NextHop>
      <RequestId>EE4C2417-9437-4333-BDEB-8493F7AA7258</RequestId>
</CreateVpnRouteEntryResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RouteDest":"10.0.0.0/24",
	"VpnInstanceId":"vpn-bp1cmw7jh1nfe43m9****",
	"OverlayMode":"Ipsec",
	"Weight":100,
	"State":"published",
	"RequestId":"CB2793A8-845F-444C-8E93-76F1BBDF9C78",
	"NextHop":"vco-bp1tui07ob10fmuro****",
	"CreateTime":1563873294331
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

