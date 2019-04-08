# Establish a global network through VPN Gateway and CEN {#concept_mgb_qxf_xdb .concept}

This topic describes how to establish a global network by using VPN Gateway and Cloud Enterprise Network \(CEN\). International enterprises can establish a global network by using VPN Gateway and CEN. CEN can reduce cross-border network latency and VPN Gateway can help lower the cost of last-mile connections and client connections.

## Scenario {#section_b3k_sxf_xdb .section}

An international company wants to deploy different applications in multiple countries, but the applications need to be accessible by multiple offices in each country. In this example, the company has one VPC in the US \(Virginia\) region, and one in the China \(Shanghai\) region, and each VPC has a separate application deployed. The company also has two offices in Virginia and two in Shanghai.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136914/155468804441627_en-US.png)

## Solution {#section_a3r_yxf_xdb .section}

The following table details traditional connectivity solutions for offices across the globe to communicate with each other, and the problems inherent in these traditional solutions.

|Traditional solution|Problem|
|:-------------------|:------|
|Communication through the Internet|Data stored locally is exposed over the Internet and the network quality of the Internet connection is not guaranteed.|
|Communication through IPsec-VPN|Cross-border communication is affected by the network quality of the Internet connection.|
|Communication through dedicated lines|The installation of dedicated lines and subsequent maintenance incur high costs.|

To resolve the preceding problems of traditional connection solutions, Alibaba Cloud allows you to use VPN Gateway and CEN to connect applications and offices located around the world.

In the Alibaba Cloud solution, an application is deployed to each VPC located in US \(Virginia\) and China \(Shanghai\) respectively \(in this example, the VPCs for Virginia and Shanghai are VPC1 and VPC2 respectively\). Then, VPC1 and VPC2 are connected by using CEN. After that, Office 1 and Office 2 in Virginia are connected to the VPN Gateway of VPC1, and Office 3 and Office 4 in Shanghai are connected to the VPN Gateway of VPC2 through IPsec-VPN connections. In this way, the applications and offices connected to the VPCs in the US \(Virginia\) region and the China \(Shanghai\) region can communicate with each other.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/136914/155468804441628_en-US.png)

## Prerequisites {#section_il5_z3p_fhb .section}

-   The Alibaba Cloud environment is prepared. Specifically, VPCs and VSwitches are created and applications are deployed.

-   Local gateways are configured in the offices and a static public IP address is configured for each local gateway.

-   The CIDR blocks to be connected do not conflict with each other.


## Step 1: Create IPsec-VPN connections for the offices in Virginia {#section_e5z_gyf_xdb .section}

1.  Create a VPN Gateway for the VPC in the US \(Virginia\) region. For more information, see [../../../../../dita-oss-bucket/SP\_74/DNVPN11881475/EN-US\_TP\_13357.md\#section\_zv3\_nyf\_xdb](../../../../../reseller.en-US/User Guide/Manage a VPN Gateway/Create a VPN Gateway.md#section_zv3_nyf_xdb).
2.  Create two customer gateways and register the public IP addresses of the two local gateways in the two Virginia offices to the customer gateways.

    The IP addresses of customer gateways are the public IP addresses of local gateways in the offices. For more information, see [../../../../../dita-oss-bucket/SP\_74/DNVPN11881475/EN-US\_TP\_13358.md\#section\_mwf\_lxc\_xdb](../../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Manage a customer gateway/Create a customer gateway.md#section_mwf_lxc_xdb).

3.  Create two IPsec-VPN connections to connect the VPN Gateway with the two customer gateways. For more information, see [../../../../../dita-oss-bucket/SP\_74/DNVPN11881475/EN-US\_TP\_13359.md\#section\_mxd\_fyc\_xdb](../../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Manage an IPsec-VPN connection/Create an IPsec-VPN connection.md#section_mxd_fyc_xdb).
    -   **Local Network**: Enter 0.0.0.0/0.

**Note:** We recommend that you set the CIDR block at the Alibaba Cloud side to 0.0.0.0/0 to simplify your network topology. In that way, you only need to establish an IPsec-VPN connection to connect each office with Alibaba Cloud and do not need to modify the configurations of the connection if you add new offices to the network.

    -   **Remote Network**: Enter the CIDR blocks of Office 1 and Office 2, that is, 10.10.10.0/24 and 10.10.20.0/24.

4.  Configure local gateways in the Virginia offices.

    Configure local gateways based on the configurations of the created IPsec-VPN connections. For more information, see [本地网关配置](../../../../../reseller.en-US/User Guide/Configure IPsec-VPN connections/Configure local gateways/Configure an IPsec-VPN connection through a USG series Next-Generation Firewall device (Huawei).md#).


## Step 2: Create IPsec-VPN connections for the offices in Shanghai {#section_btz_tyf_xdb .section}

Create IPsec-VPN connections for the offices in Shanghai. To do so, refer to the instructions detailed in Step 1.

## Step 3: Connect VPCs {#section_sr3_5yf_xdb .section}

Connect the VPCs by using CEN. For more information, see [云企业网教程概览](../../../../../reseller.en-US/Quick Start/Tutorial overview.md#).

## Step 4: Add routes in CEN {#section_qvl_djp_fhb .section}

Publish the routes in the VPCs that are directed to the VPN Gateways to CEN so that other networks in CEN can learn the routes.

For more information, see [发布路由到CEN](../../../../../reseller.en-US/User Guide/Manage routes/Manage network routes.md#section_qts_1ct_q2b).

## Step 5: Configure security groups {#section_ks3_w1g_xdb .section}

Configure security groups for the ECS instances where you applications are deployed.

After you have completed the preceding steps, you can connect your applications with offices in different regions, and the offices and applications can communicate with each other over the intranet.

