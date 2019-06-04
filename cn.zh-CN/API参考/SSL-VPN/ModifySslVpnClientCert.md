# ModifySslVpnClientCert {#doc_api_951838 .reference}

调用ModifySslVpnClientCert接口修改SSL-VPN客户端证书的名称。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=ModifySslVpnClientCert)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifySslVpnClientCert|要执行的操作。

 取值：**ModifySslVpnClientCert**。

 |
|RegionId|String|是|cn-hangzhou|SSL-VPN客户端证书所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|SslVpnClientCertId|String|是|vsc-bp1n8wcf134yl0osrcg98|SSL-VPN客户端证书的ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Name|String|否|cert2|SSL-VPN客户端证书的名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://` 或`https://`开头。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Name|String|cert2|客户端证书的名称。

 |
|RequestId|String|606998F0-B94D-48FE-8316-ACA81BB230DA|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifySslVpnClientCert
&RegionId=cn-hangzhou
&SslVpnClientCertId=vsc-bp1n8wcf134yl0osrcg98
&Name=cert2
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifySslVpnClientCertResponse>
  <SslVpnClientCertId>vsc-bp1n8wcf134yl0osrcg98</SslVpnClientCertId>
  <Name>cert2</Name>
  <RequestId>606998F0-B94D-48FE-8316-ACA81BB230DA</RequestId>
</ModifySslVpnClientCertResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Name":"cert2",
	"RequestId":"606998F0-B94D-48FE-8316-ACA81BB230DA",
	"SslVpnClientCertId":"vsc-bp1n8wcf134yl0osrcg98"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|400|InvalidName|The name is not valid|该名称格式不合法。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

