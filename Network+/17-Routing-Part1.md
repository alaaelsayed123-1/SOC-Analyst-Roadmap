# Routing – Part 1: Concepts, Types, and Lab Example

## What is Routing?
Routing is the process of forwarding packets from a source network to a destination network across multiple networks. Routers operate at **Layer 3 (Network Layer)** and make forwarding decisions based on **routing tables** and the destination IP address.

**SOC Note:** Understanding routing is crucial for SOC Analysts to track traffic flow, detect misrouted packets, and identify anomalies across networks.

---

## Router Roles and Characteristics
Routers have specific roles and features depending on where and how they are deployed:

### Core Router
- Connects multiple high-speed networks within a large enterprise or service provider.
- Handles **large amounts of traffic** efficiently.
- Focused on speed and minimal latency.

### Edge Router
- Located at the edge of a network, connecting internal networks to external networks like the Internet.
- Often implements **firewalling, NAT, or VPN services**.

### Exterior Router
- Operates between **autonomous systems (AS)** in the Internet.
- Uses exterior routing protocols like **BGP**.
- Helps route traffic between large networks (ISP-to-ISP).

### Autonomous System (AS)
- A collection of networks under **one administrative control**.
- Uses routing protocols internally (like OSPF, EIGRP) and externally communicates with other ASs via BGP.

**SOC Note:** Edge routers and exterior routers are high-value points for monitoring because attacks often attempt to enter or exit through them.

---

## Routing Table
A **routing table** is a database in the router containing paths to different network destinations.

### How It Works
1. Router receives a packet.
2. Reads the **destination IP address**.
3. Matches it against the routing table.
4. Chooses the best route (based on metric, protocol, or next hop).
5. Forwards the packet out through the correct interface.

**Example:**  
- Network 192.168.1.0/24 → connected via interface eth0  
- Network 10.0.0.0/24 → next hop 192.168.1.1  
Packets are routed accordingly.

**SOC Note:** Routing tables are essential for tracing malicious traffic and detecting unauthorized route changes.

---

## Lab Example: Ping Across Networks

### Setup
- Two LANs: LAN-A (192.168.10.0/24) and LAN-B (192.168.20.0/24)
- Router connecting both LANs
- Hosts: PC-A in LAN-A, PC-B in LAN-B

### Scenario 1: Same LAN Ping
- PC-A pings PC-A2 (same subnet)
- Mechanism:
  - ARP resolves MAC addresses
  - Packet delivered directly via Layer 2
- Result: Ping **succeeds**

### Scenario 2: Different LAN Ping
- PC-A pings PC-B (different subnet)
- Mechanism:
  1. PC-A checks subnet mask → destination is not local
  2. Packet sent to **default gateway** (router)
  3. Router checks routing table → finds route to LAN-B
  4. Router forwards packet to PC-B via LAN-B
- Result: Ping **succeeds** if routing table configured correctly

### Scenario 3: Ping Fails
- PC-A pings PC-B but routing table missing route to LAN-B
- Result: Ping **fails**
- SOC Note: Missing or misconfigured routes can cause communication failures or may indicate a misconfiguration attack.

---

## Summary
- Routers forward traffic based on routing tables.
- Core, edge, and exterior routers serve different purposes.
- SOC Analysts must monitor router traffic and tables to detect:
  - Unauthorized route changes
  - Traffic anomalies between networks
  - Potential attack entry or exit points

---

**Key Takeaways for SOC:**
- Understand packet flow across LANs and WANs.
- Know which routers and interfaces are critical for monitoring.
- Ensure routing tables are correct and secure.

