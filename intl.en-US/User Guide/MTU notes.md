# MTU notes {#concept_270137 .concept}

The maximum transmission unit \(MTU\) is the size \(in bytes\) of the largest packet supported by the network layer protocol \(such as TCP\), with headers and data included.

Network packets sent over IPsec tunnels are encrypted and then encapsulated in external packets for routing. Because an encapsulated internal packet itself must fit the MTU of the corresponding external packet, the MTU of the internal packet must be smaller.

## Gateway MTU and system MTU {#section_vdd_xz4_cvc .section}

You must configure the MTU limit of the local VPN Gateway to not more than 1,400 bytes. We recommend that you set the MTU to 1,400 bytes.

For TCP traffic, the maximum length of data that can be carried by each packet segment can be negotiated by the sender and receiver when they communicate based on the maximum segment size \(MSS\).

