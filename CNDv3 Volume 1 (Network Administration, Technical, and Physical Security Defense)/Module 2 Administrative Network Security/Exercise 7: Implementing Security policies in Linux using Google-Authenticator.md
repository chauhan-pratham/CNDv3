### Administrative Network Security Lab: Implementing Security Policies in Linux using Google Authenticator

**Objective:** Secure a Linux system with two-factor authentication (2FA) using Google Authenticator to prevent unauthorized access.

#### Lab Steps:

1. **Launch Smoothwall Firewall VM:**
   - Enter password: `toor` and press Enter.
   - Navigate to Done and press Enter.

2. **Launch Operation Department VM:**
   - Log in with username: `alice`, password: `user@123`.

3. **Adjust Power Settings:**
   - Set the screen blank time to Never in Power Settings.

4. **Open Terminal:**
   - Right-click on the desktop and select "Open in Terminal."

5. **Gain Root Access:**
   - Type `sudo su` and press Enter.
   - Enter password: `user@123` when prompted.

6. **Update the System:**
   - Run the following commands:
     ```bash
     sudo apt update
     sudo apt upgrade -y
     ```

7. **Install Google Authenticator:**
   - Install the package:
     ```bash
     sudo apt-get install libpam-google-authenticator
     ```
   - Press `Y` if prompted to continue.

8. **Configure PAM for Google Authenticator:**
   - Open the PAM configuration file:
     ```bash
     sudo nano /etc/pam.d/common-auth
     ```
   - Add the line:
     ```
     auth required pam_google_authenticator.so
     ```
   - Save the file (Ctrl + O, then Enter) and exit (Ctrl + X).

9. **Generate Time-Based Tokens:**
   - Run:
     ```bash
     google-authenticator
     ```
   - Answer `y` to enable time-based tokens and note the secret key and QR code.

10. **Set Up Google Authenticator on Android Device:**
    - Launch the Android Device VM and open the Play Store.
    - Search for and install **Google Authenticator**.
    - Open the app and select "Get started."
    - Choose "Add a code" and then "Enter a setup key."
    - Enter a name (e.g., "Alice") and the secret key from the previous step. Select "Time-based" and click "Add."

11. **Verify Authentication:**
    - Copy the one-time verification code from Google Authenticator.
    - Return to the Operation Department VM and enter the verification code to verify authentication.
    - Note the scratch codes and secret key for recovery.

12. **Update Google Authenticator File:**
    - Press `Y` to update the `~/.google_authenticator` file and follow the prompts:
      - Press `Y` for the next prompt.
      - Press `N` for the next prompt.
      - Press `Y` for the last prompt.

13. **Lock and Test Login:**
    - Close the terminal and lock the screen.
    - Attempt to log in; it will prompt for a verification code.
    - Open Google Authenticator on the Android Device VM and copy the verification code.
    - Enter the verification code on the Operation Department VM, followed by the password `user@123`.

14. **Successful Login:**
    - If the verification code and password are correct, the machine will unlock, confirming that two-factor authentication is enabled.

By following these steps, you have successfully implemented Google Authenticator for two-factor authentication on a Linux system, enhancing its security against unauthorized access.