### Implementing Password Policies Using Windows Group Policy Lab Summary

**Objective:** Learn how to create and implement a Group Policy Object (GPO) to enforce password policies in an Active Directory (AD) environment, enhancing security against unauthorized access.

**Overview:** The Group Policy Management Console (GPMC) allows network defenders to manage password policies, including complexity requirements, password length, and history. This helps protect user accounts from brute-force attacks.

**Lab Steps:**

1. **Setup:**
   - Launch the Smoothwall Firewall VM and log in with the password `toor`.
   - Launch the Active Directory Domain Controller VM and log in with the `CND\Administrator` account using the password `Pa$$w0rd`.

2. **Access Group Policy Management:**
   - Open the Group Policy Management Console (GPMC) via Windows Start -> Windows Administrative Tools or by typing `gpmc.msc` in the Run dialog.

3. **Create a New GPO:**
   - In the GPMC, expand the domain tree for `CND.com`.
   - Right-click on the domain and select "Create a GPO in this domain, and Link it here…".
   - Name the new GPO "ECCPassword Policy" and click OK.

4. **Edit the GPO:**
   - Right-click on "ECCPassword Policy" and select "Edit…".
   - Navigate to **Computer Configuration -> Policies -> Windows Settings -> Security Settings -> Account Policies -> Password Policy**.
   - Enable the "Password must meet complexity requirements" policy by double-clicking it, checking "Define this policy setting," and selecting "Enabled".

5. **Enforce the GPO:**
   - Right-click on "ECCPassword Policy" and select "Enforced" to ensure it cannot be overridden by other GPOs.
   - Link the GPO to the appropriate Organizational Unit (OU) if necessary.

6. **Apply the GPO to Specific Users:**
   - Under the Security Filtering section of "ECCPassword Policy," click "Add…".
   - Type "Martin" in the object name textbox and click "Check Names" to confirm.

7. **Force Password Change:**
   - Open Active Directory Users and Computers (dsa.msc) and locate user Martin.
   - In Martin's properties, check "User must change password at next logon" and uncheck "Password never expires" if checked.

8. **Test the Policy:**
   - Launch the Finance Department VM and log in as user Alice.
   - Change the computer's domain to `CND.com` and log in with the administrator credentials.
   - Restart the system and log in as user Martin.

9. **Update Group Policy:**
   - Open Command Prompt and run `gpupdate /force` to apply the new group policy settings.

10. **Observe Password Change Requirements:**
    - Log out from Alice and log in as Martin.
    - Attempt to change the password to a simple one (e.g., `test123`) to see the complexity requirement in action.
    - The system will reject the simple password, prompting for a more complex one (e.g., `Test@123`), which meets the policy requirements.

**Conclusion:** This lab demonstrates how to effectively implement and enforce password policies using Group Policy in an Active Directory environment. By requiring complex passwords, organizations can significantly enhance their security posture against unauthorized access.