### **SQL Injection Attack Detection Using Wireshark**  

**Description:**  
This guide outlines the steps to perform and detect an SQL injection attack using Wireshark. The attack leverages SQL injection vulnerabilities to bypass security controls and gain unauthorized access to sensitive data.

---

## **Steps to Perform SQL Injection Attack and Detect Using Wireshark**

### **Step 1: Environment Setup**
- **Launch Smoothwall Firewall VM**  
  - Login with username: `toor`  
- **Launch AdminMachine-1 VM**  
  - Login with username: `Admin` and password: `admin@123`  
- Ensure **Cain & Abel** is running with ARP poisoning route setup.  
- Launch **Wireshark** on AdminMachine-1.  
- Select **Ethernet 2** as the interface and click **Start capturing packets**.

---

### **Step 2: Perform the SQL Injection Attack**
1. On the **Attacker Machine VM**, log in with:  
   - Username: `Bob`  
   - Password: `user@123`  
2. Open a web browser and visit:  
   ```
   www.luxurytreats.com
   ```
3. Login with credentials:  
   - **Username:** `bob`  
   - **Password:** `Passw0rd`  
4. On the homepage, click on **My Orders** and select **Order ID ORD-001**.  
5. Modify the URL in the address bar to inject SQL commands:  
   ```
   http://www.luxurytreats.com/OrderDetail.aspx?Id=ORD-001 ' or 1=1;--
   ```
6. This bypasses security controls and reveals unauthorized order details.

---

### **Step 3: Detect SQL Injection in Wireshark**
1. Switch to **AdminMachine-1 VM**.  
2. Stop packet capturing in **Wireshark**.  
3. Apply the filter:  
   ```
   http
   ```
4. Locate the HTTP GET request:  
   ```
   GET /OrderDetails...
   ```
5. Right-click the packet → Select **Follow TCP Stream**.  
6. In the new window, search for the SQL injection pattern:  
   ```
   1;--
   ```

---

### **Key Indicators in Wireshark**
✅ **HTTP GET requests** containing suspicious SQL commands like `' or 1=1;--`  
✅ Presence of unusual parameters in URLs (e.g., `Id=ORD-001 ' or 1=1;--`).  
✅ Large data dumps or unexpected query results in response packets.

---

### **Mitigation Strategies**
- **Input Validation:** Use parameterized queries and prepared statements.  
- **Web Application Firewalls (WAF):** Filter malicious requests.  
- **Least Privilege Principle:** Minimize database permissions.  
- **Security Patches:** Regularly update database management systems.  

---

### **Conclusion**
Wireshark is an effective tool for detecting SQL injection attacks by identifying suspicious HTTP GET requests and tracking injected SQL payloads. Monitoring query patterns and unexpected data responses can help network defenders mitigate these threats.

---

### **Tags:**  
`#Wireshark` `#SQLInjection` `#NetworkSecurity` `#CyberSecurity`