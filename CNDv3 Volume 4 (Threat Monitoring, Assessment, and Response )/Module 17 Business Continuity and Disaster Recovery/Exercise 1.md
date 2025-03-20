# Business Continuity and Disaster Recovery using NLB

## Lab Overview
This lab demonstrates how to implement Business Continuity and Disaster Recovery using Network Load Balancing (NLB) in Windows Server. NLB ensures high availability and scalability by distributing traffic across multiple servers.

## Lab Setup
### VM Configuration
- **Web Server VM** - IP: `10.10.10.16`
- **Backup Server VM** - IP: `10.10.10.17`
- **Cluster IP** - `10.10.10.89`
- **DNS Domain** - `luxurytreats.com`

## Lab Steps
### Step 1: Configure Smoothwall Firewall
- Launch Smoothwall Firewall VM
- Login with `toor`
- Leave the VM running

### Step 2: Configure AD Domain Controller
- Launch AD Domain Controller VM
- Login with `CND\Administrator` and password `Pa$$w0rd`
- Open DNS Manager
- Create a new Forward Lookup Zone:
  - **Zone Name:** `luxurytreats.com`
- Add Host (A) Records:
  - **WebServer** - IP: `10.10.10.16`
  - **BackupServer** - IP: `10.10.10.17`

### Step 3: Install NLB Feature
**On Web Server VM:**
- Login with `Administrator` / `admin@123`
- Open **Server Manager** > Add roles and features
- Select **Network Load Balancing** feature and install it
- Repeat the same steps for the **Backup Server VM**

### Step 4: Configure DNS on Servers
- On Web Server VM:
  - Open **System Properties** > **Computer Name** > **Change** > **More...**
  - Set Primary DNS suffix to `luxurytreats.com`
  - Restart VM
- Repeat the same steps for the **Backup Server VM**

### Step 5: Configure NLB Cluster
- On Web Server VM:
  - Open **Network Load Balancing Manager**
  - Right-click **Network Load Balancing Clusters** > **New Cluster**
  - Add Host: `10.10.10.16`
  - Set Priority: `1`
  - Add Cluster IP: `10.10.10.89`
  - Set Full Internet Name: `www.luxurytreats.com`
  - Set **Multicast** mode
- Add Backup Server to Cluster:
  - Add Host: `10.10.10.17`

### Step 6: Create Cluster DNS Record
- On AD Domain Controller VM:
  - Add Host (A) Record:
    - **Name:** `www`
    - **IP:** `10.10.10.89`

### Step 7: Attacker Machine Configuration
- Login as `Bob` / `user@123`
- Open Network Settings and set DNS to `10.10.10.19`
- Edit `/etc/hosts` file to comment out the Web Server entry:
  ```sh
  # 10.10.10.16 www.luxurytreats.com
  ```
- Restart the Attacker Machine
- Access `http://www.luxurytreats.com` in the browser

### Step 8: Verify Continuity
- Shutdown Web Server VM
- Access the website again to confirm Backup Server handles requests successfully

## Conclusion
This implementation of Network Load Balancing ensures uninterrupted access to the `luxurytreats.com` website, maintaining business continuity and disaster recovery.

