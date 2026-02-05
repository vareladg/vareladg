# Windows Desktop Support & System Administration Lab

## Project Overview
This project documents a series of real-world troubleshooting scenarios encountered by IT Support Technicians in a Windows enterprise environment. The lab focuses on diagnosing and resolving issues related to operating system services, network connectivity, and Microsoft 365 application stability.

## Scenarios Covered
1. **Windows Services Management:** Resolving printer connectivity by managing the Print Spooler service.
2. **Network Troubleshooting:** Diagnosing static IP conflicts and DNS resolution failures.
3. **Microsoft 365 Support:** Troubleshooting Outlook application failures through profile management and credential clearing.

## Tools & Commands Used
* **Services.msc:** Service lifecycle management (Automatic vs. Manual).
* **Event Viewer:** Log analysis for application and system errors.
* **CLI Tools:** `ipconfig`, `ping`, `nslookup`.
* **Credential Manager:** Managing cached Windows and Office identities.

## Technical Implementation

### 1. Print Spooler Service Recovery
* **Problem:** User unable to print; printer not appearing in the system.
* **Diagnosis:** Identified that the "Print Spooler" service was set to "Disabled."
* **Resolution:** * Changed the Startup Type to **Automatic**.
  * Started the service manually to restore immediate functionality.
  * Verified persistent fix after system reboot.
 
<img width="1470" height="338" alt="image" src="https://github.com/user-attachments/assets/72f8d8f5-5f80-4b58-a1f5-e38533e50b9b" />


### 2. Network Connectivity & DNS Repair
* **Problem:** No internet access; "Destination Host Unreachable" or DNS resolution failures.

<img width="795" height="318" alt="image" src="https://github.com/user-attachments/assets/94c3e784-3123-4171-8acd-efba0c036df5" />


* **Diagnosis:** Used `ipconfig /all` to identify an incorrect static IP configuration and unreachable gateway.

<img width="794" height="551" alt="image" src="https://github.com/user-attachments/assets/0b5806e5-3110-4200-b141-0ba3da6fc3e6" />


* **Resolution:**
  1. Reverted interface to **DHCP** for dynamic addressing.

<img width="523" height="626" alt="image" src="https://github.com/user-attachments/assets/195b5b22-c0da-4f00-b97b-773119b3dd14" />

  2. Executed `ipconfig /release` and `ipconfig /renew`.

<img width="629" height="479" alt="image" src="https://github.com/user-attachments/assets/bc74d705-a3f9-4f81-8585-e3cac82cea43" />

  3. Performed `ipconfig /flushdns` to clear corrupted DNS cache.

<img width="440" height="178" alt="image" src="https://github.com/user-attachments/assets/1d474e37-1b80-4dbb-95d5-36dd34f71b1c" />

 
### 3. Microsoft 365 / Outlook Troubleshooting
* **Problem:** Outlook stuck on "Loading Profile" or repeated password prompts.
* **Diagnosis:** Confirmed webmail (OWA) functionality to isolate the issue to the local desktop client.
* **Resolution:**
  * Created a **New Outlook Profile** via Control Panel > Mail to bypass data corruption.
  * Cleared obsolete identities in **Windows Credential Manager** to resolve authentication loops.
 
Note: Since this environment uses a Windows Server Domain Controller and New Outlook (v11), troubleshooting was performed via App Advanced Options (Repair/Reset) and Windows Credential Manager, as these are the modern standard for M365 desktop support.

<img width="1014" height="688" alt="image" src="https://github.com/user-attachments/assets/82cd667e-85db-4292-a967-e8bade611b8e" />


## Key Takeaways
* **Issue Isolation:** Demonstrated the ability to determine if a fault is local (App), network-based, or account-based (Cloud).
* **Systematic Resolution:** Applied the "bottom-up" troubleshooting model (Physical > Logical > Application).
* **Service Stability:** Understood the importance of service startup types for long-term system reliability.
