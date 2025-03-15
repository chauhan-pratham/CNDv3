# AWS Identity and Access Management (IAM) Implementation

## Overview
This guide demonstrates how to implement AWS Identity and Access Management (IAM) to secure AWS services and resources by creating an IAM Group, IAM User, assigning policies, creating custom IAM policies, and enabling Multi-Factor Authentication (MFA).

---
## Steps to Implement AWS IAM

### 1. Create IAM Group in AWS
1. Go to AWS Management Console → Select **IAM** under Security, Identity, & Compliance.
2. Click on **User Groups** → Click on **Create Group**.
3. Enter **Training_Group** in the Group Name field.
4. Under **Attach Policy**, check:
   - **IAMUserChangePassword**
   - **DatabaseAdministrator**
5. Click **Create User Group**.

### 2. Create IAM User in AWS
1. Go to **IAM** → Click on **Users** → Click **Create User**.
2. Enter **Alice** in the User Name field.
3. Under **AWS Access Type**, select **AWS Management Console access**.
4. Choose **Custom password** and enter `User@123`. Check the box for **User must create a new password**.
5. Select **Add user to group** and check **Training_Group**.
6. Click **Next** → **Create User**.

### 3. Assign Permission Policy to User
1. In **IAM**, select **Users**.
2. Select **Alice** and click on **Add permissions**.
3. Choose **Attach policies directly**.
4. Search for **AmazonS3ReadOnlyAccess**, select it, and click **Next**.
5. Click **Add permissions** to complete the process.

### 4. Create a Custom IAM Policy
1. In **IAM**, click on **Policies** → Click **Create Policy**.
2. Click **Select a service**, type `cloudfront`, and select it.
3. Expand the **Actions** menu → Select **Read Access**.
4. Expand **Resources** → Select **All resources**.
5. Under **Request conditions**, select **User is MFAAuthenticated**.
6. Enter **UserAccessCustomPolicy** as the policy name.
7. Add a description: "Custom policy granting Read Access for CloudFront Services".
8. Click **Create Policy**.

### 5. Enable MFA for IAM User
1. In **IAM**, select **Users**.
2. Select **Alice** → Go to **Security Credentials** tab.
3. Copy the **Console-sign-in link**.
4. Open the URL in an incognito browser window.
5. Enter IAM user name (**Alice**) and password (**User@123**) to sign in.
6. Follow the steps to set up MFA for added security.

### 6. Verify Permissions
1. As **Alice**, attempt to access IAM services via AWS Console.
2. You should receive an error, confirming limited permissions are applied.

---
## Conclusion
By following these steps, you can successfully create and manage IAM Groups, Users, and Policies, ensuring secure access control in AWS. Implementing MFA adds an extra layer of protection for enhanced security.

