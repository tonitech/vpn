# DescribeCustomerGateways {#doc_api_951822 .reference}

调用DescribeCustomerGateways接口查询已创建的用户网关。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeCustomerGateways)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeCustomerGateways|要执行的操作。

 取值： **DescribeCustomerGateways**。

 |
|RegionId|String|是|cn-shanghai|用户网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|CustomerGatewayId|String|否|vpn-bp1q8bgx4xnkm2ogj0fiu|用户网关的ID。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CustomerGateways| | |用户网关的详细信息。

 |
|└CustomerGatewayId|String|cgw-bp1pvpl9r9adju6l5nxck|用户网关的ID。

 |
|└Name|String|test|用户网关的名称。

 |
|└Description|String|test|用户网关的描述信息。

 |
|└IpAddress|String|139.196.32.xxx|用户网关的IP地址。

 |
|└CreateTime|Long|1492747187000|用户网关的创建时间。

 |
|TotalCount|Integer|1|列表条条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|5BE01CD7-5A50-472D-AC14-CA181C5C03BE|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeCustomerGateways
&RegionId=cn-shanghai
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeCustomerGatewaysResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>5BE01CD7-5A50-472D-AC14-CA181C5C03BE</RequestId>
  <CustomerGateways>
    <CustomerGateway>
      <Name>test</Name>
      <CustomerGatewayId>cgw-bp1pvpl9r9adju6l5nxck</CustomerGatewayId>
      <CreateTime>1492747187000</CreateTime>
      <IpAddress>139.196.32.xxx</IpAddress>
    </CustomerGateway>
  </CustomerGateways>
</DescribeCustomerGatewaysResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":10,
	"RequestId":"E82612A9-CB90-4D7E-B394-1DB7F6509B29",
	"CustomerGateways":{
		"CustomerGateway":[
			{
				"CustomerGatewayId":"cgw-bp1pvpl9r9adju6l5nxck",
				"Name":"test",
				"CreateTime":1492747187000,
				"IpAddress":"139.196.32.xxx"
			}
		]
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

