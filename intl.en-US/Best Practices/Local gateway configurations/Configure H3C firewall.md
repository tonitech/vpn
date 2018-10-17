# Configure H3C firewall {#task_snz_rc2_xdb .task}

When using IPsec-VPN to create a site-to-site connection, you must configure the local gateway according to the IPsec connection configured for the Alibaba Cloud VPN Gateway. This document takes H3C firewall as an example to show how to configure the VPN settings.

-   Make sure you have configured IPsec connections. For more information, see [Configure a site-to-site connection.](https://help.aliyun.com/document_detail/65072.html?spm=a2c4g.11186623.2.3.02pwkT).

-   After you create an IPsec connection, download the configurations of the created IPsec connection.

    In this tutorial, the configurations of the IPsec connection are as follows:

    -   IPsec configuration

|Configuration|Value|
|:------------|:----|
|IKE|Authentication Algorithm|sha1|
|Encryption Algorithm|aes|
|DH Group|group2|
|IKE Version|ikev1|
|SA Life Cycle \(seconds\)|86400|
|Negotiation Mode|main|
|PSK|h3c|
|IPsec|Authentication Algorithm|sha1|
|Encryption Algorithm|aes|
|DH Group|group2|
|IKE Version|ikev1|
|SA Life Cycle \(seconds\)|86400|
|Negotiation Mode|esp|

    -   Network configuration

|Configuration|Value|
|:------------|:----|
|VPC configuration|Private IP address range|192.168.10.0/24|
|Public IP of VPN Gateway|101.xxx.xxx.127|
|IDC network configuration|Private IP address range|192.168.66.0/24|
|Public IP of local gateway|122.xxx.xxx.248|
|Uplink Ethernet Ports|Reth 1|
|Downlink Ethernet Ports|G 2/0/10|


1.   Log on to the console of the H3C firewall, and then click**Network** \> **VPN** \> **IPSec** \> **Policy** . 
2.   Configure the H3C firewall IPsec policy based on the IPsec configurations of the Alibaba Cloud VPN Gateway.  Click **Add** in the **Protected Data Stream** list, set the IP address range of the IDC to the source IP and the IP address range of the VPC to the destination IP. 
3.   Click**IKE Proposal** \> **Create**. Configure IKE proposal according to the IKE information of the IPsec connection configured for the Alibaba Cloud VPN Gateway.
4.   Click**Network** \> **VPN** \> **IPsec** \> **Policy**. 
5.   Select the new IPsec policy, click **Advanced Configuration**, configure IPsec protocol 

    according to the IPsec information of the IPsec connection configured for the Alibaba Cloud VPN Gateway.

    Create the downlink security policy and the uplink security policy.

    -   The security policy configuration from the Alibaba cloud VPC to the local IDC is shown in the following figure.

6.   Click**Policy** \> **Security Policy** \> **Create**. 

    The security policy configuration from the Alibaba Cloud VPC to the local IDC is shown in the following figure.

    The security policy configuration from the local IDC to the Alibaba Cloud VPC is shown in the following figure.

7.   Click**Network** \> **Route** \> **Static Route**. 
8.   Add the default route, set the uplink interface as the next hop of the outbound traffic. 

