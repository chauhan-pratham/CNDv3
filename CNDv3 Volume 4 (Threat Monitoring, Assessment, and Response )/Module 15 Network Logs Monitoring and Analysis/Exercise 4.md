# Network Logs Monitoring and Analysis

## Exercise 4: Identifying Suspicious Activities Using Log Monitoring and Analysis

### Lab Scenario
In this lab, you'll use Splunk to monitor and analyze logs for detecting suspicious activities such as brute-force attempts and SQL injection attacks.

### Lab Objectives
- Monitor and analyze Windows event logs for brute-force attempts.
- Monitor and analyze IIS logs for SQL injection attempts.

---

### Lab Tasks
**Prerequisite:** Ensure the Splunk Forwarder service is running on the Web Server VM.

1. **Web Server VM:**
   - Log in and attempt **three failed logins**.
   - Perform a successful login with credentials:
     - **Username:** Administrator
     - **Password:** admin@123

2. **Attacker Machine VM:**
   - Log in with credentials:
     - **Username:** Bob
     - **Password:** user@123
   - Access `http://www.luxurytreats.com` in Firefox.
   - Log in with credentials:
     - **Username:** bob
     - **Password:** Passw0rd
   - Navigate to **My Orders** and select **Order ID ORD-001**.
   - Modify the URL as follows for SQL injection:
     ```
     http://www.luxurytreats.com/OrderDetail.aspx?Id=ORD-001 ' or 1=1;--
     ```
   - Verify that unauthorized order details are displayed.

3. **Admin Machine-1 VM:**
   - Log in with credentials:
     - **Username:** Admin
     - **Password:** admin@123
   - Open Chrome and navigate to `http://localhost:8000`.
   - Log in to Splunk Enterprise with admin credentials.

4. **Analyze Windows Logs:**
   - In Splunk, go to **Search & Reporting**.
   - Click on **Data Summary** and select the **WebServer** host.
   - Click **sourcetype** > **WinEventLog:Security**.
   - Search for brute-force attempts using the query:
     ```
     EventCode=4625
     ```

5. **Analyze IIS Logs:**
   - In Splunk, go to **sourcetype** and select **iis**.
   - Click on **All Fields**, select **cs_uri_query**, and close the window.
   - Search for SQL injection-related log entries by clicking on **cs_uri_query** values.

---

### Conclusion
This exercise demonstrates how to monitor and analyze logs in Splunk to detect brute-force and SQL injection attempts, enhancing network security through proactive threat detection.

