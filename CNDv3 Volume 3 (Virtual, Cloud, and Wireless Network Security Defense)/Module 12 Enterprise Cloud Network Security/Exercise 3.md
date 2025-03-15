# AWS Network Access Control List (NACL) Firewall Implementation

## Overview
This guide outlines the steps to implement a Network Access Control List (NACL) firewall in AWS to manage inbound and outbound traffic securely.

### Lab Objectives
- Create VPC and its necessary components
- Assign inbound and outbound rules in NACL to secure an instance
- Verify server connectivity using SSH

---

## Step 1: Create VPC
1. **Log in to AWS Management Console**
2. Navigate to **Services** ➔ Search for **VPC**
3. Click **Create VPC**
4. Select **VPC and more**
5. Name the VPC (e.g., `CustomVPC`) and set IPv4 CIDR to `10.0.0.0/24`
6. Select:
   - **Number of Availability Zones**: 1
   - **Number of Public Subnets**: 1
   - **Number of Private Subnets**: 0
7. Click **Create VPC**

---

## Step 2: Create an EC2 Instance
1. Navigate to **Services** ➔ Search for **EC2**
2. Click **Instances (running)** ➔ **Launch instances**
3. Name the instance (e.g., `EC2-NACL`)
4. Select **Amazon Linux 2023 AMI**
5. Select **t2.micro** as the instance type
6. Under **Key Pair (login)**, click **Create a new key pair**
   - Name the key pair (e.g., `NACL-KP`)
   - Select **.ppk** as the private key file format
   - Click **Create key pair**
7. Under **Network Settings**, click **Edit**
   - Select the **Custom VPC** created earlier
   - Enable **Auto-assign public IP**
8. Under **Security Group Name**, type `NACL-SG`
9. Add rules:
   - Rule 1: SSH (port 22) - Source: Anywhere
   - Rule 2: All Traffic - Source: Anywhere
10. Click **Launch Instance**

---

## Step 3: Create and Associate NACL
1. Navigate to **VPC** ➔ Click on **Network ACLs**
2. Click **Create Network ACL**
3. Name the NACL (e.g., `Custom-NACL`) and select the **Custom VPC** created earlier
4. Click **Create Network ACL**
5. Go to **Subnet Associations** tab
6. Click **Edit subnet associations**
7. Select the desired subnet for the EC2 instance and click **Save changes**

---

## Step 4: Connect to EC2 Instance via PuTTY
1. Install PuTTY from `E://CND-Tools/Lab Prerequisites/PuTTY`
2. Open **PuTTYGen**, load the `.ppk` file, and save the private key
3. Open **PuTTY**
4. Under **Host Name**, enter the Public IPv4 address of the instance
5. Go to **Auth** (under SSH settings) and load the `.ppk` key
6. Click **Open** and enter `ec2-user` when prompted
7. Verify connection with:
   ```bash
   ping 8.8.8.8
   ```

---

## Step 5: Testing NACL Configuration
1. Try reconnecting to the instance using PuTTY ➔ Expect a **Network Error**
2. Navigate to **VPC** ➔ **Network ACLs**
3. Under **Inbound Rules**, you will see all traffic is denied
4. Edit **Outbound Rules** to ensure proper traffic flow as required

---

## Step 6: Clean Up Resources
1. Go to **EC2** ➔ Select the instance ➔ Click **Instance State** ➔ Click **Terminate**
2. Confirm the termination process

---

## Conclusion
By implementing Network ACLs in AWS, a network defender can effectively manage and control inbound and outbound traffic to enhance security for VPC subnets and instances.

