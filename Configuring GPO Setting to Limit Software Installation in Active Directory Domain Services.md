# Configuring GPO Setting to Limit Software Installation in Active Directory Domain Services

## Prerequisites
- Ensure you have administrative privileges.
- Active Directory Domain Services and Group Policy Management Console (GPMC) are installed.

## Steps to Configure Software Installation Restrictions via GPO

### 1. Open Group Policy Management Console (GPMC)
1. Press `Windows + R` to open the Run dialog box.
2. Type `gpmc.msc` and press `Enter`.

### 2. Create a New GPO
1. In the GPMC, navigate to your domain.
2. Right-click on the `Group Policy Objects` folder and select `New`.
3. Enter a name for the new GPO (e.g., "Limit Software Installation Policy") and click `OK`.

### 3. Edit the GPO
1. Right-click the newly created GPO and select `Edit`.
2. The Group Policy Management Editor will open.

### 4. Configure Software Restriction Policies

#### A. Set Up Software Restriction Policies
1. Navigate to `Computer Configuration` > `Policies` > `Windows Settings` > `Security Settings` > `Software Restriction Policies`.
2. Right-click `Software Restriction Policies` and select `New Software Restriction Policies`.

#### B. Define Default Security Level
1. In the `Software Restriction Policies` section, click on `Security Levels`.
2. Double-click on `Disallowed`.
3. Set it to `Default Security Level` to prevent all software from running unless explicitly allowed.
4. Click `Apply` and then `OK`.

#### C. Create Additional Rules to Allow Necessary Software
1. Under `Software Restriction Policies`, click `Additional Rules`.
2. Right-click in the pane and select `New Path Rule`.
3. Define rules for the paths of necessary software executables (e.g., `C:\Program Files`).
4. Set the security level to `Unrestricted` for these paths.
5. Click `Apply` and then `OK`.

### 5. Configure User Rights Assignment to Limit Software Installation

#### A. Configure User Rights Assignment
1. Navigate to `Computer Configuration` > `Policies` > `Windows Settings` > `Security Settings` > `Local Policies` > `User Rights Assignment`.
2. Double-click on `User Rights Assignment`.

#### B. Restrict `User Account Control: Run all administrators in Admin Approval Mode`
1. Navigate to `Computer Configuration` > `Policies` > `Windows Settings` > `Security Settings` > `Local Policies` > `Security Options`.
2. Double-click on `User Account Control: Run all administrators in Admin Approval Mode`.
3. Set it to `Enabled`.
4. Click `Apply` and then `OK`.

#### C. Define Software Restriction Policy Enforcement
1. Navigate to `Computer Configuration` > `Policies` > `Windows Settings` > `Security Settings` > `Software Restriction Policies` > `Enforcement`.
2. Double-click on `Enforcement`.
3. Select `All software files` and ensure `Apply software restriction policies to the following users:` is set to `All users except local administrators`.
4. Click `Apply` and then `OK`.

### 6. Link the GPO to an Organizational Unit (OU)
1. In the GPMC, navigate to the OU where you want to apply the GPO.
2. Right-click the OU and select `Link an Existing GPO`.
3. Choose the GPO you created (e.g., "Limit Software Installation Policy") from the list and click `OK`.

### 7. Verify GPO Application
1. Open Command Prompt on a client machine.
2. Run `gpupdate /force` to manually apply the policy.
3. Verify the settings by running `gpresult /r` to review the applied policies.

### 8. Monitor and Troubleshoot
1. Use Event Viewer to check for any Group Policy errors.
2. Navigate to `Event Viewer` > `Applications and Services Logs` > `Microsoft` > `Windows` > `GroupPolicy`.

## Conclusion
By following these steps, you can configure and apply a GPO to limit software installation in Active Directory Domain Services. Regular monitoring and updates ensure that the policies remain effective and up-to-date.
