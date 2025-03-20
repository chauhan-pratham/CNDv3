## Exercise 2: Threat Hunting in Windows using YARA

### Overview of YARA
YARA is an open-source pattern-matching tool used for malware detection and threat hunting. It allows security analysts to create flexible rules for identifying malicious content in files, directories, or system processes.

---

## Lab Instructions

### Step 1: Setup YARA
1. **Launch Admin Machine-1** and log in with:
   - **Username:** `admin`
   - **Password:** `admin@123`
2. Navigate to `E:\CND-Tools\CNDv3 Module 20 Threat Prediction With Cyber Threat Intelligence\YARA`
3. Copy `yara-4.4.0-rc1-2176-win64.zip` to `C:\Yara`.
4. Extract the zip file, move its contents to `C:\Yara`, and delete the empty folder.

### Step 2: Create a YARA Rule
1. Open **Notepad++** and create a new file.
2. Add the following YARA rule:

```yara
rule Malicious
{
    meta:
        description = "Identify malicious sites"
        author = "ECCouncil"
        date = "2023-11-22"

    strings:
        $str1 = "http://dance4.xyz/" nocase
        $str2 = "malware"

    condition:
        $str1 or $str2
}
```

3. Save the file as `rule.yar` in the `C:\Yara` folder.

### Step 3: Run YARA Scan
1. Open **Command Prompt** in the `C:\Yara` folder.
2. Type `yara64 --help` to confirm YARA installation.
3. Navigate to the shared folder on the WebServer VM (`Z:\Shared docs\Files`).
4. Run the following command to scan for threats:

```cmd
yara64 -s -r rule.yar "\\10.10.10.16\Shared docs\Files"
```

5. If a malicious file is detected, YARA will display the matching strings.

### Step 4: Best Practices
- Regularly update YARA rules to stay ahead of new threats.
- Perform routine scans to identify potential security risks.

---

### Conclusion
YARA is an effective tool for proactive threat detection. By creating targeted rules and regularly scanning files, organizations can mitigate security risks and enhance their cyber defense mechanisms.

