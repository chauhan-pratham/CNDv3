# Vulnerability Management using SecPod SanerNow

## Overview
SecPod SanerNow is a cloud-based vulnerability and patch management tool designed to identify and manage security risks across IT infrastructures.

## Lab Objectives
Demonstrate how to use SecPod SanerNow to detect and remediate vulnerabilities in network machines.

## Lab Steps

### 1. Setup and Installation
- Sign up on [SanerNow](https://sanernow.com/) using your work email.
- Launch **Admin Machine-1 - Mod 18 (COPY)** VM.
- Log in using credentials:
  - **Username:** `admin@123`
  - **Password:** `admin@123`
- Open **Google Chrome** and visit `saner.secpod.com`.
- Sign in with your registered credentials.

### 2. Agent Deployment
- Navigate to **Settings** ➔ **Agents Deployment**.
- Select **Windows distribution** and download the agent.
- Extract the downloaded `.zip` file.
- Copy the extracted folder to `E:\CND-Tools\CNDv3 Module 18 Risk Anticipation with Risk Management`.
- Run `SanerNow.exe` and follow the installation wizard:
  - Select `spsaneractivation.conf` when prompted.
  - Retain the default installation path and complete the installation.

### 3. Web Server Setup
- Switch to the **Web Server VM** and repeat the agent installation steps.

### 4. Viewing Results
- Switch back to **Admin Machine-1** and refresh the SanerNow page.
- Verify that 2 devices are added, and review the **Cyber Hygiene Score**.
- Open **Vulnerability Management** to view:
  - Vulnerable devices with risk counts.
  - Vulnerability details with severity levels.

### 5. Remediation Setup
- Navigate to **Settings ➔ Agent Configuration**.
- Click **Create Settings** ➔ Select **Remediate**.
- Choose **Default with Alternate/Secondary Microsoft Patch Server**.
- Name the setting as **Remediations** and click **Create**.

### 6. Patching Vulnerabilities
- In **Patch Management**, select **Missing Patches**.
- Choose vulnerabilities to patch and click **Apply Selected Patches**.
- In the pop-up window:
  - Set **Task Name** as `FireFox task`.
  - Select **Remediation Schedule** as `Immediate`.
- Click **Apply Selected Patches** to complete the remediation.

## Outcome
The network vulnerabilities are detected, analyzed, and successfully remediated using SecPod SanerNow.

