# Active Directory Domain Service Lab Setup

## Prerequisites
- **Virtualization Software**: Install Hyper-V, VMware, or VirtualBox.
- **ISO Files**: Windows Server and Windows Client ISO images.
- **Network Configuration**: Ensure network configurations allow communication between virtual machines.

## Step 1: Create Virtual Machines

### 1.1: Create Domain Controller (DC)
1. **Allocate Resources**: 
   - CPU: 2 Cores
   - RAM: 4 GB
   - Disk: 60 GB
2. **Install OS**: 
   - Mount Windows Server ISO and complete the installation.
   - Set a static IP address.
   - Rename the server (e.g., `DC1`).
3. **Promote to Domain Controller**:
   - Open Server Manager.
   - Add roles and features.
   - Select "Active Directory Domain Services" and install.
   - Promote the server to a domain controller.
     - Add a new forest (e.g., `example.local`).
     - Complete the wizard and reboot.

### 1.2: Create Domain-Joined Server
1. **Allocate Resources**: 
   - CPU: 2 Cores
   - RAM: 4 GB
   - Disk: 40 GB
2. **Install OS**: 
   - Mount Windows Server ISO and complete the installation.
   - Set a static IP address.
   - Rename the server (e.g., `MemberServer`).
3. **Join Domain**:
   - Open System Properties.
   - Change settings to join the domain (e.g., `example.local`).
   - Provide domain admin credentials and reboot.

### 1.3: Create Client Computer
1. **Allocate Resources**: 
   - CPU: 2 Cores
   - RAM: 2 GB
   - Disk: 40 GB
2. **Install OS**: 
   - Mount Windows Client ISO and complete the installation.
   - Set a static IP address.
   - Rename the client (e.g., `ClientPC`).
3. **Join Domain**:
   - Open System Properties.
   - Change settings to join the domain (e.g., `example.local`).
   - Provide domain admin credentials and reboot.

## Step 2: Configuration and Verification

### 2.1: Verify Domain Controller
1. **Check AD DS**:
   - Open Server Manager.
   - Verify AD DS and DNS roles are running.
2. **Create Users and Groups**:
   - Open Active Directory Users and Computers.
   - Create organizational units (OUs), users, and groups.

### 2.2: Verify Domain-Joined Server
1. **Check Domain Membership**:
   - Open System Properties.
   - Confirm the domain (e.g., `example.local`) is listed.
2. **Access AD DS**:
   - Open Active Directory Users and Computers.
   - Verify you can manage AD objects.

### 2.3: Verify Client Computer
1. **Check Domain Membership**:
   - Open System Properties.
   - Confirm the domain (e.g., `example.local`) is listed.
2. **Test User Login**:
   - Log in with a domain user account.
   - Ensure access to domain resources.

## Step 3: Final Adjustments

### 3.1: Configure Group Policies
1. **Open Group Policy Management**:
   - Create and link GPOs to OUs.
   - Configure policies as required.

### 3.2: Network and Security Settings
1. **Firewall Settings**:
   - Ensure firewalls allow necessary traffic.
2. **Update Systems**:
   - Install updates and patches on all systems.

### 3.3: Backup Configuration
1. **Backup AD DS**:
   - Schedule regular backups of the domain controller.

## Conclusion
Your AD DS lab setup is now complete with one domain controller, one domain-joined server, and one client computer. Ensure to regularly maintain and monitor your environment for optimal performance.
