### Summary of Steps for Basic Network Administration and Troubleshooting Using Windows Command-Line Utilities

1. **Launch Admin Machine-1 VM**: 
   - Click on Admin Machine-1 -Mod 5 (COPY).
   - Log in with the username `Admin` and password `admin@123`.

2. **Disable Network Adapters**:
   - Navigate to Control Panel > Network and Internet > Network and Sharing Center > Change adapter settings.
   - Right-click on each Ethernet adapter and select "Disable."

3. **Launch Web Server VM**:
   - Click on Web Server -Mod 5 (COPY) and log in with `admin@123`.

4. **Open Command Prompt**:
   - Search for `cmd`, right-click, and select "Run as administrator."

5. **Check IP Configuration**:
   - Type `ipconfig` and press Enter to view IP configuration.
   - Use `ipconfig /all` for detailed information including hostname and MAC address.

6. **Ping Test**:
   - Use `ping 10.10.10.2` to check connectivity to Admin Machine-1.
   - Expect a "Destination host unreachable" error due to disabled adapters.

7. **Enable Network Adapters**:
   - Return to Admin Machine-1, re-enable both Ethernet adapters.

8. **Re-test Ping**:
   - Switch back to Web Server and ping `10.10.10.2` again. This time, it should succeed.

9. **Use Tracert Command**:
   - On Web Server, type `tracert 10.10.10.2` to determine the route to Admin Machine-1.

10. **Check Network Statistics with Netstat**:
    - Type `netstat` to view active TCP connections.
    - Use `netstat -s -p tcp` for statistics specific to TCP.
    - Use `netstat -n` to show active TCP connections numerically.

11. **View ARP Cache**:
    - Type `arp -a` to display the ARP cache, mapping IP addresses to MAC addresses.

12. **Additional Useful Commands**:
    - `ipconfig /flushdns`: Flushes the DNS resolver cache.
    - `nbtstat -a <MachineName>`: Obtains information from WINS or LMHOST.
    - `netstat -ab`: Links each used port with its application.
    - `ping -t <IP>`: Pings a host continuously until stopped.

13. **Close Command Prompt**: After completing the troubleshooting tasks, close the Command Prompt window.

By following these steps, network defenders can effectively utilize Windows Command-line utilities for network troubleshooting and administration.