# Network Diagram


# Network Diagram

![](../../../_images/network-diagram-167.png)

For some APs, you have to configure DNS settings on your **Router** to use FansWiFi service.

# Main Steps

## Step 1: Access Router Configuration Page

## Step 2: Navigate to Network or LAN Setting

## Step 3: Set Static DNS Server under DHCP Server Configuration

- Input the following FansWiFi DNS Servers:

- 223.197.92.30 (dns01.fanswifi.com)
- 34.150.88.223 (dns02.fanswifi.com)

# Example

Linksys routers: E1200, E1500, E2500, E3200, E4200, WRT160n

## Step 1: Log in to Linksys Router Configuration Page

1. Connect your device to router in same network
2. Entering 192.168.1.1 by opening a browser (or the IP Address of your router)
3. Default Login:
Login ID: admin
Password: admin

## Step 2: Network Setup

1. Click **Setup > Basic Setup** on the top menu, then **Network Setup** on the left menu
2. Configure with following settings:

1. **Static DNS 1:** 223.197.92.30
2. **Static DNS 2:** 34.150.88.223
​
3. Click **Save**

# Huawei HG8245H

## Step 1: Log in to Huawei Router Configuration Page

1. Connect your device to router in same network
2. Entering 192.168.100.1 by opening a browser (or the IP Address of your router)
3. Default Login:
Login ID: telecomadmin
Password: admintelecom

## Step 2: DHCP Server Configuration

1. Click **LAN** on the top menu, then **DHCP Server Configuration** on the left menu
2. Configure with following settings:

1. **Enable primary DHCP server:** Enable
2. **Enable DHCP L2Relay:** Enable
3. **Primary DNS Server:** 223.197.92.30
4. **Secondary DNS Server:** 34.150.88.223
​
3. Click **Save**
