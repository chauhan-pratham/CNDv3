1. **Launch VMs**: Start the Smoothwall Firewall VM and log in with the password `toor`. Then, launch the AD Domain Controller VM and log in as `CND\Administrator` with the password `Pa$$w0rd`.

2. **Join Domain**: Access the Finance-Dept VM, log in as `FINANCE-DEPT\Alice` (password: `user@123`), and join the domain `cnd.com` through System Properties.

3. **Copy Folders**: Copy the `Restricted Programs` and `UnRestricted Programs` folders from `Z:\CNDv3 Module 09 Administrative Application Security` to the `C:` drive.

4. **Create GPO**: On the AD Domain Controller, open Server Manager, navigate to Group Policy Management, and create a new GPO named `SRP app whitelisting`.

5. **Configure Application Identity**: Edit the GPO, navigate to `Computer Configuration -> Policies -> Windows Settings -> Security Settings -> System Services`, and set the Application Identity service to Automatic.

6. **Set Up SRP**: Right-click on `Software Restriction Policies`, create new policies, and add:
   - **Path Rule**: `C:\UnRestricted Programs` as Unrestricted.
   - **Path Rule**: `C:\Restricted Programs` as Disallowed.

7. **Link GPO**: Link the `SRP app whitelisting` GPO to the `cnd.com` domain and run `gpupdate /force` on both the AD Domain Controller and Finance-Dept VM to apply the policies.

8. **Test SRP**: Restart both VMs. Attempt to run `HelloWorld.exe` from `C:\Restricted Programs` (should be blocked) and then from `C:\UnRestricted Programs` (should execute successfully).

By following these steps, network defenders can effectively implement application whitelisting using SRP to control application execution on client machines.