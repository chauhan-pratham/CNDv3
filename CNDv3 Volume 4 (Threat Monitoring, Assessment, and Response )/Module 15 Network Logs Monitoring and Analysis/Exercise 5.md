# Network Logs Monitoring and Analysis with New Relic

## Lab Objectives
- Monitor and analyze network traffic logs.
- Track logon activities and system network processes via charts.

## Lab Overview
New Relic offers real-time network monitoring, system log management, and data visualization to enhance security and system performance.

## Lab Tasks
### Step 1: Log in to Admin Machine-1
- Launch Admin Machine-1 VM.
- Login with `admin@123` credentials.

### Step 2: Access New Relic
- Open Chrome and visit [https://newrelic.com](https://newrelic.com).
- Sign up or log in with your email.

### Step 3: Install New Relic Agent
- Choose **Windows** as the environment.
- Create a **User Key** and copy it.
- Copy the provided installation command.
- Run PowerShell as Administrator and execute the command.

### Step 4: Verify Installation
- Return to the New Relic interface.
- Click **Continue** to confirm successful installation.

### Step 5: View Logs
- Under **Hosts**, select **Admin Machine-1**.
- Navigate to **Logs** and click **Open in logs** for detailed log entries.

### Step 6: Monitor Network Traffic
- Go to the **Network** tab to analyze:
  - Transmit bytes
  - Receive bytes
  - Receive errors

### Step 7: Diagnose with Lookout
- Under **TRIAGE**, access **Diagnose with Lookout** for detailed traffic insights.

### Step 8: Simulate Network Activity
- On the **Attacker Machine VM**, log in with:
  - Username: `bob`
  - Password: `user@123`
- Open Terminal and run:
  ```sh
  sudo su
  [enter password: user@123]
  ping 10.10.10.2
  ```
- Stop the ping scan with `Ctrl + Z`.

### Step 9: Confirm Network Activity in New Relic
- Switch back to Admin Machine-1 and check for traffic spikes in the **Network** tab.
- Download traffic charts from **Diagnose with Lookout** for reporting.

## Conclusion
New Relic effectively monitors network traffic and logon events, assisting network defenders in identifying potential attacks and ensuring system security.

