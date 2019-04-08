# Temporarily upgrade a VPN Gateway {#task_q2v_ccd_xdb .task}

This topic describes how to temporarily upgrade a VPN Gateway. When the time period of the upgrade expires, the VPN Gateway automatically reverts to its previous configuration.

A VPN Gateway is created. For more information, see [Create a VPN Gateway](reseller.en-US/User Guide/Manage a VPN Gateway/Create a VPN Gateway.md#).

1.  Log on to the [VPC console](https://partners-intl.aliyun.com/login-required#/vpc). 
2.  In the left-side navigation pane, choose **VPN** \> **VPN Gateways**. 
3.  Select the region of the target VPN Gateway. 
4.  Find the target VPN Gateway, and click **Temporary Upgrade** in the **Actions** column. 
5.  On the purchase page, select a new **Peak Bandwidth** and the **Restoration Time**, and complete the payment. The minimum duration for a temporary upgrade is two hours and the VPN Gateway is billed on an hourly basis after being upgraded. The upgrade takes effect after you complete the payment. Service continuity is ensured during the upgrading process and after the VPN Gateway is upgraded. However, intermittent connections may occur while the VPN Gateway is being downgraded. Therefore, we recommend that you use backend applications with reconnection functions.

