1. **Launch VMs**: Start the Smoothwall Firewall VM and log in with the password `toor`. Then, launch the Admin Machine-1 VM and log in as `Admin` (password: `admin@123`).

2. **Download Sandboxie**: Open Google Chrome and navigate to [Sandboxie Downloads](https://sandboxie-plus.com/downloads/). Download `Sandboxie-Classic-x64-v5.69.6.exe`.

3. **Install Sandboxie**: 
   - Disable any antivirus protection temporarily.
   - Run the downloaded `.exe` file. If prompted by User Account Control, click `Yes`.
   - Follow the installation prompts, agreeing to the license and completing the installation.

4. **Open Sandboxie**: After installation, Sandboxie will launch automatically. If a compatibility popup appears, click `OK`.

5. **Sandbox a Browser**: Drag the Firefox browser icon from the desktop into the Sandboxie program (Sandbox DefaultBox) and click `OK`. This will run Firefox in a sandboxed environment.

6. **Download Malware Sample**: In the sandboxed Firefox, navigate to the malware sample link: [Bezilom.exe](https://github.com/Da2dalus/The-MALWARE-Repo/blob/master/Worm/Bezilom.exe). Ensure real-time protection is turned off before downloading. Allow the download if prompted by Firefox.

7. **Access Downloaded Malware**: 
   - Open Sandboxie and right-click on `Sandbox DefaultBox`.
   - Select `Run Sandboxed` and then `Run Windows Explorer`.
   - Navigate to the Downloads folder within this sandboxed Windows Explorer to find the downloaded malware file.

8. **Terminate Malicious File**: Right-click on `Sandbox DefaultBox` and select `Terminate Programs`. Confirm the termination process. This action will clear all running programs within the sandbox.

9. **Close Sandboxie**: After terminating the programs, close the Sandboxie application.

By following these steps, network defenders can safely examine potentially suspicious files in an isolated environment using Sandboxie, effectively protecting the main computer system from potential threats.