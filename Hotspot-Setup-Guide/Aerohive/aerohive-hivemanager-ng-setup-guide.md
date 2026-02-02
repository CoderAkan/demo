## Information required for FansWiFi Manager (AeroHive HiveManager NG)

- MAC addresses of the access points (APs)

## Tested HiveOS version

- Version: **8.1r1**

---

## Configuration in AeroHive HiveManager NG

### Step 1: Configure the Network Policy

1. Click **Add Network Policy** to create a new policy profile, **or**
2. Click **Add Guest SSID** to add a new SSID to an existing network policy.

![](../../../_images/aerohive-ng-conf-0.png)

3. Name the policy.
![](../../../_images/aerohive-ng-conf-1.png)

---

### Step 2: Configure Wireless Settings (SSID)

1. Add a new SSID: **All other SSIDs (standard)**

   ![](../../../_images/information-required-for-fanswifi-manager-18.png)

2. Configure:
   - **SSID Name / SSID Broadcast Name:** (your preferred name)
   - **SSID Usage:** **Open**
   - Enable **Captive Web Portal**
   - Captive portal features: **User Auth on Captive Web Portal**
   - **Authentication Type:** **Redirect to External URL**
   - If this is your first time setup, add a new **Default Captive Web Portal**

   ![](../../../_images/information-required-for-fanswifi-manager-19.png)

---

### Step 3: Configure Captive Web Portal

1. Name the captive portal.
2. Turn **ON**: **User Auth on Captive Web Portal**

![](../../../_images/aerohive-ng-conf-2.png)

3. Configure **Login Page**
   - **Login URL:** [https://connect-p.fanswifi.com/auth](https://connect-p.fanswifi.com/auth)
   - **Password Encryption:** No Encryption
   - **Authentication Method:** PAP
   - **Success Page:** OFF
     - Enable: **Redirect clients after a successful login attempt**
     - Select: **To a specified URL**
       - [https://connect-p.fanswifi.com/auth?id=aerohive-ng&res=success](https://connect-p.fanswifi.com/auth?id=aerohive-ng&res=success)
   - **Failure Page:** OFF
     - Enable: **Redirect client after a failed login attempt**
     - Select: **To a specified URL**
       - [https://connect-p.fanswifi.com/auth](https://connect-p.fanswifi.com/auth)

   ![](../../../_images/information-required-for-fanswifi-manager-20.png)

---

### Step 3.1: Walled Garden (Hostname Rules)

1. Go to **Walled Garden** and add new rules.

   ![](../../../_images/information-required-for-fanswifi-manager-21.png)

2. For each hostname record:
   - Set **Service = All**

##### Required (FansWiFi)

- [fanswifi.com](http://fanswifi.com/)
- [radius.fanswifi.com](http://radius.fanswifi.com/)

##### Walled Garden List (Optional, you may skip this if there is no Facebook Login Enabled)

- [facebook.com](http://facebook.com/)
- [facebook.net](http://facebook.net/)
- [fbcdn.net](http://fbcdn.net/)
- [fbcdn.com](http://fbcdn.com/)
- [akamaihd.net](http://akamaihd.net/)
- [fbsbx.com](http://fbsbx.com/)
- [*.fbsbx.com](http://fbsbx.com/)

##### Walled Garden List (Optional, you may skip this if there is no Weibo Login Enabled)

- [weibo.com](http://weibo.com/)
- [weibo.cn](http://weibo.cn/)
- [sinaapp.com](http://sinaapp.com/)
- [sina.com.cn](http://sina.com.cn/)
- [sinajs.cn](http://sinajs.cn/)

##### Instagram Login (Optional, you may skip this if there is no Instagram Login Enabled)

- [instagram.com](http://instagram.com)
- [akamaihd.net](http://akamaihd.net)
- [cdninstagram.com](http://cdninstagram.com)

##### Twitter/X Login (Optional, you may skip this if there is no Twitter/X Login Enabled)

- [twitter.com](http://twitter.com)
- [twimg.com](http://twimg.com)

##### LINE Login (Optional, you may skip this if there is no LINE Login Enabled)

- [line.me](http://line.me)
- [line-scdn.net](http://line-scdn.net)

##### PayPal Login (Optional, you may skip this if there is no PayPal Login Enabled)

- [paypal.com](http://paypal.com)
- [paypalobjects.com](http://paypalobjects.com)
- [www.google-analytics.com](http://www.google-analytics.com)

##### Video Login (Optional, you may skip this if there is no Video Login Enabled)

- [akamaized.net](http://akamaized.net)
- [akamaihd.net](http://akamaihd.net)
- [ssl.google-analytics.com](http://ssl.google-analytics.com)
- [scorecardresearch.com](http://scorecardresearch.com)
- [vimeocdn.com](http://vimeocdn.com)
- [vimeo.com](http://vimeo.com)

---
**Example result (Facebook rules enabled):**

![](../../../_images/information-required-for-fanswifi-manager-22.png)

---

### Step 4: Configure Authentication (RADIUS)

1. Add a new **RADIUS Server Group**

   ![](../../../_images/information-required-for-fanswifi-manager-23.png)

2. In the RADIUS Server Group, add a new **External RADIUS Server**

   ![](../../../_images/aerohive-ng-conf-3.png)

3. Configure the external RADIUS server:
   - **Name:** FansWiFi Radius
   - **Host Name:** `radius.fanswifi.com`

      ![](../../../_images/aerohive-ng-conf-4.png)
   - **Authentication Port:** `1812`
   - **Accounting Port:** `1813`
   - **Shared Secret:** `social123`

   ![](../../../_images/information-required-for-fanswifi-manager-24.png)

4. Click **Save** to save the wireless settings.

---

### Step 5: Save the SSID Settings

1. Click **Save** to save the SSID settings.

   ![](../../../_images/information-required-for-fanswifi-manager-25.png)

---

### Step 6: Deploy Policy

1. Select the AP(s) you want to deploy to, then click **Upload**
2. Select **Delta Configuration Update**
3. Enable **Update Network Policy and Configuration**
4. Click **Perform Update**

   ![](../../../_images/information-required-for-fanswifi-manager-26.png)

   ![](../../../_images/information-required-for-fanswifi-manager-27.png)

---

### Step 7: Setup in FansWiFi Admin Panel

1. Log in:
   - [https://admin-p.fanswifi.com/login](https://admin-p.fanswifi.com/login)

2. Go to:
   - **Settings → Hotspots → Add Hotspot**

3. Configure:
   - **Venue:** Select the venue where the AP is located
   - **Hotspot Name:** A name to identify the AP
   - **AP Type:** **Aerohive**
   - **MAC Address:** Enter the AP MAC address

4. Click **Save**

![](../../../_images/information-required-for-fanswifi-manager-28.png)

---

# FAQ

## 1) How to force a WiFi user back to the login page (during testing)?

After a user logs in once, the captive portal may not show again until the session expires.

### What you can do

- In the FansWiFi Admin Panel, set a **short session duration** for testing (e.g., **1–2 minutes**).
- Then reconnect and test different login methods.

| WiFi User Logout trigger by: | WiFi User's Device<br>(usually, access a logout url on browser) | Controller Web Admin Interface |
|---|---|---|  
|  | Not available <br><br>Last Testing: 11-9-2017 <br><br> HiveOS: 8.1r1 | Not available in HiveManager <br><br>Last Testing: 11-9-2017 <br><br> HiveOS: 8.1r1 |