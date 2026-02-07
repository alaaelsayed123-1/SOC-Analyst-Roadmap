# Routing – Complete Lab (Part 1 & Part 2)

## Overview
Routing is the process of moving packets from a source device to a destination device across one or more networks. Routers operate at Layer 3 (Network layer) and make decisions based on IP addresses.  

This lab covers:
- Router roles and types
- Routing between networks
- Static and dynamic routing
- Routing protocols
- Default routes
- SOC perspective

---

## Part 1 – Routing Basics

### Router Roles & Types
- **Core Router:** Operates within the backbone of a network, high speed, connects multiple routers.  
- **Edge Router:** Connects internal networks to external networks, often at the boundary of an ISP or organization.  
- **Autonomous System (AS) Router:** Part of a network with a common routing policy.  
- **Exterior Router:** Handles routing between different autonomous systems.

**SOC Note:** Monitoring router logs is critical, as misconfigurations or route changes can indicate attacks like route hijacking.

---

### Lab Scenario 1: Ping within Same LAN
**Objective:** Test connectivity between two PCs on the same network.  

**Setup:**  
- PC1 IP: 192.168.1.10  
- PC2 IP: 192.168.1.20  

**Observation:**  
- Ping succeeds
- MAC addresses are resolved via ARP
- Source port, destination port shown in transport layer (TCP/UDP)

---

### Lab Scenario 2: Ping Between Different Networks
**Setup:**  
- Network1: 192.168.1.0/24  
- Network2: 192.168.2.0/24  
- Router connects both networks

**Observation:**  
- Ping succeeds only if router has correct routing table
- MAC address changes at each hop
- Source IP remains same; destination IP is target

**SOC Note:** Unauthorized ICMP traffic or failed pings may indicate misconfigurations or network attacks.

---

## Part 2 – Routing Protocols and Dynamic Routing

### Ways to Connect Devices Across Networks
1. **Manual (Static Routing):** Admin sets routes manually.  
2. **Dynamic Routing:** Routers exchange information automatically using protocols.

---

### Routing Protocol Fundamentals
- **Scope:** Determines where a route is valid (LAN, WAN, internet)  
- **Metric:** Quantitative value used to select best path  
  - Hop count (number of routers)  
  - Bandwidth and delay  
  - Relative/linked cost  

- **Sharing Methods:**  
  - Distance Vector: Shares routing table with neighbors (e.g., RIP)  
  - Link State: Shares topology information (e.g., OSPF)  
  - Hybrid: Combines both (e.g., EIGRP)

- **Administrative Distance (AD):** Priority for route selection from multiple protocols

---

### Routing Protocol Examples
| Protocol | Type | Metric | SOC Perspective |
|----------|------|--------|----------------|
| RIP      | Distance Vector | Hop Count | Detect routing loops and misconfigurations |
| EIGRP    | Hybrid          | Bandwidth, Delay | Monitor for unauthorized route injections |
| OSPF     | Link State      | Cost (Bandwidth) | Watch for sudden topology changes |
| IS-IS    | Link State      | Cost (Bandwidth) | Ensure no malicious route flaps |
| BGP      | Exterior        | AS Path | Critical: can affect Internet reachability |

---

### Lab Scenario 3: Static Routing Between Networks
**Topology:** PC1 → Router1 → Router2 → PC2  
- Network1: 192.168.10.0/24  
- Network2: 192.168.20.0/24  

**Router1 Config:**   
 ip route 192.168.20.0 255.255.255.0 192.168.10.2 
 **Router2 Config:**  
ip route 192.168.10.0 255.255.255.0 192.168.20.2
**Test:**  
PC1> ping 192.168.20.10

**Observation:** Ping succeeds if routes are correct.  

---

### Lab Scenario 4: Dynamic Routing with RIP
**Router1 Config:**  
router rip
version 2
network 192.168.10.0
network 192.168.20.0

**Router2 Config:**  


router rip
version 2
network 192.168.10.0
network 192.168.20.0


**Observation:**  
- Routes are learned automatically  
- Metric based on hop count  

**SOC Note:** Monitor routing updates for anomalies.

---

### Lab Scenario 5: OSPF Dynamic Routing
**Router1 Config:**  


router ospf 1
network 192.168.10.0 0.0.0.255 area 0
network 192.168.20.0 0.0.0.255 area 0

**Router2 Config:**  


router ospf 1
network 192.168.10.0 0.0.0.255 area 0
network 192.168.20.0 0.0.0.255 area 0


**Observation:**  
- OSPF converges quickly  
- Supports VLSM  
- Cost-based best path selection

---

### Lab Scenario 6: Default Route
**Router1 Config:**  


ip route 0.0.0.0 0.0.0.0 192.168.20.1

**Test:**  


PC1> ping 8.8.8.8


**Observation:**  
- Traffic goes via default route  
- SOC: Monitor default routes to detect exfiltration

---

## Lab Summary
- **Routing Part 1:** Basic connectivity, MAC/IP resolution, ping testing  
- **Routing Part 2:** Static vs Dynamic routing, routing protocols, metrics, AD, default routes  
- **SOC Perspective:** Misconfigured or malicious routes can lead to network compromise; always monitor routing tables, protocol updates, and ICMP traffic  

**Pro Tip:** Regularly verify routing tables (`show ip route`) and test connectivity (`ping`, `traceroute`).



