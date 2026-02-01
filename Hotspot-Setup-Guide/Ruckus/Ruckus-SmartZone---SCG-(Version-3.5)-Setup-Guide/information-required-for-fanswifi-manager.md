# Ruckus SmartZone / SCG (v3.5) Setup Guide

This guide provides instructions for configuring Ruckus SmartZone / SCG (Version 3.5) to work with the FansWiFi Manager platform.

## Information Required for FansWiFi Manager

- **MAC Addresses** of the APs

### FansWiFi Server / Controller Communication

The table below lists the ports that must be opened on your network firewall to ensure successful communication between the hotspot system and FansWiFi servers.

| Port Number | Protocol | Source | Destination | Direction | Purpose | Required By |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| 1812 / 1813 | UDP & TCP | Controller | FansWiFi RADIUS (103.6.85.240) | Outbound | AAA Auth & Accounting | All |
| 1700 / 3799 | UDP & TCP | FansWiFi RADIUS (103.6.85.240) | Controller | Inbound | RADIUS CoA Messages | WeChat, Video, Advanced FB |
| 8443 / 9443 | TCP | FansWiFi | Controller NBI | Inbound | Northbound API Access | All |

> [!NOTE]
> Port forwarding may be required on your firewall/router for inbound traffic to the Controller or NBI.

## Network Topology

![Network Topology](../../../_images/information-required-for-fanswifi-manager-151.png)

## Step 1: Access SmartZone

1. Access the SmartZone management interface via a Web Browser.
2. Navigate to **Configure** > **Services & Profiles** > **Authentication**.

![SmartZone authentication settings](../../../_images/information-required-for-fanswifi-manager-152.png)

## Step 2: Configure RADIUS Authentication Server

![Full authentication server view](../../../_images/information-required-for-fanswifi-manager-153.png)

1. Under the **Proxy (SZ Authenticator)** tab, click **Create New**.
   - **Name:** FansWiFi Radius
   - **Service Protocol:** RADIUS
   - **IP Address:** 103.6.85.240
   - **Port:** 1812
   - **Shared Secret:** social123
2. Click **OK** to save.

![RADIUS authentication configuration](../../../_images/information-required-for-fanswifi-manager-154.png)

## Step 3: Configure RADIUS Accounting Server

![Full accounting server view](../../../_images/information-required-for-fanswifi-manager-155.png)

1. Click **Accounting** in the left menu.
2. Under the **Proxy** tab, click **Create New**.
   - **Name:** FansWiFi Acct
   - **Service Protocol:** RADIUS Accounting
   - **IP Address:** 103.6.85.240
   - **Port:** 1813
   - **Shared Secret:** social123
3. Click **OK** to save.

![RADIUS accounting configuration](../../../_images/information-required-for-fanswifi-manager-156.png)

## Step 4: Configure AP Zone and Hotspot Service

1. Select **Access Points** from the left menu.

![Access points list](../../../_images/information-required-for-fanswifi-manager-157.png)

2. Click the **+** icon to create an AP Zone:
   - **Zone Name:** FansWiFi
   - **AP Admin Logon ID:** admin
   - **AP Admin Password:** (Your AP Admin Password)
3. Click **OK** to save.

### 4.1. Configure Hotspot (WISPr)

![Hotspot services menu](../../../_images/information-required-for-fanswifi-manager-158.png)

1. Go to **Hotspots & Portals** under **Services & Profiles**.
2. Select the **Hotspot (WISPr)** tab.
3. Select your created AP Zone and click **+ Create**.
4. Configure the following:
   - **Portal Name:** FansWiFi Portal
   - **Smart Client Support:** None
   - **Logon URL:** External
   - **Logon URL:** `https://connect-p.fanswifi.com/auth`
   - **Redirected MAC Format:** AA-BB-CC-DD-EE-FF
   - **Start Page:** `https://connect-p.fanswifi.com/auth/?res=success`
   - **Session Timeout:** 1440
   - **Grace Period:** 60

### Walled Garden Settings

> [!IMPORTANT]
> Add the following domains to the walled garden. You can download a pre-configured .csv list [here](https://cdn.fanswifi.com/assets/ruckus/fanswifi_ruckus_smartzone_walled_garden.zip).

#### Required
- `* .fanswifi.com`
- `* .cloudfront.net`

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

5. Click **OK** to save.

## Step 5: Create WLAN and SSID

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

## Step 6: Set Northbound Interface (NBI) Password

1. Navigate to **System** > **General Settings** > **Northbound Interface**.
2. If not previously set, enter a new password and click **Apply**.
3. This password will be needed for the FansWiFi Admin Panel settings.

![Northbound Interface settings](../../../_images/information-required-for-fanswifi-manager-164.png)

## Step 7: Configure SmartZone in FansWiFi Admin Panel

1. Log in to the FansWiFi Admin Panel.
2. Navigate to **Settings** > **Venues & Login Portals**.
3. Select your venue and click **Edit**.

![Admin panel venue list](../../../_images/information-required-for-fanswifi-manager-165.png)

4. Go to **WiFi** > **Controller** and configure:
   - **Ruckus SmartZone IP/Domain:** (Your controller address)
   - **Port Number:** (Your NBI port, default `9080`)
   - **Northbound Interface Password:** (The password from Step 6)
5. Click **Save**.

![Controller configuration details](../../../_images/information-required-for-fanswifi-manager-166.png)

> [!NOTE]
> If the SmartZone is behind a firewall, you must configure port forwarding for the NBI port.

## Step 8: Add AP to FansWiFi Admin Panel

1. In the FansWiFi Admin Panel, go to **Settings** > **Hotspots** > **Add Hotspot**.
2. Configure:
   - **Venue:** Select your AP location.
   - **Hotspot Name:** Give the AP an identifiable name.
   - **AP Type:** Select **Ruckus SmartZone (formerly SCG)**.
   - **MAC Address:** Enter the unique MAC address of the AP.
3. Click **Save**.
