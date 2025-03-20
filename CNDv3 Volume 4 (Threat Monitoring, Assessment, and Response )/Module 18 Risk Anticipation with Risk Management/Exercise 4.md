# Application Vulnerability Scanning using OWASP ZAP

## Overview
OWASP ZAP is an open-source security tool for detecting web application vulnerabilities. This guide explains how to perform a vulnerability scan using OWASP ZAP.

## Lab Setup
1. **Launch VMs:**
   - Start **Web Server VM** (Login: `Administrator / admin@123`).
   - Start **AdminMachine-1 VM** (Login: `admin@123`).
2. Allow the "PC discoverable" prompt by selecting **Yes** if prompted.

## OWASP ZAP Configuration
1. **Open OWASP ZAP 2.14.0** on AdminMachine-1.
2. If "Windows Protected your PC" appears, click **Run anyway**.
3. Select **No, I do not want to persist this session** and click **Start**.
4. Close the **Manage Add-ons** pop-up if it appears.

## Performing the Scan
1. Select **Automated Scan**.
2. Enter the target URL: `http://www.luxurytreats.com` and click **Attack**.
3. Wait for the scan to complete (indicated by the highlighted **Stop** button).
4. Click the following tabs to review results:
   - **Spider Tab:** View crawled URLs.
   - **Active Scan Tab:** See active scan progress.
   - **Alerts Tab:** Review detected vulnerabilities.

## Generating the Report
1. Navigate to **Reports** → **Generate Report**.
2. Save the report as `Report.html` on the desktop.
3. Open the file in your browser to review the detailed results.

## Conclusion
This guide demonstrates how to conduct vulnerability scanning on a target application using OWASP ZAP.

