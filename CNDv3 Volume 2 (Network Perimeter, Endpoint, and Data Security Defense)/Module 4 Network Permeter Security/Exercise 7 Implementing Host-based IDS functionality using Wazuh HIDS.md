### Summary of Steps for Implementing Wazuh HIDS

1. **Launch Security Onion:**
   - Open Admin Machine-2 VM and log in with username `sam` and password `admin123`.

2. **Access Wazuh Agent:**
   - Switch to Admin Machine-1 VM, log in with `admin@123`, and open Firefox.
   - Navigate to `https://10.10.10.79/`, accept risks, and log in with `cnd.labs.demos@gmail.com` and `Test@8899`.

3. **Download Wazuh Agent:**
   - Go to **Downloads** > **Wazuh Agents (3.13.1-1)** and download the MSI file.
   - Copy the `Wazuh-agent-3.13.1-1` file to `E:/CND-Tools`.

4. **Install Wazuh Agent on Web Server:**
   - Launch Web Server VM, log in with `admin@123`, and close the Server Manager if it appears.
   - Copy the Wazuh Agent from `Z:\CND-Tools` to the Desktop and run the installer.
   - Accept the license, install, and check **Run Agent configuration interface**.

5. **Configure Wazuh Agent:**
   - Set the Manager IP to `10.10.10.79`.
   - Open Command Prompt and connect to the Wazuh Manager using `ssh sam@10.10.10.79`.
   - Run `sudo so-wazuh-agent-manage`, choose action `A`, and name the agent `WebServer`.
   - Enter the agent's IP address `10.10.10.16`, confirm, and copy the generated Agent key.

6. **Complete Agent Setup:**
   - Paste the Agent key into the Wazuh Agent Manager and click **Save**.
   - Start the agent from the Manage tab and refresh to check its status.

7. **Perform FTP Attack:**
   - Launch Attacker Machine VM, log in as `Bob` with password `user@123`.
   - Copy `wrd.txt` and `pwd.txt` to the Desktop.
   - Execute the command: `hydra -L 'wrd.txt' -P 'pwd.txt' ftp://10.10.10.16` to perform the attack.

8. **Monitor Alerts in Security Onion:**
   - Switch back to Admin Machine-1, access Security Onion, and select **Alerts**.
   - Review alerts for logon failures and drill down for detailed information on the alerts, including parameters like Dst IP, severity, and failure reason.

9. **Analyze Alert Details:**
   - Observe the details of the alerts to understand the malicious activity detected by Wazuh.

---

This summary captures the essential steps while maintaining clarity and brevity. Let me know if you need any further modifications!