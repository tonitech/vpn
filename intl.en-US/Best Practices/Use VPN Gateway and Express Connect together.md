# Use VPN Gateway and Express Connect together {#concept_mgb_qxf_xdb .concept}

Multinational corporations can use Express Connect to connect two VPCs from different regions and use VPN Gateway to connect local sites within regions with low latency at a low cost.

## Example scenario {#section_b3k_sxf_xdb .section}

Multinational corporations often have the need to deploy applications in multiple countries and interconnect Operation and Maintenance systems around the world. For example, an enterprise deploys two sets of applications in the eastern United States and Shanghai, and needs to connect offices worldwide as shown in the following figure:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13371/15382959383594_en-US.png)

## Solution overview {#section_a3r_yxf_xdb .section}

Typical worldwide communication and data transfer solutions, and risks include the following:

|Typical solutions|Risks|
|:----------------|:----|
|Direct connections over the Internet|Sensitive, proprietary data is disclosed over the Internet and the network quality is unstable.|
|IPsec VPN|Provides high security, but is still dependent on the public Internet. The multinational network quality is limited by the Internet network infrastructure.|
|Dedicated leased line|High security and high network quality, but with relatively high costs.|

Alibaba Cloud provides secure, high-quality, and relatively low-cost solution for connecting office networks around the world by combining VPN Gateway and Express Connect.

You can use Express Connect to connect two VPCs and use VPN Gateway to connect the office sites to VPCs as shown in the following figure:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13371/15382959383595_en-US.png)

## Prerequisites { .section}

-   Create a VPC and a VSwitch.

-   Configure a local gateway in each office and make sure a static public IP address is available.

-   The IP address ranges of the sites to be connected cannot be in conflict with one another.


## Step 1: Create IPsec connections to the US East offices {#section_e5z_gyf_xdb .section}

You can create two IPsec connections to connect the offices in the East US region to the VPC. With VPN-Hub, the connected offices can communicate with each other. For more information, see [Configure multi-site connections](reseller.en-US/Best Practices/Configure multi-site connections.md#).

1.  Create a VPN gateway for the VPC in the East US region. For more information, see [Create a VPN gateway](../../../../reseller.en-US/User Guide/Manage a VPN Gateway.md#section_zv3_nyf_xdb).
2.  Create two customer gateways using the public IP addresses of the two offices.

    For more information, see [Create a customer gateway](../../../../reseller.en-US/User Guide/Manage a customer gateway.md#section_mwf_lxc_xdb).

3.  Create two IPsec connections to connect the VPN gateway and the customer gateways. For more information, see [Create an IPsec connection](../../../../reseller.en-US/User Guide/Manage an IPsec connection.md#section_mxd_fyc_xdb).
    -   **Local network**: Enter 0.0.0.0/0.

**Note:** We recommend that you set local network to 0.0.0.0/0, which greatly simplifies the network. Only one IPsec connection is required per office and the current configurations do not need to be changed when new IPsec connections are created.

    -   **Remote network**: 10.10.10.0/24 and 10.10.20.0/24

4.  Configure the local gateway according to the configured IPsec connections.

    Load the VPN configurations according to the requirements of the local office on gateway device. For more information, see [Local gateway configurations](reseller.en-US/Best Practices/Local gateway configurations.md#).


## Step 2: Create IPsec connections to the Shanghai offices {#section_btz_tyf_xdb .section}

Follow procedures in Step 1 to create two IPsec connections to connect the offices in the Shanghai to the Shanghai VPC.

## Step 3: Connect the two VPCs {#section_sr3_5yf_xdb .section}

You can connect the two VPCs by creating a pair of Express Connect router interfaces. For more information, see [VPC interconnection](https://help.aliyun.com/document_detail/44842.html).

The router interface configuration in this tutorial is shown in the following figure.

![](images/3596_en-US.png)

## Step 4: Configure the route { .section}

1.  Log on to the VPC console.
2.  In the left-side navigation bar, click **Route Tables**. Find the route table of the target VPC and click **Manage**.
3.  On the Route Tables page, click **Add Route Entry** to add the following routes.

    Add the following route entries for VPC 1 \(172.16.0.0/16\):

    |Destination CIDR block|Next hop type|Next hop|Description|
    |:---------------------|:------------|:-------|:----------|
    |10.10.10.0/24 \(US office 1\)|VPN Gateway|VPN Gateway for VPC 1|Route the traffic destined for 10.10.10.0/24 or 10.10.20.0/24 to the VPN gateway in the US.|
    |10.10.20.0/24 \(US office 2\)|VPN Gateway|VPN Gateway for VPC 1|
    |172.17.0.0/16 \(Shanghai VPC\)|VPC|VPC2|Route the traffic destined for the destination CIDR block to VPC 2.|
    |10.20.10.0/24 \(Shanghai office 3\)|VPC|VPC2|
    |10.20.20.0/24  \(Shanghai office 4\)|VPC|VPC2|

4.  Add the following route entries to VPC2 \(172.17.0.0/16\):

    |Destination CIDR block|Next hop type|Next hop|Description|
    |:---------------------|:------------|:-------|:----------|
    |10.20.10.0/24 \(Shanghai office 3\)|VPN Gateway|VPN Gateway for VPC 2|Route the traffic destined for 10.20.10.0/24 or 10.20.20.0/24 to the VPN gateway in Shanghai.|
    |10.20.20.0/24 \(Shanghai office 4\)|VPN Gateway|VPN Gateway for VPC 2|
    |172.16.0.0/16 \(US VPC\)|VPC|VPC1|Route the traffic destined for the destination CIDR block to VPC 1.|
    |10.10.10.0/24 \(US office 1\)|VPC|VPC1|
    |10.10.20.0/24 \(US office 2\)|VPC|VPC1|


## Step 5: Configure security rules {#section_ks3_w1g_xdb .section}

Configure security rules for the ECS instances in the VPC networks

according to your individual business requirements.

