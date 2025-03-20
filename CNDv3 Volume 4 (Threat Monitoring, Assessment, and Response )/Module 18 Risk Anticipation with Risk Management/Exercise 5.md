# Vulnerability Management of Windows Server using OpenSCAP

## Overview
OpenSCAP is an open-source framework for security compliance checking, vulnerability management, and configuration assessment of computer systems.

## Lab Objectives
- Perform vulnerability scanning on Windows Server.
- Identify threat levels for vulnerabilities.

## Steps
### 1. Setup OpenSCAP
- Launch Web Server VM and log in using `admin@123`.
- Navigate to `Z:\CNDv3 Module 18 Risk Anticipation with Risk Management\OpenSCAP`.
- Install `OpenSCAP-1.3.0-win32` following on-screen instructions.

### 2. Download Required Files
- Visit [SCAP Website](https://public.cyber.mil/stigs/scap/).
- Download:
  - `Microsoft Windows Server 2022 STIG Benchmark` (latest version).
  - `SCC 5.10 Windows` ZIP file.
- Extract both ZIP files and move them to `C:\OpenSCAP`.

### 3. Setup SCC (SCAP Compliance Checker)
- Run `SCC-5.10_Windows_setup` as Administrator.
- Follow instructions to install SCC and create a desktop shortcut.

### 4. Configure SCC for Scanning
- Launch SCC and delete all content in the "Windows" section.
- Install the `U_MS_Windows_Server_2022_V1R2_STIG.xml` content.
- Set output directory to `C:\OpenSCAP\OpenSCAP_Report`.
- Start the scan and view results.
- Save the HTML report.

### 5. Install STIG Viewer
- Download `STIG Viewer 3.4-Win64` from the SCAP website.
- Extract files and move them to `C:\OpenSCAP\STIG_Viewer`.
- Run `STIG Viewer 3` as Administrator.

### 6. Generate Checklist
- Open STIG Viewer, select `Open STIG Explorer > Open STIG`.
- Load `U_MS_Windows_Server_2022_V2R2_STIG` file.
- Create and save a checklist in `C:\OpenSCAP\STIG_Checklist` as `Windows_Server_2022`.

### 7. Import Results
- Import the XCCDF file from `C:\OpenSCAP\OpenSCAP_Report\Sessions\<date>\Results\SCAP\XML`.
- View results with CAT I, CAT II & CAT III severity details.
- Save the final checklist.

## Conclusion
This process helps network defenders use OpenSCAP for security compliance, vulnerability assessment, and configuration checks effectively.

