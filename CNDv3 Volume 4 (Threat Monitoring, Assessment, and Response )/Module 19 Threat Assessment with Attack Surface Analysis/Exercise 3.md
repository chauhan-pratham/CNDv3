## Exercise 3: System Attack Surface Analysis using Attack Surface Detector in Burp Suite

### Lab Objectives
- Install Attack Surface Detector in Burp Suite
- Identify hidden parameters and endpoints through source code analysis
- Use Attack Surface Detector's findings for security testing

### Steps to Follow
1. **Launch Smoothwall Firewall**
   - Click `Smoothwall Firewall` and log in using `toor` as the password.
   - Press `Tab` twice, select `Done`, and press `Enter`.

2. **Launch Admin Machine-1**
   - Click `Admin Machine-1 -Mod 19 (COPY)` and log in with `admin@123`.

3. **Install Burp Suite**
   - Navigate to `E:\CND-Tools\CNDv3 Module 19 Threat Assessment with Attack Surface Analysis\Burpsuit`.
   - Run the Burp Suite installer, clicking `Next` through each step.

4. **Launch Burp Suite**
   - Open Burp Suite via the Windows Search bar.
   - Accept the terms, click `Next`, and select `Start Burp`.

5. **Install Attack Surface Detector**
   - Go to the `Extension` tab and select `BApp Store`.
   - Search for `Attack Surface Detector` and click `Install`.

6. **Import Source Code**
   - Copy `LuxuryTreats.zip` from `Attack Surface Detector` folder to Desktop.
   - In Burp Suite, click `Import Endpoints from Source`.
   - Select `LuxuryTreats.zip` from the Desktop and click `OK`.

7. **Configure Target URL**
   - Set `Host` as `www.luxurytreats.com` and `Port` as `80`, then click `Submit`.

8. **View Results**
   - Review the endpoints list in the `Attack Surface Detector` tab.
   - Go to the `Target` tab to explore the Site Map.

9. **Identify Vulnerabilities**
   - Click on the `Issue Definitions` tab to review detected vulnerabilities and suggested fixes (e.g., XPath Injection, ASP.NET Debugging issues, SQL Injection).

10. **Configure Scope**
    - In `Scope Settings`, define URLs to be tested.

11. **Test Endpoints**
    - In the `Site Map`, right-click `OrderDetail.aspx` and select `Send to Intruder`.

12. **Perform Intruder Attack**
    - Navigate to the `Intruder` tab for further testing actions.

### Conclusion
Using Attack Surface Detector in Burp Suite helps a network defender perform comprehensive security testing by mapping and analyzing an application's attack surface to identify and exploit vulnerabilities.

