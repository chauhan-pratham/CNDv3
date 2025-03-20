# OSSIM Vulnerability Management Lab

## Objective
Perform vulnerability scanning using OSSIM to identify security issues in a network environment.

## Steps

### 1. Web Server Login
- Click **Web Server** VM and log in with:
  - **Username:** `admin@123`
  - **Password:** `admin@123`

### 2. OSSIM Server Login
- Launch **OSSIM Server** VM.
- Log in with:
  - **Username:** `root`
  - **Password:** `toor`

### 3. Admin Machine Login
- Launch **Admin Machine-1** VM.
- Log in with:
  - **Username:** `admin@123`
  - **Password:** `admin@123`

### 4. Access OSSIM Web UI
- Open Chrome and visit `https://10.10.10.75`.
- Bypass security warning and log in with:
  - **Username:** `admin`
  - **Password:** `admin@123`

### 5. Add Network Asset
- Navigate to **Environment > Assets & Groups**.
- Click **Add Asset** > **Add Host**.
- Enter:
  - **Name:** `Host-10-10-10-16`
  - **IP Address:** `10.10.10.16`
- Save the asset.

### 6. Edit Asset Details
- Select `Host-10-10-10-16` from the list.
- Click **Actions > Edit**.
- Set the following details:
  - **Asset Value:** `5`
  - **Operating System:** `Windows Server 2016`
  - **Device Type:** `Server > Web Server`
- Click **Save**.

### 7. Deploy HIDS Agent
- Select `Host-10-10-10-16` from the list.
- Click **Actions > Deploy HIDS Agent**.
- Enter:
  - **User:** `Administrator`
  - **Password:** `admin@123`
- Click **Deploy**.

### 8. Verify HIDS Agent
- Navigate to **Environment > Detection**.
- Click **HIDS Control** and restart the HIDS service.
- Verify `HIDS STATUS` shows **Connected**.

### 9. Create Credentials for Vulnerability Scan
- Go to **Environment > Vulnerabilities**.
- Click **Settings > Create Credential**.
- Enter:
  - **Name:** `Credentials1`
  - **Login:** `WORKGROUP\Administrator`
  - **Password:** `admin@123`
- Click **Create Credential**.

### 10. Perform Vulnerability Scan
- Navigate to **Environment > Vulnerabilities**.
- Click **Scan Jobs > New Scan Job**.
- Enter:
  - **Job Name:** `Vulnerability Scan`
  - Set **SMB Credential** as `Credentials1`.
  - Select `Host-10-10-10-16` under **All Assets**.
- Save and start the scan.

### 11. Review Results
- Once the scan completes, view the report:
  - Click the **PDF** icon under **Actions** for detailed results.

---
**End of Lab**

