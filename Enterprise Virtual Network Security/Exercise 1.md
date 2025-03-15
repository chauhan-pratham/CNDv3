# Auditing Docker Host Security Using Docker-Bench-Security Tool

## Overview
This guide outlines steps to audit and improve the security of a default Docker installation on an Ubuntu host using the **Docker-Bench-Security** tool.

---

## Lab Objectives
- Install Docker on Ubuntu OS
- Audit Docker security using Docker-Bench-Security Tool
- Fix identified security warnings

---

## Step 1: Install Docker on Ubuntu
1. **Update System Packages:**
   ```bash
   sudo apt-get update
   ```

2. **Remove Older Versions of Docker:**
   ```bash
   sudo apt-get remove docker docker-engine docker.io
   ```

3. **Install Docker:**
   ```bash
   sudo apt install docker.io
   ```

4. **Verify Installation:**
   ```bash
   apt list --installed | grep docker
   ```

5. **Check Docker Images (Optional):**
   ```bash
   sudo docker images
   ```

---

## Step 2: Install Docker-Bench-Security Tool
1. **Switch to Root User:**
   ```bash
   sudo su
   ```

2. **Clone the Docker-Bench-Security Repository:**
   ```bash
   git clone https://github.com/docker/docker-bench-security.git
   ```

3. **Navigate to the Docker-Bench-Security Directory:**
   ```bash
   cd docker-bench-security
   ```

4. **Run the Security Audit Script:**
   ```bash
   sh docker-bench-security.sh
   ```

---

## Step 3: Fix Identified Security Warnings

### 1. Configure Docker Daemon Securely
1. **Create or Edit Daemon Configuration:**
   ```bash
   gedit /etc/docker/daemon.json
   ```

2. **Add the Following JSON Configuration:**
```json
{
  "icc": false,
  "userns-remap": "default",
  "log-driver": "syslog",
  "live-restore": true,
  "userland-proxy": false
}
```
3. **Restart Docker Service:**
   ```bash
   systemctl restart docker.service
   ```

4. **Run Docker-Bench-Security Again:**
   ```bash
   sh docker-bench-security.sh
   ```

---

### 2. Enable Docker Content Trust (DCT)
By default, Docker Content Trust is **disabled**. Enable it using the following steps:

1. **Check DCT Status:**
   ```bash
   sh docker-bench-security.sh
   ```

2. **Enable DCT:**
   ```bash
   export DOCKER_CONTENT_TRUST=1
   ```

3. **Verify the Updated DCT Status:**
   ```bash
   sh docker-bench-security.sh
   ```

---

## Step 4: Capturing Network Traffic Using Wireshark

### 1. Install Wireshark
- Click **AdminMachine-1** to launch the VM.
- Log in with username **Admin** and password **admin@123**.
- Open the **Start Menu** → Search for **Wireshark** → Open the application.

### 2. Capture Network Traffic
1. Select the **Ethernet 2** interface.
2. Click the **Start Capturing Packets** (blue shark fin icon).
3. Observe the captured packets in real-time.
4. Click **Stop Capturing Packets** (red icon) when done.

### 3. Filter Network Traffic
- Use these filters to isolate specific traffic:

```bash
http   # Filter HTTP packets
tcp    # Filter TCP packets
icmp   # Filter ICMP packets
ip.addr == 10.10.10.50   # Filter packets from a specific IP
```

---

## Step 5: Final Check
- Re-run `docker-bench-security` to ensure your Docker configuration meets security standards.
- Address any remaining `WARN` messages for improved security.

---

## Conclusion
Following these steps will help secure your Docker environment and improve network monitoring using Wireshark. Regularly audit and update your configurations to maintain a robust security posture. 🚀

