### Exercise 3: Establishing a Virtual Private Network Connection using SoftEther VPN

**Objective:** Demonstrate how to establish a VPN connection using SoftEther VPN.

#### Overview of SoftEther VPN
- SoftEther VPN is a powerful, open-source VPN software that facilitates the creation of secure VPN tunnels.
- It uses HTTPS protocol (TCP port 443) to bypass firewalls, proxies, and NATs, making it suitable for various network environments.

#### Steps to Establish a VPN Connection

1. **Check Public IP:**
   - Open a web browser and search for "what is my IP" to note your public IP address.

2. **Launch Smoothwall Firewall VM:**
   - Log in with the username `Administrator` and password `toor`.

3. **Launch AD Domain Controller VM:**
   - Log in with `CND\Administrator` and password `Pa$$w0rd`.

4. **Install SoftEther VPN Server:**
   - Navigate to `Z:\CNDv3 Module 03 Technical Network Security\SoftEther VPN\SoftEther VPN Server`.
   - Run the installer `softether-vpnserver_vpnbridge-v4.30-9744-beta-2020.03.20-windows-x86_x64-intel`.
   - Follow the installation wizard, accepting the license agreement and retaining default settings.
   - Ensure "Start the SoftEther VPN Server Manager" is checked upon completion.

5. **Configure SoftEther VPN Server:**
   - Open SoftEther VPN Server Manager and set the Administrator password (e.g., `user@123`).
   - Select **Remote Access VPN Server** in the Easy Setup wizard and specify the Virtual Hub Name (e.g., `CND-VPN`).
   - Enable **L2TP Server Function** and disable VPN Azure service.
   - Create a new user (e.g., username `martin`, password `user@123`).

6. **Launch Finance-Dept VM:**
   - Log in as `Finance-Dept\Alice` with password `user@123`.

7. **Install SoftEther VPN Client:**
   - Navigate to `Z:\CNDv3 Module 03 Technical Network Security\SoftEther VPN\SoftEther VPN Client`.
   - Run the installer `softether-vpnclient-v4.30-9696-beta-2019.07.08-windows-x86_x64-intel.exe`.
   - Follow the installation steps, ensuring "Start the SoftEther VPN Client Manager" is checked.

8. **Create a Virtual Network Adapter:**
   - In the SoftEther VPN Client Manager, double-click **Add VPN Connection**.
   - When prompted, create a Virtual Network Adapter (name it `VPN`).

9. **Configure VPN Connection:**
   - Double-click the newly created Virtual Network Adapter.
   - Set the **Setting Name** (e.g., `Martin VPN`), enter your public IP in the **Host Name** field, and select the appropriate **Virtual Hub Name** (`CND-VPN`).
   - Enter the username (`martin`) and password (`user@123`) for authentication.

10. **Connect to VPN:**
    - Right-click on `Martin VPN` and select **Connect**.
    - Enter the username and password when prompted.
    - Wait for the connection to establish; the status should change to **Connected**.

11. **Verify Active Sessions:**
    - Switch back to the AD Domain Controller VM.
    - In the SoftEther VPN Server Manager, refresh to view active sessions.
    - Click **Manage Virtual Hub** to see connected users and manage VPN settings.

### Conclusion
By following these steps, a network defender can successfully establish a secure VPN connection using SoftEther VPN, allowing for safe remote access to organizational resources while maintaining network security.