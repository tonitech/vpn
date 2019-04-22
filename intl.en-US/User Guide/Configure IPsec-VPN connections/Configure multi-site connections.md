# Configure multi-site connections {#concept_wpm_bwf_xdb .concept}

You can create IPsec connections between multiple sites and locations. With the VPN-Hub function, the connected sites can communicate with the connected VPC, and also communicate with each of the other sites. VPN-Hub meets the needs of large enterprises to establish intranet communications between different sites.

## VPN-Hub overview {#section_hk4_nwf_xdb .section}

The VPN-Hub function is enabled by default. To achieve multi-site connections, you must create corresponding IPsec connections. A VPN Gateway can have up to ten IPsec connections. Therefore, you can connect up to ten office sites with one VPN Gateway.

The following scenario is used to illustrate connecting office sites in the cities of Shanghai, Hangzhou, and Ningbo. Before you begin, make sure that you have obtained the public IP address of the gateway device for each office site.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13370/15558969433592_en-US.png)

As shown in the following figure, to connect the three office sites \(Shanghai, Hangzhou, and Ningbo\), you only need to create a VPN Gateway and three customer gateways and establish three IPsec connections.

**Note:** Make sure the IP address ranges of all the connected sites do not conflict with each other.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13370/15558969433593_en-US.png)

## Step 1. Create a VPN Gateway {#section_u5j_zwf_xdb .section}

Create a customer gateway using the public IP address configured for the local gateway in the Shanghai office. For more information, see [EN-US\_TP\_13357.md\#](intl.en-US/User Guide/Manage a VPN Gateway/Create a VPN Gateway.md#).

**Note:** Make sure the IPsec-VPN function is enabled.

## Step 2: Create an IPsec connection to the Shanghai office {#section_qng_zwf_xdb .section}

1.  Create a customer gateway using the public IP address configured for the local gateway in the Shanghai office.

    For more information, see [EN-US\_TP\_13358.md\#section\_mwf\_lxc\_xdb](intl.en-US/User Guide/Configure IPsec-VPN connections/Manage a customer gateway/Create a customer gateway.md#section_mwf_lxc_xdb).

2.  Create an IPsec connection.

    Create an IPsec connection to connect the VPN Gateway and the customer gateway. For more information, see [EN-US\_TP\_13359.md\#section\_mxd\_fyc\_xdb](intl.en-US/User Guide/Configure IPsec-VPN connections/Manage an IPsec-VPN connection/Create an IPsec-VPN connection.md#section_mxd_fyc_xdb).

    -   **Local network**: 0.0.0.0/0.

**Note:** We recommend that you set local network to 0.0.0.0/0, which greatly simplifies the network. Only one IPsec connection is required per office and the current configurations do not need to be changed when new IPsec connections are created.

    -   **Remote network**: the IP address range of the local data center. In this example, it is the IP address range of the Shanghai office: 10.10.10.0/24.

3.  Configure the local gateway according to the configured IPsec connections.

    Download the configurations of the IPsec connection, then configure the local gateway.  For more information, see [Configure local gateways](intl.en-US/User Guide/Configure IPsec-VPN connections/Configure local gateways.md#).


## Step 3: Create additional IPsec connections for the other two sites {#section_dfp_jxf_xdb .section}

Follow the same procedures in the Step 2 to create two IPsec connections for the Hangzhou office and the Ningbo office.

## Step 4: Configure the route in VPC {#section_n31_kxf_xdb .section}

1.  Log on to the VPC console.
2.  In the left-side navigation bar, click **Route Tables**. Find the route table of the target VPC and click **Manage**.
3.  On the Route Tables page, click **Add Route Entry** to add the following routes.

    |Destination CIDR block|Next hop type|Next hop|
    |:---------------------|:------------|:-------|
    |10.10.10.0/24|VPN Gateway|The VPN Gateway created in the Step 1|
    |10.10.20.0/24|VPN Gateway|The VPN Gateway created in the Step 1|
    |10.10.30.0/24|VPN Gateway|The VPN Gateway created in the Step 1|


The IPsec connections to the three office sites have now been established. Each office site can now communicate with the VPC and can communicate with the other office sites over their intranet.

