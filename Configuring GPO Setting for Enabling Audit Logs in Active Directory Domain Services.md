# Configuring GPO Setting for Enabling Audit Logs in Active Directory Domain Services

## Prerequisites
- Ensure you have administrative privileges.
- Active Directory Domain Services and Group Policy Management Console (GPMC) are installed.

## Steps to Configure Audit Logs via GPO

### 1. Open Group Policy Management Console (GPMC)
1. Press `Windows + R` to open the Run dialog box.
2. Type `gpmc.msc` and press `Enter`.

### 2. Create a New GPO
1. In the GPMC, navigate to your domain.
2. Right-click on the `Group Policy Objects` folder and select `New`.
3. Enter a name for the new GPO (e.g., "Enable Audit Logs Policy") and click `OK`.

### 3. Edit the GPO
1. Right-click the newly created GPO and select `Edit`.
2. The Group Policy Management Editor will open.

### 4. Configure Audit Policy Settings

#### A. Audit Policy
1. Navigate to `Computer Configuration` > `Policies` > `Windows Settings` > `Security Settings` > `Local Policies` > `Audit Policy`.
2. Configure the following settings by double-clicking on each one and selecting `Success`, `Failure`, or both as needed:
    - **Audit account logon events**
    - **Audit account management**
    - **Audit directory service access**
    - **Audit logon events**
    - **Audit object access**
    - **Audit policy change**
    - **Audit privilege use**
    - **Audit process tracking**
    - **Audit system events**

#### B. Advanced Audit Policy Configuration
1. Navigate to `Computer Configuration` > `Policies` > `Windows Settings` > `Security Settings` > `Advanced Audit Policy Configuration` > `Audit Policies`.
2. Expand each category (e.g., `Account Logon`, `Account Management`, `Detailed Tracking`, etc.) and configure specific audit settings by double-clicking on each one and selecting `Configure the following audit events` and checking `Success`, `Failure`, or both as needed.

### 5. Link the GPO to an Organizational Unit (OU)
1. In the GPMC, navigate to the OU where you want to apply the GPO.
2. Right-click the OU and select `Link an Existing GPO`.
3. Choose the GPO you created (e.g., "Enable Audit Logs Policy") from the list and click `OK`.

## Conclusion
By following these steps, you can configure and apply a GPO to enable audit logs in Active Directory Domain Services. Regular monitoring and updates ensure that the audit policies are effective and up-to-date.
