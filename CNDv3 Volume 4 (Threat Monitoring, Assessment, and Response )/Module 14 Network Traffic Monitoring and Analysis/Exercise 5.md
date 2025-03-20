# Detecting Clear-Text Traffic using Wireshark

### Lab Scenario
Some applications allow their users to communicate through protocols such as HTTP, FTP, and Telnet. These protocols transfer data over TCP in clear-text format, which can be easily understood by someone eavesdropping on the network. As a network defender, you need to know how to determine if there is any sensitive information (such as user credentials) flowing through the network.

### Lab Objectives
This lab will demonstrate how to detect sensitive data flowing through the network in clear-text format.

### Overview of Lab
Packet capture means intercepting data packets traversing over a network using packet capture tools such as Wireshark. These captured packets are analyzed in order to determine whether correct network security policies are being followed.

### Lab Tasks

1. **Launch Smoothwall Firewall VM**
   - Click on **Smoothwall Firewall**.
   - Type `toor` as password, and press **Enter**.
   - Press the **Tab** button twice to navigate to the **Done** button, and press **Enter**.
   - Wait for a few seconds to load the Smoothwall Firewall machine.

2. **Click PfSense Firewall link**
   - If the machine is inactive, press **Enter** to activate the machine.

3. **Launch AdminMachine-1 VM**
   - Click **AdminMachine-1**.
   - Click **Ctrl+Alt+Delete**.
   - By default, the username `Admin` is selected. Type password as `admin@123` and press **Enter**.

4. **Ensure Cain & Abel application is running**
   - If not, install and set up Cain & Abel by following the instructions in **Exercise 2**.

5. **Launch Wireshark**
   - Click **Windows Search** and search for **Wireshark**.
   - Select and open the Wireshark App.
   - Select **Ethernet 2** as the interface and click the **Start capturing packets** icon (blue fin icon).

6. **Launch Attacker Machine VM**
   - Click **Attacker Machine**.
   - Login with username as `Bob` and password as `user@123`.

7. **Access the Luxury Treats Website**
   - Open **Web browser**.
   - Type the URL `http://www.luxurytreats.com` and press **Enter**.
   - Log in with username as `Bob` and password as `Passw0rd`.

8. **Analyze Captured Packets in Wireshark**
   - Switch back to **AdminMachine-1 VM**.
   - In Wireshark, click the **Stop capturing packets** icon.
   - Filter packets using the filter: `http contains luxurytreats`.
   - Choose the **HTTP POST** packet from the filtered list, right-click on its HTML form encoded data, then click **Follow -> TCP Stream**.
   - The new **TCP Stream** window will display the clear-text password `Passw0rd`.

9. **Detect FTP Clear-Text Traffic**
   - On the **Attacker Machine VM**, open **Terminal**.
   - Type the command: `ftp 10.10.10.16` (where `10.10.10.16` is the IP address of the Web Server).
   - When prompted, enter `Administrator` as the **Username** and `admin@123` as the **Password**.

10. **Analyze FTP Packets in Wireshark**
    - Switch back to **AdminMachine-1 VM**.
    - Click the **Stop capturing packets** icon.
    - Filter packets using the filter: `ftp`.
    - The captured traffic will display the **Username** as `Administrator` and **Password** as `admin@123` in clear text under the **Info** field.

### Conclusion
By following the above steps, you can successfully detect clear-text credentials in network traffic using Wireshark. This emphasizes the importance of securing sensitive data using encryption protocols such as HTTPS, SFTP, and SSH.

