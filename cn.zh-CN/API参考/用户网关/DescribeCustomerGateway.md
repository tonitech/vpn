# DescribeCustomerGateway {#doc_api_951823 .reference}

调用DescribeCustomerGateway接口查询已创建的用户网关的详细信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeCustomerGateway)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCustomerGateway|要执行的操作。

 取值： **DescribeCustomerGateway**。

 |
|CustomerGatewayId|String|是|vpn-bp1q8bgx4xnkm2ogj0fiu|用户网关的ID。

 |
|RegionId|String|是|cn-shanghai|用户网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CustomerGatewayId|String|cgw-bp1pvpl9r9adju6l5nxck|用户网关的ID。

 |
|Name|String|test|用户网关的名称。

 |
|Description|String|test|用户网关的描述信息。

 |
|IpAddress|String|139.196.32.xxx|用户网关的IP地址。

 |
|RequestId|String|99506ECB-218F-45A5-AE8E-79518451F615|请求ID。

 |
|CreateTime|Long|1492747187000|用户网关的创建时间。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeCustomerGateway
&CustomerGatewayId=vpn-bp1q8bgx4xnkm2ogj0fiu
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCustomerGatewayResponse>
  <Name>test</Name>
  <CustomerGatewayId>cgw-bp1pvpl9r9adju6l5nxck</CustomerGatewayId>
  <CreateTime>1492747187000</CreateTime>
  <RequestId>99506ECB-218F-45A5-AE8E-79518451F615</RequestId>
  <IpAddress>139.196.32.xxx</IpAddress>
</DescribeCustomerGatewayResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"Name":"test",
	"CustomerGatewayId":"cgw-bp1pvpl9r9adju6l5nxck",
	"CreateTime":1492747187000,
	"RequestId":"A0457BC9-6C0F-4437-AB9D-FB2EABC1D6A2",
	"IpAddress":"139.196.32.xxx"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|404|InvalidCustomerGatewayInstanceId.NotFound|The specified customer gateway instance id does not exist.|指定的 Instance 不存在，请您检查 Instance 是否正确。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

