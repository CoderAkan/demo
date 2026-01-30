# Information required for FansWiFi Manager


# Information required for FansWiFi Manager

- Mac Addresses of the APs

## Tested Firmware Version

- Version:**200.3.9.13.228**

# Setting on Ruckus Unleashed

## Step 1: Configure the Unleashed

- a. Access the Unleashed Admin Panel by opening a Web Browser

![](../../../_images/information-required-for-fanswifi-manager-108.png)

## Step 2: Configuration: Authentication Servers (AAA Servers)

**Radius Server**

- a. Click “Admin & Services” header

![](../../../_images/information-required-for-fanswifi-manager-109.png)

- b. Select “Services” then “AAA Servers” on the left menu
- c. Click “Create New” under “Authentication Servers” with below settings

- i.**Name:** FansWiFi Radius
- ii.**Type:** RADIUS
- iii.**Auth Method:** PAP
- iv.**Backup RADIUS:** Enabled

- First Server:

- **IP Address:** 103.6.85.240
- **Port:** 1812
- **Shared Secret:** social123
- **Confirm Secret:** social123

- Second Server:

- **IP Address:** 52.221.175.51
- **Port:** 1812
- **Shared Secret:** social123
- **Confirm Secret:** social123

- d. Click “OK” to save the configuration

![](../../../_images/information-required-for-fanswifi-manager-110.png)

## Step 4: Configuration: Hotspot Services

a. Select “Hotspot Services” from the left menu

![](../../../_images/information-required-for-fanswifi-manager-111.png)

b. Click “Create New” with below settings

- Under**General**tab:
- i.**Name:** FansWiFi
- ii.**WISPr Smart Client Support:** None
- iii.**Login Page:** [https://connect-p.fanswifi.com/auth](https://support.fanswifi.com/hotspot-setup-guide/ruckus/ruckus-unleashed-setup-guide#)
- iv.**Start Page (redirect to the following URL):** 
​[https://connect-p.fanswifi.com/auth](https://support.fanswifi.com/hotspot-setup-guide/ruckus/ruckus-unleashed-setup-guide#)
- v.**User Session:** (set it if your FansWiFi Admin Panel has session timeout & daily quota enabled)

- **Example:** Session Timeout / Daily Quota: 60 minute
- **Setting:**

- **Session Timeout:** 60 Minutes
- **Grace Period:** 60 Minutes

- v.**Intrusion Prevention:** Disabled

![](../../../_images/information-required-for-fanswifi-manager-112.png)

- Under**Authentication**tab:
- vi.**Authentication Server:** FansWiFi Radius
- vii.**Isolate wireless client traffic from other clients on the same AP:** Enabled

![](../../../_images/information-required-for-fanswifi-manager-113.png)

- Under**Walled Garden**tab, enter the following entries:
- viii.**Walled Garden List (required)**

- 1.[fanswifi.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- ix.**Walled Garden List**(Optional, you may skip this if there is no Facebook Login Enabled)

- 1.[facebook.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 2.[facebook.net](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 3.[fbcdn.net](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 4.[fbcdn.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 5.[Akamaihd.net](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 6.[www.google.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 7.[doubleclick.net](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 8.[www.google.com.hk](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)(Local Google URL of your Country / Region)

- Example:

- i. EU:[www.google.eu](http://www.google.eu/)
- ii. UK:[www.google.co.uk](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- iii. Hong Kong:[www.google.com.hk](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- iv. Japan:[www.google.co.jp](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- v. Taiwan:[www.google.com.tw](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- vi. Thailand:[www.google.co.th](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- vi. Malaysia:[www.google.com.my](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- viii. Myanmar:[www.google.com.mm](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- x.**Walled Garden List**(Optional, you may skip this if there is no Weibo Login Enabled)

- 1.[weibo.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 2.[weibo.cn](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 3.[sinaapp.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 4.[sina.com.cn](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 5.[sinajs.cn](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- xi.**Walled Garden List**(Optional, you may skip this if there is no Instagram Login Enabled))

- 1.[instagram.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 2.[akamaihd.net](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 3.[cdninstagram.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- xii.**Walled Garden List**(Optional, you may skip this if there is no Twitter Login Enabled)

- 1.[twitter.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 2.[twimg.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- xiii.**Walled Garden List**(Optional, you may skip this if there is no Video Login Enabled)

- 1.[akamaized.net](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 2.[akamaihd.net](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 3.[ssl.google-analytics.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 4.[scorecardresearch.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 5.[vimeocdn.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)
- 6.[vimeo.com](https://support.fanswifi.com/hotspot-setup-guide/openmesh/openmesh-setup-guide-ng6xx-series#)

- Click “OK” to Save the configuration

![](../../../_images/information-required-for-fanswifi-manager-114.png)

## Step 5: Create WLAN and SSID for customer access

- Select “WiFi Networks” header

![](../../../_images/information-required-for-fanswifi-manager-115.png)

- Click “Create” with below settings

- **Name:** FansWiFi
- **Usage Type:** Hotspot Service
- **Hotspot Service:** FansWiFi
- Click “Show advanced configuration” and click “Others” tab with below settings

- **Inactivity Timeout:** 60 minutes

![](../../../_images/information-required-for-fanswifi-manager-116.png)

## Step 6: Get MAC Address of AP

- a. Access the Unleashed Admin Panel

- 1. Click “Access Points” header
- 2. Click on the AP which you want to register on FansWiFi
- 3. Click “Edit” to view the MAC Address
- 4. Copy the MAC Address for FansWiFi Hotspot Setting

![](../../../_images/information-required-for-fanswifi-manager-117.png)

## Step 7: Add AP to FansWiFi Admin Panel

- Login to FansWiFi Admin Panel
- Click**Settings -> Hotspots -> Add Hotspot**

1. 1. **Venue:** Select the venue of where your Access Point locates
2. **Hotspot Name:** Name each Access Point to make it identifiable
3. **AP Type:** Select “Ruckus Unleashed”
4. **Mac Address:** Input unique MAC Address of each Access Point in your venue
2. Click**Save**

![](../../../_images/information-required-for-fanswifi-manager-118.png)

# FAQ

## 1. How to deauthorize wifi user to bring user back to the login page after login?

- During testing, you may want to try different login methods.
- But after user authorized in any login method, captive portal will not be shown again before the expiry of session time.
- If you may want to bring the user back to the captive portal page for testing different login methods, you will need to unauthorize the WiFi user.

WiFi User Logout trigger by:

WiFi User's Device

(usually, access a logout url on browser)

Controller Web Admin Interface

Not Available

Last Testing: 11-9-2017

Available

Last Testing: 11-9-2017

**WiFi User Logout trigger by:**

**Controller**

- Click on**Client**header
- Select the device you want to logout
- Click "**Delete**"

![](../../../_images/information-required-for-fanswifi-manager-119.png)
