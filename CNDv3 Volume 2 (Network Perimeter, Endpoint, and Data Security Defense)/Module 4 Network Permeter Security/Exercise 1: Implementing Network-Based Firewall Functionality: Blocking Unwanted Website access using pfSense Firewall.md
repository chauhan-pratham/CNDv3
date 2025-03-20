### Lab Exercise: Blocking Unwanted Website Access Using pfSense Firewall

**Objective:** Use pfSense to block access to unwanted websites, specifically to prevent users from visiting malicious sites and protect against phishing attacks.

#### Overview of pfSense
pfSense is an open-source firewall/router software that integrates firewall features, allowing for easy management of network security. Aliases in pfSense simplify rule management by allowing multiple hosts to be grouped under a single rule.

#### Steps to Block a Website (e.g., www.rediff.com)

1. **Launch Smoothwall Firewall VM:**
   - Log in with password `toor`.
   - Navigate to the Done button and press Enter.

2. **Launch AD Domain Controller VM:**
   - Log in using `CND\Administrator` and password `Pa$$w0rd`.

3. **Launch Admin Machine-1 VM:**
   - Log in with `admin@123`.

4. **Test Website Accessibility:**
   - Open Google Chrome and access `www.rediff.com` to confirm it is reachable.

5. **Access pfSense Web Interface:**
   - Open Chrome and go to `https://10.10.10.1`.
   - Bypass the privacy error by clicking Advanced > Proceed.
   - Log in with Username `admin` and Password `pfsense`.

6. **Create an Alias for Blocked Websites:**
   - Navigate to **Firewall > Aliases**.
   - Click **Add** to create a new alias.
   - Use the command prompt to ping `rediff.com` and note the IP address (e.g., `184.28.93.83`).
   - Fill in the alias details:
     - **Name:** BlockedWebsites
     - **Description:** Restrict access to unwanted websites
     - **Type:** Host(s)
     - **Host(s):** Add `www.rediff.com` and its IP address.
   - Click **Save** and then **Apply Changes**.

7. **Add Firewall Rule to Block Websites:**
   - Go to **Firewall > Rules** and select the **LAN** tab.
   - Click **Add** to create a new rule.
   - Set the following:
     - **Action:** Block
     - **Interface:** LAN
     - **Address Family:** IPv4
     - **Protocol:** TCP/UDP
     - **Source:** Any
     - **Destination:** Single host or alias (enter `BlockedWebsites`)
     - **Description:** Restrict access to unwanted Websites
   - Click **Save** and then **Apply Changes**.

8. **Verify Website Blocking:**
   - Launch Finance-Dept VM and log in as `Finance-Dept\Alice` with password `user@123`.
   - Open the browser and try to access `www.rediff.com`. The site should be blocked, displaying a message indicating it can't be reached.

By following these steps, you successfully configure pfSense to block access to unwanted websites, enhancing network security.  