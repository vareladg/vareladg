# Linux System Administration: User Permissions & Access Control

## Project Overview
This laboratory focuses on **System Hardening** and **Identity & Access Management (IAM)** within an Ubuntu Linux environment. I implemented the **Principle of Least Privilege (PoLP)** to secure sensitive organizational data, ensuring that access is strictly controlled based on user roles.

## Scenario
The "Finance Department" requires a secure repository for sensitive documents. The security policy mandates:
1.  **Confidentiality:** Files must be invisible to non-finance employees.
2.  **Collaboration:** All members of the Finance team must be able to read and write to the directory.
3.  **Integrity:** The system must prevent unauthorized modification or deletion of data.

## Tools Used
* **Ubuntu Linux 24.04** (Enterprise OS)
* **Bash Shell** (Command Line Interface)
* **VMware Fusion** (Virtualization)

## Key Configuration Steps

### 1. Identity & Access Management (IAM)
I created a dedicated group structure to manage permissions efficiently rather than assigning rights to individual users.
* **Command:** `sudo groupadd finance_dept`
* **User Provisioning:** Created user `employee_juan` and added them to the group using `usermod -aG`.
* **Verification:** Confirmed group membership to ensure the user inherits the correct privileges.

<img width="1405" height="181" alt="image" src="https://github.com/user-attachments/assets/8d499238-3082-4aa9-97c6-fa57e41d5482" />


### 2. Directory Hardening & Ownership
I established a secure directory and transferred ownership from the root user to the specific department group.
* **Command:** `sudo chgrp finance_dept /finance_data`
* **Outcome:** The directory is now owned by the group, allowing for granular control.

### 3. Implementing Absolute Mode Permissions
I applied strict permission bits (**770**) to lock down the directory.
* **Command:** `sudo chmod 770 /finance_data`
* **Breakdown:**
    * **Owner (7):** Read, Write, Execute.
    * **Group (7):** Read, Write, Execute.
    * **Others (0):** **No Access** (This effectively "invisibilizes" the folder for unauthorized users).

<img width="1405" height="126" alt="image" src="https://github.com/user-attachments/assets/78899fa8-591d-45b8-ab2f-51076a90c775" />


## Security Verification (Audit)
To validate the configuration, I performed a penetration test from an unprivileged user account.
* **Test:** Attempted to access `/finance_data` as a standard user (non-finance).
* **Result:** The system blocked the attempt with a **"Permission Denied"** error, confirming the security controls are active.

<img width="1404" height="271" alt="image" src="https://github.com/user-attachments/assets/c891834f-dfcd-43f4-bf2d-1aa343c85536" />


## Key Takeaways
* **Access Control Lists (ACLs):** mastered the manipulation of standard Linux permissions (`rwx`).
* **Security Best Practices:** Applied the concept of "Least Privilege" effectively.
* **CLI Proficiency:** Managed system administration tasks entirely through the terminal.
