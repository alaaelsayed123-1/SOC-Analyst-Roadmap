# Network Basics

## Next Step
Continue Network+ introduction and apply concepts in TryHackMe.

---

## Networking Advantages vs Disadvantages

### Advantages
1. **Resource Sharing** – Multiple users can access the same files, printers, or applications over the network, reducing redundancy.  
2. **Communication** – Enables fast communication between devices via email, instant messaging, or video calls.  
3. **Centralized Management** – Network administrators can monitor, update, and secure devices from a central location.  

### Disadvantages
1. **Security Risks** – Malware or attacks can spread rapidly across connected devices.  
2. **Network Dependency** – Network failures can disrupt all connected services and communication.  
3. **Management Complexity** – Requires trained personnel to maintain and secure the network.

---

## Network Components

- **Computer System:** End devices like PCs, laptops, and servers that generate or consume data.  
- **Network Media:** Physical cables (Ethernet) or wireless channels (Wi-Fi) connecting devices.  
- **Network Interface (NIC):** Hardware component allowing a device to connect to the network.  
- **Network Protocol:** Rules and standards (e.g., TCP/IP) that define how devices communicate.  

**SOC Note:** Understanding components helps identify attack surfaces and locate where logs are generated for monitoring.

---

## Network Types (Geographical)

- **LAN (Local Area Network):** Covers a small area like an office or building.  
  **SOC Note:** LAN traffic monitoring detects internal threats or lateral movement.  
- **WAN (Wide Area Network):** Connects multiple LANs over long distances.  
  **SOC Note:** WAN monitoring helps track external threats and incoming/outgoing traffic.  
- **MAN (Metropolitan Area Network):** Covers a city or campus.  
- **WLAN (Wireless LAN):** Wireless network for mobility within LAN areas.

---

## Host Roles

### Client/Server
- Server provides services; client requests services.  
- Centralized structure allows easier control and security.  
**SOC Note:** Security alerts often focus on client-server interactions (e.g., failed login attempts).

### Peer-to-Peer (P2P)
- Devices act as both client and server.  
- Simple and low-cost but less secure and harder to monitor.  
**SOC Note:** P2P networks can bypass monitoring if not segmented properly.

---

## Network Topologies

### Physical Topology
Defines how devices are physically connected.  

### Bus Topology
- Single backbone cable connecting all devices.  
- Uses broadcast messages for communication.  
**SOC Note:** Easier to detect collisions and monitor traffic.

### Star Topology
- Devices connect to a central switch or hub.  
- Most common in modern networks.  
**SOC Note:** Central device is critical; monitoring hub/switch logs is essential.

### Ring Topology
- Devices connected in a loop.  
- Data circulates in one direction.  
**SOC Note:** A break in the ring can stop communication; useful for monitoring continuity.

### Mesh Topology
- Devices have multiple connections to each other.  
- High redundancy and fault tolerance.  
**SOC Note:** Complex to monitor but very resilient; alerts can indicate link failures.

---

## Traffic Types

- **Unicast:** One-to-one communication between devices.  
- **Broadcast:** One-to-all communication in a network segment.  
- **Multicast:** One-to-many communication to selected devices.  

**SOC Note:** Understanding traffic types helps detect anomalies such as unusual broadcast storms or unauthorized multicast traffic.

---

## SOC Summary
Having a solid understanding of network types, components, host roles, topologies, and traffic flow is critical for any SOC Analyst.  
These concepts form the foundation for analyzing logs, detecting anomalies, and identifying potential attacks in real-world network environments.
