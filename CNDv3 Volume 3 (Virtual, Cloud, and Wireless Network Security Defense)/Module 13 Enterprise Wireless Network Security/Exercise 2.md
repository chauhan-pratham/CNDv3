# TP-Link Wireless Router Security Configuration Guide

## Introduction
This guide outlines step-by-step instructions to configure a TP-Link wireless router securely. By implementing these settings, you can improve the overall security of your wireless network, preventing unauthorized access and ensuring data integrity.

## Lab Objectives
- Configure key security settings on a TP-Link wireless router.
- Implement security hardening techniques to mitigate potential threats.

## Steps for Configuring Wireless Router Security

### Step 1: Access the TP-Link Router Interface
1. Launch the **Web Server** machine.
2. Click **Ctrl+Alt+Delete**.
3. Log in with:
   - **Username:** Administrator
   - **Password:** admin@123
4. Open **Google Chrome** and navigate to:
   ```
   https://emulator.tp-link.com/webpages_c7v5_20220414/index.html
   ```
5. The TP-Link router interface window will appear.

### Step 2: Quick Setup
1. Click on the **Quick Setup** tab.
2. Select **Time Zone** (e.g., `GMT-08:00 Pacific Time`) and click **Next**.
3. In **Internet Connection Type**, select **Dynamic IP** and click **Next**.
4. Select **Do NOT Clone MAC Address** and click **Next**.
5. Under **Smart Connect**, ensure **Enable** is selected and **Hide SSID** is checked.
6. Click **Yes** if prompted about unencrypted networks.
7. Click **Save** under the **Summary** section.
8. Click **Advanced** to proceed.

### Step 3: Network Configuration
1. Expand the **Network** section and select **Internet**.
2. Ensure **Dynamic IP** is selected under **Internet Connection Type**.
3. Scroll down and expand the **Advanced** drop-down.
4. Select **Use the following DNS Addresses**.
5. Enter the following DNS addresses:
   - **Primary DNS:** `208.67.222.222`
   - **Secondary DNS:** `208.67.220.220`
6. Click **Save**.
7. Select **LAN** under **Network** settings.
8. Enter the LAN IP Address as `10.10.10.20` and click **Save**.

### Step 4: Wireless Settings
1. Expand the **Wireless** section and select **Wireless Settings**.
2. Ensure **Hide SSID** is enabled under **Network Name (SSID)**.
3. Select **WPA/WPA2-Personal (Recommended)** for **Security**.
4. Set **Version** to **Auto** and **Encryption** to **AES**.
5. Provide a **strong password** in the **Password** field.
6. Click **Save**.

### Step 5: Guest Network Configuration
1. Select **Guest Network** under **Advanced**.
2. Ensure the option **Allow guests to see each other** is disabled.
3. Click **Save**.

### Step 6: QoS Configuration
1. Select the **QoS** tab under **Advanced**.
2. Ensure the **Enable QoS** option is unchecked.
3. Click **Save**.

### Step 7: NAT Forwarding Configuration
1. Under **NAT Forwarding**, select **DMZ**.
2. Ensure **Enable DMZ** is unchecked.
3. Click **Save**.

### Step 8: System Administration
1. Expand the **System Tools** section and select **Administration**.
2. Scroll down to the **Advanced** tab.
3. Ensure **Remote Management** is disabled.
4. Click **Save**.

### Step 9: Finalizing and Verifying Settings
1. Click on **Status** from the menu bar to review the configured settings.
2. As this is a simulation, settings may not be saved; however, these steps should be replicated on a live TP-Link router for effective security.

## Conclusion
By following these steps, you will have implemented key security configurations on your TP-Link wireless router. These settings will help mitigate common security threats and improve your network's overall protection.

