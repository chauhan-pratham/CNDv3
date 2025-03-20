### Administrative Network Security Lab: Implementing Password Policy using ManageEngine Password Manager

**Objective:** Manage and apply password policies to enhance the security of sensitive information on server machines.

#### Lab Steps:

1. **Launch Admin Machine-1 VM:**
   - Log in with username: `Admin`, password: `admin@123`.

2. **Install ManageEngine Password Manager:**
   - Navigate to `E:\CND-Tools\CNDv3 Module 02 Administrative Network Security\Manage Engin Password Mgr`.
   - Run `ManageEngine_PMP_64bit.exe`.
   - Click Yes for User Account Control, then click Next and accept the License Agreement.
   - Retain default settings for installation location and select "High Availability Primary Server."
   - Click OK for antivirus scan interference pop-up and skip the registration for technical support.
   - Click Next to begin installation and ignore any pop-ups during the process.
   - Uncheck the readme file option, check "Start PMP service," and click Finish.

3. **Access Password Manager Pro:**
   - Open Chrome and navigate to `https://localhost:7272/`.
   - Click on "Proceed to localhost (unsafe)."
   - Log in with username: `admin`, password: `admin`.
   - Update the password to `User@456` in the Profile Update page.

4. **Configure Exclusions in Windows Security:**
   - Open Windows Security and navigate to "Virus & threat protection."
   - Go to "Manage settings" and then "Add or remove exclusions."
   - Add an exclusion for the PMP folder located at `C:\Program Files\ManageEngine`.

5. **Set Up Password Policies:**
   - In the ManageEngine dashboard, click on Admin and then Password Policies.
   - Select the "Strong" policy and click on Add Policy.
   - Name the policy `ServerPolicyPwd`, and set the following:
     - Minimum length: 8
     - Maximum length: 15
     - Enforce Numerals, Mixed Case, and Special Characters.
   - Under Words usage, select the desired parameters.
   - Under Sequences, check "Password should not contain sequences of length" and set to 5 for both Alphabet and Numeric Sequences.
   - Under Password Similarity, set the count to 2.
   - Set Password Age to 60 days.
   - Generate a password using the policy and save it.

6. **Create a Resource Group:**
   - Click on Groups and select Add Group, then choose Dynamic group.
   - Name the group `Windows Local Admin`, select the previously created password policy, and set criteria for Windows Local Admin accounts.

7. **Add a New Windows Resource:**
   - Navigate to Resources and select Add Resource, then Add Manually.
   - Enter the Resource Name, DNS Name/IP Address, Resource Group, Domain Name, Department, and Password Policy.
   - Save and proceed to add accounts.
   - Create accounts for `Admin` and `Test` using the `ServerPolicyPwd` password policy.

8. **Configure Remote Password Reset:**
   - In the Configure Remote Password Reset page, enter `Admin` as the Administrator Account and save.

By following these steps, network defenders can effectively implement a secure password policy using ManageEngine Password Manager, ensuring the protection of sensitive information and privileged access management within the organization.