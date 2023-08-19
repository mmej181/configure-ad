
<h1>Configuring Active Directory</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>How to:</h2>
Install and Configure Active Directory


<h2>Environments and Technologies Used</h2>

- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>Stages</h2>

- Setup / Connect
- Install AD
- Create/Connect Admin/Users

<h2>Steps</h2>


<p>
<h2>Stage 1: Setup/Connect</h2>

Step 1: Create 2 VMs in Azure; The first is the Domain Controller on Windows Server and the other will be the Client VM  on Windows 10.

Step 2: Set the DC’s NIC Private IP address to static. Check that both VMs are on the same Vnet.

Step 3: From the Client VM, endless ping the DC VM’s private IP. Login to DC VM to enable ICMPv4 traffic in it’s Firewall. Check Client VM for successful ping.

</p>
<br />


<p>
<h2>Stage 2: Install AD</h2>

Step 4: In DC VM, using the Server Manager, install Active Directory Domain Services.

Step 5: Promote DC VM as a Domain Controller by setting up a ‘new forest’. 

Step 6: Restart DC VM and reconnect to it using the new user just created (new forest).

</p>
<br />


<p>
<h2>Stage 3: Create/Connect Admin/Users</h2>

Step 7: In ADUC (Active Directory Users and Computers) and create 2 OU’s (Organizational Unit), one called “Employees”, the second called “Admins”.

Step 8: Create a new user in Employees and add to the ‘Domain Admins’ Security Group. Log out of DC VM and log back in as this new user.

Step 9: Set Client VM’s DNS settings to the DC’s VM Private IP address; then restart Client VM. Log back into Client VM as admin and join it to the DC’s IP address. Drag Client VM into the OU named “Clients”.

Step 10: In Client VM, using your created user open up system properties. Allow ‘Domain Users’ access to remote desktop. 

Step 11: In DC VM, as your admin created user, open Powershell (as an administrator) to create additional users.

</p>
<br />
