# Linux Processes & Kernel Troubleshooting Lab (Ubuntu VM)

## Project Overview
This lab demonstrates a systematic approach to diagnosing and resolving performance and process-related issues within a Linux environment. By leveraging CLI tools and system logs, I simulated a real-world troubleshooting workflow to monitor CPU/memory usage, identify problematic processes, and analyze system and kernel errors safely.

## Scenario
As an IT Support Technician, I investigated performance degradation on an Ubuntu virtual machine. The goal was to identify processes consuming excessive resources, analyze logs for errors, differentiate between user space and kernel processes, and apply safe solutions without impacting system stability.

## Tools Used
* **ps, top:** Process monitoring and resource utilization analysis.  
* **kill, renice:** Process termination and priority adjustment.  
* **journalctl, dmesg:** System and kernel log analysis.  
* **stress, sleep:** Simulated high CPU and memory usage.

## Technical Implementation Steps

### 1. Simulate Problematic Processes
To mimic a real-world performance issue, I created processes that consume CPU and memory.
* **Commands:**
```bash
stress --cpu 1 --timeout 60 &
sleep 1000 &
kill -9 999999
```

* **Observation:** 
  * `stress` and `sleep` simulated resource-intensive applications.
  * The `kill -9 999999` command on a nonexistent PID generated a safe log error for troubleshooting practice.
  * This allowed me to observe system behavior when a user process fails without affecting critical kernel processes.

### 2. Monitor System Resources
Using `top`, I observed all running processes and their CPU/memory consumption.
* **Command:** `top`
* **Observation:** 
  * Identified resource-heavy processes.
  * Differentiated between **user space processes** (`sleep`, `stress`) and **kernel processes** (root-owned, essential for system stability).
  * Noted how system performance was affected by CPU and memory usage of specific processes.

<img width="1405" height="575" alt="image" src="https://github.com/user-attachments/assets/fc56c96a-9b6a-45cf-80f7-89c3079cab66" />


### 3. Review System Logs
Analyzed recent logs to detect errors or warnings.
* **Commands:**
```bash
journalctl --since "5 minutes ago" | grep -i error
sudo dmesg | tail -n 20
```

* **Observation:** 
  * Detected simulated errors from process termination.
  * Kernel warnings were observed but did not affect overall system stability.
  * Learned to prioritize critical `error` messages while monitoring non-critical `warning` messages.
 
<img width="1405" height="891" alt="image" src="https://github.com/user-attachments/assets/00ebff24-6851-417d-ab5d-1a1b8f54caa6" />


### 4. Apply Troubleshooting Actions
Depending on the observations, I applied safe solutions:
* **Adjust process priority:**
```bash
sudo renice -n 10 -p 7386
```

* **Terminate non-critical processes:**
```bash
kill 7386
```

* **Observation:** 
  * CPU and memory utilization stabilized.
  * No kernel or system processes were affected.
  * Troubleshooting restored normal system operation while maintaining safety.
 
<img width="1405" height="362" alt="image" src="https://github.com/user-attachments/assets/e3c6e871-b2b1-434d-8f10-8a95b5f8eccc" />


### 🏁 Key Takeaways
* **Systematic Troubleshooting:** Followed a structured approach to identify, isolate, and resolve resource-intensive processes.  
* **User vs Kernel Processes:** Differentiated between processes that can be safely modified and critical kernel processes that must remain untouched.  
* **Log Analysis:** Learned to interpret system and kernel logs to prioritize actions.  
* **Safe Resolution:** Applied solutions that restored system performance without impacting overall stability.  
* **Professional Documentation:** Logged troubleshooting steps in a clear, reproducible format suitable for incident reports or CV portfolio.

