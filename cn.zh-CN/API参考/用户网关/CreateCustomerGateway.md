# CreateCustomerGateway {#doc_api_951821 .reference}

调用CreateCustomerGateway接口创建用户网关。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateCustomerGateway)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateCustomerGateway|要执行的操作。

 取值：**CreateCustomerGateway**。

 |
|IpAddress|String|是|116.62.222.xxx|用户网关的IP地址。

 |
|RegionId|String|是|cn-shanghai|用户网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过 64 个 ASCII 字符。 

 |
|Description|String|否|用户网关|用户网关的描述信息。 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://` 或`https://`开头。

 |
|Name|String|否|Gateway|用户网关的名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://` 或`https://`开头。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CustomerGatewayId|String|cgw-bp1aw0a5nfff03xp1pcqc|用户网关的ID。

 |
|IpAddress|String|100.1.1.2|用户网关的IP地址。

 |
|Name|String|test|用户网关的名称。

 |
|Description|String|test|用户网关的描述信息。

 |
|CreateTime|Long|1493363486000|用户网关的创建时间。

 |
|RequestId|String|cgw-bp1aw0a5nfff03xp1pcqc|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateCustomerGateway
&IpAddress=116.62.222.xxx
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateCustomerGatewayResponse>
  <CustomerGatewayId>cgw-bp1aw0a5nfff03xp1pcqc</CustomerGatewayId>
  <RequestId>185E81B1-3916-4667-B48F-C52409B33F2B</RequestId>
  <CreateTime>1493363486000</CreateTime>
  <IpAddress>100.1.1.2</IpAddress>
</CreateCustomerGatewayResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CustomerGatewayId":"cgw-bp1jrawp82av6bws9h2ut",
	"RequestId":"D32B3C26-6C6C-4988-93E9-D2A6444CE6AE",
	"CreateTime":1493363599000,
	"IpAddress":"100.1.1.2"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|400|InvalidIpAddress.AlreadyExist|Specified IpAddress is already exist.|该IP已经存在，原因是同一个用户在同一个region内，IP不可重复。|
|400|InvalidIpAddress.WrongFormat|Specified IpAddress is invalid.|该IP不合法。|
|400|InvalidName|The name is not valid|该名称格式不合法。|
|400|InvalidDescription|The description is not valid|描述格式不合法。|
|400|Resource.QuotaFull|The quota of resource is full|资源配额已达上限。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

