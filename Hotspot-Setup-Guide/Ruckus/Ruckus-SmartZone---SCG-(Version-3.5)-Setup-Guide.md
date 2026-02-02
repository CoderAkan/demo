## Information Required for FansWiFi Manager

- **MAC Addresses** of the APs

### FansWiFi Server / Controller Communication

The table below lists the ports that must be opened on your network firewall to ensure successful communication between the hotspot system and FansWiFi servers.

| Port Number | Protocol | Source | Destination | Direction | Purpose | Required By |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1812 / 1813 | UDP & TCP | Controller | FansWiFi RADIUS (103.6.85.240) | Outbound | AAA Auth & Accounting | All |
| 1700 / 3799 | UDP & TCP | FansWiFi RADIUS (103.6.85.240) | Controller | Inbound | RADIUS CoA Messages | WeChat, Video, Advanced FB |
| 8443 / 9443 | TCP | FansWiFi | Controller NBI | Inbound | Northbound API Access | All |


{% hint style="info" %}
Port forwarding may be required on your firewall/router for inbound traffic to the Controller or NBI.
{% endhint %}

### Network Topology

![Network Topology](../../../_images/information-required-for-fanswifi-manager-151.png)

### Setting on Ruckus SmartZone / SCG

#### Step 1: Access SmartZone

1. Access the SmartZone management interface via a Web Browser.
2. Navigate to **Configure** > **Services & Profiles** > **Authentication**.

![SmartZone authentication settings](../../../_images/information-required-for-fanswifi-manager-152.png)

#### Step 2: Configuration: Authentication (RADIUS) Server

![Full authentication server view](../../../_images/information-required-for-fanswifi-manager-153.png)

1. Under the **Proxy (SZ Authenticator)** tab, click **Create New**.
   - **Name:** FansWiFi Radius
   - **Service Protocol:** RADIUS
   - **IP Address:** 103.6.85.240
   - **Port:** 1812
   - **Shared Secret:** social123
   - **Confirm Secret:** social123
2. Click **OK** to save.

![RADIUS authentication configuration](../../../_images/information-required-for-fanswifi-manager-154.png)

#### Step 3: Configuration: Accounting (RADIUS) Server

![Full accounting server view](../../../_images/information-required-for-fanswifi-manager-155.png)

##### Radius Accounting Server

1. Click **Accounting** in the left menu.
2. Under the **Proxy** tab, click **Create New**.
   - **Name:** FansWiFi Acct
   - **Service Protocol:** RADIUS Accounting
   - **IP Address:** 103.6.85.240
   - **Port:** 1813
   - **Shared Secret:** social123
3. Click **OK** to save the configuration.

![RADIUS accounting configuration](../../../_images/information-required-for-fanswifi-manager-156.png)

#### Step 4: Configure AP Zone and Hotspot Service

1. Select **Access Points** from the left menu.

![Access points list](../../../_images/information-required-for-fanswifi-manager-157.png)

2. Click the **+** icon to create an AP Zone:
   - **Zone Name:** FansWiFi
   - **AP Admin Logon ID:** admin
   - **AP Admin Password:** (Your AP Admin Password)
3. Click **OK** to save.

#### 4.1. Configure Hotspot (WISPr)

![Hotspot services menu](../../../_images/information-required-for-fanswifi-manager-158.png)

