### Network Scanning Attacks Lab Summary

**Objective:** Understand various network scanning techniques used by attackers to gather information about hosts, ports, and services on a target network.

**Overview:** Network scanning is a reconnaissance technique that helps attackers identify open ports and services, allowing them to plan subsequent attacks. Network defenders should be aware of these scanning attempts to prevent potential breaches.

**Lab Steps:**

1. **Setup:**
   - Start the PfSense Firewall VM.
   - Launch the Web Server VM and log in with `admin@123`.
   - Launch the Attacker VM and log in as user Bob with password `user@123`.

2. **Target Identification:**
   - Assume the target machine has the IP address `10.10.10.16` (Web Server).

3. **Perform Network Scans:**
   - **SYN Scan:** 
     - Command: `nmap -sS 10.10.10.16`
     - This scan identifies open ports by sending SYN packets.
   
   - **TCP Full Connect Scan:**
     - Command: `nmap -sT -T4 10.10.10.16`
     - This scan establishes a full TCP connection to identify open ports.

   - **TCP Null Scan:**
     - Command: `nmap -sN -T4 -A -v 10.10.10.16`
     - This scan sends packets with no flags set to identify open ports.

   - **TCP Xmas Scan:**
     - Command: `nmap -sX -T4 10.10.10.16`
     - This scan sends packets with the FIN, URG, and PSH flags set to identify open ports.

   - **FIN Scan:**
     - Command: `nmap -sF -T4 10.10.10.16`
     - This scan sends FIN packets to differentiate between open and closed ports.

   - **UDP Scan:**
     - Command: `nmap -sU -T5 10.10.10.16`
     - This scan identifies open UDP ports, which may take longer to complete.

4. **Review Results:**
   - Each scan provides valuable information about the state of ports and the services running on the target system, which can be exploited by attackers.

**Conclusion:** This lab illustrates how attackers utilize various network scanning techniques to gather information about a target network. Understanding these methods is crucial for network defenders to detect and mitigate potential threats effectively.