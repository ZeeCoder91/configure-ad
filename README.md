<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Deployment and Configuration Steps</h2>

<p>
Create the Domain Controller VM (Windows Server 2022) named “DC-1”. Take note of the Resource Group and Virtual Network (Vnet) that gets created on the Networking tab:
</p>
<p>
<img src="https://i.imgur.com/X13KZeX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/UVyFFo5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Create the Client VM (Windows 10) named “Client-1”. Use the same Resource Group and Vnet that was created in Step 1.a</p>
<p>
<img src="https://i.imgur.com/qrOzNVX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Ensure that both VMs are in the same Vnet (you can check the topology with Network Watcher
</p>
<p>
<img src="https://i.imgur.com/YEGgTRc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Set Domain Controller’s NIC Private IP address to be static
</p>
<p>
<img src="https://i.imgur.com/tupvfne.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<img src="https://i.imgur.com/mmKQFjf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Ensure that both VMs are in the same Vnet (you can check the topology with Network Watcher</p>
<p>
<p>
<img src="https://i.imgur.com/fLDkjmY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Login to Client-1 with Remote Desktop and ping DC-1’s private IP address with ping -t <ip address> (perpetual ping)
</p>
<p>
<img src="https://i.imgur.com/03WouCC.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/jVcfPRh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Login to the Domain Controller and enable ICMPv4 in on the local windows Firewall
</p>
<p>
<img src="https://i.imgur.com/zA0UP12.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/sB8hY5h.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/njD8aUF.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Check back at Client-1 to see the ping succeed
</p>
<p>
<img src="https://i.imgur.com/cl0shz2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Login to DC-1 and install Active Directory Domain Services
</p>
<p>
<img src="https://i.imgur.com/ElzTafx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/LkGxrEI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/ql4qfbU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/udWfDcx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/df6fHjW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Promote as a DC: Setup a new forest as mydomain.com (can be anything, just remember what it is)
</p>
<p>
<img src="https://i.imgur.com/W7RJvCG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />


<p>
<img src="https://i.imgur.com/6PSTsuz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/xGThr9l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/DAr4xMD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/uD1gwIT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/tMDqmDA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Install and close. Then, restart and log back into DC-1 as user: mydomain.com\labuser
</p>
<p>
<img src="https://i.imgur.com/CtwaMHm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
In Active Directory Users and Computers (ADUC)
</p>
<p>
<img src="https://i.imgur.com/I8Osj7F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Create an Organizational Unit (OU) called “_EMPLOYEES"</p>
<p>
<img src="https://i.imgur.com/6PJW4Cl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/6UQOCkA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Then create a new OU named “_ADMINS”</p>
<p>
<img src="https://i.imgur.com/DmONrTN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/u6ZCKq3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Create a new employee named “Jane Doe” (same password) with the username of “jane_admin”
</p>
<p>
<img src="https://i.imgur.com/MNR7gwb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/4r1yb8V.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/6QyvFwf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Add jane_doe to the “Domain Admins” Security Group
</p>
<p>
<img src="https://i.imgur.com/AUUmYXk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/IkRM5CO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/PYLxEvj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
From the Azure Portal, set Client-1’s DNS settings to the DC’s Private IP address
</p>
<p>
<img src="https://i.imgur.com/hztYHCN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
From the Azure Portal, restart Client-1
</p>
<p>
<img src="https://i.imgur.com/VZyCt5Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Login to Client-1 (Remote Desktop) as the original local admin (labuser) and join it to the domain (computer will restart)
</p>
<p>
<img src="https://i.imgur.com/MhJcB00.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/X3XnauP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/6Vuqufm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/CfTaDkL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/VTJJuck.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/z5TZnSW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/Gdtc11H.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/iJERtrg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/w5jA9y7.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/hMLyEKM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/2g4gOiH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
