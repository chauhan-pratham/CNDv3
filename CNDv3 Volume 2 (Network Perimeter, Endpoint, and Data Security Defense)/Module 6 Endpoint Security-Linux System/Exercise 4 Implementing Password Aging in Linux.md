### Summary of Steps for Implementing Password Aging in Linux

1. **Launch Smoothwall Firewall VM**: Log in with the password `toor`.
2. **Wait for Smoothwall to Load**: Allow the Smoothwall login screen to appear.
3. **Launch Operation Dept VM**: Log in as `alice` with password `user@123`.
4. **Open Terminal**: Right-click on the desktop and select "Open in Terminal."
5. **Switch to Root User**: Type `sudo su` and enter the password `user@123`.
6. **Update System**: Run `sudo apt update` and then `sudo apt upgrade`. Confirm with `Y` if prompted.
7. **Check User Details**: Execute `id alice` to view basic user information.
8. **Check Default Password Settings**: Run `grep alice /etc/shadow` to view Alice's password settings.
9. **Configure Password Aging**: Type `chage -M 90 -W 10 alice` to set the maximum password age to 90 days and warning period to 10 days.
10. **Verify Configuration**: Run `grep alice /etc/shadow` again to confirm the changes.
11. **Edit Default Password Settings**: Open the configuration file with `nano /etc/login.defs`.
12. **Set Default Password Aging Policies**: Modify the following settings:
    - `PASS_MAX_DAYS 90`
    - `PASS_MIN_DAYS 10`
    - `PASS_WARN_AGE 10`
13. **Save and Exit**: Press `Ctrl+O` to save and `Ctrl+X` to exit the editor.
14. **Add New User**: Type `useradd john` to create a new user.
15. **Verify New User Settings**: Run `grep john /etc/shadow` to check the password aging policy for the new user.
16. **Exit Terminal**: Type `exit` to close the terminal.

### Conclusion
Implementing password aging enhances security by enforcing regular password changes, making it more difficult for attackers to exploit compromised credentials. After completing these steps, it is recommended to end the lab session and relaunch for further exercises.