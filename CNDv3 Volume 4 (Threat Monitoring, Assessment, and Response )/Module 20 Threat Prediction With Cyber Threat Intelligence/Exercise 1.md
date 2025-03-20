## Exercise 1: Integrating OTX Threat Feeds in OSSIM

### Overview
AlienVault Open Threat Exchange (OTX) is a threat information sharing network. Integrating OTX pulses with OSSIM enhances security monitoring by providing actionable threat intelligence.

### Lab Objectives
- Learn to integrate OTX pulses into OSSIM for enhanced security.

### Steps to Integrate OTX with OSSIM

1. **Launch Admin Machine-1**
   - Click **Admin Machine-1** VM.
   - Click **Ctrl+Alt+Delete** and log in with:
     - **Username:** `admin`
     - **Password:** `admin@123`

2. **Sign up for an OTX Account**
   - Open **Google Chrome**.
   - Go to [OTX AlienVault](https://otx.alienvault.com).
   - Fill in the required details and click **SIGN UP**.
   - Activate your account via the confirmation email.

3. **Retrieve OTX Key**
   - Log in to your OTX account.
   - Click the **Settings** icon in the top-right corner.
   - Copy the **OTX Key** from the settings page.

4. **Access OSSIM Server**
   - Click **OSSIM Server** VM.
   - Log in with:
     - **Username:** `root`
     - **Password:** `toor`

5. **Login to OSSIM Interface**
   - Switch to **Admin Machine-1**.
   - Open **Google Chrome** and navigate to `https://10.10.10.75`.
   - Click **Advanced** and then **Proceed to 10.10.10.75 (unsafe)**.

6. **Connect OTX to OSSIM**
   - Log in with:
     - **Username:** `admin`
     - **Password:** `admin@123`
   - Click **Skip AlienVault Wizard**.
   - Click **CANCEL** on the improvement pop-up.
   - Go to **Configuration** > **Open Threat Exchange**.
   - Paste the copied **OTX Key** into the **OTX Key** field and click **CONNECT OTX ACCOUNT**.

7. **Verify Integration**
   - OSSIM will connect to your OTX account and begin downloading subscribed pulses.
   - Refresh the OSSIM browser with **F5** to view the downloaded pulses.

### Conclusion
OSSIM is now integrated with OTX, enabling real-time threat detection based on subscribed pulses.

