### Summary of Steps for Preventing Application-Level Attacks Using Microsoft URLScan Web Application Firewall

1. **Launch Attacker Machine**: Start the Attacker Machine VM and log in as `Bob` (password: `user@123`). Open Mozilla Firefox and navigate to `http://www.luxurytreats.com`.

2. **Perform XSS Attack**: Click on the Contact menu, enter the following in the comment box, and click Save Comment:
   - **Email**: `test@gmail.com`
   - **Comment**: `<script>alert("attack");</script>`
   An alert message should pop up confirming the attack.

3. **Launch Web Server VM**: Start the Web Server VM and log in as `Administrator` (password: `admin@123`). Navigate to the `Z:\CNDv3 Module 09 Administrative Application Security\Microsoft UrlScan` folder and run `urlscan_v31_x64.msi` to install URLScan.

4. **Complete Installation**: Accept the license agreement and finish the installation. URLScan will install necessary files in `%windir%\system32\inetsrv\UrlScan`.

5. **Copy URLScan Folder**: Open File Explorer, navigate to `%windir%\system32\inetsrv`, and copy the `urlscan` folder to `C:\inetpub\wwwroot\LuxuryTreats`.

6. **Configure URLScan for SQL Injection Protection**: Open `C:\inetpub\wwwroot\LuxuryTreats\urlscan\UrlScan.ini` in Notepad++ and modify it:
   - Replace Line 175 with `RuleList="SQL Injection"`.
   - Add the following rules:
     ```ini
     [SQL Injection]
     AppliesTo=.asp,.aspx
     DenyDataSection=SQL Injection Strings
     ScanUrl=0
     ScanAllRaw=0
     ScanQueryString=1
     ScanHeaders=0

     [SQL Injection Strings]
     --
     ;%3b ; a semicolon
     /*
     @ ; also catches @@
     char ; also catches nchar and varchar
     alter
     begin
     cast
     convert
     create
     cursor
     declare
     delete
     drop
     end
     exec ; also catches execute
     fetch
     insert
     kill
     open
     select
     sys ; also catches sysobjects and syscolumns
     table
     update
     ```
   - Save and close the file.

7. **Configure IIS**: Open Windows Administrative Tools, launch Internet Information Services (IIS) Manager, and navigate to the LuxuryTreats website. Under the IIS section, double-click on ISAPI Filters, select Urlscan 3.1, and click Edit. Browse to `C:\inetpub\wwwroot\LuxuryTreats\urlscan` and select `urlscan.dll`.

8. **Restart IIS**: Select the Web Server from the Connections pane and click Restart.

9. **Test URLScan Protection**: Switch back to the Attacker Machine VM, log in as `Bob`, and repeat the XSS attack steps. This time, instead of the alert, you should see an HTTP Error 404.0, indicating that URLScan has successfully blocked the malicious request.

By following these steps, network defenders can effectively use Microsoft URLScan to prevent application-level attacks such as SQL injection and XSS, enhancing the security of web applications.