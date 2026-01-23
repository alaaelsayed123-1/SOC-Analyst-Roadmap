# Practical Labs – Layered Network Communication (TCP/IP & OSI)

## Lab Overview
These labs demonstrate how data travels through network layers in real-world scenarios.  
The focus is on understanding how **ports, IP addresses, MAC addresses, DNS, ARP, and routing** work together when a web client communicates with a web server.

Each exercise follows the packet flow through:
Application → Transport → Network → Data Link layers.

---

## Lab 1: Web Client and Server on the Same Network (Using IP Address)

### Scenario
A web client communicates with a web server located on the **same LAN** using the server’s **IP address**.

### Application Layer
- Protocol: HTTP
- Client sends an HTTP request directly to the server IP

### Transport Layer
- Protocol: TCP
- Source Port: 49152
- Destination Port: 80
- Data is encapsulated into a TCP segment

### Network Layer
- Source IP: 192.168.1.10
- Destination IP: 192.168.1.20
- IP packet is created

### Data Link Layer
- Client checks ARP cache
- If MAC address is unknown, client sends ARP request to FF:FF:FF:FF:FF:FF
- Server responds with its MAC address
- Ethernet frame is built:
  - Source MAC: Client MAC
  - Destination MAC: Server MAC

### Result
- Communication succeeds directly
- No router or default gateway is involved

---

## Lab 2: Web Client and Server on the Same Network (Using Domain Name)

### Scenario
A web client accesses a web server using a **domain name instead of an IP address** within the same LAN.

### Step 1: DNS Resolution
- Client sends DNS query
- Protocol: UDP
- Destination Port: 53
- DNS server responds with server IP: 192.168.1.20

### Step 2: Web Communication

#### Transport Layer
- Protocol: TCP
- Source Port: 49153
- Destination Port: 80

#### Network Layer
- Source IP: 192.168.1.10
- Destination IP: 192.168.1.20

#### Data Link Layer
- Client uses ARP to resolve the server MAC address
- Ethernet frame is sent directly to the server

### Result
- DNS is required before HTTP communication
- After resolution, traffic flow is identical to Lab 1

---

## Lab 3: Web Client and Server on Different Networks

### Scenario
A web client communicates with a web server located on a **different network**, requiring routing.

### Transport Layer
- Protocol: TCP
- Source Port: 49154
- Destination Port: 80

### Network Layer
- Source IP: 192.168.1.10
- Destination IP: 172.16.10.20
- Destination is outside the local subnet

### Data Link Layer (Client Side)
- Client cannot ARP the server directly
- Client sends ARP request for the **default gateway**
- Ethernet frame:
  - Source MAC: Client MAC
  - Destination MAC: Router (Gateway) MAC

### Routing Process
- Router removes Layer 2 header
- IP packet remains unchanged
- Router forwards the packet to the next hop
- New MAC addresses are applied at each hop

### Result
- IP addresses stay the same end-to-end
- MAC addresses change at every hop

---

## Key Technical Observations
- Ports identify applications and services
- IP addresses identify hosts across networks
- MAC addresses are used only for local delivery
- ARP operates within the local network only
- DNS translates domain names into IP addresses
- Routers operate at Layer 3 and rebuild Layer 2 headers

---

## SOC Analyst Perspective
- ARP activity can indicate spoofing attempts
- DNS traffic reveals user behavior and intent
- Port usage identifies application-level activity
- Gateway resolution confirms routing paths
- These events are visible in packet captures, firewall logs, and IDS alerts

