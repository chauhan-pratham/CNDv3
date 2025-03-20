## Exercise 1: System Attack Surface Analysis using Windows Attack Surface Analyzer

### Lab Objectives
- Install and configure Attack Surface Analyzer (ASA)
- Perform a baseline scan
- Conduct a product scan to detect system changes

---

## Steps to Perform Attack Surface Analysis

### Step 1: Setup and Baseline Scan
1. **Launch Finance-Dept Machine**
   - Login as `Alice` with password `user@123`
2. **Install Attack Surface Analyzer**
   - Copy `ASA_win_2.3.308` from `Z:\...\Attack Surface Analyzer` to Desktop
   - Extract the file and open the extracted folder
3. **Run ASA**
   - Open `cmd` in the ASA folder
   - Run `asa.exe gui`
   - Open the GUI at `http://localhost:5000`
4. **Create Baseline Scan**
   - Select `Scan` in the ASA interface
   - Enter `BaseScan1` as the `Run Id`
   - Enable **NetworkPort Collector** only
   - Click **Start Scan**

### Step 2: Open Port 21 (FTP Service)
1. **Enable FTP Service**
   - Go to `Control Panel > Programs > Turn Windows Features on or off`
   - Enable **Internet Information Services > FTP Server** and **IIS Management Console**
2. **Restart the Machine**
3. **Create an FTP Site**
   - Create folder `C:\DemoFtp`
   - Open `IIS Manager`, right-click `Sites` and select `Add FTP Site`
   - Set the site name to `DemoFtpSite`
   - Select Port `21`, enable `No SSL`
   - Enable **Anonymous Authentication** with **Read/Write** permissions

### Step 3: Perform Port Scan
1. **Reopen ASA**
   - Run `asa.exe gui` from the ASA folder
2. **Create Port Scan**
   - Select `Scan`
   - Enter `PortScan1` as the `Run Id`
   - Enable **NetworkPort Collector** only
   - Click **Start Scan**

### Step 4: Analyze Results
1. **Analyze Scans**
   - Select `Analyze` from the menu
   - Compare `BaseScan1` with `PortScan1`
2. **Check Results**
   - Select **Result Type: Port**
   - Expand `CompareResult` to review changes on Port 21

### Step 5: Export Results
1. Click `Export` to save results in `.txt` format
2. Locate the file path in the command prompt and review changes

---

## Key Outcome
- Identified Port 21 as an insecure entry point
- Demonstrated effective system change detection using Attack Surface Analyzer

