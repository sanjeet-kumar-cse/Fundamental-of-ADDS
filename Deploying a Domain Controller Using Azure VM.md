# Deploying a Domain Controller Using Azure VM

## Prerequisites
- An active Azure subscription
- Basic knowledge of Azure and Active Directory
- Azure portal access

## Steps

### 1. Create an Azure Virtual Machine

1. **Log in to the Azure Portal**
   - Navigate to [Azure Portal](https://portal.azure.com) and log in with your credentials.

2. **Create a New Virtual Machine**
   - Go to "Virtual Machines" and click "Create" > "Azure virtual machine".
   - Fill in the following details:
     - **Subscription**: Select your subscription.
     - **Resource Group**: Create a new one or select an existing one.
     - **Virtual Machine Name**: Provide a name for your VM (e.g., `DC-VM`).
     - **Region**: Choose the appropriate region.
     - **Image**: Select `Windows Server 2019 Datacenter` or later.
     - **Size**: Choose a suitable size (e.g., `Standard DS1 v2`).
     - **Username**: Enter a username for the VM.
     - **Password**: Create a strong password.

3. **Configure Networking**
   - **Virtual Network**: Create a new virtual network or use an existing one.
   - **Subnet**: Create a new subnet or use an existing one.
   - **Public IP**: Assign a new public IP address.
   - **NIC Network Security Group**: Select Basic and ensure RDP (port 3389) is allowed.

4. **Review and Create**
   - Review the VM configuration.
   - Click "Create" to deploy the VM.

### 2. Configure the Virtual Machine

1. **Connect to the VM**
   - Once the VM is deployed, go to the VM's overview page in the Azure portal.
   - Click on "Connect" and download the RDP file.
   - Open the RDP file and connect to the VM using the username and password created earlier.

2. **Install Active Directory Domain Services (AD DS)**
   - Open `Server Manager`.
   - Click on "Add roles and features".
   - In the wizard, click "Next" until you reach the "Server Roles" page.
   - Select "Active Directory Domain Services" and click "Next".
   - Click "Add Features" when prompted, then "Next".
   - Proceed through the wizard and click "Install".

3. **Promote the Server to a Domain Controller**
   - After the installation, a notification will appear in Server Manager. Click on it and select "Promote this server to a domain controller".
   - In the Deployment Configuration tab, select "Add a new forest" and enter a root domain name (e.g., `example.com`).
   - Click "Next" and set the Forest and Domain functional levels to `Windows Server 2016` or higher.
   - Enter a Directory Services Restore Mode (DSRM) password and click "Next".
   - Continue through the wizard, reviewing and configuring settings as needed.
   - Click "Install". The server will automatically restart after the promotion.

### 3. Post-Deployment Configuration

1. **Verify Domain Controller Installation**
   - After the restart, log in to the VM using the domain credentials.
   - Open `Server Manager` and ensure the AD DS role is installed and functioning.

2. **Configure DNS Settings**
   - Open `Server Manager`.
   - Navigate to "DNS" and ensure that the VM's IP address is listed as the DNS server.

3. **Create Additional Domain Controllers (Optional)**
   - If needed, repeat the steps above to create additional domain controllers for redundancy and load balancing.

### 4. Secure the Domain Controller

1. **Configure Network Security Group (NSG) Rules**
   - In the Azure portal, navigate to your VM's network interface.
   - Go to the "Networking" tab and configure NSG rules to allow only necessary traffic (e.g., RDP, DNS).
   - Restrict inbound traffic to only required ports and IP ranges.

2. **Set Up Regular Backups**
   - Configure Azure Backup for the VM to ensure regular backups of your domain controller.
   - In the Azure portal, go to "Recovery Services vaults" and create a new vault if one doesn't exist.
   - Set up a backup policy and associate it with your VM.

### 5. Ongoing Maintenance and Monitoring

1. **Monitor the Domain Controller**
   - Regularly check the health and performance of your domain controller using Server Manager and Azure Monitor.
   - Set up alerts in Azure Monitor for critical events and performance metrics.

2. **Apply Updates and Patches**
   - Regularly apply Windows updates and security patches to your domain controller.
   - Schedule maintenance windows to minimize disruption.

## Conclusion

By following these detailed steps, you have successfully deployed a Domain Controller on an Azure VM. Regular maintenance and monitoring will ensure the security and performance of your Domain Controller.

