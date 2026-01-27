# Windows Server 2022 & Active Directory Infrastructure Lab

## Project Overview
This project involved the end-to-end deployment of a Windows Server 2022 environment as a Domain Controller. The goal was to simulate a corporate infrastructure to manage users, groups, and security policies (GPOs) while automating tasks with PowerShell.

## Scenario
As a Junior System Administrator, I built a secure and organized network domain. This involved setting up the server, joining client workstations to the domain, and implementing the Principle of Least Privilege through Organizational Units (OUs).

## Tools & Environment
* **Hypervisor:** VMware Fusion Pro and UTM
* **Operating Systems:** Windows Server 2022 (Domain Controller), Windows 11 Pro (Client Workstation)
* **Networking:** Internal Virtual Network with Static IP configuration
* **Scripting:** PowerShell

## Technical Implementation Steps

### 1. Server Deployment & Domain Configuration
<img width="1470" height="762" alt="image" src="https://github.com/user-attachments/assets/6f6ca7ed-2fad-4de8-ab22-1e710c836a6f" />

* Installed **Windows Server 2022** on UTM.
* Configured the server as a **Domain Controller** (DC) by installing Active Directory Domain Services (AD DS).
* Established a custom forest/domain.


### 2. Networking & Client Integration
<img width="312" height="355" alt="image" src="https://github.com/user-attachments/assets/d99bd2d2-2602-4e89-88ca-bf717889907f" />

* Configured static IP addresses for the DC and set the Windows 11 Client's DNS to point to the DC.
* Successfully **attached a Windows 11 VM to the domain**, verifying connectivity and DNS resolution.


### 3. OU Structure & User Management
<img width="753" height="529" alt="image" src="https://github.com/user-attachments/assets/a53683ac-7930-4bc8-8698-1ce4b449af5b" />


* Designed a logical **Organizational Unit (OU)** structure (Customer Service, Sales, IT).
* Created security groups to manage file permissions and access control.
* Managed the user lifecycle, including **creating domain users** and performing **password resets**.


### 4. Group Policy Objects (GPOs)
* To enforce security, I implemented a GPO to restrict access to the Control Panel for standard users.


<img width="1064" height="563" alt="image" src="https://github.com/user-attachments/assets/bd9d5cc4-267e-4b23-93ea-74afcefaffd9" />

* GPO configuration in the Domain Controller.


<img width="1470" height="923" alt="image" src="https://github.com/user-attachments/assets/2403a003-5958-494e-b6c4-0956b2a118e6" />

* Final result: User blocked from accessing system settings on the Windows 11 workstation.


### 5. Automation with PowerShell
* Used **PowerShell** to streamline administrative tasks, such as bulk user creation and system audits.

```powershell
# Example: PowerShell command to create a new AD User
New-ADUser -Name "John Doe" -SamAccountName "jdoe" -UserPrincipalName "jdoe@mydomain.local" -Path "OU=Users,DC=mydomain,DC=local" -Enabled $true
