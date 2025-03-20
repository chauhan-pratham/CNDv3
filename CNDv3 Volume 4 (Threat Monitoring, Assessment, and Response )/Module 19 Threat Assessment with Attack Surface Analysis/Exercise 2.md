### Exercise 2: Analyzing Web Application Attack Surface using OWASP Attack Surface Detector (ZAP Plugin)

### Objective
Identify the attack surface of a web application using the OWASP ZAP Attack Surface Detector plugin.

### Steps

1. **Launch Admin Machine-1**
   - Click `Admin Machine-1 -Mod 19 (COPY)` → Click `Ctrl+Alt+Delete` → Login with password `admin@123`.
   
2. **Copy Required Files**
   - Navigate to `E:\CND-Tools\CNDv3 Module 19 Threat Assessment with Attack Surface Analysis\Attack Surface Detector`.
   - Copy `LuxuryTreats.zip` and `attacksurfacedetector-alpha-1.1.4.zap` to the desktop.

3. **Open OWASP ZAP**
   - Launch `OWASP ZAP` → Select `No, I do not want to persist this session` → Click `Start`.

4. **Install Attack Surface Detector Plugin**
   - Go to `File → Load Add-on-File...`.
   - Select `attacksurfacedetector-alpha-1.1.4.zap` from the desktop → Click `Open`.

5. **Configure Attack Surface Detector**
   - Click the green `+` icon above the bottom pane.
   - Select `Attack Surface Detector` → Go to `Configuration` tab.

6. **Import Endpoints from Source**
   - Click `Import Endpoints from Source` → Click `Browse`.
   - Select `LuxuryTreats.zip` from the desktop → Click `Open`.
   - Click `Submit` and wait for the analysis to finish.

7. **View Results**
   - Go to the `Results` tab in the Attack Surface Detector pane.
   - View the identified endpoints and GET method parameters.

### Outcome
Successfully identified the web application's attack surface by analyzing its source code using OWASP ZAP Attack Surface Detector.

---
This guide simplifies the lab steps for quick reference and documentation purposes.

