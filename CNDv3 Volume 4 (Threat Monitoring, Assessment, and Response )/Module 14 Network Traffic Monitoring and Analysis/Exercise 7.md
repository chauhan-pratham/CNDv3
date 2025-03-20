# Detecting Brute-Force Attack Using Wireshark

## Lab Scenario
Attackers use brute-force attacks to gain unauthorized access to FTP servers and other services like SSH and Telnet. Identifying such attempts through network traffic analysis is crucial to securing the network. This lab demonstrates how to detect brute-force attacks using Wireshark.

---

## Lab Objectives
- Perform a brute-force attack on an FTP server using Hydra.  
- Detect the brute-force attack attempts using Wireshark.

---

## Lab Steps

### Step 1: Setup Environment
1. Launch **Smoothwall Firewall VM** and log in using:
   - **Username:** `toor`
   - **Password:** `toor`

2. Launch **PfSense Firewall VM** and press `Enter` to activate the machine.

3. Launch **AdminMachine-1 VM** and log in using:
   - **Username:** `Admin`
   - **Password:** `admin@123`

4. Ensure **Cain & Abel** is running and ARP poisoning route is set up.
5. Open **Wireshark** and start capturing packets on the `Ethernet 2` interface.

### Step 2: Perform Brute-Force Attack with Hydra
1. On the **Attacker Machine VM**, log in using:
   - **Username:** `Bob`
   - **Password:** `user@123`
2. Open Terminal and run the following command:
   ```bash
   hydra -L /home/bob/wrd.txt -P /home/bob/pwd.txt ftp://10.10.10.16
   ```
3. The Hydra tool will attempt multiple logins and eventually find the correct credentials.

### Step 3: Detect Brute-Force Attack Using Wireshark
1. On the **AdminMachine-1 VM**, stop the Wireshark packet capture.
2. Apply the following filter to detect failed FTP logins:
   ```
   ftp.response.code == 220
   ```
3. A large number of failed login attempts confirm the presence of a brute-force attack.

---

## Key Takeaways
- **Hydra** effectively demonstrates how attackers exploit weak credentials.
- Using Wireshark's `ftp.response.code == 220` filter highlights excessive failed login attempts, indicating brute-force activity.

---

## Recommendations
- Implement strong password policies to reduce brute-force vulnerabilities.
- Enable account lockout mechanisms after repeated failed attempts.
- Regularly monitor network traffic for unusual activity patterns.

---

