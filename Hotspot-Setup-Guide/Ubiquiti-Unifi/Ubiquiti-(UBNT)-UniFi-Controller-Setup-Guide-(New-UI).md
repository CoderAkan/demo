## Information required for FansWiFi Manager

- Mac Addresses of the APs
- IP / Domain Name of Ubnt UniFi server (Public IP Address that can be accessed via Internet)

    - Please make sure the IP Address is accessible by our IP Addresses below

        - '''
        52.220.208.185

        52.220.215.219

        52.220.219.128

        52.77.30.253

        52.220.226.90

        52.220.206.125
        '''

        - For security reasons, it's recommended to restrict the access of the public IP of the controller and put our IP Addresses in the allow list of your firewall.

- API User's username and password

## Controller Requirement

{% hint style="info" ub%}
Controller and/or Cloud Key are required to be always ON and connected to the Internet
{% endhint %}

- Ubiquiti Unifi Cloud Key <br>
​[https://www.ubnt.com/unifi/unifi-cloud-key/](https://www.ubnt.com/unifi/unifi-cloud-key/)

![](../../../_images/ubi_0.png)
​
- Ubiquiti "UniFi Network Server" installed on Windows / macOS / Linux Server (Debian / Ubuntu)

    - Related Articles

        - Download Link:[https://ui.com/download/releases/network-server](https://ui.com/download/releases/network-server)
    - Ubnt: Self-Hosting a UniFi Network Server
        - [https://help.ui.com/hc/en-us/articles/360012282453-Self-Hosting-a-UniFi-Network-Server](https://help.ui.com/hc/en-us/articles/360012282453-Self-Hosting-a-UniFi-Network-Server)

## Tested Model and Firmware Version

- UniFi Network Server

    - Controller Firmware Version: Network 8.3.32
- UniFi Cloud Key:

    - AP Model: 3.3.20.4019
    - Controller Firmware Version: 5.6.22 (Build: atag_5.6.22_10205)
- UniFi Controller Software:

    - AP Model: 3.3.20.4019
    - Controller Firmware Version: 5.6.22 (Build: atag_5.6.22_10205)

{% hint style="warning" %}
Note that different models may have different interface
{% endhint %}

## Network Topology

![](../../../_images/information-required-for-fanswifi-manager-1.png)

## Setting on Ubiquiti UniFi AP

### Step 1: Configure Router's DHCP Server DNS Setting of the WiFi Network

- **This Step is REQUIRED if you have set any Social Login (e.g. Facebook Login) to your network**

    - If this step is not finished, Social Login process may not be workable on some mobile device
    - If you do not use Social Login. You may skip this step.
- **Aim**

    - FansWiFi UBNT UniFi Controller configuration require WiFi user to use FansWiFi DNS Server
    
    - This is a key step because UBNT UniFi Controller does not support domain-based Walled Garden Setting for white-listing Social Media website for Social Login purpose

        - The AP type in this article only supports IP-Based Walled Garden. You only whitelist IP-Range but you cannot whitelist the whole domain of Social Media such as *.facebook.com.
        - Usually, Social Login do not work on AP that only support IP-Based Walled Garden since Social Network's IP Range is usually unknown. And the IP Range can be changed anytime by the Social Media provider.
        - FansWiFi's proprietary technology makes it possible for AP that support only IP-Based walled garden to use Social Login service. This is a unique feature provided by FansWiFi
    - After finishing this step, Android's Captive Portal browser will not be closed automatically after authentication
- **Configuration**

    - Optional [For specific setup only]

            - Please contact FansWiFi support if needed.

![](../../../_images/information-required-for-fanswifi-manager-2.png)

### Step 2: Configure the Ubiquiti UniFi AP

- a. Login to access the UniFi Dashboard
- b. Click "Setting" on the left menu

![](../../../_images/information-required-for-fanswifi-manager-3.png)

### Step 3: Configuration: Wireless Networks

- a. Click "WiFi" on the left sub-menu
- b. Click "Create New"

![](../../../_images/information-required-for-fanswifi-manager-4.png)

- c. Configure with the following settings:

    - **Name/SSID:** - FansWiFi Free WiFi -
    - **Advanced:** Manual
    - **Hotspot Portal:** Enable
    - **Security Protocol:** Open
- d. Click "Add WiFi Network"

![](../../../_images/information-required-for-fanswifi-manager-5.png)

### Step 4: Configuration: Guest Control

- a. Click the WiFi that you just created

![](../../../_images/ubi_1.png)

- b. Click "Guest Control" from the WiFi Setting

![](../../../_images/ubi_2.png)

- c. Select "Branding" and Configure with following settings:

    - Success Landing Page: Custom URL
       - Custom URL:[https://connect-p.fanswifi.com/auth?res=success](https://connect-p.fanswifi.com/auth?res=success)
    - Click "Save"

    ![](../../../_images/ubi_3.png)

- d. Select "Authentication" and Configure with following settings:

    - External Portal Server: Enable
        - Click "Edit" to External Portal Server
        - External Portal: 52.220.206.125
            - You can determine the IP address by entering the code "ping connect-p.fanswifi.com" through terminal
    - Click "Save"
- Click "Save"

![](../../../_images/ubi_4.png)

![](../../../_images/ubi_5.png)

e. Select "Settings" and Configure with following settings:

- **Landing Page Settings**

    - **HTTPs Redirection Support: Disable**
    - **Secure Portal: Enable**
    - **Domain: Enable**

        - **Domain (https://):** [connect-p.fanswifi.com](http://connect-p/fanswifi.com)
- **Authorization Access: Pre-Authorization Allowances**

    - Please click "Add Hostname, IP or Subnet" and enter one of the following IP address
    - Repeat this step until all the IP address are added into the system

        - **Pre-Authorization Access (Required):**
            '''
            52.220.206.125/32
            52.220.226.90/32
            '''
        - **Pre-Authorization Access (FansWiFi CDN) (Required):**
            '''
            103.21.244.0/22
            103.22.200.0/22
            103.31.4.0/22
            104.16.0.0/12
            108.162.192.0/18
            131.0.72.0/22
            141.101.64.0/18
            162.158.0.0/15
            172.64.0.0/13
            173.245.48.0/20
            188.114.96.0/20
            190.93.240.0/20
            197.234.240.0/22
            198.41.128.0/17
            '''
- **Pre-Authorization Access (Only for Facebook):**
    '''
    31.13.24.0/21
    31.13.64.0/18
    45.64.40.0/22
    66.220.144.0/20
    69.12.56.0/21
    69.63.176.0/20
    69.171.224.0/19
    74.119.76.0/22
    103.4.96.0/22
    129.134.0.0/16
    157.240.0.0/16
    173.252.64.0/18
    179.60.192.0/22
    185.60.216.0/22
    204.15.20.0/22
    '''
- Click "Save" after completing the settings

![](../../../_images/information-required-for-fanswifi-manager-6.png)

### Step 5: Configuration: RADIUS Profiles

- a. Click "Settings" > "Profiles" on the left sub-menu
- b. Click "RADIUS" on the top sub-menu
- c. Click "Create New"

![](../../../_images/ubi_6.png)

- d. Configure with the following settings:

    - **Profile Name:** FansWiFi Radius
    - **RADIUS Auth Server:**
        - **IP Address:** 103.6.85.240
        - **Port:** 1812
        - **Password/Shared Secret:** social123
    - **Accounting:** Enable
    - **Interim Update:** Enable
    - **Interim Update Interval:** 300
    - **RADIUS Accounting Server:**
        - **IP Address:** 103.6.85.240
        - **Port:** 1813
        - **Password/Shared Secret:** social123
    - Click "Apply Changes"

![](../../../_images/ubi_7.png)

### Step 6: Setup Admins

- In order to create admin account without email address for API access, you could create the account in the Legacy Interface instead of the new interface.
- a. Change to Old UI

    - Click "Settings" on the left menu
    - Click "System" on the left sub-menu
    - Click "Advanced" on the top sub-menu
    - Click "Use Legecy"

    ![](../../../_images/ubi_8.png)

- b. Add New Admin

    - Click "Settings" on the left menu
    - Click "Admins" on the left sub-menu
    - Click "Add New Admin"

    ![](../../../_images/ubi_9.png)

- c. Configure with the following settings:

    - **Invite to Controller:** Manually set and share the password
    - **Name:** \<your-admin-id\> (e.g. FansWiFiAPI)
    - **Password:** \<your-password\>
        - **Require the user to change their password:** Disabled
    - **Email:** \<your-email\>
    - **Role:** Administrator
    - **Site Permissions:**
        - **Allow devices adoption:** Disable
    - **Global Permissions:**
        - **Show pending devices:** Disable
    - Click "Create"

    ![](../../../_images/ubi_10.png)

- d. Change to New UI

    - Click "Settings" on the left menu
    - Click "User Interface" on the left sub-menu
    - Click "Apply Changes"

### Step 7: Get the MAC address of the AP

- Click "UniFi Devices" on the main menu
- Click the AP device from the list, which is the one you want to put into FansWiFi Admin Panel.
- You can see the MAC Address from the "Overview" top menu

![](../../../_images/ubi_11.png)

### Step 8: Add AP to FansWiFi Admin Panel

- Login to FansWiFi Admin Panel
- Click **Settings -> Hotspots -> Add Hotspot**

- Config with following settings

    - **Venue:** Select the venue of where your Access Point locates
    - **Hotspot Name:** Name each Access Point to make it identifiable
    - **AP Type:** Select “Ubiquiti UniFi”
    - **Mac Address:** Input unique MAC Address of each Access Point in your venue (Not controller)
- Click **Save**

![](../../../_images/ubi_12.png)

### Step 9: Add API Profile in FansWiFi Admin Panel

- a. Click "Venues & Login Portals" on the left menu
- b. Click "Edit" on the venue where your Ubiquiti UniFi AP would be used for WiFi Login

![](../../../_images/ubi_13.png)

- c. Click "Controllers"
- d. Configure with the following settings:

    - **Ubiquiti UniFi IP Address or URL:** <your-unifi-ip-address-or-url>
    - **Port Number (Default: 8443):** <your-unifi-controller-port>
    - **Admin Username:** <your-admin-id> (Configured in Step 6, i.e. FansWiFiAPI)
    - **Admin Password:** <your-admin-password> (Configured in Step 6)
- e. Click "Save"

- **Please make sure our server can reach your UniFi Controller's 8443 port**

    - Below are the IP Addresses of our servers calling UniFi via 8443 port
        '''
        52.220.208.185
        52.220.215.219
        52.220.219.128
        52.77.30.253
        52.220.226.90
        52.220.206.125
        '''

![](../../../_images/information-required-for-fanswifi-manager-7.png)

​
