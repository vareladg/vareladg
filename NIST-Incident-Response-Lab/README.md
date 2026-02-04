# Incident Response & NIST Framework: Linux Security Breach

## Project Overview
This laboratory simulates a security incident on a Linux server to practice the **Incident Response Lifecycle** established by the **NIST SP 800-61** framework. The objective was to detect, analyze, contain, and eradicate a simulated "backdoor" attack, followed by system recovery.

## Scenario
The SOC team received an alert regarding unusual behavior on a production server. A standard user reported system slowness, and logs indicated unauthorized account creation. My role was to step in as the **Incident Responder**.

## Tools & Frameworks
* **NIST Incident Response Cycle:** (Preparation, Detection, Containment, Eradication, Recovery).
* **Linux CLI:** `ps`, `grep`, `kill`, `userdel`.
* **Environment:** Ubuntu Linux Server.

## The Incident Response Lifecycle (NIST)

### Phase 1: Detection & Analysis
* **Investigation:** I performed a system audit to identify anomalies.
* **Findings:**
    1.  Identified a suspicious process named `malicious_script.sh` running in the background.
    2.  Discovered an unauthorized user account named `hacker_backdoor` in the `/etc/passwd` file.
* **Classification:** Classified as a high-severity intrusion attempt (Unauthorized Access & Malicious Code Execution).

<img width="799" height="78" alt="image" src="https://github.com/user-attachments/assets/5c4c93ab-a1b8-487c-b0fd-d3fef5f86ddd" />

<img width="670" height="223" alt="image" src="https://github.com/user-attachments/assets/22ecb014-5cf1-4504-bc3f-28e25b0d102b" />

*(Evidence of the running malicious process and the rogue user account at the bottom: **hacker_backdoor**)*

### Phase 2: Containment, Eradication & Recovery
To prevent further damage, I executed the following remediation steps:
1.  **Containment:** Terminated the malicious process immediately using the `kill -9` command to stop execution.
2.  **Eradication:**
    * Removed the executable file `malicious_script.sh` from the filesystem.
    * Deleted the compromised account `hacker_backdoor` using `userdel` to cut off access.
3.  **Recovery:** Verified system integrity by running a final audit to ensure no traces remained.

<img width="809" height="334" alt="image" src="https://github.com/user-attachments/assets/5694f647-f808-45ce-bfac-5ca402cdacb3" />

*(Verification showing the process and user have been successfully removed)*

### Phase 3: Post-Incident Activity (Lessons Learned)
* **Root Cause:** Simulated lack of access controls allowing script execution.
* **Recommendations:**
    * Implement **Auditd** for real-time monitoring of user creation.
    * Restrict execution permissions in temporary directories.
    * Enforce stronger password policies for root access.

## Skills Demonstrated
* **Process Adherence:** Applying a formal framework (NIST) to a technical problem.
* **System Forensics:** Identifying processes and users via CLI.
* **Remediation:** Safely removing threats without affecting system stability.
