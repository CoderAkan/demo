# Information required for the user


# Information required for the user

- Mac Address of the APs

# Tested Model and firmware Version

- Model: RG-AP720-L
- Firmware Version: AP_RGOS 11.1(9)B1P21, Release(06211815)

# Setting on Ruijie Cloud

## Step 1: Create a new project

- a. Access the Ruijie cloud network via this link:[https://cloud.ruijienetworks.com/](https://cloud.ruijienetworks.com/)
- b. Click "Add" and Select "Add Project"

![](../../../_images/information-required-for-the-user-285.png)

- c. Configuring SSID and Add Device:

- i. Select AP, Managed by Ruijie Cloud Web
- ii. Type in SSID and select 'No encryption (Open)' mode
- iii. Put serial number (SN) of the AP and click Finish

![](../../../_images/information-required-for-the-user-286.png)

![](../../../_images/information-required-for-the-user-287.png)

![](../../../_images/information-required-for-the-user-288.png)

## Step 2: Create SSID

- **You can skip this part if you already create SSID**
- a. Click "Device Config" on the left menu
- b. Under "Wireless" section, select "SSID"

![](../../../_images/information-required-for-the-user-289.png)

- c. Click "Add SSID"

![](../../../_images/information-required-for-the-user-290.png)

- d. Configure with following setting:

- **SSID:** *<ssid-name-you-prefer>*
- **Encryption Option:** Do not Encrypt
- **Encryption Method:** OPEN (Open)
- e. Click "OK"

![](../../../_images/information-required-for-the-user-291.png)

## Step 3: Create Captive Portal

- a. Click "Auth & Accounts" on the left menu
- b. Under "Authentication" section, select "Captive Portal"

![](../../../_images/information-required-for-the-user-292.png)

- c. Click "Add Captive Portal"

![](../../../_images/information-required-for-the-user-293.png)

- d. Configure the following settings:

- **Policy Name:** *<policy-name-you-prefer>*
- **Policy Mode:** External
- **SSID:** *Select the SSID you created inStep 2(e.g. <ssid-name-you-prefer>)*
- **Portal Server URL:** [https://connect-p.fanswifi.com/wifidog](https://connect-p.fanswifi.com/wifidog)
- **Portal IP:** 52.220.206.125
- **Seamless Online:** Enable
- e. Click "OK"

![](../../../_images/information-required-for-the-user-294.png)

## Step 4: Configure Walled Garden Lists and CLI Command

- a. Click "Auth & Accounts" on the left menu
- b. Under "Authentication" section, select "Allowlist"

![](../../../_images/information-required-for-the-user-295.png)

- c. Under ‘Pre-Authentication Access Server List’, click Add and choose Domain

![](../../../_images/information-required-for-the-user-296.png)

### Walled Garden List (required)

- 1. *.[fanswifi.com](http://fanswifi.com/)

- i.**Walled Garden List (Optional, you may skip this if there is no Facebook Login Enabled)**

1. *.[facebook.com](http://facebook.com/)
2. *.[facebook.net](http://facebook.net/)
3. *.[fbcdn.net](http://fbcdn.net/)
4. *.[fbcdn.com](http://fbcdn.com/)
5. *.[akamaihd.net](http://akamaihd.net/)
6. [www.google.com](http://www.google.com/)
7. *.[doubleclick.net](http://doubleclick.net/)
8. [www.google.com.hk](http://www.google.com.hk/)(Local Google URL of your Country / Region)

1. Example:

1. EU:[www.google.eu](http://www.google.eu/)
2. UK:[www.google.co.uk](http://www.google.co.uk/)
3. Hong Kong:[www.google.com.hk](http://www.google.com.hk/)
4. Japan:[www.google.co.jp](http://www.google.co.jp/)
5. Taiwan:[www.google.com.tw](http://www.google.com.tw/)
6. Thailand:[www.google.co.th](http://www.google.co.th/)
7. Malaysia:[www.google.com.my](http://www.google.com.my/)
8. Myanmar:[www.google.com.mm](http://www.google.com.mm/)
- ii.**Walled Garden List (Optional, you may skip this if there is no Weibo Login Enabled)**

1. *.[weibo.com](http://weibo.com/)
2. *.[weibo.cn](http://weibo.cn/)
3. *.[sinaapp.com](http://sinaapp.com/)
4. *.[sina.com.cn](http://sina.com.cn/)
5. *.[sinajs.cn](http://sinajs.cn/)
- iii.**Walled Garden List (Optional, you may skip this if there is no Instagram Login Enabled)**

1. *.[instagram.com](http://instagram.com/)
2. *.[akamaihd.net](http://akamaihd.net/)
3. *.[cdninstagram.com](http://cdninstagram.com/)
- iv.**Twitter Login (Optional, you may skip this if there is no Twitter Login Enabled)**

1. *.[twitter.com](http://twitter.com/)
2. *.[twimg.com](http://twimg.com/)

- v.**LINE Login (Optional, you may skip this if there is no LINE Login Enabled)**

1. *.[line.me](http://line.me/)
2. *.[line-scdn.net](http://line-scdn.net/)
​
- vi.**PayPal Login (Optional, you may skip this if there is no PayPal Login Enabled)**

1. *.[paypal.com](http://paypal.com/)
2. *.[paypalobjects.com](http://paypalobjects.com/)
3. [www.google-analytics.com](http://www.google-analytics.com/)

- vii.**Video Login (Optional, you may skip this if there is no Video Login Enabled)**

1. *.[akamaized.net](http://akamaized.net/)
2. *.[akamaihd.net](http://akamaihd.net/)
3. [ssl.google-analytics.com](http://ssl.google-analytics.com/)
4. *.[scorecardresearch.com](http://scorecardresearch.com/)
5. *.[vimeocdn.com](http://vimeocdn.com/)
6. *.[vimeo.com](http://vimeo.com/)

## Step 5: Enable DNS Snooping via CLI Command

- a. Click "Device Config" on the left menu
- b. Under "General" section, select "CLI Config Task"

![](../../../_images/information-required-for-the-user-297.png)

- c. Click 'Add a CLI Command Set'

- **Name:** FansWiFi DNS Setting
- **Command:**

- config t
- ip dns snooping enable

![](../../../_images/information-required-for-the-user-298.png)

## Step 6: Add AP to FansWiFi Admin Panel

- Login to FansWiFi Admin Panel
- Click**Settings -> Hotspots -> Create**
- Configure with following settings:

- **Venue:** Select the venue of where your Access Point locates
- **Hotspot Name:** Name each Access Point to make it identifiable
- **AP Type:** Select “Ruijie WiFiDog”
- **Mac Address:** Input unique MAC Address of each Access Point in your venue
- Click**Create**

![](../../../_images/information-required-for-the-user-299.png)

![](../../../_images/information-required-for-the-user-300.png)
