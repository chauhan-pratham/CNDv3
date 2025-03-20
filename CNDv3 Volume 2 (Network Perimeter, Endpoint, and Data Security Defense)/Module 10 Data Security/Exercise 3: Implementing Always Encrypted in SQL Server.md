### Implementing Always Encrypted in SQL Server: Summary Steps

1. **Launch Smoothwall Firewall VM**: 
   - Login with password: `toor`.
   - Navigate to the Done button and press Enter.

2. **Launch WebServer VM**: 
   - Click Ctrl+Alt+Delete to login.
   - Use username: `Administrator` and password: `admin@123`.
   - Close the Server Manager dashboard if it appears.

3. **Open SQL Server Management Studio (MSSMS 19)**: 
   - Search for and select MSSMS 19 from the Start menu.

4. **Connect to SQL Server**: 
   - In the Connect to Server window, select:
     - Server type: Database Engine
     - Server name: Webserver
     - Authentication: SQL Server Authentication
     - Username: `sa`
     - Password: `qwerty@123`
   - Click Connect.

5. **Navigate to CNDAccess Database**: 
   - In Object Explorer, expand Databases and locate CNDAccess.

6. **Encrypt Columns**: 
   - Right-click on CNDAccess database, select Tasks -> Encrypt Columns.
   - In the Always Encrypted wizard, click Next through the introduction and column selection.
   - Select the `Empid` column, choose Encryption Type as **Deterministic**, and keep the default Encryption Key (CEK_Auto1). Click Next.

7. **Configure Master Key**: 
   - Keep the default settings for the Master Key Configuration and click Next.

8. **In-Place Encryption Settings**: 
   - Click Next.

9. **Run Settings**: 
   - Click Next to finalize the setup.

10. **Completion**: 
    - Review the Summary and click Finish. Wait for the process to complete.

11. **Verify Encryption**: 
    - After completion, check the encryption by expanding the CNDAccess database, navigating to Tables, and right-clicking `dbo.empdata` to select Top 1000 Rows. 
    - Confirm that the `Empid` column is encrypted.

This summary captures the essential steps for implementing the Always Encrypted feature in SQL Server while maintaining clarity and brevity.