# CreateVpnGateway {#doc_api_951812 .reference}

调用CreateVpnGateway接口创建一个VPN网关。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateVpnGateway)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateVpnGateway|要执行的操作。

 取值： **CreateVpnGateway**。

 |
|Bandwidth|Integer|是|5|VPN网关的公网带宽，单位Mbps。

 取值：**5 |10 | 20 | 50 | 100**

 |
|RegionId|String|是|cn-hangzhou|VPN网关所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpcId|String|是|vpc-bp1ub1yt9cvakoelj1y9c|VPN网关所属的VPC ID。

 |
|AutoPay|Boolean|否|false|是否自动支付VPN网关的账单。

 取值：**true | false \(默认值\)**

 |
|EnableIpsec|Boolean|否|true|是否开启IPsec-VPN功能。IPsec-VPN功能提供站点到站点的连接。您可以通过创建IPsec隧道将本地数据中心网络和专有网络或两个专有网络安全地连接起来。

 取值：**true \(默认值\) | false**

 |
|EnableSsl|Boolean|否|true|开启SSL-VPN功能。提供点到站点的VPN连接，不需要配置客户网关，终端直接接入。

 取值：**true | false \(默认值\)**

 |
|InstanceChargeType|String|否|PREPAY|VPN网关的计费类型，取值：

 -   **PREPAY**：预付费，包月购买。
-   **POSTPAY**：后付费，按流量计费。

 |
|Name|String|否|MYVPN|VPN网关的名称，默认值为VPN网关的ID。

 长度为2-100个英文或中文字符，必须以大小字母或中文开头，可包含数字，下划线（\_）和短横线（-），不能以`http://`或 `https://`开头。

 |
|Period|Integer|否|1|购买时长，取值：

 **1-9 | 12 | 24 | 36**

 |
|SslConnections|Integer|否|2|允许同时连接的最大客户端数量。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Name|String|myVpn|VPN网关的名称。

 |
|OrderId|Long|202249400220415|订单ID，请前往阿里云控制台完成支付。

 |
|RequestId|String|54B48E3D-DF70-471B-AA93-08E683A1B457|请求ID。

 |
|VpnGatewayId|String|vpn-bp1q8bgx4xnkm2ogj0fiu|VPN网关的ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateVpnGateway
&Bandwidth=5
&RegionId=cn-hangzhou
&VpcId=vpc-bp1ub1yt9cvakoelj1y9c
&Name=MYVPN
&InstanceChargeType=PREPAY
&Period=1
&AutoPay=false
&EnableIpsec=true
&EnableSsl=true
&SslConnections=2
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateVpnGatewayResponse>
  <Name>myVpn</Name>
  <VpnGatewayId>vpn-bp1q8bgx4xnkm2ogj0fiu</VpnGatewayId>
  <RequestId>54B48E3D-DF70-471B-AA93-08E683A1B457</RequestId>
</CreateVpnGatewayResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CreateVpnGatewayResponse":{
		"Name":"myVpn",
		"VpnGatewayId":"vpn-bp1q8bgx4xnkm2ogj0fiu",
		"RequestId":"54B48E3D-DF70-471B-AA93-08E683A1B457"
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Resource.QuotaFull|The quota of resource is full|资源配额已达上限。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

