### Encrypting Data in Transit Using SSL: Summary Steps

1. **Launch Smoothwall Firewall VM**: 
   - If idle, press the spacebar to activate.
   - Login with password: `toor` and navigate to the Done button.

2. **Launch AD Domain Controller VM**: 
   - Click Ctrl+Alt+Delete to login with username: `Administrator` and password: `Pa$$w0rd`.
   - Close the Server Manager if it appears.

3. **Start WampServer**: 
   - Double-click the WampServer icon on the desktop or find it in Recently added.
   - Ensure the WampServer icon turns green; if not, restart the VM and try again.

4. **Configure SSL**: 
   - Open File Explorer, right-click This PC, and select Properties.
   - Go to Advanced system settings > Environment Variables. Create a new user variable:
     - Variable name: `openssl_conf`
     - Variable value: `C:\wamp64\bin\apache\apache2.4.58\conf\openssl.cnf`
   - Click OK to save.

5. **Edit Apache Configuration**: 
   - Navigate to `C:\wamp64\bin\apache\apache2.4.58\bin` and open `php` with Notepad++.
   - Uncomment line 953 by removing the ";" and save the file.
   - Restart all WampServer services.

6. **Generate SSL Certificates**: 
   - Open Command Prompt as Administrator and navigate to `C:\wamp64\bin\apache\apache2.4.58\bin`.
   - Set the environment variable: `set openssl_conf=C:\wamp64\bin\apache\apache2.4.58\conf\openssl.cnf`.
   - Generate a private key: `openssl genrsa -des3 -out server.key 1024` (use password `admin@123`).
   - Remove the passphrase: `openssl rsa -in server.key -out server.pem`.
   - Create a certificate signing request: `openssl req -new -key server.key -out server.csr`.
   - Generate the SSL certificate: `openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt`.

7. **Organize SSL Files**: 
   - Copy the generated key files to `C:\wamp64\bin\apache\apache2.4.58\conf\ssl`.

8. **Enable SSL Module**: 
   - Click on the WampServer icon, select Apache -> Apache modules -> `ssl_module`.

9. **Configure httpd-ssl.conf**: 
   - Navigate to `C:\wamp64\bin\apache\apache2.4.58\conf\extra` and open `httpd-ssl.conf` with Notepad++.
   - Ensure Apache listens on port 443 and update paths for DocumentRoot, ServerName, ErrorLog, and TransferLog.
   - Set paths for `SSLCertificateFile` and `SSLCertificateKeyFile` to the respective SSL files.

10. **Finalize Configuration**: 
    - Comment line 593 in `httpd.conf` and save.
    - Test configuration with `httpd -t` in Command Prompt; ensure it returns "Syntax OK".

11. **Restart WampServer**: 
    - Restart all services and wait for the icon to turn green.

12. **Test SSL Connection**: 
    - Open a web browser and navigate to `https://20.20.10.19/cnd`. If prompted about security, click "Continue to site".
    - Confirm access to the CND WordPress website.

By following these steps, you will successfully implement SSL to encrypt data in transit, ensuring secure communication over the web.