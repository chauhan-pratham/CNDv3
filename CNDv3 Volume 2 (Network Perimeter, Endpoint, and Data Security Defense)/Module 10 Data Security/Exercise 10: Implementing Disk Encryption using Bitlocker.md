### Summary of Steps for Implementing Disk Encryption using BitLocker

1. **Launch Smoothwall Firewall VM**: Log in with password `toor` and wait for the system to load.

2. **Launch AD Domain Controller VM**: Log in using `Pa$$w0rd`. Confirm network settings if prompted.

3. **Launch Admin Machine-1 VM**: Log in with `admin@123`.

4. **Open File Explorer**: Navigate to "This PC" and right-click on "New Volume (F:)" to access the context menu.

5. **Activate BitLocker**: Select "Turn on BitLocker" for drive F:.

6. **Set Unlock Method**: Choose "Use a password to unlock the drive" and enter `Qwerty@12345` as the password.

7. **Save Recovery Key**: Click "Save to file" and save the recovery key on the Desktop.

8. **Choose Encryption Options**:
   - Select "Encrypt entire drive" for comprehensive security.
   - Choose "New encryption mode" for fixed drives.

9. **Start Encryption**: Click "Start encrypting" and wait for the process to complete.

10. **Restart VM**: Reboot the machine to activate BitLocker.

11. **Log in Again**: Use `admin@123` to log back into Admin Machine-1.

12. **Verify Encryption**: Check that Local Disk (F:) is encrypted.

13. **Unlock Drive**: Double-click on Local Disk (F:) and enter `Qwerty@12345` to unlock.

14. **Lock Drive via Command Prompt**: Open Command Prompt as Administrator and run `manage-bde -lock f:`.

15. **Unlock with Recovery Key**: Use the saved recovery key to unlock the drive if needed.

16. **Turn Off BitLocker**: Go to Control Panel > System and Security > BitLocker Drive Encryption, and select "Turn off BitLocker" for New Volume (F:).

By following these steps, you can effectively implement BitLocker to secure sensitive data on your Windows system.