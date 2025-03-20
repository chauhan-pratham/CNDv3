### Summary of Steps for Remote Patch Management Using ManageEngine Patch Manager Plus

1. **Launch VMs**: Start the Smoothwall Firewall, AD Domain Controller, and Admin Machine-1 VMs. Log in using the provided credentials.

2. **Install ManageEngine Patch Manager Plus**:
   - Navigate to `E:\CND-Tools\CNDv3 Module 05 Endpoint Security-Windows Systems\ManageEngine Patch Manager Plus`.
   - Double-click `ManageEngine_Patch_Manager_Plus.exe` to start the installation. Accept any prompts that appear.
   - Follow the installation wizard, accepting the license agreement and retaining default settings until completion. Click "Finish" when done.

3. **Access Patch Manager Plus**:
   - Close any default browser window that opens after installation.
   - Wait for the ManageEngine Patch Manager Plus service to start, indicated by a green icon in the taskbar.
   - Open a web browser and log in to ManageEngine Patch Manager Plus using the default credentials.

4. **Add Domain**:
   - Click on "Agent" from the main menu, then select "Computers" under the Scope of Management dropdown.
   - Click the "+Add Computers" button, then "Add Domain."
   - Fill in the domain details for `cnd.com` and click "Add Domain." Sync the domain to make the computers visible.

5. **Install Agents**:
   - Select all visible machines and click "Next."
   - Click "Install Agents" to install the ManageEngine Patch Manager Plus agents on the selected machines.

6. **Scan Systems**:
   - Navigate to "Systems" and click on "Scan Systems."
   - Click "View Status" under "Update Vulnerability DB" and configure proxy settings to connect directly to the internet if necessary.
   - Update the Vulnerability DB by clicking "Update Now."

7. **Perform Patch Scan**:
   - Click on the TV icon next to the Finance-Dept under Computer Name and select "Patch Scan."
   - Refresh the page to monitor the progress of the scan.

8. **Review Scan Results**:
   - Once the scan is complete, view the Network Scan Summary and the list of scanned machines.
   - Click on the Finance-Dept Computer Name to access the scanned report.
   - Navigate to the "Missing Patches" tab to view any missing patches, or check the "Installed Patches" tab for details on installed updates.

By following these steps, network defenders can effectively manage and deploy patches across remote systems using ManageEngine Patch Manager Plus.