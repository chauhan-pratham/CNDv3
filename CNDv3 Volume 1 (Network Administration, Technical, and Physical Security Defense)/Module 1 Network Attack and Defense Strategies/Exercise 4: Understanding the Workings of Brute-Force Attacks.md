### Brute-Force Attack Lab Summary

**Objective:** Understand how brute-force attacks work and how attackers can gain unauthorized access to systems using automated tools.

**Overview:** A brute-force attack involves systematically trying numerous passwords or passphrases until the correct one is found. This lab demonstrates the use of the Hydra tool to perform a brute-force attack on an FTP server.

**Lab Steps:**

1. **Setup:**
   - Start the PfSense Firewall VM.
   - Launch the Web Server VM and log in with `admin@123`.
   - Launch the Attacker VM and log in as user Bob with password `user@123`.

2. **Target Identification:**
   - The target machine’s IP address is `10.10.10.16`.
   - Perform an Nmap scan to check if the FTP port (21) is open:
     - Command: `nmap -p 21 10.10.10.16`
   - Confirm that port 21 is open, indicating an FTP server is hosted.

3. **Initial FTP Access Attempt:**
   - Open the FTP client: `ftp 10.10.10.16`
   - Attempt to log in using random usernames and passwords to confirm access is restricted.

4. **Brute-Force Attack Using Hydra:**
   - Prepare the attack by ensuring you have two files: `wrd.txt` (usernames) and `pwd.txt` (passwords).
   - Copy `wrd.txt` and `pwd.txt` to the Desktop.
   - In the terminal, navigate to the Desktop:
     - Command: `cd Desktop`
   - Execute the Hydra brute-force command:
     - Command: `hydra -L wrd.txt -P pwd.txt ftp://10.10.10.16`
   - Hydra will attempt various combinations of usernames and passwords from the provided files.

5. **Successful Login:**
   - If Hydra successfully cracks the credentials, note the username and password.
   - Attempt to log in to the FTP server again using the cracked credentials:
     - Command: `ftp 10.10.10.16`
   - Enter the cracked credentials (e.g., `administrator/admin@123`).
   - If successful, you will gain access to the FTP terminal.

6. **Exit the FTP Client:**
   - Type `quit` to exit the FTP terminal.

**Conclusion:** This lab demonstrates how attackers can use brute-force techniques, specifically with tools like Hydra, to gain unauthorized access to systems by exploiting weak passwords. Understanding these methods is essential for network defenders to implement stronger security measures and monitor for signs of brute-force attacks.