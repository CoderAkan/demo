# Ruckus Unleashed Setup Guide

This guide provides instructions for configuring Ruckus Unleashed to work with the FansWiFi Manager platform.

## Information Required for FansWiFi Manager

- **MAC Addresses** of the APs

## Tested Firmware Version
- **Version:** 200.3.9.13.228

## Step 1: Access Ruckus Unleashed

1. Access the Ruckus Unleashed management interface via a Web Browser.

![Unleashed dashboard](../../../_images/information-required-for-fanswifi-manager-108.png)

## Step 2: Configure Authentication Servers (RADIUS)

1. Click **Admin & Services** in the top menu.

![Admin & Services menu](../../../_images/information-required-for-fanswifi-manager-109.png)

2. Select **Services** > **AAA Servers** from the left menu.
3. Click **Create New** under **Authentication Servers** and configure:
   - **Name:** FansWiFi Radius
   - **Type:** RADIUS
   - **Auth Method:** PAP
   - **Backup RADIUS:** Enabled

**First Server:**
- **IP Address:** 103.6.85.240
- **Port:** 1812
- **Shared Secret:** social123

**Second Server:**
- **IP Address:** 52.221.175.51
- **Port:** 1812
- **Shared Secret:** social123

4. Click **OK** to save.

![RADIUS server configuration](../../../_images/information-required-for-fanswifi-manager-110.png)

## Step 4: Configure Hotspot Services

1. Select **Hotspot Services** from the left menu.

![Hotspot services menu](../../../_images/information-required-for-fanswifi-manager-111.png)

2. Click **Create New** and configure:

**General Tab:**
- **Name:** FansWiFi
- **Login Page:** `https://connect-p.fanswifi.com/auth`
- **Start Page:** `https://connect-p.fanswifi.com/auth`
- **User Session:** (Configure only if your FansWiFi Admin Panel has session timeouts enabled)

![Hotspot general settings](../../../_images/information-required-for-fanswifi-manager-112.png)

**Authentication Tab:**
- **Authentication Server:** FansWiFi Radius
- **Isolate wireless client traffic:** Enabled

![Hotspot authentication settings](../../../_images/information-required-for-fanswifi-manager-113.png)

**Walled Garden Tab:**

> [!IMPORTANT]
> Add the following domains to the walled garden.

#### Required
- `* .fanswifi.com`

#### Optional (By Login Method)

**Facebook Login:**
- `* .facebook.com`
- `* .facebook.net`
- `* .fbcdn.net`
- `* .fbcdn.com`
- `* .akamaihd.net`
- `www.google.com` (or local Google URL)

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

![Hotspot walled garden summary](../../../_images/information-required-for-fanswifi-manager-114.png)


## Step 5: Create WLAN and SSID

1. Select **WiFi Networks** in the top menu.

![WiFi Networks menu](../../../_images/information-required-for-fanswifi-manager-115.png)

2. Click **Create** and configure:
   - **Name:** FansWiFi
   - **Usage Type:** Hotspot Service
   - **Hotspot Service:** FansWiFi
3. Under **Advanced Configuration** > **Others**:
   - **Inactivity Timeout:** 60 minutes
4. Click **OK**.

![WLAN creation details](../../../_images/information-required-for-fanswifi-manager-116.png)

## Step 6: Get AP MAC Address

1. In the Unleashed Admin Panel, click **Access Points**.
2. Select the relevant AP and click **Edit** to find the MAC address.

![Access Point MAC address check](../../../_images/information-required-for-fanswifi-manager-117.png)

## Step 7: Add AP to FansWiFi Admin Panel

1. Log in to the FansWiFi Admin Panel.
2. Navigate to **Settings** > **Hotspots** > **Add Hotspot**.
3. Configure the following:
   - **Venue:** Select your AP location.
   - **Hotspot Name:** Give the AP an identifiable name.
   - **AP Type:** Select **Ruckus Unleashed**.
   - **MAC Address:** Enter the AP MAC address.
4. Click **Save**.

![Hotspot creation view](../../../_images/information-required-for-fanswifi-manager-118.png)

## FAQ

### 1. How do I deauthorize a user to reset the login page?

During testing, you may need to clear an authorized session to test different login methods.

**Option A: Controller Interface**
1. Click the **Client** header.
2. Select the device and click **Delete**.

![Manual client deletion in Unleashed](../../../_images/information-required-for-fanswifi-manager-119.png)
