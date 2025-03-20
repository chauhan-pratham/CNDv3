### Summary of Steps for Implementing Suricata IDS with Splunk

1. **Login to Admin Machine-1:**
   - Use Ctrl+Alt+Delete to log in with username `Admin` and password `admin@123`.

2. **Access Splunk Enterprise:**
   - Open a web browser and navigate to `http://localhost:8000/en-US/account/login?`.
   - Log in with username `admin` and password `admin@123`.

3. **Check Splunk Service:**
   - If the page doesn’t load, ensure the `splunkd` service is running. Restart it via `services.msc` if necessary.

4. **Configure Splunk to Receive Data:**
   - Go to **Settings** > **Forwarding and receiving**.
   - Click **+Add new** and enter port `9997`, then click **Save**.

5. **Enable SplunkForwarder App:**
   - Navigate to **Apps** > **Manage Apps**.
   - Enable the **SplunkForwarder** application and edit its properties to make it visible.

6. **Restart Splunk:**
   - Go to **Settings** > **Server controls** and click **Restart Splunk**. Confirm the restart.

7. **Log Back into Splunk:**
   - After the restart, log in again with `admin` and `admin@123`.

8. **Verify Splunk Forwarder:**
   - Ensure the Splunk Forwarder service is running in Windows services.

9. **Access Data Summary:**
   - Click on **Apps** > **SplunkForwarder**.
   - In the Search console, select **Data Summary** > **Sources** tab.
   - Click on the `C:\Program Files\Suricata\log\stats.log` link to view detailed logs.

10. **Close Applications:**
    - Close the web browser on Admin Machine-1 and all windows on the Web Server VM.

---

This summary captures the essential steps while maintaining clarity and brevity. Let me know if you need any further modifications!