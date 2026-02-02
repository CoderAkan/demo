# Aruba Instant (IAP) Setup Guide

This guide provides instructions for configuring Aruba Instant Access Points (APs) to work with the FansWiFi Manager platform.

## Information Required for FansWiFi Manager

- **MAC Addresses** of the APs

## Tested Model and Firmware Version

- **Model:** IAP-105
- **Firmware Version:** 6.4.4.4-4.2.3.2_54910

## Settings on Aruba IAP

## Step 1: Configure the Aruba Instant (IAP)

- Access the Aruba Instant (IAP) management interface via a Web Browser.
- Under **Networks**, click **New** to start the configuration.

![WLAN configuration start](../../../_images/information-required-for-fanswifi-manager-259.png)

- Under **WLAN Settings**, configure the following:
  - **Name:** FansWiFi Free WiFi (or your preferred SSID)
  - **Primary usage:** Guest
- Click **Next** to save and proceed.

![WLAN settings configuration](../../../_images/information-required-for-fanswifi-manager-260.png)

- Under **VLAN**, configure:
  - **Client IP assignment:** Network assigned
  - **Client VLAN assignment:** Static
  - **VLAN ID:** 1
- Click **Next** to save and proceed.

![VLAN settings configuration](../../../_images/information-required-for-fanswifi-manager-261.png)

- Under **Security**, set Splash page type to **External**.

![Security splash page settings](../../../_images/information-required-for-fanswifi-manager-262.png)

- Under **Captive portal profile**, click **New** to set up the portal.

![Captive portal profile setup](../../../_images/information-required-for-fanswifi-manager-263.png)

- In the setup box, configure the following:
  - **Name:** FansWiFi_cp
  - **Type:** RADIUS Authentication
  - **IP or hostname:** connect-p.fanswifi.com
  - **URL:** /auth
  - **Port:** 443
  - **Use https:** Enabled
  - **Captive Portal failure:** Deny Internet
  - **Redirect URL:**
    - For redirect method: `https://connect-p.fanswifi.com/auth/?res=success&id=aruba-iap`
    - For XML API method: `https://connect-p.fanswifi.com/auth/?res=success&id=aruba-xml-api`
- Click **OK** to save.

![Captive portal configuration](../../../_images/information-required-for-fanswifi-manager-264.png)

- Under **Auth server 1**, click **New** to set up the RADIUS server.

![Auth server configuration](../../../_images/information-required-for-fanswifi-manager-265.png)

- In the setup box, configure the First Server:
  - **Server type:** RADIUS
  - **Name:** FansWiFi-rad1
  - **IP address:** 103.6.85.240
  - **Auth port:** 1812
  - **Acct port:** 1813
  - **Shared key:** social123
- Click **OK** to save.

![RADIUS server setup](../../../_images/information-required-for-fanswifi-manager-266.png)

- Configure the remaining security settings:
  - **Accounting:** Use authentication servers
  - **Accounting mode:** Authentication
  - **Accounting interval:** 3 min.
  - **Blacklisting:** Disabled
- Click **Next** to proceed.

![Additional security settings](../../../_images/information-required-for-fanswifi-manager-267.png)

- Under **Access**, select **Role-based** and click **New** under roles.
- Name the role: **FansWiFi_Preauth**.

![Pre-authentication role creation](../../../_images/information-required-for-fanswifi-manager-268.png)

- Click **New** under **Access Rules** and configure:
  - **Rule type:** Access control
  - **Service:** Network - any
  - **Action:** Allow
  - **Destination:** to domain name
  - **Domain name:** (Insert domain name from the Walled Garden list below)
- Click **OK** to save each rule.

![Access rule configuration](../../../_images/information-required-for-fanswifi-manager-269.png)

### Walled Garden List

> [!IMPORTANT]
> The following domains must be added to the walled garden for the login portal to function correctly.

#### Required
- `* .fanswifi.com`

#### Optional (based on enabled login methods)

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

![Walled garden configuration summary](../../../_images/information-required-for-fanswifi-manager-270.png)

