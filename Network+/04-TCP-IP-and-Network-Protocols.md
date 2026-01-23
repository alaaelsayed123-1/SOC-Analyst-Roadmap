# TCP/IP Model and Network Protocols (With Flows)

This document covers the **TCP/IP model**, its relationship with the **OSI model**, and a detailed explanation of **network protocols**, including **why they are used, how they work, their ports, and their communication flows**.

---

## Why TCP/IP?
TCP/IP is the practical networking model used in real-world networks and the Internet.  
It defines how data is created, transmitted, routed, and received between hosts.

**SOC Note:** All network traffic analyzed in a SOC environment follows the TCP/IP model.

---

## TCP/IP Model Layers

### 1. Application Layer
- Combines OSI Application, Presentation, and Session layers
- Provides network services to applications

**Examples:** HTTP, HTTPS, FTP, SMTP, DNS, DHCP

---

### 2. Transport Layer
- Provides host-to-host communication
- Responsible for reliability and flow control

**Protocols:** TCP, UDP

---

### 3. Internet Layer
- Handles logical addressing and routing

**Protocols:** IP, ICMP, ARP, RARP

---

### 4. Network Access Layer
- Responsible for physical transmission of data

**Technologies:** Ethernet, Wi-Fi

---

## OSI vs TCP/IP

| OSI Model | TCP/IP Model |
|----------|--------------|
| 7 Layers | 4 Layers |
| Conceptual | Practical |
| Learning model | Real-world implementation |

**Similarity:** Both describe data movement through layers.  
**Difference:** TCP/IP merges several OSI layers.

---

## Transport Protocols

### TCP – Transmission Control Protocol
- Reliable and connection-oriented
- Uses three-way handshake
- Guarantees data delivery

**Used by:** HTTP, HTTPS, FTP, SMTP, IMAP

---

### UDP – User Datagram Protocol
- Fast and connectionless
- No delivery guarantee

**Used by:** DNS, DHCP, TFTP, VoIP

---

## Web Protocols

### HTTP – TCP Port 80 (Flow)
1. Client sends HTTP request (GET/POST).
2. TCP connection is established.
3. Request is sent using IP and Ethernet/Wi-Fi.
4. Server processes request and sends response.
5. TCP ensures reliable delivery.

---

### HTTPS – TCP Port 443 (Flow)
- Same as HTTP but encrypted using SSL/TLS.
- Protects confidentiality and integrity of data.

---

## Secure Communication

### SSL / TLS
- Encryption protocols used to secure data in transit
- TLS is the modern replacement for SSL

---

## File Transfer Protocols

### FTP – TCP Ports 21 & 20 (Flow)
- Control channel on port 21
- Data transfer on port 20
- Unencrypted communication

---

### TFTP – UDP Port 69 (Flow)
- Simple and fast file transfer
- No authentication
- Used for device booting

---

### SFTP – TCP Port 22
- Secure file transfer over SSH
- Encrypted authentication and data

---

## Email Protocols

### SMTP – TCP Port 25 (Flow)
- Sends emails from client to server
- Server forwards email to recipient server

---

### POP3 – TCP Port 110
- Downloads emails and removes them from server

---

### IMAP – TCP Port 143
- Synchronizes emails across multiple devices

---

## Network Services Protocols

### DHCP – UDP Ports 67/68 (DORA Flow)
1. Discover
2. Offer
3. Request
4. Acknowledge

---

### DNS – TCP/UDP Port 53 (Flow)
1. Client queries domain name
2. DNS server responds with IP address

---

### NTP – UDP Port 123
- Synchronizes system time

---

## Network Management Protocols

### SNMP – UDP Port 161
- Network monitoring and management

---

### Telnet – TCP Port 23
- Remote access (unencrypted)

---

### SSH – TCP Port 22
- Secure remote access

---

### RDP – TCP Port 3389
- Remote desktop access for Windows systems

---

## Control Protocols

### ICMP
- Error reporting and diagnostics
- Used by ping and traceroute

---

### IGMP
- Manages multicast group memberships

---

## Multimedia Communication Protocols

### SIP
- Initiates and manages communication sessions

### RTP
- Transmits real-time audio and video

### MGCP / H.323
- Controls and manages VoIP communication

---

## Protocol Workflow (High-Level)

1. Application creates data
2. Transport layer uses TCP or UDP
3. Internet layer adds IP, ICMP, ARP
4. Network Access layer transmits data using Ethernet or Wi-Fi

---

## SOC Summary
Understanding protocol flows, ports, and purposes is essential for SOC Analysts.  
This knowledge enables traffic analysis, anomaly detection, and effective incident response.

