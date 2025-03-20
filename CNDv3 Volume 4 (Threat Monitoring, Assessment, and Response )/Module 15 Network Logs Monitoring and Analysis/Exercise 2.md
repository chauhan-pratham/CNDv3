# IIS Logs Monitoring and Analysis

## Lab Objectives
Learn to configure, view, and analyze IIS logs for monitoring web server activities and identifying suspicious behavior.

## Lab Steps
1. **Login to Web Server VM:**  
   - Click `Ctrl+Alt+Delete` ➔ Select `admin@123` ➔ Press `Enter`.

2. **Open IIS Manager:**  
   - Go to `Windows Administrative Tools` ➔ Open `Internet Information Services (IIS) Manager`.

3. **Check IIS Logging Status:**  
   - Select `Server Name` in the left pane ➔ Double-click `Logging` in the IIS section.  
   - If `Disable` appears in the Actions pane, logging is enabled.

4. **Configure IIS Logging:**  
   - Expand `Server Name` ➔ Expand `Sites` ➔ Select `LuxuryTreats`.  
   - Double-click `Logging` in the IIS section.  
   - Click `Select Fields...` ➔ Ensure the following fields are selected:
     - `Client IP Address (c-ip)`
     - `User Name (cs-username)`
     - `Protocol Status (sc-status)`
     - `Protocol Substatus (sc-substatus)`
     - `Bytes Sent (sc-bytes)`
     - `Bytes Received (cs-bytes)`
     - `Host (cs-host)`
     - `User Agent (cs(User-Agent))`
     - `Cookie (cs(Cookie))`
     - `Referer (cs(Referer))`
   - Click `OK` ➔ Click `Apply`.

5. **Generate IIS Logs:**  
   - Open `Google Chrome` ➔ Go to `www.luxurytreats.com`.  
   - Ensure the SQL Server service is running (may take 1-2 minutes).

6. **View IIS Logs:**  
   - Navigate to `C:\inetpub\logs\logFiles` ➔ Open `W3SVC2` folder.  
   - Locate log files in `u_exYYMMDD` format ➔ Open the latest file with `Notepad++`.

## End of Exercise

