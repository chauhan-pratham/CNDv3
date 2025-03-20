### Summary of Steps for File Integrity Monitoring in Windows System using ManageEngine OpManager

1. **Launch VMs**:
   - Start the **Smoothwall Firewall** VM and log in with the password `toor`.
   - Launch the **AD Domain Controller** VM and log in using the default account `CND\Administrator` with the password `Pa$$w0rd`.

2. **Install ManageEngine OpManager**:
   - Navigate to the installation file in the specified directory and run `ManageEngine_OpManager_64bit.exe` as Administrator.
   - Follow the installation wizard, accepting the license agreement and keeping default settings for the destination folder and port.
   - Select the **POSTGRESQL** option and complete the installation.

3. **Access OpManager**:
   - Launch ManageEngine OpManager and select Google Chrome to open the application.
   - Bypass the security warning by clicking on **Advanced** and then **Proceed to localhost (unsafe)**.
   - Log in to the OpManager interface.

4. **Configure File Integrity Monitoring**:
   - Navigate to the **Settings** tab and scroll to **Security Settings**.
   - Click on the **File Integrity** tab to access the FIM feature.

5. **Tamper a File**:
   - Go to `C:\Program Files\ManageEngine\OpManager\conf\Authentication` and edit the `auth-conf` file using Notepad++.
   - Delete the existing content and replace it with the following code, then save it as `shutdown.bat`:
     ```
     @echo shutdown -s -t 0
     ```

6. **Scan for File Integrity**:
   - In the OpManager console, click on **Scan Now** under the File Integrity tab.
   - After the scan completes, a notification will appear indicating the scan results. Click the hyperlink to view details.

7. **Blacklist Tampered File**:
   - Identify the tampered file (`shutdown.bat`) in the scan results.
   - Select **Blacklist** from the **Select Action** dropdown and click **Apply** to blacklist the file.

8. **Review Reports**:
   - Navigate to the **Reports** tab to view details of the tampered file and actions taken.
   - You can choose to **Whitelist** or **Exclude from Scanning** for specific files as needed.

By following these steps, network defenders can effectively monitor file integrity and respond to unauthorized changes, thereby enhancing the security of Windows systems against malicious activities.