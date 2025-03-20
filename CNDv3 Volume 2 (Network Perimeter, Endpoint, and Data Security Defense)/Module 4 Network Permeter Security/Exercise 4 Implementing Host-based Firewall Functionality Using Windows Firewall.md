### Lab Exercise: Implementing Host-based Firewall Functionality Using Windows Firewall

**Objective:** Configure the Windows Firewall on an individual endpoint to enhance security by restricting remote access.

#### Overview of Host-based Firewall
A host-based firewall, such as Windows Firewall, protects individual systems by filtering incoming and outgoing traffic, blocking malicious communications, and enforcing security policies.

#### Steps to Configure Windows Firewall

1. **Launch Required VMs:**
   - If not already running, launch the **Smoothwall Firewall**, **AD Domain Controller**, and **Admin Machine-1** VMs.
   - Log in to each VM as specified in the original instructions.

2. **Access Finance-Dept VM:**
   - In the **Admin Machine-1 VM**, open **Remote Desktop Connection**.
   - Enter the IP address `20.20.10.10` of the **Finance-Dept VM** and click **Connect**.
   - Log in with Username `Finance-Dept\Alice` and Password `user@123`.
   - Accept the Security Certificate if prompted.

3. **Open Windows Firewall Settings:**
   - Switch to the **Finance-Dept VM**.
   - Open the **Control Panel** and navigate to **System and Security**.
   - Click on **Windows Defender Firewall** and ensure it is turned on for Domain, Private, and Public networks.
   - Click on **Advanced Settings** in the left pane.

4. **Block Remote Desktop Access:**
   - In the **Windows Defender Firewall with Advanced Security** window, click on **Inbound Rules**.
   - Search for and double-click on **Remote Desktop - Shadow (TCP-In)**.
     - Select **Block the connection**, then click **Apply** and **OK**.
   - Repeat the process for:
     - **Remote Desktop - User Mode (TCP-In)**
     - **Remote Desktop - User Mode (UDP-In)**
   - Ensure all three rules are set to block connections.

5. **Verify Firewall Configuration:**
   - Close all open windows.
   - Switch back to the **Admin Machine-1 VM**.
   - Attempt to connect to the **Finance-Dept VM** using Remote Desktop by entering the IP address `20.20.10.10` and clicking **Connect**.

6. **Check Connection Status:**
   - You should receive an error message indicating that the connection cannot be established. This confirms that the Windows Firewall is successfully blocking remote access.

By following these steps, you have effectively configured the Windows Firewall on the Finance-Dept VM to block remote desktop access, thereby enhancing the security of the individual endpoint within the network.