# DescribeVpnConnection {#doc_api_951828 .reference}

调用DescribeVpnConnection接口查询已创建的IPsec连接的详细信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpnConnection)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVpnConnection|要执行的操作。

 取值： **DescribeVpnConnection**。

 |
|RegionId|String|是|cn-hangzhou|IPsec连接所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpnConnectionId|String|是|vco-bp1bbi27hojx80nck9k1i|IPsec连接的ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VpnConnectionId|String|vco-bp1bbi27hojx80nck9k1i|IPsec连接的ID。

 |
|CustomerGatewayId|String|cgw-bp1mvj4g9kogwwcxknfuv|用户网关的ID。

 |
|VpnGatewayId|String|vpn-bp1q8bgx4xnkm2ogj0fiu|VPN网关的ID。

 |
|Name|String|ipsec1|IPsec连接的名称。

 |
|LocalSubnet|String|1.1.1.0/24,1.1.2.0/24|VPC侧的网段。

 |
|RemoteSubnet|String|1.1.1.0/24,1.1.2.0/24|本地IDC侧的网段。

 |
|CreateTime|Long|1492753817000|IPsec连接的创建时间。

 |
|Status|String|ike\_sa\_not\_established|连接状态：

 -   **ike\_sa\_not\_established**表示第一阶段协商失败。
-   **ike\_sa\_established**表示第一阶段协商成功。
-   **ipsec\_sa\_not\_established**表示第二阶段协商失败。
-   **ipsec\_sa\_established**表示第二阶段协商成功。

 |
|EffectImmediately|Boolean|true|IPsec连接是否立即生效：

 -   **true**：配置变更时触发重连。
-   **false**：有流量时触发重连。重连有可能导致流量闪断。

 |
|IkeConfig| | |第一阶段协商的配置。

 |
|└IkeAuthAlg|String|sha1|IKE认证算法，支持sha1和MD5。

 |
|└IkeEncAlg|String|aes|IKE加密算法。

 |
|└IkeLifetime|Long|86400|IKE生存时间。

 |
|└IkeMode|String|main|IKE模式，支持main和aggressive模式。main模式安全性高，如果启用了NAT穿越，建议使用aggressive模式。

 |
|└IkePfs|String|group2|DH分组。

 |
|└IkeVersion|String|ikev1|IKE版本。

 |
|└LocalId|String|116.62.69.64|本端ID，支持FQDN和IP格式，默认为当前选取的VPN网关IP地址。

 |
|└Psk|String|pgw6dy7d1i8in7x5|预共享秘钥。

 |
|└RemoteId|String|139.196.32.167|对端ID，支持FQDN和IP格式，默认为当前选取的用户网关IP地址。

 |
|IpsecConfig| | |第二阶段协商的配置。

 |
|└IpsecAuthAlg|String|sha1|IPsec认证算法，支持sha1和md5。

 |
|└IpsecEncAlg|String|aes|IPsec加密算法。

 |
|└IpsecLifetime|Long|86400|IPsec生存时间。

 |
|└IpsecPfs|String|group2|DH分组。

 |
|RequestId|String|F2310D45-BCF6-4E2E-9082-B4503844BA4C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeVpnConnection
&RegionId=cn-hangzhou
&VpnConnectionId=vco-bp1bbi27hojx80nck9k1i
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVpnConnectionResponse>
  <PageNumber>1</PageNumber>
  <VpnConnections>
    <VpnConnection>
      <Name>c2</Name>
      <CustomerGatewayId>cgw-bp1wl8dtz3auwlavwhgcw</CustomerGatewayId>
      <Status>ike_sa_not_established</Status>
      <RemoteSubnet>192.168.0.0/16</RemoteSubnet>
      <IpsecConfig>
        <IpsecLifetime>86400</IpsecLifetime>
        <IpsecAuthAlg>md5</IpsecAuthAlg>
        <IpsecPfs>group2</IpsecPfs>
        <IpsecEncAlg>aes</IpsecEncAlg>
      </IpsecConfig>
      <EffectImmediately>false</EffectImmediately>
      <VpnGatewayId>vpn-bp1yfrjxn4d5t63tbqq70</VpnGatewayId>
      <CreateTime>1519391420000</CreateTime>
      <VpnConnectionId>vco-bp1w3m1p23iftycvseuc2</VpnConnectionId>
      <LocalSubnet>172.16.0.0/12</LocalSubnet>
      <IkeConfig>
        <IkeEncAlg>aes</IkeEncAlg>
        <RemoteId>47.97.176.95</RemoteId>
        <IkePfs>group2</IkePfs>
        <IkeAuthAlg>sha1</IkeAuthAlg>
        <Psk>1234567</Psk>
        <IkeMode>aggressive</IkeMode>
        <IkeLifetime>86400</IkeLifetime>
        <IkeVersion>ikev1</IkeVersion>
        <LocalId>116.62.119.2</LocalId>
      </IkeConfig>
    </VpnConnection>
  </VpnConnections>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>7D598A10-26EF-44F2-9F47-E417842F3CEA</RequestId>
</DescribeVpnConnectionResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"VpnConnections":{
		"VpnConnection":[
			{
				"CustomerGatewayId":"cgw-bp1wl8dtz3auwlavwhgcw",
				"Name":"c2",
				"Status":"ike_sa_not_established",
				"RemoteSubnet":"192.168.0.0/16",
				"IpsecConfig":{
					"IpsecLifetime":86400,
					"IpsecAuthAlg":"md5",
					"IpsecPfs":"group2",
					"IpsecEncAlg":"aes"
				},
				"VpnGatewayId":"vpn-bp1yfrjxn4d5t63tbqq70",
				"EffectImmediately":false,
				"VpnConnectionId":"vco-bp1w3m1p23iftycvseuc2",
				"CreateTime":1519391420000,
				"LocalSubnet":"172.16.0.0/12",
				"IkeConfig":{
					"IkeEncAlg":"aes",
					"IkePfs":"group2",
					"RemoteId":"47.97.176.95",
					"IkeAuthAlg":"sha1",
					"Psk":"1234567",
					"IkeMode":"aggressive",
					"IkeLifetime":86400,
					"IkeVersion":"ikev1",
					"LocalId":"116.62.119.2"
				}
			}
		]
	},
	"TotalCount":1,
	"PageSize":10,
	"RequestId":"7D598A10-26EF-44F2-9F47-E417842F3CEA"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|404|InvalidVpnConnectionInstanceId.NotFound|The specified vpn connection instance id does not exist.|指定的 VPN 连接不存在，请您检查该 VPN 链接是否正确。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

