### Summary of Steps for Integrity File Checking on Linux Using File Checksum Tool

1. **Launch Smoothwall Firewall VM**: Log in with the password `toor`.
2. **Wait for Smoothwall to Load**: Allow the Smoothwall login screen to appear.
3. **Launch Operation Dept VM**: Log in as `Alice` with password `user@123`.
4. **Open Terminal**: Access the terminal from the left pane.
5. **Switch to Root User**: Type `sudo su` and enter the password `user@123`.
6. **Download ISO File**: Open Firefox and navigate to [www.kali.org/downloads/](http://www.kali.org/downloads/). Click on Installer Images and download the NetInstaller ISO file. Copy the checksum provided for the file.
7. **Locate SHA Commands**: In the terminal, type `sha` and press the Tab key twice to view available SHA commands.
8. **Verify File Integrity with SHA-256**: Run the command:
   ```
   sha256sum Downloads/kali-linux-2023.3-installer-netinst-amd64.iso | grep <copied_checksum>
   ```
   Replace `<copied_checksum>` with the checksum you copied earlier. If the output shows the checksum in red, the file integrity is confirmed.
9. **Test Integrity Check**: Change the last digit of the checksum and run the command again. No output should be produced, indicating a mismatch.
10. **Create a Test File**: In the terminal, type:
    ```
    printf 'Hello World' > test.txt
    ```
11. **Generate SHA-512 Hash**: Create a SHA-512 hash of the test file and save it:
    ```
    sha512sum test.txt > test.sha512
    ```
12. **Verify SHA-512 Hash**: Run the following commands to verify the hash:
    ```
    sha512sum -c test.sha512
    ```
13. **Conclusion**: This process demonstrates how to check file integrity using SHA-256 and SHA-512 checksums, ensuring data authenticity and security. Note that MD5 is not recommended for cryptographic purposes due to its vulnerabilities.

By following these steps, network defenders can effectively verify the integrity of files and protect against unauthorized changes or corruption.