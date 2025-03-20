### Administrative Network Security Lab: Monitoring Activities on a Remote User System

**Objective:** Demonstrate how to monitor user activities remotely using Spytech SpyAgent.

#### Lab Steps:

1. **Launch Smoothwall Firewall VM:**
   - Enter password: `toor`.
   - Navigate to Done and hit Enter.

2. **Launch AD Domain Controller VM:**
   - Click Ctrl+Alt+Delete to log in.
   - Use username: `CND\Administrator`, password: `Pa$$w0rd`.

3. **Launch Admin Machine-1 VM:**
   - Log in with username: `Admin`, password: `admin@123`.

4. **Establish Remote Desktop Connection:**
   - Search for Remote Desktop Connection.
   - Enter AD Domain Controller IP: `20.20.10.19`, connect as Administrator with password: `Pa$$w0rd`.

5. **Install Spytech SpyAgent:**
   - Navigate to `Z:\CNDv3 Module 02 Administrative Network Security\Spyagent`.
   - Extract and run `Setup (password=spytech).exe`.
   - Disable antivirus protection if prompted.
   - Follow installation prompts, accepting terms and default settings.

6. **Configure SpyAgent:**
   - Set a new password: `qwerty@123`.
   - Choose Complete + Stealth Configuration.
   - Enable Load on Windows Startup.

7. **Start Monitoring:**
   - Click Start Monitoring and enter access password: `qwerty@123`.

8. **Perform User Activities:**
   - Log in to AD Domain Controller and perform random activities (e.g., browsing).

9. **Check Monitoring Logs:**
   - Reconnect to AD Domain Controller from Admin Machine-1.
   - Stop SpyAgent Stealth Mode and enter access password.
   - View keystrokes and website activity (e.g., Facebook) through SpyAgent GUI.

10. **Review User Activities:**
    - Access logs for keystrokes, screenshots, and program usage.

This concise guide captures the essential steps for monitoring user activities using Spytech SpyAgent while ensuring clarity and brevity.