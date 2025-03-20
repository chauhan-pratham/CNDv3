# Analyzing and Examining Various Network Packet Headers using Wireshark

### Lab Scenario
Each packet in a network contains control information and user data, also known as the payload. The control information contains data for delivering the payload, which includes, for example, source and destination IP and MAC addresses and sequencing information. The header part of the packet stores this control information. Hence, the network administrator needs to know how to examine the packet headers while also examining the data packets.

### Lab Objectives
The objective of this lab is to help students learn how to inspect TCP/IP packet header fields of different network packets.

### Overview of Wireshark Packet Capture
In packet capture, data packets traversing over a network are intercepted using packet capture tools such as Wireshark. These captured packets are analyzed in order to determine whether proper network security policies are being followed.

### Lab Tasks

1. **Launch Smoothwall Firewall VM:**  
   - Click on "Smoothwall Firewall".  
   - Type `toor` as the password and press **Enter**.  
   - Press **Tab** twice to navigate to the **Done** button and press **Enter**.  
   - Wait for the Smoothwall Firewall machine to load.  

2. **Launch AdminMachine-1 VM:**  
   - Click on **AdminMachine-1**.  
   - Click **Ctrl + Alt + Delete** to log in.  
   - Type `admin@123` as the password and press **Enter**.  

3. **Disable Microsoft Defender Antivirus:**  
   - Right-click the **Windows** button and click **Run**.  
   - Type `gpedit.msc` and click **OK**.  
   - Navigate to **Local Computer Policy** → **Computer Configuration** → **Administrative Templates** → **Windows Components** → **Microsoft Defender Antivirus**.  
   - Double-click **Turn off Microsoft Defender Antivirus** policy.  
   - Choose **Enabled**, click **Apply**, and click **OK**.

4. **Install Cain & Abel:**  
   - Navigate to `E:\CND-Tools\CNDv3 Module 14 Network Traffic Monitoring and Analysis\Cain&Abel`.  
   - Extract the `ca_setup.exe` file.  
   - Enter the password `darknet123` when prompted.  
   - Follow the installation steps.  
   - Click **Don’t Install** when the WinPcap prompt appears.

5. **Configure Cain & Abel:**  
   - Click the **Configure** option from the menu bar.  
   - Click the **Sniffer** tab, select the adapter with IP `10.10.10.2`, click **Apply**, and then **OK**.  
   - Click the **Start/Stop Sniffer** icon.  

6. **Scan for MAC Addresses:**  
   - Click the **Sniffer** tab.  
   - Click the **+** icon or right-click and select **Scan MAC Addresses**.  
   - Select **Range** and enter IP range: `10.10.10.1` to `10.10.10.254`.  
   - Click **OK**.

7. **Poison ARP Traffic:**  
   - Click the **APR** tab.  
   - Click **+**, select `10.10.10.16` (Web Server) in the left pane and `10.10.10.50` (Attacker Machine) in the right pane, and click **OK**.  
   - Click the **Start/Stop APR** yellow icon to begin poisoning.

8. **Capture Packets in Wireshark:**  
   - Open Wireshark.  
   - Select **Ethernet 2** as the interface and click the **Start Capture** icon.  
   - Click the **Stop Capture** icon after capturing packets.  

9. **Analyze Captured Packets:**  
   - Click on various packets such as **ARP**, **TCP**, **HTTP**, **ICMP**, and **DNS**.  
   - Expand the respective protocol nodes in the **Packet Details** pane to analyze each field.

10. **Check Key Packet Fields:**  
   - **ARP Packet Fields:** Source IP, Destination IP, MAC addresses, etc.  
   - **TCP Packet Fields:** Source port, destination port, sequence number, etc.  
   - **HTTP Packet Fields:** Request type, user agent, etc.  
   - **ICMP Packet Fields:** Type, code, checksum, etc.  
   - **DNS Packet Fields:** Identifier, response flag, recursion desired, etc.

11. **Analyze Statistics:**  
   - Go to **Statistics** → **IPv4 Statistics** → **Destinations and Ports**.

12. **Close All Windows:**  
   - Close Wireshark and Cain & Abel.  
   - If an **Unsaved packets** prompt appears, click **Quit without Saving**.

### Conclusion
By following these steps, a network defender can analyze various network packet headers and examine the details for better security monitoring and assessment.

