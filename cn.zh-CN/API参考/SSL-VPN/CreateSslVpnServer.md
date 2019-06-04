# CreateSslVpnServer {#doc_api_951835 .reference}

调用CreateSslVpnServer接口创建SSL-VPN服务端。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateSslVpnServer)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateSslVpnServer|要执行的操作。

 取值： **CreateSslVpnServer**。

 |
|ClientIpPool|String|是|192.168.1.0/24|是给客户端虚拟网卡分配访问地址的的地址段，不是指客户端已有的内网网段。

 当客户端通过SSL-VPN连接访问本端时，VPN网关会从指定的客户端网段中分配一个IP地址给客户端使用。

 该网段不能与**LocalSubnet**地址段冲突。

 |
|LocalSubnet|String|是|10.0.0.0/8|是客户端通过SSL-VPN连接要访问的地址段。

 本端网段可以是VPC的网段、交换机的网段、通过专线和VPC互连的IDC的网段、云服务如RDS/OSS等的网段。

 |
|RegionId|String|是|cn-hangzhou|VPN网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpnGatewayId|String|是|vpn-bp1hgim8by0kc9nga5lg3|VPN网关的ID。

 |
|Cipher|String|否|AES-128-CBC|SSL-VPN使用的加密算法。取值：

 **AES-128-CBC（默认值） |AES-192-CBC | AES-256-CBC | none**

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|Compress|Boolean|否|false|是否压缩。

 |
|Name|String|否|sslvpnname|SSL-VPN服务端的名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。

 但不能以`http://` 或`https://`开头。

 |
|Port|Integer|否|1194|SSL-VPN服务端所使用的端口，默认值为1194。 不能用使用以下端口:

 22, 2222, 22222, 9000, 9001, 9002, 7505, 80, 443, 53, 68, 123, 4510, 4560, 500, 4500

 |
|Proto|String|否|UDP|SSL-VPN服务端所使用的协议。

 取值：**UDP（默认值） | TCP**

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Name|String|test|SSL-VPN服务端的名称。

 |
|RequestId|String|E98A9651-7098-40C7-8F85-C818D1EBBA85|请求ID。

 |
|SslVpnServerId|String|vss-bp18q7hzj6largv4vk2fe|SSL-VPN服务端的ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateSslVpnServer
&ClientIpPool=192.168.1.0/24
&LocalSubnet=10.0.0.0/8
&RegionId=cn-hangzhou
&VpnGatewayId=vpn-xxxxxxxxxxx
&Action=CreateSslVpnServer
&Cipher=AES-128-CBC
&ClientToken=aaa
&Compress=false
&Name=aaa
&OwnerAccount=
&OwnerId=
&Port=
&Proto=
&ResourceOwnerAccount=
&ResourceOwnerId=
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateSslVpnServerResponse>
  <RequestId>E98A9651-7098-40C7-8F85-C818D1EBBA85</RequestId>
  <SslVpnServerId>vss-bp18q7hzj6largv4vk2fe</SslVpnServerId>
  <Name>test</Name>
</CreateSslVpnServerResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Name":"test",
	"RequestId":"E98A9651-7098-40C7-8F85-C818D1EBBA85",
	"SslVpnServerId":"vss-bp18q7hzj6largv4vk2fe"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|400|Resource.QuotaFull|The quota of resource is full|资源配额已达上限。|
|400|InvalidName|The name is not valid|该名称格式不合法。|
|404|InvalidVpnGatewayInstanceId.NotFound|The specified vpn gateway instance id does not exist.|指定的 VPN 网关不存在，请您检查 VPN 网关是否正确。|
|400|VpnGateway.Configuring|The specified service is configuring.|服务正在配置中，请您稍后再试。|
|400|VpnGateway.FinancialLocked|The specified service is financial locked.|该服务已欠费，请您先充值再操作。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

