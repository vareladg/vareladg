# Network Traffic Analysis & Security Monitoring

## Project Overview
This project focuses on **Packet Analysis** and network security auditing. I used **Wireshark** to inspect network traffic at the packet level, demonstrating the critical security difference between unencrypted protocols (HTTP) and encrypted protocols (HTTPS/TLS).

## Scenario
A security audit was requested to verify if legacy internal applications were exposing user credentials. The objective was to:
1.  Intercept live network traffic from a client machine.
2.  Identify clear-text credentials transmitted over insecure channels.
3.  Validate the effectiveness of encryption in modern web traffic.

## Tools Used
* **Wireshark** (Network Protocol Analyzer)
* **Ubuntu Linux** (Target Machine)
* **Firefox** (Traffic Generator)
* **HTTP/TLS Filters** (Data Mining)

## Key Tasks & Analysis

### 1. Environment Setup & Configuration
* Installed Wireshark on Ubuntu 24.04.
* Configured user privileges (`usermod -aG wireshark $USER`) to allow packet capture without root exposure, adhering to security best practices.
* Configured the Network Interface Card (NIC) in Promiscuous Mode to capture all traversing frames.

### 2. Vulnerability Analysis (HTTP)
* **Action:** Captured traffic while logging into a legacy web application (`http://testphp.vulnweb.com`).
* **Filter Used:** `http.request.method == POST` to isolate login form submissions.
* **Forensic Result:** By following the **TCP Stream**, I successfully intercepted the username (`test`) and password (`test`) in plain text.
* **Risk:** Demonstrates how attackers can perform Man-in-the-Middle (MitM) attacks on insecure sites.

<img width="1403" height="479" alt="image" src="https://github.com/user-attachments/assets/08d256ea-c81b-49a8-8462-47d3c61891ae" />

*(Evidence of intercepted credentials)*

### 3. Encryption Validation (HTTPS)
* **Action:** Captured traffic interacting with a secure server (Google.com).
* **Filter Used:** `tls` (Transport Layer Security).
* **Result:** The payload inspection revealed only encrypted "garbage" data, confirming that the contents were unreadable to unauthorized observers.

<img width="1404" height="891" alt="image" src="https://github.com/user-attachments/assets/17d68e27-6e50-482c-9116-51696590427c" />

*(Encrypted TLS payload, securing data privacy)*

## Results & Key Takeaways
* **Deep Packet Inspection (DPI):** Gained proficiency in dissecting network frames to understand application behavior.
* **Protocol Knowledge:** Visualized the TCP/IP handshake and the difference between Layer 7 protocols (HTTP vs HTTPS).
* **Security Awareness:** Validated why SSL/TLS certificates are mandatory for protecting sensitive data in transit.
