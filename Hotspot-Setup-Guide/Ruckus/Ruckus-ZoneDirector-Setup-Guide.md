## Information Required for FansWiFi Manager

- **MAC Addresses** of the APs

## Tested Firmware Version
- **Supported Version:** 9.8
- **NOT Supported:** 9.7 or below

{% hint style="warning" %}
Firmware 9.7 or below is confirmed NOT to work with Social Login. Please ensure your firmware is 9.8 or higher.
{% endhint %}

### FansWiFi Server / Controller Communication

The table below lists the ports that must be opened on your network firewall to ensure successful communication between the hotspot system and FansWiFi servers.

| Port Number | Protocol | Source | Destination | Direction | Purpose | Required By |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1812 / 1813 | UDP & TCP | Controller | FansWiFi RADIUS (103.6.85.240) | Outbound | AAA Auth & Accounting | All |
| 1700 / 3799 | UDP & TCP | FansWiFi RADIUS (103.6.85.240) | Controller | Inbound | RADIUS CoA Disconnect Messages | WeChat, Video, Advanced FB |

{% hint style="info" %}
Port forwarding may be required on your firewall/router depending on your network setup to allow inbound CoA traffic.
{% endhint %}

#### * Flow Diagram for Radius CoA DM (Disconnect Message) (Optional, for login method that require Temporary Internet Access only)

![RADIUS CoA DM Flow](../../../_images/information-required-for-fanswifi-manager-120.png)

**Security Notes:**
- Radius CoA Disconnect-Message requires the `Acct-Session-Id` of the connection session.
- `Acct-Session-Id` is reported by the WiFi Controller via RADIUS Accounting Messages and is unique for each session.
- FansWiFi RADIUS can only disconnect clients on SSIDs where it is configured as the Accounting Server.

**Example Disconnect-Message Packet:**
```text
Acct-Session-Id = "D91FE8E51802097" 
User-Name = "somebody" 
NAS-IP-Address = 10.0.0.1
```

### Topology

![Network Topology](../../../_images/information-required-for-fanswifi-manager-121.png)

#### Authentication Process Flow

![Authentication Process Flow](../../../_images/information-required-for-fanswifi-manager-122.png)

### Setting on Ruckus ZoneDirectors

#### Step 1: Configure the ZoneDirector

1. Access the ZoneDirector management interface via a Web Browser.
2. Click **Configure** to enter the configuration page.

![ZoneDirector configuration page](../../../_images/information-required-for-fanswifi-manager-123.png)

#### Step 2: Configure RADIUS (Authentication) Server

1. Select **AAA Servers** from the left menu.
2. Click **Create New** and configure the following:

{% hint style="info" %}
- **Name:** FansWiFi Radius
- **Type:** RADIUS
- **Backup RADIUS:** Off
- **IP Address:** `103.6.85.240`
- **Port:** `1812`
- **Shared Secret:** `social123`
{% endhint %}
- Click **OK** to save.

![RADIUS server configuration](../../../_images/information-required-for-fanswifi-manager-124.png)

#### Step 3: Configure RADIUS Accounting Server

1. Select **AAA Servers** from the left menu.
2. Click **Create New** and configure:

{% hint style="info" %}
- **Name:** FansWiFi Acct Radius
- **Type:** RADIUS Accounting
- **Backup RADIUS:** Off
- **IP Address:** `103.6.85.240`
- **Port:** `1813`
- **Shared Secret:** `social123`
{% endhint %}
- Click **OK** to save.

![RADIUS accounting server configuration](../../../_images/information-required-for-fanswifi-manager-125.png)

#### Step 4: Configure Hotspot Services

1. Select **Hotspot Services** from the left menu.

![Hotspot services menu](../../../_images/information-required-for-fanswifi-manager-126.png)

