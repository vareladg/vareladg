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


### 4. Group Policy Objects (GPOs)
* To enforce security, I implemented a GPO to restrict access to the Control Panel for standard users.


<img width="1064" height="563" alt="image" src="https://github.com/user-attachments/assets/bd9d5cc4-267e-4b23-93ea-74afcefaffd9" />

* GPO configuration in the Domain Controller.


<img width="1470" height="923" alt="image" src="https://github.com/user-attachments/assets/2403a003-5958-494e-b6c4-0956b2a118e6" />

* Final result: User blocked from accessing system settings on the Windows 11 workstation.


### 5. User Management & Security - AD Password Reset
<img width="1468" height="923" alt="image" src="https://github.com/user-attachments/assets/d4e55a00-6fb8-4c4a-a674-a4166de3a470" />


* In this final phase, I simulated one of the most frequent scenarios in IT Support: a user forgetting their password or being locked out of their account.

* Simulated a common Help Desk ticket: a user forgotten password and account lockout.
* Performed a remote password reset on the Domain Controller, ensuring the "User must change password at next logon" flag was enabled to maintain security best practices.
* Verified the policy on the Windows 11 Client, where the system forced the user to establish new credentials before granting access.

<img width="405" height="462" alt="image" src="https://github.com/user-attachments/assets/f12705e9-aa5d-4c0d-a0e3-7d28d2c46798" />




🏁 Project Conclusion
* This lab demonstrates the end-to-end implementation of an Active Directory environment. By successfully configuring network infrastructure, domain services, and security policies, I have built a functional corporate environment that follows the Principle of Least Privilege and industry-standard identity management.
