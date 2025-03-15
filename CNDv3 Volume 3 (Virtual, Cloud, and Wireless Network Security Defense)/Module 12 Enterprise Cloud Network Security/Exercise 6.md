# Using Google Secret Manager to Design and Manage Secrets

## Overview
Secret Manager is a Google Cloud service that can securely store sensitive data such as API keys, passwords, certificates, and other private information. This guide demonstrates how to create, manage, and delete secrets using the Google Cloud Console and Cloud Shell.

---

## Lab Objectives
- Enable Google Secret Manager
- Create a secret using the Google Cloud Console
- Create a secret and add values using the Cloud Shell
- Access secret values
- Delete secrets and disable Secret Manager services

---

## Steps to Implement Google Secret Manager

### Step 1: Enable Google Secret Manager
1. Go to [Google Cloud Console](https://console.cloud.google.com/).
2. Sign in with your GCP credentials.
3. In the search bar, type **Secret Manager** and select **Secret Manager API**.
4. Click **ENABLE** to enable Secret Manager.

---

### Step 2: Create a Secret Using the Cloud Console
1. In the search bar, type **Secret Manager**.
2. Click **+ Create Secret**.
3. Enter a **Name** for your secret (e.g., `Password`).
4. Enter the **Secret Value** (e.g., `Today`).
5. Retain the default settings and click **CREATE SECRET**.
6. To view the secret value:
   - Click the **More options** button next to the secret.
   - Select **View secret value**.
   - Click **Done**.

---

### Step 3: Create a New Secret Value (Version)
1. Select the created secret (e.g., `Password`).
2. Click **+ New Version**.
3. Enter the new **Secret Value** (e.g., `Tomorrow`).
4. Click **ADD NEW VERSION**.
5. To verify the new version:
   - Go to **LOGS** in Secret Manager.

---

### Step 4: Create a Secret Using the Cloud Shell
1. Click the **Activate Cloud Shell** button (located at the top right).
2. In the Cloud Shell terminal, enter:
```bash
gcloud projects list
```
3. Copy the **Project ID** for your desired project.
4. Set the project in Cloud Shell by entering:
```bash
gcloud config set project <project_id>
```
5. Create a sample certificate by entering:
```bash
openssl req -new -newkey rsa:4096 -x509 -sha256 -days 365 -nodes -out MyCertificate.crt -keyout MyKey.key
```
6. Fill out the prompts as follows:
   - Country Name: Press **Enter**
   - State or Province Name: Press **Enter**
   - Locality Name: Press **Enter**
   - Organization Name: Enter `ECC`
   - Organizational Unit Name: Enter `Technology`
   - Common Name: Enter `secrets.ecc.com`
   - Email Address: Enter your email
7. Verify the certificate by entering:
```bash
openssl x509 -in MyCertificate.crt --noout --text
```
8. Create a new secret by entering:
```bash
gcloud secrets create Certificate --replication-policy="automatic"
```
9. Add the certificate to the secret by entering:
```bash
gcloud secrets versions add Certificate --data-file="MyCertificate.crt"
```

---

### Step 5: Access Secret Value Using Cloud Shell
1. Enter the following command to access the value of your secret:
```bash
gcloud secrets versions access 1 --secret="Certificate"
```

---

### Step 6: Deleting Secrets
1. In the **Secret Manager** page, click on the **More options** button next to the secret.
2. Select **Delete**.
3. Enter the secret name and click **DELETE SECRET**.
4. Repeat for other secrets as required.

---

### Step 7: Disable Secret Manager API
1. Go to **APIs & Services** from the Google Cloud Console menu.
2. Select **Enabled APIs & Services**.
3. Find **Secret Manager API** and click **MANAGE**.
4. Click **DISABLE API**.
5. In the **Disable Secret Manager API** popup, click **DISABLE**.

---

## Conclusion
By following these steps, you have successfully implemented Google Secret Manager for secure management of sensitive data in your Google Cloud Platform environment.

