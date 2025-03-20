### Summary of Steps for Endpoint Protection using ManageEngine Endpoint Central

1. **Launch Admin Machine VM**: Start the Admin Machine VM and log in with the default credentials (admin@123).

2. **Install ManageEngine Endpoint Central**:
   - Navigate to the installation file in the specified directory.
   - Copy `ManageEngine_Endpoint_Central_Evaluation Kit.exe` to the Desktop and run it.
   - Follow the installation wizard, accepting defaults for destination folder, port, and folders.
   - Complete the installation and launch the software in a browser.

3. **Initial Setup**:
   - Sign in with default credentials (admin/admin).
   - Associate an email ID and set preferences (e.g., time zone, language).

4. **Prohibit Software**:
   - Navigate to **Application Control > Prohibit Software**.
   - Click **+ Add Prohibited SW**, search for `Notepad++`, and add it to the prohibited list.
   - Configure the uninstall command with `/SILENT` and enable the auto-uninstall policy, setting it to remove prohibited software after 2 days.

5. **Service Management**:
   - Stop and restart the ManageEngine service using the system tray icon.

6. **Scan Systems**:
   - Go to **Inventory**, select **Scan Systems**, and scan the Admin Machine.

7. **Check Prohibited Software**:
   - After rebooting, check the prohibited software list and view details of detected software.
   - Users can request software exclusion via email.

8. **Approve/Deny User Requests**:
   - Navigate to **User Requests** under the Prohibit Software tab.
   - Approve or deny requests based on user needs, adding comments if necessary.

9. **Block Executable Files**:
   - Go to **Block Executable** and click **Add Policy**.
   - Create a custom group (e.g., All Computers) and add Admin-Machine-1.
   - Add `firefox.exe` to the block list.

10. **Policy Management**:
    - Review and modify or delete policies as needed to maintain endpoint security.

This concise guide outlines the essential steps for using ManageEngine Endpoint Central to manage application control and enhance endpoint security effectively.