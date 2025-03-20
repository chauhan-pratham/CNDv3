# Network Traffic Monitoring and Analysis

## Exercise 6: Monitoring and Detecting Network Reconnaissance Attempts

### **Objective**
Identify and analyze network reconnaissance activities such as ping sweeps, ARP sweeps, aggressive scans, and TCP flag-based attacks using Wireshark.

---

## **Steps to Follow**

### **1. Setup**
- Launch **PfSense Firewall**, **AdminMachine-1**, and **Attacker Machine** VMs.
- Disable **Windows Defender** on AdminMachine-1.
- Ensure **Cain & Abel** is installed and ARP poisoning is set up.
- Open **Wireshark** and start packet capture on the **Ethernet** interface.

---

### **2. Ping Sweep Detection**
- On the **Attacker Machine**, run:
```bash
ping 10.10.10.16
```
- In **Wireshark**, apply filter:
```bash
icmp.type==8 || icmp.type==0
```
- Detect continuous ICMP requests and replies.

---

### **3. ARP Sweep Detection**
- On the **Attacker Machine**, run:
```bash
sudo nmap -sn 10.10.10.0/24
```
- In **Wireshark**, apply filter:
```bash
arp
```
- Observe numerous ARP requests targeting multiple IP addresses.

---

### **4. Aggressive Scan Detection (OS, Port, and Service Info)**
- On the **Attacker Machine**, run:
```bash
sudo nmap -A 10.10.10.16
```
- In **Wireshark**, apply these filters:

- **SYN Requests (from Attacker):**
```bash
ip.src==10.10.10.50 && (tcp.flags.syn==1 && tcp.flags.ack==0)
```
- **SYN-ACK Responses (from Target):**
```bash
ip.src==10.10.10.16 && (tcp.flags.syn==1 && tcp.flags.ack==1)
```

---

### **5. Detect Specific TCP Scans**
- **NULL Scan:**
```bash
tcp.flags==0x00
```
- **Xmas Scan:**
```bash
tcp.flags==0x029
```

---

### **6. Traceroute and OS Detection**
- Apply filter:
```bash
ip.ttl < 64
```

---

### **7. Version Detection Probes**
- Apply filter:
```bash
tcp.flags.push == 1 || tcp.payload
```

---

### **Key Indicators of Reconnaissance Attempts**
✅ Frequent SYN packets without ACK replies  
✅ Numerous ARP broadcasts within a short period  
✅ Low TTL values in packets  
✅ Clear-text data in certain payloads  

---

### **Final Tip**
Always cross-reference suspicious packets with known attack patterns for accurate detection.

