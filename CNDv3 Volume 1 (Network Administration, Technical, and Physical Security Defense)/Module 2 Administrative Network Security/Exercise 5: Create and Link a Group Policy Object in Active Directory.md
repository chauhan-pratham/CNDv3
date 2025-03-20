### Administrative Network Security Lab: Create and Link a Group Policy Object in Active Directory

**Objective:** Manage administration privileges in Active Directory to prevent privilege escalation and enhance security.

#### Lab Steps:

1. **Launch Smoothwall Firewall VM:**
   - Enter password: `toor`.
   - Navigate to Done and press Enter.

2. **Launch AD Domain Controller VM:**
   - Click Ctrl+Alt+Delete to log in.
   - Use username: `CND\Administrator`, password: `Pa$$w0rd`.

3. **Open Server Manager:**
   - Search for and open Server Manager.

4. **Access Active Directory Users and Computers:**
   - Click on Tools and select Active Directory Users and Computers.

5. **Modify Administrator Account Properties:**
   - Right-click on the Administrator account and select Properties.
   - Under the Account tab, check "Account is sensitive and cannot be delegated" and click OK.
   - Again, right-click on Administrator, go to Properties, and enable "Smart card is required for interactive logon."

6. **Create a Group Policy Object (GPO):**
   - In Server Manager, click Tools and select Group Policy Management.
   - Expand `<Forest>\Domains\<Domain>`, right-click on Group Policy Objects, and select New.
   - Name the GPO and click OK.

7. **Edit the GPO:**
   - Right-click on the newly created GPO and select Edit.
   - Navigate to Computer Configuration > Policies > Windows Settings > Security Settings > Local Policies > User Rights Assignment.

8. **Configure User Rights:**
   - **Deny access to this computer from the network:**
     - Double-click and select "Define these policy settings."
     - Click Add User or Group, type `Administrator`, check names, and click OK.
   - **Deny log on as a batch job:**
     - Repeat the above steps for "Deny log on as a batch job."
   - **Deny log on as a service:**
     - Repeat the above steps for "Deny log on as a service."

9. **Link the GPO:**
   - In Group Policy Management, navigate to `<Forest>\Domains\<Domain>`.
   - Right-click the OU where the GPO will be applied and select Link an existing GPO.
   - Choose the GPO you created and click OK.

10. **Implement Smart Card Requirement:**
    - Reboot the system to apply changes.
    - Upon login, the system will require a smart card or Windows Hello for authentication.

By following these steps, network security engineers can effectively implement security measures in Active Directory, restricting administrator privileges and enhancing overall network security.