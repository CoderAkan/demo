# Information required for FansWiFi Manager


# Information required for FansWiFi Manager

- Mac Addresses of the APs

## Documentation references

- English Version

- [https://support.huawei.com/enterprise/en/doc/EDOC1100373532/336affb0](https://support.huawei.com/enterprise/en/doc/EDOC1100373532/336affb0)
- Simplified Chinese Version

- [https://support.huawei.com/enterprise/zh/doc/EDOC1100415754/eb439b2f](https://support.huawei.com/enterprise/zh/doc/EDOC1100415754/eb439b2f)

# Setting on Huawei eKit

## Step 1: Configure with Huawei eKit

1. Access the Portal by opening a Web Browser[https://ekit.huawei.com/](https://ekit.huawei.com/)
2. Change the location to your company location on the top right conner (e.g. HK / SG)
3. Click**Service**on the top menu
4. In**Cloud Management Platform**session, Select**SME Network Center**
5. Click**Project Created,** Select your project or create a new project.

![](../../../_images/information-required-for-fanswifi-manager-323.png)

## Step 2: Create SSID

1. Click**Configuration****on the top menu
2. Select**Device Configuration**, then choose**Wi-Fi Management**on the**AP**section
3. Click**Create**to create a SSID

## Step 3: Portal Configuration

1. Configure with the following settings:

1. **Wi-Fi name:** <SSID-name-you-prefer> (e.g. - FansWiFi Free WiFi -)
2. **Security policy:** Portal authn
3. **Authentication type:** Third-party Authentication
4. **Portal authentication exemption:** Disable
5. **Bypass policy:** Enable
​
2. Portal server configuration

1. For**Portal server**session, click**Create****to create a new portal server
2. Configure with the following settings:

1. **Name:** <portal-name-you-prefer> (e.g. FansWiFi-Portal)
2. **Authentication protocol:** HTTPS
3. **Method:** POST, GET
4. **Password coding mode:** uam: Passwords are encoded in ASCII format.
5. **Portal IP:** 52.220.206.125
6. **Portal redirection URL:** [https://connect-p.fanswifi.com/auth](https://connect-p.fanswifi.com/auth)
7. **Key:** social123

1. Click**Configure**to enter the key
2. **Key:** social123
3. **Confirm key:** social123
4. Click**OK**
3. Click**OK**
4. Select**Portal server**that you created
3. Radius Configuration

1. For**RADIUS server**session, click**Create****to create a new portal server
2. Configure with the following settings:

1. **Name:** <radius-name-you-prefer> (e.g. FansWiFi-Radius)
2. **Address type:** IP address
3. **Authentication server**

1. Click**Create**
2. **Authentication server address:** 103.6.85.240
3. **Port:** 1812
4. **Real-Time Accounting:** Enable
5. **Accounting server**

1. Click**Create**
2. **Accounting Server Address:** 103.6.85.240
3. **Port:** 1813
6. **Key:** social123

1. Click**Configure**to enter the key
2. **Key:** social123
3. **Confirm key:** social123
4. Click**OK**
3. Click**Confirm**
4. Select**RADIUS server**that you created
4. **Default permit rule**Configuration

1. For**Default permit rule**session, click**Create**
2. Configure with the following settings:

1. **Name:** <permit-rule-name-you-prefer> (e.g. Walled-Garden-List)
2.
3. Add**IPv4 rule**with the following configurations:

1. Click**Create**
2. **Address Type:** IP Address/Mask
3. **IP Address/Mask:** Refer to the following IP address

1. 192.168.0.0/16
2. 172.16.0.0/12
3. 10.0.0.0/8
4. **Protocol:** Any
4. Add**IPv4 rule**with the following configurations:

1. Click**Create**
2. **Address Type:** Domain name
3. **Domain name:** Refer to the Walled Garden List (below)

1. *.[fanswifi.com](http://fanswifi.com/)
4. **Protocol:** Any
5. Repeat (i)-(iv) to add another domains in Walled Garden List
5. Walled Garden List

1. **Walled Garden List (required)**

1. 192.168.0.0/16
2. 172.16.0.0/12
3. 10.0.0.0/8
4. *.[fanswifi.com](http://fanswifi.com/)

i.**Walled Garden List (Optional, you may skip this if there is no Facebook Login Enabled)**

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

ii.**Walled Garden List (Optional, you may skip this if there is no Weibo Login Enabled)**

1. *.[weibo.com](http://weibo.com/)
2. *.[weibo.cn](http://weibo.cn/)
3. *.[sinaapp.com](http://sinaapp.com/)
4. *.[sina.com.cn](http://sina.com.cn/)
5. *.[sinajs.cn](http://sinajs.cn/)

iii.**Walled Garden List (Optional, you may skip this if there is no Instagram Login Enabled)**

1. *.[instagram.com](http://instagram.com/)
2. *.[akamaihd.net](http://akamaihd.net/)
3. *.[cdninstagram.com](http://cdninstagram.com/)

vi.**Twitter Login (Optional, you may skip this if there is no Twitter Login Enabled)**

1. *.[twitter.com](http://twitter.com/)
2. *.[twimg.com](http://twimg.com/)

vi.**LINE Login (Optional, you may skip this if there is no LINE Login Enabled)**

1. *.[line.me](http://line.me/)
2. *.[line-scdn.net](http://line-scdn.net/)

vi.**PayPal Login (Optional, you may skip this if there is no PayPal Login Enabled)**

1. *.[paypal.com](http://paypal.com/)
2. *.[paypalobjects.com](http://paypalobjects.com/)
3. [www.google-analytics.com](http://www.google-analytics.com/)

v.**Video Login (Optional, you may skip this if there is no Video Login Enabled)**

1. *.[akamaized.net](http://akamaized.net/)
2. *.[akamaihd.net](http://akamaihd.net/)
3. [ssl.google-analytics.com](http://ssl.google-analytics.com/)

1. *.[scorecardresearch.com](http://scorecardresearch.com/)
2. *.[vimeocdn.com](http://vimeocdn.com/)
3. *.[vimeo.com](http://vimeo.com/)
6. Click**OK**to save
5. Click**OK****to create SSID

## Step 4: Add AP to FansWiFi Admin Panel

- Login to FansWiFi Admin Panel
- Click**Settings -> Hotspots -> Create**
- Configure with following settings:

- **Venue:** Select the venue of where your Access Point locates
- **Hotspot Name:** Name each Access Point to make it identifiable
- **AP Type:** Select "Huawei eKit"
- **Mac Address:** Input unique MAC Address of each Access Point in your venue
- Click**Create**

![](../../../_images/information-required-for-fanswifi-manager-324.png)

![](../../../_images/information-required-for-fanswifi-manager-325.png)
