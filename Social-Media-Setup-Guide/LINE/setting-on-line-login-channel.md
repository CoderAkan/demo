# Setting on LINE Login Channel

## Step 1: Login to LINE Developers Console
 
1. Access the **Line Developers Console** by opening a Web Browser [https://developers.line.biz](https://developers.line.biz)
2. Click **Login in to Console** on the top right conner
3. Select **Business account**
4. Login by entering your email and password

## Step 2: Create a new Provider

1. Select **Provider** on the left menu
2. Click **Create a new provider**

1. ​
3. **Provider name:** <provider-name-you-prefer> (e.g. FansWiFi Provider)
4. Click **Create**

1.

## Step 3: Create a new Channel

1. After creating provider, Click **Channels** on the top sub-menu
2. Click **Create a LINE Login Channel**

1.
3. Configure with the following settings:

1. **Region to provide the service:** Japan / Thailand / Taiwan / Indonesia
2. **Company or owner's country or region:** (e.g. Thailand)
3. **Channel name:** <channel-name-you-prefer> (e.g. FansWiFi Login)
4. **Channel description:** <channel-description-you-prefer> (e.g. Social Login)
5. **App types:** Web app
6. **Require two-factor authentication:** Disable
7. Click **Create** to add a new channel

1. 
2.

## Step 4: Enable Messaging API in LINE Manager Console

1. Access the **LINE Manager Console** by opening a Web Browser [https://manager.line.biz/](https://manager.line.biz/)
2. Login by entering your email and password
3. Click **Settings** on the top menu
4. Select **Settings > Messaging API** on the left menu
5. Click **Enable Messaging API**
6. In **Select Provider** session, choose the provider that you created in step 2
7. Click **Agree**
8. Click **OK**, then click **OK**
9. After that, messaging API should be successfully created

## Step 5: Channel Basic Settings Configuration

1. Login and Access to **LINE Developers Console**
2. Click **Providers** on the left menu, then select the provider that you created
3. Click **Channels** on the top menu, then select the channel that you created
4. Select **Basic Settings** on the top menu
5. From **Linked LINE Official Account**

1. Click **Edit**
2. Select the option that include your LINE official account ID and name
3. Click **Update**
6. For **Email address permission**

1. Click **Apply**
2. For **Screenshot**, please upload the following screenshot

1. Please perform **right click** and select **Save Image As...** to download the screenshot as PNG file into your computer
2. Upload this PNG file to **LINE Developers Console** from your computer
3.
3. Click **Submit**

1.
7. Change the channel status from **Developing** to **Published**

1. **Developing** button could be obtained near the channel name
2. Then, click the **Developing** button
3. Click **Publish** to publish the channel
4. After that, the channel status should be **Published**

## Step 6: LINE Login Callback URL Configuration

1. Select **LINE Login** on the top menu
2. Configure with the following settings:

1. **Use LINE Login in your web app:** Enable
2. **Callback URL**

1. Click **Edit**
2. Enter the the following URL:

1. [https://connect-p.fanswifi.com/line/callback](https://connect-p.fanswifi.com/line/callback)
3. Click **Update**

## Step 7: Add Channel ID and Secret to FansWiFi Admin Panel

1. Select **Basic Settings** on the top menu
2. You can obtain **Channel ID** and **Channel Secret** in basic information of the channel
3. Login to FansWiFi Admin Panel
4. Click **Settings -> Venue & Login Portals**
5. Click **Edit** on the venue that you want to enable LINE login
6. Select **LINE** on the left menu
7. Configure with the followings settings:

1. **Enable:** Enable
2. **Login Type:** Advanced
3. **LINE Login Channel ID:** Obtain from channel details
4. **LINE Login Channel Secret:** Obtain from channel details
5. **LINE Official Account Name:** Your line official account name
6. Click **Save**
