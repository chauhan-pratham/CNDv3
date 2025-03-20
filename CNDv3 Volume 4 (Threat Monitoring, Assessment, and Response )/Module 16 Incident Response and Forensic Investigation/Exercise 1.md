## Exercise 1: Working with Incident Tickets in OSSIM

### Overview of OSSIM
OSSIM is an open-source SIEM tool that helps identify potential threats within the network by generating incident tickets. These tickets enable defenders to filter, prioritize, and investigate incidents efficiently.

### Lab Objectives
- Learn to create and manage incident tickets in AlienVault OSSIM.

### Lab Steps

1. **Launch Virtual Machines (VMs)**
   - Click `Web Server` VM, press `Ctrl+Alt+Delete`, and log in as `admin@123`.
   - Click `OSSIM Server` VM, log in with:
     - **Username:** `root`
     - **Password:** `toor`

2. **Access OSSIM Web Interface**
   - On `Admin Machine-1`, open Chrome and visit `https://10.10.10.75`.
   - Click `Advanced` and proceed.
   - Log in with:
     - **Username:** `admin`
     - **Password:** `admin@123`

3. **Create a New Ticket**
   - Go to `ANALYSIS` > `TICKETS`.
   - Scroll down, select `Alarm` from the drop-down, and click `CREATE`.
   - Fill in ticket details and click `SAVE`.

4. **Filter and Edit Tickets**
   - Use the `Class` and `Type` drop-downs to filter tickets.
   - Click any ticket under `TITLE` to view and edit.
   - Edit the ticket by entering:
     - **SOURCE IPS:** `10.10.10.50`
     - **DEST IPS:** `10.10.10.16`
   - Click `SAVE` to confirm changes.

### Conclusion
By following these steps, you can efficiently manage incident tickets in AlienVault OSSIM to track and respond to security events effectively.

