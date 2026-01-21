# Network Terms and Network Architecture

## Network Connectivity and Internetworking
A network can consist of multiple LANs connected together using a WAN.  
When different LANs are connected through WAN links, the result is an **internetwork**.  
The largest example of an internetwork is the **Internet**, which connects networks globally through ISPs.

**SOC Note:** Understanding internetworking helps analyze traffic that crosses network boundaries.

---

## Internet Service Provider (ISP)
An ISP provides connectivity that allows LANs to access external networks, including the Internet.

**SOC Note:** Most external attacks originate through ISP-connected interfaces.

---

## Intranet
An **Intranet** is a private internal network that is accessible only to authorized users inside the organization.

**SOC Note:** Intranet traffic is usually trusted but must still be monitored for insider threats.

---

## Extranet
An **Extranet** allows limited access to internal network resources for external users, such as partners or vendors.  
Access is usually restricted to specific services like web or mail servers.

**SOC Note:** Extranets are high-risk areas and must be tightly controlled and monitored.

---

## Firewall
A firewall controls traffic between internal networks and external networks like the Internet.  
It can block malicious traffic and prevent unauthorized access to the LAN.

**SOC Note:** Firewalls generate critical logs used by SOC teams to detect attacks.

---

## Network Devices and Roles

### Workstation
A workstation is a computer inside the network used by end users.

### Client
A client is any device that requests a service from a server.

### Server
A server is a device that provides specific services to clients.

---

## Server Roles

### File Server
Allows users to store files centrally instead of on local machines for security and backup purposes.

### Print Server
Manages printing services for all devices on the network.

### Web Server
Handles web requests from clients and returns web content.  
- Linux: Apache  
- Windows: IIS  

**SOC Note:** Web servers are common attack targets and must be monitored closely.

### Mail Server
Processes sending and receiving of email messages for clients.

### Proxy Server
Acts as an intermediary between clients and the Internet.  
Allows administrators to restrict access to specific websites.

**SOC Note:** Proxy logs are valuable for detecting suspicious browsing behavior.

---

## Directory Services (Active Directory)
Microsoft Active Directory is used for authentication and authorization.  
Users must be verified before accessing network resources.

**SOC Note:** Failed login attempts and privilege escalation attempts are key SOC alerts.

---

## Hosts
A host is any device on a network that has an IP address.

---

## IPv4 Addressing
IPv4 addresses consist of four octets, each ranging from 0 to 255.  
The address is divided into:
- Network portion
- Host portion  

The **subnet mask** determines which part identifies the network and which identifies the host.

**SOC Note:** IP addressing is essential for identifying attack sources and destinations.

---

## MAC Address
A MAC address is a physical hardware address assigned to a network interface.  
It consists of:
- **OUI** (Organizationally Unique Identifier)
- **NIC** specific identifier

**SOC Note:** MAC addresses help identify unauthorized devices inside a LAN.

---

## Practical Lab Observations

- Two PCs on the same network can communicate successfully using ping.  
- PCs on different networks cannot communicate without routing.  
- Firewall enabled: ping requests are blocked (Request Timed Out).  
- Firewall disabled: ping succeeds.  

**SOC Note:** Firewall behavior directly impacts visibility and connectivity.

---

## SOC Summary
Understanding network architecture, addressing, servers, and access control is fundamental for SOC Analysts.  
These concepts support effective monitoring, incident detection, and response in enterprise environments.

