## Information required for FansWiFi Manager 

- Mac Addresses of the APs

## Tested Model and Firmware Version

- Standalone Controller
    - Model: **Aruba Mobility Controller** **Aruba7005-US**
    - Software Version: **ArubaOS 8.10.0.9 LSR**
- Controller managed by Aruba Mobility Conductor / Mobility Master (MM / MD)
    - Software Version: **ArubaOS 8.10.0.12 LSR**

## Setting on Aruba Controller

### Step 0: Make sure the controller can successfully connect to both the Internet and FansWiFi radius server

- a. Go to **Diagnostics** > **Tools** > **Ping**
    - Please ping with the following IP address one-by-one:
        - IP address: **8.8.8.8** (Google's DNS Address)
        - IP address: **103.6.85.240** (radius.fanswifi.com)
    ![](../../../_images/aruba_ping_version_8.png)
    - Click "**Ping**"
        - If either one IP address is not success, please move to (b)
        - If both IP address are success, please move to step 1
        - ![](../../../_images/aruba_ping_version_8_result.png)
- b. If (a) does not success (i.e. the controller cannot ping 8.8.8.8 **or** our radius server address), the controller is probably do not have correct IP or Default Gateway configuration
    - Make sure your controller have a "Default Gateway" setting if not available
        - A common configuration issue is that the controller do not have the Default Gateway setting by default. If the controller do not have the default gateway setting, it can't communicate with the Internet and also our FansWiFi Radius server
    - Goto Configuration > Interface > IP route
        - Click "**+**" under **Static** >**Default Gateway**
            - **IP address:** "IP Address of your network's gateway"
            - Click "**Submit**"
            - Try step (a) again to see whether it can connect to both Internet and FansWiFi radius server or not
        ![](../../../_images/aruba_ping_version_8_res_2.png)

### Step 1: Configuration: WLAN and SSID

- a. Access the Aruba Mobility Controller by opening a Web Browser
- b. Click **Configuration > WLAN > "+"** to configure new WLAN
- c. In **General** setting
    - Name (SSID): **- FansWiFi Free WiFi -**
        - Or any SSID you preferred
    - Primary usage: **Guest**
    - Click "**Next**"
    ![](../../../_images/aruba_mob_control_8_section_d.png)
- d. In **VLANs** setting
    - VLAN: **1 (or any vlan you use)**
        - 🚨 Please make sure the controller have an L3 interface and IP address on the VLAN used for Captive Portal SSID 🚨
        - Otherwise, the controller will not able to redirect WiFi users to Captive Portal page
        - Please refer to FAQ for more details
            - [FAQ 2). If VLAN is used in your setup, make sure the controller have an Interface and IP Address on this VLAN]([#h_6d97a36cda](https://www.facebook.com/hashtag/h_6d97a36cda))
    - Click "**Next**"
    ![](../../../_images/aruba_mob_control_8_section_e.png)
- e. In **Security** setting
    ![](../../../_images/aruba_mob_control_8_section_f.png)
    - Select **ClearPass or other external Captive Portal**
    - In **Auth servers,** Click "**+**" > "**+**" (Create new server)
        - Select "**RADIUS**"
        - Configure with following settings:
            - Name: **FansWiFi_rad1**
            - IP address: **103.6.85.240**
            - Auth port: **1812**
            - Accounting port: **1813**
            - Shared key: **social123**
            - Retype key: **social123**
        - Click "**Submit**"
        ![](../../../_images/aruba_mob_control_8_section_f_2.png)
    - Then, configure with following settings:
        - Auth servers: **FansWiFi_Radius**
        - Host: **connect-p.fanswifi.com**
        - Page: **/auth**
        - Redirect URL: **https://connect-p.fanswifi.com/auth?res=success**
    - Click "**Next**"
    ![](../../../_images/aruba_mob_control_8_section_f_3.png)
- f. In **Access** setting, click "**Finish**"

### Step 2: Configuration: Walled Garden

- a. Select **Configuration > Roles & Policies > Aliases**
- b. Click **"+"** to add a walled garden
- c. Configure the settings with below settings
    - i. IP Version: **IPv4**
    - ii. Name: **FansWiFi_WalledGarden**
- d. Click **"+"** to add a rule and configure with below settings
    - i. Rule Type: **Name**
    - ii. Domain Name: **Enter walled garden domain name**
- e. Click **OK** to confirm details and add a new rule
- f. Configure the walled garden with below settings

![](../../../_images/setting-on-aruba-controller-313.png)

### Walled Garden List (required)

1. *.[fanswifi.com](http://fanswifi.com/)

### i.Walled Garden List (Optional, you may skip this if there is no Facebook Login Enabled)

1. *.[facebook.com](http://facebook.com/)
2. *.[facebook.net](http://facebook.net/)
3. *.[fbcdn.net](http://fbcdn.net/)
4. *.[fbcdn.com](http://fbcdn.com/)
5. *.[akamaihd.net](http://akamaihd.net/)
6. [www.google.com](http://www.google.com/)
7. *.[doubleclick.net](http://doubleclick.net/)
8. [www.google.com.hk](http://www.google.com.hk/)(Local Google URL of your Country / Region)
    a. Example:
        i. EU:[www.google.eu](http://www.google.eu/)
        ii. UK:[www.google.co.uk](http://www.google.co.uk/)
        iii. Hong Kong:[www.google.com.hk](http://www.google.com.hk/)
        iv. Japan:[www.google.co.jp](http://www.google.co.jp/)
        v. Taiwan:[www.google.com.tw](http://www.google.com.tw/)
        vi. Thailand:[www.google.co.th](http://www.google.co.th/)
        vii. Malaysia:[www.google.com.my](http://www.google.com.my/)
        viii. Myanmar:[www.google.com.mm](http://www.google.com.mm/)

### ii.Walled Garden List (Optional, you may skip this if there is no Weibo Login Enabled)

    1. *.[weibo.com](http://weibo.com/)
    2. *.[weibo.cn](http://weibo.cn/)
    3. *.[sinaapp.com](http://sinaapp.com/)
    4. *.[sina.com.cn](http://sina.com.cn/)
    5. *.[sinajs.cn](http://sinajs.cn/)

### iii.Walled Garden List (Optional, you may skip this if there is no Instagram Login Enabled)

    1. *.[instagram.com](http://instagram.com/)
    2. *.[akamaihd.net](http://akamaihd.net/)
    3. *.[cdninstagram.com](http://cdninstagram.com/)

### iv.Twitter Login (Optional, you may skip this if there is no Twitter Login Enabled)

    1. *.[twitter.com](http://twitter.com/)
    2. *.[twimg.com](http://twimg.com/)

### v.LINE Login (Optional, you may skip this if there is no LINE Login Enabled)

    1. *.[line.me](http://line.me/)
    2. *.[line-scdn.net](http://line-scdn.net/)

### vi.PayPal Login (Optional, you may skip this if there is no PayPal Login Enabled)

    1. *.[paypal.com](http://paypal.com/)
    2. *.[paypalobjects.com](http://paypalobjects.com/)
    3. [www.google-analytics.com](http://www.google-analytics.com/)

### vii.Video Login (Optional, you may skip this if there is no Video Login Enabled)

    1. *.[akamaized.net](http://akamaized.net/)
    2. *.[akamaihd.net](http://akamaihd.net/)
    3. [ssl.google-analytics.com](http://ssl.google-analytics.com/)
        a. *.[scorecardresearch.com](http://scorecardresearch.com/)
        b. *.[vimeocdn.com](http://vimeocdn.com/)
        c. *.[vimeo.com](http://vimeo.com/)

- g. Click **Submit** to save configuration

![](../../../_images/setting-on-aruba-controller-314.png)

### Step 3: Configuration: Captive Portal

- a. Click **Configuration > Authentication > L3 Authentication**
- b. Select **Captive Portal Authentication**
- c. Select **- FansWiFi Free WiFi -_cppm_prof**
    - a profile will be created automatically by the controller for each SSID you created **<ssid-name-you-configured>_cppm_prof** in[Step 1]([#h_6cf0c639aa](https://www.facebook.com/hashtag/h_6cf0c639aa))
- add configure with below settings
    - i. Default Role: **guest**
    - ii. Default Guest Role: **guest**
    - iii. Redirect Pause: **0**
    - iv. User Login: **Ticked**
    - v. Guest Login: **Unticked**
    - vi. Logout popup window: **Unticked**
    - vii. Use HTTP for authentication: **Ticked**
    - viii. Show FQDN: **Ticked**
    - ix. Authentication Protocol: **PAP**
    - x. Login page: **https://connect-p.fanswifi.com/auth**
    - xi. Welcome page: **https://connect-p.fanswifi.com/auth?res=success**
    - xii. Show Welcome page: **Ticked**
    - xiii. Add switch IP in redirection URL: **Ticked**
    - xiv. Adding user vlan in redirection URL: **Ticked**
    - xv. Adding AP's MAC address in redirection URL: **Ticked**
    - xvi. Allow only one active user session: **Unticked**
    - xvii. White List: Add **FansWiFi_WalledGarden** from the list (by clicking**"+"**)
        - **FansWiFi_WalledGarden was defined inStep 2**
        - **- FansWiFi Free WiFi -_cppm_prof** should remain in allow list
    - xviii. Redirect URL: **https://connect-p.fanswifi.com/auth?res=success**
- d. Click **Submit** to save configuration

![](../../../_images/setting-on-aruba-controller-315.png)

### Step 4: Configuration: AAA profile

- a. Click **Configuration > Authentication > AAA profiles**
- b. Select **AAA**
- c. Select **- FansWiFi Free WiFi -_aaa_prof**
    - a profile will be created automatically by the controller for each SSID you created **<ssid-name-you-configured>_aaa_prof** in[Step 1]([#h_6cf0c639aa](https://www.facebook.com/hashtag/h_6cf0c639aa))
- d. Leave all settings as they are, except:
    - i. RADIUS Roaming Accounting: **Ticked**
    - ii. RADIUS Interim Accounting: **Ticked**
- e. Click **Submit** to save configuration
![](../../../_images/aruba_mob_control_8_step_4.png)

### Step 5: Configuration: Radius Server

- a. Click **Configuration > Authentication > Auth servers**
- b. From **all server**, select **FansWiFi_rad1**
- c. Leave all settings as they are, except:
    - i. NAS ID: **socialnas**
    - ii. Mode: **Ticked**
    - iii. MAC address delimiter: **Dash**
    - iv. Station ID Type: **AP MAC address**
    - v. Station ID Delimiter: **Dash**
    - vi. Include SSID: **Ticked**
- e. Click **Submit** to save configuration
![](../../../_images/aruba_mob_control_8_step_5.png)

### Step 6: Add AP to FansWiFi Admin Panel

- Login to FansWiFi Admin Panel
![](../../../_images/aruba_mob_control_8_step_6_1.png)
- Click **Settings -> Hotspots -> Create**

    1. **Venue:** Select the venue of where your Access Point locates
    2. **Hotspot Name:** Name each Access Point to make it identifiable
    3. **AP Type:** Select “Aruba Mobility Controller”
    4. **Mac Address:** Input unique MAC Address of each Access Point in your venue (Not controller)
- Click **Create**

![](../../../_images/setting-on-aruba-controller-316.png)

​

## FAQ

### 1. How to deauthorize wifi user to bring user back to the login page after login?

- During testing, you may want to try different login methods.
- But after user authorized in any login method, captive portal will not be shown again before the expiry of session time.
- If you may want to bring the user back to the captive portal page for testing different login methods, you will need to unauthorize the WiFi user.


| WiFi User Logout trigger by: | WiFi User's Device<br>(usually, access a logout url on browser) | Controller Web Admin Interface | Conductor Web Admin Interface |
|---|---|---|---|
|  | No Information<br><br>Last Testing: | Not available<br><br>Last Testing: | Available<br><br>Last Testing: |


**WiFi User Logout trigger by Web UI:**

**Available for Aruba Mobility Conductor / Mobility Master (MM / MD)**

- Navigate to **Dashboard > Overview > Clients**
    - or the **Clients** button on top of the Web UI
- Select the client you want to logout
- Click **Delete wireless client** to logout the user
- ⭐ This button is likely not available in Aruba Mobility Controller in ArubaOS 8.x version

![](../../../_images/setting-on-aruba-controller-317.jpeg)

**WiFi User Logout trigger by SSH:**

Available for both Aruba Conductor and Controller

- SSH to the controller

```
ssh -o PubkeyAuthentication=no admin@<controller-ip-address>
```

- After entering the Aruba controller through ssh, you may use following commend to check the user status and mac addresses:

```
show user-table
```

- Or you may also show only captive portal users

```
show user-table authentication-method web
```

- To unearth the user, delete selected WiFi user by the mac address

```
aaa user delete mac <device-mac-address>
```

- You may also delete all the user by the following commend (Use with caution, all WiFI user on the controller would be deauthenticated. This command is only for testing phrase.)

```
aaa user delete all
```

### 2. If VLAN is used in your WLAN / SSID with captive portal, please make sure the controller have an Interface and IP Address on this VLAN

- ⭐ Please make sure the controller have an **IP address** on the VLAN
- Otherwise, the controller will not able to redirect WiFi users to Captive Portal page
- Select **Configuration > Interface > VLANs**
    - Choose the VLAN your SSID is configured
    - Configure an IP Address

![](../../../_images/setting-on-aruba-controller-318.png)
