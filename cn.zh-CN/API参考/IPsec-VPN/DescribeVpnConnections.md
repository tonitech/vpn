# DescribeVpnConnections {#doc_api_Vpc_DescribeVpnConnections .reference}

调用DescribeVpnConnections接口查询已创建的IPsec连接。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DescribeVpnConnections)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeVpnConnections|要执行的操作。

 取值： **DescribeVpnConnections**。

 |
|RegionId|String|是|cn-hangzhou|IPsec连接所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|CustomerGatewayId|String|否|cgw-bp1mvj4g9kogwxxxxxxxx|用户网关的ID。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |
|VpnGatewayId|String|否|vpn-bp1q8bgx4xnkxxxxxxxx|VPN网关的ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VpnConnections| | |IPsec连接列表的详细信息。

 |
|└IkeConfig| | |第一阶段协商的配置。

 |
|└IkeAuthAlg|String|sha1|IKE认证算法，可选sha1和MD5。

 |
|└IkeEncAlg|String|aes|IKE加密算法。

 |
|└IkeLifetime|Long|86400|IKE生存时间。

 |
|└IkeMode|String|main|IKE模式，可选main和aggressive模式。

 main模式安全性高，如果启用了NAT穿越，建议选择aggressive模式。

 |
|└IkePfs|String|group2|DH分组，可选**group1|group2|group5|group14 |group24**

 |
|└IkeVersion|String|ikev1|IKE版本。

 |
|└LocalId|String|116.xx.xx.64|本端ID，支持FQDN和IP格式，默认为当前选取的VPN网关IP地址。

 |
|└Psk|String|pgw6dy7dxxxxxxxx|预共享秘钥。

 |
|└RemoteId|String|139.xx.xx.167|对端ID，支持FQDN和IP格式，默认为当前选取的用户网关IP地址。

 |
|└IpsecConfig| | |第二阶段协商的配置。

 |
|└IpsecAuthAlg|String|sha1|IPsec认证算法，可选sha1和md5

 |
|└IpsecEncAlg|String|aes|IPsec加密算法

 |
|└IpsecLifetime|Long|86400|IPsec生存时间

 |
|└IpsecPfs|String|group2|DH分组

 |
|└VpnConnectionId|String|vco-bp10lz7aejumdxxxxxxxx|IPsec连接的ID。

 |
|└CustomerGatewayId|String|vpn-bp1q8bgx4xnkxxxxxxxx|用户网关的ID。

 |
|└VpnGatewayId|String|vpn-bp1q8bgx4xnkmxxxxxxxx|VPN网关的ID。

 |
|└Name|String|xxxxxxxxxxxx|IPsec连接的名称。

 |
|└LocalSubnet|String|1.1.1.0/24,1.1.2.0/24|VPC侧的网段。

 |
|└RemoteSubnet|String|1.1.1.0/24,1.1.2.0/24|本地IDC侧的网段。

 |
|└CreateTime|Long|1492753817000|IPsec连接的创建时间。

 |
|└Status|String|ipsec\_sa\_established|连接状态。分别为：

 -   ike\_sa\_not\_established表示第一阶段协商失败。
-   ike\_sa\_established表示第一阶段协商成功。
-   ipsec\_sa\_not\_established表示第二阶段协商失败。
-   ipsec\_sa\_established表示第二阶段协商成功。

 |
|└EffectImmediately|Boolean|true|是否立即生效。

 -   是：配置变更时触发重连。
-   否：有流量时触发重连。重连有可能导致流量闪断。

 |
|└VcoHealthCheck| | |健康检查。

 |
|└Dip|String|8.xx.xx.8|目的IP地址。

 |
|└Interval|Integer|2|健康检查的时间间隔。

 |
|└Sip|String|192.xx.xx.66|源IP地址。

 |
|TotalCount|Integer|10|列表条条目数。

 |
|PageNumber|Integer|1|当前页码。

 |
|PageSize|Integer|10|每页包含多少条目。

 |
|RequestId|String|54A4B3D0-DF4D-4C54-B8DC-5DC8DD49C939|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DescribeVpnConnections
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeVpnConnections>
  <PageNumber>1</PageNumber>
  <VpnConnections>
    <VpnConnection>
      <Name>vpn连接测试</Name>
      <CustomerGatewayId>cgw-bp1pvpl9r9adjxxxxxxxx</CustomerGatewayId>
      <RemoteSubnet>2.2.2.0/24</RemoteSubnet>
      <IpsecConfig>
        <IpsecLifetime>86400</IpsecLifetime>
        <IpsecAuthAlg>sha1</IpsecAuthAlg>
        <IpsecPfs>group2</IpsecPfs>
        <IpsecEncAlg>aes</IpsecEncAlg>
      </IpsecConfig>
      <EffectImmediately>true</EffectImmediately>
      <VpnGatewayId>vpn-bp1q8bgx4xnkmxxxxxxxx</VpnGatewayId>
      <CreateTime>1492753817000</CreateTime>
      <VpnConnectionId>vco-bp10lz7aejumdxxxxxxxx</VpnConnectionId>
      <status>ipsec_sa_established</status>
      <LocalSubnet>1.1.1.0/24,1.1.2.0/24</LocalSubnet>
      <IkeConfig>
        <IkeEncAlg>aes</IkeEncAlg>
        <RemoteId>139.xx.xx.167</RemoteId>
        <IkePfs>group2</IkePfs>
        <IkeAuthAlg>sha1</IkeAuthAlg>
        <Psk>pgw6dyxxxxxxxx</Psk>
        <IkeMode>main</IkeMode>
        <IkeLifetime>86400</IkeLifetime>
        <IkeVersion>ikev1</IkeVersion>
        <LocalId>116.xx.xx.64</LocalId>
      </IkeConfig>
    </VpnConnection>
  </VpnConnections>
  <TotalCount>1</TotalCount>
  <PageSize>10</PageSize>
  <RequestId>54A4B3D0-DF4D-4C54-B8DC-5DC8DD49C939</RequestId>
</DescribeVpnConnections>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"VpnConnections":{
		"VpnConnection":[
			{
				"CustomerGatewayId":"cgw-bp1pvpl9r9adjxxxxxxxx",
				"Name":"vpn连接测试",
				"RemoteSubnet":"2.2.2.0/24",
				"IpsecConfig":{
					"IpsecLifetime":86400,
					"IpsecAuthAlg":"sha1",
					"IpsecPfs":"group2",
					"IpsecEncAlg":"aes"
				},
				"VpnGatewayId":"vpn-bp1q8bgx4xnkmxxxxxxxx",
				"EffectImmediately":true,
				"status":"ipsec_sa_established",
				"VpnConnectionId":"vco-bp10lz7aejumdxxxxxxxx",
				"CreateTime":1492753817000,
				"LocalSubnet":"1.1.1.0/24,1.1.2.0/24",
				"IkeConfig":{
					"IkeEncAlg":"aes",
					"IkePfs":"group2",
					"RemoteId":"139.xx.xx.167",
					"IkeAuthAlg":"sha1",
					"Psk":"pgw6dyxxxxxxxx",
					"IkeMode":"main",
					"IkeLifetime":86400,
					"IkeVersion":"ikev1",
					"LocalId":"116.xx.xx.64"
				}
			}
		]
	},
	"TotalCount":1,
	"PageSize":10,
	"RequestId":"54A4B3D0-DF4D-4C54-B8DC-5DC8DD49C939"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

