# Forensic Analysis using Live-Forensicator

## Overview
Live-Forensicator is an open-source tool used for investigating and analyzing digital data on live Windows systems. This tool helps gather system information, registry data, network connections, and running processes to uncover suspicious activities.

## Lab Objectives
- Collect digital evidence such as logs, files, and registry entries.
- Analyze the data to identify potential security vulnerabilities.

## Lab Steps
1. **Launch Admin Machine-1 VM**  
   - Press `Ctrl+Alt+Delete` and login using credentials: `admin@123`.

2. **Disable Windows Defender**  
   - Go to **Search** → Type **Windows Security**.  
   - Click **Virus & Threat Protection** → **Manage settings**.  
   - Turn off **Real-time Protection** → Click **Yes** if prompted.

3. **Extract Live-Forensicator Tool**  
   - Open **File Explorer** → Navigate to `E:\CND-Tools\CNDv3 Module 16 Incident Response and Forensic Investigation\Live-Forensicator`.  
   - Open `Live-Forensicator-main.rar`.  
   - Extract the `.rar` file to the **Desktop**.

4. **Run Live-Forensicator**  
   - Go to the extracted **Live-Forensicator-main** folder.  
   - Right-click `Forensicator Powershell` → Select **Run with PowerShell**.  
   - Click **Open** if prompted.

5. **Enter Investigation Details**  
   - Type **Y** and press `Enter`.  
   - Enter the following when prompted:
   - **Investigator Name:** `Alice`  
   - **Case Reference:** `001`  
   - **Investigation Title:** `Forensic analysis`  
   - **Examination Location:** `US`  
   - **Device Description:** `Laptop`  
   - Wait for the scan to complete (it will auto-close).

6. **Analyze Results**  
   - Open the `Live-Forensicator-main` folder.  
   - Open the `ADMIN MACHINE-1` folder.  
   - Double-click the **index file** to open the report.  
   - If prompted, select **Microsoft Edge** and click **OK**.

7. **View Analysis Details**  
   - Click **View Browsing History** → Open `Chrome_History_of_Admin.txt`.  
   - Click **Users & Accounts** to inspect user details.  
   - Click **System Information** for system details.  
   - Click **Suspicious Activities** to examine possible threats.

## Conclusion
This procedure helps conduct forensic analysis on a live Windows system using Live-Forensicator to gather and analyze critical evidence.

