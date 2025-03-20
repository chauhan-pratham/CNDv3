### Lab Exercise: Implementing Host-based Firewall Protection with iptables

**Objective:** Configure the iptables firewall on an Ubuntu machine to block internet access for a specific user.

#### Overview of iptables
iptables is a command-line utility for configuring the Linux kernel firewall. It uses policy chains to allow or block traffic based on specified rules.

#### Steps to Configure iptables

1. **Launch Required VMs:**
   - If not already running, launch the **Smoothwall Firewall** and **AD Domain Controller** VMs.
   - Log in to each VM as specified in the original instructions.

2. **Access Operation Dept VM:**
   - Launch the **Operation Dept VM** and log in as user **Smith** with the password `user@123`.
   - Complete any initial setup prompts by clicking **Skip**, **Next**, and **Done**.

3. **Test Internet Access:**
   - Open the Firefox web browser and navigate to `www.google.com` to confirm that Smith has internet access.

4. **Open Terminal:**
   - Press `ALT + CTRL + T` to open the terminal.
   - Type `sudo su` to switch to the root user and press Enter.
   - Enter the root user password (`user@123`) when prompted.

5. **Identify User ID:**
   - In the terminal, type `id smith` and press Enter to find Smith's user ID (UID). Note the UID (e.g., `1001`).

6. **Check Existing iptables Rules:**
   - Type `iptables -L` and press Enter to list existing firewall rules. Confirm that no rules exist.

7. **Create a New iptables Rule:**
   - To block internet access for Smith, type the following command and press Enter:
     ```bash
     iptables -A OUTPUT -o eth0 -m owner --uid-owner 1001 -j DROP
     ```
   - This rule drops all outgoing traffic for the user with UID `1001`.

8. **Test Internet Access Again:**
   - Open the Firefox browser and try to access `www.google.com` again. The website should now be inaccessible, confirming that the iptables rule is effective.

By following these steps, you have successfully configured the iptables firewall to block internet access for a specific user on the Ubuntu machine, enhancing the security of the network.