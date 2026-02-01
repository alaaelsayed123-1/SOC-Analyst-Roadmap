# IP Address Assignment – Methods and Architecture

## TL;DR – SOC Summary
- IP addressing methods determine how devices join a network and communicate.  
- SOC Analysts need to understand addressing methods to investigate connectivity issues, unauthorized devices, and misconfigurations.  
- Knowing static vs dynamic IP, APIPA fallback, and DHCP processes helps correlate logs and detect anomalies.

---

## 1. Static IP Address Assignment

### Definition
- IP addresses are manually assigned to devices.  
- Used for servers, routers, printers, and critical network devices.

### Devices & Architecture
- Devices: Computers, servers, network printers, switches, routers.  
- Architecture: IP, subnet mask (SM), default gateway (DG), DNS manually configured.

### Example
- Device: Server  
  - IP: `192.168.1.10`  
  - SM: `255.255.255.0`  
  - DG: `192.168.1.1`  
  - DNS: `8.8.8.8`  

### SOC Perspective
- Analysts monitor static IPs to detect if a rogue device attempts to use an IP outside the approved list.  
- Misconfigured static IPs can generate duplicate IP conflicts, which appear in network logs.

---

## 2. Dynamic IP Address Assignment (DHCP)

### Definition
- Devices request IP addresses from a DHCP server.  
- Addresses are assigned automatically and leased for a specific time.

### Devices & Architecture
- Devices: Client PCs, laptops, IoT devices.  
- DHCP Server: Assigns IP, SM, DG, DNS dynamically.  
- Network segments often include routers forwarding DHCP requests.

### Example
- Client PC requests IP from DHCP server.  
- Server assigns: `192.168.1.50/24` with DG `192.168.1.1` for 24 hours lease.

### SOC Perspective
- SOC Analysts monitor DHCP logs for unauthorized devices or unusual lease requests.  
- Helps detect rogue DHCP servers in the network (DHCP starvation attacks).

---

## 3. APIPA (Automatic Private IP Addressing)

### Definition
- Fallback IP assignment when DHCP server is unreachable.  
- Uses `169.254.x.x` with subnet mask `/16`.

### Devices & Architecture
- Devices: Any DHCP client.  
- Architecture: Device self-assigns IP to communicate locally in absence of DHCP.

### Example
- PC fails to reach DHCP → assigns `169.254.12.34/16`.  
- Only allows communication within the same local segment.

### SOC Perspective
- Analysts can detect network outages or DHCP server failures.  
- APIPA addresses can indicate troubleshooting needs.

---

## 4. Alternative Configuration

### Definition
- A manual fallback method if DHCP fails, allowing static assignment of secondary parameters (IP, SM, DG, DNS).

### Example
- Device: Laptop  
- Primary: DHCP request failed  
- Alternative IP: `192.168.1.100/24`  
- DG: `192.168.1.1`  
- DNS: `8.8.4.4`  

### SOC Perspective
- Helps ensure critical devices maintain connectivity.  
- SOC logs can show alternative configuration usage, aiding troubleshooting.

---

## 5. DHCP Process – DORA Methodology

### Steps
1. **Discovery (D):** Client broadcasts `DHCPDISCOVER` to find available DHCP servers.  
2. **Offer (O):** Server responds with `DHCPOFFER` including IP, lease time, SM, DG, DNS.  
3. **Request (R):** Client selects an offer and sends `DHCPREQUEST` to the server.  
4. **Acknowledgment (A):** Server confirms assignment with `DHCPACK`.

### Devices & Architecture
- Clients, DHCP servers, routers (if DHCP relay needed).

### Example Lab
- **Setup:** VMware environment  
  - DHCP server VM  
  - Client VM  
- **Steps:**  
  1. Client requests IP → broadcast DORA  
  2. Server assigns `192.168.1.50`  
  3. Verify IP, subnet, DG on client  
- **SOC Note:** Monitor logs to verify all DORA steps and detect anomalies (e.g., rogue DHCP).

---

## 6. Lab Observations & SOC Notes

- Static IPs are easier to monitor for rogue devices.  
- Dynamic IPs require logging and correlation to track device behavior.  
- APIPA addresses indicate DHCP issues.  
- Alternative configurations maintain connectivity during DHCP failures.  
- SOC Analysts can detect IP conflicts, rogue servers, and misconfigurations through DHCP logs.

---

