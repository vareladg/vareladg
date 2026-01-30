# Network Connectivity & Troubleshooting Lab (Windows 11 Client)

## Project Overview
This project demonstrates a systematic approach to diagnosing and resolving network connectivity issues within a Windows 11 environment. By utilizing Command Line Interface (CLI) tools, I simulated a real-world troubleshooting workflow to verify local configurations, test external reachability, and analyze DNS resolution.

## Scenario
As an IT Support Technician, I performed a network health check on a Windows 11 workstation connected to a virtualized environment. The goal was to ensure the client could communicate with both internal resources (Domain Controller) and external networks.

## Tools Used
* **Ipconfig:** Interface configuration and IP stack analysis.
* **Ping:** Connectivity and latency testing using ICMP.
* **Nslookup:** DNS query and name resolution diagnostics.
* **Tracert:** Path analysis and hop identification.

## Technical Implementation Steps

### 1. Local Interface Analysis
The first step was to verify that the Windows 11 client had a valid IP address and was correctly communicating with the DHCP server.
* **Command:** `ipconfig`
* **Observation:** Confirmed the IPv4 address, Subnet Mask, and Default Gateway. This ensures the Network Interface Card (NIC) is properly configured.

<img width="1469" height="341" alt="image" src="https://github.com/user-attachments/assets/6a72528b-c263-4c8e-9c8c-0e744597ca19" />


### 2. External Connectivity Test (Layer 3)
I tested the connection to an external reliable source to rule out issues with the local gateway or the Internet Service Provider (ISP).
* **Command:** `ping 8.8.8.8`
* **Observation:** Verified a 0% packet loss. This confirms that the machine has a clear path to the internet.

<img width="1470" height="339" alt="image" src="https://github.com/user-attachments/assets/45b25aa2-8e8b-412a-8fe0-f4df1bac4dcb" />


### 3. DNS Resolution Verification
After confirming IP connectivity, I verified if the workstation could translate domain names into IP addresses.
* **Command:** `nslookup google.com`
* **Observation:** The query successfully returned the IP addresses for Google, confirming that the DNS server (configured in the previous Active Directory lab) is resolving correctly.

<img width="1470" height="267" alt="image" src="https://github.com/user-attachments/assets/4e648856-a889-4d53-8a95-3d3bc91dc33b" />


### 4. Network Path Analysis (Tracing Hops)
To identify the specific route my data takes and detect any latency "bottlenecks," I performed a trace.
* **Command:** `tracert 8.8.8.8`
* **Observation:** Analyzed each hop from the virtual gateway to the destination. This is crucial for identifying if a failure point is local or at the ISP level.

<img width="1470" height="453" alt="image" src="https://github.com/user-attachments/assets/5acad1ce-78b3-4148-a48c-b32489401d16" />


🏁 Key Takeaways
* Systematic Isolation: I followed a "bottom-up" approach, starting from the local configuration (Layer 2/3) up to DNS resolution (Layer 7).
* Environment Validation: Confirmed that the Windows 11 client is fully integrated into the lab network with functional internet access.
* Technical Documentation: Demonstrated the ability to log and interpret network diagnostics for future incident reports.
