### Summary of Steps for Encrypting Data at Rest Using VeraCrypt

1. **Launch VMs**: Start the Smoothwall Firewall VM and log in with the password `toor`. Then, launch the AD Domain Controller VM and log in as `CND\Administrator` (password: `Pa$$w0rd`). Close the server manager dashboard if it appears.

2. **Access Finance-Dept VM**: Launch the Finance-Dept VM and log in as `Finance-dept\Alice` (password: `user@123`).

3. **Download and Install VeraCrypt**:
   - Navigate to `Z:\CNDv3 Module 10 Data Security\Veracrypt` and double-click `VeraCrypt Setup 1.25.9`.
   - If prompted, click `Run` for security warnings and User Account Control.
   - Follow the installation wizard, accepting the license terms and keeping default settings until installation is complete. Click `Finish` and close any pop-ups.

4. **Create a VeraCrypt Volume**:
   - Launch VeraCrypt from the desktop.
   - Click `Create Volume`, select `Create an encrypted file container`, and click `Next`.
   - Choose `Standard VeraCrypt volume` and click `Next`.
   - Click `Select File…`, navigate to `Documents`, name the file `MyVolume`, and click `Save`.
   - Click `Next`, select `AES` for the Encryption Algorithm and `SHA-512` for the Hash Algorithm, then click `Next`.
   - Specify the volume size as `2 MB` and click `Next`.
   - Enter a strong password (e.g., `qwerty@123`), confirm it, and click `Next`.
   - Click `Yes` on the warning pop-up, set the Filesystem to `FAT`, and move the mouse randomly for at least 30 seconds before clicking `Format`.

5. **Mount the VeraCrypt Volume**:
   - After the volume is created, click `OK` and then `Exit`.
   - In VeraCrypt, click `Select File…`, navigate to `Documents`, and select `MyVolume`.
   - Choose a free drive letter (e.g., `B:`) and click `Mount`.
   - Enter the password (`qwerty@123`) and click `OK`.

6. **Use the Encrypted Volume**:
   - Open File Explorer, and you will see the mounted virtual disk (B:).
   - Create a text file named `Test`, enter some text, and save it on the desktop.
   - Copy the `Test` file and paste it into the B: drive.

7. **Dismount the Volume**:
   - In VeraCrypt, click `Dismount` and then `Exit`.
   - The B: drive will no longer be accessible, ensuring that the data is securely encrypted.

By following these steps, administrators can effectively use VeraCrypt to encrypt data at rest, safeguarding sensitive information from unauthorized access.