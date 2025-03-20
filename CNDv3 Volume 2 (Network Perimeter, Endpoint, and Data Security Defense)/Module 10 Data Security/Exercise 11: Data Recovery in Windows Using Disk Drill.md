### Summary of Steps for Data Recovery in Windows Using Disk Drill

1. **Launch Smoothwall Firewall VM**: Log in with the password `toor` and wait for the system to load.

2. **Launch Admin Machine-1 VM**: Log in using `Admin` as the username and `admin@123` as the password.

3. **Prepare for Recovery**:
   - Navigate to "This PC" and select Local Disk (F:).
   - If no files exist, create a zip file, a folder, and a text file named "CND Ex Document," "CND compliance documents," and "CND file storage records."
   - Delete the created files using Shift + Delete to bypass the Recycle Bin.

4. **Install Disk Drill**:
   - Navigate to `E:\CND-Tools\CNDv3 Module 10 Data Security\Disk Drill` and double-click `disk-drill-win.exe`.
   - Follow the installation wizard and allow User Account Control prompts.

5. **Launch Disk Drill**: Click on the Launch button after installation and close any software update windows.

6. **Scan for Lost Data**:
   - In the Disk Drill dashboard, expand the Virtual HD dropdown and select the drive where files were deleted (New Volume F:).
   - Click on "Search for lost data" to initiate the scan.

7. **Review Found Items**: Once the scan is complete, click on "Review found items" and expand the Deleted or lost section to view deleted files.

8. **Preview and Recover Files**:
   - Hover over files to preview their content by clicking the eye icon.
   - Checkmark the files you wish to recover and click "Recover."

9. **Choose Recovery Destination**:
   - In the Choose Destination popup, check "Save all files to one folder" and select the Document folder in C: drive as the destination.
   - Click "Select Folder" and then "Next" to complete the recovery.

10. **Verify Recovery**: Click on "View Logs" to see the number of files restored or "Show recovered files in Explorer" to view the recovered files.

By following these steps, network defenders can effectively use Disk Drill to recover lost or deleted files, safeguarding critical organizational data.