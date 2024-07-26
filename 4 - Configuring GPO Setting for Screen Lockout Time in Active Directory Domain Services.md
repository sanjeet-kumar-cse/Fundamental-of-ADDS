# Configuring GPO Setting for Screen Lockout Time in Active Directory Domain Services

## Prerequisites
- Ensure you have administrative privileges.
- Active Directory Domain Services and Group Policy Management Console (GPMC) are installed.

## Steps to Configure Screen Lockout Time via GPO

### 1. Open Group Policy Management Console (GPMC)
1. Press `Windows + R` to open the Run dialog box.
2. Type `gpmc.msc` and press `Enter`.

### 2. Create a New GPO
1. In the GPMC, navigate to your domain.
2. Right-click on the `Group Policy Objects` folder and select `New`.
3. Enter a name for the new GPO (e.g., "Screen Lockout Policy") and click `OK`.

### 3. Edit the GPO
1. Right-click the newly created GPO and select `Edit`.
2. The Group Policy Management Editor will open.

### 4. Configure Screen Lockout Settings

#### A. Set the Screen Saver Timeout
1. Navigate to `User Configuration` > `Policies` > `Administrative Templates` > `Control Panel` > `Personalization`.
2. Double-click on `Screen saver timeout`.
3. Set it to `Enabled`.
4. In the `Options` section, specify the number of seconds of inactivity before the screen saver activates (e.g., 600 seconds for 10 minutes).
5. Click `Apply` and then `OK`.

#### B. Force Specific Screen Saver
1. Double-click on `Force specific screen saver`.
2. Set it to `Enabled`.
3. In the `Options` section, enter the path to the screen saver executable (e.g., `C:\Windows\System32\scrnsave.scr`).
4. Click `Apply` and then `OK`.

#### C. Password Protect the Screen Saver
1. Double-click on `Password protect the screen saver`.
2. Set it to `Enabled`.
3. Click `Apply` and then `OK`.

### 5. Link the GPO to an Organizational Unit (OU)
1. In the GPMC, navigate to the OU where you want to apply the GPO.
2. Right-click the OU and select `Link an Existing GPO`.
3. Choose the GPO you created (e.g., "Screen Lockout Policy") from the list and click `OK`.


## Conclusion
By following these steps, you can configure and apply a GPO to enforce a screen lockout time in Active Directory Domain Services. Regular monitoring and updates ensure that the policies remain effective and up-to-date.
