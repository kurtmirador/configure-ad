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

- Deployed and Configure Domain Controller in Azure
- Created Organizational Units and Domain Admin Accounts 
- Joined Client Machines to the Domain
- Configured Domain Users and Enable Remote Access

<h2>Deployment and Configuration Steps</h2>

<p>
<img width="1073" alt="Screenshot 2025-04-09 at 8 37 50 PM" src="https://github.com/user-attachments/assets/5a138ef8-6a64-42f1-9343-6bce1d9e1dd6" />
</p>
<p>
Provision a Windows Server VM (DC-1) in Azure, then install and configure Active Directory Domain Services (AD DS) to set up a new forest (e.g., mydomain.com).

✅ Key Actions:

- Log into DC-1

- Install AD DS role

- Promote DC-1 to Domain Controller

- Create new domain (e.g., mydomain.com)

- Restart and log in using domain credentials
</p>
<br />

<p>
<img width="1440" alt="Screenshot 2025-04-09 at 8 41 27 PM" src="https://github.com/user-attachments/assets/0dd65218-2d3b-49ec-ab07-6e0563bcc045" />
<img width="1440" alt="Screenshot 2025-04-09 at 8 48 11 PM" src="https://github.com/user-attachments/assets/d4fcff11-b948-4e43-a217-06f136013e85" />
</p>
<p>
Use Active Directory Users and Computers (ADUC) to create Organizational Units (OUs) and a new Domain Admin user account for administrative purposes.

✅ Key Actions:

- Create _EMPLOYEES and _ADMINS OUs

- Create jane_admin user and add to “Domain Admins” group

- Log in as mydomain.com\jane_admin for all admin tasks going forward
</p>
<br />

<p>
<img width="1440" alt="Screenshot 2025-04-09 at 8 53 03 PM" src="https://github.com/user-attachments/assets/fde96513-043e-4885-8e67-18065a8e015b" />
</p>
<p>
Configure the DNS settings of Client-1 in Azure and join it to the new domain.

✅ Key Actions:

- Set Client-1 DNS to DC-1’s private IP (already done)

- Restart Client-1

- Join Client-1 to the domain (mydomain.com)

- Move Client-1 into _CLIENTS OU in ADUC
</p>
<br />

<p>
<img width="1440" alt="Screenshot 2025-04-09 at 8 54 29 PM" src="https://github.com/user-attachments/assets/83bb5d0e-a84e-4738-8a3c-a77e1661cfbb" />
</p>
<p>
Set up domain user accounts and configure Remote Desktop access for non-admin users.

✅ Key Actions:

- Enable RDP access for “Domain Users” on Client-1

- Use PowerShell script on DC-1 to bulk-create user accounts in _EMPLOYEES OU

- Log into Client-1 with one of the created user accounts to verify domain login
</p>
<br />
