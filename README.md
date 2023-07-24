<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory Deployment in VMWare Workstation</h1>
This project outlines the implementation of on-premises Active Directory on a virtual machine running Windows Server 2022. Once this virtual machine is promoted to a domain controller, I join a Windows 10 client to the domain, and create 1,000 user accounts using a PowerShell script.<br />

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
-  Create 1,000 user accounts using a PowerShell script (run PowerShell ISE as administrator)
-  Sign in to Client-1 using one of the new user accounts

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/qdAuEyv.jpg" height="70%" width="70%"/>
</p>
<p>
I began by creating a virtual machine running Windows Server 2022 in VMWare Workstation. This machine will serve as the Active Directory domain controller in this lab. I'll be referring to this VM as "DC-1".
</p>
<br />

<p>
<img src="https://i.imgur.com/o59PNzr.jpg" height="70%" width="70%"/>
</p>
<p>
Next, I created a virtual machine running Windows 10 Pro. This VM will be used to join the Active Directory domain created on DC-1. I will refer to this VM as "Client-1".
</p>
<br />

<p>
<img src="https://i.imgur.com/OJVO0mj.jpg" height="70%" width="70%"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
