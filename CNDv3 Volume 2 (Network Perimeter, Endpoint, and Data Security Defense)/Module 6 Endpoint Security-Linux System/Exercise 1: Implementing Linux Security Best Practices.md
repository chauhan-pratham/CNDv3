### Summary of Steps for Implementing Linux Security Best Practices

1. **Launch VMs**:
   - Start the **Smoothwall Firewall** VM and log in with the password `toor`.
   - Launch the **AD Domain Controller** VM and log in using `CND\Administrator` with the password `Pa$$w0rd`.
   - Open the **Operation Dept** VM and log in with username `alice` and password `user@123`.

2. **Disable Unnecessary Services**:
   - Open a terminal and run `ps ax` to view running services.
   - Disable the Apache2 service by executing:
     ```bash
     sudo update-rc.d -f apache2 remove
     ```
   - Enter the password `user@123` when prompted.

3. **Remove Unnecessary Software**:
   - Switch to root user with:
     ```bash
     sudo su
     ```
   - List installed packages using:
     ```bash
     apt list --installed
     ```
   - Identify and remove unnecessary packages (e.g., `avahi-daemon`) with:
     ```bash
     apt remove avahi-daemon
     ```
   - Confirm removal by pressing `Y` when prompted.
   - Clean up unused dependencies with:
     ```bash
     apt-get autoremove
     ```

4. **Create User Group for SSH Access**:
   - List existing users with:
     ```bash
     cat /etc/passwd
     ```
   - Create a new user group:
     ```bash
     addgroup cndusers
     ```
   - Add user `smith` to the new group:
     ```bash
     gpasswd -a smith cndusers
     ```

5. **Install OpenSSH Server**:
   - Install OpenSSH server with:
     ```bash
     apt install openssh-server
     ```
   - Confirm installation by pressing `Y`.

6. **Restrict SSH Remote Login**:
   - Open the SSH configuration file:
     ```bash
     sudo gedit /etc/ssh/sshd_config
     ```
   - Add the following lines to restrict access:
     ```
     DenyUsers smith
     DenyGroups cndusers
     ```
   - Restart the SSH service:
     ```bash
     service ssh restart
     ```

7. **Test SSH Access**:
   - From the **AD Domain Controller** VM, install PuTTY and open it.
   - Attempt to log in with user `smith` and password `user@123`. The login should be denied.

By following these steps, network defenders can effectively implement security best practices on Linux systems, reducing vulnerabilities and enhancing overall security.