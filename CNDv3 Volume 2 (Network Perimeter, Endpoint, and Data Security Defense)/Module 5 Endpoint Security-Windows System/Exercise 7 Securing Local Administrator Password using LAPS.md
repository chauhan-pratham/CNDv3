### Summary of Steps for Securing Local Administrator Password Using LAPS

1. **Prepare Environment**:
   - Ensure the PfSense Firewall is running.
   - Launch the Smoothwall Firewall and AD Domain Controller VMs, logging in with the provided credentials.
   - Launch the Finance-Dept VM and log in as `Finance-Dept\Alice`.

2. **Join Finance-Dept VM to Domain**:
   - Change the computer's domain to `WORKGROUP`, then restart.
   - After restarting, change the computer's domain back to `cnd.com` and restart again.

3. **Install LAPS on AD Domain Controller**:
   - Navigate to `Z:\CNDv3 Module 05 Endpoint Security-Windows Systems\LAPS` and run `LAPS.x64.exe`.
   - Follow the installation prompts, accepting the license agreement and installing the management tools.

4. **Create Organizational Unit (OU) and Group**:
   - In Active Directory Users and Computers, create a new OU named `CNDclient`.
   - Create a new group named `LAPSusers` under the `CNDclient` OU.
   - Create a user named `Jimmy`, set the password, and add him to the `LAPSusers` group.

5. **Move Finance-Dept VM to CNDclient OU**:
   - Move the `FINANCE-DEPT` computer to the `CNDclient` OU.

6. **Create Group Policy Object (GPO) for LAPS**:
   - Open Group Policy Management and create a new GPO named `laps5801` linked to the `CNDclient` OU.
   - Import the LAPS PowerShell module and extend the Active Directory schema using `Update-AdmPwdADSchema`.

7. **Set Permissions for LAPS**:
   - Use PowerShell commands to set permissions for the `CNDclient` OU, allowing the `LAPSusers` group to read and reset passwords.

8. **Deploy LAPS on Finance-Dept VM**:
   - Create a shared folder named `LapsShare` on the AD Domain Controller and copy `LAPS.x64.exe` into it.
   - In Group Policy Management, edit the `laps5801` GPO to deploy the LAPS software from the shared folder.

9. **Configure LAPS Settings**:
   - Enable LAPS settings in the Group Policy Management Editor, including password management and expiration settings.

10. **Update Group Policy on Finance-Dept VM**:
    - Log in to the Finance-Dept VM as `Finance-Dept\Alice` and run `gpupdate /force` in Command Prompt, then restart the VM.

11. **Verify LAPS Installation**:
    - After logging back in, check that LAPS is installed via Control Panel.
    - Run `LAPS.x64.exe` to access the LAPS UI and search for the built-in administrator password for the Finance-Dept VM.

12. **Reset Configuration**:
    - To reset the configuration, move the `FINANCE-DEPT` computer back to the Computers container in Active Directory.

By following these steps, network defenders can effectively secure local administrator passwords using the Local Administrator Password Solution (LAPS), ensuring unique and complex passwords are set and managed regularly to prevent unauthorized access and lateral movement within the network.