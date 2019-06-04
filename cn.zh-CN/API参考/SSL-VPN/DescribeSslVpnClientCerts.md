# DescribeSslVpnClientCerts {#doc_api_1088219 .reference}

调用DescribeSslVpnClientCerts接口查询已创建的SSL-VPN客户端证书。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeSslVpnClientCerts)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeSslVpnClientCerts|要执行的操作。

 取值： **DescribeSslVpnClientCerts**。

 |
|RegionId|String|是|cn-hangzhou|SSL-VPN客户端证书所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|Name|String|否|cert1|SSL-VPN客户端证书的名称。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |
|SslVpnClientCertId|String|否|vsc-bp1n8wcf134yl0osrcg98|SSL-VPN客户端证书ID。

 |
|SslVpnServerId|String|否|vss-bp18q7hzj6largv4vk2fe|SSL-VPN服务端ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|5BE01CD7-5A50-472D-AC14-CA181C5C03BE|请求ID。

 |
|SslVpnClientCertKeys| | |SSL-VPN客户端证书的详细信息。

 |
|└CreateTime|Long|1492747187000|客户端证书创建时间。

 |
|└EndTime|Long|1494966335000|客户端证书的到期时间。

 |
|└Name|String|cert1|客户端证书名称。

 |
|└RegionId|String|cn-hangzhou|SSL-VPN客户端证书的地域。

 |
|└SslVpnClientCertId|String|vsc-bp1n8wcf134yl0osrcg98|SSL-VPN客户端证书的ID。

 |
|└SslVpnServerId|String|vss-bp18q7hzj6largv4vk2fe|SSL-VPN服务端ID。

 |
|└Status|String|normal|客户端证书的状态：

 -   **expiring-soon**：证书将在1周后过期。
-   **normal**：正常。
-   **expired**：已过期。

 |
|TotalCount|Integer|1|列表条条目数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeSslVpnClientCerts
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeSslVpnServersResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <SslVpnServers>
    <SslVpnServer>
      <RegionId>cn-hanghzou</RegionId>
      <SslVpnServerId>vss-bp18q7hzj6largv4vk2fe</SslVpnServerId>
      <VpnGatewayId>vpn-bp1q8bgx4xnkm2ogj0fiu</VpnGatewayId>
      <Name>test</Name>
      <CLientIpPool>10.10.10.20/24</CLientIpPool>
      <LocalSubnet>10.10.10.10/24</LocalSubnet>
      <Proto>UDP</Proto>
      <Port>1194</Port>
      <Cipher>AES-128-CBC</Cipher>
      <Compress>true</Compress>
      <CreateTime>1492753580000</CreateTime>
      <Connections>0</Connections>
      <MaxConnections>5</MaxConnections>
      <InternetIp>47.98.xx.xx</InternetIp>
    </SslVpnServer>
  </SslVpnServers>
  <RequestId>DF11D6F6-E35A-41C3-9B20-6FC8A901FE65</RequestId>
</DescribeSslVpnServersResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DescribeSslVpnServersResponse":{
		"PageNumber":"1",
		"TotalCount":"1",
		"SslVpnServers":{
			"SslVpnServer":{
				"VpnGatewayId":"vpn-bp1q8bgx4xnkm2ogj0fiu",
				"CLientIpPool":"10.10.10.20/24",
				"Proto":"UDP",
				"Cipher":"AES-128-CBC",
				"InternetIp":"47.98.xx.xx",
				"SslVpnServerId":"vss-bp18q7hzj6largv4vk2fe",
				"Name":"test",
				"Port":"1194",
				"MaxConnections":"5",
				"RegionId":"cn-hanghzou",
				"CreateTime":"1492753580000",
				"Compress":"true",
				"LocalSubnet":"10.10.10.10/24",
				"Connections":"0"
			}
		},
		"PageSize":"10",
		"RequestId":"DF11D6F6-E35A-41C3-9B20-6FC8A901FE65"
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

