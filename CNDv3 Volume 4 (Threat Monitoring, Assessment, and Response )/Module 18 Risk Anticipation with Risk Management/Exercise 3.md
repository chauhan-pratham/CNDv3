# Network Security Audit with Nsauditor

## Lab Overview
Nsauditor Network Security Auditor is used to scan networks and hosts for vulnerabilities and provide security alerts.

## Objectives
- Install Nsauditor Network Security Auditor
- Conduct a network security audit

## Steps to Audit Network Security with Nsauditor

### Step 1: Launch Admin Machine
1. Open **Admin Machine-1 -Mod 18 (COPY)**.
2. Click **Ctrl+Alt+Delete** to log in.
3. Log in with the password: `admin@123`.
4. If prompted with **"Let's finish setting up your PC"**, click **Remind me later**.

### Step 2: Install Nsauditor
1. Open **File Explorer** and navigate to:
   ```text
   E:\CND-Tools\Lab prerequisites\Nsauditor Network Security Auditor
   ```
2. Double-click **nsauditor_setup.exe**.
3. Click **Yes** on the User Account Control pop-up.
4. Follow the installation wizard:
   - Click **Next**.
   - Select **"I accept the Agreement"**, then click **Next**.
   - Keep the default path and click **Next**.
   - Keep the default Start Menu folder and click **Next**.
   - Check **Create a desktop icon** and click **Next**.
   - Click **Install**.
5. On the completion window, uncheck **Visit Home Page** and click **Finish**.

### Step 3: Audit the Network
1. Double-click the **Nsauditor** desktop icon.
2. If prompted, click **Yes** on the security pop-up.
3. In the Nsauditor interface:
   - Click **Auditor** in the left pane.
   - In the **Host Range and Credentials** dialog:
     - Enter the IP address `10.10.10.16` for the **Host Name / Address**.
     - Select **Other Credentials**.
     - Enter:
       - **Username:** `Local-Administrator`
       - **Password:** `admin@123`
     - Click **OK**.
4. To audit multiple hosts:
   - Select **IP Range** and specify the start and end IP addresses.

### Step 4: Run the Audit
1. In the **Network Audit** dialog, click **Start Audit**.
2. Once the audit is complete, ensure the **Notify** column shows **Finished**.

### Step 5: View Audit Report
1. Navigate to **Reports -> Audit Reports List**.
2. Select the most recent audit report and click **View**.
3. Review the detailed report to identify vulnerabilities and security issues.

## Conclusion
By following these steps, you have successfully performed a network security audit using Nsauditor.

