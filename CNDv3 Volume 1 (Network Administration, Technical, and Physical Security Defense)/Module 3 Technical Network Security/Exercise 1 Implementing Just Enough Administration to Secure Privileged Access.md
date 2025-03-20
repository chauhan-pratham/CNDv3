### Exercise 1: Implementing Just Enough Administration (JEA) for Secure Privileged Access

**Objective:** Demonstrate how to create JEA session files to restrict non-admin users from executing selected PowerShell cmdlets with limited Active Directory (AD) access.

#### Overview of JEA
- JEA is a PowerShell feature that implements Role-Based Access Control (RBAC) to allow non-admin users to run specific commands while logging their activities.
- Benefits include reducing the number of administrators, creating secure endpoints, restricting user activities, and providing actionable logging.

#### Steps to Implement JEA

1. **Launch Virtual Machines:**
   - Start the Smoothwall Firewall VM and log in with the password `toor`.
   - Start the AD Domain Controller VM and log in as `CND\Administrator` with the password `Pa$$w0rd`.
   - Start the Finance-Dept VM and log in as user `martin` with the password `user@123`.

2. **Join Finance-Dept VM to AD Domain:**
   - Open System Properties and change the computer name to join the domain `cnd.com`.
   - Restart the VM to apply changes.

3. **Establish Remote PowerShell Session:**
   - Log in to the Finance-Dept VM as `martin`.
   - Open PowerShell and run:
     ```powershell
     Enter-PSSession -ComputerName DomainControll -Credential cnd\martin
     ```

4. **Configure JEA on AD Domain Controller:**
   - Log in to the AD Domain Controller VM as `Administrator`.
   - Open Windows PowerShell ISE in administrative mode.
   - Create necessary directories and files for JEA:
     ```powershell
     New-Item -Path CNDUserAccess -ItemType Directory
     New-Item -Path .\CNDUserAccess\cnduseraccess.psm1
     New-ModuleManifest -Path .\CNDUserAccess\cnduseraccess.psd1 -RootModule cnduseraccess.psm1
     New-Item -Path .\CNDUserAccess\RoleCapabilities -ItemType Directory
     New-PSRoleCapabilityFile -Path .\CNDUserAccess\RoleCapabilities\cnduseraccessJEARole.psrc
     New-PSSessionConfigurationFile -SessionType RestrictedRemoteServer -Path .\CNDEndpoint.pssc
     ```

5. **Edit Role Capabilities File:**
   - Open `cnduseraccessJEARole.psrc` and set:
     ```powershell
     VisibleCmdlets = 'Get-Service'
     ```

6. **Edit Session Configuration File:**
   - Open `CNDEndpoint.pssc` and add:
     ```powershell
     RoleDefinitions = @{ 'cnd.com\martin' = @{ RoleCapabilities = 'cnduseraccessJEARole' }; }
     ```

7. **Test and Register the Endpoint:**
   - Test the configuration:
     ```powershell
     Test-PSSessionConfigurationFile -Path .\CNDEndpoint.pssc
     ```
   - Set up the endpoint:
     ```powershell
     $session = New-PSSession DomainControll
     Copy-Item -Path CNDUserAccess -Destination 'C:\Program Files\WindowsPowerShell\Modules' -Recurse -ToSession $session -Force
     Copy-Item -Path .\CNDEndpoint.pssc -Destination c:\ -ToSession $session -Force
     Invoke-Command -Session $session -ScriptBlock {Register-PSSessionConfiguration -Path c:\CNDEndpoint.pssc -Name 'CNDUserAccess' -Force}
     ```

8. **Connect to the JEA Endpoint:**
   - From the Finance-Dept VM, run:
     ```powershell
     Enter-PSSession -ComputerName DomainControll -ConfigurationName CNDUserAccess -Credential cnd\martin
     ```
   - Verify available commands with:
     ```powershell
     Get-Command
     ```

9. **Test Command Execution:**
   - Run `Get-Service -Name MSDTC` to check the service status.
   - Attempt to run `Stop-Service -Name MSDTC` to confirm restricted access.

### Conclusion
By implementing JEA, network defenders can effectively control user access and prevent unauthorized changes on the server while allowing necessary administrative tasks.