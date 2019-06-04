# DownloadVpnConnectionConfig {#doc_api_951831 .reference}

调用DownloadVpnConnectionConfig接口获取IPsec连接的配置信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=DownloadVpnConnectionConfig)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DownloadVpnConnectionConfig|要执行的操作。

 取值： **DownloadVpnConnectionConfig**。

 |
|RegionId|String|是|cn-shanghai|IPsec连接所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|VpnConnectionId|String|是|vco-bp1bbi27hojx80nck9k1i|IPsec连接的ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|0C68048B-0F70-40DA-B8AE-1B79B5CF62E3|请求ID。

 |
|VpnConnectionConfig| | |IPsec连接的配置信息。

 |
|└IkeConfig| | |IKE配置相关配置信息。

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
|└LocalId|String|116.62.69.64|本端ID，支持FQDN和IP格式，默认为当前选取的VPN网关IP地址

 |
|└Psk|String|pgw6dy7d1i8in7x5|预共享秘钥

 |
|└RemoteId|String|139.196.32.167|对端ID，支持FQDN和IP格式，默认为当前选取的用户网关IP地址。

 |
|└IpsecConfig| | |IPsec配置信息。

 |
|└IpsecAuthAlg|String|sha1|IPsec认证算法，支持sha1和md5。

 |
|└IpsecEncAlg|String|aes|IPsec加密算法。

 |
|└IpsecLifetime|Long|86400|IPsec生存时间。

 |
|└IpsecPfs|String|group2|DH分组。

 |
|└Local|String|139.196.32.167|IPsec VPN网关的标识。

 |
|└LocalSubnet|String|1.1.1.0/24,1.1.2.0/24|VPC侧的网段。

 |
|└Remote|String|116.62.69.64|用户网关的标识。

 |
|└RemoteSubnet|String|1.1.1.0/24,1.1.2.0/24|本地IDC侧的网段。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=DownloadVpnConnectionConfig
&RegionId=cn-shanghai
&VpnConnectionId=vco-bp1bbi27hojx80nck9k1i
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DownloadVpnConnectionConfigResponse>
  <RequestId>6F4A035F-7060-45D7-B9BD-719372782AF6</RequestId>
  <VpnConnectionConfig>
    <RemoteSubnet>1.1.1.0/24,1.1.2.0/24</RemoteSubnet>
    <Local>139.196.32.167</Local>
    <IpsecConfig>
      <IpsecLifetime>86400</IpsecLifetime>
      <IpsecAuthAlg>sha1</IpsecAuthAlg>
      <IpsecPfs>group2</IpsecPfs>
      <IpsecEncAlg>aes</IpsecEncAlg>
    </IpsecConfig>
    <Remote>116.62.69.64</Remote>
    <LocalSubnet>2.2.2.0/24</LocalSubnet>
    <IkeConfig>
      <IkeEncAlg>aes</IkeEncAlg>
      <IkePfs>group2</IkePfs>
      <RemoteId>116.62.69.64</RemoteId>
      <IkeAuthAlg>sha1</IkeAuthAlg>
      <Psk>pgw6dy7d1i8in7x5</Psk>
      <IkeMode>main</IkeMode>
      <IkeLifetime>86400</IkeLifetime>
      <IkeVersion>ikev1</IkeVersion>
      <LocalId>139.196.32.167</LocalId>
    </IkeConfig>
  </VpnConnectionConfig>
</DownloadVpnConnectionConfigResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0C68048B-0F70-40DA-B8AE-1B79B5CF62E3",
	"VpnConnectionConfig":{
		"RemoteSubnet":"1.1.1.0/24,1.1.2.0/24",
		"IpsecConfig":{
			"IpsecLifetime":86400,
			"IpsecAuthAlg":"sha1",
			"IpsecPfs":"group2",
			"IpsecEncAlg":"aes"
		},
		"Local":"139.196.32.167",
		"Remote":"116.62.69.64",
		"LocalSubnet":"2.2.2.0/24",
		"IkeConfig":{
			"IkeEncAlg":"aes",
			"RemoteId":"116.62.69.64",
			"IkePfs":"group2",
			"IkeAuthAlg":"sha1",
			"Psk":"pgw6dy7d1i8in7x5",
			"IkeMode":"main",
			"IkeLifetime":86400,
			"IkeVersion":"ikev1",
			"LocalId":"139.196.32.167"
		}
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|404|InvalidVpnConnectionInstanceId.NotFound|The specified vpn connection instance id does not exist.|指定的 VPN 连接不存在，请您检查该 VPN 链接是否正确。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

