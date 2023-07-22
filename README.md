<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployment in VMWare Workstation</h1>
This project outlines the implementation of on-premises Active Directory on a virtual machine running Windows Server 2022. Once this virtual machine is promoted to a domain controller, I join a Windows 10 client to the domain, and create 1,000 user accounts using a PowerShell script.<br />


<h2>Video Demonstration</h2>

- ### [YouTube: How to Deploy on-premises Active Directory within Azure Compute](https://www.youtube.com)

<h2>Technologies Used</h2>

- VMWare Workstation (Virtual Machines)
- Active Directory Domain Services
- PowerShell ISE

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 Pro

<h2>High-Level Steps</h2>

- Create 2 virtual machines, one running Windows Server 2022 (named "DC-1", a.k.a the domain controller), and the other running Windows 10 Pro (named "Client-1")
-   Assign DC-1 a static IP address
-   Open Client-1's command prompt and perpetually ping (ping -t) DC-1's private IP address. Open Windows Defender Firewall on DC-1 and enable ICMPv4 Echo Request. Go back to Client-1's command prompt and observe the change
-   Install Active Directory Domain Services on DC-1 and promote it to a domain controller
-  Create an admin account and organizational units (OU) in Active Directory Users and Computers (ADUC), then login to DC-1 with the new admin account
-  Set Client-1's default DNS server to DC-1's private IP address, then join Client-1 to DC-1's domain
-  Create 1,000 users accounts using a PowerShell script (run PowerShell ISE as administrator)
-  Sign in to Client-1 using one of the new user accounts

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%"/>
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
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
