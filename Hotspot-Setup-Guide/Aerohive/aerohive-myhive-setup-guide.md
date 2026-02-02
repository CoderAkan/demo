## Information required for FansWiFi Manager (AeroHive Cloud-Manager)

- **MAC addresses** of the access points (APs)

---

## Setting on AeroHive Cloud-Manager

### Step 1: Configure the Interfaces and User Access

Configure:
- **Captive Web Portal**
- **RADIUS Server**

![](../../../_images/information-required-for-fanswifi-manager-29.png)

---

### Step 2: Configuration: Radius Setting

Set:

- **RADIUS Server:** `radius.fanswifi.com`
- **Shared Secret:** `social123`
- **Authentication Port:** `1812`
- **Accounting Port:** `1813`

![](../../../_images/information-required-for-fanswifi-manager-30.png)

![](../../../_images/information-required-for-fanswifi-manager-31.png)

---

### Step 3: Configuration: Captive Web Portal

![](../../../_images/information-required-for-fanswifi-manager-32.png)

![](../../../_images/information-required-for-fanswifi-manager-33.png)

#### Login page settings

- **Authentication Method:** PAP
- **Login URL:** [https://connect-p.fanswifi.com/auth](https://connect-p.fanswifi.com/auth)
- **Password Encryption:** No Encryption (Plaintext)
- **Accounting Port:** `1813`

![](../../../_images/information-required-for-fanswifi-manager-34.png)

#### Success page settings

- **Show the success page after a successful login:** Disabled / Unchecked
- **After a successful login:** Redirect to an external page
- **Redirect URL:** [https://connect-p.fanswifi.com/auth?res=success](https://connect-p.fanswifi.com/auth?res=success)

![](../../../_images/information-required-for-fanswifi-manager-35.png)

#### Failure page settings

- **Show the failure page after a failed login:** Disabled / Unchecked
- **After a failed login:** Redirect to an external page
- **Redirect URL:** [https://connect-p.fanswifi.com/auth?res=failure](https://connect-p.fanswifi.com/auth?res=failure)

![](../../../_images/information-required-for-fanswifi-manager-36.png)

---

### Step 4: Optional advanced configuration (Walled Garden)

![](../../../_images/information-required-for-fanswifi-manager-37.png)

---

### Step 5: Walled Garden list

#### Walled Garden List (required)

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


---

### Step 6: Enable DNS ALG service

Enable **DNS ALG Service** in:

**Additional Settings → Service Settings → ALG Services**

1. Click **Edit** for **Additional Service**

![](../../../_images/aerohive_myhive_0.png)
2. Expand **Service Settings**
3. Click **Edit** for **ALG Services**

![](../../../_images/aerohive_myhive_1.png)
4. Check **Enable** for **DNS ALG Service**

![](../../../_images/aerohive_myhive_2.png)

---

### Step 7: Setup in FansWiFi Admin Panel

1. Log in:
   - [https://admin-p.fanswifi.com](https://admin-p.fanswifi.com)

2. Go to:
   - **Settings → Hotspots → Add Hotspot**

3. Configure:
   - **Venue:** Select the venue where the AP is located
   - **Hotspot Name:** A name to identify the AP
   - **AP Type:** **Aerohive**
   - **MAC Address:** Enter the AP MAC address

4. Click **Save**

![](../../../_images/information-required-for-fanswifi-manager-38.png)
