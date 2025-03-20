### Summary of Steps for Delegating Admin Permission to User Using Delegation of Control Wizard

1. **Launch VMs**: Start the Smoothwall Firewall and AD Domain Controller VMs. Log in using the provided credentials.

2. **Open Active Directory Users and Computers**:
   - In the AD Domain Controller, open Server Manager from the Start menu.
   - Navigate to "Tools" and select "Active Directory Users and Computers."

3. **Start Delegation of Control Wizard**:
   - Right-click on the `FinanceOU` under `cnd.com` and select "Delegate Control…"
   - Click "Next" in the Delegation of Control Wizard.

4. **Add User or Group**:
   - Click the "Add…" button under the User or Groups section.
   - Type `Admin-Support` in the object name field, click "Check Names," and then click "OK." If necessary, use the "Advanced" option to find the group.

5. **Select Tasks to Delegate**:
   - Click "Next" and check the following tasks to delegate:
     - Create, delete, and manage user accounts
     - Reset user passwords and force password change at next logon
     - Read all user information
     - Modify the membership of a group
   - Click "Next" and review the summary.

6. **Finish the Wizard**: Click "Finish" to complete the delegation process.

7. **Verify Delegated Permissions**:
   - Switch to the Finance-Dept -Mod 5 (COPY) VM and log in as `FinanceAdmin1` using the credentials provided.
   - Open "Active Directory Users and Computers" from the Windows Tools menu.
   - Expand the `CND.com` domain and navigate to `Finance OU` to see the `Admin-Support` group and `FinanceAdmin1` user.

8. **Check Permissions**:
   - Right-click on `FinanceOU` and verify that `FinanceAdmin1` can only create new users and has no other options.

9. **Create a New User**:
   - Right-click on `FinanceOU`, select "New" > "User."
   - Enter `User1` as the first name and logon name, then click "Next."
   - Set the password to `U$er@12345`, uncheck all checkboxes, and click "Next" and then "Finish."

10. **Delete the User**:
    - Right-click on `User1` and select "Delete." Confirm the deletion.

11. **Sign Out**: Sign out from `FinanceAdmin1` and close all open windows in both the Finance-Dept and AD Domain Controller VMs.

By following these steps, network defenders can effectively delegate specific administrative permissions to users using the Delegation of Control Wizard, enhancing security and management within Active Directory.