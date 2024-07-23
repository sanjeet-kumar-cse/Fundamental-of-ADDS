# Step-by-Step Guide to Deploy a Domain Controller on Azure VM

## Prerequisites
- An active Azure subscription
- Appropriate permissions to create resources in Azure

## Step 1: Create an Azure Virtual Machine

1. Log in to the [Azure Portal](https://portal.azure.com/).
2. In the left-hand menu, click on "Virtual machines".
3. Click on the "Add" button and then select "Virtual machine".
4. Fill in the necessary fields under the "Basics" tab:
   - **Subscription**: Select your Azure subscription.
   - **Resource group**: Create a new resource group or select an existing one.
   - **Virtual machine name**: Enter a name for your VM.
   - **Region**: Choose the region closest to you or your users.
   - **Image**: Select `Windows Server 2019 Datacenter` (or any suitable Windows Server version).
   - **Size**: Choose an appropriate VM size based on your requirements.
   - **Username**: Enter a username for the VM admin account.
   - **Password**: Enter and confirm a strong password.

5. Click on the "Next: Disks" button at the bottom.

## Step 2: Configure Disks

1. Under the "Disks" tab, choose the disk options based on your requirements. For most setups, the default options should suffice.
2. Click on the "Next: Networking" button.

## Step 3: Configure Networking

1. Under the "Networking" tab, configure the network settings:
   - **Virtual network**: Create a new virtual network or select an existing one.
   - **Subnet**: Select the default subnet or create a new one.
   - **Public IP**: Choose to create a new public IP.
   - **NIC network security group**: Select "Basic" and ensure RDP (3389) is allowed for admin access.

2. Click on the "Next: Management" button.

## Step 4: Configure Management Settings

1. Configure the management settings as per your requirements. For a basic setup:
   - **Boot diagnostics**: Enable with managed storage account.
   - **Auto-shutdown**: Enable if desired and set a shutdown time.
   - **Backup**: Configure if required.

2. Click on the "Next: Advanced" button.

## Step 5: Configure Advanced Settings

1. Configure any advanced settings if required. For most setups, you can leave the defaults.
2. Click on the "Next: Tags" button.

## Step 6: Add Tags (Optional)

1. Add any necessary tags to organize your resources.
2. Click on the "Next: Review + create" button.

## Step 7: Review and Create the VM

1. Review all the settings and ensure everything is configured correctly.
2. Click on the "Create" button to start the deployment.

## Step 8: Connect to the Virtual Machine

1. Once the VM is deployed,
