# Nessus Vulnerability Analysis Guide

## Overview
This guide outlines the steps to perform a vulnerability scan using Nessus to identify potential risks in a network.

## Lab Setup
1. **Launch Systems:**
   - Launch **Smoothwall Firewall**, **AD Domain Controller**, **Web Server**, and **Admin Machine-1**.
2. **Login Credentials:**
   - Smoothwall Firewall: `Username: root | Password: toor`
   - AD Domain Controller: `Username: CND\Administrator | Password: Pa$$w0rd`
   - Web Server: `Username: Administrator | Password: admin@123`
   - Admin Machine-1: `Username: Admin | Password: admin@123`
3. **Enable Network Discovery:** Click **Yes** if prompted to allow PC discovery.

## Nessus Setup
1. **Open Google Chrome:** Navigate to `https://localhost:8834`.
2. **Bypass Security Warning:** Click **Advanced** → **Proceed to localhost (unsafe)**.
3. **Login to Nessus:**
   - Username: `admin`
   - Password: `admin@123`

## Creating a Scan Policy
1. Navigate to **Policies** → **New Policy** → **Advanced Scan**.
2. Fill in details:
   - **Name:** `NetworkScan_Policy`
   - **Description:** `Network scanning policy`
3. **Discovery Settings:**
   - Turn **Ping the remote host** `OFF`.
   - Enable:
     - **Scan Network Printers**
     - **Scan Novell Netware hosts**
4. **Port Scanning:**
   - Enable **Verify open TCP ports found by local port enumerators**.
5. **Service Discovery:**
   - Enable **CRL checking**.
6. **Assessment Settings:**
   - Enable **Scan web applications**.
7. **Advanced Settings:**
   - Set **Max TCP sessions per host** and **per scan** to `10000`.
8. **Credentials:**
   - **Windows:**
     - **Username:** `Alice`
     - **NTLM Hash:** `user@123`
     - **Domain:** `cnd.com`
   - **Database:**
     - **Username:** `admin`
     - **Password:** `admin@123`
     - **Port:** `124`
     - **Service:** `4587`
     - **Auth Type:** `SYSDBA`
9. Click **Save**.

## Running a Scan
1. Navigate to **My Scans** → **+ New Scan**.
2. Go to **User Defined** tab and select **NetworkScan_Policy**.
3. Set the following:
   - **Name:** `Local Network Scan`
   - **Description:** `Scan for network vulnerabilities`
   - **Scan Targets:** `20.20.10.10` (Finance Dept VM) or `10.10.10.16` (Web Server VM)
4. Click **Save**.
5. Click the **Launch** button to start the scan.
6. Monitor the scan status (Running → Completed).

## Reviewing Results
1. Click on the scan name to view detailed results.
2. Go to the **Vulnerabilities** tab for a list of detected issues.
3. Click on a vulnerability to view its details and recommended solutions.

## Generating a Report
1. Navigate to the **Report** menu.
2. Select **HTML** as the format and click **Generate Report**.
3. Open the downloaded report to view details and solutions.

## Mitigation
- Follow the recommended solutions from the report.
- Apply updates or patches as suggested.
- Re-run the scan to confirm remediation.

---
**End of Guide**

