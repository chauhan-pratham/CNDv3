### Summary of Steps for Securing Windows File Share in Active Directory

1. **Launch Smoothwall Firewall VM**: 
   - Log in with the password `toor`.

2. **Launch AD Domain Controller VM**: 
   - Click on AD Domain Controller and log in with `CND\Administrator` and password `Pa$$w0rd`.

3. **Open Server Manager**: 
   - Click the Windows Start button and select Server Manager.

4. **Create a New Share**:
   - Navigate to File and Storage Services > Shares.
   - Click on the TASKS dropdown and select "New Share…".
   - Choose "SMB Share - Quick" and click Next.
   - Select Volume D: as the share location and name it "FinanceData".

5. **Configure Share Settings**:
   - Enable access-based enumeration and click Next.
   - Click "Customize permissions…" to modify default permissions.

6. **Disable Inheritance**:
   - In the Advanced Security Settings, click "Disable inheritance" and convert inherited permissions to explicit permissions.
   - Remove permissions for `CND\Users` (Read & execute and Special access).

7. **Create FinanceData Security Group**:
   - Open Active Directory Users and Computers from the Tools menu.
   - Right-click on FinanceUsers OU, select New > Group.
   - Name the group "FinanceData" with Global scope and Security type.

8. **Add Users to Group**:
   - Add users Bob and John to the FinanceData group by right-clicking on each user and selecting "Add to a group…".

9. **Set Permissions for FinanceData Share**:
   - Right-click on the FinanceData share and select Properties.
   - In the Permissions section, click "Customize permissions…".
   - Add the FinanceData group and set advanced permissions (e.g., Traverse folder, List folder, Read attributes, Create files).

10. **Verify Permissions from Client Machine**:
    - Launch Finance-Dept VM and log in as `Finance-Dept\Alice`.
    - Change the computer's domain to WORKGROUP and then back to `cnd.com` to join the domain.

11. **Access the Shared Folder**:
    - Log in as John (`John@cnd.com`) and use Run to access `\\DOMAINCONTROLL` to view the FinanceData share.
    - Confirm that John can access the folder.

12. **Test Access for Unauthorized User**:
    - Log in as Martin (`martin@cnd.com`) and attempt to access the FinanceData share.
    - Confirm that Martin receives a Network Error message indicating lack of permission.

13. **Close All Windows**: 
    - Exit all open windows in both Finance-Dept and AD Domain Controller VMs.

By following these steps, network defenders can effectively manage permissions for shared folders in Active Directory, ensuring that only authorized users have access to sensitive data.