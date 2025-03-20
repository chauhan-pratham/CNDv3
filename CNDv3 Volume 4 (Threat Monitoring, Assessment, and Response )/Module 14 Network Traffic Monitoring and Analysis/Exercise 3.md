# Analyzing and Examining Various Network Packet Headers in Linux using tcpdump

### Lab Scenario
Each packet in a network contains control information and user data, known as the payload. The control information contains data for delivering the payload, which includes source and destination IP and MAC addresses, and sequencing information. The header part of the packet stores this control information. Hence, the network administrator needs to know how to examine the packet headers while examining the data packets.

### Lab Objectives
The objective of this lab is to help students learn how to inspect TCP/IP and other packet header fields of different network packets.

### Overview of tcpdump Packet Analyzer
In packet capture, data packets traversing over a network are intercepted using packet capture tools such as tcpdump. These captured packets are analyzed to determine whether proper network security policies are being followed.

---

### Lab Tasks

1. **Launch Required Machines**
   - Click **PfSense Firewall** link to launch PfSense Firewall. If the machine is inactive, press **Enter** to activate the machine.
   - Launch **Smoothwall Firewall VM** by clicking on **Smoothwall Firewall**.
   - Type **toor** as password and press **Enter**.
   - Press the **Tab** key twice to navigate to the **Done** button and press **Enter**. Wait for a few seconds to load the Smoothwall Firewall machine.

2. **Login to the Operation Dept VM**
   - Click **Operation Dept** to launch Operation Dept VM.
   - Press **Ctrl+Alt+Delete** to log in.
   - Choose **User** as **alice** and enter password as **user@123** and click **Log In**.

3. **Open a Terminal**
   - Right-click on Desktop and select **Open in Terminal** from the pop-up menu.

4. **Capture Network Packets**
   - In the terminal, type:
     ```bash
     sudo tcpdump
     ```
   - If prompted for a password, type **user@123**.
   - The tcpdump command will capture and display the packets.
   - Press **Ctrl + C** to stop capturing packets.

5. **Capture Packets from a Specific Interface**
   - In the terminal, type:
     ```bash
     sudo tcpdump -i eth0
     ```
   - Press **Ctrl + C** to end capturing packets.

6. **Capture Only TCP Packets**
   - In the terminal, type:
     ```bash
     sudo tcpdump -i eth0 tcp
     ```
   - Open another terminal and type:
     ```bash
     dd if=/dev/urandom bs=1M count=1 | nc 10.10.10.50 9000
     ```
   - Switch back to the first terminal to observe the captured TCP packets.
   - Press **Ctrl + C** to stop capturing packets.

7. **Capture Packets from Specific Port**
   - In the terminal, type:
     ```bash
     sudo tcpdump -i eth0 port 80
     ```
   - In the **Applications** menu, select **Firefox Web Browser**.
   - In Firefox, type `http://www.certifiedhacker.com` in the URL bar and press **Enter**.
   - Switch back to the terminal to observe the captured HTTP packets.
   - Press **Ctrl + C** to stop capturing packets.

8. **Capture Packets from Specific Source IP**
   - In the terminal, type:
     ```bash
     sudo tcpdump -i eth0 src 10.10.10.16
     ```
   - Open another terminal and type:
     ```bash
     ping 10.10.10.16
     ```
   - Leave the terminal open and observe the captured ICMP packets in the first terminal.
   - Close the second terminal and press **Ctrl + C** in the first terminal to stop capturing.

9. **Close All Windows**
   - Close all opened windows to complete the exercise.

---

### Conclusion
By following these steps, a network defender can effectively capture and analyze network traffic using tcpdump.

