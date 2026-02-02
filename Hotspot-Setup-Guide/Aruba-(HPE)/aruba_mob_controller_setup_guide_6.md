## Information required for FansWiFi Manager

- Mac Addresses of the APs

## Tested Model and Firmware Version

- Model: **Aruba3200-US**
- Firmware Version: **6.3.1.24**

## Setting on Aruba Controller

### Step 0: Make sure the controller can successfully connect to FansWiFi radius server

- a. Goto Diagnostics > Network > Ping

    - IP address: **103.6.85.240** (radius.fanswifi.com)

    ![](../../../_images/arub_mob_control_version_6_step_0.png)
    - Click "Ping"

        - If not success, please move to (b)
        - If success, please move to step 1

        ![](../../../_images/aruba_mob_control_6_step_0_error.png)

- b. Make sure your controller have a "Default Gateway" setting if not available

    - A common configuration issue is that the controller do not have the Default Gateway setting by default. If the controller do not have the default gateway setting, it can't communicate with the Internet and also our FansWiFi Radius server
    - Goto Configuration > IP

        - Click "**Add**" under **Static** from **Default Gateway**

        - **IP address:** "IP Address of your network's gateway"
        - Click "Add"

        ![](../../../_images/aruba_mob_control_6_step_0_2.png)

    - Try step (a) again to see whether it can connect to the radius or not

### Step 1: Configuration: WLAN and SSID

- a. Access the Aruba Mobility Controller by opening a Web Browser
- b. Click **Configuration > WIZARDS > Campus WLAN** to open wizard to configure

![](../../../_images/aruba_mob_control_6_step_1_1.png)

- c. Under WLANs box, click **New**. Enter SSID name (e.g. FansWiFi) then click **Ok** and then click **Next**.

![](../../../_images/aruba_mob_control_6_step_1_2.png)

- d. In **Forwarding Mode**, select any type suitable for your deployment, then click **Next**

![](../../../_images/information-required-for-fanswifi-manager-170.png)

- e. In **Radio & VLAN**, configure with:

    - i. Radio Type: **All**
    - ii. Broadcast SSID: **Yes**
    - iii. VLAN: **1**
- Click **Next** to save configuration

![](../../../_images/information-required-for-fanswifi-manager-171.png)

- f. In **Internal/Guest**, select "Guest" then click **Next**

![](../../../_images/information-required-for-fanswifi-manager-172.png)

- g. In **Authentication and Encryption**, select "Captive portal with authentication via credentials(username and password) provided by user" then click **Next**

![](../../../_images/information-required-for-fanswifi-manager-173.png)

- h. In **Authentication Server**, click **Add** and configure with below settings

    - Radius Server

        - i. Server type: **RADIUS**
        - ii. Name: **FansWiFi_rad1**
        - iii. IP address: **103.6.85.240**
        - iv. Auth port: **1812**
        - v. Acct port: **1813**
        - vi. Shared key: **social123**
        - vii. Retype key: **social123**
- Click **Ok** when adding each server and then click **Next**

![](../../../_images/information-required-for-fanswifi-manager-174.png)

- i. In **Role Assignment**, configure with below settings

    - i. Pre-authentication role: **FansWiFi-guest-logon**
    - ii. Authenticated role: **guest**
- Click **Next** to save configuration

![](../../../_images/information-required-for-fanswifi-manager-175.png)

- j. In **WLAN Configured**, you can review the WiFi settings and then click **Finish**

![](../../../_images/information-required-for-fanswifi-manager-176.png)

### Step 2: Configuration: Walled Garden

- a. Select **Configuration > ADVANCED SERVICES > Stateful Firewall > Destination**
- b. Click **Add** to add a walled garden

![](../../../_images/information-required-for-fanswifi-manager-177.png)

- c. Configure the settings with below settings

    - i. IP Version: **IPv4**
    - ii. Destination Name: **FansWiFi_WalledGarden**
