# 🏢 Secure Corporate Network Infrastructure Implementation

## 📌 Project Overview
This project documents the design and deployment of a scalable network infrastructure for a simulated corporate environment. The primary objective was to move beyond simple connectivity to create a **managed and secure network**. 

This implementation demonstrates the ability to segment traffic, automate IP addressing to reduce administrative overhead, and implement **Access Control Lists (ACLs)** to enforce security policies.

### **Key Competencies Demonstrated**
* **Network Segmentation:** Logical separation of user and server traffic to improve performance and security.
* **Infrastructure Services:** Deployment of DHCP and DNS services for endpoint automation.
* **Perimeter Security:** Hardening the network edge using Standard ACLs to filter unauthorized traffic.
* **Protocol Analysis:** Deep packet inspection of DORA (DHCP), DNS, and ICMP processes using Packet Tracer's simulation mode.

---

## 🛠️ Tools & Technologies

| Category | Tool / Resource | Usage |
| :--- | :--- | :--- |
| **Simulation** | **Cisco Packet Tracer** | Topology design and traffic flow simulation. |
| **Hardware** | Cisco 2960 Switches, 1841/2911 Routers | Layer 2 switching and Layer 3 routing configuration via CLI. |
| **Protocols** | DHCP, DNS, ICMP, ARP, UDP/TCP | Service configuration and transport layer analysis. |

---

## 🚀 Implementation Methodology

The project followed a layered approach based on the OSI Model:

### **1. Physical & Data Link Layer (Layers 1-2)**
* Established connectivity using appropriate media (Straight-Through vs. Crossover cables).
* Verified MAC Address Table population on switches to ensure correct frame switching.

### **2. Network Layer & Routing (Layer 3)**
* Configured router interfaces as **Default Gateways** for distinct networks (`192.168.1.x` and `192.168.2.x`).
* Validated inter-network routing to allow communication between the "Sales" and "Server" segments.

### **3. Service Automation (DHCP & DNS)**
* **DHCP Configuration:** The router dynamically assigns IP addresses, avoiding conflicts with static infrastructure IPs.
* **DNS Integration:** Deployed a DNS server to resolve internal domain names (`www.miempresa.com`), simulating a corporate intranet.

```cisco
! DHCP Configuration Snippet
ip dhcp pool RED_VENTAS
 network 192.168.1.0 255.255.255.0
 default-router 192.168.1.254
 dns-server 192.168.1.10
```

### **4. Security Hardening (ACLs)**
* **Policy:** "Block specific hosts in the Sales network from accessing sensitive Servers, while allowing all other traffic."
* **Implementation:** Applied a Standard Access Control List (ACL) inbound on the router's LAN interface.
* **Verification:** Pings from the restricted host resulted in `Destination host unreachable`, confirming the firewall rule was active.

---

## 📊 Project Artifacts & Evidence
* **Final Topology Design:**
*Figure 1: Complete network diagram showing segmented departments and centralized services.*



* **IDHCP Success:**
*Figure 2: Automatic IP assignment via DHCP.*



* **Security Verification (ACL):**
*Figure 3: Evidence of the ACL blocking unauthorized ICMP traffic.*


* **PDNS & Web Service:**
*Figure 4: Successful resolution of the internal domain and web server access.*



---

## 🔒 Project Conclusion:.
This lab demonstrates the balance between network functionality and security. By shifting from static to dynamic addressing, scalability was improved, while ACLs applied the principle of **Least Privilege** at the network level. This project solidifies foundational skills in **Cisco IOS**, **TCP/IP troubleshooting**, and **Network Defense**.
