# Ruckus One Cloud Setup Guide

This guide provides instructions for configuring Ruckus One Cloud to work with the FansWiFi Manager platform.

## Information Required for FansWiFi Manager

- **MAC Addresses** of the APs

## Step 1: Access Ruckus One Cloud

1. Access the Ruckus One management interface via a Web Browser.
2. Click **Wi-Fi** on the left menu, then select **Wi-Fi Networks List**.

![Ruckus One WiFi Networks List](../../../_images/information-required-for-fanswifi-manager-319.png)

## Step 2: Create SSID

1. Select **Networks List** on the top menu.
2. Click **Add Wi-Fi Network** on the top right.
3. In the **Network Details** section, configure the following:
   - **Network Name:** (Your preferred SSID, e.g., "FansWiFi Free WiFi")
   - **Network Type:** Captive Portal
4. Click **Next**.

## Step 3: Captive Portal Configuration

1. In the **Portal Type** section:
   - **Portal Type:** 3rd Party Captive Portal (WISPr)
2. Click **Next**.
3. In the **Settings** section, configure:
   - **Portal Provider:** Custom Provider
   - **Provider Name:** FansWiFi
   - **Captive Portal:** `https://connect-p.fanswifi.com/auth`
   - **Redirect users to:** Enabled
   - **Redirect URL:** `https://connect-p.fanswifi.com/auth?res=success`
   - **Secure your network:** None
   - **Enable MAC auth bypass:** Enabled
   - **Enable encryption for users’ MAC and IP addresses:** Enabled
   - **Enable RUCKUS DHCP service:** Enabled
   - **Use Bypass Captive Network Assistant:** Disabled
   - **Walled Garden:** (Configure using the list below)

![Captive portal configuration](../../../_images/information-required-for-fanswifi-manager-320.png)

### Walled Garden List

> [!IMPORTANT]
> Add the following domains to your walled garden for proper portal functionality.

#### Required
- `* .fanswifi.com`

#### Optional (By Login Method)

**Facebook Login:**
- `* .facebook.com`
- `* .facebook.net`
- `* .fbcdn.net`
- `* .fbcdn.com`
- `* .akamaihd.net`
- `www.google.com`
- `* .doubleclick.net`
- `www.google.com.hk` (or local Google URL)

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

**LINE Login:**
- `* .line.me`
- `* .line-scdn.net`

**PayPal Login:**
- `* .paypal.com`
- `* .paypalobjects.com`
- `www.google-analytics.com`

**Video Login:**
- `* .akamaized.net`
- `* .akamaihd.net`
- `ssl.google-analytics.com`
- `* .scorecardresearch.com`
- `* .vimeocdn.com`
- `* .vimeo.com`

## Step 4: RADIUS Configuration

1. Under **Authentication Service**, select **Authenticate Connections**.
2. For **Authentication Server**, click **Add Server**:
   - **Server Name:** FansWiFi Radius
   - **IP Address:** 103.6.85.240
   - **Port:** 1812
   - **Shared Key:** social123
3. Click **Add**.
4. Enable **Accounting Service**.
5. For **Accounting Server**, click **Add Server**:
   - **Server Name:** FansWiFi Accounting
   - **IP Address:** 103.6.85.240
   - **Port:** 1813
   - **Shared Key:** social123
6. Click **Add**.
7. Click **Next**.
8. Select your **Venue** (e.g., "My-Venue") and click **Next**.
9. In the **Summary** section, click **Add** to create the network.

## Step 5: Add AP to FansWiFi Admin Panel

1. Log in to the FansWiFi Admin Panel.
2. Navigate to **Settings** > **Hotspots** > **Create**.
3. Configure the following:
   - **Venue:** Select your AP location.
   - **Hotspot Name:** Give the AP an identifiable name.
   - **AP Type:** Select **Ruckus SmartZone (formerly SCG)**.
   - **MAC Address:** Enter the unique MAC address of the AP.
4. Click **Create**.

![Hotspot creation view 1](../../../_images/information-required-for-fanswifi-manager-321.png)
![Hotspot creation view 2](../../../_images/information-required-for-fanswifi-manager-322.png)
