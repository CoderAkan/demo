### Information required for FansWifi Manager
- Mac Addresses of the APs

### Tested Model and Firmware Version
- AP Firmware Version: 8.10.0.6_86193
- Cloud-hosted on HPE GreenLake

## Setting on Aruba Networking Central

### Step 1: Create SSID
- a. Login to Netgear Insight

![](../../_images/netgear_step_1_0.png)

- b. Click **Wirelesss** on the top menu, then click **Settings**

![](../../_images/netgear_step_1_1.png)

- c. Select **WiFi and Captive Portal** on the left menu, then click "**+**" to add SSID

![](../../_images/netgear_step_1_2.png)

- d. Configure the following settings:
    - SSID: \<ssid-name-you-prefer\>
    - Security: Open
- e. Click **Save**

![](../../_images/netgear_step_1_3.png)

### Step 2: Captive Portal Configuration
- a. Click Edit from the SSID that you created and want to configure

![](../../_images/netgear_step_2_0.png)

- b. Click **Captive Portal** on the left menu

- c. Configure the following settings:
    - **Enable Captive Portal**: Enable
    - **Captive Portal Type**: External Captive Portal
    - **Splash Page URL**: [https://connect-p.fanswifi.com/auth](https://connect-p.fanswifi.com/auth)

![](../../_images/netgear_step_2_1.png)

### Step 3: Radius Configuration

- a. Continue configure with following settings:
    - **Captive Portal Authentication Type**: Radius
    - **NAS-Identifier**: socialnas
    - **Primary Authentication Server**
        - **IPv4 Address**: 103.6.85.240
        - **Port**: 1812
        - **Password**: social123
    - **Primary Accounting Server**
        - **IPv4 Address**: 103.6.85.240
        - **Port**: 1813
        - **Password**: social123

![](../../_images/netgear_step_3_0.png)


### Step 4: Walled Garden

- a. Continue configure with following settings:
    - **Walled Garden**:
        - (1) Enter all the domain from the below Walled Garden List
        - (2) Click Add to add the domains to Walled Garden

- b. Finally, goto top menu and click Save

![](../../_images/netgear_step_4_0.png)

#### Walled Garden List (required)

1. [fanswifi.com](https://www.fanswifi.com/en-us)

##### i. Walled Garden List (Optional, you may skip this if there is no Facebook Login Enabled)

1. [facebook.com](https://www.facebook.com/)
2. [facebook.net](https://www.facebook.net/)
3. [fbcdn.net](https://www.fbcdn.net/)
4. [fbcdn.com](https://www.fbcdn.com/)
5. [akamaihd.net](https://www.akamaihd.net/)
6. [www.google.com](https://www.google.com/)
7. [doubleclick.net](https://www.doubleclick.net/)
8. [www.google.com.hk](https://www.google.com.hk/) (Local Google URL of your Country / Region)
    a. Example:
        i. EU: [www.google.eu](https://www.google.eu/)
        ii. UK: [www.google.co.uk](https://www.google.co.uk/)
        iii. Hong Kong: [www.google.com.hk](https://www.google.com.hk/)
        iv. Japan: [www.google.co.jp](https://www.google.co.jp/)
        v. Taiwan: [www.google.com.tw](https://www.google.com.tw/)
        vi. Thailand: [www.google.co.th](https://www.google.co.th/)
        vii. Malaysia: [www.google.com.my](https://www.google.com.my/)
        viii. Myanmar: [www.google.com.mm](https://www.google.com.mm/)

##### ii. Walled Garden List (Optional, you may skip this if there is no Weibo Login Enabled)

1. [weibo.com](https://www.weibo.com/)
2. [weibo.cn](https://www.weibo.cn/)
3. [sinaapp.com](https://www.sinaapp.com/)
4. [sina.com.cn](https://www.sina.com.cn/)
5. [sinajs.cn](https://www.sinajs.cn/)

##### iii. Walled Garden List (Optional, you may skip this if there is no Instagram Login Enabled)

1. [instagram.com](https://www.instagram.com/)
2. [akamaihd.net](https://www.akamaihd.net/)
3. [cdninstagram.com](https://www.cdninstagram.com)

##### iv. Twitter Login (Optional, you may skip this if there is no Twitter Login Enabled)

1. [twitter.com](https://www.twitter.com/)
2. [twimg.com](https://www.twimg.com/)

##### v. LINE Login (Optional, you may skip this if there is no LINE Login Enabled)

1. [Line.me](https://www.line.me/)
2. [line-scdn.net](https://www.line-scdn.net/)

##### vi. PayPal Login (Optional, you may skip this if there is no PayPal Login Enabled)

1. [paypal.com](https://www.paypal.com/)
2. [paypalobjects.com](https://www.paypalobjects.com/)
3. [www.google-analytics.com](https://www.google-analytics.com/)

##### vii. Video Login (Optional, you may skip this if there is no Video Login Enabled)

1. [akamaized.net](https://www.akamaized.net/)
2. [akamaihd.net](https://www.akamaihd.net/)
3. [ssl.google-analytics.com](https://ssl.google-analytics.com/)
    1. [scorecardresearch.com](https://www.scorecardresearch.com/)
    2. [vimeocdn.com](https://www.vimeocdn.com/)
    3. [vimeo.com](https://www.vimeo.com/)

### Step 5: Add AP to FansWifi Admin Panel

- Login to FansWiFi Admin Panel
- Click **Settings -> Hotspots -> Create**
- Configure with following settings:
    - **Venue**: Select the venue of where your Access Point locates
    - **Hotspot Name**: Name each Access Point to make it identifiable
    - **AP Type**: Select “Netgear Insight”
    - **Mac Address**: Input unique MAC Address of each Access Point in your venue
- Click **Create**

![](../../_images/netgear_step_5_0.png)

![](../../_images/netgear_step_5_1.png)
