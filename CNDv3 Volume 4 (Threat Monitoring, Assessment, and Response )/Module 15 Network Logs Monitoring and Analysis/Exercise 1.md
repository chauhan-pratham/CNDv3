# Windows Event Logs Monitoring and Analysis

## Lab Objectives
Learn to configure, view, and analyze Windows security logs for auditing and threat detection.

## Lab Steps
1. **Login to Web Server VM:**  
   - Click `Ctrl+Alt+Delete` ➔ Select `admin@123` ➔ Press `Enter`.

2. **Configure Audit Policy:**  
   - Click `Start` ➔ Search "Local Security Policy" ➔ Open it.  
   - Expand `Local Policies` ➔ Click `Audit Policy`.  
   - Double-click `Audit logon events` ➔ Check `Success` and `Failure` ➔ Click `Apply` and `OK`.

3. **View Security Logs:**  
   - Right-click `Start` ➔ Open `Event Viewer`.  
   - Expand `Windows Logs` ➔ Select `Security`.

4. **Generate Failed Login Logs:**  
   - Sign out ➔ Attempt 2-3 invalid logins ➔ Sign in with `admin@123`.

5. **Analyze Failed Logins:**  
   - Open `Event Viewer` ➔ Select `Security` ➔ Click `Filter Current Log...`.  
   - Search for **Event ID 4625** ➔ Click `OK`.  
   - Double-click entries for detailed information.

6. **Log Storage Path:**  
   Logs are stored at: `C:\Windows\System32\winevt\Logs`

## End of Exercise

