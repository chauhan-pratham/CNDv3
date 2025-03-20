### Performing Data Backup Using AOMEI Backupper Standard: Summary Steps

1. **Launch Smoothwall Firewall VM**: 
   - Log in with password: `toor`.
   - Navigate to the Done button and press Enter.

2. **Launch Admin Machine-1 VM**: 
   - If not already launched, click on Admin Machine-1 and log in with username: `Admin` and password: `admin@123`.

3. **Prepare Backup Folder**: 
   - Copy the **Test Documents** folder from `E:\CND-Tools\CNDv3 Module 10 Data Security\AOMEI Backupper` and paste it on the desktop of Admin Machine-1.

4. **Install AOMEI Backupper**: 
   - Navigate to `E:\CND-Tools\CNDv3 Module 10 Data Security\AOMEI Backupper` and double-click `AOMEIBackupperStd_20231221.8831304.exe`.
   - Click **Yes** on the User Access Control prompt and follow the installation wizard.
   - Select the setup language and click **OK**. If prompted with a "Better Choice" window, click **Skip**.
   - Click **Install Now** and wait for the installation to complete. Close the default browser window that opens and click **Enjoy Now**.

5. **Create a New Backup**: 
   - In the AOMEI Backupper Standard window, click **New Backup** and select **File Backup**.
   - Click **Add Folder** and select the **Test Document** folder on the desktop. Choose the target location as the **F:** drive.

6. **Schedule Backup**: 
   - Click **Schedule Backup** at the bottom of the window. In the Schedule Backup Settings, select the **Backup Scheme** tab and choose **Full Backup**. Click **OK**.
   - Click **Start Backup** to initiate the backup process and confirm to start the backup now.

7. **Finish Backup**: 
   - AOMEI Backupper will store the backup file in the target location (F:). Click **Finish** once the backup is complete.
   - The Backup Management window will confirm the creation of **My File Backup**.

8. **Perform Incremental Backup**: 
   - In the AOMEI Backupper Standard window, hover over the **My File Backup** tab, click the ellipse button, and select **Backup > Incremental Backup**.
   - Confirm the action in the dialog box and click **OK**. Wait for the backup process to complete and click **Finish**.

9. **Verify Backup**: 
   - Open the **Test Document** folder on the desktop and create a new file named **New Doc2.txt** to add data.
   - Navigate to the **F:** drive, open the **My File Backup** folder, and verify that the new backup file has been created.

10. **Uninstall AOMEI Backupper**: 
    - After completing the exercise, uninstall AOMEI Backupper to proceed to the next lab.

By following these steps, you can effectively perform data backups using AOMEI Backupper, ensuring data integrity and availability for recovery in case of data loss.