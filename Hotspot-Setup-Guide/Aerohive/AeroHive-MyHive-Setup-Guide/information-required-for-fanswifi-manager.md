# Information required for FansWiFi Manager

- Mac Addresses of the APs

# Setting on AeroHive Cloud-Manager

## Step 1: Configure the Interfaces and User Access

**Configure:** Captive Web Portal, Radius Server

![](../../../_images/information-required-for-fanswifi-manager-29.png)

## Step 2: Configuration: Radius Setting

1. **Radius Server:** [radius.fanswifi.com](http://radius.fanswifi.com/)
2. **Shared Secret:** social123
3. **Authentication Port:** 1812
4. **Accounting Port:** 1813

![](../../../_images/information-required-for-fanswifi-manager-30.png)

![](../../../_images/information-required-for-fanswifi-manager-31.png)

## Step 3: Configuration: Captive Web Portal

![](../../../_images/information-required-for-fanswifi-manager-32.png)

![](../../../_images/information-required-for-fanswifi-manager-33.png)

- **Captive Web Portal Login Page Setting**

- Authentication Method: PAP
- Login URL:[https://connect-p.fanswifi.com/auth](https://connect-p.fanswifi.com/auth)
- Password Encryption: No Encryption (Plaintext)
- Accounting Port: 1813

![](../../../_images/information-required-for-fanswifi-manager-34.png)

- **Captive Web Portal Success Page Setting**

- Show the success page after a successful login: Uncheck
- After a successful login: Redirect to an external page
- Use simple URL address:[https://connect-p.fanswifi.com/auth?res=success](https://connect-p.fanswifi.com/auth?res=success)

![](../../../_images/information-required-for-fanswifi-manager-35.png)

- **Captive Web Portal Failure Page Setting**

- Show the failure page after a successful login: Uncheck
- After a successful login: Redirect to an external page
- Use simple URL address:[https://connect-p.fanswifi.com/auth?res=failure](https://connect-p.fanswifi.com/auth?id=aerohive&res=failure)

![](../../../_images/information-required-for-fanswifi-manager-36.png)

## Step 4: Optional Advanced Configuration

- **Walled Garden**

![](../../../_images/information-required-for-fanswifi-manager-37.png)

## Step 5: Walled-Garden List

1. **FansWiFi Server**

1. [fanswifi.com](http://fanswifi.com/)
2. **For Facebook Login** (Optional, you may skip this if there is no Facebook Login Enabled)

1. [facebook.com](http://facebook.com/)
2. [facebook.net](http://facebook.net/)
3. [fbcdn.net](http://fbcdn.net/)
4. [fbcdn.com](http://fbcdn.com/)
5. [akamaihd.net](http://akamaihd.net/)
6. [www.google.com](http://www.google.com/)
7. [doubleclick.net](http://doubleclick.net/)
8. [www.google.us](http://www.google.us/)(Local Google URL of your Country / Region)

1. Example:

1. EU:[www.google.eu](http://www.google.eu/)
2. UK:[www.google.co.uk](http://www.google.co.uk/)
3. Hong Kong:[www.google.com.hk](http://www.google.com.hk/)
4. Japan:[www.google.co.jp](http://www.google.co.jp/)
5. Taiwan:[www.google.com.tw](http://www.google.com.tw/)
6. Thailand:[www.google.co.th](http://www.google.co.th/)
7. Malaysia:[www.google.com.my](http://www.google.com.my/)
8. Myanmar:[www.google.com.mm](http://www.google.com.mm/)
3. **For Weibo Login** (Optional, you may skip this if there is no Weibo Login Enabled)

1. [weibo.com](http://weibo.com/)
2. [weibo.cn](http://weibo.cn/)
3. [sinaapp.com](http://sinaapp.com/)
4. [sina.com.cn](http://sina.com.cn/)
5. [sinajs.cn](http://sinajs.cn/)
4. **For Instagram Login** (Optional, you may skip this if there is no Instagram Login Enabled)

1. [instagram.com](http://instagram.com/)
2. [cdninstagram.com](http://cdninstagram.com/)
3. [akamaihd.net](http://akamaihd.net/)
5. **For Twitter Login** (Optional, you may skip this if there is no Twitter Login Enabled)

1. [twitter.com](http://twitter.com/)
2. [twimg.com](http://twimg.com/)
6. **For Video Login** (Optional, you may skip this if there is no Video Login Enabled)

1. [akamaized.net](http://akamaized.net/)
2. [akamaihd.net](http://akamaihd.net/)
3. [ssl.google-analytics.com](http://ssl.google-analytics.com/)
4. [scorecardresearch.com](http://scorecardresearch.com/)
5. [vimeocdn.com](http://vimeocdn.com/)
6. [vimeo.com](http://vimeo.com/)

## Step 6: Enable the DNS ALG service

**Enable the DNS ALG service in the Additional Settings > Service Settings > ALG Services section of the network policy**

ALG Service > Edit >  DNS“Checked”

Please see the below setting flow:

1. Click “Edit” of “Additional Service”
​
2. Expand “Service Settings”
3. Click “Edit” button on “ALG Services”
4. Check “Enable” checkbox for “DNS ALG Service”

## Step 7: Setup in FansWiFi Admin Panel

1. Log in to FansWiFi Admin Panel

1. [https://admin-p.fanswifi.com](https://admin-p.fanswifi.com/)
2. Click “Settings” -> “Hotspots” -> “Add Hotspot”

1. **Venue:** Select the venue of where your Access Point locates
2. **Hotspot Name:** Name each Access Point to make it identifiable
3. **AP Type:** Select “Aerohive”
4. **Mac Address:** Input unique MAC Address of each Access Point in your venue
3. Click “Save”

![](../../../_images/information-required-for-fanswifi-manager-38.png)
