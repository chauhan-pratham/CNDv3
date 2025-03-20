# Network Logs Monitoring and Analysis Using Splunk

## Lab Overview
This guide covers the configuration, viewing, and analysis of logs in a centralized location using Splunk Enterprise and Universal Forwarder.

## Prerequisites
- Complete Exercise 2 before starting this lab.
- Admin Machine-1 and Web Server VMs are required.

## Step 1: Install Splunk Enterprise (Admin Machine-1)
1. Launch **Admin Machine-1** VM and log in.
2. Navigate to `E:\CND-Tools\CNDv3 Module 15 Network Logs Monitoring and Analysis\Splunk Enterprise`.
3. Run `splunk-9.1.2-b6b9c8185839-x64-release`.
4. Accept the license agreement, set username and password as `admin` / `admin@123`.
5. After installation, increase max searches per CPU:
   - Open `limits.conf` at `C:\Program Files\Splunk\etc\system\default`.
   - Set `max_searches_per_cpu=2`.
6. Restart Admin Machine-1.

## Step 2: Install Splunk Forwarder (Web Server)
1. Launch **Web Server** VM and log in.
2. Navigate to `Z:\CNDv3 Module 15 Network Logs Monitoring and Analysis\Splunk Forwarder`.
3. Run `splunkforwarder-9.1.2-b6b9c8185839-x64-release`.
4. Accept the license agreement, select **Local System** as installation type.
5. Enable **Windows Event Logs** and **Performance Monitor**.
6. Set username and password as `admin` / `admin@123`.
7. Enter IP address `10.10.10.2` and Port `9997`.
8. Finish installation and restart the Splunk Forwarder service.

## Step 3: Configure Splunk Forwarder for IIS Logs
1. Open `inputs.conf` in `C:\Program Files\SplunkUniversalForwarder\etc\system\local` and add:
   ```ini
   [monitor://C:\inetpub\logs\logfiles]
   sourcetype=iis
   ignoreOlderThan=14d
   host=WebServer
   ```
2. Open `outputs.conf` in the same location and add:
   ```ini
   [iis*]
   Pulldown_type=true
   MAXTIMESTAMPLOOKAHEAD=32
   SHOULD_LINEMERGE=False
   CHECK_FOR_HEADER
   REPORT-iis2=iis2
   ```
3. Create `props.conf` with:
   ```ini
   [iis*]
   Pulldown_type=true
   MAXTIMESTAMPLOOKAHEAD=32
   SHOULD_LINEMERGE=False
   CHECK_FOR_HEADER
   REPORT-iis2=iis2
   ```
4. Create `transforms.conf` with:
   ```ini
   [default]
   host=WebServer
   [ignore_comments]
   REGEX=^#.*
   DEST_KEY=queue
   FORMAT=nullQueue
   [iis2]
   DELIMS=" "
   FIELDS=date time s-ip cs-method cs-uri-stem cs-uri-query s-port cs-username c-ip cs(User-Agent) cs(Cookie) cs(Referer) cs-host sc-status sc-substatus sc-win32-status sc-bytes cs-bytes time-taken
   ```
5. Restart Splunk Forwarder Service.

## Step 4: Configure Splunk Enterprise for Receiving Logs
1. Log in to Splunk Enterprise on Admin Machine-1 (`http://localhost:8000`).
2. Navigate to **Settings** → **Forwarding and Receiving**.
3. Add a new receiving port (`9997`).
4. Enable the **SplunkForwarder** app under **Manage Apps**.
5. Restart Splunk Enterprise.

## Step 5: Viewing Logs in Splunk
1. Navigate to **Apps** → **SplunkForwarder**.
2. Click **Data Summary** and select the Web Server host.
3. To view failed login attempts, run the following search query:
   ```spl
   sourcetype="WinEventLog:Security" EventCode=4625
   ```
4. To view IIS logs:
   - Access `http://www.luxurytreats.com` from Attacker Machine.
   - Refresh Splunk Enterprise and locate IIS logs under **sourcetype → iis**.

## End of Exercise
This guide covered the installation, configuration, and analysis of Splunk logs for centralized monitoring.

