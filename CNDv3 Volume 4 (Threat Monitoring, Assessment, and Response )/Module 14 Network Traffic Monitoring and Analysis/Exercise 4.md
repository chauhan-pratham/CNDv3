# Applying Various Filters in Wireshark

### Lab Scenario
Wireshark filters traffic flowing through the entire network. This traffic contains various kinds of data packets associated with multiple protocols between source and destination. Searching for specific packets, ports, or IP addresses manually is challenging. Applying Wireshark filters helps track down a huge amount of traffic and discover the intended packets. As a network defender, understanding various Wireshark filters is crucial for narrowing traffic to obtain desired results.

### Lab Objectives
This lab will help you become familiar with various Wireshark filters.

### Overview of Wireshark Filters
Wireshark has various filters that help you filter packets containing the following:
- Source IP address
- Destination IP address
- Internet Control Message Protocol (ICMP) traffic, etc.

### Lab Tasks

1. Launch Smoothwall Firewall VM by clicking on `Smoothwall Firewall`.
2. Type `toor` as the password and press **Enter**.
3. Press the **Tab** button twice to navigate to the **Done** button, and press **Enter**.
4. Wait a few seconds to load the Smoothwall Firewall machine.
5. Click `PfSense Firewall` link. If inactive, press **Enter** to activate the machine.

#### Launch Wireshark on AdminMachine-1
6. Click `AdminMachine-1` to launch AdminMachine-1 VM.
7. Click `Ctrl+Alt+Delete`.
8. By default, the username `Admin` is selected. Type the password `admin@123` and press **Enter**.
9. Click **Windows Search** and search for **Wireshark**. Select and open the Wireshark app.

#### Capturing Network Traffic
10. In Wireshark's main window, select `Ethernet 2` as the interface.
11. Click the **Start Capturing Packets** (blue shark fin icon) to begin capturing network traffic.

#### Generating Network Traffic
12. Click `Attacker Machine` to launch AttackerMachine VM.
13. Login with the username `Bob` and password `user@123`.
14. Open the web browser and access `http://www.luxurytreats.com`.
15. In the terminal, type `ftp 10.10.10.16` and press **Enter**.

#### Filtering Traffic in Wireshark
16. Return to AdminMachine-1 and click the **Stop Capturing Packets** icon (red color icon) in the toolbar.

### Applying Filters in Wireshark

- **HTTP Filter:** Type `http` in the filter field and press **Enter** to view HTTP-specific traffic.
- **TCP Filter:** Type `tcp` in the filter field and press **Enter** to view TCP-specific traffic.
- **FTP Filter:** Type `ftp` in the filter field and press **Enter** to view FTP-specific traffic.

### Filtering Based on IP Address

- **All Traffic for a Specific IP:** Use `ip.addr==10.10.10.50`.
- **Traffic from a Specific Source IP:** Use `ip.src==10.10.10.50`.
- **Traffic Destined for a Specific IP:** Use `ip.dst==10.10.10.16`.
- **Traffic Greater Than a Specific IP Address:** Use `ip.dst > 10.10.10.16`.
- **Traffic Less Than a Specific IP Address:** Use `ip.dst < 10.10.10.16`.

### Filtering Based on Port Number

- **All Traffic for a Specific Port:** Use `tcp.port==80`.
- **Traffic from a Specific Port:** Use `tcp.srcport==443`.
- **Traffic to a Specific Port:** Use `tcp.dstport==80`.
- **Exclude Traffic on Specific Port:** Use `!(tcp.port==443)`.
- **Traffic on Port Greater Than or Equal to a Specific Port:** Use `tcp.port>=443`.
- **Traffic on Port Less Than or Equal to a Specific Port:** Use `tcp.port<=443`.

### Filtering Traffic Using Contains Keyword

- **Filter HTTP Traffic Containing Specific Text:** Use `http contains "www.luxurytreats.com"`.
- **Filter HTTP Traffic with Host Containing Specific Text:** Use `http.host contains "www.luxurytreats.com"`.

### Filtering TCP Traffic by Flags

- **Packets with SYN and ACK Bits Set:** Use `tcp.flags & 0x012`.
- **Packets with Only SYN Flag Set:** Use `tcp.flags & 0x002`.
- **Packets with Only ACK Flag Set:** Use `tcp.flags & 0x010`.

### Combining Filters with Logical Operators

- **Combine Conditions:** Use `tcp.seq==1 && tcp.len==0` to find packets matching both conditions.

### Conclusion
By mastering these Wireshark filters, network defenders can efficiently analyze network traffic, isolate malicious packets, and identify security threats. Mastering these filters is essential for network monitoring and forensic analysis.

