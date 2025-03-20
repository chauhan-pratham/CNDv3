### Summary of Steps for Securing IoT Device Communication Using TLS/SSL

1. **Install MQTT Broker**:
   - Launch the Web Server VM and log in with the username "Administrator" and password "admin@123."
   - Navigate to the Bevywise MQTTRoute folder and run `Bevywise_MQTTRoute_4.exe`.
   - Accept the agreement, proceed with the default installation settings, and complete the installation.

2. **Install IoT Simulator**:
   - Launch the Admin Machine-1 VM and log in with the username "Admin" and password "admin@123."
   - Navigate to the Bevywise IoT Simulator folder and run `Bevywise_IoTSimulator_3`.
   - Accept the agreement, keep default settings, and complete the installation.

3. **Launch IoT Simulator**:
   - Navigate to `C:\Bevywise\IotSimulator\bin` and run `runsimulator.bat`.
   - Open the IoT Simulator in a web browser and create a new network named "CND_FINANCE_NETWORK."

4. **Configure Network Settings**:
   - Set the Broker IP Address to `10.10.10.16` and save the settings.
   - Add a new device (e.g., "Temperature_Sensor" with ID "TS1") to the network and start the network.

5. **Monitor Communication**:
   - Use Wireshark to capture traffic on the Ethernet interface.
   - Open the MQTTRoute web interface and send a command to the device using the topic "High_Tempe."

6. **Verify Communication**:
   - Check the IoT Simulator for the alert message sent to the device.
   - Use Wireshark to filter traffic on TCP port 1883 to view unencrypted messages.

7. **Implement TLS/SSL**:
   - Close the MQTTRoute Broker and edit the `broker.conf` file to enable TLS by changing `TLS_ENABLED=FALSE` to `TLS_ENABLED=TRUE`.
   - Restart the Broker to use TCP port 8883 for secure communication.

8. **Copy Certificates**:
   - Copy the Client and root certificate folders from the server to the client machine.
   - Replace existing certificates in the IoT Simulator directory.

9. **Reconnect IoT Simulator**:
   - Stop the IoT Simulator and restart it to apply the new TLS/SSL settings.
   - Select the existing network "CND_FINANCE_NETWORK" and enable TLS/SSL in the settings.

10. **Send Commands Over TLS/SSL**:
    - Use the MQTTRoute web interface to send a command to the device using the topic "High_Tempe."
    - Verify the alert message in the IoT Simulator.

11. **Capture and Verify Encrypted Traffic**:
    - Stop Wireshark and filter traffic to view encrypted packets.
    - Confirm that the communication is secure by checking the details of the encrypted application data.

By following these steps, network defenders can effectively secure IoT device communication using TLS/SSL, protecting against unauthorized access and ensuring data integrity within the network.