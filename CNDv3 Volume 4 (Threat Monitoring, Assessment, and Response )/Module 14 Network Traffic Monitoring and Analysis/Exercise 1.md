# Capturing Network Traffic Using Wireshark

## Lab Scenario
Network traffic contains various data packets that require proper analysis. Wireshark, a powerful network packet analyzer, simplifies this task with its graphical interface for easier sorting and filtering of network data. This guide outlines the steps to capture network traffic using Wireshark.

## Lab Objectives
- Launch firewall VMs for network configuration
- Capture network traffic using Wireshark

---

## Steps to Capture Network Traffic

### Step 1: Launch Firewall Machines
1. **PfSense Firewall:**
   - Click the **PfSense Firewall** link to launch the VM.
   - If the machine is inactive, press **Enter** to activate it.

2. **Smoothwall Firewall:**
   - Click the **Smoothwall Firewall** link to launch the VM.
   - Enter the password as `toor` and press **Enter**.
   - Press the **Tab** key twice to navigate to the **Done** button and press **Enter**.
   - Wait for the Smoothwall Firewall to load successfully.

---

### Step 2: Launch Admin Machine
1. Click **AdminMachine-1** to launch the AdminMachine VM.
2. Click the **Ctrl+Alt+Delete** link to proceed with the login.
3. Enter the following credentials:
   - **Username:** `Admin`
   - **Password:** `admin@123`
4. Click **Enter** to log in.

5. If a **Network** window appears, click **Yes**.
6. If the **Let’s finish setting up your PC** window appears, click **Remind me later**.

---

### Step 3: Open Wireshark
1. Click on the **Start** button.
2. Search for **Wireshark** in the search bar.
3. Click the **Wireshark** app to open it.

---

### Step 4: Start Capturing Network Traffic
1. In the Wireshark main window, select the interface you wish to monitor (e.g., **Ethernet 2**).
2. Click the **Start Capturing Packets** button (blue shark fin icon) from the toolbar.
3. If a **Wireshark Update** popup appears, click **Remind me later**.

Wireshark will begin capturing network traffic from the selected interface.

---

### Step 5: Finalizing
- Once the traffic is captured, review the data as required.
- Close all opened windows when the analysis is complete.

---

## Conclusion
By following these steps, a network defender can efficiently capture and monitor network traffic using Wireshark, gaining valuable insights into data packets and potential network threats.

