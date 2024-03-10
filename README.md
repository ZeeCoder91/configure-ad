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

<p>Enable ICMPv4 on the Domain Controller's Firewall:
<li>Log into the Domain Controller.</li>
<li>Access Windows Firewall settings.</li>
<li>Enable the ICMPv4 rule to allow incoming ping requests.</li>
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
Return to Client-1 to confirm that the ping operation was successful.
</p>
<p>
<img src="https://i.imgur.com/cl0shz2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Log into DC-1 and, using Server Manager, initiate the installation of Active Directory Domain Services by clicking "Add Roles and Features.</p>
<p>
<img src="https://i.imgur.com/ElzTafx.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/LkGxrEI.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Select "Active Directory Domain Services" from the options available.</p>
<p>
<img src="https://i.imgur.com/ql4qfbU.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Proceed to select and add the necessary features.</p>
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
Initiate the promotion to a Domain Controller by establishing a new forest, naming it "mydomain.com" (this can be any name; ensure it's memorable).</p>
<p>
<img src="https://i.imgur.com/W7RJvCG.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Choose a password for the Domain Administrator account. Note: This password won’t be needed for the current lab’s activities.</p>
<p>
<img src="https://i.imgur.com/6PSTsuz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Proceed by selecting the default options at each step.</p>
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
Install, then close the installer. Restart DC-1, and log back in using the credentials for user: mydomain.com\labuser</p>
<p>
<img src="https://i.imgur.com/CtwaMHm.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
In Active Directory Users and Computers(ADUC)
</p>
<p>
<img src="https://i.imgur.com/I8Osj7F.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Let's now introduce a structure to organize our directory. We'll start by creating an Organizational Unit (OU) named "_EMPLOYEES". This step helps in categorizing user accounts and managing them effectively. To do this, access the Active Directory Users and Computers console, right-click on your domain, select "New", and then "Organizational Unit". Input "_EMPLOYEES" as the name.</p>
<p>
<img src="https://i.imgur.com/6PJW4Cl.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/6UQOCkA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Next, we'll create a special folder for administrator accounts called "_ADMINS". This helps us keep things organized and secure. To do this, go to the Active Directory Users and Computers area, right-click on your domain, choose "New", then "Organizational Unit", and name it "_ADMINS".</p>
<p>
<img src="https://i.imgur.com/DmONrTN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Next, let's add a new team member named "Jane Doe" to our system. We'll give her the username "jane_admin" and set up her password. This step involves creating a user account for Jane in the Active Directory, ensuring she has the access she needs to perform her tasks.
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

<p>For Jane Doe to have domain admin privileges, her user account, located in the Admins Organizational Unit, requires additional configuration. Right-click on Jane Doe's account, select "Properties," then navigate to the "Members Of" tab to proceed with assigning her the necessary administrative roles.
<p>
<img src="https://i.imgur.com/6QyvFwf.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
To grant Jane Doe administrative rights, click "Add" under her account settings and include "jane_admin" in the "Domain Admins" security group.
</p>
<p>
<img src="https://i.imgur.com/AUUmYXk.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Enter "Domain Admins" into the designated field to add Jane Doe to this built-in security group, then click "OK."
<p>
<img src="https://i.imgur.com/IkRM5CO.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>Click "Apply" followed by "OK" to confirm the addition of our user to the Domain Admins group.
<p>
<img src="https://i.imgur.com/PYLxEvj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<h3>Join Client-1 to the domain by changing its settings to become a member of "mydomain.com"</h3>
<p>
In the Azure Portal, update Client-1's DNS settings to use the private IP address of your Domain Controller.
</p>
<p>
<img src="https://i.imgur.com/hztYHCN.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
In the Azure Portal, navigate to Client-1 and initiate a restart.
</p>
<p>
<img src="https://i.imgur.com/VZyCt5Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Log into Client-1 using Remote Desktop as the local admin (labuser), and connect it to the domain. The computer will need to restart afterward.</p>
<p>
<img src="https://i.imgur.com/MhJcB00.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Log into the Domain Controller using Remote Desktop, and in the Active Directory Users and Computers (ADUC) interface, check that Client-1 appears in the "Computers" container at the root of the domain.
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
Enable Remote Desktop access on Client-1 for non-administrative users.
</p>
<p>
<img src="https://i.imgur.com/CfTaDkL.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Grant remote desktop access to all domain users by adding them to the Remote Desktop Users group.</p>
<p>
<img src="https://i.imgur.com/VTJJuck.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
To execute the script provided by your instructor, start by launching PowerShell ISE with administrative privileges. Once open, create a new document within the ISE and copy the entire script content into this new file.</p>
<p>
<img src="https://i.imgur.com/z5TZnSW.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/Gdtc11H.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
Attempt to log into Client-1 using one of the account credentials provided (make sure to note the password from the script).
</p>
<p>
<img src="https://i.imgur.com/iJERtrg.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />

<p>
<img src="https://i.imgur.com/hMLyEKM.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />


<p>
<img src="https://i.imgur.com/2g4gOiH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<br />
