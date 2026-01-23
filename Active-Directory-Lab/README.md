# Windows Server 2022 & Active Directory Infrastructure Lab

## Project Overview
This project involved the end-to-end deployment of a Windows Server 2022 environment as a Domain Controller. The goal was to simulate a corporate infrastructure to manage users, groups, and security policies (GPOs) while automating tasks with PowerShell.

## Scenario
As a Junior System Administrator, I built a secure and organized network domain. This involved setting up the server, joining client workstations to the domain, and implementing the Principle of Least Privilege through Organizational Units (OUs).

## Tools & Environment
* **Hypervisor:** VirtualBox
* **Operating Systems:** Windows Server 2022 (Domain Controller), Windows 11 Pro (Client Workstation)
* **Networking:** Internal Virtual Network with Static IP configuration
* **Scripting:** PowerShell

## Technical Implementation Steps

### 1. Server Deployment & Domain Configuration
* Installed **Windows Server 2022** on VirtualBox.
* Configured the server as a **Domain Controller** (DC) by installing Active Directory Domain Services (AD DS).
* Established a custom forest/domain.

### 2. Networking & Client Integration
* Configured static IP addresses for the DC and set the Windows 11 Client's DNS to point to the DC.
* Successfully **attached a Windows 11 VM to the domain**, verifying connectivity and DNS resolution.

### 3. OU Structure & User Management
* Designed a logical **Organizational Unit (OU)** structure (Admins, Users, HR, IT).
* Created security groups to manage file permissions and access control.
* Managed the user lifecycle, including **creating domain users** and performing **password resets**.

### 4. Group Policy Objects (GPOs)
* Implemented GPOs to enforce security and desktop environments.
* *Example:* Disabling Control Panel access for standard users to prevent unauthorized system changes.

### 5. Automation with PowerShell
* Used **PowerShell** to streamline administrative tasks, such as bulk user creation and system audits.

```powershell
# Example: PowerShell command to create a new AD User
New-ADUser -Name "John Doe" -SamAccountName "jdoe" -UserPrincipalName "jdoe@mydomain.local" -Path "OU=Users,DC=mydomain,DC=local" -Enabled $true
