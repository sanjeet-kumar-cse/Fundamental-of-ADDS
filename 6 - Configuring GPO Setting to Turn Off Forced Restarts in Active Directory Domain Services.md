# Configuring GPO Setting to Turn Off Forced Restarts in Active Directory Domain Services

## Prerequisites
- Ensure you have administrative privileges.
- Active Directory Domain Services and Group Policy Management Console (GPMC) are installed.

## Steps to Configure Turn Off Forced Restarts via GPO

### 1. Open Group Policy Management Console (GPMC)
1. Press `Windows + R` to open the Run dialog box.
2. Type `gpmc.msc` and press `Enter`.

### 2. Create a New GPO
1. In the GPMC, navigate to your domain.
2. Right-click on the `Group Policy Objects` folder and select `New`.
3. Enter a name for the new GPO (e.g., "Disable Forced Restarts Policy") and click `OK`.

### 3. Edit the GPO
1. Right-click the newly created GPO and select `Edit`.
2. The Group Policy Management Editor will open.

### 4. Configure Windows Update Settings

#### A. Turn Off Auto-Restart for Updates
1. Navigate to `Computer Configuration` > `Policies` > `Administrative Templates` > `Windows Components` > `Windows Update`.
2. Double-click on `No auto-restart with logged on users for scheduled automatic updates installations`.
3. Set it to `Enabled`.
4. Click `Apply` and then `OK`.

### 5. Configure Active Hours (Optional)
To further control when restarts can occur, you can configure Active Hours.

1. Navigate to `Computer Configuration` > `Policies` > `Administrative Templates` > `Windows Components` > `Windows Update`.
2. Double-click on `Turn off auto-restart for updates during active hours`.
3. Set it to `Enabled`.
4. Set the `Active Hours Start` and `Active Hours End` as desired.
5. Click `Apply` and then `OK`.

### 6. Link the GPO to an Organizational Unit (OU)
1. In the GPMC, navigate to the OU where you want to apply the GPO.
2. Right-click the OU and select `Link an Existing GPO`.
3. Choose the GPO you created (e.g., "Disable Forced Restarts Policy") from the list and click `OK`.


## Conclusion
By following these steps, you can configure and apply a GPO to turn off forced restarts after Windows updates in Active Directory Domain Services. Regular monitoring and updates ensure that the policies remain effective and up-to-date.
