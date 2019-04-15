# Tutorial overview {#concept_f5d_bvz_wdb .concept}

The tutorial describes how to use the SSL-VPN function to connect a remote client with a VPC.

## Prerequisites {#section_hft_2vz_wdb .section}

The following conditions must be met before you deploy a VPN Gateway:

-   The client and the VPC are not using the same private CIDR block.
-   The client is able to access the Internet.

## Procedure {#section_hpk_dvz_wdb .section}

The following figure illustrates the work flow of how to connect a client to a VPC by using the SSL-VPN function.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13353/155529341741027_en-US.png)

1.  Create a VPN Gateway

    Create a VPN Gateway and enable the SSL-VPN function.

2.  Create an SSL server

    Specify the IP address range of the SSL server and the IP address range used by the client.

3.  Create a client certificate

    Create the client certificate according to server configurations, and then download the client certificate and configurations.

4.  Configure the client

    Download and install client VPN software in the client, load the client certificate and configurations, and initiate the connection.

5.  Configure security groups

    Make sure that the security group rules of ECS instances in the VPC allow remote access.


