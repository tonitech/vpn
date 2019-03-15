# 下载IPsec连接配置 {#task_czy_ttz_bhb .task}

配置IPsec连接并协商成功后，您可以下载IPsec连接配置，将该配置加载到本地网关设备中。

您已经创建了IPsec连接。详细信息，请参见[创建IPsec连接](cn.zh-CN/用户指南/创建IPsec连接.md#)。

1.  登录[专有网络管理控制台](https://vpcnext.console.aliyun.com/nat/)。 
2.  在左侧导航栏，单击**VPN** \> **IPSec连接**。 
3.  在IPsec连接页面，选择IPsec连接的地域。 
4.  找到目标IPsec连接，单击**操作**列下的**下载对端配置**。 

    **说明：** 下载配置中的RemotSubnet和LocalSubnet与创建IPsec连接时的本端网段和对端网段正好是相反的。因为从阿里云VPN网关的角度看，对端是本地IDC的网段，本端是阿里云侧的VPC网段；而从本地IDC的网关设备角度看，LocalSubnet就是指本地IDC的网段，RemotSubnet则是指阿里云VPC的网段。


