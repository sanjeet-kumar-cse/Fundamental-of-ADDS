# Configuring GPO Setting for Removable Media in Active Directory Domain Services

## Prerequisites
- Ensure you have administrative privileges.
- Active Directory Domain Services and Group Policy Management Console (GPMC) are installed.

## Steps to Configure Removable Media via GPO

### 1. Open Group Policy Management Console (GPMC)
1. Press `Windows + R` to open the Run dialog box.
2. Type `gpmc.msc` and press `Enter`.

### 2. Create a New GPO
1. In the GPMC, navigate to your domain.
2. Right-click on the `Group Policy Objects` folder and select `New`.
3. Enter a name for the new GPO (e.g., "Removable Media Policy") and click `OK`.

### 3. Edit the GPO
1. Right-click the newly created GPO and select `Edit`.
2. The Group Policy Management Editor will open.

### 4. Configure Removable Media Settings

#### A. Deny Write Access to Removable Drives Not Protected by BitLocker
1. Navigate to `Computer Configuration` > `Policies` > `Administrative Templates` > `Windows Components` > `BitLocker Drive Encryption` > `Removable Data Drives`.
2. Double-click on `Deny write access to removable drives not protected by BitLocker`.
3. Set it to `Enabled`.
4. Click `Apply` and then `OK`.

#### B. Deny Write Access to Removable Drives
1. Navigate to `Computer Configuration` > `Policies` > `Administrative Templates` > `System` > `Removable Storage Access`.
2. Double-click on `Removable Disks: Deny write access`.
3. Set it to `Enabled`.
4. Click `Apply` and then `OK`.

#### C. Deny Execute Access to Removable Drives
1. Double-click on `Removable Disks: Deny execute access`.
2. Set it to `Enabled`.
3. Click `Apply` and then `OK`.

#### D. Deny Read Access to Removable Drives
1. Double-click on `Removable Disks: Deny read access`.
2. Set it to `Enabled`.
3. Click `Apply` and then `OK`.

#### E. All Removable Storage Classes: Deny All Access
1. Double-click on `All Removable Storage classes: Deny all access`.
2. Set it to `Enabled`.
3. Click `Apply` and then `OK`.

### 5. Link the GPO to an Organizational Unit (OU)
1. In the GPMC, navigate to the OU where you want to apply the GPO.
2. Right-click the OU and select `Link an Existing GPO`.
3. Choose the GPO you created (e.g., "Removable Media Policy") from the list and click `OK`.


## Conclusion
By following these steps, you can configure and apply a GPO to manage removable media in Active Directory Domain Services. Regular monitoring and updates ensure that the policies remain effective and up-to-date.
