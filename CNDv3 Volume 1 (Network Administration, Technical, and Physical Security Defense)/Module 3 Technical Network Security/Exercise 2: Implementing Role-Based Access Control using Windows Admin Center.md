### Exercise 2: Implementing Role-Based Access Control (RBAC) using Windows Admin Center (WAC)

**Objective:** Demonstrate how to install Windows Admin Center (WAC) and configure RBAC to restrict user activities.

#### Overview of Windows Admin Center (WAC)
- WAC is a web-based tool for managing servers and clients, providing features like device management, event management, file management, and more.
- RBAC in WAC allows limited access to users based on predefined roles, ensuring that users can only perform specific tasks.

#### Steps to Implement WAC and Configure RBAC

1. **Launch Virtual Machines:**
   - Start the **WebServer VM** and log in with `Administrator` and password `admin@123`.
   - Start the **AdminMachine-1 VM** and log in with `Admin` and password `admin@123`.

2. **Install Windows Admin Center:**
   - Navigate to `E:\CND-Tools\CNDv3 Module 03 Technical Network Security\Windows Admin Center` and run `WindowsAdminCenter2211.msi`.
   - Accept the terms and proceed through the installation wizard, leaving default settings.
   - Uncheck the "Automatically update options" and complete the installation.
   - Open WAC and select **Microsoft Edge** as the browser.

3. **Add WebServer to WAC:**
   - In WAC, click the **+Add** button and select **Add under Servers**.
   - Enter `Webserver` as the server name and provide credentials (`Administrator` and `admin@123`).
   - Connect to the WebServer, which is now listed under **All Connections**.

4. **Create User for RBAC:**
   - In the WebServer VM, navigate to **Local Users and Groups** in the RBAC tab.
   - Click **New User** and create a user named `John Dawason` with username `john` and password `user@123`.

5. **Configure RBAC:**
   - In WAC, go to **Settings** and select **Role-based Access Control**.
   - Click **Apply** to enable RBAC, confirming any prompts to restart the WinRM service.
   - Wait for up to 10 minutes for RBAC to be applied, then refresh the WebServer connection.

6. **Assign User to RBAC Role:**
   - In WAC, navigate to **Local Users & Groups** and select user `john`.
   - Click **Manage Membership** and uncheck **Users**, then check **Windows Admin Center Readers**.
   - Click **Save** to update the user's role.

7. **Log in as User John:**
   - Navigate back to the **WebServer** and select **Manage as**.
   - Enter `john` as the username and `user@123` as the password to log in.
   - Confirm that the connection shows as **Webserver (Limited Access)**.

8. **Test User Permissions:**
   - Attempt to create a new storage by navigating to **Storage** and selecting **Create VHD**.
   - Fill in the required fields and click **Submit**.
   - An error notification will appear stating that the operation was blocked by RBAC settings.

### Conclusion
By utilizing Windows Admin Center and configuring RBAC, network defenders can effectively manage user permissions and restrict access to sensitive operations, ensuring a secure environment while allowing necessary administrative tasks.