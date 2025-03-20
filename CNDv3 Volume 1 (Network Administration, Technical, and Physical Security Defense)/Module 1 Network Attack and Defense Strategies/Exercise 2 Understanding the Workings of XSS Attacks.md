### XSS Attack Lab Summary

**Objective:** Understand Cross-Site Scripting (XSS) attacks and how they can compromise web applications.

**Overview:** XSS attacks exploit vulnerabilities in dynamically generated web pages, allowing attackers to inject malicious scripts that execute in the browsers of users who visit the affected page.

**Lab Steps:**

1. **Setup:**
   - Start the PfSense Firewall VM.
   - Launch the Web Server VM and log in with `admin@123`.
   - Launch the Attacker VM and log in as user Bob with password `user@123`.

2. **Access the Target Website:**
   - Open Firefox and navigate to `http://www.luxurytreats.com`.
   - Ensure the SQL Server service is running on the web server.

3. **Initiate the XSS Attack:**
   - Click on "Contact" in the top menu to access the contact page.
   - In the Email textbox, enter a valid email address.
   - In the Comment textbox, inject the following JavaScript code: 
     ```html
     <script> alert("You are hacked"); </script>
     ```
   - Click "Save Comment."

4. **Observe the Result:**
   - A pop-up message saying "You are hacked" will appear, indicating that the XSS attack was successful.

**Conclusion:** This lab demonstrates how an attacker can exploit XSS vulnerabilities to inject malicious scripts into a web page, potentially leading to session hijacking, phishing, and other malicious activities. Understanding these attacks is crucial for network defenders to protect web applications from such threats.