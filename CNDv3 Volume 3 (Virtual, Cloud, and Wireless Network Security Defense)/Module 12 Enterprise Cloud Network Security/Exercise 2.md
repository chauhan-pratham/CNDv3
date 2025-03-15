# AWS Key Management Service (KMS) Implementation Guide

## Introduction
This guide demonstrates how to create and manage cryptographic keys using AWS Key Management Service (KMS) and implement those keys in AWS services such as Amazon S3, EBS Volumes, and Amazon Redshift.

---
## Prerequisites
Before you begin:
- Ensure you have an AWS account.
- Ensure you have an IAM user with sufficient permissions.
- Complete the steps in **Exercise 1: Implementing AWS Identity and Access Management (IAM)** as this setup will use the IAM user and group created earlier.

---
## Steps to Implement AWS KMS for Encryption

### 1. Create a KMS Master Key
1. Go to the **AWS Management Console**.
2. In the **Search** field, type `KMS` and select **Key Management Service**.
3. In the left pane, select **Customer managed keys**.
4. Click **Create key**.
5. Select **Symmetric key** (default) and click **Next**.
6. In the **Alias** field, enter `CND_user_MasterKey`.
7. Assign permissions to allow IAM user `Alice` to use this key.
8. Click **Next** and review the key policy in JSON format.
9. Click **Finish** to create the Master Key.

---
### 2. Encrypt AWS S3 Using AWS KMS Master Key
1. In the AWS Management Console, go to **S3**.
2. Click **Create bucket**.
3. Provide a bucket name (e.g., `training-groups12`) and click **Next**.
4. Enable the following options under **Properties**:
   - **Versioning**
   - **Server Access Logging** (Optional)
5. Under **Default Encryption**, choose **SSE-KMS** and select your key: `CND_user_MasterKey`.
6. Click **Save changes**.

---
### 3. Encrypt EBS Volume Using AWS KMS Master Key
1. In the AWS Management Console, go to **EC2**.
2. In the left panel, select **Volumes**.
3. Click **Create Volume**.
4. Specify the size and ensure **Encryption** is enabled.
5. In the **Master Key** dropdown, select your key: `CND_user_MasterKey`.
6. Click **Create Volume**.

---
### 4. Encrypt Amazon Redshift Using AWS KMS Master Key
1. In the AWS Management Console, go to **Redshift**.
2. Click **Create cluster**.
3. Enter the **Admin password** (e.g., `Dbuser123`).
4. After the cluster is created, click on the cluster link (e.g., `redshift-cluster-1`).
5. Click **Edit**, then scroll down to **Database Configuration**.
6. Select **Edit Encryption**.
7. Choose **Use AWS Key Management Service (AWS KMS)** and select your key: `CND_user_MasterKey`.
8. Click **Save changes**.

---
### 5. Add User Permissions for KMS Key
1. In the AWS Management Console, go to **KMS**.
2. Select **Customer managed keys**.
3. Select your key: `CND_user_MasterKey`.
4. Scroll to **Key Users** and click **Add**.
5. Search for and select the IAM user `Alice`.
6. Click **Add**.

---
### 6. Clean Up Resources (Post-Lab)
- For **Amazon Redshift**, delete the cluster:
  1. Go to **Redshift**.
  2. Select the cluster.
  3. Click **Actions** → **Delete** (uncheck **Final Snapshot**).

Following these steps ensures secure encryption management for your AWS resources using AWS KMS.

---
## Conclusion
Implementing AWS KMS with proper configurations enhances data security in your AWS environment. Always follow best practices for managing encryption keys, ensuring data confidentiality and integrity.

