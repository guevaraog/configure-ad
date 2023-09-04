# configure-ad
<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Computer)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create a bunch of additional users and attempt to log into client-1 with one of the users

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/sLZeu3i.png" height="30%" width="30%" alt="Windows Server 2022 VM"/>
<img src="https://i.imgur.com/2e02u0b.png" height="30%" width="30%" alt="Windows 10 VM"/>
<br />
<img src="https://i.imgur.com/xoDq43i.png" height="40%" width="40%" alt="Static Setting"/>
<img src="https://i.imgur.com/b14EG9s.png" height="60%" width="60%" alt="Static setting ipconfig"/>
</p>
<p>
Create the Domain Controller VM (Windows Server 2022) named “DC-1”.
<br />
Take note of the Resource Group and Virtual Network (Vnet) that get created at this time.
<br />
Set Domain Controller’s NIC Private IP address to be static.
<br />
Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created.
<br />
Ensure that both VMs are in the same Vnet (you can check the topology with Network Watcher).
</p>
<br />

<p>
<img src="https://i.imgur.com/OCqXQ1c.png" height="40%" width="40%" alt="Virtual Machines"/>
<br />
<img src="https://i.imgur.com/IDjt3do.png" height="20%" width="20%" alt="Ping timed out"/>
<br />
<img src="https://i.imgur.com/dKNlOF8.png" height="40%" width="40%" alt="Windows Defender Firewall"/>
<br />
<img src="https://i.imgur.com/5bzuAN8.png" height="70%" width="70%" alt="Core networking diagnostics"/>
<br />
<img src="https://i.imgur.com/Njhi0eO.png" height="70%" width="70%" alt="Core networking diagnostics with permissions"/>
<br />
<img src="https://i.imgur.com/L4H0wT3.png" height="20%" width="20%" alt="Ping worked and is sending signal back"/>
</p>
<p>
Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping).
<br />
Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall.
<br />
Check back at Client-1 to see the ping succeed.
</p>
<br />

<p>
<img src="https://i.imgur.com/AgddVvs.png" height="30%" width="30%" alt="Select server roles"/>
<img src="https://i.imgur.com/LWw3zTD.png" height="30%" width="30%" alt="Deployment Configurations"/>
<br />
<img src="https://i.imgur.com/ObyB98g.png" height="30%" width="30%" alt="Users created"/>
</p>
<p>
Login to DC-1 and install Active Directory Domain Services.
<br />
Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is).
<br />
Restart and then log back into DC-1 as user: mydomain.com\your created username.
</p>
<br />

<p>
<img src="https://i.imgur.com/PIOv3hg.png" height="20%" width="20%" alt="_EMPLOYEES"/>
<img src="https://i.imgur.com/RmVMd2r.png" height="20%" width="20%" alt="_ADMINS"/>
<br />
<img src="https://i.imgur.com/0gnt6pR.png" height="20%" width="20%" alt="Jane Doe"/>
<img src="https://i.imgur.com/SmhtffS.png" height="30%" width="30%" alt="Active Directory Users and Computers"/>
<br />
<img src="https://i.imgur.com/AK1CU0n.png" height="5%" width="20%" alt="Domain Admins"/>
</p>
<p>
In Active Directory Users and Computers (ADUC), create an Organizational Unit (OU) called “_EMPLOYEES”.
<br />
Create a new OU named “_ADMINS”.
<br />
(The following name was used as an example of how to setup admin for real world purposes).
<br />
Create a new employee named “Jane Doe” (same password) with the username of “jane_admin”.
<br />
Add jane_admin to the “Domain Admins” Security Group.
<br />
Log out/close the Remote Desktop connection to DC-1 and log back in as “mydomain.com\jane_admin”.
<br />
Use jane_admin as your admin account from now on.
</p>
<br />

<p>
<img src="https://i.imgur.com/lZiQlDV.png" height="20%" width="20%" alt="DNS"/>
<img src="https://i.imgur.com/NAVeAHJ.png" height="20%" width="20%" alt="domain.com"/>
<br />
<img src="https://i.imgur.com/mVte3WQ.png" height="20%" width="20%" alt="mydomain.com"/>
</p>
<p>
From the Azure Portal, set Client-1’s DNS settings to the DC’s Private IP address.
<br />
From the Azure Portal, restart Client-1.
<br />
Login to Client-1 (Remote Desktop) as the original local admin (labuser) and join it to the domain (computer will restart).
<br />
Login to the Domain Controller (Remote Desktop) and verify Client-1 shows up in Active Directory Users and Computers (ADUC) inside the “Computers” container on the root of the domain.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
