# DeleteVpnConnection {#doc_api_951830 .reference}

调用DeleteVpnConnection接口删除指定的IPsec连接。

**说明：** 删除IPSec连接后，VPC与本地IDC之间的连接将中断。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DeleteVpnConnection)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteVpnConnection|要执行的操作。

 取值： **DeleteVpnConnection**。

 |
|RegionId|String|是|cn-hangzhou|IPsec连接所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpnConnectionId|String|是|vco-bp1bbi27hojx80nck9k1i|IPsec连接的ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过 64 个 ASCII 字符。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|606998F0-B94D-48FE-8316-ACA81BB230DA|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DeleteVpnConnection
&RegionId=cn-hangzhou
&VpnConnectionId=vco-bp1bbi27hojx80nck9k1i
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteVpnConnectionResponse>
  <RequestId>606998F0-B94D-48FE-8316-ACA81BB230DA</RequestId>
</DeleteVpnConnectionResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"606998F0-B94D-48FE-8316-ACA81BB230DA"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|404|InvalidVpnConnectionInstanceId.NotFound|The specified vpn connection instance id does not exist.|指定的 VPN 连接不存在，请您检查该 VPN 链接是否正确。|
|400|VpnGateway.Configuring|The specified service is configuring.|服务正在配置中，请您稍后再试。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

