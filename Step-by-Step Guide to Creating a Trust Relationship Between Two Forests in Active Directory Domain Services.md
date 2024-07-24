# Step-by-Step Guide to Creating a Trust Relationship Between Two Forests in Active Directory Domain Services

## Prerequisites
- Administrative privileges in both forests.
- DNS name resolution configured between both forests.
- Both forests operating at Windows Server 2003 forest functional level or higher.

## Steps to Create a Forest Trust

### 1. Prepare DNS Name Resolution

#### A. Configure Conditional Forwarders
1. Open the DNS Manager on the first forest (Forest A).
2. Right-click on `Conditional Forwarders` and select `New Conditional Forwarder`.
3. Enter the domain name of the second forest (Forest B).
4. Enter the IP addresses of the DNS servers in Forest B.
5. Repeat these steps on the DNS server in Forest B for Forest A.

#### B. Verify DNS Resolution
1. Use the `nslookup` command on a domain controller in Forest A to verify resolution of Forest B's domain and vice versa.

### 2. Open Active Directory Domains and Trusts

1. On a domain controller or a machine with RSAT tools installed, open `Active Directory Domains and Trusts`.
2. Right-click on the root domain of Forest A and select `Properties`.

### 3. Create the Trust

#### A. Configure Trust on Forest A
1. In the root domain properties of Forest A, go to the `Trusts` tab.
2. Click on `New Trust` to start the New Trust Wizard.
3. Click `Next` to continue.
4. Enter the DNS name of the root domain of Forest B and click `Next`.
5. Select `Forest trust` and click `Next`.
6. Choose `Two-way` or `One-way: incoming` or `One-way: outgoing` as needed and click `Next`.
7. Select `This domain only` or `Both this domain and the specified domain` as needed and click `Next`.
8. Enter the credentials for a user with administrative privileges in Forest B and click `Next`.
9. Select the trust authentication level: `Forest-wide authentication` or `Selective authentication`.
10. Review the settings and click `Next`.
11. Click `Finish` to create the trust.

#### B. Validate the Trust on Forest A
1. In the Trusts tab, select the trust you created.
2. Click `Properties`, then `Validate`.
3. Choose to validate for `Both sides of the trust` and enter the credentials for Forest B.
4. Confirm validation and ensure it completes successfully.

### 4. Configure the Trust on Forest B

1. Repeat steps 2 and 3 on a domain controller in Forest B, using the DNS name of the root domain of Forest A.
2. When specifying trust direction and credentials, ensure they match the settings configured on Forest A.

### 5. Verify Trust Relationship

1. In `Active Directory Domains and Trusts` on both Forests, right-click the root domain, go to the `Trusts` tab, and select `Properties`.
2. Validate the trust and ensure there are no errors.

### 6. Configure Selective Authentication (Optional)

If you chose `Selective authentication`, configure the permissions as follows:
1. Open `Active Directory Users and Computers`.
2. Navigate to the domain or OU where you want to grant access.
3. Right-click on the object and select `Properties`.
4. Go to the `Security` tab, and click `Add`.
5. Enter the names of the user or groups from the trusted forest and grant the appropriate permissions.

## Conclusion
By following these steps, you can create and verify a trust relationship between two forests in Active Directory Domain Services. Regular monitoring and updates ensure that the trust remains effective and up-to-date.
