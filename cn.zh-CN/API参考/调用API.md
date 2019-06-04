# 调用API {#concept_354701 .concept}

VPN网关和专有网络使用同一个服务地址（endpoint）。接口调用是向VPN网关API的服务端地址发送HTTP GET请求。您需要按照接口说明在请求中加入相应请求参数，调用后系统会返回处理结果。请求及返回结果都使用UTF-8字符集进行编码。

## 请求结构 {#section_oh9_42n_k0m .section}

VPN网关的API是RPC风格，您可以通过发送HTTP GET请求调用VPN网关API。

其请求结构如下：

``` {#codeblock_cxj_4ce_kuw}
http://Endpoint/?Action=xx&Parameters
```

其中：

-   Endpoint：VPN网关API 的服务接入地址为`vpc.aliyuncs.com`。
-   Action：要执行的操作，如使用CreateVpnGateway创建VPN网关。
-   Version：要使用的API版本，弹性公网IP的API版本是2016-04-28。
-   Parameters：请求参数，每个参数之间用&分隔。

    请求参数由公共请求参数和API自定义参数组成。公共参数中包含API版本号、身份验证等信息。详细信息，请参见[公共参数](../../../../cn.zh-CN/API参考/公共参数.md#)。


下面是一个调用CreateVpnGateway接口创建VPN网关的示例：

**说明：** 为了便于查看，本文档中的示例都做了格式化处理。

``` {#codeblock_c2t_00w_ifn}
https://vpc.aliyuncs.com/?Action=CreateVpnGateway
&Format=xml
&Version=2016-04-28
&Signature=xxxx%xxxx%3D
&SignatureMethod=HMAC-SHA1
&SignatureNonce=15215528852396
&SignatureVersion=1.0
&AccessKeyId=key-test
&Timestamp=2012-06-01T12:00:00Z
…
```

## API授权 {#section_dg5_yrv_pxr .section}

为了确保您的账号安全，建议您使用子账号的身份凭证调用API。如果您使用RAM账号调用VPN网关API，您需要为该RAM账号创建、附加相应的授权策略。

VPN网关中可授权的资源和接口列表，请参见[RAM鉴权](../../../../cn.zh-CN/API参考/RAM鉴权.md#)。

## API签名 {#section_sbz_565_l4h .section}

VPN网关服务会对每个API请求进行身份验证，无论使用HTTP还是HTTPS协议提交请求，都需要在请求中包含签名（Signature）信息。

VPN网关通过使用AccessKey ID和AccessKey Secret进行对称加密的方法来验证请求的发送者身份。AccessKey是阿里云账号和RAM用户发布的一种身份凭证\(类似于用户的登录密码\)，其中AccessKey ID用于标识访问者的身份。AccessKey Secret是用于加密签名字符串和服务器端验证签名字符串的密钥，必须严格保密。

RPC API需按如下格式在请求中增加签名（Signature）：

`https://endpoint/?SignatureVersion=*1.0*&SignatureMethod=*HMAC-SHA1*&Signature=*XXXX%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx*`

以CreateVpnGateway为例，假设AccessKey ID是`testid`， AccessKey Secret是`testsecret`，则签名前的请求URL如下：

``` {#codeblock_ymo_8xb_ocj}
http://vpc.aliyuncs.com/?Action=CreateVpnGateway
&Timestamp=2016-05-23T12:46:24Z
&Format=XML
&AccessKeyId=testid
&SignatureMethod=HMAC-SHA1
&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx
&Version=2014-05-26
&SignatureVersion=1.0
```

完成以下步骤计算签名：

1.  使用请求参数创建待签名字符串：

    ``` {#codeblock_qky_psb_y4i}
    GET&%2F&AccessKeyId%3Dtestid&Action%3DCreateVpnGateway&Format%3DXML&SignatureMethod%3DHMAC-SHA1&SignatureNonce%3D3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx&SignatureVersion%3D1.0&TimeStamp%3D2016-02-23T12%253A46%253A24Z&Version%3D2014-05-15
    ```

    。

2.  计算待签名的HMAC的值。

    在AccessKey Secret后添加一个&作为计算HMAC值的key。本示例中的key为`testsecret&`。

    ``` {#codeblock_ahy_s0f_jx2}
    CT9X0VtwR86fNWS********juE=
    ```

3.  将签名加到请求参数中：

    ``` {#codeblock_fo1_3fd_ars}
    http://vpc.aliyuncs.com/?Action=CreateVpnGateway
    &Timestamp=2016-05-23T12:46:24Z
    &Format=XML
    &AccessKeyId=testid
    &SignatureMethod=HMAC-SHA1
    &SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0axxxxxxxx
    &Version=2014-05-26
    &SignatureVersion=1.0
    &Signature=XXXX%3D
    ```


