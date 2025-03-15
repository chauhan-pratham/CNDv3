# Implementing Azure AD Multi-Factor Authentication Settings to Block and Unblock Users

## Lab Scenario
Azure AD offers Multi-Factor Authentication (MFA) to allow an administrator to block or unblock a user from accessing the system. This guide walks through the steps to create a new user in Azure AD and manage their MFA status.

## Lab Objectives
- Create an Azure AD user
- Enable Azure AD MFA
- Block and Unblock a user in Azure AD MFA

## Prerequisites
- An Azure account (Free or Paid)
- Admin permissions to access Azure AD settings

## Steps to Implement Azure AD MFA

### Step 1: Log in to Azure Portal
1. Go to [Azure Portal](https://azure.microsoft.com/en-in/account/)
2. Click **Sign in** and enter your account credentials.

### Step 2: Create a New User in Azure AD
1. In the Azure Portal search bar, type **Microsoft Entra ID** and select it.
2. Click on **+ Add** and select **User > Create New User**.
3. Under **Identity**, provide the following details:
   - **User name:** `Chris`
   - **Name:** `Chris Watson`
4. Uncheck **Auto-generate password**, enter `Secadmin@1231` as the password, then click **Next: Properties**.
5. Under **Identity and Job Info**, enter:
   - **First Name:** `Chris`
   - **Last Name:** `Watson`
   - **User Type:** `Member`
   - **Job Title:** `Network Administrator`
   - **Company Name:** `Global Security Tech Ltd`
   - **Department Name:** `IT Department`
6. Click **Next: Assignments**, keep default settings, and click **Next: Review + Create**.
7. Click **Create** to finalize user creation.

### Step 3: Enable Azure AD MFA
1. Navigate to **Microsoft Entra ID** → **Security** → **Multifactor Authentication**.
2. Click **Get Free Premium Trial** to activate MFA features (if not activated).
3. Follow the prompts to activate both **Enterprise Mobility + Security E5** and **Azure AD Premium P2**.

### Step 4: Block a User in Azure AD MFA
1. Navigate to **Multifactor Authentication** → **Block/Unblock users**.
2. Click **+ Add** to block a user.
3. Enter the username (e.g., `Chris@eccdemoaccgmail.onmicrosoft.com`).
4. In the **Reason** field, type a reason such as `Lost Laptop`.
5. Click **OK**. The user will now be blocked.

### Step 5: Unblock a User in Azure AD MFA
1. Navigate to **Multifactor Authentication** → **Block/Unblock users**.
2. Click **Unblock** next to the blocked user.
3. Enter a reason such as `Trusted User`.
4. Click **OK**. The user will be unblocked successfully.

### Step 6: Deleting the User
1. Navigate to **Microsoft Entra ID** → **Users**.
2. Select the user (e.g., `Chris Watson`).
3. Click **Delete** at the top.
4. Confirm the deletion to remove the user from Azure AD.

## Cleanup
- Ensure you delete, shut down, or terminate all resources created in this lab to prevent additional billing.

## Conclusion
Following these steps, you have successfully:
- Created an Azure AD user
- Enabled Azure AD MFA
- Blocked and unblocked a user in Azure AD

These actions help secure user access in your Azure environment using Azure AD MFA.

