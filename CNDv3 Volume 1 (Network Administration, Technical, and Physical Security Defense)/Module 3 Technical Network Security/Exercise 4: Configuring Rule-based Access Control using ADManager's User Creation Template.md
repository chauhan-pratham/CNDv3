### Exercise 4: Configuring Rule-based Access Control using ADManager's User Creation Template

**Objective:** Demonstrate how to create rules and apply restrictions for organizational users using ADManager Plus.

#### Overview of ADManager Plus
ADManager Plus is a comprehensive Active Directory management tool that simplifies user and group management, automates user account processes, and provides reporting capabilities. It allows administrators to create customizable templates and workflows, making it easier to manage user accounts and maintain compliance.

#### Steps to Configure Rule-based Access Control

1. **Launch Smoothwall Firewall VM:**
   - Log in with the password `toor`.

2. **Launch AD Domain Controller VM:**
   - Log in with `CND\Administrator` and password `Pa$$w0rd`.

3. **Install ADManager Plus:**
   - Navigate to `Z:\CNDv3 Module 03 Technical Network Security\Manage Engine ADManager`.
   - Run `ManageEngine_ADManager_Plus_64.exe`.
   - Follow the installation wizard, keeping default settings (port 8080, program folder as ADManager Plus).
   - Click **Finish** once the installation is complete.

4. **Log in to ADManager Plus:**
   - Access the server login page and use the default credentials (`admin` for both username and password).

5. **Create a User Creation Template:**
   - Navigate to the **Management** tab and select **User Creation Templates**.
   - Click **Create** and name the template (e.g., `Finance-Template`).
   - Click on **Creation Rules** and then **Create New Rule**.

6. **Define User Creation Rules:**
   - Under **Rule 1 Conditions**, click **Add Conditions**.
   - Select **Department** from the dropdown and specify the value as **Finance**.
   - Under **Assign Values**, select **Container** and choose **FinanceOU**.
   - Click **Save Template** to finalize the creation of the `Finance-Template`.

7. **Create a User Using the Template:**
   - Go back to the **Management** tab and select **Create Single User**.
   - Choose the `Finance-Template` from the dropdown.
   - Fill in the user details: First name as `martin` and Last name as `cooper`.
   - Set the password to `Pa$$w0rd` and confirm it.

8. **Assign User to the Finance OU:**
   - Under the **Department** section, select **Finance**.
   - Go back to the **General** tab, select **Container**, and choose **FinanceOU**.
   - Click **Create** to finalize the user creation.

9. **Verify User Creation:**
   - Access **AD Explorer** from the top-right corner.
   - Expand **FinanceOU** in the left pane to find the newly created user `martincooper`.
   - Click on the user to view details and confirm that all restrictions and rules are applied.

### Conclusion
By utilizing ADManager Plus, network defenders can effectively streamline user account provisioning and enforce rule-based access control through customizable templates. This automation helps safeguard against unauthorized access and ensures compliance with organizational policies.