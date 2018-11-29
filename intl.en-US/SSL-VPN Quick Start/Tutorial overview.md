# Tutorial overview {#concept_f5d_bvz_wdb .concept}

The tutorials illustrate how to use SSL-VPN to connect a VPC from a remote computer using the Linux, Windows, and Mac operating systems.

## Prerequisites {#section_hft_2vz_wdb .section}

Switch to the new VPC console.

## Procedure {#section_hpk_dvz_wdb .section}

Follow these steps to access the VPC from the client using the SSL-VPN feature:

1.  Create a VPN Gateway

    Create a VPN Gateway with SSL-VPN enabled.

2.  Create an SSL server

    Specify the IP address range of the SSL server and the IP address range used by the client for connection.

3.  Create a client certificate

    Create the client certificate according to the server configuration, and download the client certificate and configurations.

4.  Configure the client

    Download and install the client VPN software in the client, load the client certificate and configurations, and initiate the connection.

5.  Configure security rules

    Make sure the security group rules of the ECS instance allow remote access.


