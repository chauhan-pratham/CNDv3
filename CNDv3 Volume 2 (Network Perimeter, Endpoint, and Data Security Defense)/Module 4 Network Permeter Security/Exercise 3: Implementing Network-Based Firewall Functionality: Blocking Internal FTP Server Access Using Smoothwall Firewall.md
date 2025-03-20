### Lab Exercise: Blocking Internal FTP Server Access Using Smoothwall Firewall

**Objective:** Configure Smoothwall to block access to an internal FTP server, enhancing network security by controlling access based on organizational policies.

#### Overview of Smoothwall
Smoothwall is a firewall that protects networks from unauthorized access. It uses rules to control traffic flow, allowing network defenders to block specific IPs or services.

#### Steps to Block FTP Access

1. **Launch Required VMs:**
   - If not already running, launch the **Smoothwall Firewall**, **AD Domain Controller**, and **Admin Machine-1** VMs.
   - Log in to each VM as specified in the original instructions.

2. **Access Smoothwall Web Interface:**
   - In the **Admin Machine-1 VM**, open Google Chrome and navigate to `http://20.20.10.53:81`.
   - Log in with Username `admin` and Password `toor`.

3. **Configure Firewall Rules:**
   - Navigate to the **Networking** menu and click on the **Incoming** tab.
   - Click on the **Outgoing** tab to review the current configuration.
   - Remove any unnecessary Purple interface rules by checking the boxes and clicking **Remove**.

4. **Allow Access to the Orange Interface:**
   - Ensure that the Orange interface is explicitly declared to allow connections between the DMZ server and the internal client machine.

5. **Test FTP Access:**
   - Launch the **Finance-Dept VM** and log in as `Finance-Dept\Alice` with the password `user@123`.
   - Open **File Explorer** and enter `ftp://10.10.10.16` in the address bar. Confirm that the FTP site is accessible without credentials.

6. **Create a Rule to Block FTP Access:**
   - Switch back to the **Admin Machine-1 VM** and navigate to **Networking > IP Block**.
   - Add a new rule with the following details:
     - **Source IP (or network):** `10.10.10.16`
     - **Action:** Select **Drop packet**
     - **Comment:** Block FTP site
     - **Enabled:** Check the box
   - Click **Add** to set the rule.

7. **Verify Rule Creation:**
   - After adding the rule, confirm that the message "Block rules set" appears, indicating the rule has been successfully added.

8. **Test FTP Access Again:**
   - Switch back to the **Finance-Dept VM** and log in as `Finance-Dept\Alice` if not already logged in.
   - Open **File Explorer** and enter `ftp://10.10.10.16` again. This time, you should see a message indicating that the FTP site cannot be reached.

By following these steps, you have successfully configured the Smoothwall firewall to block access to the internal FTP server, thereby enhancing the security of the network against unauthorized access.