1. Go to **Hotspots & Portals** under **Services & Profiles**.
2. Select the **Hotspot (WISPr)** tab.
3. Select your created AP Zone and click **+ Create**.
4. Configure the following:
   - **Portal Name:** FansWiFi Portal
   - **Smart Client Support:** None
   - **Logon URL:** External
   - **Logon URL:** [https://connect-p.fanswifi.com/auth](https://connect-p.fanswifi.com/auth)
   - **Redirected MAC Format:** AA-BB-CC-DD-EE-FF
   - **Start Page:** [https://connect-p.fanswifi.com/auth/?res=success](https://connect-p.fanswifi.com/auth/?res=success)
   - **Session Timeout:** 1440
   - **Grace Period:** 60

   ![](../../../_images/ruckus_smart_zone_3.5_0.png)

##### Walled Garden Settings

{% hint style="info" %}
1. You may download the walled garden list .csv files on <br>
https://cdn.fanswifi.com/assets/ruckus/fanswifi_ruckus_smartzone_walled_garden.zip
2. Import the walled garden list corresponding to your enabled login methods
3. Input the local Google URL of your Country / Region

- Example:
   - EU: [www.google.eu](https://www.google.eu)
   - UK: [www.google.co.uk](https://www.google.co.uk)
   - Hong Kong: [www.google.com.hk](https://www.google.com.hk)
   - Japan: [www.google.co.jp](https://www.google.co.jp)
   - Taiwan: [www.google.com.tw](https://www.google.com.tw)
   - Thailand: [www.google.co.th](https://www.google.co.th)
   - Malaysia: [www.google.com.my](https://www.google.com.my)
   - Myanmar: [www.google.com.mm](https://www.google.com.mm)

{% endhint %}

##### Required
- [*.fanswifi.com](https://*.fanswifi.com)
- [*.cloudfront.net](https://*.cloudfront.net)

##### Optional (By Login Method)

**Facebook Login:**
- [*.facebook.com](https://*.facebook.com)
- [*.facebook.net](https://*.facebook.net)
- [*.fbcdn.net](https://*.fbcdn.net)
- [*.fbcdn.com](https://*.fbcdn.com)
- [*.akamaihd.net](https://*.akamaihd.net)
- [*.fbsbx.com](https://*.fbsbx.com)

**Weibo Login:**
- [*.weibo.com](https://*.weibo.com)
- [*.weibo.cn](https://*.weibo.cn)
- [*.sinaapp.com](https://*.sinaapp.com)
- [*.sina.com.cn](https://*.sina.com.cn)
- [*.sinajs.cn](https://*.sinajs.cn)

**Instagram Login:**
- [*.instagram.com](https://*.instagram.com)
- [*.akamaihd.net](https://*.akamaihd.net)
- [*.cdninstagram.com](https://*.cdninstagram.com)

**Twitter Login:**
- [*.twitter.com](https://*.twitter.com)
- [*.twimg.com](https://*.twimg.com)

**Video Login:**
- [*.akamaized.net](https://*.akamaized.net)
- [*.akamaihd.net](https://*.akamaihd.net)
- [ssl.google-analytics.com](https://ssl.google-analytics.com)
- [*.scorecardresearch.com](https://*.scorecardresearch.com)
- [*.vimeocdn.com](https://*.vimeocdn.com)
- [*.vimeo.com](https://*.vimeo.com)

- Click **OK** to save.

![](../../../_images/ruckus_smart_zone_3.5_1.png)

#### Step 5: Create WLAN and SSID

![Wireless LANs menu](../../../_images/information-required-for-fanswifi-manager-159.png)

1. Select **Wireless LANs** from the left menu.
2. Click **+ Create** and configure:
   - **Name:** FansWiFi Free WiFi
   - **SSID:** FansWiFi Free WiFi
   - **Zone:** FansWiFi
   - **WLAN Usage Type:** Hotspot (WISPr)
   - **Authentication Method:** Open
   - **Encryption Method:** None
   - **Hotspot (WISPr) Portal:** FansWiFi Portal
   - **Authentication Service:** FansWiFi Radius
   - **Accounting Service:** FansWiFi Acct

![WLAN configuration view 1](../../../_images/information-required-for-fanswifi-manager-160.png)

![WLAN configuration view 2](../../../_images/information-required-for-fanswifi-manager-161.png)

3. Under **Advanced Options**:
   - **Inactivity Timeout:** 1000 seconds
   - **Bypass CNA:** Disabled

![WLAN configuration view 3](../../../_images/information-required-for-fanswifi-manager-162.png)

![WLAN configuration view 4](../../../_images/information-required-for-fanswifi-manager-163.png)

#### Step 6: Set Northbound Interface (NBI) Password

1. Navigate to **System** > **General Settings** > **Northbound Interface**.
2. If you have previously set a NBI password, you may skip this step. If not, please enter a new password now and click **Apply**.
3. This password will be used in the controller setting later on.

![Northbound Interface settings](../../../_images/information-required-for-fanswifi-manager-164.png)

#### Step 7: Configure SmartZone in FansWiFi Admin Panel

1. Log in to the FansWiFi Admin Panel: [https://admin-p.fanswifi.com](https://admin-p.fanswifi.com)
2. Navigate to **Settings** > **Venues & Login Portals**.
3. Select your venue and click **Edit**.

![Admin panel venue list](../../../_images/information-required-for-fanswifi-manager-165.png)

4. Go to **WiFi** > **Controller** and configure:
   - **Ruckus SmartZone IP/Domain:** (Your controller address)
   - **Port Number:** (Your NBI port, default `9080`)
   - **Northbound Interface Password:** (The password from Step 6)
5. Click **Save**.

![Controller configuration details](../../../_images/information-required-for-fanswifi-manager-166.png)

{% hint style="danger" %}
**Exceptional Case: SmartZone / vSCG behinds Router / Firewall** <br>
If the SmartZone / vSCG is behind Router / Firewall, it is not directly accessible by FansWiFi Server. In this case, you need to configure port forwarding on your Router / Firewall to forward the port to the SmartZone / vSCG.
{% endhint %}

#### Step 8: Add AP to FansWiFi Admin Panel

- In the FansWiFi Admin Panel, go to **Settings** > **Hotspots** > **Add Hotspot**.
{% hint style="info" %}
   - **Venue:** Select your AP location.
   - **Hotspot Name:** Give the AP an identifiable name.
   - **AP Type:** Select **Ruckus SmartZone (formerly SCG)**.
   - **MAC Address:** Enter the unique MAC address of the AP.
{% endhint %}
- Click **Save**

![](../../../_images/ruckus_3.5_2.png)
