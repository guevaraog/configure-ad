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
<br />
<img src="https://i.imgur.com/2e02u0b.png" height="30%" width="30%" alt="Windows 10 VM"/>
<br />
<img src="https://i.imgur.com/xoDq43i.png" height="40%" width="40%" alt="Static Setting"/>
<br />
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
<img src="https://i.imgur.com/OCqXQ1c.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/IDjt3do.png" height="20%" width="20%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/dKNlOF8.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/5bzuAN8.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/Njhi0eO.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<br />
<img src="https://i.imgur.com/L4H0wT3.png" height="20%" width="20%" alt="Disk Sanitization Steps"/>
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
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
