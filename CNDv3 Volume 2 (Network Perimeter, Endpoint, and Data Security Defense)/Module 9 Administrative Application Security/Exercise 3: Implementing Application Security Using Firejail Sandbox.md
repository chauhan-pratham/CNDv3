1. **Launch VMs**: Start the Smoothwall Firewall VM and log in with the password `toor`. Then, launch the AD Domain Controller VM and log in as `CND\Administrator` with the password `Pa$$w0rd`. Finally, access the Operation Dept VM and log in as `alice` (password: `user@123`).

2. **Install Firejail**: Open a terminal in the Home Folder and run the command:
   ```bash
   sudo apt install firejail
   ```
   Enter the password `user@123` when prompted and confirm any additional disk space usage.

3. **Install Firetool**: Create a directory for Firetool:
   ```bash
   sudo mkdir Firetool
   ```
   Change to the Firetool directory and install Firetool:
   ```bash
   cd Firetool
   sudo apt-get install -y firetools
   ```
   Confirm any additional disk space usage.

4. **Run an Application in Firejail**: Launch LibreOffice in the Firejail sandbox:
   ```bash
   firejail libreoffice
   ```
   This opens LibreOffice, allowing you to create and save documents in the `/home/Document` directory.

5. **Open Firetool GUI**: Run Firetool to manage sandboxed applications:
   ```bash
   firetools
   ```
   Use the GUI to open LibreOffice and minimize it.

6. **Create a Custom Profile**: Change to the home directory and create a configuration directory:
   ```bash
   cd ~
   mkdir -p .config/firejail
   ```
   Copy the existing LibreOffice profile:
   ```bash
   cd .config/firejail
   cp /etc/firejail/libreoffice.profile libreoffice.profile
   ```
   Edit the profile to restrict access to the Documents folder:
   ```bash
   sudo gedit libreoffice.profile
   ```
   Add the line:
   ```plaintext
   blacklist ${HOME}/Documents
   ```
   Save and close the editor.

7. **Test the Custom Profile**: Run LibreOffice again in Firejail:
   ```bash
   firejail libreoffice
   ```
   Attempt to open a document from the Documents folder; an error message should indicate permission is denied.

8. **Close Applications**: Use `CTRL+C` in the terminal to close Firejail and exit.

By following these steps, network defenders can effectively use Firejail to sandbox applications, enhancing security by restricting their access to system resources.