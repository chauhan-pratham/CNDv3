### Partition Recovery Using MiniTool Power Data Recovery Tool: Summary Steps

1. **Launch Smoothwall Firewall VM**: 
   - Log in with password: `toor`.
   - Navigate to the Done button and press Enter.

2. **Launch Admin Machine-1 VM**: 
   - If not already launched, click on Admin Machine-1 and log in with username: `Admin` and password: `admin@123`.

3. **Check Available Partitions**: 
   - Open **File Explorer** and navigate to **This PC** to view available partitions (e.g., Local Disk (C:), New Volume (D:), New Volume (F:)).

4. **Delete a Partition**: 
   - Right-click the **Windows Start** icon and select **Disk Management**.
   - Right-click on **New Volume (D:)** and select **Delete Volume**. Confirm the deletion in the pop-up.

5. **Install MiniTool Power Data Recovery**: 
   - Navigate to `E:\CND-Tools\CNDv3 Module 10 Data Security\MiniTool Power Data Recovery`.
   - Double-click `pdr-free.exe` to launch the installer. Click **Yes** on the User Account Control pop-up and follow the installation steps.
   - **Important**: Do not install the software on the drive containing lost data to avoid overwriting.

6. **Launch MiniTool Power Data Recovery**: 
   - Once installation is complete, the tool will automatically launch. If prompted about a new version, click **No**.

7. **Select Partition for Recovery**: 
   - In the MiniTool interface, select **New Volume (NTFS)** under the **Lost Partition** section and click **Scan**.

8. **Review Scanned Results**: 
   - After the scanning process completes, view the list of drives and files under the **Path** tab.

9. **Recover Deleted Partition**: 
   - Check the partition that needs to be restored and click **Save**.
   - In the **Select a directory to save files** window, right-click on **Local Disk (C:)** and select **New Directory**. Name it **Recovered Data** and click **OK**.

10. **Finalize Recovery**: 
    - Select the **Recovered Data** folder and click **OK** to save the recovered files.

11. **Verify Recovered Files**: 
    - Navigate to `C:\Recovered Data` to confirm that the lost files from the deleted partition have been successfully restored.

By following these steps, you can effectively use MiniTool Power Data Recovery to recover deleted partitions, demonstrating the importance of having multiple recovery tools available for network defenders.