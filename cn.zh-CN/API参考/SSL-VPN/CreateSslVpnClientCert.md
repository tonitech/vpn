# CreateSslVpnClientCert {#doc_api_1088216 .reference}

调用CreateSslVpnClientCert接口创建SSL-VPN客户端证书。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateSslVpnClientCert)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateSslVpnClientCert|要执行的操作。

 取值： **CreateSslVpnClientCert**。

 |
|RegionId|String|是|cn-hangzhou|VPN网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|SslVpnServerId|String|是|vss-m5et0q3iy1qex328wcujx|SSL-VPN服务端的ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Name|String|否|SslVpnClientCert1|客户端证书的名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Name|String|SslVpnClientCert|客户端证书的名称。

 |
|RequestId|String|079874CD-AEC1-43E6-AC03-ADD96B6E4907|请求ID。

 |
|SslVpnClientCertId|String|vsc-m5euof6s5jy8vs5kdz2r2|客户端证书的ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateSslVpnClientCert
&RegionId=cn-hangzhou
&SslVpnServerId=vss-m5et0q3iy1qex328wcujx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateSslVpnClientCertResponse>
  <SslVpnClientCertId>vsc-bp1n8wcf134yl0osrcg98</SslVpnClientCertId>
  <RequestId>606998F0-B94D-48FE-8316-ACA81BB230DA</RequestId>
</CreateSslVpnClientCertResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"606998F0-B94D-48FE-8316-ACA81BB230DA",
	"SslVpnClientCertId":"vsc-bp1n8wcf134yl0osrcg98"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|400|Resource.QuotaFull|The quota of resource is full|资源配额已达上限。|
|400|VpnGateway.Configuring|The specified service is configuring.|服务正在配置中，请您稍后再试。|
|400|VpnGateway.FinancialLocked|The specified service is financial locked.|该服务已欠费，请您先充值再操作。|
|400|InvalidName|The name is not valid|该名称格式不合法。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

