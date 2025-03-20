### Summary of Steps for Implementing ModSecurity

1. **Launch Smoothwall Firewall:**
   - Open the Smoothwall Firewall VM and log in with the password `toor`.

2. **Access Operation Dept VM:**
   - Launch the Operation Dept VM and log in as `Alice` with password `user@123`.
   - Open the terminal and switch to the root directory using `sudo su`.

3. **Update and Install Apache:**
   - Run `apt update` and `apt upgrade`, then install Apache with:
     ```bash
     apt install apache2 -y
     ```

4. **Install and Enable ModSecurity:**
   - Install ModSecurity using:
     ```bash
     apt install libapache2-mod-security2 -y
     ```
   - Enable the module with:
     ```bash
     a2enmod security2
     ```
   - Restart Apache to apply changes:
     ```bash
     systemctl restart apache2
     ```

5. **Configure ModSecurity:**
   - Rename the recommended configuration file:
     ```bash
     mv /etc/modsecurity/modsecurity.conf-recommended /etc/modsecurity/modsecurity.conf
     ```
   - Edit the configuration file with:
     ```bash
     nano /etc/modsecurity/modsecurity.conf
     ```
   - Change `SecRuleEngine DetectionOnly` to `SecRuleEngine On` to enable blocking.
   - Update `SecAuditLogParts` to `ABCEFHJKZ` for better logging.
   - Save and exit the file.

6. **Set Up OWASP ModSecurity Core Rule Set:**
   - Clone the OWASP CRS repository:
     ```bash
     git clone https://github.com/coreruleset/coreruleset /etc/apache2/modsecurity-crs
     ```
   - Change to the CRS directory:
     ```bash
     cd /etc/apache2/modsecurity-crs/
     ```
   - Rename the setup file:
     ```bash
     mv crs-setup.conf.example crs-setup.conf
     ```
   - Edit the security configuration:
     ```bash
     nano /etc/apache2/mods-enabled/security2.conf
     ```
   - Update the include lines to point to the new CRS:
     ```plaintext
     IncludeOptional /etc/apache2/modsecurity-crs/crs-setup.conf
     IncludeOptional /etc/apache2/modsecurity-crs/rules/*.conf
     ```
   - Rename the multipart attack rule file:
     ```bash
     mv ./rules/REQUEST-922-MULTIPART-ATTACK.conf ./rules/REQUEST-922-MULTIPART-ATTACK.conf.example
     ```

7. **Test and Restart Apache:**
   - Test the Apache configuration:
     ```bash
     apache2ctl -t
     ```
   - If the syntax is OK, restart Apache:
     ```bash
     systemctl restart apache2
     ```

8. **Verify ModSecurity Functionality:**
   - Access the URL `http://localhost/index.html?exec=bin/bash` in Firefox.
   - After configuration, this should return a **403 Forbidden** error, indicating the request was blocked.

9. **Check Apache Error Logs:**
   - Confirm ModSecurity is working by checking the error logs:
     ```bash
     cat /var/log/apache2/error.log | grep "Access denied with code 403"
     ```

---

This summary captures the essential steps while maintaining clarity and brevity. Let me know if you need any further modifications!