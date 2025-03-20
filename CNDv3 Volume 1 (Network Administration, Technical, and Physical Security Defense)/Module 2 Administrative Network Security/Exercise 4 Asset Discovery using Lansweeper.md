### Administrative Network Security Lab: Asset Discovery using Lansweeper

**Objective:** Demonstrate the management of devices on a network and identify vulnerabilities using Lansweeper.

#### Lab Steps:

1. **Launch Smoothwall Firewall VM:**
   - Enter password: `toor`.
   - Navigate to Done and press Enter.

2. **Launch AD Domain Controller VM:**
   - Click Ctrl+Alt+Delete to log in.
   - Use username: `CND\Administrator`, password: `Pa$$w0rd`.

3. **Access Lansweeper:**
   - Open Google Chrome and go to `Lansweeper.com`.
   - Sign in or register a new account with your email and password.

4. **Set Up Lansweeper:**
   - Name your site and click CREATE.
   - Download the Lansweeper Scanner and copy the linking code.

5. **Install Lansweeper:**
   - Run `LansweeperSetup`.
   - Accept terms and select Easy Install.
   - Click Finish after installation.

6. **Configure Cloud Management:**
   - Open Microsoft Edge and select Cloud management.
   - Paste the linking code and click Next.
   - Confirm linking to Lansweeper Cloud and finish setup.

7. **Start Scanning:**
   - Log in with your credentials.
   - Wait for the scanning process to complete.

8. **Access Dashboard:**
   - View the Dashboard for an overview of assets, inventory health, security, and software.

9. **View Assets:**
   - Click on Assets to see Total assets, New Assets, and scan issues.
   - Select Total assets to view all devices on the network.

10. **Identify Vulnerabilities:**
    - Look for assets with hazard signs indicating vulnerabilities (e.g., ADMIN-MACHINE-1, DESKTOP-81C8T2S).
    - Click on an asset to view its properties and scan issues.

11. **Review Scan Issues:**
    - Check the Scan issues tab for details on vulnerabilities and their types.

12. **Explore Software:**
    - Navigate to the Software tab to view installed software across the network.

13. **Monitor New Devices:**
    - Return to the Dashboard to check for new devices added in the past week.

14. **Check Antivirus Status:**
    - Click on Workstations with antivirus disabled to identify systems without antivirus protection.

15. **General Overview:**
    - Review the Most Common Asset Types among users.

By following these steps, network defenders can effectively manage assets and mitigate vulnerabilities within the network using Lansweeper.