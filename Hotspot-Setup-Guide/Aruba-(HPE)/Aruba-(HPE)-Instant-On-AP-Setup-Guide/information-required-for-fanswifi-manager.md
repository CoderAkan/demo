# Information required for FansWiFi Manager


# Information required for FansWiFi Manager

- Mac Addresses of the APs (usually can be found at the back of the router)

# Tested model and firmware version

- Model: Aruba Instant-On AP11
- Firmware Version: 2.8.0

## Official documentation:

[https://www.arubainstanton.com/techdocs/en/content/intro/desktop/set-portal-des.htm](https://www.arubainstanton.com/techdocs/en/content/intro/desktop/set-portal-des.htm)

# Accessing the Aruba Instant-On AP

Setup the basic Aruba Instant-On account according to Aruba Instant-On’s setup guide and deployment guide

- Setup Guide:[https://www.arubainstanton.com/techdocs/en/content/get-started/prov-oc.htm](https://www.arubainstanton.com/techdocs/en/content/get-started/prov-oc.htm)
- Deployment Guide:[https://www.arubainstanton.com/files/Aruba_Instant_On_Deployment_Guide.pdf](https://www.arubainstanton.com/files/Aruba_Instant_On_Deployment_Guide.pdf)

- 1. According to Aruba’s setup guide, to add the AP to the Aruba Instant-On Portal in the initial setup, it is required that the AP is on the same network as your PC / Mobile / Laptop with a local IP address in the same network.
- 2. Then open a web browser:[https://portal.arubainstanton.com/](https://portal.arubainstanton.com/)or[https://portal.instant-on.hpe.com](https://portal.instant-on.hpe.com/)
- 3. Enter email and password to login, if you do not have an account, you can follow Aruba’s setup guide[https://www.arubainstanton.com/techdocs/en/content/get-started/prov-oc.htm](https://www.arubainstanton.com/techdocs/en/content/get-started/prov-oc.htm)to register and setup the Aruba Instant-On Portal

![](../../../_images/information-required-for-fanswifi-manager-8.png)

# Setting FansWiFi on Aruba Instant-On Cloud Portal

## Step 1:ClickNetworks/active networks

![](../../../_images/information-required-for-fanswifi-manager-9.png)

## Step 2:ClickCreate Networkat the top right corner to add a new network or choose a existing one

![](../../../_images/information-required-for-fanswifi-manager-10.png)

## Step 3:Choose the configurations like the following figure (you can choose your own network name) and clickSave

- a. Identification

- **i. Network Usage**: Guest
- **ii. Security**: None or Wi-Fi Enhanced Open
- **iii. Network Option:** Guest Portal (Checked)
- b. Click**Save**

![](../../../_images/information-required-for-fanswifi-manager-11.png)

- c. IP Assignment

- i.**IP Assignment:** Specific to This Network**(Suggested)**
- ii.**Base IP Address**: 172.16.0.0 (Or change to other network if needed)
- iii.**Subnet Mask:** 255.255.248.0 (2048 Clients)**(Suggested)**

![](../../../_images/information-required-for-fanswifi-manager-12.png)

## Step 4: Configure the Guest Portal

- **a. After configuring the SSIDs, move to the “Guest Portal” session**

![](../../../_images/information-required-for-fanswifi-manager-13.png)

## Step 5:Finish the settings according to the following configuration and screenshot

- a.**Type:** External
- b.**Portal URL:** [https://connect-p.fanswifi.com/auth](https://connect-p.fanswifi.com/auth)
- c.**Redirect URL:** [https://connect-p.fanswifi.com/auth?res=success](https://connect-p.fanswifi.com/auth?res=success)
- d.**Authentication:** Select “User authentication (default)”
- e.**Authentication Option:**

- i.**Require RADIUS Message-Authenticator:** Unchecked (Do not check)
- ii.**RADIUS Accounting:** Checked
- f.**Primary RADIUS Server**

- i.**Server IP address or domain name:** radius.fanswifi.com
- ii.**Shared Secret:** social123
- g.**Network Access Attributes**

- **NAS Identifier:** socialnas
- h.**NAS IP Address:** Select “Use device IP (default)”

![](../../../_images/information-required-for-fanswifi-manager-14.png)

## Step 6:For “Allowed domains” (Walled Garden) part, please follow below setup

- **a. Add FansWiFi domain (required)**

- **i.** fanswifi.com
- ii. cacerts.digitalcertvalidation.com
- iii. statusa.digitalcertvalidation.com
- iv. ocsp.digicert.com
- b. Select the Social Media you wish to use for Login if it is available on the list

- i. Aruba may update this list accordingly
-
- c. If your desire Social Media is not on Aruba’s default list, please add below domain accordingly

- **Walled Garden List (Optional, you may skip this if there is no Weibo Login Enabled)**

weibo.com

weibo.cn

sinaapp.com

sina.com.cn

sinajs.cn
- **Walled Garden List (Optional, you may skip this if there is no Instagram Login Enabled)**

instagram.com

akamaihd.net

cdninstagram.com
- **Twitter Login (Optional, you may skip this if there is no Twitter Login Enabled)**

twitter.com

twimg.com
- **LINE Login (Optional, you may skip this if there is no LINE Login Enabled)**

[http://line.me](http://line.me)

line-scdn.net
- **PayPal Login (Optional, you may skip this if there is no PayPal Login Enabled)**

paypal.com

paypalobjects.com

[www.google-analytics.com](http://www.google-analytics.com)
- **Video Login (Optional, you may skip this if there is no Video Login Enabled)**

akamaized.net

akamaihd.net

ssl.google-analytics.com

scorecardresearch.com

vimeocdn.com

vimeo.com

## Step 7:[Suggested]Access Control(Security Setting)

- a. Suggested to enable the “**Access Restrictions**” and select “**Network Destinations**” to prevent any device in the network being accessed by the WiFi guest. This is an important feature for protecting your own network.

- i. This can prevent WiFi Guest user to access any other devices in your network including your Router, POS Machine, Surveillance Camera, internal computer…etc.
- b. Allow user to access**Internet**only

![](../../../_images/information-required-for-fanswifi-manager-15.png)

## Step 8: Add AP to FansWiFi Admin Panel

- Login to FansWiFi Admin Panel
- Click**Settings -> Hotspots -> Add Hotspot**

- Configure with following settings:

- **Venue:** Select the venue of where your Access Point locates
- **Hotspot Name:** Name each Access Point to make it identifiable
- **AP Type:** Select “Aruba”
- **Mac Address:** Input unique MAC Address of each Access Point in your venue (Not controller)
- Click**Save**

![](../../../_images/information-required-for-fanswifi-manager-16.png)

![](../../../_images/information-required-for-fanswifi-manager-17.png)
