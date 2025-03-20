### Implementing Password Policies in Linux Lab Summary

**Objective:** Set up strong password policies on an Ubuntu Linux system to enhance security against unauthorized access.

**Overview:** Strong password policies help prevent brute-force attacks by enforcing complexity and length requirements for user passwords. The Pluggable Authentication Module (PAM) is used to manage these policies.

**Lab Steps:**

1. **Setup:**
   - Ensure that the Smoothwall Firewall, AD Domain Controller, and Operation Department VMs are running.
   - Launch the Smoothwall Firewall VM and log in with the password `toor`.
   - Launch the AD Domain Controller VM and log in with the `CND\Administrator` account using the password `Pa$$w0rd`.
   - Launch the Operation Department VM and log in as user Alice with the password `user@123`.

2. **Configure System Packages:**
   - Open the terminal and run:
     ```bash
     sudo dpkg --configure -a
     ```
   - If prompted, enter the password `user@123`.
   - Switch to the root user:
     ```bash
     sudo su
     ```
   - Navigate to the Desktop:
     ```bash
     cd Desktop
     ```

3. **Fix Broken Packages:**
   - Run the following command to fix any broken packages:
     ```bash
     apt --fix-broken install
     ```

4. **Install PAM Module:**
   - Install the PAM module for password quality:
     ```bash
     apt-get -y install libpam-pwquality cracklib-runtime
     ```

5. **Configure Password Settings:**
   - Edit the common-password file:
     ```bash
     gedit /etc/pam.d/common-password
     ```
   - If prompted, enter the password `user@123`.
   - Locate the line starting with `password requisite pam_pwquality.so` and modify it to include:
     ```plaintext
     retry=3 minlength=8 ucredit=-1 dcredit=-3 ocredit=-1
     ```
   - This configuration sets:
     - Minimum password length to 8 characters.
     - At least 1 uppercase letter (`ucredit=-1`).
     - At least 3 digits (`dcredit=-3`).
     - At least 1 special character (`ocredit=-1`).

6. **Save Changes and Reboot:**
   - Save the changes and close the file.
   - Reboot the system.

7. **Test Password Policy Implementation:**
   - Log in as user Alice with the password `user@123`.
   - Open the terminal and attempt to change the password:
     ```bash
     sudo passwd
     ```
   - Enter the current password (`user@123`).
   - Attempt to set a weak password (e.g., `test123`). The system should reject it due to policy violations.

8. **Set a Valid Password:**
   - Change the password again using:
     ```bash
     sudo passwd
     ```
   - Enter the current password (`user@123`).
   - Set a new valid password (e.g., `Cnduser@123`) and confirm it. The password should be accepted.

9. **Revert Password Change (Optional):**
   - To change Alice’s password back to `user@123`, run:
     ```bash
     sudo passwd
     ```
   - Enter the current password (`Cnduser@123` or `user@123` as needed) and set the new password.

**Conclusion:** This lab demonstrates how to implement strong password policies in a Linux environment using PAM. By enforcing complexity and length requirements, network defenders can significantly enhance the security of user accounts against unauthorized access.