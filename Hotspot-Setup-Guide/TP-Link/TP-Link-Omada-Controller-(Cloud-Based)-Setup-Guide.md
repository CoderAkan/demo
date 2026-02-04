# TP-Link Omada (Cloud-Based) Setup Guide

This guide provides instructions for configuring TP-Link Omada Cloud-Based Controllers to work with the FansWiFi Manager platform.

## Information Required for FansWiFi Manager

- **MAC Addresses** of the APs
- **IP / Domain Name** of the Omada server
- **Hotspot Operator** username and password (Admin credentials are not required)

## Tested Model and Firmware Version

### Access Point
- **AP Model:** EAP265 (Standalone Mode, managed by EAP Controller)
- **Hardware Version:** 1.0
- **Firmware Version:** 5.0.6 Build 20220429 Rel. 44315

### Not Supported
- EAP115 Cluster Mode is **NOT** supported
- EAP110 and EAP120 are **NOT** supported
- Standalone EAPs (not managed by Omada Controller) are **NOT** supported

### Omada EAP Controller
- **Controller Firmware Version:** 5.15.16.40 (Omada Network System)
- **Note:** The EAP Controller software must be running at all times.

## Settings on TP-Link Omada Cloud-Based Controller

## Step 1: Configure DNS Setting (Optional)

> [!NOTE]
> This step is only for specific setups. Please contact FansWiFi support if needed.

## Step 2: Login to Omada Controller

- Start the EAP Local Controller (Omada) software and log in to the management page.

![Omada login page](../../../_images/information-required-for-fanswifi-manager-227.png)

## Step 3: Configure SSID

If you have already created an SSID, you can skip this step.

1. Click **Dashboard** on the left menu.
2. Select **Site List** on the top menu.
3. Select a site and click **Launch**.
4. Click **Settings** on the left menu.

![Omada settings menu](../../../_images/information-required-for-fanswifi-manager-228.png)

5. Under **Wired & Wireless Networks**, select **WLAN**.
6. Click **Create New Wireless Network**.

![Create new wireless network](../../../_images/information-required-for-fanswifi-manager-229.png)

7. Configure with the following settings:
   - **SSID Name:** (Your preferred SSID)
   - **Device Type:** EAP
   - **Guest Network:** Enabled
   - **Security:** None
8. Click **Apply**.

![WLAN configuration details](../../../_images/information-required-for-fanswifi-manager-230.png)

## Step 4: Configure Portal

1. Click **Settings** on the left menu.
2. Under **Authentication**, select **Portal**.

![Portal settings](../../../_images/information-required-for-fanswifi-manager-231.png)

3. Click **Create New Portal**.

![Create new portal](../../../_images/information-required-for-fanswifi-manager-232.png)

4. Configure the following:
   - **Portal Name:** FansWiFi Portal
   - **Portal:** Enabled
   - **SSID & Network:** Select the SSID created in Step 3.
   - **Authentication Type:** External Portal Server
   - **External Portal Server:** URL
   - **URL:** `https://connect-p.fanswifi.com/auth`
   - **HTTPS Redirection:** Disable
   - **Landing Page:** Selected Promotion URL
   - **URL:** `https://connect-p.fanswifi.com/auth?res=success`
5. Click **Apply**.

![Portal configuration details](../../../_images/information-required-for-fanswifi-manager-233.png)

## Step 5: Access Control Settings

1. Click **Access Control** on the top menu.

![Access control menu](../../../_images/information-required-for-fanswifi-manager-234.png)

2. Configure the following:
   - **Pre-Authentication Access:** Enabled
3. Click **Add** to include the following IP ranges:

| Policy Name | IP Range |
| :--- | :--- |
| Production 1 | 52.220.206.125/32 |
| Production 2 | 52.220.226.90/32 |
| Cloudflare 1 | 103.21.244.0/22 |
| Cloudflare 2 | 103.22.200.0/22 |
| Cloudflare 3 | 103.31.4.0/22 |
| Cloudflare 4 | 104.16.0.0/12 |
| Cloudflare 5 | 108.162.192.0/18 |
| Cloudflare 6 | 131.0.72.0/22 |
| Cloudflare 7 | 141.101.64.0/18 |
| Cloudflare 8 | 162.158.0.0/15 |
| Cloudflare 9 | 172.64.0.0/13 |
| Cloudflare 10 | 173.245.48.0/20 |
| Cloudflare 11 | 188.114.96.0/20 |
| Cloudflare 12 | 190.93.240.0/20 |
| Cloudflare 13 | 197.234.240.0/22 |
| Cloudflare 14 | 198.41.128.0/17 |

