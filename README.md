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
-  Sign in to Client-1 using one of the newly-created user accounts

<h2>Deployment and Configuration Steps</h2>

<p>
<img src="https://i.imgur.com/nphDZTr.jpg" height="70%" width="70%"/>
</p>

<p>
<img src="https://i.imgur.com/A5MKfqD.jpg" height="70%" width="70%"/>
</p>
<p>
I began by creating 2 virtual machines in VMWare Workstation. This first machine (named "DC-1") will be running Windows Server 2022, and it will serve as the domain controller running Active Directory. The other machine (named "Client-1") will be running Windows 10, and I'll be joining it to the domain created on DC-1 later on in the lab.
</p>
<br />

<p>
<img src="https://i.imgur.com/Zo1R5Rm.jpg" height="70%" width="70%"/>
</p>

<p>
<img src="https://i.imgur.com/OZGRWbU.jpg" height="70%" width="70%"/>
</p>
<p>
As you can see in the diagram, I have to assign DC-1 a static IP address in order to allow Client-1 to join the domain. This is because domain controllers also act as DNS servers for their clients. When a domain is created, it's assigned a unique domain name (I'll be naming DC-1's domain "mydomain.com"). If Client-1's DNS server has no record of mydomain.com, there's no way to join the domain. A computer can't join a domain if it doesn't know that domain exists! (I know this is confusing, but it should become more clear as we go through the lab).
</p>
<br />

<p>
<img src="https://i.imgur.com/D5J8tPm.jpg" height="70%" width="70%"/>
</p>

<p>
<img src="https://i.imgur.com/Xdil2Tt.jpg" height="70%" width="70%"/>
</p>

<p>
<img src="https://i.imgur.com/V8oEJTx.jpg" height="70%" width="70%"/>
</p>
<p>
With DC-1 and Client-1 both on, I opened Client-1's command prompt and continuously pinged DC-1's private IP address to test connectivity. The requests were timing out, so I opened Windows Defender Firewall in DC-1 and enabled inbound Core Networking Diagnostics (ICMPv4 protocol). This allowed DC-1 to receive ICMP traffic, and as a result the ping succeeded, confirming connectivity between the two machines.
</p>
<br />

<p>
<img src="https://i.imgur.com/BGxgzEG.jpg" height="70%" width="70%"/>
</p>

<p>
<img src="https://i.imgur.com/UUjsOec.jpg" height="70%" width="70%"/>
</p>
<p>
In DC-1, I installed Active Directory Domain Services (AD DS) from the Server Manager Dashboard. Once AD DS was installed, I promoted DC-1 to a domain controller, allowing it to manage accounts and devices on the domain. I named the new domain "mydomain.com" for the sake of simplicity.
</p>
<br />

<p>
<img src="https://i.imgur.com/k5vtn0r.jpg" height="70%" width="70%"/>
</p>
<p>
With Active Directory Domain Services installed, I opened Active Directory Users and Computers (ADUC) and created two organizational units (OUs) and a user account. I named the OUs "_ADMINS" and "_EMPLOYEES", and the new user was “Ryan Mallory”. Ryan was going to be an administrator, so I created the account inside the _ADMINS OU and made him a member of the Domain Admins group, giving the account administrative privilege. I logged out of the default account and logged back in as Ryan.
</p>
<br />

<p>
<img src="https://i.imgur.com/e4V47ms.jpg" height="70%" width="70%"/>
</p>

<p>
<img src="https://i.imgur.com/lGFZIa6.jpg" height="70%" width="70%"/>
</p>
<p>
Now that DC-1 was promoted to a domain controller, it now had the option to act as a DNS server. This would allow Client-1 to set DC-1's private IP address as its default DNS server, allowing Client-1 to join the domain. It's necessary for DC-1 to act as Client-1's DNS server because DC-1 is the only DNS server that has an existing record of mydomain.com. 
<br />

<p>
<img src="https://i.imgur.com/x5DMCsZ.jpg" height="70%" width="70%"/>
</p>
<p>
The last step in setting up the domain was creating more users, and I accomplished this generating 1,000 randomly-named user accounts using a PowerShell script. All of the accounts were placed into the _EMPLOYEES OU.
</p>
<br />

<p>
<img src="https://i.imgur.com/hwZQCM0.jpg" height="70%" width="70%"/>
</p>

<p>
<img src="https://i.imgur.com/JGasb0S.jpg" height="70%" width="70%"/>
</p>
<p>
In order to test if the newly-created user accounts were functional, I picked a random "employee" from the _EMPLOYEES OU and used that account to login to Client-1. The login was successful, and I used the hostname and whoami commands to confirm the account identity.
</p>
<br />
