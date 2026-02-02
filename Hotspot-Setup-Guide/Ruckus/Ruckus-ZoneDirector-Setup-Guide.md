# Ruckus ZoneDirector Setup Guide

This guide provides instructions for configuring Ruckus ZoneDirector to work with the FansWiFi Manager platform.

## Information Required for FansWiFi Manager

- **MAC Addresses** of the APs

## Tested Firmware Version
- **Supported Version:** 9.8
- **NOT Supported:** 9.7 or below

> [!WARNING]
> Firmware 9.7 or below is confirmed NOT to work with Social Login. Please ensure your firmware is 9.8 or higher.

## FansWiFi Server / Controller Communication

The table below lists the ports that must be opened on your network firewall to ensure successful communication between the hotspot system and FansWiFi servers.

| Port Number | Protocol | Source | Destination | Direction | Purpose | Required By |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1812 / 1813 | UDP & TCP | Controller | FansWiFi RADIUS (103.6.85.240) | Outbound | AAA Auth & Accounting | All |
| 1700 / 3799 | UDP & TCP | FansWiFi RADIUS (103.6.85.240) | Controller | Inbound | RADIUS CoA Disconnect Messages | WeChat, Video, Advanced FB |

> [!NOTE]
> Port forwarding may be required on your firewall/router depending on your network setup to allow inbound CoA traffic.

### RADIUS CoA Disconnect Message Flow (Optional)

![RADIUS CoA DM Flow](../../../_images/information-required-for-fanswifi-manager-120.png)

**Security Notes:**
- Radius CoA Disconnect-Message requires the `Acct-Session-Id` of the connection session.
- `Acct-Session-Id` is reported by the WiFi Controller via RADIUS Accounting Messages and is unique for each session.
- FansWiFi RADIUS can only disconnect clients on SSIDs where it is configured as the Accounting Server.

**Example Disconnect-Message Packet:**
```text
Acct-Session-Id = "D91FE8E51802097" User-Name = "somebody" NAS-IP-Address = 10.0.0.1
```

## Topology

![Network Topology](../../../_images/information-required-for-fanswifi-manager-121.png)

### Authentication Process Flow

![Authentication Process Flow](../../../_images/information-required-for-fanswifi-manager-122.png)

## Step 1: Access ZoneDirector

1. Access the ZoneDirector management interface via a Web Browser.
2. Click **Configure** to enter the configuration page.

![ZoneDirector configuration page](../../../_images/information-required-for-fanswifi-manager-123.png)

## Step 2: Configure RADIUS Server

1. Select **AAA Servers** from the left menu.
2. Click **Create New** and configure the following:
   - **Name:** FansWiFi Radius
   - **Type:** RADIUS
   - **Backup RADIUS:** Off
   - **IP Address:** 103.6.85.240
   - **Port:** 1812
   - **Shared Secret:** social123
3. Click **OK** to save.

![RADIUS server configuration](../../../_images/information-required-for-fanswifi-manager-124.png)

## Step 3: Configure RADIUS Accounting Server

1. Select **AAA Servers** from the left menu.
2. Click **Create New** and configure:
   - **Name:** FansWiFi Acct Radius
   - **Type:** RADIUS Accounting
   - **Backup RADIUS:** Off
   - **IP Address:** 103.6.85.240
   - **Port:** 1813
   - **Shared Secret:** social123
3. Click **OK** to save.

![RADIUS accounting server configuration](../../../_images/information-required-for-fanswifi-manager-125.png)

## Step 4: Configure Hotspot Services

1. Select **Hotspot Services** from the left menu.

![Hotspot services menu](../../../_images/information-required-for-fanswifi-manager-126.png)

2. Click **Create New** and configure:
   - **Name:** FansWiFi
   - **Login Page:** `https://connect-p.fanswifi.com/auth`
   - **Start Page:** `https://connect-p.fanswifi.com/auth`
   - **Authentication Server:** FansWiFi Radius
   - **Accounting Server:** FansWiFi Acct Radius
   - **Encryption Method:** None
   - **Inactive Timeout:** 60 minutes

