<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployed in the Cloud (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />


<!--- <h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com) --->

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Setup Resources in Azure
- Ensure Connectivity between the client and Domain Controller
- Install Active Directory
- Create an Admin and Normal User Account in AD
- Join Client-1 to your domain (mydomain.com)
- Setup Remote Desktop for non-administrative users on Client-1
- Create additional users and attempt to log into client-1 with one of the users


<h2>Deployment and Configuration Steps</h2>

<p>
Begin by setting up a new computer system named "DC-1" in Azure. This system will act as a manager for other computers in the network and runs on Windows Server 2022. It's important to note down the group and network paths it uses, found under the "Networking" section, because they help organize and connect everything efficiently.</p>
<p>
<img src="https://i.imgur.com/X13KZeX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/UVyFFo5.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Next, set up a user computer system called "Client-1" that runs Windows 10, using Azure. Make sure to place it in the same organizational group and network path you noted earlier. This helps keep the systems connected and organized.</p>
<p>
<img src="https://i.imgur.com/qrOzNVX.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Verify that both virtual machines (VMs) are connected within the same virtual network (Vnet).This step is crucial for ensuring that your systems can communicate seamlessly and are properly integrated within the same network environment.
</p>
<p>
<img src="https://i.imgur.com/YEGgTRc.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Configure the Domain Controller's network interface card (NIC) to use a static private IP address. This step is vital to maintain consistent network communication and avoid potential disruptions that could occur if the Domain Controller were to receive a new IP address dynamically. A static IP ensures that the Domain Controller is easily locatable by other devices on the network at all times.</p>
<p>
<img src="https://i.imgur.com/tupvfne.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<img src="https://i.imgur.com/mmKQFjf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Verify that both virtual machines (VMs) are located within the same virtual network (Vnet). You can confirm their network configuration by utilizing the Network Watcher's topology feature. This step is crucial for ensuring seamless communication between the VMs, as being on the same Vnet allows for direct network connections without the need for complex routing or additional network services.</p>
<p>
<p>
<img src="https://i.imgur.com/fLDkjmY.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h2>Network Connection Validation</h2>
<p>Ensure Client-1 can communicate with DC-1:</p>
<ol>
    <li>Access <strong>Client-1</strong> via Remote Desktop.</li>
    <li>Open command prompt.</li>
    <li>Type: <code>ping -t &lt;DC-1's IP&gt;</code> and press Enter.</li>
</ol>
<p>Continuous pinging tests the network connection stability between Client-1 and DC-1.</p>
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

<p>Click on Active Directory Domain Services</p>
<p>
<img src="https://i.imgur.com/ql4qfbU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Add the features</p>
<p>
<img src="https://i.imgur.com/udWfDcx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
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

<p>Set the Password (We won't be using it in this lab)</p>
<p>
<img src="https://i.imgur.com/6PSTsuz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Next</p>
<p>
<img src="https://i.imgur.com/xGThr9l.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Next</p>
<p>
<img src="https://i.imgur.com/DAr4xMD.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Next</p>
<p>
<img src="https://i.imgur.com/uD1gwIT.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Next</p>
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

<p>Create a new employee named “Jane Doe” (same password) with the username of “jane_admin”
</p>
<p>
<img src="https://i.imgur.com/u6ZCKq3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/MNR7gwb.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/4r1yb8V.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>A user account has been created for Jane Doe in the Admins Organizational Unit. But, we have to take additional steps to make this user an actual domain admin. We have to right click Jane Doe's account and click on Properties > Members Of
<p>
<img src="https://i.imgur.com/6QyvFwf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Click Add to add jane_admin to the “Domain Admins” Security Group
</p>
<p>
<img src="https://i.imgur.com/AUUmYXk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Type in 'Domain Admins' which is a built-in security group into the field. Click Ok.
<p>
<img src="https://i.imgur.com/IkRM5CO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Click apply and ok. Our user has now been added to the Domain Admins group.
<p>
<img src="https://i.imgur.com/PYLxEvj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>Join Client-1 to your domain (mydomain.com):</h3>
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
Login to the Domain Controller (Remote Desktop) and verify Client-1 shows up in Active Directory Users and Computers (ADUC) inside the “Computers” container on the root of the domain
</p>
<p>
<img src="https://i.imgur.com/X3XnauP.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
<img src="https://i.imgur.com/6Vuqufm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
Setup Remote Desktop for non-administrative users on Client-1
</p>
<p>
<img src="https://i.imgur.com/CfTaDkL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
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