4. Click **Save**.

![Pre-authentication access configuration](../../../_images/information-required-for-fanswifi-manager-235.png)

## Step 6: Configure RADIUS Profile

1. Click **Settings** on the left menu.
2. Under **Authentication**, select **MAC-Based Authentication**.
3. Enable **MAC-Based Authentication**.
4. Click **Create New RADIUS Profile**.

![Create RADIUS profile](../../../_images/information-required-for-fanswifi-manager-236.png)

5. Configure the new profile:
   - **Profile Name:** FansWiFi Radius
   - **Authentication Server 1:**
     - **IP/URL:** 103.6.85.240
     - **Port:** 1812
     - **Password:** social123
   - **Accounting Server 1:**
     - **Enable RADIUS Accounting**
     - **IP/URL:** 103.6.85.240
     - **Port:** 1813
     - **Password:** social123
     - **Interim Update:** Enabled
     - **Interim Update Interval:** 300 Seconds
6. Click **Save**.

![RADIUS profile details](../../../_images/information-required-for-fanswifi-manager-237.png)

7. Finalize MAC-Based Authentication settings:
   - **SSID:** Select All
   - **RADIUS Profile:** FansWiFi Radius
8. Click **Apply**.

![Final MAC-based authentication settings](../../../_images/information-required-for-fanswifi-manager-238.png)

## Step 7: Get AP MAC Address

You will need the MAC address for Step 10. You can find it on the bottom of the device or in the controller:

1. Click **Devices** on the left menu.
2. Select **Access Points** on the top menu.
3. Note the MAC address of the AP you wish to add.

![Devices list in Omada](../../../_images/information-required-for-fanswifi-manager-239.png)

## Step 8: Create API Admin Account

This account is required for API calls from the FansWiFi Portal Server (used in Step 11).

1. Click **Hotspot** on the left menu.

![Hotspot menu](../../../_images/information-required-for-fanswifi-manager-240.png)

2. Select **Operators** and click **Create Operator**.

![Operators list](../../../_images/information-required-for-fanswifi-manager-241.png)

3. Configure the following:
   - **Administrator Type:** Local User
   - **Username:** (e.g., `FansWiFiAPI`)
   - **Password:** (Your chosen password)
   - **Role:** Admin
   - **Site Privileges:** Select the relevant site(s).
4. Click **Create**.

![Operator creation details](../../../_images/information-required-for-fanswifi-manager-242.png)

## Step 9: Get Controller Domain and ID

You can find the domain and controller ID in the browser URL when viewing the Hotspot section.

![Controller URL inspection](../../../_images/information-required-for-fanswifi-manager-243.png)

## Step 10: Add AP to FansWiFi Admin Panel

1. Log in to the FansWiFi Admin Panel.
2. Go to **Settings** > **Hotspots** > **Create**.
3. Configure the following:
   - **Venue:** Select the AP location.
   - **Hotspot Name:** Give the AP an identifiable name.
   - **AP Type:** Select **TP-Link EAP**.
   - **MAC Address:** Enter the AP MAC address (from Step 7).
4. Click **Save**.

![Hotspot creation in FansWiFi](../../../_images/information-required-for-fanswifi-manager-244.png)

## Step 11: Add API Profile in FansWiFi Admin Panel

1. Click **Venues & Login Portals** on the left menu.
2. Click **Edit** for the relevant venue.
3. Click **Controllers**.
4. Configure the following:
   - **TP-Link Omada Controller IP or URL:** `https://<your-controller-url>`
   - **Port Number:** 443 (or your configured port)
   - **Admin Username:** (The operator username from Step 8)
   - **Admin Password:** (The operator password from Step 8)
5. Click **Save**.

![Controller configuration in FansWiFi](../../../_images/information-required-for-fanswifi-manager-245.png)