- d. Click **Add** to add a rule and configure with below settings

    - i. Rule Type: **name**
    - ii. Domain Name: ***Enter walled garden domain name***
- e. Click **Add** to confirm details and add a new rule

![](../../../_images/aruba_mob_6_step_2_e.png)

- f. Configure the walled garden with below settings

## Walled Garden List (required)

1. *.[fanswifi.com](http://fanswifi.com/)

i. **Walled Garden List (Optional, you may skip this if there is no Facebook Login Enabled)**

1. *.[facebook.com](http://facebook.com/)
2. *.[facebook.net](http://facebook.net/)
3. *.[fbcdn.net](http://fbcdn.net/)
4. *.[fbcdn.com](http://fbcdn.com/)
5. *.[akamaihd.net](http://akamaihd.net/)
6. [www.google.com](http://www.google.com/)
7. *.[doubleclick.net](http://doubleclick.net/)
8. [www.google.com.hk](http://www.google.com.hk/)(Local Google URL of your Country / Region)

    - a. Example:

        - i. EU:[www.google.eu](http://www.google.eu)
        - ii. UK:[www.google.co.uk](http://www.google.co.uk/)
        - iii. Hong Kong:[www.google.com.hk](http://www.google.com.hk/)
        - iv. Japan:[www.google.co.jp](http://www.google.co.jp/)
        - v. Taiwan:[www.google.com.tw](http://www.google.com.tw/)
        - vi. Thailand:[www.google.co.th](http://www.google.co.th/)
        - vii. Malaysia:[www.google.com.my](http://www.google.com.my/)
        - viii. Myanmar:[www.google.com.mm](http://www.google.com.mm/)

ii. **Walled Garden List (Optional, you may skip this if there is no Weibo Login Enabled)**

1. *.[weibo.com](http://weibo.com/)
2. *.[weibo.cn](http://weibo.cn/)
3. *.[sinaapp.com](http://sinaapp.com/)
4. *.[sina.com.cn](http://sina.com.cn/)
5. *.[sinajs.cn](http://sinajs.cn/)

iii. **Walled Garden List (Optional, you may skip this if there is no Instagram Login Enabled)**

1. *.[instagram.com](http://instagram.com/)
2. *.[akamaihd.net](http://akamaihd.net/)
3. *.[cdninstagram.com](http://cdninstagram.com/)

iv. **Twitter Login (Optional, you may skip this if there is no Twitter Login Enabled)**

1. *.[twitter.com](http://twitter.com/)
2. *.[twimg.com](http://twimg.com/)

v. **LINE Login (Optional, you may skip this if there is no LINE Login Enabled)**

1. *.[line.me](http://line.me/)
2. *.[line-scdn.net](http://line-scdn.net/)

vi. **PayPal Login (Optional, you may skip this if there is no PayPal Login Enabled)**

1. *.[paypal.com](http://paypal.com/)
2. *.[paypalobjects.com](http://paypalobjects.com/)
3. [www.google-analytics.com](http://www.google-analytics.com/)

vii. **Video Login (Optional, you may skip this if there is no Video Login Enabled)**

1. *.[akamaized.net](http://akamaized.net/)
2. *.[akamaihd.net](http://akamaihd.net/)
3. [ssl.google-analytics.com](http://ssl.google-analytics.com/)
    - a. *.[scorecardresearch.com](http://scorecardresearch.com/)
    - b. *.[vimeocdn.com](http://vimeocdn.com/)
    - c. *.[vimeo.com](http://vimeo.com/)

- g. Click **Apply** to save configuration

![](../../../_images/information-required-for-fanswifi-manager-178.png)

### Step 3: Configuration: Captive Portal

- a. Click **Configuration > SECURITY > Authentication > L3 Authentication**

![](../../../_images/information-required-for-fanswifi-manager-179.png)

- b. Click **FansWiFi-cp_prof** add configure with below settings

    - i. Default Role: **guest**
    - ii. Default Guest Role: **guest**
    - iii. Redirect Pause: **0**
    - iv. User Login: **Ticked**
    - v. Guest Login: **Unticked**
    - vi Logout popup window: **Unticked**
    - vii. Use HTTP for authentication: **Ticked**
    - viii. Show FQDN: **Ticked**
    - ix. Authentication Protocol: **PAP**
    - x. Login page: **[https://connect-p.fanswifi.com/auth](https://connect-p.fanswifi.com/auth)**
    - xi. Welcome page: ***leave it as it is***
    - xii.Show Welcome page: **Unticked**
    - xiii. Add switch IP in redirection URL: **Ticked**
    - xiv. Adding user vlan in redirection URL: **Ticked**
    - xv. White List: Add **FansWiFi_WalledGarden** from the list
        - **FansWiFi_WalledGarden was defined inStep 2: Configuration: Walled Garden**
    - xvi. Redirect URL:
        - [https://connect-p.fanswifi.com/auth?res=success&id=aruba-xml-api](https://connect-p.fanswifi.com/auth?res=success&id=aruba-xml-api)
- c. Click **Apply** to save configuration
- Reference: ArubaOS 8.12.0 TechDocs [https://arubanetworking.hpe.com/techdocs/ArubaOS_8.12.0_Web_Help/Content/arubaos-solutions/captive-portal/capt-port-auth-prof.html](https://arubanetworking.hpe.com/techdocs/ArubaOS_8.12.0_Web_Help/Content/arubaos-solutions/captive-portal/capt-port-auth-prof.html)

![](../../../_images/information-required-for-fanswifi-manager-180.png)

- d. Then under **FansWiFi-cp_prof**, click **Server Group**
- e. Configure **Server Group >** as **FansWiFi_srvgrp-xxx (where xxx is a random number)**
- f. Click **Apply** to save configuration

![](../../../_images/information-required-for-fanswifi-manager-181.png)

### Step 4: Configuration: XML API Server

- a. Click **Configuration > SECURITY > Authentication > XML API Server**

![](../../../_images/information-required-for-fanswifi-manager-182.png)

- b. Under **XML API Server,** add either of the following ip address:

    - i. 52.220.226.90 
    - ii. 52.220.206.125
    - iii. 52.77.30.253
    - iv. 52.220.219.128
    - v. 52.220.215.219
    - vi. 52.220.208.185
- c. Click **Add** and then click **Apply** to save configuration

![](../../../_images/information-required-for-fanswifi-manager-183.png)

- d. Then click the configured IP address

![](../../../_images/information-required-for-fanswifi-manager-184.png)

- e. Under the selected XML API Server, configure with below settings:

    - Key: **aruba123**
    - Retype: **aruba123**
- f. Click **Apply** to save configuration

![](../../../_images/information-required-for-fanswifi-manager-185.png)

### Step 5: Configuration: AAA Profile

- a. Click **Configuration > SECURITY > Authentication > AAA Profiles**
- b. Click **FansWiFi-aaa_prof** and configure with below settings

    - Initial role: **FansWiFi-guest-logon**
    - RADIUS Interim Accounting: **Ticked**
- c. Click **Apply** to save configuration

![](../../../_images/information-required-for-fanswifi-manager-186.png)

- d. Under **FansWiFi-aaa_prof**, click **RADIUS Accounting Server Group**
- e. Select **FansWiFi-srvgrp-xxx (where xxx is a random number)**
- f. Click **Apply** to save configuration

![](../../../_images/information-required-for-fanswifi-manager-187.png)

- g. Under **FansWiFi-aaa_prof,** click **XML_API Server**
- h. Select the XML API Server IP address you configured (e.g. 52.220.226.90) and click **Add**
- i. Click **Apply** to save configuration

![](../../../_images/information-required-for-fanswifi-manager-188.png)

### Step 6: Configuration: Radius Server

- a. Click **Configuration > SECURITY > Authentication > Servers > RADIUS Server**

![](../../../_images/information-required-for-fanswifi-manager-189.png)

- b. Click **FansWiFi_rad1** and configure with below settings

    - First Radius Server

        - i. NAS ID: **Aruba_"mac address of aruba controller"**
        - ii. Mode: **Ticked**
        - iii. MAC address delimiter: **dash**
- c. Click **Apply** to save configuration

Finally, click **Save Configuration** at the top and reboot the controller to ensure all settings take effect

## Step 7: Configure Aruba Mobility Controller Address to FansWiFi Admin Panel

*Please send this information to your FansWiFi account manager*

**(required for WeChat WiFi, you may skip this step if there is no WeChat WiFi Enabled)**

**FansWiFi Admin Panel (Setting > Venue Setting)**

![](../../../_images/information-required-for-fanswifi-manager-190.png)

1. Send below information to FansWiFi

    - Public IP Addresses / Domain Name of Mobility Controller
    - Radius CoA Port: 3799

![](../../../_images/information-required-for-fanswifi-manager-191.png)

{% hint style="danger" %}
### Exceptional Case: Controller behind Router / Firewall

If the Controller is behind Router / Firewall, it is not directly accessible via FansWiFi Radius Server via the Internet. In this case, configure port forwarding on your Router / Firewall to forward the port to the Controller.
{% endhint %}

![](../../../_images/information-required-for-fanswifi-manager-192.png)

Please see below example:
 
Assume the Public IP of the Router is 1.1.1.1 in this example

1. Configure Port Forwarding to forward Router’s 50000 Port to Controller’s CoA Port (Default: 3799)

    {% hint style="info" %}
    - **Inbound port:** 50000 *(You can replace this with any port you want in your setup)*
    - **Destination IP:** 192.168.1.100 *(Controller's IP in your network)*
    - **Destination Port:** 3799
    {% endhint %}

2. Send below information to FansWiFi
    {% hint style="info" %}
    - Public IP Addresses of Router: 1.1.1.1 or Domain Name (URL)
    - Radius CoA Port: 50000 (You can replace any port you want in your setup)
    {% endhint %}

Setting in FansWiFi Admin Panel

![](../../../_images/information-required-for-fanswifi-manager-193.png)

### Step 8: Add AP to FansWiFi Admin Panel

- Login to FansWiFi Admin Panel
- Click **Settings -> Hotspots -> Add Hotspot**
1. Configure the hotspot in FansWiFi Admin Panel:

   {% hint style="info" %}
   - **Venue:** Select the venue where your Access Point is located
   - **Hotspot Name:** Name each Access Point to make it identifiable
   - **AP Type:** Select “Aruba Mobility Controller”
   - **Mac Address:** Input unique MAC Address of each Access Point in your venue
   {% endhint %}

2. Click **Save**

![](../../../_images/information-required-for-fanswifi-manager-194.png)

## FAQ

### 1. How to deauthorize wifi user to bring user back to the login page after login?

- During testing, you may want to try different login methods.
- But after user authorized in any login method, captive portal will not be shown again before the expiry of session time.
- If you may want to bring the user back to the captive portal page for testing different login methods, you will need to unauthorize the WiFi user.

| WiFi User Logout trigger by: | WiFi User's Device<br>(usually, access a logout url on browser) | Controller Web Admin Interface |
|---|---|---|
|  | No Information<br><br>Last Testing: 11-9-2017 | Not available<br><br>Last Testing: 18 Jul 2018 |


**WiFi User Logout trigger by:**

**Controller**

- Navigate to **Monitoring > CONTROLLER > Clients**
- Select the client you want to logout
- Click **Disconnect** to logout the user

![](../../../_images/information-required-for-fanswifi-manager-195.png)
