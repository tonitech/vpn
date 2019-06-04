# CreateVpnConnection {#doc_api_1087753 .reference}

调用CreateVpnConnection接口创建IPsec连接。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Vpc&api=CreateVpnConnection)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateVpnConnection|要执行的操作。

 取值： **CreateVpnConnection**。

 |
|CustomerGatewayId|String|是|vpn-bp1q8bgx4xnkm2ogj0fiu|用户网关的ID。

 |
|LocalSubnet|String|是|1.1.1.0/24,1.1.2.0/24|需要和本地IDC互连的VPC侧的网段，用于第二阶段协商。

 多个网段之间用逗号分隔，例如：192.168.1.0/24,192.168.2.0/24。

 |
|RegionId|String|是|cn-shanghai|IPsec连接所在的地域。

 您可以通过调用[DescribeRegions](~~36063~~)接口获取地域ID。

 |
|RemoteSubnet|String|是|1.1.1.0/24,1.1.2.0/24|本地IDC的网段，用于第二阶段协商。

 多个网段之间用逗号分隔，例如：192.168.3.0/24,192.168.4.0/24。

 |
|VpnGatewayId|String|是|vpn-bp1q8bgx4xnkm2ogj0fiu|VPN网关的ID。

 |
|ClientToken|String|否|02fb3da4-130e-11e9-8e44-0016e04115b|客户端token，用于保证请求的幂等性。 由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个 ASCII 字符。

 |
|EffectImmediately|Boolean|否|false|是否删除当前已协商成功的IPsec隧道并重新发起协商。取值：

 -   **true**：配置完成后立即进行协商。
-   **false**（默认值）：当有流量进入时进行协商。

 |
|IkeConfig|String|否|ikev1|第一阶段协商的配置信息：

 -   **IkeConfig.Psk**：用于IPsec VPN网关与用户网关之间的身份认证。默认情况下会随机生成，也可以手动指定密钥。长度限制为100个字符。
-   **IkeConfig.IkeVersion**：IKE协议的版本。取值：ikev1| ikev2，默认值：ikev1。
-   **IkeConfig.IkeMode**：IKE V1版本的协商模式。取值：main | aggressive，默认值：main。
-   **IkeConfig.IkeEncAlg**：第一阶段协商的加密算法，取值：aes | aes192 | aes256 | des | 3des，默认值：aes。
-   **IkeConfig.IkeAuthAlg**：第一阶段协商的认证算法，取值：md5 | sha1，默认值：sha。
-   **IkeConfig.IkePfs**：第一阶段协商使用的Diffie-Hellman密钥交换算法，取值：group1 | group2 | group5 | group14 | group24，默认值：group2。
-   **IkeConfig.IkeLifetime**：第一阶段协商出的SA的生存周期。取值范围为0-86400，单位为秒，默认值：86400。
-   **IkeConfig.LocalIdIPsec**：VPN网关的标识，长度限制为100个字符，默认值为VPN网关的公网IP地址。
-   **IkeConfig.RemoteId**：用户网关的标识，长度限制为100个字符，默认值为用户网关的公网IP地址。

 |
|IpsecConfig|String|否|aes|第二阶段协商的配置信息：

 -   **IpsecConfig.IpsecEncAlg**：第二阶段协商的加密算法，取值：aes | aes192 | aes256 | des | 3des，默认值：aes。
-   **IpsecConfig. IpsecAuthAlg**：第二阶段协商的认证算法，取值：md5 | sha1，默认值：sha1。
-   **IpsecConfig. IpsecPfs**：转发所有协议的报文。第一阶段协商使用的Diffie-Hellman密钥交换算法，取值：group1 | group2 | group5 | group14 | group24，默认值：group2。
-   **IpsecConfig. IpsecLifetime**：第二阶段协商出的SA的生存周期。取值范围为 0-86400，单位为秒，默认值：86400。

 |
|Name|String|否|IPsec|IPsec连接的名称。 长度为 2-128个字符，必须以字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。但不能以`http://`或`https://`开头。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VpnConnectionId|String|vco-bp15oes1py4i66rmdnc7k|IPsec连接的ID。

 |
|CreateTime|Long|1544666102000|IPsec连接的创建时间。

 |
|Name|String|test|IPsec连接的名称。

 |
|RequestId|String|082AD562-B8DB-4BB2-861F-DA1FCA01FD76|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://vpc.aliyuncs.com/?Action=CreateVpnConnection
&CustomerGatewayId=vpn-bp1q8bgx4xnkm2ogj0fiu
&LocalSubnet=1.1.1.0/24,1.1.2.0/24
&RegionId=cn-shanghai
&RemoteSubnet=1.1.1.0/24,1.1.2.0/24
&VpnGatewayId=vpn-bp1q8bgx4xnkm2ogj0fiu
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateVpnConnectionResponse>
  <VpnConnectionId>vco-bp1bbi27hojx80nck9k1i</VpnConnectionId>
  <CreateTime>1493363928000</CreateTime>
</CreateVpnConnectionResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"VpnConnectionId":"vco-bp15oes1py4i66rmdnc7k",
	"CreateTime":1544666102000
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|Forbbiden.SubUser|User not authorized to operate on the specified resource as your account is created by another user.|您没有权限操作该资源，请您申请操作权限后再试。|
|403|Forbidden|User not authorized to operate on the specified resource.|您没有权限操作指定资源，请提交工单咨询。|
|400|Resource.QuotaFull|The quota of resource is full|资源配额已达上限。|
|404|InvalidCustomerGatewayInstanceId.NotFound|The specified customer gateway instance id does not exist.|指定的 Instance 不存在，请您检查 Instance 是否正确。|
|404|InvalidVpnGatewayInstanceId.NotFound|The specified vpn gateway instance id does not exist.|指定的 VPN 网关不存在，请您检查 VPN 网关是否正确。|
|400|InvalidVpnConnection.AlreadyExists|Vpn connection already exists.|VPN 连接已经存在，不用再次添加。|
|400|VpnGateway.Configuring|The specified service is configuring.|服务正在配置中，请您稍后再试。|
|400|VpnGateway.FinancialLocked|The specified service is financial locked.|该服务已欠费，请您先充值再操作。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Vpc)

