### Summary of Steps for Implementing Name-based Mandatory Access Controls Using AppArmor

1. **Launch VMs**:
   - Start the **Smoothwall Firewall** VM and log in with the password `toor`.
   - Launch the **AD Domain Controller** VM and log in using `CND\Administrator` with the password `Pa$$w0rd`.
   - Open the **Operation Dept** VM and log in with username `Alice` and password `user@123`.

2. **Open Terminal and Gain Root Access**:
   - Press `Ctrl+Alt+T` to open the terminal.
   - Switch to root user by typing:
     ```bash
     sudo su
     ```
   - Enter the password `user@123`.

3. **Update System and Check AppArmor Status**:
   - Update the package list:
     ```bash
     apt-get update
     ```
   - Check the current status of AppArmor:
     ```bash
     apparmor_status
     ```

4. **Install AppArmor Utilities**:
   - Install AppArmor and its utilities:
     ```bash
     apt install apparmor apparmor-utils
     ```
   - Confirm installation if prompted.

5. **Create AppArmor Profile for Ping Command**:
   - Test the ping command:
     ```bash
     ping 10.10.10.1
     ```
   - Stop the ping with `Ctrl+C`.
   - Create a directory to avoid enforcement errors:
     ```bash
     mkdir -p /var/lib/snapd/apparmor/snap-confine
     ```
   - Create a basic profile for the ping command:
     ```bash
     aa-autodep ping
     ```

6. **Modify Profile to Deny Execution**:
   - Check the created profile:
     ```bash
     apparmor_status
     ```
   - Enforce the profile:
     ```bash
     aa-enforce ping
     ```
   - Edit the profile to deny execution:
     ```bash
     gedit /etc/apparmor.d/usr.bin.ping
     ```
   - Add the following line after line 6:
     ```
     # Deny execution for all users
     deny /usr/bin/ping x,
     ```
   - Save and close the file.

7. **Reload the Profile**:
   - Reload the modified profile:
     ```bash
     sudo apparmor_parser -r /etc/apparmor.d/usr.bin.ping
     ```

8. **Verify Profile Enforcement**:
   - Check the status of the profile:
     ```bash
     apparmor_status
     ```

9. **Test the Restricted Command**:
   - Reboot the system.
   - Open the terminal and switch to root user:
     ```bash
     sudo su
     ```
   - Attempt to ping again:
     ```bash
     ping 10.10.10.1
     ```
   - The command should return null, indicating it is restricted.

10. **Check AppArmor Logs**:
    - Verify the logs for AppArmor messages:
      ```bash
      sudo journalctl | grep apparmor
      ```

By following these steps, network defenders can effectively implement AppArmor to enhance security by restricting access to specific commands and resources on a Linux system.