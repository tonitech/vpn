# ModifyCustomerGatewayAttribute {#doc_api_Vpc_ModifyCustomerGatewayAttribute .reference}

调用ModifyCustomerGatewayAttribute接口修改用户网关的名称和描述信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Vpc&api=ModifyCustomerGatewayAttribute&type=RPC&version=2016-04-28)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyCustomerGatewayAttribute|要执行的操作。

 取值： **ModifyCustomerGatewayAttribute**。

 |
|CustomerGatewayId|String|是|vpn-bp1q8bgx4xnkm2ogj\*\*\*\*|用户网关的ID。

 |
|RegionId|String|是|cn-shanghai|用户网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|用于保证请求的幂等性。

 由客户端生成该参数值，要保证在不同请求间唯一，最大值不超过 64 个 ASCII 字符。 

 |
|Description|String|否|test|用户网关的描述信息。

 长度为 2-256个字符，必须以字母或中文开头，但不能以`http://` 或`https://`开头。

 |
|Name|String|否|test|用户网关的名称。

 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CustomerGatewayId|String|cgw-bp1pvpl9r9adju6l5\*\*\*\*|用户网关的ID。

 |
|Name|String|test|用户网关的名称。

 |
|Description|String|test|用户网关的描述信息。

 |
|IpAddress|String|139.196.32.xxx|用户网关的IP地址。

 |
|CreateTime|Long|1492747187000|用户网关的创建时间。

 |
|RequestId|String|E61293C8-AF07-4E87-A272-542680038F93|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=ModifyCustomerGatewayAttribute
&CustomerGatewayId=vpn-bp1q8bgx4xnkm2ogj****
&RegionId=cn-shanghai
&Name=test
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyCustomerGatewayAttributeResponse>
      <CustomerGatewayId>cgw-bp1pvpl9r9adju6l5****</CustomerGatewayId>
      <RequestId>E61293C8-AF07-4E87-A272-542680038F93</RequestId>
      <CreateTime>1492747187000</CreateTime>
      <IpAddress>139.196.32.xxx</IpAddress>
</ModifyCustomerGatewayAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CustomerGatewayId":"cgw-bp1pvpl9r9adju6l5****",
	"CreateTime":1492747187000,
	"RequestId":"8AA5CE21-2E6A-4530-BDF5-F055849476E6",
	"IpAddress":"139.196.32.xxx"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|404|InvalidCustomerGatewayInstanceId.NotFound|The specified customer gateway instance id does not exist.|指定的 Instance 不存在，请您检查 Instance 是否正确。|
|400|InvalidName|The name is not valid|该名称格式不合法。|
|400|InvalidDescription|The description is not valid|描述格式不合法。|

访问[错误中心](https://error-center.aliyun.com/status/product/Vpc)查看更多错误码。

