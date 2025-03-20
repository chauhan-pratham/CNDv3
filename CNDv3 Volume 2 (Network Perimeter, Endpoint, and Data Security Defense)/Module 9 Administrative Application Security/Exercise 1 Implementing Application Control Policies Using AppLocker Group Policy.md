### Summary of Steps for Implementing AppLocker

1. **Launch Smoothwall Firewall:**
   - Open the Smoothwall Firewall VM and log in with the password `toor`.

2. **Access AD Domain Controller:**
   - Launch the AD Domain Controller VM and log in as `CND\Administrator` with password `Pa$$w0rd`.
   - Open Internet Explorer and close Microsoft Edge.

3. **Open Group Policy Management:**
   - Click on the Start icon, select **Server Manager**, then navigate to **Tools** > **Group Policy Management**.

4. **Create a New Group Policy Object (GPO):**
   - Right-click on **Group Policy Objects** and select **New**.
   - Name it **Whitelist Using AppLocker** and click **OK**.

5. **Edit the GPO:**
   - Right-click on the new GPO and select **Edit**.
   - Navigate to **Computer Configuration** > **Policies** > **Windows Settings** > **Security Settings** > **System Services**.
   - Right-click on **Application Identity**, select **Properties**, check **Define this policy setting**, set to **Automatic**, and click **Apply** and **OK**.

6. **Configure AppLocker:**
   - Navigate to **Computer Configuration** > **Policies** > **Windows Settings** > **Security Settings** > **Application Control Policies** > **AppLocker**.
   - Click on **Configure Rule Enforcement** and set **Executable rules** to **Enforce rules**. Click **Apply** and **OK**.

7. **Automatically Generate Rules:**
   - Right-click on **Executable Rules** and select **Automatically Generate Rules**.
   - Retain default options and click **Next** to generate rules.
   - Review and click **Create** to finalize the rules.

8. **Deny Access to Microsoft Edge:**
   - Right-click on the rule for **Internet Explorer**, select **Properties**, check the **Deny** radio button, and click **Apply** and **OK**.

9. **Link the GPO:**
   - Right-click on the **cnd.com** domain, select **Link an Existing GPO**, and choose **Whitelist Using AppLocker**.

10. **Update Group Policy:**
    - Click on **Whitelist Using AppLocker**, go to the **Status** tab, and click **Detect Now**.
    - Open Command Prompt and run `gpupdate /force` to update the policy.

11. **Test the Policy:**
    - Attempt to open Internet Explorer; you should see a message stating, "This app has been blocked by your system administrator."
    - If the message does not appear, restart the AD Domain Controller and repeat the last steps.

12. **Disable the GPO Link (if needed):**
    - Open **Group Policy Management**, right-click on **Whitelist Using AppLocker**, and select **Link Enabled** to disable the link.

---

This summary captures the essential steps while maintaining clarity and brevity. Let me know if you need any further modifications!