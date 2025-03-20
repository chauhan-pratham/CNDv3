### Lab Exercise: Blocking Insecure Ports Using pfSense Firewall

**Objective:** Configure pfSense to block insecure outbound traffic on HTTP (port 80) to enhance network security.

#### Overview of Firewall Rules
- **Inbound Rules:** Protect against incoming malicious traffic.
- **Outbound Rules:** Control outgoing traffic from the internal network, preventing vulnerabilities.

#### Steps to Block HTTP Traffic (Port 80)

1. **Launch Required VMs:**
   - If not already running, launch the **Smoothwall Firewall**, **AD Domain Controller**, and **Finance-Dept** VMs.
   - Log in to each VM as specified in the original instructions.

2. **Test Website Accessibility:**
   - In the **Finance-Dept VM**, open Google Chrome and navigate to `http://www.itsecgames.com/` to confirm access.

3. **Access pfSense Web Interface:**
   - In the **Admin Machine-1 VM**, open Chrome and go to `http://10.10.10.1`.
   - Bypass the privacy warning by clicking Advanced > Proceed.
   - Log in with Username `admin` and Password `pfsense`.

4. **Create a Firewall Rule to Block HTTP:**
   - Navigate to **Firewall > Rules** and select the **LAN** tab.
   - Click the **Add** button to create a new rule.
   - Set the following parameters:
     - **Action:** Reject
     - **Interface:** LAN
     - **Address Family:** IPv4
     - **Protocol:** TCP/UDP
     - **Source:** Any
     - **Destination:** Any
     - **Destination Port Range:** HTTP (80)
     - **Description:** Rule for Rejecting any website using HTTP (80) port
   - Click **Save** and then **Apply Changes**.

5. **Verify Website Blocking:**
   - Switch back to the **Finance-Dept VM** and try accessing `http://www.itsecgames.com/`. You should see a message indicating that the site can’t be reached, confirming that the firewall rule is effective.

6. **Cleanup:**
   - Close the browser window.
   - In the **Admin Machine-1 VM**, navigate back to **Firewall > Rules**.
   - Select the created rule(s) by checking the corresponding checkboxes and click **Delete**.
   - Confirm the deletion and click **Apply Changes**.

7. **Reboot pfSense:**
   - Navigate to **Diagnostics > Reboot**.
   - Select **Normal Reboot** and click **Submit**.
   - Confirm the reboot in the pop-up.

8. **Final Steps:**
   - Once pfSense reboots, the sign-in page will appear. Close the browser.

By following these steps, you successfully configure pfSense to block insecure outbound traffic on HTTP, enhancing the security of the organization's network.