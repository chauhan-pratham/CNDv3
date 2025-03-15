# Configuring Security on a Wireless Router

A wireless router is a device that performs the functions of a router and includes the functions of a wireless access point.

### Lab Scenario
Organizations allow wireless devices to connect to their network in today’s environment (Bring Your Own Device or BYOD). However, the security of the network infrastructure is a major challenge for organizations while adopting wireless devices. A wireless router/access point is the main entry for attackers. Attackers compromise wireless access points to gain access to the organization’s network. Organizations should ensure that their wireless access points are configured securely. As a network defender, you should be able to configure the wireless router securely by applying all possible hardening techniques.

### Lab Objectives
This lab will demonstrate the various hardening techniques on a wireless router.

### Overview of Wireless Router Security
A wireless router is the first line of defense against attackers trying to access the organization’s network. To prevent attackers from compromising the security of wireless routers, appropriate configuration changes need to be made in order to make a router more secure.

### Lab Tasks
1. **Launch WebServer VM**
   - Click on Web Server to launch WebServer VM.
   - Click on Ctrl+Alt+Delete.
   - Log in with the username: **Administrator** and password: **admin@123**.

2. **Access Linksys Wireless Router Simulator**
   - Open Google Chrome.
   - Visit [Linksys Wireless Router Simulator](https://ui.linksys.com/LegacyRouters/WRT54G/v8/).

3. **Basic Setup**
   - Click on **Setup** > **Basic Setup**.
   - Specify:
     - Router Name: **Linksys-Router Setup**
     - Host Name: **host1**
     - Domain Name: **domain1**
   - Select **Auto** for MTU.
   - Provide Local IP Address as **192.168.1.254** and Subnet Mask as **255.255.255.0**.
   - Set DHCP Server to **Enable**.
   - Specify Starting IP Address and Maximum Number of DHCP Users.
   - Provide DNS Server IP addresses:
     - **208.67.222.222**
     - **208.67.220.222**
   - Click **Save Settings**.

4. **DDNS Configuration**
   - Click on the **DDNS** tab.
   - Select **Disable** from the drop-down for DDNS Service.
   - Click **Save Settings**.

5. **MAC Address Clone**
   - Click on **MAC Address Clone**.
   - Set MAC Clone to **Disable**.

6. **Advanced Routing**
   - Click on **Advanced Routing**.
   - Set Operating Mode to **Gateway**.
   - Specify Routing Details:
     - Router Name: **Linksys-Router**
     - Destination LAN IP: **10.10.10.20**
     - Subnet Mask: **255.255.255.0**
     - Default Gateway: **10.10.10.1**
   - Select Interface as **LAN & Wireless**.
   - Click **Save Settings**.

7. **Wireless Security Configuration**
   - Click on the **Wireless** tab.
   - Click **Basic Wireless Settings** and set **Wireless SSID Broadcast** to **Disable**.
   - Click **Wireless Security** and select:
     - Security Mode: **WPA2 Personal**
     - WPA Algorithms: **AES**
     - Enter a strong **WPA Shared Key**.
   - Click **Save Settings**.

8. **Wireless MAC Filter**
   - Click on **Wireless MAC Filter**.
   - Set Wireless MAC Filter to **Enable**.

9. **Firewall Settings**
   - Click on **Security**.
   - Enable:
     - **Block Anonymous Internet Requests**
     - **Filter IDENT (Port 113)**

10. **Access Restrictions**
   - Click **Access Restrictions**.
   - Under **Applications & Gaming**, enter:
     - Application Name
     - Start/End Port
     - Protocol
     - IP Address
     - Enable the rule.

11. **DMZ and QoS Configuration**
   - Click on the **DMZ** tab and set DMZ to **Disable**.
   - Click on the **QoS** tab and set QoS to **Disable**.

12. **Administration Settings**
   - Click on the **Administration** tab.
   - Set a **strong password** for the wireless router.
   - Under Web Access, set Access Server to **HTTPS**.
   - Set Remote Router Access to **Disable**.
   - Enable **Log** under the Log tab.

13. **Final Verification**
   - Click **Status** from the menu bar to review and confirm changes.

### Conclusion
By applying these configurations, a network defender can ensure that the wireless router is secured against potential threats, ensuring safer network access for organizational environments.

