# Securing SDN Communication Using SSL

## Overview
This guide outlines steps to configure Secure Sockets Layer (SSL) between a Switch and an SDN Controller using Mininet for improved network security.

---

## Lab Objectives
- Install Mininet on Ubuntu OS
- Create an SDN using Mininet emulator
- Enable SSL between the Switch and SDN Controller

---

## Step 1: Update the System
1. **Launch OperationDept VM**
2. **Login with credentials:**
   ```bash
   Username: alice
   Password: user@123
   ```
3. **Open Terminal:**
   ```bash
   Press Ctrl+Alt+T
   ```

4. **Update and Upgrade the System:**
   ```bash
   sudo apt-get update && sudo apt upgrade -y
   ```

---

## Step 2: Install Mininet
1. **Clone the Mininet Repository:**
   ```bash
   git clone https://github.com/mininet/mininet
   ```

2. **Verify Downloaded Files:**
   ```bash
   ls
   ```

3. **Install Mininet:**
   ```bash
   mininet/util/install.sh -a
   ```

4. **Verify Installation:**
   ```bash
   sudo mn
   exit
   ```

---

## Step 3: Create and Configure Virtual Network
1. **Launch Mininet MiniEdit:**
   ```bash
   python2 mininet/examples/miniedit.py
   ```
2. **Create a Network:**
   - Drag two hosts (h1, h2), one switch (s1), and one controller (c0) into the canvas.
   - Link the two hosts with the switch and the switch with the controller.

3. **Check Network Connectivity:**
   - Go to **Run** → Select **Run**
   - Open the **Host: h2** terminal
   - Open the **Host: h1** terminal

4. **Ping Host h1 from Host h2:**
   ```bash
   ping 10.0.0.1
   ```
   > Press **Ctrl + C** to stop the ping process.

---

## Step 4: Enable SSL Security
1. **Stop the Network:**
   - Go to **Run** → Select **Stop**

2. **Configure SSL on the Controller:**
   - Right-click on the **c0 controller** → Select **Properties**
   - Set **Protocol** to **SSL** → Click **OK**

3. **Configure NetFlow and sFlow on Switch:**
   - Right-click on the **s1 switch** → Select **Properties**
   - Check **Enable NetFlow** and **Enable sFlow** → Click **OK**

4. **Test Network Connection:**
   - Attempt to ping **Host h1** from **Host h2**
   - **Ping should now fail**, confirming that SSL has restricted network communication for security.

---

## Conclusion
By enabling SSL on the SDN controller and configuring NetFlow/sFlow, you enhance the security of the SDN environment. This reduces the risk of controller compromise and secures critical network traffic. 🚀

