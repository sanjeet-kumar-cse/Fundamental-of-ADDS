# Step-by-Step Guide to Connect Entra ID (Azure AD) to On-Premises AD DS

## Prerequisites
- Administrative access to both Azure AD and on-premises AD DS.
- Azure AD Connect installed on an on-premises server.
- Azure subscription with Azure AD.

## Steps to Connect Entra ID to On-Premises AD DS

### 1. Prepare On-Premises Environment

#### A. Ensure Network Connectivity
1. Verify that the server intended for Azure AD Connect can communicate with Azure AD over the internet.
2. Ensure that the on-premises AD DS domain controllers are reachable from the Azure AD Connect server.

#### B. Create a Service Account in On-Premises AD
1. Open `Active Directory Users and Computers`.
2. Create a new user (e.g., `ADConnect_Svc`) in an appropriate OU.
3. Set a strong password and configure the account to have password never expire.

### 2. Install Azure AD Connect

#### A. Download Azure AD Connect
1. Download the latest version of Azure AD Connect from the [Microsoft website](https://www.microsoft.com/en-us/download/details.aspx?id=47594).

#### B. Install Azure AD Connect
1. Run the Azure AD Connect installer on the on-premises server.
2. Choose `Express Settings` if you want a quick setup. For a more customized setup, select `Customize`.

### 3. Configure Azure AD Connect

#### A. Express Settings Configuration
1. For Express Settings, Azure AD Connect will configure synchronization using default settings.
2. Enter Azure AD global administrator credentials when prompted.
3. Enter the credentials for the on-premises AD DS service account created earlier.
4. Complete the setup wizard.

#### B. Custom Settings Configuration
1. Choose `Customize` during installation for more granular control.
2. Select `Password Hash Synchronization`, `Pass-through Authentication`, or `Federation` as per your requirements.
3. Enter Azure AD global administrator credentials.
4. Enter the credentials for the on-premises AD DS service account.
5. Select the on-premises domains/OU you want to synchronize.
6. Configure filtering options if needed.
7. Set up optional features like `Password Writeback`, `Azure AD App and Attribute Filtering`, `Exchange Hybrid Deployment`, etc.
8. Review the settings and complete the setup.

### 4. Verify Synchronization

#### A. Open Synchronization Service Manager
1. Open `Synchronization Service Manager` from the Start menu.
2. Go to the `Operations` tab and verify that synchronization has occurred successfully.

#### B. Check Synchronization in Azure AD
1. Log in to the Azure portal.
2. Navigate to `Azure Active Directory` > `Azure AD Connect`.
3. Verify the last synchronization status and ensure there are no errors.

### 5. Configure Additional Synchronization Options (Optional)

#### A. Password Writeback
1. In the Azure portal, navigate to `Azure Active Directory` > `Azure AD Connect`.
2. Click on `Manage Password Reset`.
3. Enable `Password Writeback`.

#### B. Device Writeback
1. Open the Azure AD Connect wizard again.
2. Select `Configure Device Options`.
3. Enable `Device Writeback`.

### 6. Monitor and Maintain Synchronization

#### A. Schedule Synchronization
1. By default, Azure AD Connect syncs every 30 minutes. You can manually trigger synchronization using:
    ```powershell
    Start-ADSyncSyncCycle -PolicyType Delta
    ```

#### B. Monitor Synchronization
1. Regularly check the synchronization status in the Azure portal and the Synchronization Service Manager.
2. Set up alerts and notifications for synchronization issues.

## Conclusion
By following these steps, you can connect Entra ID (Azure AD) to your on-premises AD DS, enabling a synchronized identity management solution. Regular monitoring and updates ensure the synchronization remains effective and up-to-date.