### Walled Garden List

> [!IMPORTANT]
> The following domains must be added to the walled garden.

#### Required
- `* .fanswifi.com`

#### Optional (By Login Method)

**Facebook Login:**
- `* .facebook.com`
- `* .facebook.net`
- `* .fbcdn.net`
- `* .fbcdn.com`
- `* .akamaihd.net`
- `* .fbsbx.com`

**Weibo Login:**
- `* .weibo.com`
- `* .weibo.cn`
- `* .sinaapp.com`
- `* .sina.com.cn`
- `* .sinajs.cn`

**Instagram Login:**
- `* .instagram.com`
- `* .akamaihd.net`
- `* .cdninstagram.com`

**Twitter Login:**
- `* .twitter.com`
- `* .twimg.com`

**Video Login:**
- `* .akamaized.net`
- `* .akamaihd.net`
- `ssl.google-analytics.com`
- `* .scorecardresearch.com`
- `* .vimeocdn.com`
- `* .vimeo.com`

3. Click **OK** to save.

![Hotspot service configuration details](../../../_images/information-required-for-fanswifi-manager-127.png)

## Step 5: Create WLAN and SSID

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

## Step 6: Configure ZoneDirector in FansWiFi Admin Panel

> [!NOTE]
> Please provide the following information to your FansWiFi account manager. This is required for advanced login methods (e.g., WeChat, WhatsApp).

### FansWiFi Admin Panel (Setting > Venue Setting)

![FansWiFi Admin Panel venue settings](../../../_images/information-required-for-fanswifi-manager-129.png)

1. Provide the following to FansWiFi:
   - **Public IP Address** or **Domain Name** of the ZoneDirector.
   - **RADIUS CoA Port:** 3799

![RADIUS CoA settings view](../../../_images/information-required-for-fanswifi-manager-130.png)

### ZoneDirector behind Router/Firewall

If the ZoneDirector is behind a router/firewall, configure port forwarding to make it accessible.

![Port forwarding diagram](../../../_images/information-required-for-fanswifi-manager-131.png)

**Example Configuration:**
Assume the Router's Public IP is `1.1.1.1`.

1. **Port Forwarding:** Forward a chosen port (e.g., `50000`) to the ZoneDirector CoA Port (default `3799`).
   - **Inbound Port:** 50000
   - **Destination IP:** 192.168.1.100 (ZoneDirector IP)
   - **Destination Port:** 3799

2. **Information to provide FansWiFi:**
   - **Public IP:** 1.1.1.1 or Domain Name.
   - **RADIUS CoA Port:** 50000.

### Admin Panel Final Settings

![FansWiFi Admin Panel final settings](../../../_images/information-required-for-fanswifi-manager-132.png)

## Step 7: Add AP to FansWiFi Admin Panel

1. Log in to the FansWiFi Admin Panel.
2. Navigate to **Settings** > **Hotspots** > **Add Hotspot**.
3. Configure:
   - **Venue:** Select your AP location.
   - **Hotspot Name:** Give the AP an identifiable name.
   - **AP Type:** Select **Ruckus ZoneDirector**.
   - **MAC Address:** Enter the unique MAC address of the AP.
4. Click **Save**.

![Hotspot creation in FansWiFi](../../../_images/information-required-for-fanswifi-manager-133.png)

​

## FAQ

### 1. How do I deauthorize a user to reset the login page?

During testing, you may need to clear an authorized session to test different login methods.

**Option A: Controller Interface**
1. Click the **Monitor** tab.
2. Select **Wireless Clients** on the left menu.
3. Under **Active Clients**, select the device and click the **red cross** on the corresponding row.

![Manual deauthorization in ZoneDirector](../../../_images/information-required-for-fanswifi-manager-134.png)
