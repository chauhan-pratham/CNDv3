# Securing Amazon Web Services Storage

### Lab Scenario
In the cloud, data are stored on Internet-connected servers in data centers. It is important that network defenders understand and implement the data storage security features for data encryption and access management tools provided by service providers to secure the data stored in the data centers.

### Lab Objectives
This lab demonstrates how to:
- Assign Permissions to Amazon S3 Using ACL
- Assign Permissions to Amazon S3 Using Bucket Policy

### Overview of AWS Storage
Amazon S3 allows uploading and retrieving data at any time from anywhere on the internet. It stores data as objects within buckets. By default, all Amazon S3 buckets are accessed by authorized users. Restrict access to S3 resources by combining bucket policies, ACLs, and IAM policies to provide access to the right entities.

---

## Lab Steps

### Step 1: Log in to AWS Management Console
1. Go to [AWS Console](https://aws.amazon.com/).
2. Click on **AWS Management Console** from the **My Account** drop-down menu.
3. Click on **Sign in using root user email**.
4. Enter the AWS administrator account ID and click **Next**.
5. Enter the password and click **Sign-in**.

### Step 2: Access Amazon S3
1. Click on **Services**.
2. In the search field, type **S3**, and select **S3 Scalable Storage in the Cloud**.
3. Select the **training-group12** bucket.

### Step 3: Configure Permissions
1. Navigate to the **Permissions** tab.
2. Under **Block public access**, click **Edit**.
3. Uncheck **Block all public access** and click **Save changes**.
4. In the confirmation dialog, type **confirm** and click **Confirm**.

### Step 4: Assign ACL Permissions
1. Under the **Permissions** tab, click **Edit** under **Access Control List (ACL)**.
2. Ensure all permissions are selected for the **Bucket Owner**.
3. Click **Save Changes**.

### Step 5: Configure Bucket Policy
1. In the **Permissions** tab, click **Edit** under **Bucket Policy**.
2. Click on the **Policy generator** link (opens in a new tab).
3. In the AWS Policy Generator page:
   - Set **Type of Policy** to **S3 Bucket Policy**.
   - Set **Effect** to **Allow**.
   - In the **Principal** field, enter a wildcard (`*`).
   - Set **AWS Service** to **Amazon S3**.
4. Switch back to the original tab, copy the bucket's ARN, and paste it in the **Amazon Resource Name (ARN)** field.
5. Check **All Actions** and click **Add Statement**.
6. Click **Generate Policy**.
7. Copy the generated JSON policy and close the popup.
8. Switch to the first tab with the S3 Management Console and paste the copied JSON code into the **Bucket policy editor**.
9. Click **Save**.

### Step 6: Verify Changes
1. The bucket now has public access with updated policies.
2. Ensure to review the settings and verify the applied permissions.

---

### Conclusion
By following these steps, network defenders can effectively secure Amazon S3 storage by using ACLs and bucket policies to manage permissions efficiently.

