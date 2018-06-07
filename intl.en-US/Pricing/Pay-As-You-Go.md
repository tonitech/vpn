# Pay-As-You-Go {#concept_iyc_hwx_wdb .concept}

VPN Gateway supports Pay-As-You-Go billing. Fees are based on the actual network traffic and are billed hourly.

## Billing items {#section_bpp_lwx_wdb .section}

The VPN Gateway provides IPSEC-VPN and SSL-VPN functions, and the billing items for different functions vary, as shown in the following table.

Total cost of each VPN gateway= instance retention fee + traffic fee + SSL specification fee

-   Instance retention fee:

    Each VPN gateway is calculated separately. The instance configuration fee is billed on an hourly basis. The fee is deducted in real time and partial hours are billed as full hours.

    **Note:** Two VPN Gateway specifications are available to use: 10 Mbps and 100 Mbps.

-   Traffic fee:

    Each VPN gateway is calculated separately. Cumulative outbound traffic of the VPN gateway in an hour is billed. Inbound traffic is not billed. Outbound traffic refers to data transferred from the Alibaba Cloud data center to the Internet. The reverse is inbound traffic.

-   SSL specification fee:

    After the SSL-VPN function is enabled, you must select the SSL specification according to the maximum number of clients connected simultaneously. The fee varies by specification. 

    **Note:** The SSL specification fee is charged only when the SSL-VPN function is enabled.


## VPN instance fee {#section_zqt_mzx_wdb .section}

The VPN gateway offers different bandwidth specifications, and the instance fee also varies by the VPN gateway specification.

**Note:** The prices in the following table are only for reference. Take the prices on the purchase page as standard.

|Region|10 Mbps \(USD/hour\)|100 Mbps \(USD/hour\)|
|:-----|:-------------------|:--------------------|
|Mainland China|0.059|0.209|
|Singapore|0.087|0.262|
|Australia \(Sydney\)|0.087|0.389|
|US \(Virginia\)|0.066|0.295|
|US \(Silicon Valley\)|0.082|0.392|
|Germany \(Frankfurt\)|0.077|0.359|
|Malaysia \(Kuala Lumpur\)|0.080|0.240|
|UAE \(Dubai\)|0.090|0.420|
|Japan \(Tokyo\)|0.091|0.275|
|India \(Mumbai\)|0.082|0.249|

## Traffic fee {#section_jrt_mzx_wdb .section}

**Note:** The prices in the following table are only for reference. Take the prices on the purchase page as standard.

|Region|Traffic fee \(USD/Gbps/hour\)|
|:-----|:----------------------------|
|Mainland China|0.125|
|Singapore|0.117|
|Australia \(Sydney\)|0.130|
|US \(Virginia\)|0.078|
|US \(Silicon Valley\)|0.078|
|Germany \(Frankfurt\)|0.070|
|Malaysia \(Kuala Lumpur\)|0.125|
|UAE \(Dubai\)|0.447|
|Japan \(Tokyo\)|0.120|
|India \(Mumbai\)|0.117|

## SSL specification fee {#section_dst_mzx_wdb .section}

After the SSL-VPN function is enabled, you must select the SSL specification according to the maximum number of clients connected simultaneously. The fee varies by specification. 

**Note:** The prices in the following table are only for reference. Take the prices on the purchase page as standard.

|SSL specification|USD/hour|
|:----------------|:-------|
|5|0.048|
|10|0.074|
|20|0.117|
|50|0.226|
|100|0.328|
|500|1.09|
|1000|1.547|