- Set **Assign pre-authentication role** to **FansWiFi_Preauth** and click **Finish**.

## Step 2: Add XML API Server (Optional - for XML API method)

- a. Navigate to **More** > **Services**.

![Navigate to services](../../../_images/information-required-for-fanswifi-manager-271.png)

- b. Go to **Network Integration**.
- c. Under **XML API Server**, click **New** and configure:
  - **Name:** (Use one of the following IP addresses)
    - 52.220.226.90
    - 52.220.206.125
    - 52.77.30.253
    - 52.220.219.128
    - 52.220.215.219
    - 52.220.208.185
  - **Subnet:** (Same as Name)
  - **Mask:** 255.255.255.0
  - **Passphrase:** aruba123
- d. Click **OK** to add the server.

![XML API Server configuration](../../../_images/information-required-for-fanswifi-manager-272.png)
![XML API Server list view](../../../_images/information-required-for-fanswifi-manager-273.png)

- e. Click **OK** to save.

![Finalize XML API settings](../../../_images/information-required-for-fanswifi-manager-274.png)

## Step 3: Configure Aruba IAP Address in FansWiFi Admin Panel

> [!NOTE]
> Please send this information to your FansWiFi account manager. Required for advanced login methods (e.g., WeChat, WhatsApp).

### FansWiFi Admin Panel (Setting > Venue Setting)

![Admin panel venue settings](../../../_images/information-required-for-fanswifi-manager-275.png)

1. Provide the following to FansWiFi:
   - **Public IP Address** or **Domain Name** of the Mobility Controller
   - **Radius CoA Port:** 3799

![RADIUS CoA configuration](../../../_images/information-required-for-fanswifi-manager-276.png)

### Controller behind Router/Firewall

If the controller is behind a router or firewall, you must configure port forwarding to make it accessible.

![Controller behind firewall diagram](../../../_images/information-required-for-fanswifi-manager-277.png)

**Example Configuration:**
Assume the Router's Public IP is `1.1.1.1`.

1. **Port Forwarding:** Forward a chosen port (e.g., `50000`) to the Controller's CoA Port (default `3799`).
   - **Inbound Port:** 50000
   - **Destination IP:** 192.168.1.100 (Controller IP)
   - **Destination Port:** 3799

2. **Information to provide FansWiFi:**
   - **Public IP:** 1.1.1.1 (or Domain Name)
   - **Radius CoA Port:** 50000

### Admin Panel Settings

![Admin panel settings view](../../../_images/information-required-for-fanswifi-manager-278.png)

## Step 4: Add AP to FansWiFi Admin Panel

- Login to the FansWiFi Admin Panel.
- Navigate to **Settings** > **Hotspots** > **Create**.
- Configure the following:
  - **Venue:** Select your AP location.
  - **Hotspot Name:** Give the AP a unique name.
  - **AP Type:** Select **Aruba Instant AP (IAP)**.
  - **MAC Address:** Enter the unique MAC address of the AP.
- Click **Create**.

![Hotspot creation view 1](../../../_images/information-required-for-fanswifi-manager-279.png)
![Hotspot creation view 2](../../../_images/information-required-for-fanswifi-manager-280.png)

## FAQ

### 1. How do I deauthorize a user to reset the login page?

During testing, you may need to clear an authorized session to test different login methods.

**Option A: WiFi User device**
1. Open a browser on the device.
2. Navigate to: `https://securelogin.arubanetworks.com/auth/logout.html`

![Logout page view](../../../_images/information-required-for-fanswifi-manager-281.png)

**Option B: Controller Interface**
1. Select the connected client device.

![Client list in controller](../../../_images/information-required-for-fanswifi-manager-282.png)

2. Click the **'x'** button next to the access point.

![Disconnect client button](../../../_images/information-required-for-fanswifi-manager-283.png)

3. Confirm by clicking **Disconnect Now**.

![Confirm disconnection](../../../_images/information-required-for-fanswifi-manager-284.png)
