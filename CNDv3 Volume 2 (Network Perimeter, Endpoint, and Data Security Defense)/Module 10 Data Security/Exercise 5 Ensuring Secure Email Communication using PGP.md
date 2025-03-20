### Ensuring Secure Email Communication using PGP: Summary Steps

1. **Prepare Environment**: 
   - If needed, create two new email accounts for demonstration.
   - Launch Smoothwall Firewall VM and log in with password: `toor`.
   - Launch WebServer VM and log in with username: `Administrator` and password: `admin@123`. Close the Server Manager if it appears.

2. **Set Up Folders**: 
   - Create two folders on the desktop named **PGP keys** and **Public keys**.

3. **Install Gpg4win**: 
   - Navigate to `Z:\CNDv3 Module 10 Data Security\Gpg4win` and double-click `gpg4win-4.2.0.exe`.
   - Click **Run** on the security warning, then click **OK** on the installer language window.
   - Click **Next** through the setup, selecting components as needed.

4. **Create PGP Key Pair**: 
   - After installation, run Kleopatra and select **New Key Pair**.
   - Enter the name (e.g., **CND User1**) and email address. Check **Protect the generated key with passphrase** and click **Advanced Settings**.
   - Choose **RSA** with a key size of **4,096 bits**. Ensure **Signing** and **Valid Until** options are checked, then click **OK**.
   - Enter the passphrase `Qwerty@123` and confirm it.

5. **Export Public Key**: 
   - Right-click on **CND User1** and select **Export**. Save the file as **Public** on the desktop.
   - Right-click the **Public** file and select **Edit with Notepad++** to view the PGP public key block.

6. **Backup Secret Key**: 
   - Right-click on **CND User1** and select **Backup Secret Keys**. Save it as **Private** on the desktop and enter the passphrase `Qwerty@123` to confirm.

7. **Save Public Key as Text**: 
   - Copy the PGP public key block from Notepad++ and save it as **Public Key.txt**.

8. **Import Public Key**: 
   - In Kleopatra, click **Import** and select **Public Key.txt** from the desktop.

9. **Encrypt a Message**: 
   - Open a new tab in Notepad++, type "Hello World," and copy the message.
   - In Kleopatra, go to **Tools > Clipboard > Encrypt**. Add the recipient by selecting **CND User1** and click **Next**.
   - Confirm that encryption succeeded and copy the encrypted message to the clipboard.

10. **Decrypt the Message**: 
    - In Kleopatra, go to **Tools > Clipboard > Decrypt/Verify**. Enter the passphrase `Qwerty@123`.
    - Confirm that decryption succeeded and copy the original message to the clipboard.

11. **View Decrypted Message**: 
    - Open a new tab in Notepad++ and paste to see the decrypted message.

By following these steps, you can securely send and receive emails using PGP encryption, ensuring both confidentiality and integrity of the communication. Close all opened windows in the WebServer after completing the lab.