2. Click **Create New** and configure:
   - **Name:** FansWiFi
   - **Login Page:** [https://connect-p.fanswifi.com/auth](https://connect-p.fanswifi.com/auth)
   - **Start Page:** [https://connect-p.fanswifi.com/auth](https://connect-p.fanswifi.com/auth)
   - **User Session:** (set it if your FansWiFi Admin Panel has session timeout & daily quota enabled)
      - **Example**: Session Timeout / Daily Quota: 60 minutes
      - **Setting**:
         - **Session Timeout:** 60 minutes
         - **Grace Period:** 60 minutes 

   - **Authentication Server:** FansWiFi Radius
   - **Accounting Server:** FansWiFi Acct Radius
   - **Encryption Method:** None
   - **Advanced Option:**
      - **Inactive Timeout:** 60 minutes

### Walled Garden List

#### Walled Garden List (required)
{% hint style="info" %}
- `* .fanswifi.com`
{% endhint %}

#### FWalled Garden List (Optional, you may skip this if there is no Facebook Login Enabled):**

{% hint style="info" %}
- `* .facebook.com`
- `* .facebook.net`
- `* .fbcdn.net`
- `* .fbcdn.com`
- `* .akamaihd.net`
- `* .fbsbx.com`
{% endhint %}

#### Walled Garden List (Optional, you may skip this if there is no Weibo Login Enabled)

{% hint style="info" %}
- `* .weibo.com`
- `* .weibo.cn`
- `* .sinaapp.com`
- `* .sina.com.cn`
- `* .sinajs.cn`
{% endhint %}

#### Walled Garden List (Optional, you may skip this if there is no Instagram Login Enabled)

{% hint style="info" %}
- `* .instagram.com`
- `* .akamaihd.net`
- `* .cdninstagram.com`
{% endhint %}

#### Walled Garden List (Optional, you may skip this if there is no Twitter Login Enabled)

{% hint style="info" %}
- `* .twitter.com`
- `* .twimg.com`
{% endhint %}

#### Walled Garden List (Optional, you may skip this if there is no Video Login Enabled)

{% hint style="info" %}
- `* .akamaized.net`
- `* .akamaihd.net`
- `ssl.google-analytics.com`
- `* .scorecardresearch.com`
- `* .vimeocdn.com`
- `* .vimeo.com`
{% endhint %}

- Click **OK** to save.

![Hotspot service configuration details](../../../_images/information-required-for-fanswifi-manager-127.png)

#### Step 5: Create WLAN and SSID

1. Select **WLANs** from the left menu.
2. Click **Create New** and configure:
   - **Name:** FansWiFi
   - **ESSID:** FansWiFi
   - **WLAN Usage Type:** Hotspot Service (WISPr)
   - **Authentication Method:** Open
   - **Encryption Method:** Open
   - **Hotspot Service:** FansWiFi
   - **Inactivity Timeout:** 60 minutes
3. Click **OK** to save.

![WLAN creation details](../../../_images/information-required-for-fanswifi-manager-128.png)

#### Step 6: Configure ZoneDirector in FansWiFi Admin Panel

{% hint style="warning" %}
Please send this information to your FansWiFi account manager

(required for Advanced Login Method (e.g. WeChat or WhatsApp Login) ONLY, you may skip this step if there is no Advanced Login Method Enabled)

FansWiFi Admin Panel (Setting > Venue Setting)
{% endhint %}

#### FansWiFi Admin Panel (Setting > Venue Setting)

![FansWiFi Admin Panel venue settings](../../../_images/information-required-for-fanswifi-manager-129.png)

1. Provide the following to FansWiFi:
   - **Public IP Address** or **Domain Name** of the ZoneDirector.
   - **RADIUS CoA Port:** `3799`

![RADIUS CoA settings view](../../../_images/information-required-for-fanswifi-manager-130.png)

{% hint style="danger" %}
Exceptional Case: ZoneDirector behinds Router / Firewall

If the ZoneDirector is behind Router / Firewall, it is not directly accessible via FansWiFi Radius Server via Internet. In this case, you need to configure port forwarding on your Router / Firewall to forward the port to the ZoneDirector.
{% endhint %}

![Port forwarding diagram](../../../_images/information-required-for-fanswifi-manager-131.png)


**Example Configuration:**
Assume the Router's Public IP is `1.1.1.1`.

1. **Port Forwarding:** Forward a chosen port (e.g., `50000`) to the ZoneDirector CoA Port (default `3799`).
   {% hint style="info" %}
   - **Inbound Port:** `50000`
   - **Destination IP:** `192.168.1.100` (ZoneDirector IP)
   - **Destination Port:** `3799`
   {% endhint %}

2. **Send below information to FansWiFi:**
   {% hint style="info" %}
   - **Public IP:** `1.1.1.1` or Domain Name.
   - **RADIUS CoA Port:** `50000`.
   {% endhint %}

#### Admin Panel Final Settings

![FansWiFi Admin Panel final settings](../../../_images/information-required-for-fanswifi-manager-132.png)

#### Step 7: Add AP to FansWiFi Admin Panel

1. Log in to the FansWiFi Admin Panel.
2. Navigate to **Settings** > **Hotspots** > **Add Hotspot**.

{% hint style="info" %}
- **Venue:** Select your AP location.
- **Hotspot Name:** Give the AP an identifiable name.
- **AP Type:** Select **Ruckus ZoneDirector**.
- **MAC Address:** Enter the unique MAC address of the AP.
{% endhint %}

- Click **Save**.

![Hotspot creation in FansWiFi](../../../_images/information-required-for-fanswifi-manager-133.png)

​

## FAQ

### 1. How do I deauthorize a user to reset the login page?

- During testing, you may want to try different login methods.
- But after user authorized in any login method, captive portal will not be shown again before the expiry of session time. 
- If you may want to bring the user back to the captive portal page for testing different login methods, you will need to unauthorize the WiFi user.

| WiFi User Logout trigger by: | WiFi User's Device<br>(usually, access a logout url on browser) | Controller Web Admin Interface |
|---|---|---|
|  | Not Available<br><br>Last Testing: 11-9-2017 | Available<br><br>Last Testing: 11-9-2017 |


**WiFi User Logout trigger by:**
**Controller**

1. Click the **Monitor** tab.
2. Select **Wireless Clients** on the left menu.
3. Under **Active Clients**, select the device and click the **red cross** on the corresponding row.

![Manual deauthorization in ZoneDirector](../../../_images/information-required-for-fanswifi-manager-134.png)
