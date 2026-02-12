# Connect TP-Link EAP to Omada Controller (Self-Hosted)

## Step 0: Connect TP-Link EAP to Omada Local Controller

* a. Connect the TP-Link EAP device to the controller
* b. Download and Open Omada Discovery Utility (4.1.4)
  * You can download it from [here](https://support.omadanetworks.com/hk/product/omada-software-controller/#EAP_Discovery_Tool)
* c. You should find the TP-Link EAP device information from Omada Discovery Utility
* d. Choose the device that you want to connect to Omada Controller, then click "Manage"

![](../../.gitbook/assets/tp_link_connect_0.png)

* e. Config the following settings:
  * **Controller IP/Inform URL:** `<your-controller-ip-address-or-url>:8043`
  * **Username:** `admin`
  * **Password:** `admin`
    * The username and password are based on default setting of EAP device, it may be differ
    * If you not sure EAP username and password, please reset EAP device and enter the default username and password
  * Click "Apply"
  * When the status become "Setting Succeed", the device should successfully connect to Omada Controller

![](../../.gitbook/assets/tp_link_connect_1.png)

*   f. Login to Microsoft Azure, then click "Networking" and "Network settings" from the left menu

    * Enable the following ports for the controller
      * ICMP Any
      * Any 80, 443, 8088, 8043, 8843
      * UDP 19810, 29810, 27001
      * TCP 29811-29816, 27002, 27017, 27217

    ![](../../.gitbook/assets/tp_link_connect_2.png)
*   g. The device should appear on the Omada Controller

    ![](../../.gitbook/assets/tp_link_connect_3.png)
