### File Recovery Using EaseUS Data Recovery Wizard: Summary Steps

1. **Launch Smoothwall Firewall VM**: 
   - Log in with password: `toor`.
   - Navigate to the Done button and press Enter.

2. **Launch Admin Machine-1 VM**: 
   - If not already launched, click on Admin Machine-1 and log in with username: `Admin` and password: `admin@123`.

3. **Prepare for Deletion**: 
   - Ensure there are files or folders in the **F:** drive (specifically **F:\My File Backup**). If not, create some files or folders to delete.

4. **Delete Files**: 
   - Delete the **My File Backup** folder to simulate accidental deletion.

5. **Install EaseUS Data Recovery Wizard**: 
   - Open Windows Explorer and navigate to `E:\CND-Tools\CNDv3 Module 10 Data Security\EaseUS`.
   - Double-click `drw_free_installer_20230703.153`.
   - Click **Yes** on the User Account Control pop-up and then click **Install Now** in the installer.

6. **Start EaseUS Data Recovery Wizard**: 
   - Once installation is complete, the EaseUS Data Recovery Wizard will automatically start. Follow the wizard to reach the main window.

7. **Select Location for Recovery**: 
   - In the EaseUS Data Recovery Wizard, select the **F:** drive (the partition from which you deleted files) and click **Search for lost data**.

8. **Recover Deleted Files**: 
   - Select **Deleted Files** from the search results and click **Recover**. If the files are not found, perform a **Deep Scan** for more thorough recovery.

9. **Save Recovered Files**: 
   - Choose a location to save the recovered files and click **Select Folder**.

10. **View Recovery Report**: 
    - A recovery report will be displayed, and you will be redirected to the folder containing the recovered files.

11. **Verify Recovered Files**: 
    - Navigate to the location where the recovered files were saved to confirm that the files have been successfully restored.

By following these steps, you can effectively recover deleted files using EaseUS Data Recovery Wizard, demonstrating the importance of data recovery tools for network defenders in managing data loss scenarios.